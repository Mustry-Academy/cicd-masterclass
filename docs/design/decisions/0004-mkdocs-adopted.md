# CDR 0004 — MkDocs Material adopted; lab docs aggregated at build time

- **Status:** accepted
- **Date:** 2026-05-29
- **Decider:** Sam Donche
- **Applies to:** the `docs/` tree in `cicd-masterclass` and how lab-repo docs reach the published site
- **Supersedes:** [CDR 0002 — MkDocs Material deferred](./0002-mkdocs-deferred.md)

## Context

CDR 0002 deferred MkDocs and kept `docs/` as plain Markdown, but shaped the
folders so a MkDocs site could drop in later without restructuring. The content
has stabilised enough to stand the site up, and there is now a need to surface
the lab repos' docs alongside the hub's cross-cutting docs.

## Decision

1. **Adopt MkDocs Material now.** `mkdocs.yml` lives at the repo root; `docs_dir`
   is the existing `docs/` tree. Build deps are pinned in `docs/requirements.txt`.
   The audience folders (`reference/`, `design/`, …) map to nav sections, exactly
   as 0002 anticipated. `docs/README.md` doubles as the MkDocs home page (MkDocs
   treats `README.md` as a directory index) so GitHub rendering still works.

2. **Lab docs are aggregated at *build* time, never copied into this repo.**
   Phase 2 uses `mkdocs-multirepo-plugin` with each lab pinned to a **tag/ref**.
   The plugin does a sparse checkout into a temp dir at build; nothing from a lab
   repo is committed here.

## Consequences

- **CDR 0001 stays intact.** Build-time aggregation means no committed copies and
  no staleness window — the lab repos remain the single source of truth. Tag-pinning
  also gives reproducible "this is the v1.0 course site" builds rather than tracking
  each lab's `main`.
- The *published* site now presents lab content under the hub's roof. That changes
  navigation, not ownership — which is why it gets a CDR rather than living silently
  in config.
- `site/` is gitignored; a GitHub Pages publish workflow is a separate, later decision.
- Empty audience folders (`setup/`, `instructor/`, `student-handbook/`) are omitted
  from nav until they have pages.

## Related

- [CDR 0001 — Lab repos stay canonical](./0001-lab-repos-canonical.md)
- [CDR 0002 — MkDocs Material deferred](./0002-mkdocs-deferred.md) (superseded by this CDR)
