# Document organisation

How these notes are carved into chapters, sections and subsections, and what
`TOPICS.md` records. `STYLE.md` is the companion: it governs how a passage *reads*,
this file governs where the passage *lives*.

Read by both skills, for different reasons:

- **`/organise`** treats this file as its standard. Its job is to make the document
  match it.
- **`/integrate`** treats it as a constraint. Its job is to put new material where it
  belongs without disturbing what is already there, and this file tells it whether
  the new material fits an existing section or has earned one of its own.

## There is no syllabus

No list of topics for this course exists and none is coming. Nobody knows what
`Chapters/` should eventually look like. Everything below is therefore a description
of how the author's *other* notes ended up, applied as a target — not a plan handed
down from a course outline.

Three consequences run through the whole file:

1. **Structure is provisional and stays provisional.** Early lectures land wherever
   looked right at the time. By lecture ten it may be obviously wrong. That is
   expected, not a failure.
2. **Nothing exists because a discrete mathematics course "usually" covers it.**
   Every chapter, section and `TOPICS.md` line traces to a lecture, or to a lecture
   explicitly saying we would come back to something.
3. **Prefer the arrangement whose mistakes self-heal.** Some structural mistakes
   correct themselves as lectures arrive; others harden. See
   [Which axis to optimise](#which-axis-to-optimise).

## What the corpus actually looks like

Measured over the author's four sibling repositories — [TopologyNotes][t],
[LogicNotes][l], [RepTheoryEPFL][r], [LieAlgebrasNotes][a] — 12,277 lines, 14
chapters, 66 sections, 181 subsections:

| Unit | Lines | Contains | Boxed environments |
| --- | --- | --- | --- |
| **Chapter** | median ≈ 830, range 313–1844 | 2–8 sections, typically 3–6 | — |
| **Section** | median 148, IQR 99–229 | median 3 subsections, IQR 2–3 | median 9, IQR 5–13 |
| **Subsection** | median 48, IQR 30–79 | prose and environments only | median 3, IQR 2–5 |

[t]: https://github.com/thefundamentaltheor3m/TopologyNotes
[l]: https://github.com/thefundamentaltheor3m/LogicNotes
[r]: https://github.com/thefundamentaltheor3m/RepTheoryEPFL
[a]: https://github.com/thefundamentaltheor3m/LieAlgebrasNotes

Two hard facts from the same measurement:

- **There are no subsubsections.** One appears in 12,277 lines. Depth stops at
  subsection; below that, use a paragraph break, or `description`/`enumerate` inside
  an environment. If material seems to need a fourth level, the section above it is
  wrong.
- **A section almost always has at least two subsections.** 54 of 66 sections have
  two or more; 8 have none at all (these are short, single-idea sections) and only 4
  have exactly one. **A section with exactly one subsection is the shape to avoid**
  — either the subsection heading is redundant, or the section should be a
  subsection of something larger.

## What earns each level

### Subsection

**One idea, developed once.** A definition with its examples; a single theorem with
its proof; one construction. Median 48 lines and 3 boxed environments — if a
prospective subsection has one environment and four lines of prose, it is a
paragraph, not a subsection.

The test: can you name it in a noun phrase without "and"? "Directed Sets and Nets"
passes because nets are defined *in terms of* directed sets. "Colourings and
Ramsey Numbers" does not.

### Section

**A coherent line of argument, made of two or more such ideas.** Median 148 lines, 9
environments, 2–3 subsections. A section is what you would set as a single reading:
the subsections are the steps, and the section title says what they add up to.

Reach for a new section when the material genuinely does not continue the argument of
any existing one. Reach for a new *subsection* of an existing section when it does.
Under ~100 lines and 5 environments, prefer the subsection.

### Chapter

**A topic area that the course will spend weeks on.** Median 830 lines, 3–6 sections.
A chapter is a big unit: no single lecture is a chapter, and a chapter with one
section is a chapter that has not happened yet.

This is the level where the absent syllabus hurts most, because a new chapter is a
bet on where the course is going, and the bet is expensive to unwind — renaming or
splitting a chapter renumbers every result under it. So:

- Do not open a chapter for material that could be a section of an existing one.
- Do open one when a section has grown past ~800 lines, or when its contents have
  visibly stopped being about what its title says.
- Chapter 1 is allowed to be undersized early on, because everything starts there.
  Do not "fix" that by inventing chapters 2 and 3.

### Which axis to optimise

When the current material cannot satisfy every norm at once — and early in a course
it cannot — favour the arrangement whose deviations *self-heal*:

- **Sections per chapter self-heals.** One section today becomes four by lecture
  eight, with no edits to anything already written.
- **Section and subsection sizes do not.** Get them wrong and you are splitting or
  merging files later, renumbering results and chasing stale `\Cref`s.

So a chapter that is temporarily one well-proportioned section beats a chapter of
three undersized sections that will need merging. Record the deviation in
`TOPICS.md` rather than structuring around it.

## Naming

**Chapter directories** are `Chapters/<N>_<Abbrev>/`, with `<Abbrev>` a short
CamelCase or Snake_Case abbreviation of the topic: `2_Nets`, `3_Set_Theory`,
`4_Func_Anal`, `5_Algebraic_Topology`, `2_Char`, `3_Root`.

**Chapter 1's directory is `1_Intro`, by convention, whatever the chapter is called.**
Three of the four sibling repositories do this — including ones whose chapter 1 is
titled *A Recap of Undergraduate Topology* and *Character Theory* — so `1_Intro` is
not template residue and is not a misnomer. Leave it.

**Chapter files** are `<N>_<Abbrev>.tex` inside their own directory, matching the
directory name: `Chapters/2_Nets/2_Nets.tex`. They hold `\chapter{...}`,
`\thispagestyle{empty}`, the chapter's intro prose, any chapter-wide
`boxnotation`/`boxconvention`, and then one `\input` per section in reading order.

**Section files** are `<N>_<M>_<Abbrev>.tex`, abbreviated the same way:
`1_1_Metric_Spaces.tex`, `2_1_Combinatorics.tex`, `1_3_Algebras.tex`. Subsections do
not get their own files — they live inside their section's file.

**Titles** are noun phrases in title case: *Nets and Filters*, *Solvability and
Nilpotency*, *Convergence of Nets*, *Some "Completely Trivial Combinatorics"*. The
author's idiom for a first chapter that really is introductory is *An Introduction to
the Theory of X*, but a chapter 1 with a plain topic title is equally in keeping.

**Labels** follow `STYLE.md`: `Ch<N>:CH` for chapters, `Ch<N>:Sec:<Name>` and
`Ch<N>:Subsec:<Name>` where a section or subsection is actually referenced. Adding a
label to every heading is not house style.

## `TOPICS.md`

The running map of topic to location, at the repository root.

**`/organise` owns this file.** It decides the outline, the annotations and the
inference note. **`/integrate` appends to it**: a line for each section it added
material to, dated with the lecture. If `/integrate` finds itself wanting to rewrite
the outline rather than add to it, that is the signal to stop and hand over to
`/organise`.

Sections:

- A leading HTML comment saying what the structure currently looks like it is
  becoming, explicitly flagged as inference, and free for the next run to disagree
  with.
- The outline: chapters mapped to directories, sections and subsections beneath them,
  each annotated with the lecture date that supplied it.
- `## Signposted` — topics a lecture pointed at without reaching, annotated with the
  lecture that signposted them. Not sections, and not to be promoted to sections
  until a lecture supplies content.
- `## Unplaced` — material that could not be confidently placed.
- Any deviation from the norms above that is being tolerated deliberately, with the
  condition that would end it ("one section for now; revisit at ~3 sections").

Every line must be traceable to a lecture. A section appears here because a lecture
put material in it, not because the topic is one the course will presumably reach.

## Restructuring costs, and who pays them

Results are numbered **per section** (`\newtheorem{theorem}{Theorem}[section]`), so
moving material across a section boundary renumbers it, and moving a section between
chapters renumbers everything in both. After any restructuring:

- grep for `\Cref`s to anything that moved, and for labels whose `Ch<N>:` prefix no
  longer matches their chapter;
- rebuild and read the log for undefined references and duplicate labels;
- check the ToC against the outline in `TOPICS.md`.

Because these costs are real, **`/integrate` does not restructure**. It may create a
section or subsection for material that has nowhere to go, and it may adjust a title
that its new material has made inaccurate — nothing else. Everything beyond that is
`/organise`'s, and `/organise` proposes before it moves.
