# ProfitSignal

ProfitSignal is an operational profit recovery platform for hospitality businesses.

The product promise: **find recoverable dollars hiding across vendor invoices, delivery payouts, labor, bar variance, comps/voids, menu cost drift, and rebates — then turn every finding into a recovery workflow.**

## Category

Operational Profit Recovery.

Not a dashboard. Not generic BI. Not a chatbot. ProfitSignal is a system of action for money leakage.

## Run the static MVP

```bash
python3 -m http.server 5173
# open http://localhost:5173
```

## Current MVP

- Signal Inbox ranked by recoverable dollars, confidence, urgency, and owner
- Signal Detail workflow with evidence, recommended action, assignment, and recovery status
- Recovery Pipeline: New -> Assigned -> In Review -> Claim Ready -> Submitted -> Recovered
- Upload Center for invoices, delivery payouts, POS exports, labor summaries, inventory counts, and rebate terms
- Mock hospitality data for multi-unit restaurants, bars, nightlife, and pizza/sports-bar operators
- Claude Code handoff specs in `/docs`

## Product philosophy

Every Signal must answer:

1. What happened?
2. How much money is involved?
3. Why do we believe it happened?
4. What should happen next?
5. Who owns recovery?
6. How do we verify dollars recovered?

## Recommended production architecture

- Frontend: Next.js or Vite React
- DB: Supabase Postgres
- Auth: Supabase Auth or Clerk
- Storage: Supabase Storage or S3
- Jobs: Trigger.dev or Inngest
- Integrations: POS, AP/invoice OCR, delivery payout CSV/API, labor, inventory, accounting
- AI: anomaly clustering, claim drafting, evidence summarization, prioritization only

## Core wedge

Do not build a reporting app. Build a recovery queue that proves value in dollars.

First customer: a 2-12 unit restaurant/bar group with fragmented vendor, delivery, labor, inventory, and closeout workflows.
