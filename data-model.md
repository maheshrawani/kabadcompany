# Data Model

## Kabad Company — Core Data Architecture

**Status:** Early-stage research and product exploration  
**Purpose:** Define the information structure required to operate recyclable-material sourcing manually today and support software and AI workflows later.

---

## 1. Why a Data Model Matters

The first version of Kabad Company can operate with spreadsheets, WhatsApp and human coordination.

However, if every conversation is stored as unstructured text, it becomes difficult to answer basic questions such as:

- Which buyers currently need PP?
- Which suppliers regularly have HDPE?
- What price was actually achieved?
- Which suppliers delivered acceptable quality?
- Which buyers purchase repeatedly?
- Which requirements are still active?
- Why did a transaction fail?

A structured data model creates the foundation for answering these questions.

---

## 2. Core Entities

The initial system can be organized around:

```text
Company
├── Buyer
├── Supplier
├── Material
├── Requirement
├── Supply
├── Match
├── Transaction
├── Shipment
└── Communication
```

Not every entity needs to become a separate software table immediately.

---

## 3. Company

A company record could contain:

```yaml
company:
  id: COMP-001
  name: Example Industries
  type: recycler
  city: Ghaziabad
  state: Uttar Pradesh

  contact:
    name: Contact Person
    phone: ""
    email: ""

  status: active
  verification_status: pending
```

Possible company types:

- Recycler
- Processor
- Manufacturer
- Scrap dealer
- Aggregator
- Waste-management company
- Trader
- Logistics provider
- Other

A company may play more than one role.

---

## 4. Buyer

A buyer is an organization that purchases recyclable material or recycled feedstock.

Example:

```yaml
buyer:
  id: BUY-001
  company_id: COMP-001

  buying_categories:
    - PP
    - HDPE

  geography:
    preferred_regions:
      - Delhi NCR
      - Western UP

  status: active
```

The buyer record should describe the organization broadly.

Specific purchasing requirements belong in the requirement entity.

---

## 5. Supplier

A supplier represents a source of recyclable material.

Example:

```yaml
supplier:
  id: SUP-001
  company_id: COMP-002

  supplier_type:
    - scrap_dealer

  materials:
    - PP
    - HDPE
    - LDPE

  operating_regions:
    - Ghaziabad
    - Noida

  verification_status: supplier_reported
```

A supplier can have multiple material supplies.

---

## 6. Material

Material should be separated from individual transactions.

Example:

```yaml
material:
  id: MAT-PP
  family: PP
  name: Polypropylene

  attributes:
    form:
      - scrap
      - regrind
      - granules

    common_quality_fields:
      - color
      - contamination
      - moisture
      - washing
```

Different material families may require different attributes.

---

## 7. Material Taxonomy

An initial taxonomy could include:

```text
Plastic
├── PP
├── HDPE
├── LDPE
├── PET
├── ABS
├── HIPS
└── Mixed Plastics
```

The taxonomy should remain extensible.

Future categories may include:

```text
Paper
Metal
Textile
Glass
E-waste
Batteries
Other recyclable materials
```

These should be added only when there is a real operating need.

---

## 8. Material Specification

A material specification describes what a particular buyer or supplier means by the material.

Example:

```yaml
material_specification:
  material_family: PP
  form: regrind
  color: mixed

  quality:
    washed: true
    contamination: low
    moisture: buyer_defined

  grade:
    value: buyer_specific
    source: buyer
```

The same material family can therefore have many commercially different specifications.

---

## 9. Requirement

A requirement represents a specific buying need.

Example:

```yaml
requirement:
  id: REQ-001
  buyer_id: BUY-001

  material:
    family: PP
    form: regrind
    grade: buyer_specific

  quantity:
    required_mt: 20
    minimum_mt: 15

  location:
    delivery_city: Ghaziabad

  commercial:
    price_basis: delivered

  timing:
    required_by: YYYY-MM-DD

  status: active
```

The requirement should preserve the buyer's original request as well as the normalized structured version.

---

## 10. Requirement Lifecycle

A requirement can move through states:

```text
New
 ↓
Clarification Needed
 ↓
Qualified
 ↓
Supplier Search
 ↓
Supplier Responses
 ↓
Buyer Review
 ↓
Negotiation
 ↓
Confirmed
 ↓
Completed
```

It may also become:

```text
Expired
Cancelled
On Hold
Failed
```

---

## 11. Supply

A supply record represents material currently or potentially available from a supplier.

Example:

```yaml
supply:
  id: SUPPLY-001
  supplier_id: SUP-001

  material:
    family: PP
    form: regrind

  quantity:
    available_mt: 25

  location:
    pickup_city: Noida

  commercial:
    quoted_price: X
    price_basis: pickup

  availability:
    status: available
    valid_until: YYYY-MM-DD
```

Supply information is time-sensitive.

A price from three months ago should not automatically be treated as today's price.

---

## 12. Match

A match connects a requirement with a possible supply.

```yaml
match:
  id: MATCH-001

  requirement_id: REQ-001
  supply_id: SUPPLY-001

  status: potential

  compatibility:
    material: match
    grade: unknown
    quality: partial
    quantity: match
    location: match
    timing: match
    price: pending

  next_action:
    type: verify_quality
```

This structure allows uncertainty to remain visible.

---

## 13. Transaction

A transaction represents a commercially confirmed movement of material.

Example:

```yaml
transaction:
  id: TXN-001

  requirement_id: REQ-001
  supply_id: SUPPLY-001

  material:
    family: PP
    form: regrind

  quantity:
    agreed_mt: 20
    delivered_mt: 19.7

  commercial:
    agreed_price: X
    price_basis: delivered

  status: completed
```

The transaction should store what actually happened, not just what was originally quoted.

---

## 14. Transaction Status

Possible states:

```text
Potential
 ↓
Negotiating
 ↓
Confirmed
 ↓
Loading
 ↓
In Transit
 ↓
Delivered
 ↓
Quality Accepted
 ↓
Settled
 ↓
Completed
```

Possible failure states:

```text
Cancelled
Supplier Failed
Buyer Rejected
Quality Rejected
Price Changed
Logistics Failed
Quantity Short
Payment Issue
```

The reason for failure should be recorded whenever possible.

---

## 15. Shipment

A transaction may involve one or more shipments.

Example:

```yaml
shipment:
  id: SHIP-001
  transaction_id: TXN-001

  origin:
    city: Noida

  destination:
    city: Ghaziabad

  quantity_mt: 20

  transport:
    responsibility: supplier
    vehicle_type: truck

  status: delivered
```

Separating shipment from transaction allows one transaction to contain multiple loads.

---

## 16. Communication

Important information often originates in WhatsApp or phone conversations.

A future system could capture:

```yaml
communication:
  id: MSG-001

  company_id: COMP-002
  channel: whatsapp

  timestamp: YYYY-MM-DDTHH:MM

  content_type: requirement

  extracted_data:
    material: PP
    quantity_mt: 10
    price: X
    location: Noida
```

The original message should remain available when possible.

AI-extracted information should be treated as extracted data, not unquestionable truth.

---

## 17. Source of Truth

Each important field should ideally have:

```text
Value
+
Source
+
Timestamp
+
Confidence / verification status
```

Example:

```yaml
price:
  value: X
  source: supplier_message
  timestamp: YYYY-MM-DD
  verification: supplier_reported
```

This becomes especially important for:

- Price
- Quantity
- Quality
- Availability
- Delivery status

---

## 18. Verification Levels

A simple verification model could be:

```text
Level 0 — Unverified
Level 1 — Self-reported
Level 2 — Document / evidence reviewed
Level 3 — Transaction verified
Level 4 — Repeated transaction history
```

These levels are a framework for research, not a certification system.

---

## 19. Contact Data

Contacts should be separate from company identity where possible.

Example:

```yaml
contact:
  id: CONT-001
  company_id: COMP-001

  name: Contact Person
  role: Purchase Manager

  phone: ""
  email: ""

  preferred_channel: whatsapp
```

One company may have multiple contacts.

---

## 20. Price Data

Prices should never be stored as a single number without context.

A useful price record may contain:

```yaml
price:
  value: X
  unit: INR/kg

  basis:
    - pickup
    - delivered

  location: Ghaziabad

  material: PP

  effective_date: YYYY-MM-DD

  source:
    type: supplier_quote
```

This allows historical price analysis later.

---

## 21. Quality Data

Quality information can include:

```yaml
quality:
  grade: ""
  form: regrind
  color: mixed
  washed: true

  contamination:
    value: ""
    unit: percent

  moisture:
    value: ""
    unit: percent

  inspection:
    status: pending
```

Not every field will apply to every material.

---

## 22. Quantity Data

Quantities should include units.

Preferred structure:

```yaml
quantity:
  value: 20
  unit: MT
```

Potential units:

- kg
- MT
- tonnes
- pieces
- bags
- truckloads

Where possible, normalize internally to a standard unit.

---

## 23. Location Data

Location can contain:

```yaml
location:
  city: Noida
  district: Gautam Buddha Nagar
  state: Uttar Pradesh
  country: India
```

Exact addresses should only be stored when operationally necessary.

---

## 24. Relationship Model

A simplified relationship diagram:

```text
Company
 ├── Buyer
 ├── Supplier
 └── Contacts

Buyer
 └── Requirements

Supplier
 └── Supplies

Requirement
 └── Matches

Supply
 └── Matches

Match
 └── Transaction

Transaction
 └── Shipments
```

This creates a traceable path from demand to supply to completed transaction.

---

## 25. Example End-to-End Record

```text
Buyer
  ↓
Requirement
  ↓
Potential Matches
  ↓
Supplier
  ↓
Supply
  ↓
Commercial Confirmation
  ↓
Transaction
  ↓
Shipment
  ↓
Delivery
  ↓
Quality Result
  ↓
Settlement
```

Every stage can add data.

---

## 26. What Data Should Be Captured First?

The initial manual system should focus on a small number of high-value fields:

### Buyer

- Company
- Contact
- Material
- Quantity
- Quality
- Location
- Price basis
- Timing

### Supplier

- Company
- Contact
- Material
- Quantity
- Location
- Expected price
- Quality information
- Availability

### Transaction

- Final quantity
- Final price
- Freight
- Quality outcome
- Delivery outcome
- Payment outcome
- Success/failure reason

Do not create a complex database before these fields are consistently captured.

---

## 27. Data Quality Rules

The system should eventually enforce rules such as:

```text
Quantity must have a unit.
Price must have a price basis.
Price should have a timestamp.
Material should use a recognized category.
Unknown quality should remain unknown.
Expired supply should not appear as active.
Completed transactions should preserve final values.
```

---

## 28. Historical Data

Historical records are valuable because they can answer questions such as:

- What price was achieved for a material?
- Which suppliers repeatedly supplied it?
- Which buyers repeatedly purchased it?
- Which locations produced workable economics?
- Which quality issues caused rejection?
- Which suppliers became reliable over time?

Historical data should never be used without considering its date and market context.

---

## 29. AI and the Data Model

AI can help convert unstructured information into structured records.

Example:

WhatsApp:

> "PP regrind 10 ton available in Noida, around ₹X, can load tomorrow."

Potential extraction:

```yaml
material: PP
form: regrind
quantity_mt: 10
location: Noida
price: X
availability: tomorrow
```

A human can then confirm the extracted information.

---

## 30. Data Confidence

Every AI-generated field could eventually have a confidence state:

```text
Confirmed
Human Verified
AI Extracted
Inferred
Unknown
```

The system should avoid silently converting an inference into a confirmed commercial fact.

---

## 31. Data for Matching

The matching engine can consume:

```text
Requirements
+
Supplies
+
Material specifications
+
Price data
+
Location data
+
Transaction history
+
Verification data
```

This creates the foundation for the matching workflow described in `matching-workflow.md`.

---

## 32. Data for Price Intelligence

Transaction records can eventually support:

```text
Material
→ Grade
→ Location
→ Date
→ Quantity
→ Price
→ Freight
→ Final delivered economics
```

This could become one of the most valuable datasets generated by actual transactions.

---

## 33. Data for Supplier Intelligence

Over time:

```text
Supplier
→ Materials
→ Quantities
→ Prices
→ Quality outcomes
→ Delivery outcomes
→ Transaction history
```

This can help distinguish between:

```text
New supplier
Known supplier
Repeated supplier
Verified supplier
Reliable supplier
```

The labels should be based on documented activity.

---

## 34. Data for Buyer Intelligence

Similarly:

```text
Buyer
→ Materials purchased
→ Quantity
→ Frequency
→ Locations
→ Quality requirements
→ Price basis
→ Transaction history
```

This can reveal recurring demand patterns.

---

## 35. Privacy

The project should avoid publishing real commercial records publicly.

GitHub examples should use:

- Synthetic companies
- Fake phone numbers
- Placeholder prices
- Anonymized transactions

Private operational data should remain in appropriate private systems.

---

## 36. Initial Technology Approach

The data model can initially be implemented with:

```text
Google Sheets / Airtable / Database
        +
WhatsApp
        +
n8n
        +
AI
```

The exact technology stack should be chosen after operational requirements are better understood.

---

## 37. Database Evolution

A possible progression:

```text
Phase 1
Spreadsheet

      ↓

Phase 2
Structured database

      ↓

Phase 3
Operational dashboard

      ↓

Phase 4
Matching engine

      ↓

Phase 5
AI-assisted sourcing system
```

Technology should follow validated workflow rather than precede it.

---

## 38. What Should Not Be Assumed

The project is not assuming that:

- More data automatically means better decisions.
- AI can verify material quality remotely.
- Historical prices are always current.
- Supplier-reported quantities are always accurate.
- A database alone creates marketplace liquidity.
- Every buyer and supplier should be automatically matched.

Real-world validation remains necessary.

---

## 39. Current Status

This document describes a proposed data architecture.

It is not a production database schema.

The immediate goal is to identify which data fields are genuinely useful during real transactions and remove fields that create unnecessary operational work.

---

## 40. Long-Term Vision

The long-term data architecture could connect:

```text
Demand
   ↓
Material Intelligence
   ↓
Supply
   ↓
Matching
   ↓
Logistics
   ↓
Transaction
   ↓
Quality
   ↓
Payment
   ↓
Learning
```

Each completed transaction can contribute structured information to the next decision.

---

## Core Principle

> **Capture the smallest amount of structured data that creates meaningful operational learning, then expand the model only when real transactions prove that additional data is useful.**
