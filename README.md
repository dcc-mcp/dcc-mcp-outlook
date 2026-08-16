# dcc-mcp-outlook

Outlook adapter for the DCC-MCP ecosystem — thin application layer over
[dcc-mcp-office](https://github.com/loonghao/dcc-mcp-office).

**Status: planned — not started.** This repository is a placeholder created
as part of the Office Automation Platform repo split (see
`dcc-mcp-office/docs/adr/006-shared-office-core-split.md`). Work starts in
Phase 3, blocked on the `dcc-mcp-office` M1 (COM MVP) release.

## Scope (proposal §11.2)

- - `outlook.message.create_draft` — drafts only by default
- `outlook.calendar.prepare_event`
- Classic Outlook → COM provider; New Outlook → Graph/Office.js provider
  (proposal §7, §19.4: identities and permissions kept separate)

## Upstream

- `dcc-mcp-office` — protocol, IR, C# runtime, Open XML worker, security
  policy, generic skills.
- `dcc-mcp-core` — gateway, jobs, artifacts, skills runtime, lifecycle.

## License

MIT
