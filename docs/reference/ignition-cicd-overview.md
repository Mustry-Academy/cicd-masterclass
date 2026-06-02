# Ignition CI/CD — the architectural framing

A one-page mental model that ties the eight labs together. Read this once before Day 1; the labs fill in the detail.

## The question the course answers

> How do you ship changes to a production Ignition gateway with the same discipline that web teams ship changes to production servers?

"Discipline" means: every change is reviewed, every change is tested by a machine before a human looks at it, every change is reproducible from a single commit hash, and a bad change can be rolled back fast.

## The five moving parts

1. **Source of truth** — A Git repository holds the Ignition project as text (JSON files in 8.3). Whatever is in `main` *is* what production runs. _(Days 1, 3.)_
2. **Change pipeline** — Pull requests, code review, branch protection. A change can't reach `main` without passing automated checks. _(Days 1, 2.)_
3. **Validation** — Linters, schema checks, smoke tests, gateway dry-runs. Run automatically on every PR by GitHub Actions. _(Day 2.)_
4. **Deployment** — A mechanism that takes a green commit on `main` and applies it to a target gateway. Two flavours: file-based and image-based. _(Day 3.)_
5. **Production realities** — Secrets, databases that need to migrate alongside code, multi-gateway environments, zero-downtime cutovers. _(Day 4.)_

## How the labs map to the moving parts

| Moving part | Labs |
|---|---|
| Source of truth | 01, 02, 04 |
| Change pipeline | 02, 03 |
| Validation | 03 |
| Deployment | 04, 05, 06 |
| Production realities | 07, 08 |

See [`docs/design/lab-dependency-graph.md`](../design/lab-dependency-graph.md) for the dependency order.

## Why Ignition is harder than a web app

Three things make Ignition CI/CD genuinely different from web CI/CD, and the course returns to each repeatedly:

- **State lives in the runtime.** A gateway has tag history, alarm journals, audit logs that you can't `git checkout`. Deploys must preserve this state.
- **The "build" is project files, not a binary.** There is no `npm run build`. You're shipping a folder of JSON. This means deploys are *file replacements*, with all the version-skew risks that implies.
- **A wrong deploy can affect physical equipment.** Rollback strategy is not optional. The cost of a bad deploy isn't a 500 page — it's a stopped line.

The course doesn't dodge these. Days 3 and 4 are about acknowledging them and choosing strategies that respect them.

## What this course is not

- Not an Ignition fundamentals course (IU 8.3 Credential is the prerequisite).
- Not a Git fundamentals course in isolation — Day 1 is fast because the audience is senior. Lab-01/02 are revision, not introduction.
- Not vendor-specific to any one CI platform — we use GitHub Actions because it's where most teams land, but the principles port to Azure DevOps, GitLab CI, Jenkins.

---

_This is a deliberately short framing. Each lab's `README.md` and `docs/` go deep on the specifics._
