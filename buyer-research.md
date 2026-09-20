# Buyer Research

## Kabad Company — Industrial Buyer Discovery Framework

**Status:** Early-stage research and validation  
**Initial geography:** Delhi-NCR and surrounding industrial markets  
**Initial material focus:** Recyclable plastics

---

## 1. Purpose

Kabad Company is researching the demand side of the recycling ecosystem before attempting to build a technology platform around it.

The objective is to understand how industrial buyers actually purchase recyclable materials, what information they require, how they evaluate suppliers, and why potential transactions succeed or fail.

This document is a working framework for buyer discovery.

It is not a directory of confirmed buyers.

---

## 2. Who Is an Industrial Buyer?

The term "buyer" can represent several different types of organizations.

Potential buyer segments include:

- Plastic recyclers
- Plastic processors
- Reprocessed granule manufacturers
- Compounders
- Injection moulding manufacturers
- Blow moulding manufacturers
- Extrusion companies
- Packaging manufacturers
- Automotive component manufacturers
- Consumer-product manufacturers
- Industrial-product manufacturers
- Waste-processing companies
- Material traders
- Other organizations using recycled feedstock

Different buyer types may have completely different specifications and purchasing behavior.

---

## 3. Buyer Discovery Principle

A company appearing to recycle plastic does not automatically mean it is an active buyer of every plastic type.

Therefore, Kabad Company separates:

**Potential buyer**

from

**Qualified buyer**

from

**Active buyer requirement**

A company should only be treated as an active requirement when there is evidence of a current or recurring need.

---

## 4. Buyer Qualification

A basic buyer qualification record should answer:

```text
Company:
Location:
Industry:
Material required:
Grade:
Form:
Quantity:
Frequency:
Quality requirements:
Price basis:
Delivery location:
Payment terms:
Current sourcing method:
Current supplier situation:
Trial requirement:
Sample requirement:
Decision maker:
Last verified:
```

Not every field will be known during the first conversation.

The objective is to progressively reduce uncertainty.

---

## 5. First Conversation

The initial conversation should focus on understanding the buyer rather than immediately selling material.

Example questions:

### Requirement

1. Which plastic materials do you currently purchase?
2. Which grades do you use?
3. What form do you prefer?
4. What quantity do you typically purchase?
5. Is the requirement one-time or recurring?

### Quality

6. What quality specifications are important?
7. What contamination level is acceptable?
8. Do you require washed material?
9. Do you require a specific color?
10. Do you inspect samples before approval?

### Commercials

11. Do you normally buy on delivered or pickup pricing?
12. What are your usual payment terms?
13. How are quality deductions handled?
14. Is there a trial quantity before recurring supply?

### Logistics

15. Where should material be delivered?
16. What quantity can you receive per shipment?
17. Do you arrange transportation or does the supplier?

### Supplier Relationship

18. Do you currently have regular suppliers?
19. What problems do you face with current suppliers?
20. What would make you consider a new supplier?

These questions are intended to discover the real purchasing process.

---

## 6. Requirement Format

A buyer requirement should eventually be converted into a structured record.

Example:

```yaml
buyer:
  company: Example Recycler
  location: Ghaziabad

requirement:
  material: PP
  grade: buyer_specific
  form: regrind
  quantity_mt: 20
  frequency: monthly

quality:
  washed: required
  contamination: buyer_defined
  color: mixed_allowed

commercial:
  price_basis: delivered
  payment_terms: buyer_defined
  trial_required: true

logistics:
  delivery_location: Ghaziabad
  supplier_transport: possible
```

This is a working data structure, not an industry standard.

---

## 7. Active Requirement vs General Interest

A critical distinction is:

### General Interest

> "We purchase PP."

This is useful background information but not necessarily actionable.

### Active Requirement

> "We currently need 20 MT of PP regrind delivered to Ghaziabad."

This can potentially be matched with available supply.

### Recurring Requirement

> "We need approximately 20 MT every month."

This is more valuable for understanding repeatable demand.

The system should preserve these distinctions.

---

## 8. Buyer Requirement Lifecycle

A requirement can move through several stages:

```text
Discovered
   ↓
Contacted
   ↓
Qualified
   ↓
Requirement Captured
   ↓
Supplier Search
   ↓
Material Offered
   ↓
Sample / Verification
   ↓
Commercial Negotiation
   ↓
Trial Transaction
   ↓
Approved Supplier
   ↓
Recurring Requirement
```

Not every requirement will reach the final stages.

Tracking where requirements stop can reveal operational bottlenecks.

---

## 9. Why Buyer Requirements Fail

Potential failure reasons include:

### Price

The supplier's executable price is higher than the buyer's workable price.

### Quality

The material does not meet the buyer's specification.

### Quantity

The supplier cannot provide the required quantity.

### Logistics

Freight makes the transaction uneconomic.

### Timing

Material is not available when required.

### Payment

Supplier and buyer have incompatible payment expectations.

### Trust

One party is unwilling to transact without additional verification.

### Information

The requirement or material description is incomplete.

### Consistency

A supplier may provide one acceptable load but cannot maintain quality across recurring loads.

These failure reasons should be recorded rather than treated as random deal failures.

---

## 10. Supplier Evaluation From the Buyer's Perspective

A buyer may evaluate a supplier on:

- Material quality
- Consistency
- Quantity
- Price
- Delivery reliability
- Communication
- Documentation
- Payment terms
- Ability to provide recurring supply
- Response speed
- History of previous transactions

The project should investigate which of these factors actually matter most for each material category.

---

## 11. The Importance of Samples

For some materials, a buyer may need to inspect a sample before accepting a larger shipment.

Potential process:

```text
Supplier Identified
       ↓
Material Information
       ↓
Photos / Video
       ↓
Sample
       ↓
Buyer Inspection
       ↓
Approval / Rejection
       ↓
Commercial Agreement
       ↓
Trial Quantity
```

The exact process will vary by buyer and material.

The repository should document real observed workflows as they are discovered.

---

## 12. Buyer Location

Buyer location matters because the commercial price may need to be evaluated on a delivered basis.

For every active requirement, the system should ideally record:

- Buyer city
- Industrial area
- Delivery location
- Expected quantity
- Preferred vehicle or shipment size
- Receiving constraints
- Delivery frequency

Exact private addresses and personal contact details should not be published in this public repository.

---

## 13. Pricing Information

Kabad Company will distinguish between:

### Market indication

A broad or informal price observation.

### Buyer indication

A price communicated by a buyer for a specified material and condition.

### Supplier offer

A price offered by a supplier.

### Executable price

A price that appears commercially viable after considering:

- Material quality
- Quantity
- Freight
- Payment terms
- Deductions
- Other transaction costs

This distinction is important because a quoted price is not automatically a completed transaction price.

---

## 14. Buyer Research Database

A future internal database could contain:

| Field | Purpose |
|---|---|
| Company | Identify buyer |
| Industry | Understand application |
| Location | Estimate logistics |
| Materials | Understand demand |
| Grades | Capture specifications |
| Quantity | Measure demand |
| Frequency | Identify recurring demand |
| Price basis | Understand commercials |
| Quality | Understand acceptance |
| Payment terms | Evaluate transaction fit |
| Sample process | Understand qualification |
| Current supplier | Understand switching difficulty |
| Pain points | Identify opportunity |
| Last verified | Prevent stale requirements |
| Status | Track relationship |

The public repository will use anonymized examples rather than private commercial records.

---

## 15. Buyer Discovery Channels

Potential buyer discovery can involve:

- Public company websites
- Industrial directories
- Manufacturing directories
- Recycling registries
- Trade associations
- Industry events
- LinkedIn
- Business networks
- Referrals
- Existing relationships
- Direct outreach
- Public procurement information where relevant

Publicly available information should be verified before being treated as current.

---

## 16. Researching a Buyer

A structured research process can be:

```text
Company Identified
       ↓
Verify Company Exists
       ↓
Understand Industry
       ↓
Identify Materials Used
       ↓
Identify Recycling / Processing Activity
       ↓
Find Relevant Contact
       ↓
Ask About Current Requirements
       ↓
Record Requirement
       ↓
Verify Date
```

The final step is important because public information can become outdated.

---

## 17. Buyer Demand Map

Over time, Kabad Company aims to build a non-public demand map showing:

```text
Material
   ↓
Grade
   ↓
Buyer
   ↓
Location
   ↓
Quantity
   ↓
Frequency
   ↓
Quality
   ↓
Price Basis
```

This could eventually become one of the inputs for an automated matching system.

---

## 18. Matching Concept

A future matching engine should not simply match:

> "PP" → "PP"

It should evaluate multiple dimensions.

Conceptually:

```text
Material compatibility
        +
Grade compatibility
        +
Quality compatibility
        +
Quantity compatibility
        +
Location compatibility
        +
Price compatibility
        +
Timing compatibility
        +
Supplier reliability
        =
Potential match
```

The weights of these variables should be learned from actual transaction outcomes rather than assumed in advance.

---

## 19. Questions We Are Trying to Answer

Buyer research should help answer:

1. Which material categories have recurring demand?
2. Which grades are most frequently requested?
3. How much quantity is typically purchased?
4. What makes a buyer try a new supplier?
5. How important are samples?
6. How important is price versus consistency?
7. How much does freight affect sourcing decisions?
8. What payment terms are common?
9. What causes supplier rejection?
10. Which buyer requirements can be standardized?
11. Which requirements remain highly buyer-specific?
12. Which parts of the process can realistically be automated?

---

## 20. Validation Rules

A buyer requirement should not be presented as confirmed simply because a company once mentioned that it buys a material.

Before treating a requirement as actionable, we should try to verify:

- Material
- Quantity
- Quality
- Location
- Timing
- Price basis
- Current status

The date of verification should be recorded.

---

## 21. Research Ethics & Privacy

This project involves commercial relationships.

We will not publish:

- Private phone numbers
- Personal email addresses
- Private WhatsApp conversations
- Confidential pricing agreements
- Customer databases
- Private contracts
- Sensitive commercial information

Public research should focus on the structure of the market and anonymized learnings.

---

## 22. Current Status

Buyer research is ongoing.

The current objective is to move from a list of potential companies to a smaller set of **verified, active, and recurring material requirements**.

The project will prioritize evidence from direct conversations and real transaction attempts over assumptions based only on company descriptions.

---

## 23. Next Research Step

The next stage is to build structured buyer profiles and document recurring requirements by:

- Material
- Grade
- Quantity
- Location
- Frequency
- Quality
- Commercial terms
- Transaction outcome

This dataset can later be used to test whether AI-assisted sourcing and material matching can create measurable operational value.
