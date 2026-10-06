# AGENTS.md — dcc-mcp-outlook

> **Placeholder repository — no implementation yet.**

Thin Outlook adapter over `dcc-mcp-office` (ADR-006 split). Planned for
Phase 3 and graded `host_limited`: it targets a locally installed Outlook
over MAPI/COM with interactive first-run consent, has no headless path,
and is exempt from the CI verification gate. See [README.md](./README.md)
and the platform proposal in
`dcc-mcp-office/docs/proposals/office-automation-platform-v1.0.md`.

The `dcc-mcp-office` M1 (COM MVP) blocker is resolved — it shipped in
`dcc-mcp-office` v0.2.0.
