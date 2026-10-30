# Authenticated Recipient Staging Approval Automation

Records a specific operator grant to stage up to five approved recipients into a selected paused campaign, then coordinates that approved group.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exact group selection:** Uses batch, campaign and one-to-five person references.
- **Fresh evidence:** Previews and refreshes current recipient and exclusion information.
- **Durable grant:** Rejects changed state before saving the staging authorization.
- **Group completion checks:** Verifies the staged count and confirms that campaign activation and sending remain false.

## Workflow

1. Select recipients through the authenticated staging form.
2. Review the current staging evidence and approve the exact group.
3. Refresh state and save the bounded staging grant.
4. Call Approved Group Staging.
5. Validate the group completion receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| GoHighLevel API | Current contact identity and exclusion information. |
| Instantly API | Campaign recipients, existing leads and block-list information. |
| Approved Group Staging | Coordinates each authorized recipient. |

## Repository contents

- [`workflows/authenticated-recipient-staging-approval.json`](../workflows/authenticated-recipient-staging-approval.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-recipient-staging-approval.json` | 17 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [approved-recipient-group-staging-automation](approved-recipient-group-staging-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Staging is enabled in this export, but staging approval is not permission to activate a campaign or send messages.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
