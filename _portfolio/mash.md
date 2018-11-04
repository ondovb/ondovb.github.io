---
layout: post
title: Mash
subtitle: Accelerated genomic distance measurement
tags: [Test, Ipsum, Markdown, Portfolio]
feature-img: "assets/img/mash-banner.png"
thumbnail: "assets/img/mash.png"
---

Comparing a pair of genomes, say, to identify a new sample as a pathogen or not,
can be done fairly quickly. But if you need pairwise comparisons among a large
group of genomes, like for building trees of their ancestry, the problem becomes
quadratic and quickly explodes.

Inspired by algorithms for duplicate detection
in web search, we used locality sensitive hashing to preprocess thousands of
genomes, creating small signatures of each called sketches. Comparing these
sketches is orders of magnitude faster than the whole genomes, making the
quadratic step of pairwise comparison much more tractable. This allowed us to
perform an unprecedented clustering, shown below, of every organism in
[RefSeq](https://www.ncbi.nlm.nih.gov/refseq/), the major repository of reference
genome sequences.

<img style="margin:auto;" src="/assets/img/mash.png"/>

The sketching strategy also vastly reduces the memory footprint of
searching a single sample against a large database, such as RefSeq, allowing
real time search on limited hardware:

<iframe src="https://player.vimeo.com/video/148872250?title=0&byline=0&portrait=0" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

More at [mash.readthedocs.io](https://mash.readthedocs.io/en/latest/).
