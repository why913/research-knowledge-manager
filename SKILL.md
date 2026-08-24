---
name: research-knowledge-manager
description: Turn research material into a durable, evidence-linked knowledge base of atomic notes. Use when the user wants to process a paper or PDF into notes, set up or maintain a research vault or second brain, answer a question strictly from their own notes, draft a report, paper section, or slides that stays traceable to sources, or audit a knowledge base for duplicates, orphans, and unsourced claims.
license: MIT
compatibility: Needs read/write access to a user-designated vault directory. Uses an Obsidian-style MCP server when one is present, and plain file operations otherwise. No network access required.
metadata:
  author: why913
  version: "1.0"
  homepage: https://github.com/why913/research-knowledge-manager
---

# Research Knowledge Manager

Collecting material is not building knowledge. Material becomes an asset only once it is
distilled into atomic notes, tied to its evidence, connected to what is already known, and
actually used to produce something.

Your job is to run that loop, not to summarise documents.

## Start of every task

1. **Locate the vault.** If the user has not named one, ask. Never guess a directory and
   never create a vault outside the path they give you.
2. **Read the standing rules first**, if they exist: `MEMORY.md`, then `Home.md`, then the
   templates in `80-Templates/`. `MEMORY.md` holds how to work, never what is known.
3. **Detect your capabilities before acting.** If you have tools for browsing or editing an
   Obsidian-style vault (listing vaults, searching notes, reading/writing notes), use them —
   they respect the user's confirmation prompts. Otherwise use ordinary file reads and writes.
   Never assume a specific tool exists by name.

## Four rules that never bend

1. **Sources are immutable.** Never edit, overwrite, move, or delete an original PDF, page
   capture, or dataset. Every generated claim must trace back to untouched evidence.
2. **One note, one concept.** `lithium-interface-side-reactions.md` — not `paper-A-summary.md`.
   A note answers one durable question and gets reused for years. Summaries answer nothing and
   get read once.
3. **No claim without a source.** Every note records where it came from: source, author, year,
   page, figure. If you cannot establish it, write `unverified` and say so in your
   report. Never invent a citation, page number, or figure reference.
4. **Links must mean something.** Link concepts that genuinely relate — prerequisite,
   contradiction, method-to-application. Never manufacture links to make a graph look busy.

## Vault layout

    00-Inbox/        captured, not yet processed
    10-Sources/      original PDFs, papers, captures, course material — read-only
    20-Cards/        atomic notes, the actual asset
    30-Projects/     active research threads
    40-Outputs/      drafts, reports, slides, experiment plans
    80-Templates/    note templates
    90-Archive/      done or dormant
    Home.md          navigation: current direction, entry points, recent work
    MEMORY.md        how you work: rules, format, boundaries — not knowledge
    Knowledge-Log.md log: date, task, files created/changed, open questions

Full layout and the note templates: `references/vault-layout.md`, `references/templates.md`.

## Workflows

**Set up a vault** — list every directory and file you intend to create, confirm nothing gets
overwritten, then create them. Never delete or move anything that already exists.

**Process a source** — read it without modifying it. Extract the research question, method,
results, and limitations. Pull out 3–7 concepts with durable value. For each: search
`20-Cards/` first, extend the existing note if there is one, create it if there is not. Attach
evidence. Link deliberately. Update `Home.md` and the log. Report what you created, why, and
what stayed unverified. Detail: `references/ingest.md`.

**Answer from the vault only** — separate what the notes support with evidence, which notes
back it, where notes disagree, what is missing, and what you inferred. Do not fill gaps with
outside knowledge; name the gap instead.

**Produce an output** — build it from the notes so the chain output → note → original source
stays walkable. Detail: `references/outputs.md`.

**Audit** — check for unprocessed inbox items, duplicate notes, orphans, unsourced claims,
unverified markers, and broken links. Never delete and never restructure the vault on your own
judgement; write anything uncertain to `00-Inbox/Needs-Review.md` and hand back a health report.
Checklist: `references/audit.md`.

## Reference files

Load one only when the task calls for it:

| File | Read it when |
| --- | --- |
| `references/vault-layout.md` | Setting up a vault, or unsure where something belongs |
| `references/templates.md` | Creating a note, literature note, or `MEMORY.md` |
| `references/ingest.md` | Processing a source into notes |
| `references/outputs.md` | Building a report, paper section, or slides |
| `references/audit.md` | Running an audit |
