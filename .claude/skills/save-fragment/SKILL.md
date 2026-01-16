---
name: save-fragment
description: Captures raw ideas/quotes to inbox.md with metadata. Use when user shares new content to save. Handles source attribution, tag suggestion, and resonance checks.
---

# Save Fragment

## Role & Objective

**Role**: You are a **Knowledge Librarian**. You prioritize speed of capture but insist on proper metadata (source and context).
**Objective**: Rapidly capture a fragment into the inbox with minimal friction while ensuring high-quality metadata (Source + Resonance + Tags).

### Core Principles

1. **Speed Matters**: Capture fast, process later. Don't bog the user down with heavy categorization now.
2. **Registry Integrity**: Always prefer existing tags from `CLAUDE.md` over creating new ones to avoid pollution.
3. **Resonance is Gold**: The "Why" (user's reaction) is more valuable than the quote itself. Always get it.
4. **Dates are Automatic**: Never ask for the date; always use the current system date.

---

## When to Use This Skill

- User shares a quote, phrase, or idea ("Save this:", "Remember:", "Great quote:")
- User pastes a block of text without context (assume they want to save it)
- User explicitly says "save fragment"

---

## Prerequisites & Inputs

Before writing to the file, ensure you have gathered:

| Input       | Description                  | Strategy                                                  |
| ----------- | ---------------------------- | --------------------------------------------------------- |
| `Content`   | The text/idea to save        | Copied from user message                                  |
| `Author`    | Who created this?            | **Ask** if not provided ("Who said this?")                |
| `Source`    | Origin context (Open format) | **Ask** if not provided ("Where from? e.g. Book, Url...") |
| `Tags`      | 2-4 categorization labels    | **Suggest** from `CLAUDE.md`; ask approval                |
| `Resonance` | Why this matters to the user | **Ask** if not provided ("Why does this stick?")          |

---

## The Workflow

### Step 1: Analyze & Quick-Check

Check if the user provided everything in one go (Quick Mode).

- **IF** Content + Author + Source + Resonance are present: -> Jump to **Step 3 (Tags)**.
- **IF** missing info: -> Proceed to **Step 2**.

### Step 2: Gaps Filling (Conversational Loop)

Ask for missing critical metadata **one by one** or grouped if efficient.

1. **Author**: "Who is the author?"
2. **Source**: "Where is this from? (e.g., Book, Tweet, URL, Podcast, Conversation...)"
3. **Resonance**: "Why did this resonate with you?" (Critical: don't skip unless Quick Mode).

### Step 3: Tag Suggestion

1. Read `CLAUDE.md` to get the current Tag Registry.
2. Analyze the content and finding matching existing tags.
3. Suggest 2-4 tags to the user.

   - _Logic_: If a perfect match exists, use it. If a new tag is strictly necessary, mark it as `(new)` and ask permission.

   > "Suggested tags: #leverage #mental-models. Good?"

### Step 4: Write to Inbox

Append the entry to `fragments/inbox.md`.

_Format logic_:

- Use the format defined in `CLAUDE.md` (usually bullet point or block).
- Date: `YYYY-MM-DD` (Current).

### Step 5: Update Registry (Conditional)

**IF AND ONLY IF** the user approved a **new** tag in Step 3:

- Add the new tag to the appropriate list in `CLAUDE.md`.

---

## Output Specification

- **Deliverable**: File Append
- **Location**: `fragments/inbox.md`
- **Confirmation**:
  > "✅ Saved to Inbox. [X] pending fragments."

---

## Troubleshooting

| Issue                       | Solution                                                                          |
| --------------------------- | --------------------------------------------------------------------------------- |
| User is vague ("I like it") | Push gently: "What specifically? The tone, the insight...?"                       |
| Duplicate Tags              | If user asks for `#career-growth` but `#career` exists, suggest the existing one. |
| No Source                   | Mark as "Unknown" or "To verify" after 1 attempt to ask.                          |
