# Event Registration and Attendance Reporting Automation

This workflow summarizes current-month event participation from GoHighLevel contact tags and writes a monthly snapshot per event in Airtable.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Event definitions:** Includes Mastermind, Venture Vitality and Pitch to Yes event names.
- **Status coverage:** The implemented status set is registered, accepted and attended.
- **Tag-based counts:** Builds current-month event tags and reads the total matching contact count from each search response.
- **Monthly rollup:** Combines status counts into one event row and updates it using a month-and-event Snapshot Key.

## Workflow

1. Start the weekly schedule.
2. Generate each current-month event and status tag combination.
3. Search GoHighLevel contacts for each tag and read the reported total.
4. Aggregate registered, accepted and attended counts by event.
5. Upsert Event Monthly Snapshot by Snapshot Key.

## Tools

| Tool | Purpose |
| --- | --- |
| GoHighLevel API | Contact tag searches and reported match totals. |
| n8n | Schedule, API requests and sync. |
| JavaScript | Event definitions and monthly aggregation. |
| Airtable | Event Monthly Snapshot table. |

## Repository contents

- [`workflows/event-registration-and-attendance-reporting-version-01.json`](../workflows/event-registration-and-attendance-reporting-version-01.json)
- [`workflows/event-registration-and-attendance-reporting-version-02.json`](../workflows/event-registration-and-attendance-reporting-version-02.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `event-registration-and-attendance-reporting-version-01.json` | 6 | Active | Supplied export |
| `event-registration-and-attendance-reporting-version-02.json` | 6 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`, `httpHeaderAuth`.

## Export limitations and configuration notes

- Marked active in the export. Event names, tag format and search totals must match the CRM configuration. The implemented code reports registered, accepted and attended, despite older notes mentioning declined.
- The code reports registered, accepted and attended; older setup notes also mention declined, which is not in the implemented status list.
- Alternate supplied versions are retained together. Review differences before selecting a version; filenames do not imply production maturity.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
