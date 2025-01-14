---
layout: post
title: Stanford's Workshop on Foundation Models
author: Rylan Schaeffer
date: 2021-08-24
tags: artificial-intelligence
---

Stanford HAI's new Center for Research on Foundation Model hosted a workshop
yesterday and today to discuss [foundation models](https://arxiv.org/abs/2108.07258?sf149288348=1),
the term Stanford professors gave to models that are trained at scale and are adaptable to a wide
range of downstream tasks. I casually listened in. My favorite takeways were 

1. [Michael Bernstein](https://hci.stanford.edu/msb/)'s threshold effects. Specifically, as thresholds to entry are lowered,
 widespread adoption follows, frequently with unintended use cases. Perhaps in 5 years, everyone
 will have their own personal GPT-3 to manage their email, Twitter accounts and secret troll accounts.

2. [Dan Ho](https://law.stanford.edu/directory/daniel-e-ho/)'s foundation models for law. There is low-hanging fruit in making the law more accessible
 to everyone, but [foundation models don't always perform well at legal reasoning](https://dho.stanford.edu/wp-content/uploads/CaseHOLD.pdf).

3. [Slav Petrov](https://research.google/people/author38945/)'s talk on whether scale is all that matters.
 He made two points. First, a model is an architecture + training data + hyperparameters + loss function +
 distilled and/or offline cached inference because the model is too big to use in practice. Second,
 scaling won't solve key necessities when using these models e.g.  controllable policies (what are the right
 control affordances, justification of decisions, managing expectations) since none of these
 problems are scale-dependent.
