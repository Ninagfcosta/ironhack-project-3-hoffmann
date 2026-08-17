# GDPR Compliance Peer Audit

This repository contains the GDPR audit lab for **LAB | Audit your teammate's project — GDPR lens**. The audited system is Marc's Project 3, the **VR Competitive Intelligence Copilot** (a review-scraping and report-generation agent).

## Files in this repository

### `system_brief_janaina_hoffmann.md`
Plain-language system brief describing what Marc's project does: what it takes as input, what it outputs, who is affected, and whether a human reviews its output before action is taken. This is the starting point required before any audit work.

### `data_processing_brief_nina.md`
The factual data-processing brief provided by the project owner (Marc). Describes, without drawing legal conclusions: what personal data the system touches (review text, reviewer identifiers, requester identifiers), where it comes from, what it is used for, who processes it (OpenAI, Firecrawl, Tavily, Notion, Slack), where it is stored, and whether any automated decision-making occurs.

### `gdpr-audit-marc-project.md`
The full GDPR audit built on top of the two documents above. Contains:
- **Audit worksheet — Section A (Data map):** categories of personal data, sources, purposes, lawful basis (marked TBD — legal review), retention, recipients/sub-processors, and international transfers.
- **Audit worksheet — Section B (Risk and rights):** special-category data risk, Article 22 automated-decision check, DPIA need, data subject rights most at risk, controller/processor split, and DPA gaps.
- **Audit worksheet — Section C (Law stacking):** AI Act, ePrivacy, and Data Act cross-checks.
- **Client recommendation memo:** bottom-line recommendation (stop), top three required actions, and residual risks that remain even after fixes.

## Audit summary

**Bottom line:** Stop and remediate before further processing. The system currently has no documented lawful basis, no data subject notice, no Data Processing Agreements with any of its four external processors, and no retention limit or erasure process — despite processing text written by identifiable individuals and transferring it outside the EU/EEA.
