---
layout: page
title: Counting RNA secondary structures (PhD)
description: First polynomial-time algorithm for symmetry-distinct RNA structures
img: assets/img/rnadist.png
importance: 1
github: https://github.com/masarunakajima/distinguishable_count
category: research
---
For my PhD at USC (Smith Lab), I developed a new algorithm
for counting distinguishable RNA secondary structures. This problem is
central to the combinatorial analysis of RNA structures, a
fundamental topic in computational biology. The algorithm I
developed is the first to solve the problem in polynomial time.
It combines group theory with dynamic programming. The work was published in the
[Journal of Computational Biology (2023)](https://www.liebertpub.com/doi/full/10.1089/cmb.2022.0501). I implemented the
algorithm in C++ and validated it on a high-performance computing cluster ([GitHub](https://github.com/masarunakajima/distinguishable_count)).

## Abstract

> RNA secondary structures are essential abstractions for
> understanding spacial folding behaviors of those macromolecules.
> Many secondary structure algorithms involve
> a common dynamic programming setup to exploit the property that
> secondary structures can be decomposed into substructures.  Dirks et
> al. (2007) noted that this setup cannot directly address an issue of
> distinguishability among secondary structures, which arises for
> classes of sequences that admit non-trivial symmetry.  Circular
> sequences are among these. We examine the problem of counting
> distinguishable secondary structures. Drawing from elementary
> results in group theory, we identify useful subsets of secondary
> structures. We then extend an algorithm due to Hofacker et
> al. (2012) for computing the sizes of these subsets. This yields a
> cubic-time algorithm to count distinguishable structures compatible
> with a given circular sequence. Further, this general approach may
> be employed to solve similar problems for which the RNA structures of
> interest involve symmetries.
