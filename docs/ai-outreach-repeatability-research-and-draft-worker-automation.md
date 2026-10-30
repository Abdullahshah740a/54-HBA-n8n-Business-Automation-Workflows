# AI Outreach Repeatability Research and Draft Worker Automation

Runs isolated research, scoring and copy steps for repeatability tests using a dedicated saved-state table.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Durable ownership:** Claims the isolated state row and verifies its revision before continuing.
- **Provider checkpoint:** Saves and confirms an action before making an authorized provider request.
- **Budgeted processing:** Applies the saved call and cost limits across research, scoring and draft stages.
- **Receipt and hold:** Returns usage, review rows and continuation eligibility, retaining a lock when effects remain unresolved.
- **Search transport:** Includes a separate Perplexity search request in addition to research and OpenAI processing.

## Workflow

1. Read the isolated state and validate the run.
2. Claim the next step and save its checkpoint.
3. Make the authorized provider request.
4. Apply the result and update usage.
5. Save the state and return a continuation or held receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Perplexity API | Research or search provider. |
| OpenAI API | Scoring and draft-generation provider. |

## Repository contents

- [`workflows/ai-outreach-repeatability-research-and-draft-worker.json`](../workflows/ai-outreach-repeatability-research-and-draft-worker.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `ai-outreach-repeatability-research-and-draft-worker.json` | 17 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `openAiApi`, `perplexityApi`.

## Export limitations and configuration notes

- Inactive no-send test worker. The nominal test scope is two dollars and 28 calls, with actual saved-state gates controlling which requests can proceed.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
