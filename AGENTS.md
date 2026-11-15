# AGENTS.md — dcc-mcp-outlook

> **Placeholder repository — no implementation yet.**

Thin Outlook adapter over `dcc-mcp-office` (ADR-006 split). Planned for
Phase 3 and graded `host_limited`. It implements no capability yet; the
scope in [README.md](./README.md) is a plan, not an available feature.

The proposal (§7, §19.4) separates two routes with different capabilities
and authorization boundaries: the Classic Outlook desktop COM/MAPI route
(needs a locally installed Outlook and interactive first-run consent, no
unattended/headless path) and the New Outlook / cloud Graph and Office.js
route (does not use COM; the proposal treats it as the headless option,
with an Azure application registration and tenant admin consent, and
identities and permissions kept separate). Neither route is implemented
here.

`host_limited` records a host limitation on the Classic Outlook COM route:
a real Outlook COM session and interactive consent cannot run on a hosted
CI runner. It is not a blanket CI exemption. This repository runs
`.github/workflows/docs-ci.yml` (markdown lint) and
`.github/workflows/repo-contract.yml` (repository contract) on every pull
request; those gates verify the documentation and static repository
contract and apply as usual. The grade describes the current placeholder,
not a permanent property. Here it is prose-level; `dcc-mcp-word` already
ships a machine-readable grading contract (`capabilities.py`,
`host_matrix.py`). See the platform proposal in
`dcc-mcp-office/docs/proposals/office-automation-platform-v1.0.md`.

The `dcc-mcp-office` M1 (COM MVP) blocker is resolved — it shipped in
`dcc-mcp-office` v0.2.0.
