# Membership Revenue Reconciliation and Executive Reporting Automation

This workflow reconciles Stripe membership data into Airtable and refreshes executive membership figures. It distinguishes collected revenue, annualized recurring value and distinct active paid customers.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Payment and subscription intake:** Retrieves paid invoices, charges and subscriptions with pagination, then loads an Airtable Stripe Price Map.
- **Explicit tier mapping:** Resolves membership tier through Stripe Price ID rather than guessing from amounts or product names.
- **Payment reconciliation:** Creates invoice-based payment records and matches charges for available fee, net amount and contact metadata.
- **Member reporting:** Creates subscription records and counts distinct active membership customer IDs rather than subscription rows.
- **Exception handling:** Records unmapped prices and unresolved identities, and stops if the price map is empty or both invoice and subscription reads are empty.
- **Executive metrics:** Updates collected membership revenue and active paid-member counts by the configured tiers; calculates annualized value separately.

## Workflow

1. Start the daily or manual run.
2. Fetch Stripe data and the Airtable Price Map.
3. Classify prices and shape payments, subscriptions, exceptions and executive updates.
4. Build Airtable batches with stable invoice, subscription and exception keys.
5. Write the records and update the configured executive tiles.

## Tools

| Tool | Purpose |
| --- | --- |
| Stripe API | Paid invoices, charges, customers and subscriptions. |
| n8n | Scheduling, paginated requests and batched writes. |
| JavaScript | Classification, reconciliation and metric calculation. |
| Airtable | Price Map, member records, payments, exceptions and executive tiles. |

## Repository contents

- [`workflows/membership-revenue-reconciliation-and-executive-reporting.json`](../workflows/membership-revenue-reconciliation-and-executive-reporting.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `membership-revenue-reconciliation-and-executive-reporting.json` | 15 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`.

## Export limitations and configuration notes

- Inactive in the export. Classification depends on a maintained Stripe Price Map and account-specific Airtable fields and record mappings; collected revenue and ARR are separate measures.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
