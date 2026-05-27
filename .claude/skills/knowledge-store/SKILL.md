---
name: knowledge-store
description: "Add, update, or capture information in the Keywell knowledge store (GitHub repo: KeywellAI/knowledge). Use this skill whenever the user wants to document something, save a decision, record a process, write up a runbook, capture customer notes, add a glossary term, log a research finding, or put something in the knowledge base. Also trigger when the user says things like 'we should document that,' 'let's save this,' 'write this up,' 'add this to our docs,' 'remember this for the team,' or 'knowledge store.' The skill handles placement, formatting, branching, and committing automatically so the user doesn't need to know the repo structure."
---

# Knowledge Store Skill

Adds or updates content in the [KeywellAI/knowledge](https://github.com/KeywellAI/knowledge.git) repo — Keywell's internal source-of-truth documentation.

---

## Workflow Overview

1. **Understand** what the user wants to document
2. **Determine placement** — pick the right folder/file based on content type
3. **Check for conflicts** — scan existing docs for contradictory or duplicate information
4. **Draft the doc** in Keywell's markdown conventions
5. **Confirm with user** (brief) before committing
6. **Commit and push** to a branch, or directly to `main` for minor additions

---

## Step 1 — Understand the Content

If the user has already explained what they want to document, extract:
- **Topic**: what is this about?
- **Content type**: decision, process, spec, data source, glossary term, customer note, research finding, etc.
- **Key details**: the actual content to write up

If the user is vague (e.g., "add this to the knowledge store"), ask one focused question: "What would you like to document?" Then proceed once you have enough to work with.

**When the user provides a document URL:**

First, determine whether they want to (a) just log the URL for future reference, or (b) fully fetch, parse, and integrate the content into the knowledge store. These are very different amounts of work — don't parse a whole document when the user just wants a breadcrumb.

Read context clues:

| Signal | Likely intent |
|---|---|
| "log this," "keep track of," "save the link," "for reference," "so we can find it" | Log only — save the URL with a brief description |
| "add this," "transfer this," "document this," "put this in the knowledge store" (with no other content provided) | Ambiguous — confirm before fetching |
| Pastes a URL alongside actual content or explains what's in it | Parse and integrate — they've done the work of telling you what matters |
| "here is our [X], this will be used for [Y]" | Parse and integrate — they're pointing you at primary source material |

If it's unclear after reading context, ask simply:
> "Do you want me to save the link as a reference, or pull the content and document it fully?"

When logging only: create a short file (or a section in a relevant existing file) with the URL, a one-line description of what it is, and when/how to use it. Don't fetch the document.

---

## Step 2 — Determine Placement

Clone or pull the repo fresh each time to get current structure:

```bash
cd /tmp && rm -rf knowledge && git clone https://github.com/KeywellAI/knowledge.git
```

Then scan the structure:
```bash
find /tmp/knowledge -name "*.md" | grep -v ".git" | sort
```

Use this routing table (from the repo's README) to pick the right folder:

| Content type | Target folder |
|---|---|
| Why we made a product or architecture decision | `product/decisions/` or `engineering/architecture/` |
| How a feature is supposed to work | `product/features/` |
| How to run a deploy, rollback, or incident response | `engineering/runbooks/` |
| Technical standards, coding conventions, PR process | `engineering/standards/` |
| System design, data models, integrations | `engineering/architecture/` |
| What a data source contains and how to use it | `data/sources/` |
| Definition of a clinical or business term | `data/glossary/` |
| How we talk about Keywell to customers | `go-to-market/messaging/` |
| Notes on a specific customer or prospect | `go-to-market/customers/` |
| Email templates, pitch notes, outreach scripts | `go-to-market/templates/` |
| General conference info (new conference, typical costs, CFP patterns) | `go-to-market/conferences/index.md` |
| Specific confirmed dates for a conference in a given year | `go-to-market/conferences/YYYY.md` |
| New hire guides | `operations/onboarding/` |
| Recurring processes (planning, retros, reviews) | `operations/processes/` |
| HR, security, company policies | `operations/policies/` |
| Industry landscape, trends, TAM analysis | `research/market/` |
| User interviews, personas, and insights | `research/users/` |

**When in doubt**, read the README at `/tmp/knowledge/README.md` and any existing files in candidate folders to see what's already there and where this content fits best.

**Choosing a filename**: lowercase with hyphens, descriptive, one topic per file. Examples: `claims-data-source.md`, `pr-process.md`, `acme-health-customer.md`.

**Existing file vs. new file**: If the topic clearly belongs in a file that already exists, append or update that file rather than creating a new one.

---

## Step 3 — Check for Conflicts

Before drafting, search the cloned repo for any existing content that touches the same topic. The goal is to catch contradictions — cases where you're about to write something that disagrees with what's already there.

**Search for related content:**

```bash
# Search by key terms from the new content
grep -r "[key term]" /tmp/knowledge --include="*.md" -l

# Read any files that look relevant
cat /tmp/knowledge/[matching-file.md]
```

Cast a reasonably wide net — if you're adding information about brand colors, search for "color", "brand", "palette", "hex", etc. across the whole repo, not just the obvious folder.

**Conflict types and how to handle each:**

| Situation | What to do |
|---|---|
| New info supersedes old (old is stale) | Update or replace the old content in the same commit; don't leave contradictory versions in the repo |
| Genuine ambiguity (both could be true in different contexts) | Clarify scope in both places — e.g., "legacy brand" vs. "current brand", "v1 pricing" vs. "v2 pricing" |
| Near-duplicate (same topic, slightly different wording) | Consolidate into one canonical entry; remove the weaker version |
| Outright contradiction (one must be wrong) | Surface it to the user before writing anything |

**When to stop and ask the user:**

If you find a direct contradiction and you can't determine from context which version is current, pause and say:

> "Before I save this, I found something that conflicts with what you've shared. [Quote or describe the existing note and where it lives.] Which is correct — the existing version, what you've just told me, or is there a distinction I'm missing?"

Once you have clarity, proceed: update the old content, archive it, or add context that disambiguates. Never silently create a second version that contradicts the first.

**Archiving stale content:**

If the old information is clearly outdated rather than wrong, move it rather than delete it:

```bash
mkdir -p /tmp/knowledge/[folder]/archive
mv /tmp/knowledge/[folder]/old-file.md /tmp/knowledge/[folder]/archive/old-file.md
```

Add a one-line note at the top of the archived file:
```markdown
> **Archived [YYYY-MM-DD]** — superseded by [link to new doc].
```

---

## Step 4 — Draft the Doc

Follow Keywell's markdown conventions:

```markdown
# Title (Title Case)

Last updated: YYYY-MM-DD    ← include for runbooks, processes, policies
Owner: Name / Team          ← include when there's a clear DRI

One-sentence summary of what this doc covers.

---

## Section Heading

Content here...
```

**Style notes:**
- Write to stay useful over time — decisions, processes, standards, context
- Keep docs focused on one topic; link to related docs rather than duplicating
- Use tables for structured comparisons
- Use code blocks for commands, config, and code samples
- Be direct; skip filler phrases

**Content-type templates** — apply the right one:

### Decision / ADR
```markdown
# Decision: [What Was Decided]

Last updated: YYYY-MM-DD
Owner: [Name]

## Context
What situation prompted this decision?

## Decision
What did we decide?

## Rationale
Why this option over alternatives?

## Consequences
What does this mean going forward? What tradeoffs are we accepting?
```

### Runbook
```markdown
# Runbook: [Process Name]

Last updated: YYYY-MM-DD
Owner: [Team]

## When to use this
[Trigger condition]

## Prerequisites
- [What you need before starting]

## Steps
1. Step one
2. Step two
...

## Rollback / If something goes wrong
[Recovery steps]
```

### Data Source
```markdown
# Data Source: [Name]

Last updated: YYYY-MM-DD
Owner: Data

## What it is
[Description]

## What it contains
[Tables, fields, key concepts]

## How to access it
[Connection, tooling, location]

## Common use cases
[What teams use this for]

## Gotchas / Known issues
[Edge cases, data quality issues]
```

### Glossary Term
```markdown
# [Term]

**Category:** Clinical / Business / Technical

**Definition:**
[Clear, precise definition in 1-3 sentences]

**Also known as:** [Aliases, if any]

**Related terms:** [Links to related glossary entries]

**Context:** [Why this term matters for Keywell]
```

### Conference Entry

Conference information always requires **two writes** — one to the general index and one to the annual page. Never write to only one.

**When adding a new conference to the roster** (not yet in the index):
1. Add a row to the table in `go-to-market/conferences/index.md` with typical month, cost range, CFP timing
2. Add a row to `go-to-market/conferences/YYYY.md` (current or specified year) with any confirmed specific dates

**When adding specific dates for an existing conference:**
1. Update `go-to-market/conferences/YYYY.md` — fill in confirmed dates, location, registration deadline, CFP deadline, attending status
2. If the general info in `index.md` is stale or wrong (e.g., typical month has shifted), update that too

**Annual page row format:**
```markdown
| [Conference Name] | [Confirmed dates or "TBD (typically [Month])"] | [City, State] | [Date or TBD] | [Date or TBD] | [Yes / No / TBD] | [Any notes] |
```

**Index table row format:**
```markdown
| [Conference Name] | [National/Regional] | [Month] | [Typical City, State] | [$X–$Y] | [~Month (prior yr) or Varies] | [$X exhibit; $Y–$Z sponsorship] |
```

**Create a new annual page** if `go-to-market/conferences/YYYY.md` doesn't exist yet — copy the header and table structure from an existing year file.

### Customer Note
```markdown
# [Customer / Prospect Name]

Last updated: YYYY-MM-DD
Owner: [AE / CSM Name]

## Overview
[Who they are, what they do, why they matter]

## Use case
[What they're trying to solve with Keywell]

## Key contacts
| Name | Role | Notes |
|---|---|---|

## Status
[Prospect / Active / Churned — and current stage]

## Notes
[Free-form notes, meeting summaries, context]
```

---

## Step 5 — Confirm with User

Show the user what you're about to save — keep it simple and jargon-free:

> "Here's what I'll add to the knowledge store:"
> [show the drafted content in a readable way]
> "Does this look right, or would you like to change anything before I save it?"

For small additions (a glossary term, a quick customer note) you can skip ahead and confirm *after* saving instead — just tell them what you did.

---

## Step 6 — Save to the Knowledge Store

This runs entirely behind the scenes. The user doesn't need to know any git commands — just do it and report back clearly when done.

**Decide where it goes:**
- **Straight to `main`** (most things): new docs, glossary terms, customer notes, research notes, process docs, runbooks, feature specs
- **Branch for review** (sensitive or shared docs): changes to `engineering/` architecture or standards, `operations/policies/`, or significant edits to an existing doc others depend on

**Run the save:**

```bash
cd /tmp/knowledge
git config user.email "claude@keywell.ai"
git config user.name "Claude (Keywell AI)"
mkdir -p [target-folder]
cat > [target-folder/filename.md] << 'EOF'
[content]
EOF
git add [target-folder/filename.md]
git commit -m "docs: add [brief description]"
git push origin main
```

For a branch (review-required docs):
```bash
cd /tmp/knowledge
git config user.email "claude@keywell.ai"
git config user.name "Claude (Keywell AI)"
BRANCH="docs/$(date +%Y%m%d)-[short-slug]"
git checkout -b "$BRANCH"
mkdir -p [target-folder]
cat > [target-folder/filename.md] << 'EOF'
[content]
EOF
git add [target-folder/filename.md]
git commit -m "docs: add [brief description]"
git push origin "$BRANCH"
```

**After saving, tell the user in plain language:**

For a direct push:
> "Done! I saved that to the knowledge store under **[folder/filename.md]**. You can view it at https://github.com/KeywellAI/knowledge/blob/main/[folder/filename.md]."

For a branch:
> "I've drafted that in the knowledge store and it's ready for a quick review before it goes live. You (or anyone on the team) can approve it here: https://github.com/KeywellAI/knowledge/compare/[branch-name] — just click 'Create pull request' and then 'Merge' when it looks good."

Never mention git, branches, commits, or `main` to the user unless they ask. Just tell them where to find it or what action (if any) they need to take.

---

## Error Handling

- **Push fails (auth)**: Git and Claude Code permissions are configured in Keywell's org settings. If push still fails, let the user know: "I wasn't able to save that — it looks like there may be a permissions issue. Can you check with your team that Claude Code has access to the knowledge repo?"
- **Folder doesn't exist**: Create it with `mkdir -p` — new folders are fine, the repo is organized by directory.
- **Ambiguous placement**: When genuinely unclear, ask simply: "Should this live under [Option A] or [Option B]?" — no need to explain the folder structure.
- **Updating an existing file**: Read the file first, merge the new content thoughtfully, then write the whole file back. Don't just append if it would break the doc's structure.
