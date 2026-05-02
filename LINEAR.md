# Linear Operating Model

Atelia Labs uses Linear because AI coding agents work better with a structured
execution queue. Linear is not the public source of truth.

## Principle

GitHub owns public truth. Linear owns execution state.

## Project

Use the existing Linear project:

- `Atelia Public Launch Foundation`

This project covers early public OSS infrastructure, repository hygiene, CI,
GitHub setup, release preparation, and first agent-ready implementation work.

## When To Create Linear Issues

Create or sync work into Linear when:

- a GitHub issue needs decomposition into smaller steps;
- an AI agent should be assigned a bounded implementation task;
- work spans multiple repositories;
- sequencing, blocking, or priority matters;
- the task should remain visible in an execution queue while GitHub discussion
  stays public.

Do not create Linear issues for:

- every small GitHub comment;
- public proposals before they are accepted;
- security-sensitive details that belong in private vulnerability reporting;
- vague brainstorming.

## Required Linear Issue Shape

Agent-ready Linear issues should include:

- goal
- repository
- required reading
- acceptance criteria
- verification
- expected GitHub PR or issue link
- human decisions / blockers

## Reflection Back To GitHub

When Linear work changes public state, reflect it back through:

- a GitHub issue comment;
- a pull request;
- a design document;
- a release note;
- a discussion summary.

This prevents Linear from becoming a private shadow roadmap.
