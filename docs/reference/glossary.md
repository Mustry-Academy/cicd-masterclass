# Glossary

Terms used across the masterclass. Lab-specific jargon stays in the lab's own `docs/`; this glossary is for vocabulary that appears in two or more labs.

## A

**Answer key** — Instructor-only solutions for an exercise block. Lives in each lab repo under `instructor-notes/block-X-key.md`. Indexed from [`docs/instructor/answer-keys-index.md`](../instructor/answer-keys-index.md).

## B

**Block** — A ~90-minute teaching unit. Each day has four blocks (A, B, C, D), each following the I-do / We-do / You-do / Debrief pattern.

**Blue/green deploy** — A deployment strategy where two identical production environments ("blue" and "green") run in parallel; traffic is switched from one to the other atomically. Covered in lab-08.

## C

**Canary deploy** — A deployment strategy where a new version is rolled out to a small subset of users/gateways first, then expanded if healthy. Covered in lab-08.

**Cohort** — A single delivery of the masterclass to a group of learners, typically over four days. Each cohort pins to specific tag versions of every satellite repo (see [`tools/cohort-pins.yml`](../../tools/cohort-pins.yml)).

## F

**File-based deploy** — Deploying Ignition projects as exported JSON files into a gateway's project folder. Contrast with image-based deploy. Covered in lab-04.

## G

**Gateway** — An Ignition runtime process. The course uses three Docker-based gateways (local, dev, prod) to simulate promotion flow.

## I

**Image-based deploy** — Deploying Ignition projects as Docker images. Contrast with file-based deploy. Covered in lab-05.

## L

**Lab repo** — A satellite repo (e.g. `cicd-lab-03-github-actions`) holding the canonical exercise content for one or more blocks. See [lab-dependency-graph.md](../design/lab-dependency-graph.md).

## P

**Preflight** — The `cicd-preflight` tool/repo, run by learners ≥7 days before Day 1 to validate their environment.

## S

**Self-hosted runner** — A GitHub Actions runner running on infrastructure the team controls (vs. GitHub-hosted). Introduced in lab-03; required for the Ignition-touching labs (lab-04 onward).

---

_Add terms as they appear in slides or exercise briefs. Keep entries short — link to a fuller treatment in the relevant lab's `docs/` when one exists._
