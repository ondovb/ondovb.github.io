---
layout: post
title: Krona
subtitle: Interactive hierarchical exploration
tags: [A Tag, Test, Lorem, Ipsum]
excerpt_separator: <!--more-->
feature-img: "assets/img/krona-banner.png"
thumbnail: "assets/img/krona.png"
---

Visualizing metagenomic communities, such as the types bacteria in the human
microbiome, can be complicated by levels of granularity. For example, you may
not know a priori whether you should be looking at the species level or genus
level, or perhaps even higher if you would like to see host DNA or contamination.

We approached this problem using sunburst displays, which show meaningful
overviews across complex hierarchies. However, to fully explore the
complexity of a microbiome, we also had to allow interactivity, which we
provided with a novel,
radial zooming technique. Our implementation creates self-contained HTML files,
with data embedded as XML and the interface JavaScript in the header. These can
easily be shared or embedded, like this one:

<iframe scrolling="no" style="padding:0;width:100%;height:400px;" src="http://marbl.github.io/Krona/examples/rdp.krona.html?dataset=0&node=571&collapse=true&color=false&depth=8&font=10&key=true"></iframe>

More at [github.com/marbl/Krona/wiki](https://github.com/marbl/Krona/wiki).
