---
layout: post
title: Region Expansion in Triangular Quadtrees
pubs:
-   authors: Brian Ondov, Hanan Samet
feature-img: "assets/img/regions-banner.png"
thumbnail: "assets/img/regions.png"
badges:
- GIS
---

In Geographic Information Systems, often a region needs to be expanded to
include everything within a certain distance, creating a "buffer" zone. For
example, you may want to query everything that is within a mile of a shoreline
or in the wider corridor of a highway. This operation is also useful in photo
editing, computer vision, and robot motion planning. 

If the region is stored in a square [quadtree](https://en.wikipedia.org/wiki/Quadtree),
[Ang et al.](https://doi.org/10.1109/34.56221) showed that these regions can be
quickly approximated using the L<sub>∞</sub>-norm (i.e. the
[chessboard distance](https://en.wikipedia.org/wiki/Chebyshev_distance)) instead
of euclidean distance.

Sometimes, though, maps are stored in triangular quadtrees, for example in
[astronomy](http://voservices.net/footprint/) applications. For these cases, the
chessboard distance cannot be used, and the algorithm of Ang et al. is not
directly applicable.

<img style="margin:auto;" src="/assets/img/regions.png"/>

Using the principles of the original method by Ang et al., we create a new
algorithm that quickly approximates region expansion in triangular quadtrees,
using a triangle-friendly, hexagonal norm instead of the L<sub>∞</sub>-norm. We
show that this algorithm can perform similarly to the square quadtree case,
greatly accelerating the operation versus a naïve method.
