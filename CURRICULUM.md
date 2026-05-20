# Curriculum

A detailed day-by-day breakdown of the CI/CD for Ignition masterclass. Each day is structured around four 90-minute blocks (with the final block slightly shorter), using the **I do / We do / You do / Debrief** pattern.

---

## Day 1 — Foundations and the Git mindset

**Goal:** participants leave with a working mental model of Git, know how to operate in branches, and can open a clean pull request.

| Block | Topic | Lab |
|---|---|---|
| A | Why version control matters; Git's object model demystified | `cicd-lab-01-git-fundamentals` |
| B | Everyday workflows: add, commit, branch, merge, rebase | `cicd-lab-01-git-fundamentals` |
| C | Branching strategies compared: Git Flow vs GitHub Flow vs trunk-based | `cicd-lab-02-branching-and-prs` |
| D | Pull requests done right: scope, review, and merge hygiene | `cicd-lab-02-branching-and-prs` |

---

## Day 2 — Collaboration, code quality, and automation

**Goal:** participants can write a GitHub Actions workflow that validates a Compose file and runs on every PR.

| Block | Topic | Lab |
|---|---|---|
| A | Validation and linters as your safety net | `cicd-lab-03-github-actions` |
| B | GitHub Actions: workflows, jobs, steps | `cicd-lab-03-github-actions` |
| C | Self-hosted runners: when, why, and how | `cicd-lab-03-github-actions` |
| D | CI/CD pipelines that work; deployment strategy primer (blue/green, canary, rolling) | discussion + demo |

---

## Day 3 — Ignition-specific deployments

**Goal:** participants understand the Ignition 8.3 file structure deeply enough to design a deployment strategy around it.

| Block | Topic | Lab |
|---|---|---|
| A | Ignition 8.3 file structure decoded | `cicd-lab-04-ignition-file-based-deploy` |
| B | Image-based vs file-based deploys: tradeoffs and when to choose which | `cicd-lab-04-ignition-file-based-deploy` |
| C | The `.dockerignore` and `.deployignore` files | `cicd-lab-05-ignition-image-based-deploy` |
| D | Multi-gateway and multi-project deploys | `cicd-lab-06-multi-gateway-deploy` |

---

## Day 4 — Ignition in the real world

**Goal:** participants leave with a working multi-gateway deployment pipeline and a concrete plan for their own environment.

| Block | Topic | Lab |
|---|---|---|
| A | Deploying the database alongside your code | `cicd-lab-07-secrets-and-db` |
| B | Configuration options explored | `cicd-lab-07-secrets-and-db` |
| C | Secrets management without the headaches | `cicd-lab-07-secrets-and-db` |
| D | Keeping local development fast and frictionless; capstone brief | `cicd-lab-08-blue-green-canary` |

**Post-course capstone (T 0 → T +14, ~10–15 hours):** build a working CI/CD pipeline for the provided scenario. Includes a 30-minute 1:1 review with the instructor.
