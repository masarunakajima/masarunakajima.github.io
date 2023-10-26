---
layout: page
title: dnmtools project
description: Bioinformatics tool development
img: assets/img/4.jpg
importance: 1
github: https://github.com/smithlabcode/dnmtools
category: work
---
I am a committer to
[dnmtools](https://github.com/smithlabcode/dnmtools), a software suite,
written primarily in C/C++, for the analysis of DNA methylation data.
My role in this project was to improve the efficiency of some of the tools,
and I enjoyed the learning! [Here](https://github.com/smithlabcode/dnmtools/commits?author=masarunakajima) is the list of my commits.

## Formatting alignment files

Computational biologists often work with large files of DNA sequences,
and it is important that these files are formatted correctly. In the
context of DNA methylation data, we work with alginment data we call *reads*.
These reads are aligned, or mapped, to the reference genome,
and the alignment data
are stored in [SAM/BAM](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://samtools.github.io/hts-specs/SAMv1.pdf) format. This is accomplished
by `dnmtools abismal`. We further process the alignment data using
`dnmtools format` to format the the mapped reads for downstream analysis.
My first task was to improve the efficienty of `dnmtools format`.
I wrote the details in my [blog](../../blog/2023/revcomp-byte).
The outcome was about 30 % reduction in computation time, which can be
a lot when you are working with large files.

