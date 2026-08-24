# Templates

Write these into `80-Templates/` when setting up a vault. Note content follows the user's
language; the headings below are the skeleton, not a requirement to write in English.

## Atomic note

The unit of the whole system. One durable question per note.

```markdown
# <Concept name, not a paper title>

## Claim

The single most important judgement, in one sentence. If it takes a paragraph,
this is probably two notes.

## Why it holds

The mechanism or reasoning. Where it applies. Where it stops applying.
Boundary conditions matter more than the claim itself.

## Evidence

- Source:
- Author:
- Year:
- Page / section:
- Figure / table:

## Related

[[prerequisite-concept]] — why it is a prerequisite
[[competing-explanation]] — where they disagree

## So what

How this changes the next decision, experiment, or piece of writing.
If nothing, say so — some notes are pure background and that is fine.
```

Two failure modes to avoid:

- **The claim is a topic, not a judgement.** "Interface stability" is a topic. "Artificial SEI
  layers raise critical current density by suppressing dendrite nucleation, but only below
  60 °C" is a judgement.
- **The `Related` links carry no reason.** A bare `[[x]]` ages into noise. One clause on why
  makes it survive.

## Literature note

One per source. It is a landing pad, not the asset — the notes extracted from it are.

```markdown
# <Source title>

- Authors:
- Year / venue:
- File: [[10-Sources/<filename>]]
- Read on:

## Question

What problem the authors set out to solve.

## Method

How they attacked it, in enough detail to judge the results.

## Results

What they actually showed, separated from what they claim it means.

## Limitations

Sample size, conditions, assumptions, what the authors admit and what they skip.

## Notes extracted

[[concept-a]] [[concept-b]] [[concept-c]]

## Unverified

Anything you could not confirm from the source itself.
```

## MEMORY.md starter

```markdown
# How to work in this vault

- Read this file and Home.md before every task.
- Vault path: <absolute path>
- Note language: <the user's language>

## Rules

- Never modify, move, or delete anything in 10-Sources/.
- New material lands in 00-Inbox/ first.
- One note, one concept. No paper-summary notes in 20-Cards/.
- Every claim carries source, author, year, page, figure.
- Anything unconfirmed is marked `unverified` and reported, never guessed.
- Deleting or overwriting requires explicit confirmation first.
- After each task: update Home.md and Knowledge-Log.md.

## Conventions

- Filenames: <English | localised>
- Date format: YYYY-MM-DD
```

## Home.md starter

```markdown
# Home

## Current direction

<one paragraph: what question is being worked on and why>

## Projects

- [[30-Projects/<thread>]] — one line of status

## Recently changed

- YYYY-MM-DD — what changed

## Notes worth re-reading

- [[<note>]] — why it matters
```
