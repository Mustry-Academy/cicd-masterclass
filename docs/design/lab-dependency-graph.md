# Lab dependency graph

How the eight lab repos depend on each other, and where they map to course days.

```mermaid
flowchart TD
    P[cicd-preflight<br/><i>T −7 days</i>] --> L1

    subgraph D1[Day 1 — Foundations]
        L1[lab-01<br/>git-fundamentals] --> L2[lab-02<br/>branching-and-prs]
    end

    subgraph D2[Day 2 — Collaboration & CI]
        L3[lab-03<br/>github-actions]
    end

    subgraph D3[Day 3 — Ignition deploys]
        L4[lab-04<br/>file-based-deploy] --> L5[lab-05<br/>image-based-deploy]
        L5 --> L6[lab-06<br/>multi-gateway-deploy]
    end

    subgraph D4[Day 4 — Production]
        L7[lab-07<br/>secrets-and-db] --> L8[lab-08<br/>blue-green-canary]
    end

    L2 --> L3
    L3 --> L4
    L6 --> L7
```

## Reading the graph

- **Hard prerequisites** (solid arrows): the downstream lab assumes the upstream lab's outcomes. Skipping breaks the learner.
- **Day groupings** are facilitation boundaries, not hard dependencies — a participant who arrives mid-cohort can in principle parachute into a day if they've done the prerequisite labs.
- **`cicd-preflight`** is not a lab; it's a one-off environment validator. Learners run it ≥7 days before Day 1.

## Status (as of 2026-05-29)

| Lab | Repo exists | Notes |
|---|---|---|
| 01 | ✅ | Generic Python/Flask, no Ignition yet |
| 02 | ✅ | Builds on 01 |
| 03 | ✅ | First CI lab |
| 04 | ✅ | First Ignition lab (Docker, three gateways) |
| 05 | ❌ | Not yet created |
| 06 | ❌ | Not yet created |
| 07 | ❌ | Not yet created |
| 08 | ❌ | Not yet created |

Track creation in [`content-backlog.md`](./content-backlog.md).
