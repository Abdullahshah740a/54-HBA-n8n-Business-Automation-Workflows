# Isolated Two Prospect AI Provider Proof Automation

Initializes and runs an isolated two-person provider test while leaving the production operating table outside the test state.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Fixed test scope:** Requires the known two identities and an empty isolated table.
- **Fresh eligibility:** Refreshes identity and exclusion evidence before creating the test state.
- **Combined limits:** Configures a two-dollar total cost cap and a 28-call cap.
- **No-send proof receipt:** Runs the isolated bounded driver and labels the result as preliminary provider proof.

## Workflow

1. Validate the one-time execution window and empty test store.
2. Prepare the exact identities and read current exclusions.
3. Create the isolated authorized state.
4. Verify the limits and two-record count.
5. Run the isolated driver and return the test receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| GoHighLevel API | Current contact identity and exclusion information. |
| Instantly API | Campaign recipients, existing leads and block-list information. |
| Perplexity API | Research or search provider. |
| OpenAI API | Scoring and draft-generation provider. |

## Repository contents

- [`workflows/isolated-two-prospect-ai-provider-proof.json`](../workflows/isolated-two-prospect-ai-provider-proof.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `isolated-two-prospect-ai-provider-proof.json` | 10 | Inactive | Supplied export |

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

- Inactive, fixed-scope no-send test. The saved scope explicitly excludes client acceptance, output-quality acceptance and production sending.
- Historical proof receipts, identity anchors, hashes and time windows were sanitized. Regenerate evidence in an isolated environment; these files do not constitute live production proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
