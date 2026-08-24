# Research Knowledge Manager

This directory is an Agent Skill. The full instructions live in `SKILL.md`, with details in
`references/`.

**If your runtime loads skills on demand** (Claude Code, Codex, Cursor, Gemini CLI, Copilot,
Cline, Amp, Warp, OpenCode, Antigravity, Windsurf …), you do not need this file — read
`SKILL.md` when a task matches its description.

**If your runtime does not read `SKILL.md`** (Zed, Aider, Augment, Trae, Kiro …), this file is
the entry point. Read `SKILL.md` at the start of any task involving research material, notes, or
a knowledge vault. The condensed contract below is enough to not do damage in the meantime; it
is not a substitute for reading it.

## Condensed contract

The job is to turn research material into atomic, evidence-linked notes that stay reusable —
not to summarise documents.

**Four rules that never bend:**

1. **Sources are immutable.** Never edit, move, or delete an original PDF, capture, or dataset.
2. **One note, one concept.** `critical-current-density.md`, never `paper-A-summary.md`.
3. **No claim without a source.** Record source, author, year, page, figure. What you cannot
   confirm is marked `unverified` and reported. Never invent a citation or page number.
4. **Links must mean something.** Link real relationships; never pad a graph.

**Before acting:** locate the vault (ask if unknown — never guess a path), read `MEMORY.md` and
`Home.md` if present, and detect your own capabilities rather than assuming a tool exists by
name. If you have tools for an Obsidian-style vault, use them; otherwise use plain file I/O.

**Vault layout:** `00-Inbox/` `10-Sources/` (read-only) `20-Cards/` `30-Projects/`
`40-Outputs/` `80-Templates/` `90-Archive/`, plus `Home.md`, `MEMORY.md`, `Knowledge-Log.md`.

**Never, without explicit confirmation:** delete or overwrite a file, restructure the vault,
merge notes, or move things in bulk. Uncertain changes are written to `00-Inbox/Needs-Review.md`
as questions instead.

## Reusing this in your own project

Copy the section above into your project's `AGENTS.md`, `.rules`, or `CONVENTIONS.md`, and keep
this skill directory somewhere the agent can read `SKILL.md` and `references/` from.
