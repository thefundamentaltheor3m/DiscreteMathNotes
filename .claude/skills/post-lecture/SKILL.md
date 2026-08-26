---
name: post-lecture
description: Everything that needs doing after a lecture, in one pass and one pull request — address the `% [CLAUDE]` directives, integrate the new material into the chapter structure, then convert spellings to American. Use when the user says "/post-lecture", "do the post-lecture pass", "process today's lecture", "I've just finished a lecture", or otherwise asks for the whole after-lecture routine rather than one part of it.
---

# The post-lecture pass

Three things need doing after a lecture, and doing them separately means three
branches, three pull requests and three reviews for one lecture's worth of work. This
skill runs all three on one branch and opens one pull request.

**It is a composition, not a skill with a scope of its own.** It adds no rules about
how to write, where material goes, or which spellings are house style — each component
skill owns that, and duplicating any of it here would just create two copies to drift
apart. Read each component skill when you reach its phase and follow it as written.
The only things this file decides are the order, the branching, and how the phases
report.

## The phases, and why in this order

| | Phase | Skill |
| --- | --- | --- |
| 1 | Address the inline directives | `.claude/skills/address-comments/SKILL.md` |
| 2 | Integrate the new material | `.claude/skills/integrate/SKILL.md` |
| 3 | Convert spellings | `.claude/skills/americanise/SKILL.md` |

The order is not arbitrary and should not be rearranged:

**`/address-comments` goes first, while the material is still raw and still in one
place.** A `% [CLAUDE]` directive is written in situ and means almost nothing outside
its surroundings — "finish proof using previous lemma", "elaborate on this" — and once
`/integrate` has redistributed the material those surroundings are gone. Doing it first
also means phase 2 moves finished passages rather than half-finished ones with markers
still in them.

**`/integrate` goes second**, with complete passages to place. Note that phase 1's
commit lands *inside* the window `/integrate` diffs over, so anything
`/address-comments` wrote is automatically part of the material to be integrated —
that is intended, not a bug to work around.

**`/americanise` goes last, so that it catches everything.** The author writes British
English by habit, so the raw notes need converting; but phases 1 and 2 also write prose,
and running the sweep first would miss every word of it. Last is the only position that
covers both.

## One branch, three commits, one pull request

Each component skill has its own "branch, commit, PR" step. **Those are overridden
here.** Do not create three branches and do not open three pull requests.

```bash
git checkout -b post-lecture/<lecture-date>
```

Commit **once per phase**, with the phase named in the subject. Three commits rather
than one, because the phases are very different kinds of change and the author needs to
tell them apart in review: what was written to satisfy a directive, what merely moved,
and what is a cosmetic spelling sweep. `/americanise` in particular touches a lot of
lines shallowly, and folded into one commit it would swamp the changes that need real
attention.

Open the pull request once, at the end, from the `/integrate` step's template extended
to cover all three phases.

## Phases that have nothing to do

Skip them. If there are no `% [CLAUDE]` directives this lecture, phase 1 makes no
commit; if every spelling is already American, phase 3 makes no commit. Say so in the
report. Never create an empty commit to mark a phase as having run.

If `/integrate` finds nothing new at all, then there was no lecture to process: stop,
say so, and do not open a pull request.

## When a phase cannot finish

Do not abandon the run. Complete the phases that can be completed, and be exact in the
report about what was left and why. A lecture where the comments were addressed and the
material integrated, with three spellings flagged as ambiguous, is a good outcome; a
lecture where nothing happened because one directive was unclear is not.

The component skills each say when to stop and ask rather than guess — an ambiguous
`% [CLAUDE]` directive, two readings of a `\sorry`, a date that disagrees with the
commit. Honour that, but **batch it**: gather the questions and ask them together, at
the end, rather than interrupting three times.

## The approval gate

`/integrate` says to produce a plan and stop for confirmation before writing anything.
That gate exists because placement is editorial judgment and the author is the editor.

When `/post-lecture` is invoked as a single autonomous pass, you cannot stop for it.
`/integrate` already provides for this: say plainly that you are proceeding without
approval, apply the plan, and put the full plan and its rationale in the commit message
and the pull request body instead. The pull request *is* the approval step — which is
why the placement rationale and every overruled heading of the author's have to be
legible there, not merely implied by the diff.

If the author is present and interactive, prefer the gate: show the plan after phase 1
and wait.

## Verify once, at the end

Each phase has its own checks; run them. But the build is what matters and it only
needs to pass once, on the final state:

```bash
latexmk -pdf -outdir=TeX_Outputs main.tex
```

Read the log for undefined references and duplicate labels, refresh the committed
`TeX_Outputs/main.pdf`, and confirm the inbox came out as `/integrate` requires.

## Report back

One report, three sections, in phase order — each as its component skill specifies, so
nothing about what to report is decided here. Then, across the whole run:

- **Which phases ran and which were skipped**, with why.
- **Everything batched for the author**: questions, ambiguities, anything flagged.
- **The overruled structure**, hoisted from the `/integrate` section. It is the single
  most likely thing to want reverting, and burying it in the middle of a three-part
  report defeats the purpose.
- The build result.

## What this skill deliberately does not include

- **`/fill-sorries`.** It is authorized to work mathematics out for itself, which is a
  different kind of risk from the three phases here, and it deserves its own review
  rather than being swept into a routine pass. Run it separately when you want it.
- **`/organize`.** That is the periodic restructuring pass over the notes as a whole,
  not a per-lecture chore. `/integrate` records structural pressure in `TOPICS.md` when
  it sees it; `/organize` gets run when that has accumulated.

Neither omission is an oversight, so do not helpfully add them.
