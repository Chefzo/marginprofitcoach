# Vendor Signal Engine v1

This is the first real ProfitSignal engine. Do not start with broad BI. Start with vendor invoice recovery because it is measurable, explainable, and easy to validate with CSVs.

## Input files

1. Vendor invoice export
2. Approved price book
3. Optional credit memo export
4. Optional purchase order export

## Import pipeline

1. Upload file
2. Detect file type
3. Normalize columns
4. Validate rows
5. Store source rows
6. Run detectors
7. Generate Signals
8. Attach evidence
9. Create claim packet draft

## Required normalized invoice fields

- vendor_name
- invoice_number
- invoice_date
- location_name
- sku
- item_name
- quantity
- unit
- unit_price
- extended_price
- fees
- raw_row

## Required price book fields

- vendor_name
- sku
- item_name
- unit
- pack_size
- approved_price
- effective_start
- effective_end

## Detectors

### 1. Price variance detector

Compare invoice unit price to approved price.

Signal if:
- actual price > approved price
- difference exceeds threshold
- quantity and price book match are confident enough

Recoverable amount:
(actual_price - approved_price) * quantity

Evidence:
- invoice row
- approved price book row
- price difference
- quantity
- invoice number

### 2. Duplicate invoice detector

Signal if two or more invoices share:
- same vendor
- same invoice number, or
- same date + same amount + similar line items

Confidence is higher with exact invoice number match.

### 3. Missed credit detector

Signal if:
- credit due was manually flagged
- substitution/shortage appears on receiving notes
- no matching credit memo found

### 4. Abnormal fee detector

Signal if freight, fuel, service, split-case, or miscellaneous fees exceed historical baseline.

### 5. Contract drift detector

Signal if invoice pricing has increased from trailing 30/60/90 day baseline without matching approved price book update.

## Confidence scoring

Start simple:

- exact SKU match: +35
- exact vendor match: +15
- active price book period: +20
- invoice math reconciles: +10
- quantity/unit match: +10
- historical price supports finding: +10

Clamp score between 0 and 100.

## Signal output

Title:
`{vendor} overcharged {item_name}`

Summary:
`Invoice {invoice_number} charged {actual_price} vs approved {approved_price} for {quantity} units.`

Recoverable:
calculated variance

Recommended action:
Generate credit request to vendor with invoice and price book evidence.

## Claim packet draft

Subject:
Credit request for invoice {invoice_number}

Body:
- State variance clearly
- Cite approved price
- Cite actual charged price
- Cite quantity
- Request credit memo
- Attach evidence

AI may draft wording. Human approval required before sending.

## V1 success criteria

- Upload invoice CSV and price book CSV
- Generate at least one credible Vendor Signal
- Show exact calculation
- Show evidence rows
- Draft claim packet
- Allow user to mark Submitted or Recovered
