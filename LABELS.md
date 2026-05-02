# Label Taxonomy

Labels should make GitHub issues useful for humans, maintainers, and AI agents.
The canonical label set is stored in `.github/labels.yml`.

## Sync Policy

`labels.yml` is the canonical source for public Atelia repository labels.
Repository labels should be synchronized from it before issue templates or
triage automation depend on a label name.

For now, label sync is intentionally manual:

- create or update labels from `labels.yml` in each public repository;
- do not delete legacy labels until there are no open issues or PRs using them;
- prefer renaming obvious legacy variants when they are unused, such as
  `type: bug` -> `type:bug`;
- keep Dependabot labels such as `dependencies` and `github_actions` when
  Dependabot creates them.

Do not add a label-sync GitHub Action yet. Add automation only after manual
sync becomes repetitive enough to justify another moving part.

## Families

- `type:*`: what kind of work this is
- `area:*`: which repository or product surface is affected
- `priority:*`: urgency / importance
- `status:*`: workflow state
- `agent:*`: whether an AI agent can safely pick it up
- `needs:*`: missing decision, information, reproduction, or review
- `source:*`: where the work originated

## Minimum Rules

Every triaged issue should have:

- one `type:*`
- at least one `area:*`
- one `priority:*`
- one `status:*`

Agent-ready issues should also have:

- `agent:ready`
- clear acceptance criteria
- required reading
- expected verification
- known human decisions or blockers

## Linear Mapping

Linear labels should stay coarser than GitHub labels. Recommended mappings:

- GitHub `area:github`, `type:ops` -> Linear `github`, `type:ops`
- GitHub `area:secretary` -> Linear `secretary`
- GitHub `area:clients`, `area:kit`, `area:mac`, `area:ios` -> Linear `clients`
- GitHub `needs:human` -> Linear `needs-human`
- GitHub `agent:ready` -> Linear `agent-ready`

GitHub keeps public taxonomy. Linear keeps execution queue filters.

## Initial Triage Labels

Issue forms start new issues with `status:needs-triage`.

Maintainers should replace or supplement that state during triage:

- `status:accepted` when the issue is accepted and ready to schedule;
- `status:blocked` when a decision or dependency is missing;
- `agent:ready` only when the issue has enough context for an AI coding agent;
- `agent:needs-context` when the issue is useful but not yet executable;
- `agent:do-not-run` when human direction is required before agent work.
