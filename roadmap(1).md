# Roadmap

## Kabad Company — Six-Month Validation and Build Roadmap

**Status:** Initial project roadmap  
**Time horizon:** Six months  
**Approach:** Manual-first validation → structured data → selective automation → AI-assisted operations

---

## 1. Roadmap Philosophy

Kabad Company should not begin by trying to build a large recycling marketplace.

The project should progress in this order:

```text
Market Understanding
        ↓
Real Transactions
        ↓
Transaction Data
        ↓
Repeatable Workflow
        ↓
Automation
        ↓
AI-Assisted Intelligence
        ↓
Scalable Product
```

The purpose of the first six months is to determine which parts of this model deserve deeper investment.

---

## 2. Six-Month Objective

By the end of the initial six-month period, the project should aim to have:

- A clearer understanding of the target recycling market
- A network of relevant buyers and suppliers
- Real transaction experience
- A structured transaction dataset
- A tested sourcing workflow
- Early price intelligence
- Evidence about recurring demand
- Initial automation experiments
- A clearer business model hypothesis
- A decision about what should be built next

The objective is **validation**, not premature scale.

---

# Phase 1 — Market and Network Validation

## Month 1

### Primary Objective

Understand the market directly and build the first useful network.

### Activities

#### Buyer discovery

Identify and speak with:

- Plastic recyclers
- Plastic processors
- Compounders
- Manufacturers using recycled feedstock
- Scrap purchasers
- Industrial buyers

Capture:

```text
Material
Grade
Form
Quality
Quantity
Location
Price basis
Frequency
Payment terms
```

### Supplier discovery

Build relationships with:

- Scrap dealers
- Aggregators
- Collection networks
- Local material suppliers
- Industrial scrap generators

Capture:

```text
Material
Quantity
Location
Quality
Expected price
Availability
Frequency
```

### Geography

Initial focus can remain concentrated around:

```text
Delhi NCR
Ghaziabad
Noida
Greater Noida
Faridabad
Western Uttar Pradesh
```

The geography can expand only after the initial market shows repeatable economics.

---

## Month 1 Deliverables

```text
Buyer database
Supplier database
Material taxonomy
Buyer requirement format
Supplier onboarding format
Transaction tracking sheet
Initial price observations
```

### Key Question

> Can we consistently find real buyer requirements and credible supply?

---

# Phase 2 — First Transactions

## Month 2

### Primary Objective

Move from conversations to actual commercial activity.

The workflow becomes:

```text
Buyer Requirement
       ↓
Supplier Search
       ↓
Material Qualification
       ↓
Commercial Feasibility
       ↓
Buyer Confirmation
       ↓
Transaction
```

### Operating Principle

Do not optimize for the number of contacts.

Optimize for:

```text
Useful requirements
+
Credible supply
+
Completed transactions
```

---

## Month 2 Data Capture

For every serious opportunity, record:

- Buyer
- Supplier
- Material
- Quantity
- Quality
- Price
- Price basis
- Freight
- Location
- Timing
- Outcome
- Failure reason

---

## Month 2 Deliverables

```text
First completed transactions
First transaction dataset
Initial supplier reliability observations
Initial buyer-demand observations
Initial price intelligence
Failure analysis
```

### Key Question

> Can the project repeatedly facilitate transactions that make commercial sense?

---

# Phase 3 — Process Validation

## Month 3

### Primary Objective

Identify the repeatable operating process.

By this stage, compare transactions and ask:

```text
Where do deals usually fail?
What information is missing?
Which materials move most easily?
Which buyers repeat?
Which suppliers repeat?
Where does freight destroy economics?
Which quality issues cause rejection?
```

---

## Process Standardization

Convert successful patterns into SOPs.

Potential SOPs:

```text
Buyer onboarding
Requirement qualification
Supplier onboarding
Material qualification
Supplier outreach
Price negotiation
Match review
Transaction confirmation
Logistics coordination
Quality confirmation
Settlement
Post-transaction review
```

---

## Matching Prototype

Build a basic rule-based matching process:

```text
Buyer requirement
      ↓
Filter material
      ↓
Filter grade/form
      ↓
Filter quantity
      ↓
Filter location
      ↓
Check quality
      ↓
Check price
      ↓
Human review
```

No complex AI model is required yet.

---

## Month 3 Deliverables

```text
Validated operating workflow
Transaction SOP
Matching prototype
Structured transaction database
Failure taxonomy
Initial repeat-buyer list
Initial repeat-supplier list
```

### Key Question

> Which parts of the sourcing workflow are actually repeatable?

---

# Phase 4 — Data and Automation

## Month 4

### Primary Objective

Automate repetitive work without automating commercial responsibility.

---

## First Automation Candidates

### 1. Requirement extraction

Convert buyer messages into structured requirements.

### 2. Supplier message extraction

Convert supplier messages into supply records.

### 3. Research

Assist with company and buyer/supplier research.

### 4. Follow-ups

Generate reminders for pending conversations.

### 5. Data entry

Automatically populate structured records after human review.

---

## Example

Input:

> "Need 20 ton PP regrind delivered Ghaziabad around ₹X."

Potential structured record:

```yaml
material: PP
form: regrind
quantity_mt: 20
delivery_city: Ghaziabad
price_indication: X
status: clarification_required
```

The system can then ask for missing information.

---

## Month 4 Deliverables

```text
AI-assisted requirement extraction
AI-assisted supplier extraction
Research workflow
Follow-up automation
Structured operational database
Basic dashboard / reporting
```

### Key Question

> Can automation reduce repetitive work without reducing accuracy?

---

# Phase 5 — Intelligence Layer

## Month 5

### Primary Objective

Use accumulated transaction data to improve sourcing decisions.

---

## Price Intelligence

Analyze:

```text
Material
Grade
Form
Location
Quantity
Quality
Price
Freight
Date
Transaction outcome
```

The objective is to understand commercial patterns rather than publish an assumed universal market price.

---

## Supplier Intelligence

Track observed:

```text
Availability
Quality consistency
Price consistency
Delivery reliability
Transaction history
```

---

## Buyer Intelligence

Track:

```text
Recurring requirements
Material demand
Quantity
Frequency
Quality requirements
Location
Transaction history
```

---

## Matching Intelligence

The system can begin experimenting with:

```text
Requirement
+
Supply
+
Price
+
Freight
+
Quality
+
History
```

to identify potentially useful matches.

Human review remains part of the process.

---

## Month 5 Deliverables

```text
Price intelligence prototype
Supplier intelligence
Buyer demand intelligence
Improved matching workflow
Transaction analytics
Recurring-demand detection
```

### Key Question

> Does accumulated data actually improve sourcing decisions?

---

# Phase 6 — Business Model and Product Decision

## Month 6

### Primary Objective

Decide what Kabad Company should become based on evidence.

Possible directions include:

```text
Brokerage / Sourcing Service
        OR
Managed Procurement
        OR
Material Aggregation
        OR
Recycled Material Trading
        OR
B2B Marketplace
        OR
Sourcing Intelligence Platform
        OR
Combination of models
```

The project should not decide this purely from theory.

The decision should come from transaction evidence.

---

## Business Model Evaluation

Evaluate:

### Demand

- How frequently do buyers require material?
- Which materials have recurring demand?
- How predictable is demand?

### Supply

- How fragmented is supply?
- How reliable are suppliers?
- Can quality be standardized?

### Economics

- What gross spread or service fee is achievable?
- What costs reduce contribution?
- Does freight make deals unworkable?
- Are transactions repeatable?

### Operations

- How much human effort is required per transaction?
- Which tasks can be automated?
- Which tasks require human judgment?

### Retention

- Do buyers return?
- Do suppliers return?
- Do relationships become recurring?

---

# Six-Month Milestones

A simplified view:

```text
MONTH 1
Market + Network
      ↓
MONTH 2
Transactions
      ↓
MONTH 3
Process Validation
      ↓
MONTH 4
Automation
      ↓
MONTH 5
Intelligence
      ↓
MONTH 6
Business Model Decision
```

---

# Core Metrics

## Network Metrics

Track:

```text
Qualified buyers
Qualified suppliers
Active requirements
Active supply records
```

Avoid using raw contact count as the main measure of progress.

---

## Transaction Metrics

Track:

```text
Transactions initiated
Transactions completed
Transaction value
Repeat transactions
Failure rate
Average time to completion
```

---

## Matching Metrics

Track:

```text
Potential matches
Relevant matches
Buyer-approved matches
Supplier-approved matches
Completed matches
False positives
False negatives
```

---

## Quality Metrics

Track:

```text
Accepted loads
Rejected loads
Quality deductions
Sample approval rate
Quality-related failures
```

---

## Commercial Metrics

Track:

```text
Quoted price
Confirmed price
Final realized price
Freight
Transaction costs
Contribution
Repeatability
```

---

# Weekly Operating Rhythm

A practical weekly cycle:

## Monday

Review:

```text
Active buyer requirements
Active supplier availability
Pending transactions
```

## Tuesday–Thursday

Focus on:

```text
Supplier sourcing
Buyer conversations
Negotiation
Transaction execution
```

## Friday

Review:

```text
Completed transactions
Failed opportunities
Price observations
Quality issues
```

## Weekend / Weekly Review

Analyze:

```text
What worked?
What failed?
What should change?
What should be automated?
```

The exact cadence can evolve with workload.

---

# Monthly Review

At the end of each month, answer:

### Market

```text
What did we learn about demand?
What did we learn about supply?
```

### Economics

```text
Which transactions made commercial sense?
```

### Operations

```text
Where did time get wasted?
```

### Data

```text
Which fields were useful?
Which fields were unnecessary?
```

### Product

```text
What should become software?
```

---

# Decision Gates

The project should use evidence-based decision gates.

## Gate 1

Do real buyer requirements exist?

If not:

```text
Improve buyer discovery.
```

---

## Gate 2

Can suppliers fulfill requirements?

If not:

```text
Improve supplier network or change material/geography.
```

---

## Gate 3

Can transactions work commercially?

If not:

```text
Investigate price, quality, freight and terms.
```

---

## Gate 4

Are transactions repeatable?

If not:

```text
Do not scale technology prematurely.
```

---

## Gate 5

Does data improve decisions?

If yes:

```text
Increase investment in intelligence and automation.
```

---

# Technology Roadmap

## Stage 1

```text
WhatsApp
+
Google Sheets
+
Human research
```

## Stage 2

```text
Structured database
+
n8n
+
AI extraction
```

## Stage 3

```text
Dashboard
+
Matching
+
Price intelligence
```

## Stage 4

```text
AI-assisted sourcing
+
Automated workflows
+
Operational intelligence
```

## Stage 5

Potentially:

```text
B2B platform
+
Network effects
+
Advanced intelligence
```

Stage 5 is a future possibility, not a current commitment.

---

# AI Roadmap

AI capabilities can evolve gradually.

### Level 1 — Assist

```text
Research
Summaries
Data formatting
```

### Level 2 — Extract

```text
Requirements
Supplier offers
Prices
Transaction data
```

### Level 3 — Recommend

```text
Potential matches
Follow-ups
Research priorities
```

### Level 4 — Orchestrate

```text
Multi-step workflows
Data updates
Notifications
```

### Level 5 — Optimize

Potential future research:

```text
Demand forecasting
Supply forecasting
Commercial analysis
Network intelligence
```

The system should progress only when earlier levels are reliable.

---

# Risk Management

## Risk: Low-Quality Data

Response:

```text
Capture source + timestamp + verification status.
```

## Risk: Supplier Bypass

Response:

```text
Build trusted relationships
+
provide genuine sourcing value
+
protect sensitive commercial information.
```

## Risk: Price Volatility

Response:

```text
Use timestamped price observations.
```

## Risk: Quality Rejection

Response:

```text
Improve specification and verification.
```

## Risk: Freight Economics

Response:

```text
Calculate delivered economics before confirmation.
```

## Risk: Overbuilding Technology

Response:

```text
Validate manually first.
```

## Risk: Marketplace Liquidity

Response:

```text
Focus on a narrow material/geography/problem before broad expansion.
```

---

# What Success Looks Like After Six Months

Success does not necessarily mean:

```text
A large app
Thousands of users
A public marketplace
Large technology team
```

A successful validation could instead look like:

```text
Real buyers
+
Real suppliers
+
Real transactions
+
Repeat demand
+
Documented economics
+
Structured data
+
Useful automation
+
Clear next business model
```

That would provide a stronger foundation for the next stage.

---

# Long-Term Possibilities

If the six-month validation produces strong evidence, Kabad Company could potentially evolve toward:

```text
Industrial sourcing network
        ↓
Material intelligence
        ↓
Verified supply network
        ↓
AI-assisted matching
        ↓
Logistics coordination
        ↓
Transaction infrastructure
```

Eventually, the platform could potentially support multiple recyclable-material categories.

However, expansion should follow demonstrated demand and operational capability.

---

# Research Questions for the Next Stage

The project should continue investigating:

1. Which materials have the strongest recurring industrial demand?
2. Which specifications are hardest for buyers to source?
3. Where are the largest supply gaps?
4. Which geographic corridors have workable freight economics?
5. What causes the most transaction failures?
6. Which supplier attributes predict successful transactions?
7. Which buyer requirements are most predictable?
8. What information is most valuable for price discovery?
9. Which manual tasks consume the most time?
10. Which automation produces measurable operational value?
11. Which business model produces sustainable transaction economics?
12. Which parts of the network become defensible over time?

---

# Current Project Position

Kabad Company is currently positioned as an **early-stage market-validation project**.

The immediate priority is:

```text
Learn
→ Transact
→ Record
→ Analyze
→ Automate
→ Repeat
```

The project should remain flexible about its final form until enough evidence has been collected.

---

# Core Principle

> **Do not build the company we imagine. Build the system that real transactions prove is needed.**
