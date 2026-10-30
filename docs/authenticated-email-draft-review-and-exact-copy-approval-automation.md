# Authenticated Email Draft Review and Exact Copy Approval Automation

Lets an authorized reviewer inspect a prospect email, its research evidence and its current sender details before recording a review decision.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Evidence-based review:** Shows the subject, body, offer, sender, qualification evidence and source links.
- **Revision loop:** Supports saving edits for another review; changed copy cannot be approved in the same unchanged-copy approval step.
- **Exact-copy binding:** Validates reviewer identity, state revision and copy hash before persisting a decision.

## Workflow

1. Select the batch and person in the authenticated form.
2. Inspect the exact draft and supporting evidence.
3. Choose approval or save edits for another review.
4. Refresh state and validate that the reviewed copy has not changed.
5. Save and verify the review receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |

## Repository contents

- [`workflows/authenticated-email-draft-review-and-exact-copy-approval.json`](../workflows/authenticated-email-draft-review-and-exact-copy-approval.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-email-draft-review-and-exact-copy-approval.json` | 11 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Export limitations and configuration notes

- Draft approval records a specific copy version. Sending and campaign release are separate actions.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
