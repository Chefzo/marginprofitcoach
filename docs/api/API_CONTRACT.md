# ProfitSignal API Contract

This is the target API shape for the production app.

## Authentication

All endpoints require organization-scoped auth.

Headers:
- Authorization: Bearer token
- X-Organization-Id

## Signals

### GET /api/signals
Returns ranked Signal Inbox.

Query params:
- status
- type
- location_id
- min_confidence
- owner_id

Response item:
```json
{
  "id": "sig_123",
  "type": "vendor",
  "title": "Sysco price variance on mozzarella",
  "recoverableAmount": 148200,
  "confidence": 98,
  "urgency": "high",
  "status": "new",
  "owner": null,
  "location": "One Fourteen",
  "detectedAt": "2026-07-01T12:00:00Z"
}
```

### GET /api/signals/:id
Returns Signal detail with evidence, calculation, recovery, tasks, and claim packet.

### PATCH /api/signals/:id
Updates status, owner, due date, dismissed reason.

### POST /api/signals/:id/claim-packet
Generates a draft claim packet. AI may draft language, but human approval is required.

### POST /api/signals/:id/mark-recovered
Records recovered amount and resolution note.

## Uploads

### POST /api/uploads
Accepts CSV/XLS/PDF/image files.

Payload:
- file
- source_type: invoice, price_book, delivery_payout, pos_export, labor_summary, rebate_terms
- location_id optional
- vendor_id optional

Response:
```json
{
  "dataSourceId": "ds_123",
  "status": "queued"
}
```

### GET /api/uploads/:id
Returns parsing/import status.

## Recovery pipeline

### GET /api/recoveries
Returns recovery cards grouped by status.

### PATCH /api/recoveries/:id
Updates recovery status, submitted date, recovered amount, notes.

## Vendors

### GET /api/vendors
Returns vendors.

### POST /api/vendors
Creates a vendor.

## Settings

### GET /api/settings/thresholds
Returns Signal generation thresholds.

### PATCH /api/settings/thresholds
Updates thresholds per organization/location/type.

## Engine jobs

### POST /api/engine/run
Runs Signal generation for selected data sources.

Payload:
```json
{
  "dataSourceIds": ["ds_1", "ds_2"],
  "engineTypes": ["vendor_price_variance", "duplicate_invoice"]
}
```

## Error behavior

Every API response should include a stable error code for operator-safe messaging.
Do not fail silently. If data quality is poor, create low-confidence Signals or import warnings, not fake certainty.
