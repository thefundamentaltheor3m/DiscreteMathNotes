# Topics

Where each topic lives. Owned by `/organise`; `/integrate` appends to it.
What earns a chapter, a section and a subsection: `.claude/ORGANISATION.md`.

<!-- INFERENCE, not a plan. There is no syllabus for this course and none is coming,
     so every line below traces to a lecture. On sixteen lectures the shape reads as a
     toolkit and four bodies of theory that use it: probability first, because every
     argument in the notes produces an object by showing a random one works; then
     colouring graphs and hypergraphs; then set systems; then concentration as a
     subject in its own right; then the local lemma; and last Ramsey theory, which
     began life as a section of the graphs chapter on 2026-08-26 and became a
     chapter on 2026-10-07, once van der Waerden and Hales--Jewett had arrived and
     the Ramsey numbers were the odd section out in a chapter about colouring
     graphs. It sits last because its newest material leans on the local lemma.
     Chapter 1 is still the one to watch: three thin sections, and the author
     asked for it on the assumption that more probability will arrive. Chapter 5
     is two short sections, with the local lemma's proof supplied on 2026-10-07
     and an application of it sitting in 6.2.3. The next run should feel
     free to disagree with all of this. -->

## 1. Probability  ->  `Chapters/1_Intro/`

```
1.1 Probability Spaces                              [2026-09-04, 2026-09-11]
    Sets down the objects: what a probability space is and what it means for
    random variables on it to be independent.
      probability spaces, events, random variables
      independence, of events and of finite and infinite families, boxed
      independence of an event from a family of events, which the
        dependency graphs of 5.1 need                                [supplied]
      the convention that Omega is finite and F is its power set

1.2 Expectation                                     [2026-09-04, 2026-09-14]
    What the average of a random variable is, how it meets independence, and
    what it becomes once something has been observed.
      expectation, as an integral against the measure               (preamble)
      the two facts about independent variables: images stay
        independent, and expectation is multiplicative              (preamble)
    1.2.1 Conditional Expectation                   [2026-09-14]
      E(X | A), for an event A of nonzero probability, and the same
        written as a sum over the image of X
      E(X | Y) as a random variable on Omega
      the tower property, stated and not proved
      E(X | Y_1, ..., Y_k), for several variables at once           [supplied]

1.3 Deviation from the Mean                         [2026-09-02, 2026-09-04]
    Bounds how far a random variable strays from its expectation, which is what
    every later chapter actually wants from it.
      Markov's inequality, stated and proved                        [supplied]
      variance, and its additivity on independent variables         [supplied]
      Chebyshev's inequality, proved from Markov                    [supplied]
      Var/E^2 -> 0 gives Pr(X != 0) -> 1, as a corollary            [supplied]
      n fair coins, bounded by Chebyshev                            [supplied]
```

## 2. Graphs and Colourings  ->  `Chapters/2_Graphs/`

```
2.1 Colourings                                      [2026-08-24]
    Asks when a thing can be coloured with few colours, of graphs and then of
    the more general hypergraphs.
      k-colourings of a graph                                       (preamble)
    2.1.1 2-Colourings of Graphs                    [2026-08-24]
      odd closed walks give odd cycles
      2-colourable <=> no odd cycle
    2.1.2 Colourings of Hypergraphs                 [2026-08-24]
      hypergraphs, k-uniformity, proper colourings
      m(k), and the question "what is m(3)?"
    2.1.3 The Value of m(3)                         [2026-08-24, 2026-08-26]
      the reduction to 6 vertices
      m(3) = 7: balanced colourings for the lower bound, the
        Fano plane for the upper                                    [supplied]
    2.1.4 Bounds on m(k)                            [2026-08-26]
      m(k) >= 2^(k-1), by a union bound over random colourings
      m(k) = O(k^2 2^k), set as an exercise
    2.1.5 Maker-Breaker Games                       [2026-08-26]
      breaker wins when m + Delta < 2^k, by a potential argument     (lemma)
      Erdos-Selfridge: breaker wins when m < 2^(k-1), as a corollary
      8x8x8 tic-tac-toe, as an aside the course drops

2.2 Chromatic Number                                [2026-09-02]
    Comes back to colouring graphs, and asks how many colours a graph needs
    and how far that can be from the obvious lower bound.
      chi(G)                                                        (preamble)
    2.2.1 Trivial Bounds                            [2026-09-02]
      cliques and the clique number; omega(G) <= chi(G) <= Delta + 1
      the star (Delta large, chi = 2) and the odd cycle (omega = 2, chi = 3)
    2.2.2 Perfect Graphs                            [2026-09-02]
      induced subgraphs                                             [supplied]
      perfect graphs, defined and not pursued
    2.2.3 Zykov's Construction                      [2026-09-02]
      G_1, G_2, G_3 drawn; triangle-free with chi(G_k) = k, proved
        by induction                                                [supplied]
    2.2.4 Graphs of Large Girth                     [2026-09-02]
      girth; Erdos: girth >= k and chi >= k at once
      independent sets and alpha(G)
      alpha(G) >= n/2d for average degree d >= 1, by the method
        of alterations                                              [supplied]
      G_{n,p}, defined                                              [supplied]
      G_{n,p} at p = n^{eps - 1}: alpha <= n/2k and fewer than n/2
        short cycles, whp; delete a vertex per short cycle

2.3 The Chromatic Number of the Plane               [2026-09-21]
    Colours the plane itself, two points adjacent when they are a unit apart:
    traps its chromatic number between 4 and 7, and then shows that only its
    finite subgraphs matter.
    2.3.1 The Unit Distance Graph                   [2026-09-21]
      the unit distance graph on R^2
      chi >= 3 from the unit triangle, chi >= 4 from Moser's spindle
      chi <= 7 from a 7-coloured hexagonal tessellation, with hexagons
        of diameter 2/(sqrt(21) - 2) < d < 1 and why that works     [supplied]
      the spindle and the tessellation, drawn                       [supplied]
    2.3.2 Compactness                               [2026-09-21]
      compactness as the finite intersection property for closed sets
      chi(G) = sup of chi(H) over finite subgraphs H, via Tychonoff
      every finite subgraph k-colourable => G k-colourable: P_e clopen
        as a preimage, finite subgraphs give the finite intersections,
        Tychonoff the rest; and the theorem deduced from it          [supplied]
```

## 3. Set Systems  ->  `Chapters/3_Set_Systems/`

```
3.1 Matchings in Bipartite Graphs                   [2026-08-28]
    Turns from colouring a hypergraph to choosing from one: can a vertex be
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

## 4. Moments and Concentration  ->  `Chapters/4_Moments/`

```
4.1 Second Moment Methods                           [2026-09-04, 2026-09-09]
    Asks when a random graph contains a fixed graph at all, which is the
    question the first moment cannot answer.
      triangles in G_{n,p}: E(X) -> 0 and E(X) -> infinity, and why
        neither settles anything                                    (preamble)
      np -> infinity gives a triangle whp, by the second moment     [supplied]
      the threshold for an arbitrary H as a subgraph                [handwritten]
      eps(H) = max over subgraphs J of e(J)/v(J)                    [handwritten]
      p = o(n^{-1/eps(H)}) gives no H, by Markov on the densest
        part of H                                                   [supplied]
      K_4 minus an edge: eps = 5/4, and E(X) -> 1/4 at the
        threshold, where the first moment stops deciding            [supplied]

4.2 Chernoff's Bound                                [2026-09-11]
    Goes past the second moment: how to bound a deviation when every power
    of X - E(X) is too weak.
      degrees in G_{n,1/2}, and why Chebyshev's 2500/n is useless
      higher moments, and the exponential that beats all of them
      Chernoff: Pr(eta >= a) <= e^{-a^2/2n} for a +/-1 walk
      the same bound for |xi_i| <= 1 and E(xi_i) = 0, via the chord
        of e^{tx} across [-1, 1]
      the picture of e^{tx} under its chord                         [supplied]

4.3 Martingales                               [2026-09-14, 2026-09-16]
    Takes concentration off sums altogether: a quantity revealed a little at a
    time, each revelation moving the expectation only slightly, concentrates as
    sharply as a random walk does.
      martingales, defined                                          (preamble)
      the second of the three conditions, illegible in the raw
        notes                                                       [supplied]
    4.3.1 Exposing a Random Graph                   [2026-09-14]
      chi(G_{3,1/2}), and its expectation of 2
      the exposure tree, drawn as graphs with the conditional
        expectation under each                                      [supplied]
      the edge-exposure martingale                                  [supplied]
      the vertex-exposure martingale for G_{n,1/2}, and why its
        increments are bounded by 1                                 [supplied]
    4.3.2 Azuma's Inequality                        [2026-09-14]
      Azuma: Pr(X_m - X_0 >= lambda sqrt m) <= e^{-lambda^2/2},
        stated and not proved                                       [supplied]
      chi(G_{n,1/2}) within lambda sqrt n of its mean               [supplied]
    4.3.3 The Doob Martingale                       [2026-09-16]
      X_0 = E(X) and X_i = E(X | Y_1, ..., Y_i), of which 4.3.1's
        two exposure martingales are instances
      that it always averages, and is a martingale in the sense of
        4.3 only once its increments are bounded
    4.3.4 McDiarmid's Inequality                    [2026-09-16]
      k-coordinatewise-Lipschitz, for a map out of a product
      McDiarmid: Pr(X >= E(X) + a) <= e^{-a^2/2n}, for a
        1-coordinatewise-Lipschitz f of independent coordinates
      its proof, begun and broken off at g_i                        [sorry]
      the Smiley Face Lemma of Frieze and Pegden, stated and not
        proved, as what McDiarmid is for; its (eps, D)-copies boxed and
        D made a distance, after the paper                            [CORRECTED]
```

## 5. The Local Lemma  ->  `Chapters/5_Local_Lemma/`

```
5.1 The Lovasz Local Lemma                          [2026-09-16]
    Asks when a random object can avoid every one of a family of bad events,
    each allowed to depend on a few of the others, where the union bound of
    2.1.4 needs them rare enough to avoid all at once.
      independent bad events of probability < 1 are all avoided   (preamble)
      the motivating question: k-uniform hypergraphs whose edges each
        meet at most D others, and when they are 2-colourable
      dependency graphs, with the family independence of 1.1
      A ~ B for adjacency in a fixed dependency graph
      the local lemma, for a finite family and weights 0 < x_A < 1,
        now titled the asymmetric form; its proof, by induction on
        the set of events conditioned on                             [supplied]
      the symmetric form, e p (d + 1) <= 1, as a corollary, on the
        author's instruction of 2026-10-08                           [supplied]

5.2 Nonrepetitive Sequences                         [2026-09-21]
    An infinite binary sequence whose identical blocks are exponentially far
    apart: the first application of the local lemma in view.
      Beck's theorem, stated and not proved, not named in the lecture
```

## 6. Ramsey Theory  ->  `Chapters/6_Ramsey/`

```
6.1 Ramsey Numbers                                  [2026-08-26, 2026-09-25, 2026-09-28]
    Turns the colouring question around: how large must a structure be before
    every colouring of it is forced to produce something monochromatic. Was 2.2
    of the graphs chapter until 2026-10-07.
    6.1.1 Ramsey Numbers of Graphs                  [2026-08-26]
      R(k), for edge colourings of complete graphs
      R(3) >= 6, from the two-coloured K_5
      known values and the best known bounds
      R(k, l) <= R(k-1, l) + R(k, l-1), stated; proof deferred to
        undergraduate graph theory notes, cross-ref pending
    6.1.2 Hypergraph Ramsey Numbers                 [2026-09-25]
      Erdos-Szekeres, stated as the motivation and not proved
      K_(r)(n); cliques of a colour, their size counted in vertices
      R_(r)(k, l), for red/blue colourings of hyper-edges
      K_(1)(4), K_(2)(4), K_(3)(4), and a clique in a coloured K_4,
        drawn                                                       [supplied]
      R_(1)(k, l) = k + l - 1, by pigeonhole                        [supplied]
    6.1.3 A Recursive Upper Bound                   [2026-09-25]
      R_(r)(k, l) <= R_(r-1)(R_(r)(k-1, l), R_(r)(k, l-1)) + 1 for
        r, k, l >= 2, by the shadow colouring at one vertex
      the two cases of the proof, and A, B and n named             [supplied]
      H a copy of K_(r-1)(n-1); at r = 2 the graph bound above      [supplied]
      every R_(r)(k, l) exists, by induction on r, then k + l       [supplied]
    6.1.4 A Better Upper Bound                      [2026-09-28]
      the recursion unwound: a tower for R_(3), a super-tower for R_(4)
      the stepping-up construction for R_(3): a sequence x_1, ..., x_{m+1}
        in which the colour of a triple depends on its first two, by
        halving; R_(3)(k, l) <= 2^{m^2} with m = R_(2)(k-1, l-1)
      the same for R_(r): R_(r)(k, l) <= 2^{binom(m, r-1) + 1} with
        m = R_(r-1)(k-1, l-1), "for r, k, l sufficiently large"
    6.1.5 Cups and Caps                             [2026-09-28]
      k-caps and k-cups, drawn; ES(k, l), for points in general position
      ES(k, l) <= ES(k-1, l) + ES(k, l-1) - 1 for k, l >= 3, by the last
        points of (k-1)-caps and the slopes at p_1, drawn
      ES(k, l) <= 2 binom(k+l-4, k-2) <= 2^{k+l}, by induction on k + l

6.2 Van der Waerden's Theorem                       [2026-09-30, 2026-10-07]
    Asks the Ramsey question of the integers: must an r-colouring of N
    contain arbitrarily long monochromatic arithmetic progressions?
      VW(k, r), and the theorem that it exists; VW(2, r) = r + 1     (preamble)
    6.2.1 Colour-Focusing                           [2026-09-30]
      VW(3, 2) >= 9, from the colouring RRBBRRBB                     [supplied]
      VW(3, 2) <= 325, by blocks of five, two identically coloured
        blocks and the block 2j - i, drawn
      colour-focused APs and their focus point
      VW(3, 3) <= 30625 (2 * 3^30625 + 1), by going up one level,
        drawn
    6.2.2 Colour-Focus Numbers                      [2026-09-30]
      CF(k, r, s), the least N forcing a monochromatic (k+1)-AP or s
        colour-focused k-APs of different colours with focus in [N]
      VW(k, r) <= CF(k-1, r, r)
      CF(k, r, s) <= CF(k, r, s-1) * 2 VW(k, r^{CF(k, r, s-1)}) for
        2 <= s <= r, by stretching APs across an AP of blocks, drawn
      CF(k, r, s) exists, by induction on k and then on s; van der
        Waerden's theorem as the corollary
    6.2.3 A Lower Bound from the Local Lemma        [2026-10-07]
      VW(k, 2) > (k-1) 2^{k-1} / (e k^2), so Omega(2^k / k), from the
        symmetric local lemma; the lecture quoted the bound as
        "shown", and nothing in the notes had shown it               [supplied]

6.3 The Hales--Jewett Theorem                       [2026-10-02, 2026-10-05, 2026-10-07]
    Strips the arithmetic out of colour-focusing: colours the hypercube
    [n]^d and forces a combinatorial line, then reads progressions off it.
    6.3.1 Combinatorial Lines                       [2026-10-02]
      templates, active and fixed coordinates, L_sigma, the last point   [supplied]
      the three combinatorial lines of [3]^2 through a point, and the
        anti-diagonal that is not one                                [supplied]
      HJ(n, r), and the theorem that it exists
    6.3.2 Colour-Focused Lines                      [2026-10-05]
      colour-focused lines, and the 3 x 3 example, drawn
      FHJ(n, r, s); HJ(n, r) <= FHJ(n, r, r)                        [supplied]
      FHJ(n, r, s) <= FHJ(n, r, s-1) + HJ(n-1, r^{n^{FHJ(n, r, s-1)}})
        for 2 <= s <= r: the lecture's setup, with the [n]^{D_1 + D_2}
        split drawn, and the concatenation of lines completed        [supplied]
      the Hales--Jewett theorem, by induction on n then s, with
        FHJ(n, r, 1) <= HJ(n-1, r) as the base                        [supplied]
    6.3.3 From Lines to Progressions                [2026-10-02, 2026-10-07]
      Gallai's theorem: a monochromatic alpha X + beta in any
        r-colouring of Z^k, by colouring [n]^d through sums of the
        x_i; sourced to Graham-Rothschild-Spencer ch. 2 and to
        Hales-Jewett 1963                                            [supplied]
      phi: [n]^d -> [n^d] by base-n digits takes lines to progressions,
        so VW(n, r) <= n^{HJ(n, r)}                                   [supplied]
      why that is all the argument needs of phi, and gamma, the sum
        of squares, giving quadratic progressions

6.4 Infinite Ramsey Theory                          [2026-10-07]
    The complete graph on N, where every 2-colouring of the edges has
    an infinite monochromatic clique, and the finite statement that
    Peano arithmetic cannot prove.
      the infinite clique, by the standard nested-neighbourhood
        argument; the lecture's argument coloured vertices          [CORRECTED]
      relatively large sets, and the large Ramsey number R-bar;
        rewritten on the author's instruction                        [supplied]
      Paris-Harrington: its existence is unprovable in PA, cited
```

Material marked `[handwritten]` is the second half of the lecture of 4 September
2026: the laptop died partway through it (a35742c, "PARTIAL - LAPTOP ABOUT TO
DIE"), and the rest arrived typed in the inbox a week later (885c140, "things up
to lecture 8", 2026-09-11), so it was typed up afterwards rather than live,
presumably from handwritten notes. A reviewer of PR #22 read the same history as
showing 9 September material; both readings fit it, the marker records only
that the text was not typed in the lecture, and it is left as it is. [settled
2026-10-07]

Entries marked `[supplied]` are arguments this repository's skills worked out,
not arguments the lecturer gave; each carries a `% [FILLED]`, `% [CLAUDE]`-derived
or `% Not from the lecture` comment at its site.

`Chapters/1_Intro/` is the author's directory name for chapter 1 across three of
the four sibling repositories, whatever that chapter is titled. It now holds the
probability chapter rather than the graphs one; it is a convention, not template
residue, and is not a misnomer for a chapter called *Probability*. Leave it.

The inbox is `Chapters/todays_lecture.tex`, beside the chapter directories rather
than inside one, and `main.tex` `\input`s it after every chapter. It was moved there
on 2026-09-15, out of `Chapters/1_Intro/`, because one lecture's material is normally
spread across several chapters and the file it arrives in should not belong to any of
them; until then a lecture about set systems rendered under chapter 1 until it was
integrated. `CLAUDE.md` and the `/integrate` and `/post-lecture` skills name the new
path. Material typed there is found by `/integrate` from the git history, not from its
position in the document.

## Deliberate deviations

Places where the structure does not yet look like `ORGANISATION.md` describes,
tolerated on purpose, with the condition that ends each one.

```
Chapter 1 is three sections of thirty-odd lines each, where the corpus runs 2-8
    sections of median 148 lines.
    Why tolerated: the author asked for it explicitly on 2026-09-15 and said to
    build it on the assumption that more probability is coming. A chapter with
    too few sections self-heals as lectures arrive; carving one line of enquiry
    into three would not, and these are three -- what the objects are, what the
    average is, how far from it things stray.
    Ends when: two or three more lectures' worth of probability has arrived, at
    which point the section sizes take care of themselves.

1.2 Expectation is a section with one subsection.
    Why tolerated: the author asked for expectation to be a section and
    conditional expectation a subsection of it, which is exactly this shape, and
    4 of the corpus's 66 sections have exactly one subsection. The preamble
    material -- the definition and the two facts about independent variables --
    is the obvious second subsection once anything else lands beside it.
    Ends when: a lecture adds enough to expectation proper to name it.

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
    now 6.1.

2.2 Ramsey Numbers was a section with one definition, one figure and no result
    (tolerated 2026-08-26, to end when a lecture returned to Ramsey theory).
    ENDED 2026-09-25: the lecture of that date did, with hypergraph Ramsey
    numbers, now 6.1.2 and 6.1.3.

The chapter title "Graphs and Colourings" was a bet on one lecture (2026-08-24).
    MET 2026-08-28 and worse by 2026-08-31, when half the chapter was set
    systems. RESOLVED 2026-09-02 by /organise: the set-systems sections became
    a chapter of their own, and the graphs chapter is again about what its title
    says. That chapter is now chapter 2 and the set systems chapter 3.
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
                                 Since used as a tool in 3.2, 3.3 and 2.2.4.
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
the converse threshold           "our goal is to show that once the expected
                                 number of Js goes to infinity, we have a copy
                                 of H" --- stated 2026-09-09 as the destination of
                                 4.1 and not reached. It is the second-moment
                                 half of the threshold theorem, and 1.3's
                                 corollary plus 4.1's triangle proof are the
                                 two pieces it needs.
Szemeredi                        named in passing 2026-09-04, in the handwritten
                                 notes, as what eps(H) is "some sort of edge
                                 density for". Nothing further.
Hoeffding's extension            asserted 2026-09-11: the same bound for
                                 independent xi_i with |xi_i| <= 1 and mean 0.
                                 The chord argument for a single factor is
                                 written out; the deduction of the full bound
                                 from it is not.
fourth moment bounds             mentioned 2026-09-11 as enough for the degrees
                                 of G_{n,1/2}, "but that won't always be the
                                 case". Not carried out.
perfect graphs                   defined 2026-09-02 and then left: the lecture named
                                 the class in which omega = chi holds hereditarily
                                 and went straight to how badly it can fail. If a
                                 lecture develops them, 2.2.2 is the seed of a
                                 section.
chi(G) >= |V(G)| / alpha(G)      used 2026-09-02 with "thus" at the end of the Erdos
                                 proof. True because each colour class is an
                                 independent set; the notes do not say it.
girth exactly k, chi exactly k   the lecture stated Erdos's theorem with equalities;
                                 the proof gives girth > k and chi >= k, and the
                                 statement now says "at least". The exact form does
                                 follow for k >= 3 (delete vertices until chi = k,
                                 then add a disjoint C_k); recorded in a CORRECTED
                                 comment in 2.2.4, not in the notes.
McDiarmid's proof                begun 2026-09-16 and broken off at the
                                 definition of g_i. Left \sorry on the author's
                                 instruction: Wes is to post notes on Azuma and
                                 McDiarmid, to be integrated with attribution.
the Smiley Face Lemma            stated 2026-09-16 as an application of
                                 McDiarmid, from Frieze and Pegden, "Separating
                                 subadditive Euclidean functionals", RSA 51
                                 (2017) 375-403. Not proved. Carried a SUSPECT
                                 until 2026-10-07: as written it was false for
                                 every bounded region D. Settled against the
                                 paper's Observation 3.1, where D is a distance
                                 and a copy is isolated from the other points.
                                 The name is the lecturer's; it is not in the
                                 paper.
2-colourability from the LLL      posed 2026-09-16 as the motivation for the local
                                 lemma: what condition on k makes a k-uniform
                                 hypergraph whose edges each meet at most D
                                 others 2-colourable? The bad events and their
                                 probability 2^{-(k-1)} are set up; the answer
                                 needs the local lemma, whose proof is next
                                 lecture's. It generalises 2.1.4's union bound.
the Lovasz Local Lemma's proof   promised 2026-09-16 for next lecture, in the
                                 author's own words on the \sorry; no later
                                 lecture in the notes gave it. SUPPLIED
                                 2026-10-07, marked [FILLED].
Azuma's inequality               stated 2026-09-14 and not proved. The notes say
                                 what the proof is --- 4.2's exponential-moment
                                 argument applied to each increment
                                 conditionally --- and do not carry it out.
the tower property               stated 2026-09-14, and the second display of
                                 1.2.1 with it, under one "it is easy to show".
                                 Neither is proved.
chi(G_{n,1/2}) ~ n / log n       asserted 2026-09-14 in 4.3.2, as the thing the
                                 sqrt(n) window is narrow compared to. From
                                 outside the course, and flagged as such where
                                 it is used.
Moser's spindle has chi = 4      asserted 2026-09-21 ("it turns out") and not
                                 proved. The spindle is drawn to scale in 2.3.1;
                                 why it has no 3-colouring is not in the notes.
the de Bruijn-Erdos theorem      the compactness theorem of 2.3.2, 2026-09-21,
                                 not named in the lecture. Its content is the
                                 lemma after it, whose proof was completed on
                                 2026-10-07, together with the theorem's.
Beck's theorem                   stated 2026-09-21, not named and not proved:
                                 an infinite binary sequence whose identical
                                 blocks of length n are at least (2 - eps)^n
                                 apart. "Our argument will involve binary
                                 sequences" says the lecture means to prove it,
                                 presumably by the local lemma on finite words
                                 and then compactness. Now 5.2.
Erdos-Szekeres                   stated 2026-09-25 as the motivation for
                                 hypergraph Ramsey numbers, and explicitly not
                                 proved that day. How it follows from them is
                                 not yet said.
finiteness of R_(r)(k, l)        assumed 2026-09-25 and not shown: R_(r)(k, l)
                                 is defined as a least n, and 6.1.3 is a bound
                                 on it that presumes the right-hand side exists.
                                 The proof's "by induction" points at the
                                 argument (on r, then k + l), whose bases, the
                                 lemma and R_(r)(1, l) = R_(r)(k, 1) = 1, are not
                                 written. Raised by both reviewers of #25. Now
                                 the corollary closing 6.1.3, supplied on the
                                 author's instruction (2026-09-30).
R(k, l) <= R(k-1, l) + R(k, l-1)  "what we know about Ramsey numbers on graphs",
                                 2026-09-25. Now stated in 6.1.1 on the
                                 author's instruction (2026-09-29), unproved:
                                 "See undergraduate graph theory notes", with a
                                 \todo for the cross-reference to Michele's notes.
                                 6.1.3 cites it, and notes that its own bound
                                 at r = 2, with the lemma, is this one.
R_(2)(k, l) <= binom(k+l-2, k-1)  "Recall also that", 2026-09-28, at the top of
                                 6.1.4. It follows from the graph recursion
                                 above by induction, and the notes do not say
                                 so.
"sufficiently large" in 6.1.4    the stepping-up theorem of 2026-09-28 is stated
                                 for r, k, l "sufficiently large"; the middle
                                 inequality binom(m, r-1) + 1 <= m^{r-1} needs
                                 r >= 3, and nothing else needs more. Left as
                                 the lecturer put it.
convex problems                  "improve the bound even further when we're
                                 dealing with convex problems", 2026-09-28:
                                 reached the same day, as 6.1.5. The exact value
                                 ES(k, l) = binom(k+l-4, k-2) + 1 is not stated.
VW(3, 2) = 9                     only 9 <= VW(3, 2) <= 325 is in the notes
                                 (2026-09-30); that 9 suffices is not shown.
VW(k, 2) = Omega(2^k / k)        the lecture of 7 October said this had been
                                 "shown using the Lovasz Local Lemma"; no
                                 lecture in these notes shows it, so the
                                 proposition is supplied in 6.2.3 and marked.
                                 The lemma it uses was itself a \sorry until
                                 the same day.
the Lean aside                   "In Lean this would be induction k generalizing
                                 r s", a footnote of 2026-09-30, is why
                                 listings and lstlean.tex arrived in #26.
infinite Ramsey for k-sets       6.3 states and proves only the case of edges
                                 and 2 colours (2026-10-07); the large Ramsey
                                 number is defined for k-subsets and c colours,
                                 and its existence "follows from the infinite
                                 version of Ramsey's theorem by a compactness
                                 argument, which we will not give".
Paris-Harrington                 named 2026-10-07 and explicitly not proved.
```

## Unplaced

Nothing. The local lemma of 2026-09-16 and Beck's theorem of 2026-09-21 were
held in the inbox, the first on the author's instruction, until the author asked
on 2026-09-23 for the inbox to be emptied; they are now chapter 5.

The lectures of 28 and 30 September 2026 were held out of the notes until
2026-10-07 at the author's request (they are the author's assessed contribution
to a collective notes repository, and were edited in a local-only copy
meanwhile). They arrived in #26 together with the lectures of 2, 5 and 7
October, and were integrated with them on 2026-10-07. The same commit re-synced
the 25 September block, already integrated in #25, into the inbox; that copy was
byte-identical to the pre-#25 inbox and was dropped, not integrated twice.

## Structural pressure

Observations for `/organise`, recorded rather than acted on.

```
2.1.5 Maker-Breaker Games is a game inside a section about colourings.
    It earns its place for now: Erdos-Selfridge is the same 2^(k-1) threshold as
    2.1.4, so the subsection continues that line of enquiry rather than opening
    a new one, and the lecturer closed it with "we won't say any more about
    tic-tac-toe in this course". If a later lecture returns to positional games,
    this wants lifting out into a section of its own. [noted 2026-08-26,
    re-examined and left 2026-09-02, 2026-09-15, 2026-10-07]

The "moreover" of Erdos-Ko-Rado is stated twice in 3.3, once inside the theorem
    and once as the extremal theorem that actually proves it. The duplication is
    the author's -- both were written in the lecture -- and neither /integrate
    nor /organise may delete a statement, so both stand, with the second
    cross-referenced as the first made precise. Merging them is the author's
    call. [noted 2026-08-31, left 2026-09-02, 2026-09-15, 2026-10-07]

The Lovasz Local Lemma is a new body of theory parked at the end of a chapter
    about concentration. It is in the inbox rather than in chapter 4, so it is not
    yet a structural fact, but it is the shape of one: avoiding a family of bad
    events is not what "Moments and Concentration" names, and the lemma brings its
    own vocabulary --- dependency graphs, the x_A weights, the ~ relation. If next
    lecture's proof and applications land as expected this wants a chapter of its
    own rather than a fifth section of chapter 4, and the union bound of 2.1.4 that
    it generalises is two chapters back. Do not act on this until the material has
    somewhere to be. [noted 2026-09-16; ACTED ON 2026-09-23, when the author
    asked for the inbox to be emptied: the local lemma is now chapter 5, whose
    introduction points back at 2.1.4's union bound. The author confirmed chapter
    5 as its home the same day]

4.3 Martingales is four subsections and the only section in chapter 4 with any,
    which is a sign it is carrying two lines of enquiry rather than one: 4.3.1 and
    4.3.2 build a martingale and bound it, 4.3.3 and 4.3.4 generalise the
    construction and read a second inequality off it. Both halves are about the
    same object, so it is left as one section, and the corpus tolerates four
    subsections comfortably. Worth re-examining if a lecture adds a third
    inequality of this kind. [noted 2026-09-16, re-examined and left 2026-10-07]

1.3 Deviation from the Mean and chapter 4 both bound deviations, and a reader
    could reasonably ask why Markov and Chebyshev are not in chapter 4 with
    Chernoff and Azuma. The line drawn is use: 1.3 holds the two inequalities
    the other chapters apply as tools and never discuss, and chapter 4 is where
    concentration is the subject. That line is defensible but it is a line, and
    it is worth re-examining the first time a lecture proves something new about
    Markov or Chebyshev rather than merely using them. [noted 2026-09-15,
    re-examined and left 2026-10-07]

2.3.2 Compactness is about every graph, and sits under the plane only because
    the lecture introduced it for the plane: the lemma is de Bruijn-Erdos, for
    any G. Beck's theorem, now 5.2, will need the same
    compactness step for sequences rather than colourings. If the course keeps
    passing from finite to infinite this way, the compactness argument may want
    a home of its own, nearer the local lemma than the plane. [noted 2026-09-21,
    re-examined and left 2026-10-07: Beck's theorem is still only stated, so
    the second use of compactness does not yet exist]


```

Resolved by the `/organise` pass of 2026-10-07, kept as a record:

```
Ramsey theory was split across two chapters [noted 2026-09-25 as "2.2 is a
    preamble about graphs with two subsections about hypergraphs", and
    2026-10-07 as the split proper]. Section 2.2, Ramsey Numbers, moved whole
    into chapter 6 as 6.1, its preamble becoming 6.1.1 Ramsey Numbers of
    Graphs and its four subsections 6.1.2-6.1.5; van der Waerden,
    Hales--Jewett and infinite Ramsey became 6.2-6.4. Chapter 2 is three
    sections of colouring graphs, which is what its title says, and 2.3 and
    2.4 became 2.2 and 2.3. The five labels of the moved section changed
    prefix from Ch2: to Ch6:; every \Cref to them was inside the section.
    The sentence of chapter 2's introduction that announced Ramsey numbers
    moved, with its [CORRECTED] note, to chapter 6's. Nothing else moved.
```

Resolved by the `/organise` pass of 2026-09-15, kept as a record:

```
Chapter 3 should have been chapter 1, and the author said so twice [noted
    2026-09-11, acted on 2026-09-15]. The probability material was written last
    and used first: Markov's inequality was stated in 3.1 and used by name in
    the proof of Erdos's girth theorem twenty pages earlier, which carried a
    forward \Cref saying so. The terse review is now chapter 1 in its own right,
    the forward reference is a backward one, and the apologetic parenthesis
    around it is gone. Everything in the notes renumbered: chapters 1, 2 and 3
    became 2, 3 and 4, every label's Ch<N>: prefix moved with its chapter, and
    Markov, Chebyshev and the second-moment corollary went from Ch3: to Ch1:.

3.1 A Terse Review of Probability was one undivided section, and by 2026-09-14
    a long untitled preamble with one subsection bolted on the end [noted
    2026-09-14]. It is now chapter 1's three sections: 1.1 Probability Spaces,
    1.2 Expectation with 1.2.1 Conditional Expectation, and 1.3 Deviation from
    the Mean. The author specified the middle one.
```

Resolved by the `/organise` pass of 2026-09-02, kept as a record:

```
The m(3) = 7 development was loose prose at the end of 2.1.2 [noted 2026-08-26].
    Now subsection 2.1.3, The Value of m(3). Results number per section, so
    nothing was renumbered.

Chapter 1 was called "Graphs and Colourings" and half of it was set systems
    [noted 2026-08-28, 2026-08-31, 2026-09-02]. Those sections became their own
    chapter, Set Systems; Chromatic Number moved next to the colouring it
    continues. Everything in the moved sections was renumbered, and five labels
    changed their chapter prefix.

Whether the three set-systems sections were one section, a chapter, or one
    section plus two [noted 2026-08-28, 2026-08-31]. A chapter of three
    sections: Hall, Sperner and Erdos-Ko-Rado ask three different questions of a
    family of sets, and 3.2 and 3.3 share a method but not a question.

The author's \section{Perfect Graphs} was demoted by /integrate and its tail
    split off [noted 2026-09-02]. /organise went one step further and split
    Zykov's construction out of it as 2.3.3 (2.2.3 since 2026-10-07), so that "Perfect Graphs" now
    heads only the two definitions and the ToC shows the construction.

Intersecting Families had no subsections and two theorems with proofs. Now
    3.3.1 The Erdos-Ko-Rado Theorem and 3.3.2 The Extremal Case. The weakest of
    the 2026-09-02 changes: a subsection-free section is legitimate in the
    corpus, and this one was split so that the second theorem is visible from
    the table of contents.
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
