# LinkedIn Outreach Event Validation and Meridian Reporting Automation

Captures Valley outreach events and sends compact event facts to Meridian for downstream reporting. The payload sent onward contains an event key, event type and occurrence time.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Event validation:** Accepts seven configured Valley event types and checks timestamp and prospect identity fields.
- **Stable event key:** Hashes event type, occurrence time, prospect, campaign and message context; a conversation ID alone is not treated as a unique event.
- **Compact reporting payload:** Excludes the original message body and prospect contact details from the outgoing event fact.

## Workflow

1. Receive the Valley POST event.
2. Validate its type, timestamp and identity context.
3. Generate the SHA 256 event key.
4. POST the normalized event to the Meridian Valley ingest endpoint.

## Tools

| Tool | Purpose |
| --- | --- |
| Valley | Source outreach and response events. |
| n8n | Webhook intake and HTTP handoff. |
| JavaScript and crypto | Validation and event-key hashing. |
| Meridian and Supabase | Configured event-ingest backend. |

## Repository contents

- [`workflows/linkedin-outreach-event-validation-and-meridian-reporting.json`](../workflows/linkedin-outreach-event-validation-and-meridian-reporting.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `linkedin-outreach-event-validation-and-meridian-reporting.json` | 3 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `httpHeaderAuth`.

## Export limitations and configuration notes

- The export calls an external ingest endpoint; its internal database and aggregation logic are outside this workflow. No LinkedIn message is sent here.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
