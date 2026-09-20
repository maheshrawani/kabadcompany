# Automation Architecture

## Kabad Company — AI, Automation and Operations Architecture

**Status:** Early-stage research and validation  
**Purpose:** Explore how repetitive sourcing, research, communication, data capture and transaction workflows could eventually be automated while keeping important commercial decisions under human control.

---

## 1. Automation Philosophy

Kabad Company is intentionally starting with manual execution.

The initial workflow is:

```text
Human discovers requirement
        ↓
Human finds suppliers
        ↓
Human coordinates transaction
        ↓
Data is recorded
        ↓
Patterns are identified
        ↓
Automation is introduced where useful
```

The objective is not to automate everything.

The objective is to automate **repetitive work after the underlying process is understood**.

---

## 2. Why Manual-First

A recycling transaction can contain many variables:

- Material
- Grade
- Quality
- Quantity
- Price
- Freight
- Location
- Timing
- Payment
- Buyer acceptance

Automating an unclear process can make mistakes happen faster.

Manual execution allows the project to discover:

```text
What actually happens?
What information matters?
Where do transactions fail?
What work is repetitive?
What requires human judgment?
```

---

## 3. Potential Automation Layers

A future architecture could contain:

```text
Communication
      ↓
Data Extraction
      ↓
Structured Database
      ↓
Matching
      ↓
Research
      ↓
Human Review
      ↓
Communication
      ↓
Transaction
      ↓
Analytics
```

---

## 4. Communication Layer

Potential channels:

- WhatsApp
- Email
- Phone
- Web forms
- Internal dashboard
- Supplier/buyer portal

The first operating environment may remain heavily WhatsApp-based because many market participants already use it.

---

## 5. Message Intake

Example supplier message:

> "PP regrind 15 ton available in Noida. Rate around ₹X. Can load tomorrow."

An AI workflow could identify:

```yaml
material: PP
form: regrind
quantity_mt: 15
location: Noida
price: X
availability: tomorrow
```

The extracted information should be flagged as AI-extracted until confirmed.

---

## 6. Requirement Extraction

Buyer messages may be similarly structured.

Example:

> "Need 20 ton washed PP regrind, delivery Ghaziabad, looking around ₹X."

Potential extraction:

```yaml
material: PP
form: regrind
washed: true
quantity_mt: 20
delivery_city: Ghaziabad
price_indication: X
```

The system should identify missing information rather than inventing it.

---

## 7. Missing Information Detection

AI could ask:

```text
Missing:
- Grade
- Color
- Contamination specification
- Required delivery date
```

Instead of allowing the workflow to proceed with incomplete information.

This could reduce avoidable mismatches.

---

## 8. Normalization

Different people may use different terminology:

```text
PP scrap
PP regrind
Polypropylene scrap
PP maal
```

AI could normalize the language into a common internal taxonomy.

However, the original message should remain available.

---

## 9. Supplier Research Automation

Given a company name, future workflows could assist with:

```text
Company identification
Location
Material categories
Public website
Public contact information
Industry
Capabilities
Potential buyer/supplier role
```

Research results should be separated into:

```text
Verified information
Source-reported information
AI interpretation
Unknown
```

---

## 10. Buyer Research Automation

Similarly, a workflow could help identify potential industrial buyers by researching:

- Recycling facilities
- Plastic processors
- Compounders
- Manufacturers
- Scrap purchasers
- Industrial users

The objective is to accelerate research, not automatically declare that a company is an active buyer.

---

## 11. Research Agent

A future research agent could receive:

```text
"Find potential PP buyers in Delhi-NCR."
```

and produce:

```text
Company
Location
Potential material
Source
Public contact
Reason for relevance
Verification status
```

A human should review the list before outreach.

---

## 12. Buyer Requirement Workflow

A future automated sequence:

```text
Buyer message
      ↓
AI extraction
      ↓
Requirement record
      ↓
Missing fields check
      ↓
Human confirmation
      ↓
Supplier search
      ↓
Potential matches
```

This connects directly with `buyer-requirement-workflow.md`.

---

## 13. Supplier Matching Workflow

Potential architecture:

```text
Requirement
      ↓
Material normalization
      ↓
Supplier database search
      ↓
Hard constraint filtering
      ↓
Commercial feasibility
      ↓
Potential match list
      ↓
Human review
```

The matching engine should not make final commercial commitments.

---

## 14. Price Intelligence Automation

AI could help extract:

```text
Material
Quantity
Price
Price basis
Location
Date
Quality
Source
```

from messages and documents.

The structured data can then feed the price-intelligence system.

---

## 15. Follow-Up Automation

Many transactions require repeated follow-ups.

Potential workflow:

```text
Requirement created
      ↓
Supplier contacted
      ↓
No response
      ↓
Follow-up reminder
      ↓
Supplier response
      ↓
Update record
```

The system should avoid excessive messaging.

Follow-up frequency should be configurable.

---

## 16. WhatsApp Requirement Distribution

A future workflow could:

```text
Buyer requirement confirmed
        ↓
Generate supplier-facing requirement
        ↓
Remove private buyer information
        ↓
Send to approved supplier network
        ↓
Collect responses
        ↓
Extract offers
        ↓
Present structured options
```

This is particularly relevant to the current supplier-network approach.

---

## 17. Privacy in Supplier Distribution

The system should distinguish between:

### Internal information

```text
Buyer identity
Exact commercial strategy
Internal margin
Private contact
```

and:

### Supplier-facing information

```text
Material
Quantity
Location
Target/indication
Quality requirement
Transportation terms
Response method
```

Only information necessary for the sourcing interaction should be shared.

---

## 18. Buyer Communication

Potential workflow:

```text
Supplier response
      ↓
AI summarizes
      ↓
Human verifies
      ↓
Buyer receives structured option
```

Example:

```text
PP regrind
Quantity: 10 MT
Pickup: Noida
Price: ₹X/kg pickup
Quality: Supplier-reported
Availability: Tomorrow
Verification: Pending
```

This is more useful than forwarding a long conversation.

---

## 19. Document Automation

Future workflows could process:

- Quotations
- Purchase orders
- Invoices
- Weighment slips
- Quality reports
- Delivery documents

The workflow could extract relevant fields and attach them to the transaction record.

---

## 20. Transaction Creation

A confirmed commercial agreement could trigger:

```text
Create transaction
      ↓
Create shipment record
      ↓
Record agreed terms
      ↓
Assign status
      ↓
Create follow-up tasks
```

Human confirmation should remain available before critical records are finalized.

---

## 21. Logistics Updates

Potential workflow:

```text
Loading scheduled
      ↓
Reminder
      ↓
Dispatch confirmation
      ↓
Delivery update
      ↓
Quality confirmation
      ↓
Settlement
```

Initially, these can be simple reminders and data-entry prompts.

---

## 22. Transaction Completion

A transaction should not automatically be marked complete merely because dispatch occurred.

Possible completion checks:

```text
Material delivered
+
Quantity recorded
+
Quality outcome recorded
+
Commercial adjustment recorded
+
Payment status recorded
```

The exact requirements may vary by transaction.

---

## 23. AI Agent Roles

Instead of one general-purpose agent, the system could eventually use specialized agents.

### Research Agent

Finds and structures public company information.

### Buyer Intelligence Agent

Organizes buyer requirements and recurring demand.

### Supplier Intelligence Agent

Organizes supplier capabilities and availability.

### Matching Agent

Identifies potential supply-demand matches.

### Price Intelligence Agent

Normalizes and analyzes price observations.

### Transaction Agent

Maintains transaction status and follow-ups.

### Documentation Agent

Creates summaries and structured records.

Humans remain responsible for important commercial decisions.

---

## 24. n8n as Orchestration Layer

A workflow automation platform such as n8n could eventually coordinate:

```text
WhatsApp / Email
      ↓
Webhook / Trigger
      ↓
AI extraction
      ↓
Database
      ↓
Matching
      ↓
Human approval
      ↓
Communication
      ↓
Transaction record
```

The exact technology stack may change as the project develops.

---

## 25. Example n8n Workflow

Conceptually:

```text
[Incoming Message]
        ↓
[Extract Information]
        ↓
[Validate Fields]
        ↓
[Database Lookup]
        ↓
[Find Potential Matches]
        ↓
[Human Approval]
        ↓
[Send Response]
        ↓
[Update Record]
```

This is an architectural concept, not a production workflow.

---

## 26. Human-in-the-Loop

Human approval should remain especially important for:

- Price commitments
- Quality acceptance
- Supplier verification
- Buyer commitments
- Final matching
- Contract interpretation
- Payment actions
- Dispute handling

AI should assist rather than silently make irreversible decisions.

---

## 27. Confidence and Escalation

A future system could classify extracted information as:

```text
High confidence
Medium confidence
Low confidence
Unknown
```

Low-confidence or commercially sensitive actions can be routed to a human.

Example:

```text
AI:
"Quantity appears to be 20 MT."

Human:
Confirm quantity.

System:
Continue workflow.
```

---

## 28. Exception Handling

Automation should explicitly handle exceptions.

Examples:

```text
Missing price
Unknown grade
Conflicting quantity
Supplier changed price
Buyer changed requirement
Quality rejected
Freight unavailable
No supplier response
Duplicate requirement
Expired requirement
```

An automation that only handles successful cases is incomplete.

---

## 29. Duplicate Detection

The same requirement may arrive multiple times.

A future system could detect:

```text
Same buyer
+
Same material
+
Similar quantity
+
Same delivery location
+
Similar timing
```

and flag a possible duplicate.

Human review can decide whether it is actually the same requirement.

---

## 30. Requirement Expiry

Buyer requirements can become outdated.

A future system could track:

```text
Created
Last confirmed
Expires
Reconfirmed
Closed
```

Expired requirements should not continue generating supplier outreach.

---

## 31. Supplier Availability Expiry

Similarly:

```text
Supplier says:
10 MT available today
```

does not mean:

```text
10 MT available next week
```

Supply records should have timestamps and validity periods.

---

## 32. Automation Learning Loop

The architecture should connect operational outcomes back into the system:

```text
Automation
      ↓
Action
      ↓
Human / Market Outcome
      ↓
Transaction Data
      ↓
Performance Analysis
      ↓
Workflow Improvement
```

This is more valuable than simply increasing the number of automated actions.

---

## 33. AI Evaluation

AI workflows should be evaluated using:

- Extraction accuracy
- Missing-field detection accuracy
- Human correction rate
- Research relevance
- Matching relevance
- False positives
- False negatives
- Time saved
- Transaction impact

A workflow should only remain automated if it performs reliably enough for its specific task.

---

## 34. Automation Risk Levels

A possible framework:

### Low Risk

- Summaries
- Data formatting
- Research organization
- Reminder generation

### Medium Risk

- Supplier matching
- Price normalization
- Requirement classification
- Follow-up suggestions

### High Risk

- Price commitments
- Quality decisions
- Payment actions
- Contract decisions
- Final commercial acceptance

High-risk workflows should require human approval.

---

## 35. Technology Stack — Exploratory

Potential components:

```text
Communication
WhatsApp / Email

Automation
n8n

AI
LLM / AI models

Database
Structured database / spreadsheet

Storage
Cloud storage

Interface
Internal dashboard

Analytics
Database + reporting layer
```

These are technology categories, not fixed vendor commitments.

---

## 36. Initial Technology Principle

Do not build:

```text
Complex marketplace
+
Complex mobile app
+
Complex AI agents
```

before validating:

```text
Buyer demand
+
Supplier supply
+
Commercial feasibility
+
Repeat transactions
```

Technology should solve demonstrated operational bottlenecks.

---

## 37. First Automation Candidates

The first useful automations are likely to be:

1. Requirement extraction
2. Supplier message extraction
3. Data entry assistance
4. Buyer/supplier research
5. Follow-up reminders
6. Requirement formatting
7. Transaction summaries
8. Price-data organization

These can reduce repetitive work without removing commercial judgment.

---

## 38. Future Automation Candidates

After sufficient transaction data:

```text
Automated matching
+
Price intelligence
+
Demand alerts
+
Supply alerts
+
Recurring requirement detection
+
Transaction prediction / prioritization
```

These should be validated experimentally.

---

## 39. What AI Should Not Claim

The system should never automatically claim:

```text
"Material quality verified."
```

when it only analyzed a message.

It should distinguish:

```text
Supplier reported
AI extracted
Human verified
Transaction verified
```

This distinction is critical.

---

## 40. Security

Future automation should protect:

- API keys
- WhatsApp credentials
- Database credentials
- Customer information
- Supplier information
- Commercial data
- AI prompts containing sensitive data

Secrets should never be committed to the public GitHub repository.

---

## 41. Public GitHub Rules

The public repository should contain:

```text
Architecture
Documentation
Synthetic examples
Research
Schemas
Pseudocode
```

It should not contain:

```text
Real phone numbers
Private customer lists
API keys
Passwords
Private contracts
Confidential prices
Personal data
```

---

## 42. Current Status

The automation architecture is currently exploratory.

The project is not claiming to have a fully automated recycling marketplace or autonomous sourcing system.

The immediate objective is to use AI and automation selectively to reduce repetitive operational work while validating the business model manually.

---

## 43. Long-Term Architecture

A mature system could eventually look like:

```text
                ┌──────────────────┐
                │ Buyers / Demand  │
                └────────┬─────────┘
                         ↓
                ┌──────────────────┐
                │ AI Requirement   │
                │ Extraction       │
                └────────┬─────────┘
                         ↓
┌──────────────┐  ┌──────────────────┐  ┌───────────────┐
│ Suppliers    │→ │ Matching Engine  │ ←│ Material Data │
└──────────────┘  └────────┬─────────┘  └───────────────┘
                           ↓
                  ┌─────────────────┐
                  │ Human Review    │
                  └────────┬────────┘
                           ↓
                  ┌─────────────────┐
                  │ Transaction     │
                  │ Coordination    │
                  └────────┬────────┘
                           ↓
                  ┌─────────────────┐
                  │ Transaction DB  │
                  └────────┬────────┘
                           ↓
                  ┌─────────────────┐
                  │ Intelligence &  │
                  │ Learning        │
                  └─────────────────┘
```

---

## 44. Core Principle

> **Automate the repetition, not the responsibility.**

The long-term objective is to build systems that make recyclable-material sourcing faster, more organized and more data-driven while keeping humans responsible for important commercial decisions.
