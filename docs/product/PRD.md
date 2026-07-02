# ProfitSignal PRD

## One-line category

ProfitSignal is an Operational Profit Recovery platform.

## Problem

Hospitality operators leak money across vendor pricing, invoice errors, delivery payouts, labor overruns, bar shrink, comps/voids, food cost drift, and unclaimed rebates. Existing tools capture data but rarely own the recovery workflow. Operators still use exports, spreadsheets, texts, manual review, and manager judgment.

## Customer

Best first customer: 2-12 location restaurant/bar/nightlife group using fragmented POS, labor, inventory/AP, accounting, delivery, and spreadsheets.

Buyer: owner/operator, CFO/controller, director of operations.

Daily users: owner, controller, GM, purchasing manager, bar manager, DOO.

## Product promise

Open ProfitSignal and know exactly where recoverable money exists today, what evidence supports it, who owns it, and what action will recover it.

## V1 Wedge

Signal Inbox + Upload Center + Recovery Pipeline.

Users upload or import operational files. ProfitSignal detects profit leakage and creates Signals.

## Signal types for V1

1. Vendor Signal
   - price variance
   - duplicate invoice
   - missed credit
   - abnormal freight/fees

2. Delivery Signal
   - payout mismatch
   - missing deposit
   - refund discrepancy
   - promo funding mismatch

3. Labor Signal
   - overtime leak
   - labor percentage spike
   - schedule-vs-sales variance

4. Menu Signal
   - margin drift
   - cost increase not reflected in price

5. Rebate Signal
   - unclaimed rebate
   - expiring rebate window
   - missing distributor credit

## Core workflow

1. Upload data or sync source.
2. Engine detects Signals.
3. User reviews Signal Inbox.
4. User opens Signal Detail.
5. System shows calculation, evidence, confidence, and recommended action.
6. User assigns owner and status.
7. User generates claim/action packet.
8. Team submits recovery.
9. Recovered dollars are recorded.

## V1 Screens

- Signal Inbox
- Signal Detail
- Recovery Pipeline
- Upload Center
- Integrations placeholder
- Settings

## What not to build in V1

- Full POS replacement
- Full AP automation
- Full inventory
- Scheduling/payroll
- Loyalty
- Guest CRM
- Generic AI chatbot
- Broad BI dashboards

## Success metrics

- Time to first Signal: under 10 minutes after upload
- At least 3 credible recoverable opportunities from pilot data
- Buyer says the product found dollars they would not have found manually
- 70 percent or more of Signals get assigned or dismissed with reason
- Recovered value exceeds monthly subscription within 30-60 days
