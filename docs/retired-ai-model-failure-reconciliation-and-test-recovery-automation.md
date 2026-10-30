# Retired AI Model Failure Reconciliation and Test Recovery Automation

Inspects an actual finished execution for a specific model-not-found rejection, reconciles the held isolated proof and revises its saved model configuration.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exact failure evidence:** Requires the expected pending research action and provider 404 model_not_found response in the owning execution.
- **Controlled takeover:** Claims only the expected finished proof state.
- **Provenance preservation:** Retains source results, provider receipts and usage history while applying the configured model revision.

## Workflow

1. Validate the one-time repair window and held proof.
2. Read the owning n8n execution including its saved result.
3. Confirm the exact non-inference model rejection.
4. Claim and reconcile the proof, then revise the saved model settings.
5. Save and return the recovery receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| n8n execution API | Evidence of the actual prior execution response. |

## Repository contents

- [`workflows/retired-ai-model-failure-reconciliation-and-test-recovery.json`](../workflows/retired-ai-model-failure-reconciliation-and-test-recovery.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `retired-ai-model-failure-reconciliation-and-test-recovery.json` | 10 | Inactive | Supplied export |

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

- Inactive no-send historical repair for one specific rejection. It does not itself prove that the replacement model produces acceptable output or authorize prospect sending.
- Historical proof receipts, identity anchors, hashes and time windows were sanitized. Regenerate evidence in an isolated environment; these files do not constitute live production proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
