# CDR 0002 — MkDocs Material deferred; markdown-only for now

- **Status:** superseded by [CDR 0004](./0004-mkdocs-adopted.md)
- **Date:** 2026-05-29
- **Decider:** Sam Donche
- **Applies to:** the `docs/` tree in `cicd-masterclass`

## Context

The original README marked the MkDocs Material handbook as "deferred to post-beta". The hub restructure (see [CDR 0001](./0001-lab-repos-canonical.md)) raised the question of whether to stand up MkDocs now or keep deferring.

## Decision

Keep deferring the MkDocs site. Structure `docs/` so that MkDocs nav can drop in cleanly later without restructuring:

- Sub-folders by audience (`setup/`, `reference/`, `instructor/`, `student-handbook/`, `design/`) map directly to future top-level nav sections.
- All docs are plain Markdown that renders well on GitHub today.
- No MkDocs config (`mkdocs.yml`) is committed yet; no GitHub Pages workflow is set up.

## Consequences

- Lower maintenance overhead while content is still being written.
- Learners and instructors browse via GitHub for now — acceptable since both audiences are already authenticated to the org.
- When the content stabilizes post-beta, adding MkDocs is mostly a config and theming exercise; the folder layout is already shaped for it.
- A future CDR will record the decision to publish (or not) and which theme.

## Related

- [CDR 0001 — Lab repos stay canonical](./0001-lab-repos-canonical.md)
