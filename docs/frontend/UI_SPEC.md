# ProfitSignal UI Spec

## Product feel

Premium, fast, operator-minded, and money-focused. The UI should feel closer to Ramp/Linear than a restaurant dashboard.

## Core navigation

1. Signal Inbox
2. Recoveries
3. Upload Center
4. Integrations
5. Settings

## Signal Inbox

The homepage. No generic charts.

Top hero:
- Recoverable this month
- Ready to recover
- Signals found
- Recovered to date

Main list:
- Signal title
- Signal type
- Recoverable amount
- Confidence
- Status
- Owner
- Urgency

Sorting default: highest recoverable amount adjusted by confidence and urgency.

## Signal Detail

Must answer:
- What happened?
- How much is recoverable?
- Why do we believe this?
- What evidence supports it?
- What should happen next?
- Who owns it?
- What is the recovery status?

Sections:
- Signal summary
- Recovery value
- Confidence score
- Evidence cards
- Calculation table
- Recommended action
- Claim packet draft
- Timeline
- Assignment/status controls

## Recovery Pipeline

Kanban-style pipeline:
- New
- Assigned
- In Review
- Claim Ready
- Submitted
- Recovered
- Dismissed

Each card shows dollars first.

## Upload Center

Upload cards:
- Vendor invoices
- Price book
- Delivery payout report
- POS export
- Labor summary
- Inventory/counts
- Rebate terms

After upload:
- Show parsing status
- Show data quality issues
- Show generated Signals

## Mobile priorities

Owner phone view should show:
- Total recoverable
- Ready-to-recover dollars
- Highest priority Signals
- Approvals needed
- Recent recovered dollars

## Design rules

- Use Signal instead of alert.
- Use recoverable dollars as the primary visual hierarchy.
- Never bury evidence.
- Status transitions should be one click.
- AI-generated text must be labeled draft and require approval.
- Avoid dense charts unless they support a specific Signal.
