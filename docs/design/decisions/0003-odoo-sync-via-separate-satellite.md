# CDR 0003 — Course is published to Odoo via a separate satellite; hub has zero sync footprint

- **Status:** accepted
- **Date:** 2026-05-29
- **Decider:** Sam Donche
- **Applies to:** `cicd-masterclass` and every future Mustry Academy course hub

## Context

Mustry Academy publishes its courses into Odoo eLearning (the company LMS). For the CI/CD-for-Ignition masterclass that means turning the content scattered across this hub plus the eight `cicd-lab-NN` satellites into a single Odoo course.

A working spike already exists at `mustry-academy/test-odoo-course-population` — Python + XML-RPC, idempotent upsert via `ir.model.data` XMLIDs, local docker-compose Odoo + Postgres for dev testing. The question was *where* to place the production version of that sync, and *what* (if anything) should land in this hub repo to make sync happen.

Two further constraints drove the decision:
- The sync should be **invisible to learners** — students cloning this hub or any lab repo should never encounter Odoo plumbing, credentials, workflows, or config that doesn't pertain to learning the course.
- More Mustry Academy courses are coming. Whatever tool we build for CI/CD should service those courses too, without copy-paste per hub.

## Decision

Course content is synced to Odoo eLearning by a **separate satellite repo**, `mustry-academy/academy-odoo-sync` (being renamed from `test-odoo-course-population`). The sync repo is instructor/maintainer-only — learners are never asked to clone it.

The sync repo uses a **course adapter** pattern: per-course Python modules (e.g. `adapters/cicd_masterclass.py`) translate the raw shape of each course's source repos into a generic Pydantic IR that a shared upserter writes to Odoo. The cicd-masterclass adapter knows about this hub's `slides/`, `exercises/dayN/`, and `docs/reference/` layout, plus the `cicd-lab-NN/exercises/block-*.md` layout in each satellite — and explicitly never references `instructor-notes/`.

**This hub deliberately has zero sync footprint.** No code, no `mkdocs.yml`-style sync config, no GitHub Actions workflow, no `odoo-course.yml` at the root. The only artefact in this hub that even acknowledges the sync exists is this CDR.

## Consequences

- Adding the CI/CD course to Odoo, and adding any future Mustry Academy course, requires changes only in `academy-odoo-sync` (a new ~100-line adapter + one line in its `courses.yml`). This hub and the lab repos remain untouched.
- Students cloning any course repo see only course material. They can't accidentally trigger or break a sync.
- Odoo credentials live exclusively in `academy-odoo-sync`'s GitHub Secrets — never in this hub or in any lab repo.
- Each synced course carries a **sync receipt** in its Odoo channel description (per-source git SHAs + sync timestamp + run id), so anyone looking at the live course in Odoo can tell which commit they're seeing. A `--dry-run` mode previews what the next sync would change before it runs.
- Production syncs are triggered exclusively by a `workflow_dispatch` action on `academy-odoo-sync` — no cron, no auto-on-push. Every prod publish is a deliberate human action.
- Trade-off: course authors who edit content here cannot trigger a re-publish without access to the sync repo. That's intentional — it keeps the publish event explicit and instructor-controlled.

## Related

- [CDR 0001 — Lab repos stay canonical](./0001-lab-repos-canonical.md) — same underlying principle: this hub is the indexing layer; canonical artefacts (lab content, sync infrastructure) live in dedicated satellite repos.
- [CDR 0002 — MkDocs Material deferred](./0002-mkdocs-deferred.md)
- Sync repo: `mustry-academy/academy-odoo-sync` (formerly `test-odoo-course-population`)
- Prior plan that informed this decision: `~/.claude/plans/we-plan-on-creating-snappy-wren.md`
