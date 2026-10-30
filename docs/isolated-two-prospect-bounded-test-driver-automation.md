# Isolated Two Prospect Bounded Test Driver Automation

Coordinates a bounded sequence of single-step calls against an isolated proof worker, returning its final saved processing receipt.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Bounded execution:** Requires a run ID and enforces a 29-invocation guard.
- **Safe continuation:** Continues only when the prior receipt is ready, permits another step and retains no ownership lock.
- **Worker separation:** Delegates provider operations and saved-state handling to the child workflow.

## Workflow

1. Receive the internal proof run.
2. Check the loop and continuation conditions.
3. Invoke one worker step.
4. Repeat when allowed and return the final receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Subworkflow loop and branching. |
| JavaScript | Bound checks and receipt filtering. |
| Isolated Provider Worker | Executes the next isolated processing step. |

## Repository contents

- [`workflows/isolated-two-prospect-bounded-test-driver.json`](../workflows/isolated-two-prospect-bounded-test-driver.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `isolated-two-prospect-bounded-test-driver.json` | 5 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [isolated-ai-research-scoring-and-draft-test-worker-automation](isolated-ai-research-scoring-and-draft-test-worker-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive no-send driver for the two-person proof. Its loop bound is separate from the worker cost and provider-call caps.
- Historical proof receipts, identity anchors, hashes and time windows were sanitized. Regenerate evidence in an isolated environment; these files do not constitute live production proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
