# Transaction Data

## Kabad Company — Transaction Intelligence Framework

**Status:** Early-stage validation  
**Purpose:** Define the minimum information to capture from real recyclable-material transactions so that every deal improves operational knowledge, commercial understanding, and future product design.

---

## 1. Why Transaction Data Matters

The most valuable learning will come from actual transactions.

A completed or failed transaction can reveal:

- What material was actually available
- What quantity was actually delivered
- What price was actually accepted
- What freight actually cost
- Whether quality matched expectations
- Whether the buyer accepted the load
- Whether the supplier performed reliably
- Why the transaction succeeded or failed

This information can become the foundation for future sourcing intelligence.

---

## 2. Transaction vs Conversation

A conversation is not a transaction.

Example:

```text
Supplier says:
"10 MT PP available at ₹X/kg."
```

This is a supply claim.

A transaction requires additional evidence:

```text
Material confirmed
+
Commercial terms agreed
+
Material dispatched
+
Material delivered
+
Buyer accepted
```

The system should preserve the distinction.

---

## 3. Transaction Lifecycle

A transaction can move through:

```text
Lead
 ↓
Potential Match
 ↓
Commercial Discussion
 ↓
Negotiation
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
Payment / Settlement
 ↓
Completed
```

Possible alternative outcomes:

```text
Cancelled
Supplier Failed
Buyer Cancelled
Quality Rejected
Price Changed
Quantity Short
Logistics Failed
Payment Delayed
Other Failure
```

---

## 4. Transaction ID

Every transaction should receive a unique identifier.

Example:

```text
TXN-2026-0001
```

This makes it easier to connect:

```text
Buyer
Requirement
Supplier
Supply
Shipment
Price
Quality
Payment
```

---

## 5. Core Transaction Record

A basic record could look like:

```yaml
transaction:
  id: TXN-2026-0001

  buyer_id: BUY-001
  supplier_id: SUP-001
  requirement_id: REQ-001

  material:
    family: PP
    form: regrind
    grade: ""

  quantity:
    agreed_mt: 20
    delivered_mt: 19.7

  commercial:
    agreed_price: X
    price_basis: delivered

  status: completed
```

---

## 6. Requirement vs Actual Result

The system should store both:

### Requirement

```text
Buyer requested:
20 MT
```

### Actual

```text
Delivered:
19.7 MT
```

This difference is operationally important.

The same applies to:

- Price
- Quality
- Timing
- Freight
- Payment

---

## 7. Commercial Data

Capture:

```text
Quoted price
Negotiated price
Confirmed price
Final effective price
Price basis
Payment terms
Taxes where applicable
Brokerage / service fee where applicable
Freight
Other agreed costs
```

The exact commercial fields may vary by transaction structure.

---

## 8. Price Evolution

A transaction may have several prices:

```text
Initial indication
      ↓
Supplier quote
      ↓
Negotiated price
      ↓
Confirmed price
      ↓
Final realized price
```

Do not overwrite earlier values.

The history can explain why the economics changed.

---

## 9. Quantity Data

Capture:

```text
Requested quantity
Offered quantity
Confirmed quantity
Loaded quantity
Delivered quantity
Accepted quantity
Rejected quantity
```

Example:

```text
Requested: 20 MT
Confirmed: 20 MT
Loaded: 20 MT
Delivered: 19.7 MT
Accepted: 19.5 MT
```

The differences can reveal logistics or quality issues.

---

## 10. Material Specification

Record the actual material specification:

```yaml
material:
  family: PP
  grade: ""
  form: regrind
  color: mixed

  quality:
    washed: true
    contamination: ""
    moisture: ""
```

Only capture attributes relevant to the material and buyer.

---

## 11. Quality Evidence

Possible quality evidence:

- Supplier description
- Photos
- Videos
- Sample
- Buyer inspection
- Third-party report
- Delivery inspection
- Rejection record

The source of quality information should be stored.

---

## 12. Sample Stage

For uncertain materials, a transaction may involve:

```text
Supplier identified
       ↓
Photos / specification
       ↓
Sample requested
       ↓
Sample received
       ↓
Buyer approval
       ↓
Bulk order
```

The system should record whether a sample was:

```text
Not required
Requested
Received
Approved
Rejected
```

---

## 13. Quality Outcome

After delivery:

```text
Accepted
Partially Accepted
Accepted with Deduction
Rejected
Pending
```

If there is a deduction or rejection, record the reason.

Example:

```yaml
quality_outcome:
  status: accepted_with_deduction
  reason: contamination
  deduction: ""
```

---

## 14. Supplier Performance

A transaction can generate supplier-performance observations.

Potential fields:

```text
Quantity accuracy
Quality consistency
Dispatch reliability
Delivery reliability
Communication
Price adherence
Documentation
```

These should be based on actual events rather than subjective labels.

---

## 15. Buyer Performance

The buyer side can also be tracked.

Potential fields:

```text
Requirement accuracy
Decision speed
Price stability
Inspection process
Payment reliability
Cancellation history
Repeat demand
```

The purpose is operational learning, not arbitrary scoring.

---

## 16. Logistics Data

Capture where useful:

```yaml
logistics:
  origin: Noida
  destination: Ghaziabad

  responsibility:
    transport: supplier

  vehicle:
    type: truck

  freight:
    quoted: X
    actual: Y

  loading:
    date: YYYY-MM-DD

  delivery:
    date: YYYY-MM-DD
```

Actual freight is more valuable than estimated freight.

---

## 17. Timing

Capture:

```text
Requirement date
Supplier availability date
Confirmation date
Loading date
Dispatch date
Expected delivery
Actual delivery
```

This can help identify recurring delays.

---

## 18. Payment Data

Where operationally necessary:

```yaml
payment:
  agreed_terms: ""
  invoice_amount: X
  amount_paid: Y
  payment_status: pending
  payment_date: ""
```

Sensitive financial information should be stored securely.

---

## 19. Failure Reasons

Failed transactions should not simply be marked:

```text
FAILED
```

Instead, record the reason.

Possible reasons:

```text
Price mismatch
Quality mismatch
Quantity unavailable
Supplier backed out
Buyer cancelled
Freight too high
Payment terms mismatch
Delivery delay
Material already sold
Incorrect material description
Rejected after inspection
Communication failure
Other
```

---

## 20. Failure Analysis

Example:

```text
Buyer requirement:
20 MT PP regrind

Supplier:
20 MT available

Initial economics:
Workable

Failure:
Actual contamination higher than expected

Result:
Buyer rejected / revised price
```

This becomes useful learning.

---

## 21. Successful Transaction

A successful transaction might look like:

```text
Buyer requirement
       ↓
Supplier identified
       ↓
Specification confirmed
       ↓
Price agreed
       ↓
Freight confirmed
       ↓
Material loaded
       ↓
Material delivered
       ↓
Quality accepted
       ↓
Payment completed
```

The full chain should ideally be recorded.

---

## 22. Repeat Transactions

A repeat transaction can connect to the previous transaction.

Example:

```text
TXN-0001
   ↓
TXN-0008
   ↓
TXN-0015
   ↓
TXN-0022
```

This allows analysis of recurring relationships.

---

## 23. Recurring Demand

A buyer may require:

```text
20 MT every month
```

Instead of creating one disconnected record every month, the system can eventually maintain:

```text
Recurring Requirement
       ↓
Monthly Requirement
       ↓
Transaction
```

This may help forecast future sourcing work.

---

## 24. Transaction Economics

For each completed deal, the project should eventually be able to understand:

```text
Buyer-side commercial value
-
Supplier-side commercial cost
-
Freight / logistics
-
Operational costs
-
Service / brokerage fee where applicable
=
Contribution / transaction economics
```

The exact accounting treatment depends on the business model.

The purpose is to understand whether the transaction is commercially repeatable.

---

## 25. No Assumed Profit

A quoted buyer price minus supplier price should not automatically be called profit.

There may be:

- Freight
- Taxes
- Brokerage
- Quality deductions
- Payment costs
- Operational expenses
- Rejections
- Working-capital costs

Final economics should be calculated only after relevant costs are known.

---

## 26. Transaction Ledger

A spreadsheet could begin with:

| Field | Example |
|---|---|
| Transaction ID | TXN-2026-0001 |
| Buyer | Buyer A |
| Supplier | Supplier B |
| Material | PP |
| Grade | — |
| Form | Regrind |
| Requested Qty | 20 MT |
| Confirmed Qty | 20 MT |
| Delivered Qty | 19.7 MT |
| Agreed Price | ₹X/kg |
| Price Basis | Delivered |
| Freight | ₹Y |
| Quality Outcome | Accepted |
| Payment Status | Settled |
| Status | Completed |
| Failure Reason | — |

---

## 27. Minimum Viable Transaction Data

At the beginning, capture only:

### Parties

- Buyer
- Supplier

### Material

- Material
- Grade where relevant
- Form
- Quantity

### Commercial

- Agreed price
- Price basis
- Freight where relevant

### Operations

- Pickup location
- Delivery location
- Loading date
- Delivery date

### Outcome

- Quality result
- Accepted quantity
- Payment status
- Success/failure reason

This is enough to begin learning.

---

## 28. Data Source

Each important value should ideally have a source.

Example:

```yaml
agreed_price:
  value: X
  source: buyer_confirmation
  timestamp: YYYY-MM-DD
```

Possible sources:

```text
Buyer message
Supplier message
Quotation
Purchase order
Invoice
Weight slip
Delivery confirmation
Quality report
Human observation
```

---

## 29. AI-Assisted Data Capture

AI can eventually convert conversations into transaction records.

Example:

```text
"20 ton PP regrind final ₹X delivered,
truck loading tomorrow morning."
```

Potential extraction:

```yaml
material: PP
form: regrind
quantity_mt: 20
price: X
basis: delivered
loading_date: tomorrow
```

The system should flag uncertain fields for human confirmation.

---

## 30. Document Extraction

Future workflows could extract data from:

- Quotations
- Purchase orders
- Invoices
- Weighment slips
- Quality reports
- Delivery documents

The extracted data should be linked to the relevant transaction.

---

## 31. Transaction Timeline

A future dashboard could show:

```text
10:00 — Buyer requirement received
11:15 — Supplier identified
12:00 — Price discussed
14:30 — Commercial terms confirmed
Next Day — Loading
+1 Day — Delivery
+1 Day — Quality accepted
+2 Days — Payment settled
```

This makes operational bottlenecks easier to identify.

---

## 32. Transaction-Level Learning

Every transaction can answer:

```text
What worked?
What failed?
What changed?
What caused the delay?
What caused the price difference?
What caused quality issues?
Would we repeat this relationship?
```

These answers should become structured data where practical.

---

## 33. Matching Feedback

Transaction outcomes can improve the matching engine.

Example:

```text
Suggested match
      ↓
Buyer rejected due to quality
      ↓
Record reason
      ↓
Matching rule updated
```

Repeated patterns can eventually inform AI-assisted matching.

---

## 34. Price Intelligence Feedback

Completed transactions can improve price intelligence:

```text
Quoted price
      ↓
Negotiated price
      ↓
Final transaction price
      ↓
Realized economics
```

This provides stronger evidence than an unverified market quote.

---

## 35. Supplier Intelligence Feedback

Repeated transactions can reveal:

```text
Availability consistency
Quality consistency
Price consistency
Delivery reliability
```

This should be based on documented transactions.

---

## 36. Buyer Intelligence Feedback

Similarly:

```text
Recurring demand
Quantity consistency
Specification consistency
Payment behavior
Cancellation patterns
```

Again, the objective is operational intelligence rather than arbitrary scoring.

---

## 37. Transaction Security

Commercial records may contain sensitive information.

The system should protect:

- Phone numbers
- Email addresses
- Exact addresses
- Prices
- Buyer requirements
- Supplier information
- Contracts
- Payment records
- Transaction history

Public GitHub documentation should use synthetic data.

---

## 38. Data Retention

The project should define which records need to be retained for:

- Operational learning
- Accounting
- Compliance
- Customer support
- Commercial disputes

Retention requirements may vary depending on the eventual legal and business structure.

---

## 39. Evaluation Metrics

Early transaction metrics could include:

### Operational

- Time from requirement to supplier
- Time from confirmation to dispatch
- Delivery delay
- Quantity variance

### Commercial

- Quote-to-final-price difference
- Freight variance
- Contribution per transaction
- Repeat transaction rate

### Quality

- Acceptance rate
- Rejection rate
- Deduction rate
- Sample-to-bulk conversion

### Matching

- Relevant match rate
- False-positive rate
- Buyer rejection rate
- Supplier rejection rate

---

## 40. Transaction Dataset

After sufficient activity, the dataset could look conceptually like:

```text
Transaction
├── Buyer
├── Supplier
├── Material
├── Specification
├── Quantity
├── Price
├── Freight
├── Location
├── Timing
├── Quality
├── Payment
├── Outcome
└── Failure / Success Reason
```

This becomes the foundation for future analytics.

---

## 41. What Not to Automate Immediately

The project should not initially automate decisions such as:

- Final quality acceptance
- Price commitment
- Supplier verification
- Buyer approval
- Contract interpretation
- Payment authorization

AI can assist with preparation and analysis, while humans retain commercial control.

---

## 42. Current Operating Approach

The immediate goal is:

```text
Find buyer requirement
      ↓
Find supplier
      ↓
Facilitate transaction
      ↓
Record actual outcome
      ↓
Learn
      ↓
Repeat
```

The system should become more sophisticated only when the data demonstrates what is worth automating.

---

## 43. Long-Term Vision

A mature transaction intelligence layer could connect:

```text
Buyer Demand
      ↓
Supplier Availability
      ↓
Matching
      ↓
Commercial Feasibility
      ↓
Logistics
      ↓
Quality
      ↓
Settlement
      ↓
Historical Learning
```

This could eventually support AI-assisted sourcing and operations.

---

## 44. Core Principle

> **Every real transaction should produce more than revenue or loss; it should produce structured knowledge about material, price, quality, logistics, counterparties and repeatability.**
