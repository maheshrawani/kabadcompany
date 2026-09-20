# AI Use Cases

## Kabad Company — Applying AI to Recyclable-Material Sourcing

**Status:** Early-stage research and experimentation  
**Purpose:** Identify practical AI applications that can improve recycling-material sourcing without replacing human commercial judgment.

---

## 1. Why AI Matters

The recycling and scrap ecosystem contains large amounts of unstructured information.

Examples include:

- WhatsApp messages
- Phone call notes
- Buyer requirements
- Supplier descriptions
- Photos and videos
- Price discussions
- Company websites
- Public directories
- Transaction records
- Logistics information

Much of this information is useful but difficult to organize manually.

AI could help turn this unstructured information into structured operational knowledge.

The goal is not to use AI simply because it is available.

The goal is to identify repetitive tasks where AI can improve:

- Speed
- Information quality
- Research capacity
- Matching
- Documentation
- Follow-up
- Analysis

---

# 2. Guiding Principle

The project follows:

> **Use AI after understanding the workflow, not before.**

A technology solution should be based on a repeated problem observed in the market.

For example:

```text
Repeated buyer messages
        ↓
Manual requirement extraction takes time
        ↓
Define structured fields
        ↓
Test AI extraction
        ↓
Measure accuracy
        ↓
Automate if useful
```

This prevents building technology around assumptions.

---

# 3. AI Opportunity Map

Potential AI applications can be grouped into:

1. Research
2. Requirement extraction
3. Supplier information processing
4. Buyer-supplier matching
5. Conversation intelligence
6. Price and transaction analysis
7. Knowledge management
8. Follow-up automation
9. Document processing
10. Operational decision support

---

# 4. Buyer Requirement Extraction

A buyer may send:

```text
Need 20 ton PP regrind in Ghaziabad.
Should be clean and preferably washed.
Need it this week.
Regular requirement.
```

An AI system could convert this into:

```yaml
material: PP
form: regrind
quantity_mt: 20
location: Ghaziabad
quality:
  clean: true
  washed: preferred
timing: this_week
frequency: recurring
status: qualification_pending
```

The important feature is not just extraction.

The AI should also identify missing information.

For example:

```text
Missing:
- Grade
- Color
- Price basis
- Payment terms
```

---

# 5. Supplier Message Extraction

A supplier may send:

```text
PP ka 15 ton maal hai.
Ghaziabad mein hai.
Photos bhej raha hoon.
Rate 21 hai.
```

AI could extract:

```yaml
material: PP
quantity_mt: 15
location: Ghaziabad
price: 21
price_unit: unknown
price_basis: unknown
photos: available
verification: supplier_reported
```

The system should then flag:

```text
Need clarification:
- ₹21 per what unit?
- Pickup or delivered?
- Grade?
- Form?
- Quality?
```

AI should not fill missing information by guessing.

---

# 6. Conversation Intelligence

With appropriate privacy controls and user consent, AI could summarize commercial conversations.

Example:

```text
Buyer wants:
- 20 MT PP regrind
- Ghaziabad delivery
- Recurring monthly requirement

Pending:
- Grade confirmation
- Sample approval
- Final price

Next action:
Request grade specification and sample requirements.
```

This can reduce the amount of manual CRM work.

Private conversations should never be published in the public repository.

---

# 7. Buyer-Supplier Matching

A future matching system could compare:

### Buyer

```text
PP
20 MT
Regrind
Ghaziabad
Specific quality
₹X/kg delivered
Immediate
Recurring
```

with:

### Supplier

```text
PP
25 MT
Regrind
Noida
Matching quality
₹Y/kg pickup
Available now
Recurring
```

The system could identify this as a potential match and flag the remaining variable:

```text
Freight from Noida → Ghaziabad
```

---

# 8. Matching Should Be Multi-Dimensional

A simple keyword match is insufficient.

Conceptually:

```text
Material compatibility
        +
Grade compatibility
        +
Form compatibility
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
Reliability
        =
Potential Match
```

Different material categories may require different weighting.

These weights should eventually be informed by transaction outcomes.

---

# 9. Missing Information Detection

One of the most useful AI functions may be identifying incomplete requirements.

Example:

```text
Buyer:
"Need HDPE scrap 30 ton."
```

AI response:

```text
Requirement incomplete.

Need to confirm:
1. HDPE grade
2. Form
3. Color
4. Quality
5. Contamination tolerance
6. Delivery location
7. Price basis
8. Required date
9. Recurring quantity
```

This can prevent wasted supplier outreach.

---

# 10. Company Research

AI can help accelerate research into potential buyers and suppliers.

A research workflow could be:

```text
Company Name
      ↓
Industry Identification
      ↓
Products / Manufacturing Activity
      ↓
Possible Material Use
      ↓
Recycling Activity
      ↓
Location
      ↓
Potential Contact
      ↓
Qualification
```

AI-generated research should be checked against reliable sources before being used commercially.

---

# 11. Supplier Discovery

AI can assist with finding potential suppliers by analyzing public information.

Possible sources include:

- Company websites
- Industrial directories
- Public registries
- Industry associations
- LinkedIn
- Search results
- Public business listings

The AI should distinguish:

```text
Found online
```

from:

```text
Verified active supplier
```

These are not equivalent.

---

# 12. Buyer Discovery

The same approach can be used for buyer discovery.

Potential signals:

- Recycled-material manufacturing
- Plastic processing
- Granule production
- Injection moulding
- Extrusion
- Packaging
- Automotive plastics
- Industrial plastic products

The purpose is to identify companies worth contacting and then verify their current purchasing requirements directly.

---

# 13. Research Automation

AI can reduce repetitive research work.

Example:

```text
Research 100 companies
        ↓
Extract:
- Company
- Location
- Industry
- Materials
- Website
- Public contact
- Recycling activity
        ↓
Human verification
        ↓
Qualified prospect list
```

The human verification step is important because public business data can be outdated or inaccurate.

---

# 14. Price Intelligence

As transaction history grows, AI could analyze:

- Supplier prices
- Buyer indications
- Delivered prices
- Freight
- Quantity
- Material grade
- Quality
- Location
- Transaction outcome

The objective would not initially be to produce a single "correct" market price.

Instead, the system could help identify:

- Observed price ranges
- Location differences
- Quality premiums/discounts
- Freight impact
- Recurring patterns
- Unusual quotes

---

# 15. Transaction Failure Analysis

Failed transactions are valuable data.

AI could classify failures into:

```text
Price
Quality
Quantity
Freight
Timing
Payment
Trust
Availability
Specification
Communication
Other
```

Then analyze questions such as:

- Which failure occurs most often?
- Which material has the highest failure rate?
- How often does freight kill an otherwise viable deal?
- Which suppliers consistently meet requirements?
- Which requirements are poorly specified?

This can guide operational improvements.

---

# 16. Knowledge Base

Over time, Kabad Company can build an internal knowledge base containing:

```text
Material Knowledge
+
Buyer Requirements
+
Supplier Knowledge
+
Transaction History
+
Logistics Knowledge
+
Research
+
Operational SOPs
```

AI could use this knowledge base to answer internal questions such as:

> "Which suppliers have previously provided HDPE regrind in NCR?"

or:

> "What information do our buyers usually require before accepting PP?"

---

# 17. AI-Assisted Follow-Up

A future system could identify:

- Buyer requirements that need confirmation
- Suppliers whose availability has expired
- Samples awaiting approval
- Negotiations without a response
- Transactions awaiting settlement
- Recurring requirements approaching their expected purchase cycle

This can reduce missed opportunities.

---

# 18. Document Processing

AI can potentially process non-confidential documents such as:

- Buyer requirement sheets
- Material specifications
- Public company documents
- Test reports
- Public regulatory documents
- Logistics documents
- Internal SOPs

The system could extract structured fields and create summaries.

Sensitive documents should be handled with appropriate access controls.

---

# 19. WhatsApp as an Operational Interface

The initial market may prefer WhatsApp over a complicated procurement platform.

Therefore, a future system could potentially work around existing communication habits.

Conceptually:

```text
Buyer sends WhatsApp message
        ↓
AI extracts requirement
        ↓
Missing information identified
        ↓
Human confirms
        ↓
Supplier network searched
        ↓
Potential matches identified
        ↓
Human reviews
        ↓
Supplier contacted
```

The objective is to improve the existing workflow rather than force every participant into a new application.

---

# 20. Human-in-the-Loop

AI should not independently make important commercial decisions during the early stage.

Human review should remain involved in:

- Material verification
- Quality approval
- Price confirmation
- Supplier qualification
- Buyer qualification
- Final matching
- Transaction confirmation
- Payment decisions

AI should provide recommendations, structure information, and reduce repetitive work.

---

# 21. AI Accuracy Framework

For every AI workflow, Kabad Company should measure:

### Accuracy

Did the AI extract the information correctly?

### Completeness

Did it identify all relevant fields?

### Hallucination rate

Did it invent information?

### Time saved

How much manual work was removed?

### Business impact

Did the workflow improve the chance or speed of completing a transaction?

An AI workflow should only become operationally important if it provides measurable value.

---

# 22. Example AI Pipeline

A future pipeline could look like:

```text
WhatsApp / Email / Form
          ↓
Message Classification
          ↓
Requirement Extraction
          ↓
Missing Information Detection
          ↓
Structured Requirement
          ↓
Supplier Matching
          ↓
Commercial Feasibility
          ↓
Human Review
          ↓
Supplier Outreach
          ↓
Transaction Workflow
          ↓
Outcome Recorded
          ↓
Learning Dataset
```

---

# 23. Learning From Transactions

Every transaction can become training or evaluation data, subject to appropriate privacy and data-use controls.

Example:

```text
Requirement
      ↓
Potential Match
      ↓
Transaction
      ↓
Outcome
```

Over time, the system could learn which characteristics are associated with successful transactions.

This should be done carefully.

Correlation should not automatically be treated as causation.

---

# 24. Technology Stack — Exploration

Potential technologies may include:

- Large language models
- Python
- APIs
- Databases
- Workflow automation
- Web research tools
- WhatsApp-compatible business systems
- Vector search / semantic search
- Structured data pipelines
- Dashboards

The actual technology stack will be selected based on demonstrated workflow requirements.

The project is not committed to a particular vendor or architecture at this stage.

---

# 25. Initial AI Experiments

Early experiments should focus on small, measurable tasks:

### Experiment 1
Convert buyer messages into structured requirements.

### Experiment 2
Identify missing buyer information.

### Experiment 3
Convert supplier messages into structured supply records.

### Experiment 4
Match simple buyer requirements with supplier records.

### Experiment 5
Summarize transaction outcomes.

### Experiment 6
Classify transaction failure reasons.

### Experiment 7
Research and qualify potential companies.

Each experiment should have a clear input, output, and evaluation method.

---

# 26. What AI Should Not Do

The system should not:

- Invent prices
- Invent material specifications
- Claim a supplier is verified without evidence
- Claim a buyer has an active requirement without verification
- Promise a transaction
- Hide important commercial terms
- Replace quality inspection
- Make unsupported claims about companies
- Publish private contact information
- Expose confidential transaction data

AI should improve information flow, not create false certainty.

---

# 27. Long-Term Possibility

If enough data is accumulated, the project could potentially develop:

```text
AI Research Layer
        +
Material Intelligence
        +
Buyer Demand Graph
        +
Supplier Supply Graph
        +
Transaction History
        +
Logistics Intelligence
        +
Matching Engine
        =
Recyclable-Material Intelligence Infrastructure
```

This is a long-term research direction, not a claim about current product capabilities.

---

# 28. Current Status

Kabad Company is currently in the research and validation stage.

AI is being considered as an operational layer that can help:

- Research faster
- Structure information
- Reduce repetitive work
- Improve matching
- Analyze transactions
- Build institutional knowledge

The immediate priority remains understanding real market behavior and executing real transactions.

---

# 29. Success Criteria

An AI workflow will be considered useful if it can demonstrate measurable improvement in one or more areas:

- Reduced research time
- Faster requirement qualification
- Better data completeness
- Faster supplier discovery
- Better potential matches
- Reduced repetitive communication
- Better transaction documentation
- Better understanding of failure reasons
- Increased repeatability of successful workflows

The project will prioritize measurable utility over AI features for their own sake.
