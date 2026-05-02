# Label Taxonomy

Labels should make GitHub issues useful for humans, maintainers, and AI agents.
The canonical label set is stored in `.github/labels.yml`.

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
