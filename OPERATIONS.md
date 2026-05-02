# Atelia Labs Operations

This document defines the public engineering operating model for Atelia Labs.
It is intentionally lightweight, but the quality bar is production-grade.

## Source Of Truth

GitHub is the public source of truth.

- code
- pull requests
- issues
- public design discussions
- releases
- CI and required checks
- security notices
- contributor entry points

Linear is the execution queue for maintainers and AI agents.

- decomposition
- prioritization
- assignment
- handoff
- agent work queues
- implementation tracking

Do not duplicate long-running truth in both systems. GitHub records public
decisions and artifacts. Linear carries execution state. When Linear work
changes public behavior, the result is reflected back to GitHub through an
issue, PR, discussion, doc, or release note.

## Repository Classes

- `.github`: organization defaults, reusable workflows, shared labels, and
  operating policy.
- `atelia`: project-wide philosophy, governance, protocol-facing specs, AX, UX,
  extension contracts, hooks, and release policy.
- `atelia-secretary`: Rust daemon implementation and daemon-side contracts.
- `atelia-kit`: shared Swift package.
- `atelia-mac`: macOS client.
- `atelia-ios`: iOS client.

## Required Local Files

Every public implementation repository should keep:

- `.github/CODEOWNERS`
- `.github/workflows/ci.yml`
- `.github/dependabot.yml`
- `.github/pull_request_template.md` when repository-specific required reading
  matters
- repository-specific issue templates only when the organization defaults are
  not specific enough

Organization-wide defaults live in `.github`:

- `CONTRIBUTING.md`
- `SECURITY.md`
- `SUPPORT.md`
- `CODE_OF_CONDUCT.md`
- `.github/ISSUE_TEMPLATE/*`
- `.github/pull_request_template.md`

Related operating documents:

- `LABELS.md`
- `LINEAR.md`
- `RULESETS.md`
- `RELEASES.md`

## CI Policy

All CI workflows use least-privilege permissions:

```yaml
permissions:
  contents: read
  pull-requests: read
```

Pull request and push runs use concurrency cancellation so outdated checks do
not waste runner time.

Required check names should remain stable where the check applies:

- `Markdown`
- `Rust`
- `Swift`
- `Dependency Review` for implementation repositories with supported
  dependency graph data

Branch protection or rulesets should not be applied until these check names
exist on the default branch.

See `RULESETS.md` for the remote rollout order.

## Merge Policy

Before branch protection is enabled:

- maintainer judgment can merge small docs-only changes after review;
- implementation PRs should pass CI and include verification notes;
- security-sensitive changes should receive explicit human review.

After branch protection is enabled:

- default branch changes go through pull requests;
- required CI checks must pass;
- force pushes and branch deletion are disabled;
- conversation resolution is required;
- CODEOWNERS approval can be enabled once ownership boundaries are stable.

## Release Policy

Implementation repositories use SemVer once they have release artifacts or
stable documented APIs.

- `atelia-secretary`: SemVer
- `atelia-kit`: SemVer
- `atelia-mac`: SemVer when app builds are installable
- `atelia-ios`: SemVer when app builds are installable
- `atelia`: specification snapshots; SemVer or dated tags are acceptable

Release notes must call out:

- user-facing behavior changes
- protocol or schema changes
- security-sensitive changes
- extension / hook / permission compatibility changes
- migration notes

See `RELEASES.md` for the release checklist.

## Linear Policy

Use the Linear project `Atelia Public Launch Foundation` for launch-foundation
execution work.

GitHub Issue -> Linear issue is appropriate when:

- the work needs decomposition;
- an AI coding agent needs an execution queue;
- sequencing or priority matters;
- the issue spans multiple repositories.

Linear issue -> GitHub reflection is required when:

- public docs change;
- a public decision is made;
- a PR implements the work;
- a release note is affected.

Do not use Linear as a private replacement for public design accountability.
