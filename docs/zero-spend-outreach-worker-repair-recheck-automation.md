# Zero Spend Outreach Worker Repair Recheck Automation

Invokes the existing main worker once to check that repaired operating state produces a safe no-action receipt with provider and release gates closed.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **One-time guard:** Requires a hardcoded short execution window and an exact run reference.
- **Single worker check:** Calls the main checkpointed worker once.
- **Zero-spend assertion:** Checks the returned calls, cost and ownership status against the expected no-action result.

## Workflow

1. Enter the bounded recheck window.
2. Call the existing worker for the fixed run.
3. Validate the zero-spend, no-held-lock receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | One-time trigger and subworkflow call. |
| JavaScript | Window and receipt assertions. |
| Main Checkpointed Worker | Existing processing component under test. |

## Repository contents

- [`workflows/zero-spend-outreach-worker-repair-recheck.json`](../workflows/zero-spend-outreach-worker-repair-recheck.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `zero-spend-outreach-worker-repair-recheck.json` | 4 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [checkpointed-ai-research-scoring-and-email-draft-processing-automation](checkpointed-ai-research-scoring-and-email-draft-processing-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive historical recheck, not a recurring production job. It does not reopen release gates or approve new prospect processing.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
