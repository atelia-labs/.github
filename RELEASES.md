# Release Operations

Atelia Labs uses a thin release process until implementation artifacts become
stable. The release process should stay boring and explicit.

## Versioning

- `atelia-secretary`: SemVer once daemon behavior is installable or consumed by
  clients.
- `atelia-kit`: SemVer once public Swift APIs are consumed by clients or third
  parties.
- `atelia-mac`: SemVer once app builds are distributed.
- `atelia-ios`: SemVer once app builds are distributed.
- `atelia`: specification snapshots; SemVer is acceptable when protocol
  compatibility matters, otherwise dated tags are acceptable.

## Release Notes

Release notes must include:

- user-visible changes;
- protocol, manifest, hook, tool, schema, or extension compatibility changes;
- permission, approval, audit, or security-sensitive changes;
- migration steps;
- known limitations;
- verification performed.

## Pre-Release Checklist

- CI passes on the release commit.
- Dependency review has no unresolved high-risk change.
- Public docs match the released behavior.
- Security-sensitive changes have explicit human review.
- Extension and tool schema changes include compatibility notes.
- Follow-up issues exist for intentionally deferred work.

## Tags

Prefer annotated tags for implementation releases:

```bash
git tag -a v0.1.0 -m "v0.1.0"
git push origin v0.1.0
```

Specification-only tags may use dated names when that is clearer:

```bash
git tag -a specs-2026-05-02 -m "Specification snapshot 2026-05-02"
git push origin specs-2026-05-02
```
