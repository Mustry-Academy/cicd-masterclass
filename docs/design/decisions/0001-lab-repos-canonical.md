# CDR 0001 — Lab repos stay canonical; the hub never duplicates

- **Status:** accepted
- **Date:** 2026-05-29
- **Decider:** Sam Donche
- **Applies to:** all repos in the `mustry-academy` GitHub org that are part of the CI/CD-for-Ignition masterclass

## Context

The masterclass spans this hub repo (`cicd-masterclass`) and eight numbered lab repos (`cicd-lab-01` … `cicd-lab-08`), plus tooling satellites like `cicd-preflight`. Each lab repo already contains its own `README.md`, `exercises/block-*.md` (hands-on instructions), `docs/` (lab-specific reference sheets), `instructor-notes/block-*-key.md` (answer keys), and runnable code.

When learners check out a lab, they need the exercise instructions next to the code they're about to touch.

## Decision

The hub never copies content that exists in a lab repo. Specifically:

- **Per-day exercise briefs** in `exercises/dayN/README.md` are short (~1 screen). They state outcomes and link out to canonical block files in lab repos.
- **Reference content** in `docs/reference/` is only for material used by two or more labs. Lab-specific reference content stays in the lab's own `docs/` folder.
- **Instructor answer keys** are indexed (`docs/instructor/answer-keys-index.md`) — never copied — from each lab's `instructor-notes/`.
- **Tooling repos** (`cicd-preflight`, `cicd-template-ignition-project`) follow the same rule: documented and version-pinned from the hub, never vendored.

## Consequences

- One source of truth per piece of content; no staleness window between hub and lab copies.
- Hub stays small and scannable.
- Hub readers must follow links into lab repos to reach hands-on detail. The hub README must make this navigation obvious.
- If a piece of reference content turns out to be reused across labs, it migrates from the lab's `docs/` *into* `docs/reference/` (with a redirect note left behind), not the other way around.

## Related

- [CDR 0002 — MkDocs Material deferred](./0002-mkdocs-deferred.md)
- [CDR 0003 — Odoo sync via separate satellite](./0003-odoo-sync-via-separate-satellite.md) — extends this principle to publishing infrastructure
