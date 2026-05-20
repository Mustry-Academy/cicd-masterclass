# CI/CD for Ignition — Masterclass

> Premium, hands-on training in version control, GitHub Actions, and multi-gateway deployments for Ignition 8.3.

This is the **hub repo** for the masterclass. It contains the curriculum, the schedule, the slides, the exercise index, and links to the lab repos.

## Who this is for

Senior Ignition integrators, and the IT/engineering colleagues who work with them, who want to ship Ignition the way real software is shipped: with Git, pull requests, CI pipelines, and reproducible deployments.

**Prerequisite:** current Inductive University 8.3 Credential, or equivalent professional experience.

## Schedule

| Day | Theme |
|---|---|
| 1 | Foundations and the Git mindset |
| 2 | Collaboration, code quality, and automation |
| 3 | Ignition-specific deployments |
| 4 | Ignition in the real world |

Each day runs **09:00–17:15 CET**. See the [Participant Guide](https://github.com/mustry-academy/academy-handbook/blob/main/participant-guide.md) for the daily structure.

## Lab repos

| # | Repo | Used on day |
|---|---|---|
| 01 | [`cicd-lab-01-git-fundamentals`](https://github.com/mustry-academy/cicd-lab-01-git-fundamentals) | 1 |
| 02 | [`cicd-lab-02-branching-and-prs`](https://github.com/mustry-academy/cicd-lab-02-branching-and-prs) | 1 |
| 03 | [`cicd-lab-03-github-actions`](https://github.com/mustry-academy/cicd-lab-03-github-actions) | 2 |
| 04 | [`cicd-lab-04-ignition-file-based-deploy`](https://github.com/mustry-academy/cicd-lab-04-ignition-file-based-deploy) | 3 |
| 05 | [`cicd-lab-05-ignition-image-based-deploy`](https://github.com/mustry-academy/cicd-lab-05-ignition-image-based-deploy) | 3 |
| 06 | [`cicd-lab-06-multi-gateway-deploy`](https://github.com/mustry-academy/cicd-lab-06-multi-gateway-deploy) | 3 |
| 07 | [`cicd-lab-07-secrets-and-db`](https://github.com/mustry-academy/cicd-lab-07-secrets-and-db) | 4 |
| 08 | [`cicd-lab-08-blue-green-canary`](https://github.com/mustry-academy/cicd-lab-08-blue-green-canary) | 4 |

Plus:

- [`cicd-preflight`](https://github.com/mustry-academy/cicd-preflight) — run this 7+ days before Day 1 to validate your environment
- `cicd-template-ignition-project` — a reusable starter for your own Ignition projects after the course

## Before Day 1

1. Read the [Participant Guide](https://github.com/mustry-academy/academy-handbook/blob/main/participant-guide.md)
2. Clone and run [`cicd-preflight`](https://github.com/mustry-academy/cicd-preflight)
3. Join the Discord (link in your welcome email)
4. Attend the optional setup call at T −7 days

## Repo layout

```
cicd-masterclass/
├── README.md           ← you are here
├── slides/             ← Slidev source, one deck per day
├── exercises/          ← exercise briefs (one folder per day)
└── docs/               ← MkDocs Material source (companion handbook)
```

## Licence

- Code in this repo: [Apache 2.0](./LICENSE)
- Slides, exercise briefs, and docs: [CC BY-NC 4.0](./CONTENT-LICENSE.md)

## Contact

- Lead instructor: Jasper Mustry (jasper@mustrysolutions.com)
- General enquiries: academy@mustrysolutions.com
- Discord: cohort link in your welcome email
