# Vault layout

The numeric prefixes sort directories in workflow order. Keep them — they are what keeps the
vault navigable once it passes a few hundred notes.

    00-Inbox/
        Captured but not yet processed. Should trend toward empty.
        Needs-Review.md — open questions, and any change you refused to make unilaterally.

    10-Sources/
        Original PDFs, papers, page captures, course slides, datasets.
        Read-only. One subdirectory per source when a source has several files.

    20-Cards/
        Atomic notes. Flat is fine — search and links do the organising, not folders.
        This is the asset. If everything else were lost, this is what you would want back.

    30-Projects/
        One file per active research thread: the question, current state, open problems,
        and which notes it draws on.

    40-Outputs/
        Drafts, reports, slides, experiment plans. Each output names the notes it was built
        from, so the chain back to sources stays walkable.

    80-Templates/
        Note templates. See templates.md.

    90-Archive/
        Finished or dormant. Never delete — move here.

## Root files

| File | Holds | Never holds |
| --- | --- | --- |
| `Home.md` | Current direction, project entry points, recent changes, notes worth re-reading | Knowledge |
| `MEMORY.md` | How to work: workflow, format, safety rules, judgement calls | Paper content, data, conclusions |
| `Knowledge-Log.md` | Date, task run, files created, files changed, open questions | Analysis |

`MEMORY.md` is the one worth being strict about. It answers *how does the agent behave here*,
so it stays short and stable. The moment it starts accumulating findings it becomes too long to
read at the start of every task, which defeats the whole point of having it.

## Where a given thing belongs

| You have | It goes to |
| --- | --- |
| A PDF the user just dropped | `10-Sources/`, and a stub in `00-Inbox/` if not yet processed |
| "Solid electrolyte interphase forms in the first cycle" | `20-Cards/` — one concept, evidence attached |
| "Summary of Zhang et al. 2024" | Nowhere. Split it into concepts, or it is not a note |
| A meeting decision about which experiment to run next | `30-Projects/<thread>.md` |
| A slide deck you generated | `40-Outputs/`, listing its source notes |
| A note that turned out wrong | Correct it in place and log it. Archive only if the whole topic is dead |

## Localisation

Directory and file names can be localised — a Chinese vault might use `知识库日志.md` for
`Knowledge-Log.md` and `待确认.md` for `Needs-Review.md`. Pick one convention, keep it
consistent, and record the choice in `MEMORY.md` so later sessions follow it.

Note *content* always follows the user's own language regardless of what the filenames are.
