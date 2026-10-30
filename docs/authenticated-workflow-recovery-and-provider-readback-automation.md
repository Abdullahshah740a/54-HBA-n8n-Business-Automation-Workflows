# Authenticated Workflow Recovery and Provider Readback Automation

Helps an authorized operator inspect a stopped execution and reconcile uncertain saved effects without automatically repeating the original provider action.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Execution ownership check:** Reads the owning n8n execution before attempting a controlled state takeover.
- **Provider evidence reads:** Inspects the relevant Google Sheets or Instantly result.
- **Recovery reconciliation:** Releases a clean completed lock or retains it when evidence remains uncertain; can request manual evidence.

## Workflow

1. Open the authenticated recovery page.
2. Confirm the inspection and refresh the held state.
3. Read the owning execution and validate takeover conditions.
4. Read the relevant provider result.
5. Save reconciliation and report whether the lock was safely released.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Google Sheets API | Dedicated Input and Review worksheet access. |
| Instantly API | Campaign, recipient, verification or outcome operations as specified. |
| n8n execution API | Checks the prior execution state. |

## Repository contents

- [`workflows/authenticated-workflow-recovery-and-provider-readback.json`](../workflows/authenticated-workflow-recovery-and-provider-readback.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-workflow-recovery-and-provider-readback.json` | 27 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `googleSheetsOAuth2Api`, `httpHeaderAuth`.

## Export limitations and configuration notes

- Recovery inspects and reconciles; it does not rerun the original send, staging or export action. Uncertain evidence keeps the operation held.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
