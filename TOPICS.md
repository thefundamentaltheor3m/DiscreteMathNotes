# Topics

Where each topic lives. Owned by `/organize`; `/integrate` appends to it.
What earns a chapter, a section and a subsection: `.claude/ORGANIZATION.md`.

<!-- INFERENCE, not a plan. There is no syllabus for this course and none is coming,
     so every line below traces to a lecture. On one lecture's evidence the shape
     reads as: graphs first, with colorability as the running thread, and the
     generalization from graphs to hypergraphs arriving immediately. If later
     lectures keep pushing on extremal counting, the hypergraph material is the
     obvious seed for a chapter of its own. The next run should feel free to
     disagree with all of this. -->

## 1. Graphs and Colorings  ->  `Chapters/1_Intro/`

```
1.1 Colorings                                       [2026-08-24]
    Asks when a thing can be colored with few colors, of graphs and then of
    the more general hypergraphs.
      k-colorings of a graph                                        (preamble)
    1.1.1 2-Colorings of Graphs                     [2026-08-24]
      odd closed walks give odd cycles
      2-colorable <=> no odd cycle
    1.1.2 Colorings of Hypergraphs                  [2026-08-24]
      hypergraphs, k-uniformity, proper colorings
      m(k), and the reduction to 6 vertices for m(3)
```

`Chapters/1_Intro/` is the author's directory name for chapter 1 across three of
the four sibling repositories, whatever that chapter is titled. It is a convention,
not template residue, and is not a misnomer for a chapter called *Graphs and
Colorings*. Leave it.

## Deliberate deviations

Places where the structure does not yet look like `ORGANIZATION.md` describes,
tolerated on purpose, with the condition that ends each one.

```
Chapter 1 has one section, where the corpus runs 2-8.
    Why tolerated: lecture 1 is a single line of enquiry -- when can a thing be
    colored with few colors, asked of graphs and then of hypergraphs -- and
    splitting one line of enquiry into two sections to hit a count would assert a
    separation the lecture does not have. A chapter short of sections self-heals
    the moment lecture 2 lands; a misjudged idea boundary does not.
    Ends when: a lecture opens a genuinely different question. That is section 1.2.

The chapter title "Graphs and Colorings" is a bet placed on one lecture.
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

## Template scaffolding

Cleared, on the author's go-ahead, 2026-08-24. None of it had acquired real content,
and none of it survives in any of the four sibling repositories.

```
Chapters/0_Overview.tex                 removed -- one template sentence, rendered as
                                        the first prose in the document
Chapters/2_Another Chapter/             removed -- placeholder chapter, two placeholder
                                        sections, pages 7-9 of 11
Chapters/1_Intro/1_2_Another_Section.tex  removed earlier -- held only \lipsum and
                                        occupied the 1.2 slot
```

What remains, deliberately:

```
Chapters/Appendices/                    kept, \input still commented out in main.tex.
                                        3 of the 4 sibling repos keep an Appendices
                                        directory, 2 of those with the \input
                                        commented out. This matches; leave it.
```
