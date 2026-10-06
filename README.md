# dcc-mcp-outlook

Outlook adapter for the DCC-MCP ecosystem — thin application layer over
[dcc-mcp-office](https://github.com/dcc-mcp/dcc-mcp-office).

**Status: plan withdrawn — not started.** This repository is a placeholder
created as part of the Office Automation Platform repo split (see
`dcc-mcp-office/docs/adr/006-shared-office-core-split.md`).

The Phase 3 plan this repository was created against has been withdrawn.
Outlook is reachable only through MAPI/COM, which needs an installed
Outlook plus interactive first-run consent and cannot be exercised in CI,
so the adapter has no verifiable delivery path on the shared `office`
route. The Graph/Office.js branch for New Outlook (proposal §7, §19.4) is
the only headless option, and it requires an Azure application
registration and tenant admin consent before any of it can be validated.

Reopening this repository requires, at minimum:

1. a Microsoft Graph path for mail and calendar that CI can mock;
2. an Outlook document IR and COM backend in `dcc-mcp-office`, which today
   models only presentations, Word documents and workbooks;
3. evidence of real user demand for mail and calendar automation.

The proposal scope below is kept for reference only. It is not a
commitment.

## Scope (proposal §11.2)

- `outlook.message.create_draft` — drafts only by default
- `outlook.calendar.prepare_event`
- Classic Outlook → COM provider; New Outlook → Graph/Office.js provider
  (proposal §7, §19.4: identities and permissions kept separate)

## Upstream

- `dcc-mcp-office` — protocol, IR, C# runtime, Open XML worker, security
  policy, generic skills.
- `dcc-mcp-core` — gateway, jobs, artifacts, skills runtime, lifecycle.

## License

MIT
