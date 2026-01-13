# Fragments Vault

<a href="https://www.serudda.com/skills/fragments"><img src="https://i.ibb.co/TB2TySYc/fragments-vault.jpg" alt="Claude Life Assistant Demo" border="0"></a>

A vault to capture phrases, quotes, and ideas found while reading.

---

## The Problem it Solves

You are deep in the zone, coding or reading documentation, and you find a concept or quote that resonates.

You want to save it, but the friction kills the flow:

- **Context Switching:** Opening Notion, Obsidian, or a notes app breaks your mental state.
- **The "Copy-Paste" Graveyard:** You dump it in a generic "Notes" page and never look at it again because it lacks context (tags, source, _why_ it mattered).
- **Vendor Lock-in:** Your second brain is trapped in a proprietary database instead of plain text files you own.

**Fragments Vault** solves this by bringing your note-taking directly into your terminal workflow, powered by Claude.

## Why use this with Claude Code?

1.  **Zero Friction:** Stay in your terminal. No switching apps. Just a command.
2.  **AI-Powered Taxonomy:** You don't need to manually organize. Claude suggests tags and categories based on the content.
3.  **Git-Backed:** Your thoughts are just Markdown files. Version control them. Diff them. Own them.
4.  **Context Preservation:** The system forces you to answer "Why?" — ensuring that in 6 months, you remember why this fragment mattered.

---

## Structure

This project uses a flat file structure for simplicity.

> **Note:** The files `career.md`, `building.md`, and `life.md` are just **examples** of categories. You can rename them, delete them, or add new ones (e.g., `ruby.md`, `marketing.md`) to fit your mental model.

```
fragments/
├── inbox.md         # Where everything arrives (unprocessed)
├── career.md        # Example: Work, money, negotiation
├── building.md      # Example: Side projects, shipping, startups
└── life.md          # Example: Philosophy, values, decisions
```

**inbox.md** is the landing zone. Fragments live there until you process them.
Check `fragments/inbox.md` to see a real-world example of a captured fragment.

---

## How to Capture a Fragment

### Step 1: Invoke the skill

Tell Claude:

- "Save this fragment: [the phrase]"
- "/save-fragment"
- "I want to save this quote"

### Step 2: Answer the questions

Claude will ask you:

1.  **Source** — Where does it come from? (author, book, tweet, article)
2.  **Tags** — It will show you existing tags and suggest some
3.  **Why** — Why did it catch your attention?

### Step 3: Done

The fragment is saved in `inbox.md` with this structure:

```markdown
---
> "The exact phrase here"

**Source**: Naval Ravikant, Twitter
**Tags**: #leverage #value #career
**Why**: Connects with my idea that specialization comes from obsession
**Date**: 2026-01-13

---
```

---

## Tag System

### Why it matters

Tags allow finding related fragments even if they are in different categories. A fragment about #leverage can be in `career.md` or in `building.md` — the tag connects them.

### Available tags

They are in `CLAUDE.md` under "Tags Registry". Before creating a new one, check if something similar already exists.

| Category     | Tags                                                                                          |
| ------------ | --------------------------------------------------------------------------------------------- |
| **Career**   | #salary #negotiation #employers #value #leverage #job-search #promotion #skills #expertise    |
| **Building** | #side-projects #indie #startup #shipping #mvp #build-in-public #product #growth #monetization |
| **Life**     | #honesty #values #relationships #decisions #freedom #minimalism #time #priorities #focus      |

### Creating new tags

If you need a tag that doesn't exist:

1.  Claude will propose it with "(new)"
2.  You confirm
3.  It gets added to the registry in `CLAUDE.md`

This prevents ending up with #career and #carrera and #work meaning the same thing.

---

## The Complete Flow

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   READ ──► FIND PHRASE ──► /save-fragment ──► inbox.md      │
│                                                             │
│   (later, when you have time)                               │
│                                                             │
│   /process-fragments ──► categorize ──► career.md           │
│                                         building.md         │
│                                         life.md             │
│                                                             │
│   (when you need inspiration)                               │
│                                                             │
│   /browse-fragments ──► search by tag ──► find              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Available Skills

| Skill                | What it does                                   |
| -------------------- | ---------------------------------------------- |
| `/save-fragment`     | Quick capture to inbox                         |
| `/process-fragments` | Process inbox and move to categories (pending) |
| `/browse-fragments`  | Search and explore fragments (pending)         |

---

## Tips

### The "Why" is the most valuable part

In 2 years you will read "The best time to plant a tree was 20 years ago" and you won't remember why you saved it. The "why" gives you context:

- "Reminded me that it's always a good time to start"
- "Contradicts the idea that you need the perfect moment"

### Don't worry about categorizing when capturing

Everything goes to inbox first. Categorize later, when you have 5-10 fragments accumulated. Capture should be fast and frictionless.

### Tags cross categories

A fragment with #leverage can be in `career.md` (leverage in your job) or in `building.md` (leverage in your product). The tag allows you to find all fragments about that concept regardless of where they live.
