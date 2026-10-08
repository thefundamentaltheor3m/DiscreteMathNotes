# House style

The voice and LaTeX conventions of these notes, distilled from the notes themselves
and from the author's other lecture-note repositories, which share this template and
this style:

- [TopologyNotes](https://github.com/thefundamentaltheor3m/TopologyNotes)
- [LogicNotes](https://github.com/thefundamentaltheor3m/LogicNotes)
- [RepTheoryEPFL](https://github.com/thefundamentaltheor3m/RepTheoryEPFL)
- [LieAlgebrasNotes](https://github.com/thefundamentaltheor3m/LieAlgebrasNotes)

Those repositories are the corpus. When this file is silent on something, or when
you want a second opinion on how a passage should read, go and look at how they do
it — they carry roughly 12,000 lines of settled prose in exactly this style. If a
clone is available locally, grep it; otherwise fetch the relevant file from GitHub.
Reading two or three real sections before writing is cheaper than getting the voice
wrong.

The single test for anything you write: **could the author have written it?** Not
"is it correct", not "is it thorough" — those are necessary. Seamless is the bar.

Within these notes, the lectures of 28 and 30 September 2026 — now 6.1.4 *A Better
Upper Bound*, 6.1.5 *Cups and Caps* and 6.2.1–6.2.2 on van der Waerden's theorem —
are the exemplar: almost entirely the author's own prose, written up with care, and
the author's own statement of what the voice sounds like. Read them before writing
anything longer than a sentence, and compare what you wrote against them afterwards.

This file is about how a passage *reads*. Its companion, `.claude/ORGANISATION.md`,
is about where a passage *lives* — what earns a chapter, a section and a subsection,
measured over the same corpus, plus the file-naming conventions and the format of
`TOPICS.md`. Heading titles and file names are covered there, not here.

## Voice

**First-person plural, and it does the work.** "We begin by defining the so-called
**derived series**…", "We now begin discussing some nontrivial objects…", "Next, we
state what it means for a net to converge." The `we` is the author and reader
walking through the material together, not a passive-voice screen.

**Every boxed environment is introduced by prose, usually one sentence.** This is the
most recognisable feature of the notes: results are almost never stacked back to
back. The bridging sentence says what is coming and, when it can, why:

> We have already encountered a trivial family of solvable Lie algebras.
>
> There is also a less trivial example.
>
> We have a special term for Lie algebras for which the derived series stabilises at $0$.
>
> This gives us a natural relationship between nilpotency and solvability.
>
> The following is thus obvious.

Note how short they are. One clause of signposting, then get out of the way. A
paragraph of motivation before a definition is fine when the definition is genuinely
unmotivated; three paragraphs is not.

**Colloquial, occasionally funny, never chatty.** The register is a good lecturer at
a blackboard: "Here's a cool result.", "Let's start with a motivating question:",
"get ready to do some fishing", "We can say something so many ways…", "We have time
for only one more thing, which won't even be on the basic exam." Reproduce this
where it fits naturally; do not manufacture it. A flat, correct sentence is much
better than a forced joke.

**Concise, but never at the cost of the reader.** Steps that are genuinely mechanical
get compressed ("This is essentially just definitions.", "First, note the following
fact (which we won't bother to prove)."). Steps where the reader could plausibly get
stuck get spelled out. The author writes to be re-read months later, so the *idea* of
an argument is always visible even when the arithmetic is terse. Do not pad; do not
write "Note that", "It is important to observe that", or "In other words" as filler.

**British spelling**, and it matters here: *colouring*, *neighbourhood*,
*generalisation*, *organised*, *stabilises*, *centraliser*, *characterisation*.
The author writes it by habit, so it is what the raw notes arrive in; anything an
assistant writes into the notes, `TOPICS.md` or these instructions should match.
Identifiers are no exception (`\colouredcyclegraph`, `\labelledpoint`, files like
`2_1_Colourings.tex`), but LaTeX's own spellings are fixed and stay as they are:
`\color`, `xcolor`, `tcolorbox`, `\begin{center}`, `\centering`, TikZ's `gray`.

(The notes were American from 2026-08-24 to 2026-10-07; that was reverted, and the
`/americanise` skill that enforced it is gone. Old commit messages and pull requests
from that period still say *coloring* and `/organize`.)

**Abbreviations used inline, unpunctuated:** `ie,` `eg,` `cf.` `TFAE`, `WLOG`.

**Standing hypotheses go in a sentence, not a box:** "Throughout this section, $L$
will denote an arbitrary Lie algebra.", "Fix a topological space $X$."

**Do not coin terminology inside a proof or a running argument.** No "call a pair of
vertices *covered* if some edge contains both", no "say a vertex is *good* when …",
no "let us call such a set *nice*". Terminology in these notes is introduced in a
`boxdefinition` or a `boxnotation`, where a reader can find it again; a term invented
mid-argument cannot be looked up, and the ceremony of defining it costs more than it
saves. Say the thing in ordinary language instead, as many times as you need to —
"an edge covers the $\binom{3}{2} = 3$ pairs among its vertices" needs no coinage,
because *covers* is doing ordinary work rather than standing for a definition.

If a notion genuinely earns a name — it is used across several results, or the
argument is unreadable without it — then it earns a `boxdefinition` before the proof,
not an aside inside it.

## LaTeX mechanics

**One paragraph per source line.** Lines run to 300–600 characters; nothing is hard
wrapped. Never reflow a paragraph you are editing, and never introduce wrapping.

**Blank line between every top-level block** — prose paragraph, environment, display.
Four-space indentation inside environments.

**`align*` is the default display environment**, even for a single line, even for a
one-line `cases`. `equation`/`\[…\]` are essentially unused. Displays inside a
sentence are not followed by a blank line when the sentence continues.

**Boxed environments always**, never the plain `theorem`/`definition`/`example`
forms. The full family is in `TeX_Setup/environments.tex`; `CLAUDE.md` lists them by
colour. Frequency across the corpus, which is a good prior for what to reach for:
`boxdefinition` ≫ `boxlemma` ≈ `boxexample` > `boxtheorem` ≈ `boxproposition` >
`boxconvention` > `boxcorollary` > `boxnotation` > `boxcexample` > `boxexercise` >
`boxwarning` > `boxnexample`.

**Optional titles on definitions, rarely on results.** `\begin{boxdefinition}[Derived
Series]` — title-cased, naming the concept. Theorems and lemmas usually go untitled
unless the result has a name (`[Cartan's First Criterion]`).

**`\hfill` immediately after `\begin{box…}` or `\begin{proof}` when the body opens
with a list**, otherwise the first item collides with the environment header:

```tex
\begin{boxnotation} \hfill
    \begin{itemize}
        \item $[k]$ will denote $\set{1, \ldots, k}$.
    \end{itemize}
\end{boxnotation}
```

**The term being defined is `\textbf{bolded}` inside the definition body**, on first
use: "A hypergraph $H$ is **$k$-uniform** if $\abs{f} = k$ for all $f \in H$."
`\textit{}` is for emphasis in prose.

**Case splits and multi-part proofs use `description`**, with the case name in the
optional argument:

```tex
\begin{proof} \hfill
    \begin{description}
        \item[$\parenth{\implies}$] …
        \item[$\parenth{\impliedby}$] …
    \end{description}
\end{proof}
```

Named cases are underlined and end with a full stop:
`\item[\underline{$b > 0$.}]`, `\item[\underline{Base Case: $n = 1$.}]`,
`\item[\underline{$(1) \implies (2)$.}]`.

**`enumerate` options seen in the corpus:** `[noitemsep]`,
`[label = \normalfont \arabic*.]`, `[label = (\arabic*)]`, `[label = (\roman*)]`,
`[label = (\alph*)]`, combined with `noitemsep`. Plain `itemize` for unordered lists.

**Quotes are LaTeX quotes:** ``` ``like this'' ```, never `"` and never `''` alone.

**Dashes are `---`, set closed up:** `directed sets---that is, posets`. The corpus
uses `---` sixty-odd times and a literal Unicode `—` never; a Unicode em dash in the
source is one of the easiest seams to spot.

**`\Cref`, never `\cref`.** The corpus uses `\Cref` 239 times and `\cref` zero times.
`\Cref{Ch1:Eg:Poset_Downward_Cone}` mid-sentence, capital `C` regardless of position.
`(cf. \Cref{…})` is the idiom for a parenthetical back-reference.

## Labels

`Ch<N>:<Kind>:<Name>`, with `<Name>` in `Title_Snake_Case` or `CamelCase` — both
appear; match whatever the file you are editing already does.

| Kind | Used for |
| --- | --- |
| `CH` | chapter, as `Ch<N>:CH` — the only label with no third component |
| `Def` | definitions |
| `Thm`, `Prop`, `Lemma`, `Cor` | results (`Lemma` in full is the majority spelling; `Lem` also appears) |
| `Eg`, `CEg` | examples, counterexamples |
| `Eq` | tagged displays |
| `Sec`, `Subsec` | sections and subsections |
| `Fig`, `Tab` | figures and tables |
| `Exo` | exercises |

Examples from the corpus: `Ch1:Def:Poset`, `Ch1:Eg:2D_NonAbelian_Lie_Algebra`,
`Ch2:Prop:KillingIdeal`, `Ch1:Cor:EngelNilpotency`, `Ch1:Eq:Avging_Maschke_Pf`.
`SP:` prefixes results imported from outside the course's own development
(`SP:Thm:Maschke`, `SP:Zorn`), and `APP:` appendix material.

**Label only what gets referenced.** Most environments in the corpus carry no label
at all. Adding one to everything is not house style.

## Macros

`TeX_Setup/shortcuts.tex` is the vocabulary and it is long. **Grep it before writing
any raw math** — there is almost certainly already a macro. The conventions it
follows, which any new macro must follow too:

- **Delimiters auto-size.** `\parenth`, `\brac`, `\set`, `\setst{elts}{cond}`,
  `\abs`, `\norm`, `\floor`, `\ceil`, `\cycl`, `\oc`, `\co` — all `\left…\right`.
  Bare `(`…`)` around a nontrivial expression is a style error.
- **`p`-prefix for a parenthesised operator:** `\pgcd`, `\plcm`, `\pdim`, `\pker`,
  `\pim`, `\pdet`, `\pdeg`, `\psin`, `\psup`, `\pchar`. The lecture-1 addition
  `\dist{v_0, u}` follows this shape.
- **`of`-suffix for parenthesised function application:** `\fof`, `\gof`, `\Tof`,
  `\varphiof`, `\muof`, `\Powset`. Plus the bare `\of{…}` for "apply whatever
  precedes".
- **`\!` before the delimiter** in every operator macro, so `\rank{A}` sets as
  $\operatorname{rank}(A)$ with no gap: `\operatorname{rank}\!\parenth{#1}`.
- **`\operatorname{}`**, not `\mathrm{}` or `\text{}`, for operator names.
- Grouped under all-caps banner comments — `% DELIMITERS:`, `% FUNCTIONS:`,
  `% LINEAR ALGEBRA:`, `% TIKZ:`, `% DISCRETE MATH COURSE` — with new
  course-specific macros appended under the last of these.

**`\sorry`** (red `sorry`, borrowed from Lean) marks a gap: a proof not given, a case
not covered, an argument the lecture waved at. Leaving a `\sorry` is honest and
expected; silently writing a hand-wave in its place is not. Closing them is the
`/fill-sorries` skill's job, and one of only two places in the repository where an
assistant is expected to work the mathematics out for itself; the other is
`/check-correctness`, which checks whether what is written is true and leaves
`% [SUSPECT]` where it believes something is wrong and cannot fix it.

## TikZ

Figures are `\begin{figure}[H]` + `\centering` + `tikzpicture`, occasionally
`wrapfigure` when the picture belongs beside the prose. `\caption`/`\label` are
usually commented out rather than filled in — the figure is referenced by position,
not number.

**Reusable pictures become macros in the `% TIKZ:` block of `shortcuts.tex`**, not
inline TikZ repeated at each use site. The existing precedents are `\drawplane`
(gridded, labelled axes), `\drawsquare{halfwidth}` (the labelled square that the
dihedral-group discussion reuses), and `\labelledpoint{x}{y}{dx}{dy}{label}`. This is
the pattern to follow for anything a graph theory course will want repeatedly — cycle
graphs, path graphs, complete graphs, a labelled hypergraph — parameterised by the
one thing that varies. Available libraries are listed in `TeX_Setup/packages.tex`:
`positioning`, `cd`, `shapes.geometric`, `arrows`, `decorations.markings`.

`cd` and `cd*` are the commutative-diagram environments (`tikzcd` wrapped in
`equation`/`equation*`).

## Anti-patterns

Things that read as "an assistant wrote this", all of which appear nowhere in the
corpus:

- A boxed environment with no introductory sentence before it.
- Bulleted lists standing in for prose that should carry an argument.
- "Note that", "It is worth noting that", "Importantly", "In other words" as
  sentence openers.
- Scaffolding that announces the argument instead of making it: "To see this, …",
  "Now count.", "We proceed as follows." The next sentence is the argument; start
  there.
- Coining a term mid-proof rather than defining it in a box (see above).
- A summary paragraph at the end of a section restating what was just proved.
- Bold or italics for emphasis in running prose beyond the defined-term convention.
- Reformatting, rewrapping, or re-indenting lines you did not otherwise need to
  touch — it buries the real change in the diff.
- Explaining a step the author would have taken as read, or hedging a claim the
  author would simply have asserted.

Four further failures, each named by the author on 2026-10-07 after reading an
assistant's work, and each of them worth a pass of its own over anything you wrote:

- **Jargon.** Words that are not standard mathematics and not defined in the notes,
  borrowed from engineering or business and used as if they were terms of art:
  *load-bearing*, *escape clause*, *bites*, *buys us*, *benchmark*, *leans on*,
  *machinery*, *scaffolding*, *bookkeeping*, *the honest route*, *cheap* and
  *expensive* for anything but money, *does real work*, *this is where X happens*.
  The author does not write like this and reads it as corporate filler. Say the
  mathematical thing in ordinary words: a hypothesis is *needed* or *used*, a
  theorem *gives* a bound, an argument *shows* something. If a word has to be in
  quotation marks to sound right, it is the wrong word.
- **Organisation.** A definition the notes will use again goes in a `boxdefinition`,
  not in a running sentence; a result that will be cited goes in a box with a
  label. Material is scoped the way the author scopes it — one idea per subsection,
  the idea named in the heading — and not the way an assistant finds convenient to
  explain. The reader is the author, re-reading before an exam: arrange things the
  way they would look for them.
- **Precision.** A lecture is allowed to be hand-wavy, and the notes record the
  lecture. Supplying the missing hypothesis or the missing step is right; spelling
  out the boundary case nobody will ever hit, splitting a hair the argument does
  not depend on, or qualifying a sentence three times is not. Be exactly as
  precise as the argument needs, and no more. Clarity is the goal; thoroughness is
  a means to it and stops being one the moment it costs clarity.
- **Length.** Two opposite failures, both common. Verbose where nothing is being
  said: a bridge that restates the box below it, a summary of what was just
  proved, a sentence of motivation that could be a clause. Terse where the point
  is: a "clearly" over the step that carries the argument, a bound stated without
  the one line that makes it come out, an assumption used without being named.
  Before leaving a passage, ask of each sentence whether removing it loses
  anything, and of each step whether the author could reconstruct it in six months.
