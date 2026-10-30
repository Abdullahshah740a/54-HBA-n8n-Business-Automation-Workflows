# Checkpointed AI Research Scoring and Email Draft Processing Automation

Processes the next saved prospect step with durable state before and after a research, scoring or draft-generation request.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exclusive state claim:** Checks the run and claims the operating row before progressing.
- **Durable provider checkpoint:** Persists and verifies the next action before a Perplexity or OpenAI request.
- **Usage and state updates:** Normalizes the result, applies the transition and returns calls, cost and review-row information.
- **Reconciliation hold:** Keeps ownership when a provider effect remains unresolved; otherwise releases it for the next step.

## Workflow

1. Read operating state and validate the run.
2. Claim the row and prepare the next action.
3. Save and confirm the provider checkpoint.
4. Call the selected research or model endpoint if authorized.
5. Apply the result, save state and return a continuation receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Perplexity API | Research or search provider. |
| OpenAI API | Scoring and draft-generation provider. |

## Repository contents

- [`workflows/checkpointed-ai-research-scoring-and-email-draft-processing.json`](../workflows/checkpointed-ai-research-scoring-and-email-draft-processing.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `checkpointed-ai-research-scoring-and-email-draft-processing.json` | 15 | Active | Supplied export |

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

- Marked active despite its draft label. It is a processing worker, not the campaign activation component. Provider authorization and saved limits still control work.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
