---
layout: page
title: RNA count (PhD)
description: Development of a new counting algorithm
img: assets/img/rnadist.png
importance: 1
github: https://github.com/masarunakajima/distinguishable_count
category: work
---
For my PhD project, I worked on the development of a new algorithm
for counting distinguishable RNA secondary structures. This work is
relevant in combinatoric analysis of RNA structures, which is a
fundamental problem in computational biology. The algorithm I
developed is the first that solved the problem in polynomial time.
This work has been accepted for publication in the Journal of
Computational Biology (publication pending). I implemented the
algorithm in C++ ([github](https://github.com/masarunakajima/distinguishable_count)).

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
