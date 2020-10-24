---
layout: post
title: Exploring syntactic attention in Transformers
excerpt_separator: <!--more-->
feature-img: "assets/img/attention-banner.png"
thumbnail: "assets/img/attention.png"
pubs:
-   pdf: /assets/attention.pdf
    type: Manuscript
    authors: Yancy Liao, Jacqueline Nelligan, Brian Ondov, Gina Wong
badges:
- ML
- NLP
---

The Transformer, which has quickly become the state-of-the-art architecture
for neural language processing, is based on the principle of self-attention, or
attention within the same sentence. This allows embeddings not just
of words, but of whole phrases and sentences into a rich latent space, letting
knowledge from single-language, self-supervised learning transfer to all kinds of
supervised downstream tasks. However, we are only beginning to understand what
the multiple attention "heads" of the architecture actually learn to attend to,
and whether they specialize to linguistic rules as we might expect intuitively.

Drawing from the work of <a href="https://arxiv.org/abs/1906.04341">
Clark et al.<a/> and <a href="https://arxiv.org/abs/1905.09418">Voita et al.</a>,
we explore the roles of attention heads by comparing syntactic parses of
sentences to the activations they induce in the network. Using a model trained
end-to-end for English-to-German translation, we recapitulate some of the
phenomena that Clark et al. observed in BERT, which is pre-trained monolingually.
For example, we find attention heads whose activations are good predictors of
determiners and direct objects in the source sentence.

<img style="margin:auto;" src="/assets/img/attention1.png"/>
<img style="margin:auto;" src="/assets/img/attention2.png"/>

We also recapitulate the finding of Voita et al. that transformers
can learn to prune many heads across various layers without significantly
degrading performance. Interestingly, however, we also found that if the learned
pruning was reversed---that is, masking heads found to be important, while
keeping the rest---performance still was not significantly degraded. This
suggests that, while these networks are indeed robust to ablation, specific
syntactic functions may be more distributed than suspected.
