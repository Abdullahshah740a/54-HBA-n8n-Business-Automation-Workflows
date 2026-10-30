# Webhook Event Acknowledgement and Trusted Monitor Wake Automation

Receives an external event notification only as a wake signal, then starts a monitor that reads its own authenticated evidence.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Minimal receipt:** Accepts a POST webhook notification.
- **Untrusted body isolation:** Discards the incoming event body rather than copying claimed outcomes into operating state.
- **Trusted follow-up:** Calls the authenticated monitor with an empty request.

## Workflow

1. Receive the webhook notification.
2. Discard all submitted body data.
3. Wake the authenticated monitoring workflow.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Webhook | Receives the external wake signal. |
| JavaScript | Removes the submitted payload. |
| Automatic Reply and Bounce Monitor | Reads and verifies current provider outcomes. |

## Repository contents

- [`workflows/webhook-event-acknowledgement-and-trusted-monitor-wake.json`](../workflows/webhook-event-acknowledgement-and-trusted-monitor-wake.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `webhook-event-acknowledgement-and-trusted-monitor-wake.json` | 3 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [automatic-email-reply-and-bounce-monitoring-automation](automatic-email-reply-and-bounce-monitoring-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Marked active in the export. The webhook body is not treated as a trusted delivery, reply or bounce record.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
