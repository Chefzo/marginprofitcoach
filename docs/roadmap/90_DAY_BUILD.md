# ProfitSignal 90-Day Build Plan

## Days 1-15: Static MVP and customer validation

Deliver:
- Signal Inbox static MVP
- Signal Detail static MVP
- Recovery Pipeline mock
- Upload Center mock
- PRD, schema, API, UI spec

Validate:
- Operators understand Signals immediately
- Buyers care about recoverable dollars more than reports
- Upload-to-Signal flow feels compelling
- First wedge should be vendor variance, delivery payout, or rebates

## Days 16-30: Production scaffold

Deliver:
- Next.js app in `apps/web`
- TypeScript
- Tailwind
- Supabase project
- Auth
- Organization/location/user model
- Signal Inbox backed by database
- Seed data

## Days 31-45: Upload and parsing MVP

Deliver:
- CSV upload for vendor invoices
- CSV upload for price book
- Normalized invoice lines
- Price variance engine
- Generated Vendor Signals
- Evidence cards

## Days 46-60: Recovery workflow

Deliver:
- Signal assignment
- Status transitions
- Claim packet drafts
- Recovery tracking
- Recovered amount logging
- Dismissed reason
- Audit timeline

## Days 61-75: Second Signal category

Choose one:
- Delivery payout mismatch
- Rebate claim opportunity
- Labor leakage

Criteria:
- fastest data access
- clearest ROI
- easiest buyer proof

## Days 76-90: Paid pilot readiness

Deliver:
- Organization onboarding
- Basic roles
- Exportable recovery report
- CSV templates
- Pilot dashboard for recovered value
- Error/data quality handling
- First paid pilot package

## Paid pilot success criteria

- Time to first Signal under 10 minutes
- At least $1,000 credible recoverable opportunity discovered
- At least 3 Signal types demonstrated with real data
- Buyer agrees value is worth $300-$1,000/month/location or success fee
