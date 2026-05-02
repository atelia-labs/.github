# Issue Triage

GitHub Issues are the public intake surface for Atelia Labs. Linear is the
execution queue for maintainers and AI agents.

The initial triage policy is intentionally manual. Do not install a third-party
triage GitHub App yet. Add automation only after real issue volume shows which
steps are repetitive and safe to automate.

## First Pass

For each new GitHub issue:

1. Confirm it belongs in GitHub rather than a discussion, private security
   report, or Linear-only execution note.
2. Apply one `type:*` label.
3. Apply at least one `area:*` label.
4. Apply one `priority:*` label.
5. Keep or replace `status:needs-triage`.
6. Add `needs:*` labels for missing evidence, design, security review, or human
   decisions.

Close duplicates or unsupported requests with a short public explanation.

## When To Create Linear Work

Create or sync a Linear issue when:

- the GitHub issue needs decomposition;
- sequencing, priority, or blocking relationships matter;
- a coding agent needs a bounded execution task;
- the work spans multiple repositories;
- public discussion has settled into accepted implementation work.

Do not create Linear issues for every public comment or open-ended proposal.
Keep GitHub as the place where public reasoning and decisions can be audited.

## Agent-Ready Criteria

Use `agent:ready` only when the issue includes:

- a concrete goal;
- relevant repository or file scope;
- required reading;
- acceptance criteria;
- expected verification;
- known human decisions or blockers.

Use `agent:needs-context` when the issue is likely useful but not yet executable.
Use `agent:do-not-run` when agent work would be risky without human direction.

## Automation Later

Automation candidates:

- label drift checks against `labels.yml`;
- stale `status:needs-triage` reminders;
- issue form completeness checks;
- Linear issue creation for accepted `agent:ready` work.

Do not automate issue closure, priority assignment, or human-decision labels
until the project has enough examples to evaluate false positives.
