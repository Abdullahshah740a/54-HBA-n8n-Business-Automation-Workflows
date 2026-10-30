# LinkedIn Outreach Event Capture and Airtable Sync Automation

This workflow receives Valley outreach events and centralizes prospect, campaign and response information in Airtable for follow-up analysis.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Webhook intake:** Accepts Valley event payloads through a POST endpoint.
- **Prospect and campaign context:** Maps prospect name, email, LinkedIn URL, company, title and campaign name.
- **Response details:** Captures event type, interest level, tag, response text, communication medium and timestamp.
- **Event matching:** Builds an Event ID from available message or conversation identifiers with a timestamp-based fallback.
- **Raw event archive:** Upserts mapped data and the original payload into Raw Valley Events.

## Workflow

1. Valley sends an outreach event to the webhook.
2. Read the prospect, campaign, message and conversation objects.
3. Normalize the event fields and build the Event ID.
4. Upsert Raw Valley Events using the Event ID match field.

## Tools

| Tool | Purpose |
| --- | --- |
| Valley | Outreach event and prospect information source. |
| n8n | Webhook handling and synchronization. |
| JavaScript | Payload normalization and event key construction. |
| Airtable | Raw Valley Events storage. |

## Repository contents

- [`workflows/linkedin-outreach-event-capture-and-airtable-sync.json`](../workflows/linkedin-outreach-event-capture-and-airtable-sync.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `linkedin-outreach-event-capture-and-airtable-sync.json` | 4 | Active | Supplied export |

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

- Marked active in the export. The workflow logs incoming events; it does not generate or send LinkedIn outreach messages.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
