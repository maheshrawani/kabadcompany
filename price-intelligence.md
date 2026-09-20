# Price Intelligence

## Kabad Company — Price Discovery and Commercial Intelligence Framework

**Status:** Early-stage research and validation  
**Purpose:** Define how Kabad Company can collect, normalize, understand and eventually use recyclable-material price information without pretending that a single quoted price represents the entire market.

---

## 1. Why Price Intelligence Matters

In recyclable-material sourcing, a quoted price is rarely meaningful by itself.

A useful price record may depend on:

- Material
- Grade
- Form
- Quality
- Color
- Quantity
- Location
- Pickup or delivered basis
- Freight
- Payment terms
- Loading conditions
- Date
- Buyer requirements
- Supplier reliability

Therefore:

> **Price should be treated as a commercial observation with context, not as a universal market fact.**

---

## 2. Price Discovery Problem

Different participants may quote:

```text
Supplier:
₹X/kg pickup

Recycler:
₹Y/kg delivered

Trader:
₹Z/kg

Buyer:
₹A/kg for accepted quality
```

These values cannot be compared directly without understanding the commercial basis.

The system should normalize the context before drawing conclusions.

---

## 3. Core Price Record

A basic price observation could look like:

```yaml
price_observation:
  id: PRICE-001

  material:
    family: PP
    grade: ""
    form: regrind
    quality: ""

  price:
    value: X
    currency: INR
    unit: kg

  basis:
    type: pickup
    location: Noida

  quantity:
    value: 10
    unit: MT

  date:
    quoted_on: YYYY-MM-DD

  source:
    type: supplier_quote
    verification: supplier_reported
```

The original source should be retained whenever possible.

---

## 4. Price Is Time-Sensitive

A price observed today should not automatically be presented as the current market price tomorrow.

For every price, capture:

```text
Date
Time where useful
Material
Location
Quantity
Quality
Price basis
Source
```

This allows historical comparisons without confusing old observations with current quotes.

---

## 5. Price Types

The system should distinguish different types of prices.

### Indicative Price

A preliminary indication before detailed negotiation.

### Quoted Price

A supplier or buyer has provided a specific commercial number.

### Negotiated Price

A price reached during commercial discussion.

### Confirmed Transaction Price

The agreed price for an actual transaction.

### Final Realized Price

The effective price after delivery, quality adjustment, rejection, deductions or other commercial changes.

These are not interchangeable.

---

## 6. Final Realized Economics

A transaction may start with:

```text
Quoted price = ₹X/kg
```

But final economics may include:

```text
Quoted price
+ Freight
+ Loading/unloading
+ Handling
- Quality deduction
- Rejection
- Other agreed adjustments
```

The final effective economics should be recorded separately from the initial quote.

---

## 7. Pickup vs Delivered Price

Two common commercial bases:

```text
Pickup price
```

means the quoted price applies at the supplier location.

```text
Delivered price
```

means the quote includes delivery to the buyer's location under the agreed terms.

A matching system should not compare these directly without accounting for freight.

---

## 8. Freight-Aware Price

A simplified model:

```text
Delivered Cost
=
Material Price
+
Freight
+
Applicable Handling Costs
```

Example:

```text
Supplier quote: ₹X/kg pickup
Estimated freight: ₹Y/kg

Estimated delivered economics:
₹(X + Y)/kg
```

This is an illustration, not a market quote.

Actual freight should be confirmed before a transaction is finalized.

---

## 9. Quantity Effects

Price can vary with quantity.

For example:

```text
2 MT
10 MT
25 MT
100 MT
```

may not receive the same commercial terms.

Therefore, every price observation should capture quantity where available.

---

## 10. Quality Effects

Two loads of the same material family may have different economics because of:

- Contamination
- Moisture
- Color
- Form
- Washing
- Sorting
- Grade
- Packaging
- Consistency

Therefore:

```text
PP ≠ one universal PP price
```

The commercial specification must be recorded.

---

## 11. Location Effects

The same material may have different workable economics in:

- Delhi
- Ghaziabad
- Noida
- Greater Noida
- Faridabad
- Meerut
- Other markets

Location affects:

- Local demand
- Supply availability
- Freight
- Competition
- Buyer density
- Supplier density

Price observations should therefore include geography.

---

## 12. Price Bands

Once sufficient observations exist, the project could explore price ranges instead of publishing a single number.

Example:

```text
Observed quotes:
₹X
₹Y
₹Z

Potential observed range:
₹X–₹Z/kg
```

The range should include:

- Date
- Material specification
- Location
- Sample size

A small number of quotes should not be presented as a statistically representative market price.

---

## 13. Transaction-Backed Prices

The most valuable price records are likely to come from completed transactions because they contain more commercial context.

Potential hierarchy:

```text
Completed transaction
        ↑
Confirmed commercial quote
        ↑
Negotiated indication
        ↑
General market statement
```

This is a data-quality framework, not a universal ranking of market prices.

---

## 14. Supplier Price History

A supplier record could accumulate:

```text
Supplier
 ↓
Material
 ↓
Date
 ↓
Quoted price
 ↓
Final transaction price
 ↓
Quality outcome
```

This can reveal whether a supplier's quoted price is generally close to realized transaction economics.

---

## 15. Buyer Price History

Similarly:

```text
Buyer
 ↓
Material
 ↓
Specification
 ↓
Date
 ↓
Buying indication
 ↓
Confirmed purchase
 ↓
Final realized price
```

This can help identify recurring demand and changing requirements.

---

## 16. Price Spread

In a sourcing transaction, there may be:

```text
Buyer workable price
-
Supplier workable price
=
Commercial spread
```

But the spread may need to cover:

- Brokerage
- Freight coordination
- Quality risk
- Payment risk
- Operational effort
- Taxes or transaction costs where applicable

The spread should therefore not automatically be treated as profit.

---

## 17. Transparent Commercial Model

Kabad Company may initially operate as a sourcing or brokerage facilitator.

A transparent structure could be:

```text
Buyer requirement
      ↓
Buyer buying indication
      ↓
Supplier offers material
      ↓
Commercial terms clarified
      ↓
Supplier agrees to supply
      ↓
Transaction coordinated
```

The exact commercial model should be tested through real transactions.

---

## 18. Avoiding False Price Promises

A supplier should not be told:

> "We can definitely sell your material for ₹X."

unless there is a confirmed buyer commitment under those terms.

A safer commercial communication is:

> "Current buyer buying indication is around ₹X/kg, subject to material quality, quantity, location and final confirmation."

This preserves accuracy.

---

## 19. Price Verification

A future price record can include:

```yaml
verification:
  status: supplier_reported

  evidence:
    - whatsapp_message
    - quotation
    - purchase_order
    - completed_transaction

  verified_by:
    type: human
```

The evidence level should remain visible.

---

## 20. Price Changes

A quote can change because of:

- Buyer requirement changes
- Quality differences
- Supply availability
- Freight changes
- Market movement
- Quantity changes
- Payment terms
- Negotiation

The system should record changed quotes rather than overwriting history.

---

## 21. Price Timeline

Example:

```text
01 Sep — Indicative quote
       ↓
03 Sep — Negotiated quote
       ↓
05 Sep — Confirmed transaction
       ↓
07 Sep — Delivery
       ↓
07 Sep — Quality adjustment
       ↓
08 Sep — Final realized economics
```

This provides a much richer view than a single price field.

---

## 22. Market Price Database

A future internal database might contain:

```text
Date
Material
Grade
Form
Quality
Location
Quantity
Price
Price basis
Freight
Buyer/Supplier type
Source
Verification
Transaction status
```

This could eventually support internal price intelligence.

---

## 23. Price Normalization

Before comparing observations, normalize:

### Unit

```text
kg
MT
```

### Currency

```text
INR
```

### Basis

```text
Pickup
Delivered
```

### Quantity

```text
Actual / quoted quantity
```

### Material

```text
Standardized category
```

### Date

```text
Timestamped observation
```

---

## 24. Price Intelligence Should Be Contextual

A future dashboard could show:

```text
Material:
PP Regrind

Region:
Delhi NCR

Observed period:
Recent data window

Observed quotes:
Range

Transaction-backed observations:
Count

Last confirmed transaction:
Date

Average / median:
Only where sufficient data exists
```

The dashboard should clearly distinguish observation from statistical inference.

---

## 25. Confidence

A future price intelligence system could assign a confidence state based on evidence such as:

```text
Source quality
+
Recency
+
Number of observations
+
Transaction confirmation
+
Specification consistency
```

This should be treated as a data-quality indicator rather than a claim of exact market truth.

---

## 26. AI Price Extraction

AI could extract commercial information from messages such as:

> "HDPE regrind 15 ton, ₹X pickup, loading tomorrow."

Potential structured extraction:

```yaml
material: HDPE
form: regrind
quantity_mt: 15
price: X
basis: pickup
availability: tomorrow
```

A human should be able to review or correct the extraction.

---

## 27. AI Price Comparison

AI could help answer:

```text
Compare today's supplier quotes for PP regrind in Noida.
```

The system could normalize:

- Quantity
- Price basis
- Material specification
- Location
- Date

and present the observations.

It should not silently invent missing freight or quality information.

---

## 28. Freight Intelligence

Over time, transaction records could support internal estimates for:

```text
Origin
+
Destination
+
Material quantity
+
Vehicle type
+
Actual freight
```

This may eventually improve delivered-cost estimation.

Initial estimates should remain explicitly labeled as estimates.

---

## 29. Failed Price Matches

Failed transactions are useful.

Example:

```text
Buyer workable price: X
Supplier expected price: Y

Difference:
Not commercially workable
```

Record:

- Buyer price
- Supplier price
- Freight
- Quality
- Quantity
- Final outcome

Repeated failures may reveal a market gap or a mismatch in specifications.

---

## 30. Price Discovery Workflow

A practical workflow:

```text
Buyer Requirement
       ↓
Determine Specification
       ↓
Collect Supplier Quotes
       ↓
Normalize Price Basis
       ↓
Estimate Freight
       ↓
Check Quality
       ↓
Calculate Commercial Feasibility
       ↓
Present Options
       ↓
Negotiate
       ↓
Confirm
       ↓
Record Final Transaction
```

---

## 31. Data Sources

Potential internal sources:

- Buyer conversations
- Supplier conversations
- Quotations
- Purchase orders
- Invoices
- Delivery records
- Quality reports
- Completed transactions
- Freight records

External research can provide context, but actual transaction data should remain clearly separated from external market estimates.

---

## 32. Data Freshness

A price intelligence system should consider:

```text
Fresh
Recent
Aged
Expired
```

The exact time windows should vary by material and market.

A volatile market may require more frequent updates than a stable one.

---

## 33. No Universal Market Price

One of the core principles is:

> **There may be no single correct price for a recyclable material.**

Instead, there may be a set of commercially different prices depending on:

```text
Specification
+
Location
+
Quantity
+
Quality
+
Timing
+
Price basis
+
Counterparty
```

The system should preserve this complexity rather than flattening it prematurely.

---

## 34. Initial Manual System

The first version can be a spreadsheet containing:

| Date | Material | Grade | Form | Quality | Qty | Location | Price | Basis | Source | Status |
|---|---|---|---|---|---:|---|---:|---|---|---|

Additional transaction fields can be added later.

The objective is to prove that collecting this data creates useful decisions.

---

## 35. What Not to Build Yet

The project does not currently need:

- A public price index
- Automated market-price publishing
- High-frequency price prediction
- Complex financial models
- Automated supplier bidding
- Guaranteed price recommendations

These should only be considered after sufficient real transaction data exists.

---

## 36. Long-Term Possibilities

If enough high-quality transaction data accumulates, future systems could explore:

```text
Historical price intelligence
+
Delivered-cost estimation
+
Demand signals
+
Supply signals
+
Quality outcomes
+
AI-assisted commercial analysis
```

This could become a useful internal decision-support layer.

---

## 37. Evaluation

Price intelligence should eventually be evaluated by:

- Accuracy of recorded quotes
- Freshness
- Number of verified observations
- Difference between quoted and realized price
- Freight-estimation error
- Time saved during sourcing
- Improvement in transaction feasibility assessment

The goal is better commercial decisions, not simply more data.

---

## 38. Privacy

Commercial price information can be sensitive.

Public project documentation should use:

- Synthetic prices
- Anonymized companies
- Placeholder quantities
- Redacted contacts

Real commercial records should remain private.

---

## 39. Current Status

Price intelligence is currently a research and operating framework.

The immediate goal is to collect real observations during sourcing and completed transactions.

The project should first learn:

```text
What information actually changes a buying decision?
```

before building sophisticated pricing software.

---

## 40. Core Principle

> **A useful price is not just a number. It is a number attached to a material specification, quantity, location, quality, commercial basis, date and evidence.**
