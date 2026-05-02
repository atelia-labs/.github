# GitHub Rulesets

This document defines the intended GitHub ruleset rollout for Atelia Labs.
Do not enable remote branch rules before the referenced workflows exist on the
default branch.

## Default Branch

Apply to `main` in every public repository:

- require pull requests before merge;
- require status checks to pass;
- require conversation resolution;
- block force pushes;
- block branch deletion;
- restrict bypass to repository administrators only;
- allow linear history when it does not block normal maintainer workflow.

Required checks:

- `Markdown`
- `Rust` for `atelia-secretary`
- `Swift` for Swift package or client repositories
- `Dependency Review`

Check names should be confirmed from the first pull request after CI is merged.
GitHub may display reusable workflow checks as nested names.

## CODEOWNERS

Enable required CODEOWNERS review after ownership boundaries are stable.
Until then, keep CODEOWNERS as routing information rather than a hard gate.

Initial ownership model:

- organization operations and policy: founder / maintainers;
- protocol, extension, hook, AX, and UX contracts: founder / maintainers;
- Secretary runtime and tool contracts: Secretary maintainers;
- Apple clients and Swift package: client maintainers.

## Rollout Order

1. Merge `.github` shared workflows and organization defaults.
2. Merge each repository workflow that calls the shared workflows.
3. Open a small pull request in each repository and record the exact check
   names GitHub reports.
4. Enable branch rulesets with the observed check names.
5. Turn on required CODEOWNERS review only after the routing file is trusted.

## Do Not Automate Yet

Do not auto-merge, auto-resolve discussions, or auto-close issues until the
agent workflow has enough audit evidence. These can become official extensions
or maintained actions later.
