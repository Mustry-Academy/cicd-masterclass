# Docs

Cross-cutting documentation for the masterclass. Lab-specific docs live in each lab repo's own `docs/` folder — see [CDR 0001](./design/decisions/0001-lab-repos-canonical.md).

This tree builds into a MkDocs Material site ([CDR 0004](./design/decisions/0004-mkdocs-adopted.md), which supersedes [CDR 0002](./design/decisions/0002-mkdocs-deferred.md)). Everything also renders as plain Markdown on GitHub. To preview the site locally:

```sh
python3 -m venv .venv && source .venv/bin/activate
pip install -r docs/requirements.txt
mkdocs serve   # → http://localhost:8000
```

## Sub-folders

- [**`setup/`**](./setup/) — Prerequisites, workstation setup, preflight tool usage. Read these before Day 1.
- [**`reference/`**](./reference/) — Cross-lab content: the [Ignition CI/CD overview](./reference/ignition-cicd-overview.md), [glossary](./reference/glossary.md), troubleshooting index.
- [**`instructor/`**](./instructor/) — Facilitation handbook, timing cheatsheet, known pitfalls, and the index of answer keys (which live in each lab's `instructor-notes/`).
- [**`student-handbook/`**](./student-handbook/) — Recipe for assembling the printable handbook from slides + briefs. Deferred until content stabilizes.
- [**`design/`**](./design/) — Curriculum Decision Records (CDRs), lab dependency graph, content backlog.
