# ProfitSignal Data Model

## Core entities

### organizations
Represents a customer account.

Fields:
- id
- name
- industry
- created_at

### locations
Restaurant/bar/store locations.

Fields:
- id
- organization_id
- name
- concept_type
- timezone
- external_ids

### users
Platform users.

Fields:
- id
- organization_id
- name
- email
- role
- status

### vendors
Suppliers, distributors, service vendors, and marketplaces.

Fields:
- id
- organization_id
- name
- vendor_type
- account_number
- contact_email
- terms

### data_sources
Uploaded files or connected integrations.

Fields:
- id
- organization_id
- location_id nullable
- source_type: upload, pos, delivery, labor, inventory, accounting, manual
- provider
- file_url
- status
- imported_at

### signals
The core object. A recoverable or preventable profit leakage opportunity.

Fields:
- id
- organization_id
- location_id nullable
- signal_type: vendor, delivery, labor, menu, rebate, bar, cash, tax, accounting
- title
- summary
- recoverable_amount_cents
- recurring_amount_cents nullable
- confidence_score 0-100
- urgency: low, medium, high, critical
- status: new, assigned, in_review, claim_ready, submitted, recovered, dismissed
- owner_user_id nullable
- due_at nullable
- detected_at
- recovered_at nullable
- dismissed_reason nullable

### signal_evidence
Evidence behind a Signal.

Fields:
- id
- signal_id
- evidence_type: invoice_line, payout_row, labor_snapshot, pos_export, vendor_contract, manual_note, calculation
- title
- description
- source_record_id nullable
- file_url nullable
- amount_cents nullable
- metadata jsonb

### recoveries
Tracks actual recovery work.

Fields:
- id
- signal_id
- recovery_type: vendor_claim, delivery_dispute, labor_action, price_update, rebate_claim, internal_control
- status: draft, sent, waiting, approved, recovered, denied
- expected_amount_cents
- recovered_amount_cents nullable
- counterparty
- submitted_at nullable
- resolved_at nullable

### tasks
Operational follow-up.

Fields:
- id
- organization_id
- signal_id nullable
- title
- owner_user_id
- status: open, done, blocked, dismissed
- due_at
- proof_required boolean

### claim_packets
Draft outbound claim/action packets.

Fields:
- id
- signal_id
- channel: email, pdf, internal_task
- subject
- body
- status: draft, approved, sent
- approved_by nullable
- sent_at nullable

### price_book_items
Known expected vendor pricing.

Fields:
- id
- organization_id
- vendor_id
- sku
- item_name
- unit
- pack_size
- expected_price_cents
- effective_start
- effective_end nullable

### invoice_lines
Normalized invoice rows.

Fields:
- id
- organization_id
- vendor_id
- location_id nullable
- invoice_number
- invoice_date
- sku nullable
- item_name
- quantity
- unit_price_cents
- extended_price_cents
- fees_cents
- raw jsonb

### delivery_payout_rows
Normalized delivery/platform payout rows.

Fields:
- id
- organization_id
- location_id
- provider
- order_id
- order_date
- gross_sales_cents
- fees_cents
- refunds_cents
- expected_payout_cents
- actual_payout_cents
- raw jsonb

### labor_snapshots
Labor summaries from scheduling/payroll/POS.

Fields:
- id
- organization_id
- location_id
- business_date
- daypart nullable
- sales_cents
- labor_cents
- scheduled_labor_cents nullable
- overtime_cents nullable
- hours
- raw jsonb

## Source of truth

ProfitSignal owns Signals, Recoveries, Tasks, Claim Packets, and Evidence interpretation.
External systems remain source of truth for POS sales, labor punches, vendor invoices, accounting records, and delivery payout reports.

## Derived data

- recoverable amount
- confidence score
- urgency
- recurring monthly impact
- claim readiness
- duplicate risk score
- price variance
- payout mismatch
