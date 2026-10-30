# Bounded Outreach Batch Processing Driver Automation

Coordinates repeated single-step worker calls for a saved batch while preventing an unbounded loop or unsafe continuation.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Run binding:** Requires a batch run ID for every invocation.
- **Continuation gate:** Only loops when the prior worker receipt is ready, permits the next step and retains no lock.
- **Loop bound:** Stops at the configured 281-invocation guard and returns the final worker receipt.

## Workflow

1. Receive the internal batch run reference.
2. Validate the loop and prior receipt.
3. Call one checkpointed worker step.
4. Repeat only while continuation is permitted.
5. Return the final receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Subworkflow calls and branch routing. |
| JavaScript | Loop bounds and receipt checks. |
| Checkpointed Worker | Processes the next saved research, score or copy step. |

## Repository contents

- [`workflows/bounded-outreach-batch-processing-driver.json`](../workflows/bounded-outreach-batch-processing-driver.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `bounded-outreach-batch-processing-driver.json` | 5 | Active | Supplied export |

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

- The driver does not itself research leads, draft email or activate campaigns; those actions belong to its dependent workers and approval stages.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
