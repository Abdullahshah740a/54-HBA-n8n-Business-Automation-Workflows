# Prospect Identity Anchor Research Retry Automation

Adds approved identity and organization clues to a held two-person research test, then resumes within its original limits.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Identity correction:** Uses approved profile or company source clues for the exact test people.
- **Attempt limits:** Permits a bounded second research attempt per person rather than restarting the test.
- **Preserved provenance:** Retains first attempts, held outputs and accumulated usage under the same two-dollar and 28-call caps.

## Workflow

1. Validate the fixed invocation window and expected held state.
2. Refresh identity or exclusion evidence.
3. Claim the isolated row and prepare the narrowly scoped revision.
4. Save the revision without resetting prior usage or receipts.
5. Run the remaining allowed test steps and return the combined receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Fresh Exclusion Reader | Refreshes identity and suppression evidence. |
| Isolated Bounded Driver | Continues the approved remaining provider steps. |

## Repository contents

- [`workflows/prospect-identity-anchor-research-retry.json`](../workflows/prospect-identity-anchor-research-retry.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `prospect-identity-anchor-research-retry.json` | 11 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.
- [isolated-two-prospect-bounded-test-driver-automation](isolated-two-prospect-bounded-test-driver-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive no-send retry tied to a specific held state and short execution window. It is not a general identity-enrichment service.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
