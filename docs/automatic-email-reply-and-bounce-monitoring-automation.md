# Automatic Email Reply and Bounce Monitoring Automation

Checks authenticated Instantly outcomes and records delivery-related changes for the saved outreach campaign, then drains a bounded set of follow-up outcome tasks.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Multiple wake paths:** Supports schedule, manual invocation and an internal provider-event wake.
- **Authenticated event reads:** Reads provider evidence rather than treating an external webhook body as a trusted result.
- **Saved monitoring checkpoint:** Claims the operating state and persists progress before continuing reads.
- **Outcome handoff:** Invokes the effects worker for pending tasks with a maximum of 60 drain iterations per monitor execution.

## Workflow

1. Start the scheduled, manual or internal monitor.
2. Claim available state and save the checkpoint.
3. Read and consume the authenticated provider events.
4. Persist monitoring results.
5. Drain eligible outcome tasks and return the monitoring receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Instantly API | Campaign, recipient, verification or outcome operations as specified. |
| Outcome Effects Worker | Applies and reconciles resulting campaign or recipient actions. |

## Repository contents

- [`workflows/automatic-email-reply-and-bounce-monitoring.json`](../workflows/automatic-email-reply-and-bounce-monitoring.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `automatic-email-reply-and-bounce-monitoring.json` | 21 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `httpHeaderAuth`.

## Related workflow dependencies

- [email-outcome-response-and-campaign-protection-automation](email-outcome-response-and-campaign-protection-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Marked active in the export. It depends on the configured workspace, subscription and campaign mappings; a notification alone is not accepted as outcome proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
