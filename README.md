# dcc-mcp-outlook

Outlook adapter for the DCC-MCP ecosystem — thin application layer over
[dcc-mcp-office](https://github.com/dcc-mcp/dcc-mcp-office).

**Status: planned, not started — Phase 3, graded `host_limited`.** This
repository is a placeholder created as part of the Office Automation
Platform repo split (see
`dcc-mcp-office/docs/adr/006-shared-office-core-split.md`). It implements
no adapter capability yet; the scope below is a plan, not an available
feature.

Outlook stays in the plan, but it is graded `host_limited`. The proposal
(§7, §19.4) describes two routes with different capabilities and
authorization boundaries:

- **Classic Outlook** — desktop automation through the Outlook Object
  Model / MAPI/COM. It needs a locally installed Outlook and interactive
  first-run consent, so this route has no unattended (headless) path.
- **New Outlook / cloud** — Microsoft Graph and Office.js / Outlook Web
  Add-ins. This route does not use COM; the proposal treats it as the
  headless option, but it has a different authorization boundary: an
  Azure application registration and tenant admin consent, with
  identities and permissions kept separate from the COM provider.

Neither route is implemented in this placeholder, so no capability is
claimed as available.

The `host_limited` grade records a host limitation on the Classic Outlook
COM route: a real Outlook COM session and interactive first-run consent
cannot be exercised on a hosted CI runner, so that runtime acceptance has
no unattended CI path. It is not a blanket CI exemption. This repository
does run CI — `.github/workflows/docs-ci.yml` (markdown lint) and
`.github/workflows/repo-contract.yml` (repository contract) check the
documentation and static repository contract on every pull request, and
those gates apply here as usual. The grade describes the current
placeholder, not a permanent property or a promise about future host
capabilities; once a headless, CI-verifiable path exists, it should be
verified in CI.

Moving off the `host_limited` grade — that is, reaching a path CI can
verify automatically — requires, at minimum:

1. a Microsoft Graph path for mail and calendar that CI can mock;
2. an Outlook document IR and COM backend in `dcc-mcp-office`, which today
   models only presentations, Word documents and workbooks;
3. evidence of real user demand for mail and calendar automation.

In this placeholder the grade is prose-level: it is not yet wired to the
machine-readable grading contract that `dcc-mcp-word` already ships in
`capabilities.py` and `host_matrix.py` (`verified` / `host_limited` /
`unimplemented`, with a host matrix and tests). A machine-readable
contract does exist in the ecosystem; this repository simply has not
adopted it yet.

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
