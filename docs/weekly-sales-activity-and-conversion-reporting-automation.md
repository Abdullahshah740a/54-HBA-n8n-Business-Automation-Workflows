# Weekly Sales Activity and Conversion Reporting Automation

This legacy workflow is designed to summarize appointment activity, new opportunities and closed sales into an Airtable Sales Engine row, including selected sales representative breakdowns.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Reporting inputs:** Reads Airtable Opportunities and Raw Appointments, then retrieves GoHighLevel users for ownership names.
- **Call categorization:** Buckets Alignment, Conversion, PulseCheck and PostCheck activity and excludes canceled or no-show appointments from booked counts.
- **Weekly metrics:** Counts new opportunities, selected close categories, qualified Proximity records and WhatsApp stage activity.
- **Representative attribution:** Maps activity to configured sales representative names.
- **Sales Engine output:** Prepares weekly numeric fields while leaving manual targets out of the calculated output.

## Workflow

1. Start the weekly or manual run.
2. Load opportunities, appointments and user names.
3. Filter records using the configured current Monday-to-next-Monday window.
4. Aggregate call and opportunity activity by type and selected representative.
5. Pass the result to the Sales Engine upsert node.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Scheduled and manual aggregation workflow. |
| Airtable | Source appointment and opportunity tables and Sales Engine destination. |
| GoHighLevel API | Sales user lookup. |
| JavaScript | Date filtering and activity aggregation. |

## Repository contents

- [`workflows/weekly-sales-activity-and-conversion-reporting.json`](../workflows/weekly-sales-activity-and-conversion-reporting.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `weekly-sales-activity-and-conversion-reporting.json` | 7 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`, `httpHeaderAuth`.

## Export limitations and configuration notes

- Inactive legacy version. It uses a current-week window and upsert matching on Airtable record id, although the computed output supplies no id. Its close classifications also need alignment with the opportunity feed. The CEO refresh workflow includes a newer weekly activity branch.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
