# Building an output

An output is assembled from notes, not written from scratch alongside them. If you find
yourself writing new claims directly into a report, those claims belong in notes first —
otherwise the knowledge leaves with the document.

## Sequence

1. **Establish scope.** What is being produced, for whom, how long, and what it must argue.
2. **Gather the notes.** Search `20-Cards/`, collect what is relevant, and list them before
   writing. If the notes do not cover the argument, say so — do not paper over the gap with
   outside knowledge.
3. **Check the evidence still holds.** A note carrying `unverified` markers cannot silently
   become a confident sentence in a report.
4. **Write, keeping attribution.** Every substantive claim traces to a note, which traces to a
   source. Preserve that chain in the output file.
5. **File it in `40-Outputs/`** with a `Source notes` section listing what it was built from.
6. **Update `Home.md` and `Knowledge-Log.md`.**

## Output header

```markdown
# <Title>

- Produced: YYYY-MM-DD
- For: <venue, meeting, reader>
- Built from: [[note-a]] [[note-b]] [[note-c]]
- Gaps: <what the vault could not support>
```

That `Gaps` line is the point. It tells the next reader — including the user, months later —
exactly which parts of the document rest on the vault and which do not.

## What "traceable" rules out

- A number in a slide with no note behind it
- A citation added to make a paragraph look supported, that no note actually holds
- A confident claim built from a note marked `unverified`
- Filling a gap from general knowledge without labelling it as such

If the user explicitly asks you to draft beyond the vault, do it — but mark those passages so
they can be told apart from the sourced ones.
