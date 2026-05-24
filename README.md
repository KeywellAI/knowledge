# Keywell Knowledge Store

The source of truth for Keywell's internal knowledge — equivalent to the Docs section in ClickUp. Everything here should be written to stay useful over time: decisions, processes, standards, and context that new and existing team members need.

---

## File Structure

```
knowledge/
├── product/                  ← Product decisions, roadmap context, feature specs
│   ├── decisions/            ← ADRs and key product calls with rationale
│   └── features/             ← Per-feature specs and requirements docs
│
├── engineering/              ← Technical standards, architecture, and how-tos
│   ├── architecture/         ← System design docs, data models, integrations
│   ├── standards/            ← Coding conventions, PR process, branching strategy
│   └── runbooks/             ← Step-by-step ops guides (deploys, incidents, etc.)
│
├── data/                     ← Data sources, schemas, and definitions
│   ├── sources/              ← Docs for each data source (Tuva, claims, EHR, etc.)
│   └── glossary/             ← Business and clinical term definitions
│
├── go-to-market/             ← Sales, marketing, and customer-facing knowledge
│   ├── messaging/            ← Positioning, value props, competitive landscape
│   ├── customers/            ← Customer context, use cases, and onboarding notes
│   └── templates/            ← Email templates, pitch notes, outreach scripts
│
├── operations/               ← Company processes and team norms
│   ├── onboarding/           ← New hire guides by role
│   ├── processes/            ← Recurring processes (planning, retros, reviews)
│   └── policies/             ← HR, security, and company policies
│
└── research/                 ← Market research, user research, and competitive intel
    ├── market/               ← Industry landscape, trends, TAM analysis
    └── users/                ← User interviews, personas, and insights
```

---

## What Goes Where

| Content type | Folder |
|---|---|
| Why we made a product or architecture decision | `product/decisions/` or `engineering/architecture/` |
| How a feature is supposed to work | `product/features/` |
| How to run a deploy, rollback, or incident response | `engineering/runbooks/` |
| What a data source contains and how to use it | `data/sources/` |
| Definition of a clinical or business term | `data/glossary/` |
| How we talk about Keywell to customers | `go-to-market/messaging/` |
| Notes on a specific customer or prospect | `go-to-market/customers/` |
| How to onboard a new engineer / PM / etc. | `operations/onboarding/` |
| A process that runs on a schedule (planning, retros) | `operations/processes/` |
| Notes from a user interview or research session | `research/users/` |

---

## Conventions

- **File format**: Markdown (`.md`) for all docs.
- **File names**: lowercase with hyphens — e.g., `claims-data-source.md`, `pr-process.md`.
- **One topic per file**: keep docs focused. Link to related docs rather than duplicating.
- **Dates**: include a `Last updated:` line at the top of docs that go stale (runbooks, processes, policies).
- **Ownership**: add an `Owner:` line to docs that have a clear DRI.

---

## Contributing

1. Create a branch from `main`.
2. Add or update the relevant doc.
3. Open a PR — at least one reviewer for anything in `engineering/` or `operations/policies/`.
4. Merge to `main` when approved.

For quick fixes (typos, broken links), push directly to `main`.
