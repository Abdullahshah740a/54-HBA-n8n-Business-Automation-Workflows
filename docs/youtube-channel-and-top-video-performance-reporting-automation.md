# YouTube Channel and Top Video Performance Reporting Automation

This workflow captures YouTube channel metrics and the most-viewed video identified by the configured search, then appends a dated Airtable snapshot.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Channel metrics:** Retrieves total subscribers, total channel views and total videos.
- **Top-video lookup:** Searches the configured channel for one video ordered by view count and requests its statistics.
- **Video reporting:** Records the selected video title, view count and YouTube link alongside channel totals.
- **Snapshot history:** Creates a new Airtable record with the snapshot date rather than updating a fixed current row.

## Workflow

1. Start the configured schedule.
2. Request the channel statistics.
3. Search the channel for its highest-view-count video in the returned search result.
4. Fetch the selected video view count.
5. Create a YouTube Snapshots record with channel and video fields.

## Tools

| Tool | Purpose |
| --- | --- |
| YouTube Data API | Channel statistics, video search and video statistics. |
| n8n | Scheduled requests and field mapping. |
| Airtable | YouTube Snapshots history table. |

## Repository contents

- [`workflows/youtube-channel-and-top-video-performance-reporting-version-01.json`](../workflows/youtube-channel-and-top-video-performance-reporting-version-01.json)
- [`workflows/youtube-channel-and-top-video-performance-reporting-version-02.json`](../workflows/youtube-channel-and-top-video-performance-reporting-version-02.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `youtube-channel-and-top-video-performance-reporting-version-01.json` | 5 | Inactive | Supplied export |
| `youtube-channel-and-top-video-performance-reporting-version-02.json` | 3 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`.

## Export limitations and configuration notes

- Inactive in the export. Subscribers Gained Today is hardcoded to zero rather than calculated. API access, channel selection and destination mappings need to be valid before scheduled reporting.
- Inactive in the export. Subscribers Gained Today is fixed at zero, and there is no difference calculation. Multiple runs on one date create separate records rather than replacing a daily snapshot.
- Alternate supplied versions are retained together. Review differences before selecting a version; filenames do not imply production maturity.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
