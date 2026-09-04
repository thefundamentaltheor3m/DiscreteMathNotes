# Topics

Where each topic lives. Owned by `/organize`; `/integrate` appends to it.
What earns a chapter, a section and a subsection: `.claude/ORGANIZATION.md`.

<!-- INFERENCE, not a plan. There is no syllabus for this course and none is coming,
     so every line below traces to a lecture. On six lectures' evidence the shape reads
     as one method and two bodies of theory it is applied to: the probabilistic method
     (lecture 6, and as a tool throughout), colorings of graphs and hypergraphs
     (lectures 1, 2, 5) and families of sets (lectures 3, 4). The method was promoted
     to chapter 1 on 2026-09-04, because lecture 6 stated Markov and Chebyshev in their
     own right rather than reaching for them in passing, and because every other chapter
     already used them. Chapter 1 is thin and expected to grow: the second-moment
     argument it sets up was cut off mid-lecture. The next run should feel free to
     disagree with all of this. -->

## 1. The Probabilistic Method  ->  `Chapters/1_Intro/`

```
1.1 A Terse Review of Probability                   [2026-09-04]
    Collects the two deviation inequalities the notes run on, and the
    consequence of the second that the lecture actually reached for.
      Markov, proved by comparison against the variable equal to a
        on X >= a and 0 elsewhere                                   [supplied]
      variance; the E(X^2) - E(X)^2 form, and additivity over
        independent summands                                        [supplied]
      Chebyshev, proved from Markov applied to (X - E(X))^2 at a^2  [supplied]
      Var/E^2 -> 0 forces Pr(X != 0) -> 1                           [supplied]
      n fair coins: Pr(|X - n/2| >= eps n) <= 1/(4 eps^2 n)         [supplied]

1.2 Triangles in Random Graphs                      [2026-09-04]
    Asks for which p the random graph contains a triangle, and gets as far as
    reducing that to a computation of the variance.
      G_{n, p}, defined                                             [supplied]
      E(X) = binom(n, 3) p^3 for the triangle count
      p = o(1/n): no triangle, with probability -> 1, by Markov at a = 1
      p = omega(1)/n: E(X) -> infinity, which only suggests a triangle
      the second-moment reduction; Var(X) for the triangle count is a \sorry
```

## 2. Graphs and Colorings  ->  `Chapters/2_Graphs/`

```
2.1 Colorings                                       [2026-08-24]
    Asks when a thing can be colored with few colors, of graphs and then of
    the more general hypergraphs.
      k-colorings of a graph                                        (preamble)
    2.1.1 2-Colorings of Graphs                     [2026-08-24]
      odd closed walks give odd cycles
      2-colorable <=> no odd cycle
    2.1.2 Colorings of Hypergraphs                  [2026-08-24]
      hypergraphs, k-uniformity, proper colorings
      m(k), and the question "what is m(3)?"
    2.1.3 The Value of m(3)                         [2026-08-24, 2026-08-26]
      the reduction to 6 vertices
      m(3) = 7: balanced colorings for the lower bound, the
        Fano plane for the upper                                    [supplied]
    2.1.4 Bounds on m(k)                            [2026-08-26]
      m(k) >= 2^(k-1), by a union bound over random colorings
      m(k) = O(k^2 2^k), set as an exercise
    2.1.5 Maker-Breaker Games                       [2026-08-26]
      Erdos-Selfridge: breaker wins when m + Delta < 2^k
      8x8x8 tic-tac-toe, as an aside the course drops

2.2 Ramsey Numbers                                  [2026-08-26]
    Turns the question around: how large must a structure be before every
    coloring of it is forced to produce something monochromatic.
      R(k), for edge colorings of complete graphs
      R(3) >= 6, from the two-colored K_5
      known values and the best known bounds

2.3 Chromatic Number                                [2026-09-02]
    Comes back to coloring graphs, and asks how many colors a graph needs
    and how far that can be from the obvious lower bound.
      chi(G)                                                        (preamble)
    2.3.1 Trivial Bounds                            [2026-09-02]
      cliques and the clique number; omega(G) <= chi(G) <= Delta + 1
      the star (Delta large, chi = 2) and the odd cycle (omega = 2, chi = 3)
    2.3.2 Perfect Graphs                            [2026-09-02]
      induced subgraphs                                             [supplied]
      perfect graphs, defined and not pursued
    2.3.3 Zykov's Construction                      [2026-09-02]
      G_1, G_2, G_3 drawn; triangle-free with chi(G_k) = k, proved
        by induction                                                [supplied]
    2.3.4 Graphs of Large Girth                     [2026-09-02]
      girth; Erdos: girth >= k and chi >= k at once
      independent sets and alpha(G)
      alpha(G) >= n/2d for average degree d >= 1, by the method
        of alterations                                              [supplied]
      G_{n,p} at p = n^{eps - 1}: alpha <= n/2k and fewer than n/2
        short cycles, whp; delete a vertex per short cycle
```

## 3. Set Systems  ->  `Chapters/3_Set_Systems/`

```
3.1 Matchings in Bipartite Graphs                   [2026-08-28]
    Turns from coloring a hypergraph to choosing from one: can a vertex be
    picked out of each edge, all of them different?
    3.1.1 Adjacency Matrices                        [2026-08-28]
      Adj(H), once vertices and edges are put in some order
      the hypergraph / 0,1 matrix / bipartite graph trifecta
      two worked examples, the second read off a matrix rather than drawn
    3.1.2 Hall's Marriage Theorem                   [2026-08-28]
      Hall, both directions, by induction on |A|, for A finite
      families of distinct representatives, as Hall read on a hypergraph
      the biregular corollary: 1 <= d_2 <= d_1 gives a complete matching of A

3.2 Sperner Systems                                 [2026-08-28]
    How large can a family of subsets of [n] be when none contains another?
      the containment diagram on [3], and each layer as a Sperner system
      Sperner's theorem, by the random-permutation (LYM) argument

3.3 Intersecting Families                           [2026-08-31]
    Forbids the opposite of 3.2: how large can a family of k-subsets be when
    no two of them are allowed to miss each other?
      intersecting k-uniform hypergraphs                            (preamble)
      the small cases k = 1, 2, 3 and the star, and why k > n/2 beats them
    3.3.1 The Erdos-Ko-Rado Theorem                 [2026-08-31]
      the statement, with the k | n warmup on a random partition
      k-intervals of a cycle, and at most k of them pairwise intersect
        -- uniquely a star once n >= 2k+1                           [supplied]
      the bound, by counting hyper-edges among the intervals of a
        random cycle                                                [supplied]
    3.3.2 The Extremal Case                         [2026-08-31]
      |H| = binom(n-1,k-1) forces a star, by transposing adjacent
        vertices of the cycle one at a time                         [supplied]
      the picture: a swap disturbs two intervals, at most one of
        them through x                                              [supplied]
```

Entries marked `[supplied]` are arguments this repository's skills worked out,
not arguments the lecturer gave; each carries a `% [FILLED]`, `% [CLAUDE]`-derived
or `% Not from the lecture` comment at its site.

`Chapters/1_Intro/` is the author's directory name for chapter 1 across three of
the four sibling repositories, whatever that chapter is titled. It is a convention,
not template residue, and since 2026-09-04 chapter 1 is *The Probabilistic Method*
rather than anything introductory. Leave it. The graph theory that used to be
chapter 1 now lives in `Chapters/2_Graphs/`.

The inbox `Chapters/1_Intro/todays_lecture.tex` keeps that path, which `CLAUDE.md`
and the skills name, and is `\input` at the end of whichever chapter the directory
belongs to -- as of 2026-09-04, chapter 1. That happens to be the chapter the
course is currently in. Material typed there is found by `/integrate` from the git
history, not from its position in the document, so it may end up in any chapter.

## Deliberate deviations

Places where the structure does not yet look like `ORGANIZATION.md` describes,
tolerated on purpose, with the condition that ends each one.

```
2.2 Ramsey Numbers is a section with one definition, one figure and no result.
    Why tolerated: it is one line of enquiry -- how large before every coloring
    is forced to produce something monochromatic -- opened in one lecture and
    not returned to since. Folding it into 2.1 would fuse two questions, which
    is the mistake that does not self-heal; a thin section does.
    Ends when: a lecture returns to Ramsey theory, or the course visibly never
    will, in which case it can become a subsection of 2.1.

Chapter 1 has two sections and neither has subsections, on one partial lecture's
    evidence, where the corpus runs 2-8 sections.
    Why tolerated: the lecture it came from was cut off mid-argument ("LAPTOP
    ABOUT TO DIE"), and the argument it was cutting off -- the variance of the
    triangle count -- is still open as a \sorry in 1.2. A chapter with too few
    sections self-heals as lectures arrive; carving these two into more would
    split one line of enquiry.
    Ends when: the second-moment argument is finished and the chapter reaches
    three or so sections.

Chapter 3 is titled "Set Systems" on two lectures' evidence.
    The three sections ask three different questions of a family of subsets,
    which is what a chapter title has to cover; "Extremal Set Theory" was
    rejected because Hall's theorem is not extremal. Renaming a chapter
    renumbers nothing (labels carry the chapter number, not its name), so this
    is a cheap bet.
    Ends when: chapter 3 holds three or so more sections and the title still
    names what they are about, or does not.
```

Retired, kept as the record of why earlier structure looked as it did:

```
Chapter 1 had one section, where the corpus runs 2-8 (tolerated 2026-08-24).
    ENDED 2026-08-26: lecture 2 opened the Ramsey question, which became 1.2,
    now 2.2.

The chapter title "Graphs and Colorings" was a bet on one lecture (2026-08-24).
    MET 2026-08-28 and worse by 2026-08-31, when half the chapter was set
    systems. RESOLVED 2026-09-02 by /organize: the set-systems sections became
    a chapter of their own, and the coloring chapter is again about what its
    title says.
```

## Signposted

Topics a lecture pointed at without reaching. Not sections, and not to be promoted
to sections until a lecture supplies content.

```
m(3) for 3-uniform hypergraphs   posed 2026-08-24. The argument broke off at
                                 "6 edges and 6 vertices" at the end of 2.1.2.
                                 REACHED 2026-08-26: m(3) = 7, now 2.1.3.
m(2) = 3                         asserted 2026-08-24 without justification.
R(3) = 6                         asserted 2026-08-26 as "rather nontrivial",
                                 not proved. Only R(3) >= 6 is in the notes.
2^(k/2) <= R(k) <= 3.8^k         quoted 2026-08-26 as the best known bounds,
                                 with no indication of where either comes from.
m(k) = O(k^2 2^k)                set as an exercise 2026-08-26. Would close the
                                 gap above 2.1.4's lower bound.
the probabilistic method         flagged 2026-08-26: the union bound in 2.1.4
                                 could have been phrased as a count, but the
                                 lecturer warned that this will not always hold.
                                 REACHED 2026-09-04: treated as a subject, and
                                 now chapter 1.
matchings between the layers     gestured at 2026-08-28 as the intuitive route
                                 to Sperner's theorem, and said to break down
                                 "before k exceeds n/2". Not carried out; the
                                 proof given is the random-permutation one.
what makes a matching complete   used throughout 3.1 and never defined. The
                                 notes say "complete matching of A" from Hall
                                 onwards without saying what one is.
binom(n,k) for k > n/2           asserted 2026-08-31 as working "because of
                                 something involving pigeons and holes". True
                                 and easy -- two k-sets with 2k > n cannot be
                                 disjoint -- but the notes do not say it.
Hilton-Milner                    not named 2026-08-31, but it is the standard
                                 route to the uniqueness in 3.3 and would give
                                 a second proof of the extremal theorem. The
                                 proof in the notes goes the other way, through
                                 the cycle, and needs nothing external.
perfect graphs                   defined 2026-09-02 and then left: the lecture named
                                 the class in which omega = chi holds hereditarily
                                 and went straight to how badly it can fail. If a
                                 lecture develops them, 2.3.2 is the seed of a
                                 section.
chi(G) >= |V(G)| / alpha(G)      used 2026-09-02 with "thus" at the end of the Erdos
                                 proof. True because each color class is an
                                 independent set; the notes do not say it.
Markov's inequality              used 2026-09-02 by name, not stated.
                                 REACHED 2026-09-04: stated and proved as the
                                 first result of 1.1.
girth exactly k, chi exactly k   the lecture stated Erdos's theorem with equalities;
                                 the proof gives girth > k and chi >= k, and the
                                 statement now says "at least". The exact form does
                                 follow for k >= 3 (delete vertices until chi = k,
                                 then add a disjoint C_k); recorded in a CORRECTED
                                 comment in 2.3.4, not in the notes.
Var(X) for the triangle count    the lecture of 2026-09-04 set the second-moment
                                 argument up and stopped before computing the
                                 variance. Carries a \sorry at the end of 1.2.
the second moment method         named as the thing "more sophisticated than the
                                 expectation" 2026-09-04, and used once. If a
                                 lecture develops it as a method, 1.1's corollary
                                 is the seed.
the densest subgraph threshold   not said in the lecture. Recorded in a CORRECTED
                                 comment in 1.2, because it is why a diverging
                                 expectation does not settle the question: a
                                 subgraph count's threshold is set by the densest
                                 subgraph, not by where the expectation passes 1.
the girth half of Erdos's proof  noticed 2026-09-04 during review. The proof of
                                 the theorem in 2.3.4 spells out only the
                                 chromatic-number half; the girth conclusion
                                 follows from deleting a vertex per short cycle
                                 but is never stated. Incomplete, not incorrect.
```

## Unplaced

Nothing.

## Structural pressure

Observations for `/organize`, recorded rather than acted on.

```
2.1.5 Maker-Breaker Games is a game inside a section about colorings.
    It earns its place for now: Erdos-Selfridge is the same 2^(k-1) threshold as
    2.1.4, so the subsection continues that line of enquiry rather than opening
    a new one, and the lecturer closed it with "we won't say any more about
    tic-tac-toe in this course". If a later lecture returns to positional games,
    this wants lifting out into a section of its own. [noted 2026-08-26,
    re-examined and left 2026-09-02, 2026-09-04]

The "moreover" of Erdos-Ko-Rado is stated twice in 3.3, once inside the theorem
    and once as the extremal theorem that actually proves it. The duplication is
    the author's -- both were written in the lecture -- and neither /integrate
    nor /organize may delete a statement, so both stand, with the second
    cross-referenced as the first made precise. Merging them is the author's
    call. [noted 2026-08-31, left 2026-09-02, 2026-09-04]
```

Resolved by the `/organize` pass of 2026-09-04, kept as a record:

```
The tools were stated after their first uses [noted 2026-09-04 by /integrate].
    Markov and Chebyshev arrived as chapter 3, but Markov is used by name in
    what was 1.3.4 and a union bound over random colorings runs in what was
    1.1.4, both earlier in the document. RESOLVED: the probabilistic chapter is
    now chapter 1, on the author's decision, and the graph and set-system
    chapters became 2 and 3. Every Ch<N>: label prefix moved with them and every
    \Cref was rewritten; results renumber per section, so nothing inside a
    section changed number.

G_{n, p} was defined in what was 1.3.4 and used from the probabilistic chapter
    [noted 2026-09-04 by /integrate]. RESOLVED by the same reordering: the
    definition now opens 1.2, where the random-graph material is, and 2.3.4's
    Erdos proof cites it backwards. Nothing renumbered -- it was the last
    numbered environment in its old section.
```

Resolved by the `/organize` pass of 2026-09-02, kept as a record:

```
The m(3) = 7 development was loose prose at the end of what is now 2.1.2
    [noted 2026-08-26]. Now subsection 2.1.3, The Value of m(3). Results number
    per section, so nothing was renumbered.

The coloring chapter was called "Graphs and Colorings" and half of it was set
    systems [noted 2026-08-28, 2026-08-31, 2026-09-02]. Those sections are now
    chapter 3, Set Systems; Chromatic Number moved next to the coloring it
    continues. Everything in the moved sections was renumbered, and five labels
    changed their chapter prefix.

Whether Hall, Sperner and Erdos-Ko-Rado were one section, a chapter, or one
    section plus two [noted 2026-08-28, 2026-08-31]. A chapter of three
    sections: they ask three different questions of a family of sets, and 3.2
    and 3.3 share a method but not a question.

Intersecting Families had no subsections and two theorems with proofs. Now
    3.3.1 The Erdos-Ko-Rado Theorem and 3.3.2 The Extremal Case. The weakest of
    the 2026-09-02 changes: a subsection-free section is legitimate in the
    corpus, and this one was split so that the second theorem is visible from
    the table of contents.

The author's \section{Perfect Graphs} was demoted by /integrate and its tail
    split off [noted 2026-09-02]. /organize went one step further and split
    Zykov's construction out of it as 2.3.3, so that "Perfect Graphs" now
    heads only the two definitions and the ToC shows the construction.
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
