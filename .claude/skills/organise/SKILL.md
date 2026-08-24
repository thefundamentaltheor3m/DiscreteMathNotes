---
name: organise
description: Refactor the chapter, section and subsection structure of these discrete mathematics notes so that what is already written sits where it belongs, and maintain TOPICS.md as the record of that structure. Use when the notes have outgrown or drifted from their current arrangement — a section doing the work of three, a chapter whose title no longer describes its contents, material in the wrong place, a heading level that should not exist — or when TOPICS.md needs rebuilding. Triggers on "/organise", "organise the notes", "reorganise the chapters", "restructure this", "sort out TOPICS.md". Not for absorbing a new lecture: that is /integrate.
---

# Organising the notes

There is no syllabus for this course. The structure of `Chapters/` was therefore
never designed — it accreted, one lecture at a time, and every lecture was placed
using only the information available before the next one happened. This skill is the
correction pass: it takes the notes as they stand and rearranges *them*, adding
nothing and removing nothing.

Read these first, in order:

- `.claude/ORGANISATION.md` — what earns a chapter, a section and a subsection, what
  the corpus actually measures, the naming conventions, and the format and ownership
  of `TOPICS.md`. **This skill's job is to make the document match that file.**
- `CLAUDE.md` — build commands, preamble layout, authoring conventions.
- `.claude/STYLE.md` — the voice, for the connecting prose that restructuring
  inevitably needs rewritten.

## Scope: what this skill is and is not

`/organise` and `/integrate` share their format, their guiding principles and their
respect for the author's mathematics. They do not share a scope, and confusing the
two is the main way either can do damage.

| | `/integrate` | `/organise` |
| --- | --- | --- |
| Input | one lecture's raw notes | the notes as they already stand |
| Adds material | yes, that is the point | **never** |
| Restructures | only enough to house the new material | yes, that is the point |
| `TOPICS.md` | appends its own entries | **owns the file** |
| Ends with | the raw file dissolved | the same content, better arranged |

**This skill adds no mathematics and no exposition beyond connecting prose.** If you
find yourself writing a definition, finishing a proof, or supplying an example, stop:
that is `/address-comments` or a lecture's job, not this one. The content going in is
the content coming out.

**This skill deletes nothing.** Not a duplicate, not a triviality, not a stray aside.
Restructuring that loses a sentence has failed, however much better the outline
looks.

If the notes contain a `Lecture_*.tex` staging file, this skill is the wrong one —
that file is `/integrate`'s. Say so and stop. Running `/organise` first on unintegrated
material would restructure around content that is about to move anyway.

## Procedure

### 1. Take inventory

Before forming any opinion, measure. The judgment calls later are all comparisons
against `ORGANISATION.md`'s numbers, and eyeballing gets them wrong.

For every chapter, section and subsection: its title, its file, its line count, its
count of boxed environments, and a one-line summary of what it covers. Also record

- every `\subsubsection` (there should be none),
- every section with exactly one subsection (the shape `ORGANISATION.md` says to
  avoid),
- every chapter or section whose title no longer describes its contents,
- every label, and every `\Cref` that points at one — this is the map of what
  renumbering will break.

Keep the inventory for the rest of the run. Nothing may be dropped, so an
unrecorded item is an item at risk.

### 2. Read the corpus, not just the notes

The standard is the author's other notes, not your instincts about how a textbook
should look. `ORGANISATION.md` summarises them, but when a specific call is close —
is this one subsection or two? does this deserve a section? — go and look at how a
comparable piece of material is handled in [TopologyNotes][t], [LogicNotes][l],
[RepTheoryEPFL][r] or [LieAlgebrasNotes][a]. Find the nearest analogue and follow it.

[t]: https://github.com/thefundamentaltheor3m/TopologyNotes
[l]: https://github.com/thefundamentaltheor3m/LogicNotes
[r]: https://github.com/thefundamentaltheor3m/RepTheoryEPFL
[a]: https://github.com/thefundamentaltheor3m/LieAlgebrasNotes

Two questions worth asking of the corpus every time:

- **Is this material one idea or several?** That is the subsection test, and the
  corpus is full of worked examples of where the author draws the line.
- **Would the author have given this its own heading?** Median subsection is 48
  lines and 3 environments. Below that, the corpus uses a paragraph break.

### 3. Diagnose

State what is wrong with the current arrangement, as a list of specific findings,
each with the measurement behind it. "Section 1.2 is 45 lines with 4 environments and
one subsection, against a corpus median of 148 lines and 3 subsections" is a finding.
"The structure could be cleaner" is not.

Then say what is *right*, and leave it alone. A correction pass that rewrites
everything it touches is indistinguishable from noise, and the author has to review
every line of it.

Where the notes cannot satisfy the norms at all — early in a course they cannot —
apply the self-healing rule from `ORGANISATION.md`: favour the arrangement whose
deviations resolve themselves as lectures arrive, and record the deviation in
`TOPICS.md` with the condition that will end it.

### 4. Plan, and get it approved

Produce the plan and **stop for confirmation before moving anything.** The plan
states:

- the target outline, in full, as it will appear in `TOPICS.md`;
- for each move: what content, from where, to where, and which finding it answers;
- every heading created, deleted, promoted or demoted, with its title;
- every file created, renamed or deleted;
- every renumbering the move causes, and every `\Cref` that will need checking;
- the connecting prose to be rewritten, with a sentence on what each passage will
  now have to do — a section that acquires a new neighbour usually needs its opening
  sentence changed;
- anything you have decided to leave alone despite it being off-norm, and why.

Structure is editorial judgment and the author is the editor. Restructuring is also
the most expensive thing to undo in these notes, because it renumbers results. Never
skip this step, even when the diagnosis looks unarguable.

If the run is happening in a context where you cannot stop and ask — an automated
pass, a one-shot request for a finished branch — then say so plainly, apply the
plan, and put the full plan and its rationale in the commit message and the pull
request body instead. What is not acceptable is moving things silently.

### 5. Apply

Working rules, in order of importance:

**Content is invariant.** Every definition, statement, proof, display, figure and
paragraph comes out the other side character-for-character identical, unless it is
connecting prose. Move by cutting and pasting whole blocks; do not retype, do not
"tidy while moving". If a passage seems wrong, leave it wrong and report it.

**Rewrite connecting tissue freely, and only that.** Section and subsection titles,
opening and closing sentences, the one-sentence bridges that carry the reader between
environments, chapter intro prose. These are what make a rearrangement read as though
it had always been that way, and rewriting them is the whole point. `STYLE.md` has
the voice.

**Move whole ideas.** Do not split a definition from the example that motivates it,
or a theorem from its proof, across a heading boundary. If a section boundary would
land in the middle of an argument, the boundary is in the wrong place.

**Preserve labels wherever possible.** A label's `Ch<N>:` prefix should match its new
chapter, so a cross-chapter move means renaming labels and updating every `\Cref` to
them. A same-chapter move should leave labels untouched — renaming a label nobody
asked you to rename is churn that shows up in the diff and helps nobody.

**File and directory names follow the content.** A section that moves to slot 1.3
becomes `1_3_<Abbrev>.tex`, and its `\input` moves with it. Use `git mv` so the
rename is visible in the diff rather than appearing as a delete plus an add. Quote
paths: some directory names contain spaces. Chapter 1's directory stays `1_Intro`
regardless of the chapter's title — see `ORGANISATION.md`.

**No subsubsections, ever.** If the plan wanted one, the section above it was wrong.

**Placeholders left over from the template** — `Chapters/0_Overview.tex`,
`Chapters/2_Another Chapter/`, `Chapters/Appendices/` — are in scope for this skill
in a way they are not for `/integrate`, since they are a structural problem. Propose
clearing them; never clear a file that has acquired real content.

### 6. Rebuild TOPICS.md

`/organise` owns this file; rewrite it to describe the new structure, in the format
`ORGANISATION.md` specifies. In particular:

- the leading inference note about where the structure looks to be heading, marked as
  inference and left open for the next run to disagree with;
- every line traceable to a lecture, with its date;
- `## Signposted` kept separate from the outline, so a topic a lecture merely pointed
  at cannot harden into a section nobody asked for;
- any deliberate deviation from the norms, with the condition that will end it.

### 7. Verify

1. **Inventory check** — walk the inventory and name the file and heading each item
   now sits under. Anything unaccounted for is a bug; find it before continuing.
2. **Content diff** — `git diff` and confirm that every changed line of mathematics
   is a pure move. `git diff --stat` should show a lot of renames and few
   modifications outside titles and bridging prose. This is the check that catches
   the failure mode of this skill, which is rewriting while rearranging.
3. **Build** — `latexmk -pdf -outdir=TeX_Outputs main.tex`. Read the log for
   undefined references and duplicate labels: those are the symptoms of a botched
   move. Grep for `\Cref`s to anything that moved.
4. **Numbering** — check the rendered ToC against the outline in `TOPICS.md`, and
   spot-check that results renumbered the way the plan said they would.
5. **Refresh `TeX_Outputs/main.pdf`** — it is tracked deliberately.

### 8. Branch, commit, PR

Never restructure directly on `main`.

```bash
git checkout -b organise/<short-description>
git add -A && git commit    # subject: "Reorganise <what>"
git push -u origin organise/<short-description>
```

Then attempt the PR — `gh` is on some of the author's machines and not others, so
check rather than assume:

```bash
gh auth status
gh pr create --base main --title "Reorganise <what>" --body-file <file>
```

Write the body to a file so it survives shell quoting, and put the diagnosis and the
plan in it: for a restructuring PR, the rationale *is* the reviewable content, since
the diff is mostly moves. Follow the build with `gh pr checks --watch`; a red build
on `main` breaks the published PDF. If `gh` is unavailable, say so and print the
compare URL instead:

```
https://github.com/thefundamentaltheor3m/DiscreteMathNotes/compare/main...organise/<short-description>
```

## Report back

- **The diagnosis**: each finding, with the measurement behind it.
- **The moves**: what went where, and which finding each one answers.
- **What was left alone**, including anything off-norm you decided to tolerate and
  the condition that would change your mind.
- **Renumbering**: what changed number, and every `\Cref` you checked.
- **Prose you rewrote** — titles, bridges, intros. These are the only places where
  words changed, so they are what the author needs to read.
- **Anything you think is wrong** in the notes, quoted, left unchanged.
- The build result.

Be specific about the prose. In a restructuring pass the moves are mechanical and
verifiable, but the rewritten sentences are yours, and they are the part the author
cannot check from the outline alone.
