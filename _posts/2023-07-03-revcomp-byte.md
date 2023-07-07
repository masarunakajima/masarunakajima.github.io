---
layout: post
title: Reverse compliment in BAM format
date: 2023-07-03 11:39:00
description: Improving the efficiency by working directly with native data structure
---
## Little bit about BAM format

The [BAM](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://samtools.github.io/hts-specs/SAMv1.pdf)
format is used to store sequence alignment information in a compressed,
binary representation. It is a more compact alternative to the SAM format. The
[HTSlib](https://github.com/samtools/htslib) library provides tools to work
with the above formats. One of the basic object in this
library is the `bam_t` structure which represents an alignment record. This
object stores information such as the location of the alignment against the
reference genome, query sequence, and CIGAR string.

## Query sequence

Today, I wan to focus on the query sequence stored in `bam_t` format. Each base is repsented by a 4-bit integer, as shown below.

| Base | Number | Binary   |
| ---- | ------ | -------- |
| A    | 1      | `0001` |
| C    | 2      | `0010` |
| G    | 4      | `0100` |
| T    | 15     | `1000` |

This allows packaging 2 bases in one byte. For example the sequence `ACGTA` can
be represented as `00010010 01001000 00010000`. That is, we can represent a
 `n`-long sequences in `ceil(n/2)` bytes. Here, let's call two bases packed in
 a byte as a **base couple**.

## Reverse compliment

 In processing alignment data, we often need to reverse compliment the query.
 For example, we may want to merge a paired-end reads, which involves taking
 the reverse compliment of the second read. Given a sequence represented in the
 above format, one way to accomplish is to decode the sequence into a string,
 take the reverse compliment, and encode it back to the above format. However,
 it would be faster and memory efficient if we could do this without decoding
 and encoding the sequence. The method I used is to take the reverse compliment
 of each base couple and reverse the order of the base couples. The code is
 shown below.

```c
static inline void
revcom_byte_then_reverse(unsigned char *a, unsigned char *b) {
  unsigned char *p1, *p2;
  for (p1 = a, p2 = b - 1; p2 > p1; ++p1, --p2) {
    *p1 = byte_revcom_table[*p1];
    *p2 = byte_revcom_table[*p2];
    *p1 ^= *p2;
    *p2 ^= *p1;
    *p1 ^= *p2;
  }
  if (p1 == p2) *p1 = byte_revcom_table[*p1];
}

static void
revcomp_seq_by_byte(bam1_t *aln) {
  const size_t l_qseq = get_qlen(aln);
  auto seq = bam_get_seq(aln);
  size_t num_bytes = ceil(l_qseq / 2.0);
  auto seq_end = seq + num_bytes;
  revcom_byte_then_reverse(seq, seq_end);
  if (l_qseq % 2 == 1) {
    for (size_t i = 0; i < num_bytes - 1; i++) {
      seq[i] = (seq[i] << 4) | (seq[i + 1] >> 4);
    }
    seq[num_bytes - 1] <<= 4;
  }
}
```

Here, `byte_revcom_table` is a lookup table that stores the reverse compliment
of the base couples. The function `revcom_byte_then_reverse` takes two pointers
and reverse the compliment of the base couples between them. For example, if
the sequence of base couples is `AC GT TA`, then the function will change it to
`TA AC GT`, which is the reverse compliment of the entire sequence. However,
if the number of bases is odd, then this function outputs a sequence that is
not quite the reverse compliment. For example, if the sequence of base couples
is `AC GT T-`, then the function will change it to `-A AC GT`, where what we
want is `AA CG T-`. The rest of the function `revcomp_seq_by_byte` takes care
of this case.
