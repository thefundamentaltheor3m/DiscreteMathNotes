---
name: integrate
description: Absorb one lecture's raw notes into the structured chapter/section hierarchy of these discrete mathematics notes. Use when the user has just taken notes in a throwaway "Lecture <date>" section and wants them redistributed by topic, matching the existing expository style, boxed environments, numbering, and labels. Triggers on "/integrate", "integrate my notes", "integrate today's lecture", "fold in the last lecture".
---

# Integrating a lecture into the notes

Raw notes are taken linearly, in lecture order. The notes themselves are organised
by topic. This skill is the translation between the two: it takes one lecture's
worth of unsorted material and distributes it into the right chapters, sections and
subsections, writing whatever connecting prose is needed to make the result read as
though it had always been there.

Read `CLAUDE.md` first — it holds the build commands, the preamble layout, and the
authoring conventions this skill must reproduce. Everything below assumes it.

## The staging convention

A raw lecture lives as an ordinary section file inside the chapter that was current
during the lecture:

```
Chapters/1_Logic/1_4_Lecture_0824.tex     <- raw; \section{Lecture 2026-08-24}
```

Recognise a raw file by `Lecture_` in its basename. It is `\input` by its chapter
file like any other section, so the notes always compile. **Integration dissolves
it**: its content is redistributed and the file and its `\input` line are removed.

If the user names a file or a date, use that. Otherwise glob
`Chapters/**/*Lecture_*.tex`; if exactly one exists, that is the target. If several
exist, list them and ask which to integrate — do not guess, and do not integrate
several at once unless asked.

## Procedure

### 1. Build the ledger

Before changing anything, enumerate **every** discrete piece of the raw file into a
checklist: each theorem-like environment, each displayed derivation, each figure or
TikZ picture, each paragraph of prose, each aside. Give every item a short handle
and quote its opening words. Keep this ledger for the rest of the run. It is the
only guard against silently dropping something, and the raw file is deleted at the
end, so an unledgered item is a lost item.

### 2. Read the surrounding notes

- `TOPICS.md` — the running topic map (see below). The primary placement authority.
- `main.tex` — chapter order and which chapters are commented out.
- Every chapter file, and any section file the ledger might touch.
- `TeX_Setup/shortcuts.tex` and `TeX_Setup/environments.tex` — the available macro
  and environment vocabulary. Grep these before writing raw math; the notes have a
  house macro for most things.

### 3. Plan, and get it approved

Produce a plan and **stop for confirmation before writing anything**. The plan states,
for each ledger item, where it goes and why; then separately lists

- new sections or subsections to create, with their titles,
- existing material to be moved, quoting what and from where to where,
- new linking prose to be written, with a sentence on what each passage will argue,
- anything you cannot place confidently.

Placement is editorial judgment and the user is the editor. Never skip this step,
even when the answer looks obvious.

For items you genuinely cannot place, prefer parking them over guessing: leave them
in a clearly-marked holding section and record them under `## Unplaced` in
`TOPICS.md`. A wrong confident placement is worse than a flagged one.

### 4. Apply

Working rules, in order of importance:

**Never lose or alter mathematics.** Definitions, theorem/lemma/proposition
statements, and proofs move *verbatim* — copy them, do not retype or paraphrase them.
If a statement seems wrong or incomplete, move it unchanged and flag it in the report;
do not fix it silently.

**Rewrite freely at the level of connective tissue.** Transitions, motivating
sentences, section titles and ordering are yours to adjust so the result reads
continuously. This is the whole point of the skill — a purely additive integration
would leave the notes a pile of lectures.

**Never delete a statement.** Not a duplicate, not a triviality, not an aside. If two
lectures state the same result, merge them into one environment, keep the stronger or
better-worded statement, and say so in the report.

Then, mechanically:

- Match the existing prose voice: first-person plural ("we now show"), unindented
  paragraphs, sentences that carry the argument between environments rather than
  bare lists of results.
- Use the **boxed** environment for every theorem-like item (`boxdefinition`,
  `boxtheorem`, `boxlemma`, `boxexample`, `boxexercise`, …) — see `CLAUDE.md` for the
  full family. Raw notes are usually written loosely; converting them is expected.
- Replace ad-hoc math with house macros: `\parenth`, `\set`, `\setst`, `\abs`,
  `\floor`, `\ceil`, `\R`, `\Z`, `\N`, `\pgcd`, `\Sym`, and so on. Add a genuinely
  new macro to `shortcuts.tex` rather than defining it inline.
- Mark a gap the lecture left — a proof not given, a case not covered — with `\sorry`.
- One file per section, named `<chapter>_<section>_<Topic>.tex`, `\input` from the
  chapter file in reading order. Quote paths: directory names may contain spaces.
- Label new chapters `Ch<N>:CH`, sections `Ch<N>:S<M>`, and named results
  `Ch<N>:<handle>`, following the existing `Ch1:CH` pattern — but if the notes have
  settled on a different scheme by the time you read them, follow the notes.
  Cross-reference with `\cref`, and add references both ways when a new result
  depends on an older one.
- Remember results are numbered per *section*, so moving a theorem across a section
  boundary renumbers it. Grep for stale `\cref`s to anything you moved.
- Delete the raw file and its `\input` line last, once every ledger item is placed.

### 5. Update TOPICS.md

The topic map is a plain outline: chapters mapping to directories, sections beneath
them, each annotated with the lecture date that supplied it, plus a trailing
`## Unplaced` list. Create it on first run if absent. Add sections the syllabus
implies but no lecture has reached yet, marked `(empty)` — they are what tells the
next integration where a topic is heading.

```
## 1. Logic  -> Chapters/1_Logic/
  1.1 Propositions        [2026-08-24]
  1.2 Truth tables        [2026-08-24]
  1.3 Quantifiers         (empty)

## Unplaced
  pigeonhole (mentioned 2026-08-26)
```

### 6. Verify

1. **Ledger check** — walk the ledger and name the file and section each item landed
   in. Anything unaccounted for is a bug; find it before continuing.
2. **Build** — `latexmk -pdf -outdir=TeX_Outputs main.tex`. It must compile. Check
   the log for undefined references and duplicate labels, which are the usual
   symptoms of a botched move.
3. Refresh the committed `TeX_Outputs/main.pdf` (it is tracked deliberately).

### 7. Branch, commit, PR

```bash
git checkout -b integrate/<lecture-date>
git add -A && git commit    # subject: "Integrate lecture of <date>"
git push -u origin integrate/<lecture-date>
gh pr create --fill         # if gh is unavailable, print the compare URL instead:
                            # https://github.com/thefundamentaltheor3m/DiscreteMathNotes/compare/main...integrate/<date>
```

Never integrate directly on `main`. The PR body should carry the substance of the
report below, so the diff is reviewable without re-deriving your reasoning.

## Report back

Close with: where each group of material went; every existing passage you moved or
rewrote, and why; the linking prose you added; anything left unplaced or flagged;
and the build result. Be specific about the edits to existing content — those are
the ones the user most needs to check, and burying them defeats the propose-then-apply
step.

## First run

The repository starts from a template whose chapters are placeholders
(`An Introduction to the Theory of Introductions`, `Another Chapter`,
`0_Overview.tex`) and whose `main.tex` still carries template metadata
(`\COURSENUMBER`, `\REPONAME`, …). On the first integration, offer to clear the
placeholder chapters and set the real course metadata — but ask first, and never
delete a chapter that has acquired real content.
