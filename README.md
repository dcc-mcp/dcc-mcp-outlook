# dcc-mcp-outlook

Outlook adapter for the DCC-MCP ecosystem — thin application layer over
[dcc-mcp-office](https://github.com/dcc-mcp/dcc-mcp-office).

**Status: planned, not started — Phase 3, graded `host_limited`.** This
repository is a placeholder created as part of the Office Automation
Platform repo split (see
`dcc-mcp-office/docs/adr/006-shared-office-core-split.md`).

Outlook stays in the plan, but it is graded `host_limited`: automation
runs only against a locally installed Outlook through MAPI/COM, and the
first run needs interactive user consent. There is no headless path, so
the adapter **cannot be verified in CI** and is explicitly exempt from the
CI verification gate that other adapters must pass. Anyone depending on
this adapter should expect to run it on a workstation with Outlook
installed, not in an automated pipeline.

The Graph/Office.js branch for New Outlook (proposal §7, §19.4) is the
only headless option, and it requires an Azure application registration
and tenant admin consent before any of it can be validated.

Moving off the `host_limited` grade — that is, reaching a path CI can
verify automatically — requires, at minimum:

1. a Microsoft Graph path for mail and calendar that CI can mock;
2. an Outlook document IR and COM backend in `dcc-mcp-office`, which today
   models only presentations, Word documents and workbooks;
3. evidence of real user demand for mail and calendar automation.

`host_limited` is currently a prose-level grading only; a machine-readable
grading contract does not exist yet.

The proposal scope below remains the intended scope, subject to the
`host_limited` constraints above.

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
