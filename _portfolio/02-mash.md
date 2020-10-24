---
layout: post
title: "Mash: Accelerated Genomic Distance Measurement"
tags: [Test, Ipsum, Markdown, Portfolio]
feature-img: "assets/img/mash-banner.png"
thumbnail: "assets/img/mash.png"
pubs:
-   pdf: mash.pdf
    type: Paper
    journal: Genome Biology
    doi: https://doi.org/10.1186/s13059-016-0997-x
    journal: Genome Biol
    date: "2016-06-20"
    authors: Brian Ondov, Todd Treangen, Páll Melsted, Adam Mallonee, Nicholas Bergman, Sergey Koren, Adam Phillippy
    title: "Mash: fast genome and metagenome distance estimation using MinHash"
-   authors: Brian Ondov, Gabriel Starrett, Anna Sappington, Aleksandra Kostic, Sergey Koren, Christopher Buck, Adam Phillippy
    title: "Mash Screen: high-throughput sequence containment estimation for genome discovery"
    date: "2019-11-05"
    journal: Genome biology
    pdf: screen.pdf
    type: Paper
    journal: Genome Biology
    doi: https://doi.org/10.1186/s13059-019-1841-x
badges:
- CB
---

Comparing a pair of genomes, say, to identify a new sample as a pathogen or not,
can be done fairly quickly. But if you need pairwise comparisons among a large
group of genomes, like for building trees of their ancestry, the problem becomes
quadratic and quickly explodes.

Inspired by an [algorithm](https://doi.org/10.1109/SEQUEN.1997.666900) for
duplicate detection in web search, we used locality sensitive hashing to
preprocess thousands of genomes, creating small signatures of each called
sketches. Comparing these sketches is orders of magnitude faster than the whole
genomes, making the quadratic step of pairwise comparison much more tractable.
This allowed us to perform an unprecedented clustering, shown below, of every
organism in [RefSeq](https://www.ncbi.nlm.nih.gov/refseq/), the major repository
of reference genome sequences.

<img style="margin:auto;" src="/assets/img/mash.png"/>

The sketching strategy also vastly reduces the memory footprint of
searching a single sample against a large database, such as RefSeq, allowing
real time search on limited hardware, as described in this talk:

<iframe src="https://player.vimeo.com/video/148872250?title=0&byline=0&portrait=0" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

### Containment ###

What if, instead of comparing two similarly-sized genomes, we want to ask
whether a small sequence (like a microbial genome) is contained in a much larger
sequence (e.g. a metagenome)? It turns out the original algorithm doesn't work
so well for this case. This motivated us to adapt it into a new method that acts
as a "screen." Instead of creating a sketch for the larger sequence mixture, we
stream through all of it while keeping track of hits to a database of reference
sketches.

<img style="margin:auto;" src="/assets/img/screen.png"/>

Combined with a large compute cluster, the efficiency of this approach allowed
us to create an unprecedented table of the containment of all RefSeq genomes
(~100,000) within every metagenome (~100,000) in the [SRA](https://www.ncbi.nlm.nih.gov/sra)
(the major repository for raw sequence data). This provides a valuable resource
for retrospective discovery, for example finding relatives of a newly discovered
virus.
