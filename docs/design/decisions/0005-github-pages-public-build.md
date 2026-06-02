# CDR 0005 — Publish the docs site to GitHub Pages; public build excludes internal docs

- **Status:** accepted
- **Date:** 2026-05-29
- **Decider:** Sam Donche
- **Applies to:** how the `cicd-masterclass` docs site is published
- **Extends:** [CDR 0004 — MkDocs Material adopted](./0004-mkdocs-adopted.md) (which left Pages as a later decision)

## Context

CDR 0004 stood up the MkDocs Material site and explicitly deferred the publish
mechanism. `cicd-masterclass` is a **private** repo, but a GitHub Pages site
published from a private repo is **public to the internet** on every tier below
Enterprise Cloud (which the org is not on). The `docs/` tree contains
instructor-facing facilitation material and internal curriculum-design records
(CDRs) that must not be exposed publicly.

## Decision

1. **Publish to GitHub Pages** via a GitHub Actions workflow
   (`.github/workflows/docs.yml`) on push to `main`, using the "GitHub Actions"
   Pages source (no `gh-pages` branch). Site URL:
   `https://mustry-academy.github.io/cicd-masterclass/`.

2. **The public build excludes internal content.** CI builds with a dedicated
   config, `mkdocs.ci.yml`, that `INHERIT`s the local `mkdocs.yml` and uses
   `exclude_docs` to drop `instructor/` and `design/` from the artifact. This is
   `exclude_docs`, not merely a trimmed nav, because **an un-nav'd MkDocs page is
   still served at its URL** — only file exclusion actually withholds it.

3. **Local `mkdocs serve` keeps using `mkdocs.yml`** and shows everything,
   including instructor and design docs.

## Consequences

- Learner-facing docs (Home, Reference, and later Setup / Student Handbook) are
  the only content on the public site.
- Two manual, one-time steps remain (not git-managed): enable Pages with the
  Actions source, and keep the repo private.
- The home page (`docs/README.md`) still names the `instructor/` and `design/`
  sections and links to them; those links dangle on the public site. A
  public-specific landing page is a possible follow-up.
- When Phase 2 (CDR 0004) pulls lab-repo docs in at build time, the CI checkout
  will need a token with org read access — to be designed then.

## Related

- [CDR 0004 — MkDocs Material adopted](./0004-mkdocs-adopted.md)
- [CDR 0001 — Lab repos stay canonical](./0001-lab-repos-canonical.md)
