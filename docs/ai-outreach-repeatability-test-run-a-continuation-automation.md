# AI Outreach Repeatability Test Run A Continuation Automation

Refreshes current evidence for the saved repeatability run A and invokes its bounded processing driver.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Fixed run and window:** Requires the exact proof context and a hardcoded short invocation window.
- **Fresh exclusion check:** Reads current evidence before updating the isolated snapshot.
- **Saved-state continuation:** Requires the existing run A identity and retains saved progress rather than initializing another batch.

## Workflow

1. Validate the invocation and isolated run.
2. Read current identity and exclusion evidence.
3. Claim and update the proof state.
4. Release the saved state and run the bounded driver.
5. Return the proof processing receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Fresh Exclusion Reader | Current identity and suppression evidence. |
| Repeatability Bounded Driver | Coordinates remaining test steps. |

## Repository contents

- [`workflows/ai-outreach-repeatability-test-run-a-continuation.json`](../workflows/ai-outreach-repeatability-test-run-a-continuation.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `ai-outreach-repeatability-test-run-a-continuation.json` | 12 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [ai-outreach-repeatability-bounded-driver-automation](ai-outreach-repeatability-bounded-driver-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive no-send proof invocation tied to a fixed run. It is not a general recurring outreach or production release workflow.
- Historical proof receipts, identity anchors, hashes and time windows were sanitized. Regenerate evidence in an isolated environment; these files do not constitute live production proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
