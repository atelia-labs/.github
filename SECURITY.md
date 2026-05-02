# Security Policy

Please do not disclose security issues publicly until maintainers have reviewed
them.

Use GitHub private vulnerability reporting when available.

Security-sensitive areas include:

- repository access;
- secrets;
- automation;
- hooks and external event sources;
- extension execution;
- approval and audit logs;
- local file and terminal access in native clients.

## Triage

Maintainers should classify security reports by affected surface:

- local host execution;
- extension manifest, permission, service, or runtime boundary;
- Secretary approval, audit, or autonomous execution;
- external account, repository, workflow, webhook, or secret access;
- client-side storage, notification, or user consent.

Security fixes should use private coordination until disclosure is safe. Public
follow-up should include the affected versions, user impact, mitigation,
upgrade path, and any extension or permission compatibility changes.

## Automation

Security automation should be strict, but it should not create hidden authority.
CI, dependency review, Dependabot, CodeQL, label sync, and release automation
must use least-privilege permissions and should be documented before becoming
required gates.
