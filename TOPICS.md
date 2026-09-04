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
      m(3) = 7: balanced colorings for the lower bound, the
        Fano plane for the upper                       [2026-08-26]
    1.1.3 Bounds on m(k)                            [2026-08-26]
      m(k) >= 2^(k-1), by a union bound over random colorings
      m(k) = O(k^2 2^k), set as an exercise
    1.1.4 Maker-Breaker Games                       [2026-08-26]
      Erdos-Selfridge: breaker wins when m + Delta < 2^k
      8x8x8 tic-tac-toe, as an aside the course drops

1.2 Ramsey Numbers                                  [2026-08-26]
    Turns the question around: how large must a structure be before every
    coloring of it is forced to produce something monochromatic.
      R(k), for edge colorings of complete graphs
      R(3) >= 6, from the two-colored K_5
      known values and the best known bounds

1.3 Matchings in Bipartite Graphs                   [2026-08-28]
    Turns from coloring a hypergraph to choosing from one: can a vertex be
    picked out of each edge, all of them different?
    1.3.1 Adjacency Matrices                        [2026-08-28]
      Adj(H), once vertices and edges are put in some order
      the hypergraph / 0,1 matrix / bipartite graph trifecta
      two worked examples, the second read off a matrix rather than drawn
    1.3.2 Hall's Marriage Theorem                   [2026-08-28]
      Hall, both directions, by induction on |A|, for A finite
      families of distinct representatives, as Hall read on a hypergraph
      the biregular corollary: 1 <= d_2 <= d_1 gives a complete matching of A

1.4 Sperner Systems                                 [2026-08-28]
    How large can a family of subsets of [n] be when none contains another?
      the containment diagram on [3], and each layer as a Sperner system
      Sperner's theorem, by the random-permutation (LYM) argument

1.5 Intersecting Families                           [2026-08-31]
    Forbids the opposite of 1.4: how large can a family of k-subsets be when
    no two of them are allowed to miss each other?
      intersecting k-uniform hypergraphs
      the small cases k = 1, 2, 3 and the star, and why k > n/2 beats them
      Erdos-Ko-Rado, with the k | n warmup on a random partition
      k-intervals of a cycle, and at most k of them pairwise intersect
        -- uniquely a star once n >= 2k+1                  [supplied]
      the extremal case: |H| = binom(n-1,k-1) forces a star, by transposing
        adjacent vertices of the cycle one at a time       [supplied]

1.6 Chromatic Number                                [2026-09-02]
    Comes back to coloring graphs, and asks how many colors a graph needs
    and how far that can be from the obvious lower bound.
      chi(G), and the trivial bounds omega(G) <= chi(G) <= Delta + 1
    1.6.1 Trivial Bounds                            [2026-09-02]
      cliques and the clique number
      the star (Delta large, chi = 2) and the odd cycle (omega = 2, chi = 3)
    1.6.2 Perfect Graphs                            [2026-09-02]
      induced subgraphs                                         [supplied]
      perfect graphs, defined and not pursued
      Zykov's construction: triangle-free with chi(G_k) = k, proved
        by induction                                            [supplied]
    1.6.3 Graphs of Large Girth                     [2026-09-02]
      girth; Erdos: girth >= k and chi >= k at once
      independent sets and alpha(G)
      alpha(G) >= n/2d for average degree d >= 1, by the method
        of alterations                                          [supplied]
      G_{n,p} at p = n^{eps - 1}: alpha <= n/2k and fewer than n/2
        short cycles, whp; delete a vertex per short cycle
```

Entries marked `[supplied]` are arguments this repository's skills worked out,
not arguments the lecturer gave; each carries a `% [FILLED]` comment at its site.

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
    ENDED 2026-08-26: lecture 2 opened the Ramsey question, which is a different
    question, so it became section 1.2 exactly as anticipated. Left standing as the
    record of why 1.1 was not split; /organize should retire the entry.

The chapter title "Graphs and Colorings" is a bet placed on one lecture.
    Ends when: chapter 1 holds three or so lines of enquiry. Re-read it then and
    check the title still names what the chapter is about; renaming later
    renumbers every label under it.
    MET 2026-08-28: lecture 3 brought two more lines of enquiry, neither of them
    about coloring. Recorded under Structural pressure; /organize should act.
```

## Signposted

Topics a lecture pointed at without reaching. Not sections, and not to be promoted
to sections until a lecture supplies content.

```
m(3) for 3-uniform hypergraphs   posed 2026-08-24. The argument breaks off at
                                 "6 edges and 6 vertices" at the end of 1.1.2.
                                 REACHED 2026-08-26: m(3) = 7, finished in 1.1.2.
m(2) = 3                         asserted 2026-08-24 without justification.
R(3) = 6                         asserted 2026-08-26 as "rather nontrivial",
                                 not proved. Only R(3) >= 6 is in the notes.
2^(k/2) <= R(k) <= 3.8^k         quoted 2026-08-26 as the best known bounds,
                                 with no indication of where either comes from.
m(k) = O(k^2 2^k)                set as an exercise 2026-08-26. Would close the
                                 gap above 1.1.3's lower bound.
the probabilistic method         flagged 2026-08-26: the union bound in 1.1.3
                                 could have been phrased as a count, but the
                                 lecturer warned that this will not always hold.
matchings between the layers     gestured at 2026-08-28 as the intuitive route
                                 to Sperner's theorem, and said to break down
                                 "before k exceeds n/2". Not carried out; the
                                 proof given is the random-permutation one.
what makes a matching complete   used throughout 1.3 and never defined. The
                                 notes say "complete matching of A" from Hall
                                 onwards without saying what one is.
binom(n,k) for k > n/2           asserted 2026-08-31 as working "because of
                                 something involving pigeons and holes". True
                                 and easy -- two k-sets with 2k > n cannot be
                                 disjoint -- but the notes do not say it.
Hilton-Milner                    not named 2026-08-31, but it is the standard
                                 route to the uniqueness in 1.5 and would give
                                 a second proof of the extremal theorem. The
                                 proof in the notes goes the other way, through
                                 the cycle, and needs nothing external.
perfect graphs                   defined 2026-09-02 and then left: the lecture named
                                 the class in which omega = chi holds hereditarily
                                 and went straight to how badly it can fail.
chi(G) >= |V(G)| / alpha(G)      used 2026-09-02 with "thus" at the end of the Erdos
                                 proof. True because each color class is an
                                 independent set; the notes do not say it.
Markov's inequality              used 2026-09-02 by name, not stated.
girth exactly k, chi exactly k   the lecture stated Erdos's theorem with equalities;
                                 the proof gives girth > k and chi >= k, and the
                                 statement now says "at least". The exact form does
                                 follow for k >= 3 (delete vertices until chi = k,
                                 then add a disjoint C_k); recorded in a CORRECTED
                                 comment in 1.6.3, not in the notes.
G_{n, p}                         used 2026-09-02 without definition; a boxed
                                 definition was supplied in 1.6.3 and marked as not
                                 from the lecture.
```

## Unplaced

Nothing.

## Structural pressure

Observations for `/organize`, recorded rather than acted on.

```
1.1.4 Maker-Breaker Games is a game inside a section about colorings.
    It earns its place for now: Erdos-Selfridge is the same 2^(k-1) threshold as
    1.1.3, so the subsection continues that line of enquiry rather than opening
    a new one, and the lecturer closed it with "we won't say any more about
    tic-tac-toe in this course". If a later lecture returns to positional games,
    this wants lifting out into a section of its own. [noted 2026-08-26]

The m(3) = 7 development is loose prose at the end of 1.1.2, not a subsection.
    It is now the longest thing in that subsection and has a figure and two
    boxed environments of its own. Splitting it out would renumber everything
    after it, so it is left where the lecture put it. [noted 2026-08-26]

Chapter 1 is called "Graphs and Colorings" and half of it is no longer about
    either. 1.3 and 1.4 ask about matchings and about antichains, neither has
    anything to do with coloring, and both are about hypergraphs rather than
    graphs. This is exactly the condition the chapter-title deviation above set
    for re-reading the title. Renaming renumbers every label under the chapter,
    so nothing is done about it here. Run /organize. [noted 2026-08-28]

Whether 1.3 and 1.4 want to be one section, or a chapter of their own, is
    /organize's call. They were split because neither needs the other and
    either order reads -- the proof of Sperner uses no matching theory, and Hall
    never mentions antichains -- which is ORGANIZATION.md's test for two lines
    of enquiry rather than one. But they arrived in a single lecture and share
    their objects, and if lecture 4 continues either of them the right home may
    be a chapter about set systems rather than two sections inside a chapter
    about coloring. [noted 2026-08-28]
    ANSWERED 2026-08-31, in the affirmative: lecture 4 continues 1.4 closely.
    See the entry below.

Lecture 4 continues 1.4, and the chapter is now three sections of extremal set
    theory wearing a coloring chapter's title. 1.5 asks 1.4's question with the
    containment constraint swapped for an intersection constraint, and answers
    it by the same random-permutation device -- the proof of Sperner and the
    k | n warmup for Erdos-Ko-Rado are the same argument twice. So the case for
    1.4 and 1.5 being one line of enquiry, or a chapter of their own together
    with 1.3, is now much stronger than it was on 2026-08-28.
    Not acted on here, and deliberately: merging them means splitting 1.4's
    existing content into subsections and retitling it, and splitting or merging
    an existing heading is /organize's, not /integrate's. A chapter carrying one
    section too many self-heals; a misjudged idea boundary does not. The author
    also wrote \section themselves, which is their own proposal for a section
    rather than a subsection.
    Run /organize. Three things for it to weigh together: the chapter title
    (flagged 2026-08-28 and now worse), whether 1.3/1.4/1.5 become a chapter on
    set systems, and whether 1.4 and 1.5 are one section or two.
    [noted 2026-08-31]

The "moreover" of Erdos-Ko-Rado is stated twice in 1.5, once inside the theorem
    and once as the extremal theorem that actually proves it. The duplication is
    the author's -- both were written in the lecture -- and /integrate may not
    delete a statement, so both stand, with the second cross-referenced as the
    first made precise. Merging them is /organize's call. [noted 2026-08-31]

1.6 Chromatic Number is a coloring section sitting after three sections of extremal
    set theory. It continues 1.1's question -- how many colors does a graph need --
    and its Zykov graphs and Erdos's theorem read most naturally right after 1.1 and
    1.2, before the notes leave coloring for hypergraph set systems. It was appended
    as 1.6 because /integrate may not renumber 1.3-1.5 to make room. This is the
    fourth thing for /organize to weigh with the chapter title (flagged 2026-08-28,
    2026-08-31): a chapter that opens and closes with coloring around a set-systems
    middle wants either reordering or splitting. [noted 2026-09-02]

The author wrote \section{Chromatic Number} and \section{Perfect Graphs}, and asked
    in a comment whether each deserved a section or a subsection. Integrated as one
    section with three subsections, the second of them carrying the author's
    "Perfect Graphs" heading demoted to a subsection and its tail (girth, Erdos)
    split into a third. Reason: ORGANIZATION.md's section test is one line of
    enquiry with a destination, and everything here walks toward Erdos's theorem
    -- perfect graphs are named only as the case the rest of the section shows
    can fail arbitrarily badly. If a later lecture develops perfect graphs on
    their own (the strong perfect graph theorem, say), that subsection is the
    seed of a section and /organize should lift it. [noted 2026-09-02]
```

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
