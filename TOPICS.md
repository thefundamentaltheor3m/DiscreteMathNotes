# Topics

Where each topic lives. Owned by `/organise`; `/integrate` appends to it.
What earns a chapter, a section and a subsection: `.claude/ORGANISATION.md`.

<!-- INFERENCE, not a plan. There is no syllabus for this course and none is coming,
     so every line below traces to a lecture. On one lecture's evidence the shape
     reads as: graphs first, with colourability as the running thread, and the
     generalisation from graphs to hypergraphs arriving immediately. If later
     lectures keep pushing on extremal counting, the hypergraph material is the
     obvious seed for a chapter of its own. The next run should feel free to
     disagree with all of this. -->

## 1. Graphs and Colourings  ->  `Chapters/1_Intro/`

```
1.1 Colourings                                       [2026-08-24]
    Asks when a thing can be coloured with few colours, of graphs and then of
    the more general hypergraphs.
      k-colourings of a graph                                        (preamble)
    1.1.1 2-Colourings of Graphs                     [2026-08-24]
      odd closed walks give odd cycles
      2-colourable <=> no odd cycle
    1.1.2 Colourings of Hypergraphs                  [2026-08-24]
      hypergraphs, k-uniformity, proper colourings
      m(k), and the reduction to 6 vertices for m(3)
```

`Chapters/1_Intro/` is the author's directory name for chapter 1 across three of
the four sibling repositories, whatever that chapter is titled. It is a convention,
not template residue, and is not a misnomer for a chapter called *Graphs and
Colourings*. Leave it.

## Deliberate deviations

Places where the structure does not yet look like `ORGANISATION.md` describes,
tolerated on purpose, with the condition that ends each one.

```
Chapter 1 has one section, where the corpus runs 2-8.
    Why tolerated: lecture 1 is a single line of enquiry -- when can a thing be
    coloured with few colours, asked of graphs and then of hypergraphs -- and
    splitting one line of enquiry into two sections to hit a count would assert a
    separation the lecture does not have. A chapter short of sections self-heals
    the moment lecture 2 lands; a misjudged idea boundary does not.
    Ends when: a lecture opens a genuinely different question. That is section 1.2.

The chapter title "Graphs and Colourings" is a bet placed on one lecture.
    Ends when: chapter 1 holds three or so lines of enquiry. Re-read it then and
    check the title still names what the chapter is about; renaming later
    renumbers every label under it.
```

## Signposted

Topics a lecture pointed at without reaching. Not sections, and not to be promoted
to sections until a lecture supplies content.

```
m(3) for 3-uniform hypergraphs   posed 2026-08-24. The argument breaks off at
                                 "6 edges and 6 vertices" at the end of 1.1.2.
m(2) = 3                         asserted 2026-08-24 without justification.
```

## Unplaced

Nothing.

## Template scaffolding still standing

Not content, but `\input` from `main.tex`, so it compiles into the PDF. Clearing it
is a structural change and therefore `/organise`'s to propose: **recommended, awaiting
the author's go-ahead**, since none of it has acquired real content.

```
Chapters/0_Overview.tex                 placeholder
Chapters/2_Another Chapter/             placeholder chapter, two placeholder sections
Chapters/Appendices/                    placeholder, \input already commented out
```

`Chapters/1_Intro/1_2_Another_Section.tex` was in this list and has been removed: it
held nothing but `\lipsum` and occupied the 1.2 slot.
