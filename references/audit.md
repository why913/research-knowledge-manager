# Audit

Run periodically, or when the vault starts feeling unreliable. The output is a report, not a
restructured vault.

## Hard constraints

- **Never delete anything.** Not a duplicate, not an orphan, not an empty file.
- **Never restructure on your own judgement.** Do not rename directories, move notes in bulk,
  or merge notes without saying so and getting agreement.
- Anything uncertain goes into `00-Inbox/Needs-Review.md` as a question, not an action.

An audit that quietly "fixes" things is worse than no audit — the user loses track of what the
vault even claims.

## Checklist

| Check | Looking for |
| --- | --- |
| Inbox backlog | Items in `00-Inbox/` never processed. Note how long they have sat |
| Duplicate notes | Two notes making the same claim under different names. Report, propose a merge, do not merge |
| Orphans | Notes nothing links to and which link nowhere. Often a real gap, sometimes just background |
| Unsourced claims | Notes with an empty or partial `Evidence` block |
| `unverified` markers | Collect all of them with what it would take to confirm each |
| Broken links | `[[targets]]` that resolve to nothing — usually a rename or a note never written |
| Summary notes | Anything in `20-Cards/` that is a paper summary rather than one concept |
| Stale projects | Threads in `30-Projects/` with no movement, that should be archived or revived |
| Outputs without provenance | Files in `40-Outputs/` with no `Built from` list |

## Report format

```markdown
# Vault health — YYYY-MM-DD

## Numbers

- Notes: N  ·  Sources: N  ·  Inbox: N unprocessed
- Unsourced claims: N  ·  unverified markers: N  ·  Broken links: N

## Needs a decision

1. <finding> — <what you propose> — <why you did not just do it>

## Fixed

- <only things that were unambiguous and non-destructive: a broken link
  whose target was obviously renamed, a missing log entry>

## Written to Needs-Review.md

- <questions raised>
```

## What counts as unambiguous enough to fix

Fix without asking: a broken link where the target was clearly renamed and only one candidate
exists; a missing entry in `Knowledge-Log.md`; a typo in a filename you just created this
session.

Everything else — merges, deletions, moves, rewriting a claim, resolving a conflict between two
notes — is reported, not done.
