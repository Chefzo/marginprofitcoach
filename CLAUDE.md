# Claude Code Handoff: ProfitSignal

You are building ProfitSignal, an operational profit recovery platform. Treat this as a serious startup codebase, not a demo dashboard.

## Product thesis

ProfitSignal continuously finds recoverable profit hiding across invoices, delivery payouts, labor, bar variance, menu costs, rebates, and operational leakage. Every finding becomes a Signal with evidence, dollar value, confidence, owner, recommended action, and recovery status.

## Non-negotiables

- Do not build generic dashboards.
- Do not make AI the center of the UI.
- Do not create passive analytics without an action workflow.
- Every primary object should be tied to recoverable dollars, evidence, status, and owner.
- Build mobile-first, especially for owner/operator phone review.
- Keep V1 narrow: Signal Inbox, Signal Detail, Upload Center, Recovery Pipeline, Settings.

## Current repo state

This repo starts as a zero-dependency static MVP so the product logic and UX can be reviewed fast. Your next job is to convert it into a production-ready Next.js/Supabase app without losing the product focus.

## Recommended migration path

1. Preserve the current MVP screens and data model.
2. Create a Next.js app under `apps/web`.
3. Add TypeScript, Tailwind, shadcn/ui, and Supabase client.
4. Implement schema from `docs/database/SCHEMA.md`.
5. Seed mock signals and evidence.
6. Rebuild the Signal Inbox and Signal Detail first.
7. Add Upload Center with mocked parsing before real OCR/integrations.
8. Add real auth and organization/location scoping.

## First production milestone

A user can upload a vendor invoice CSV and a current price book CSV, then ProfitSignal generates Vendor Signals for price variance, duplicate invoice risk, missing credit, or abnormal freight/fees.

## Definition of done for V1

- Signal Inbox is the homepage.
- Signals are ranked by recoverable value and confidence.
- Signal Detail shows evidence, calculation, draft action, owner, and status.
- Recovery Pipeline tracks each opportunity through recovered or dismissed.
- Upload Center accepts CSV/manual mock files.
- User can assign owners and change status.
- All mock data is replaceable with database records.
