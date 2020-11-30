# Directed Graphical Models


A directed graphical model is one way of combining graphs with random variables. Specifically,
a directed graphical model $$G = (V, E)$$ is defined as the tuple of $$V$$, a set of vertices, each 
representing a random variable, and $$E \subseteq V \times V$$, a set of directed edges.
One particular $$G$$ defines a family of joint distributions over the random variables
by imposing conditional independencies in the edges. 
We denote the $$i$$th random variable $$X_i$$ and its set of parent nodes

$$\pi_i = \{j \in V \lvert (j, i) \in E \}$$

__Importantly, $$G$$ cannot have cycles__. If it does, there is no consistent way to assign
conditional probabilities.

## Extracting Conditional Independence from Directed Graphs

I use numbers to represent random variables rather than $$x_1, x_2, ...$$. I couldn't get
BayesNet to work with Markdown, so bear with the poor "pictures".  

- Ex 1: $$ 1 \rightarrow 2 \rightarrow 3$$ .Here, by the definition of conditional probabilities, we have
$$p(1,2,3) = p(1)p(2\lvert1)p(3\lvert1,2)$$. By the structure of the graph, we also have 
$$p(1,2,3) = p(1)p(2\lvert1)p(3\lvert2)$$. Setting the two equal shows $$p(3\lvert1,2) = p(3\lvert2)$$, meaning
3 is conditionally independent from 1 given 2.

- Ex 2: $$ 1 \leftarrow 2 \rightarrow 3$$. A similar analysis shows that $$1 \perp 3 \lvert 2$$.
Intuitively, if $$1$$ and $$3$$ are descendents of $$2$$, then knowing the parent $$2$$ renders the
 two descendents independent.

- Ex 3: $$ 1 \rightarrow 2 \leftarrow 3 $$. This one is trickier, but not by much. Suppose $$2$$ is the child of $$1$$ and $$3$$. Initially,
there's no relationship between the parents, so $$1 \perp 3$$, but if I observe that the child
has blue eyes and that $$1$$ does not, this tells me something about $$3$$. Consequently,
$$1 \perp 3$$ but $$1 \not\perp 3 \lvert 2$$.

__Directed Local Markov Property__:  A distribution $$p$$ over $$X^{\lvertV\lvert}$$ ($$V$$ is the set of 
variables) is said to satisfy the directed local
Markov property with respect to a DAG $$G = (V, E)$$ if $$\forall i \in V, x_i \perp 
x_{nd(i) \\ pi_i} \lvert \pi_i$$ where $$\pi_i$$ are the parents of $$i$$ and
 $$nd(i)$$ are the non-descendents of $$i$$. 

Directed Separation (or d-separation) describes rules for extracting
conditional independencies in a DAG. 

__Directed (d-) Separation__: For DAG $$G = (V, E)$$, we say the set of nodes $$A$$ is d-separated from the
 nodes $$B$$ with respect to nodes $$C$$ if every _path_ between nodes $$a\in A$$ and 
 $$b \in B$$ is _blocked_. A _path_ is a chain of edges that connect
two vertices, regardless of those edges' directionality. For determining whether a path is _blocked_,
there are really just two rules motivated by the earlier examples ($$1 \rightarrow 2 \rightarrow 3, 
1 \leftarrow 2 \rightarrow 3, 1 \rightarrow 2 \leftarrow 3$$):

1. Suppose arrows on the path don't meet head to head (e.g. $$1 \rightarrow 2 \rightarrow 3, 
1 \leftarrow 2 \rightarrow 3$$). Then the path is blocked if a node along the path is observed
and unblocked if not observed.

2. Suppose arrows on the path do meet head to head (e.g. $$1 \rightarrow 2 \leftarrow 3$$).
Then the path is unblocked if a node along the path is observed and blocked if not observed.
This also holds for descendents of node $$2$$.

__Directed Global Markov Property__: A distribution $$p$$ satisfies the 
global Markov property with respect to a DAG $$G=(V,E)$$ if $$\forall x_A, x_B, x_C \subset V,
\, x_A \perp x_B \lvert x_C \Leftrightarrow$$ $$A$$ and $$B$$ are d-separated by $$C$$.

It turns out that both the global Markov property and the local Markov property are equivalent,
and that both properties are equivalent to factorization.

__Theorem__: Let $$G$$ be a DAG. The following are equivalent:

1. $$p$$ factorizes according to $$G$$

2. $$p$$ satisfies the directed global Markov property with respect to $$G$$

3. $$p$$ satisfies the directed local Markov property with respect to $$G$$ 

The implication is that the following two lists are equivalent:

1. List all distributions that factorize according to the graph structure

2. List all distributions, then discard distributions which violate the conditional
independencies obtained by testing d-separation


Let $$I(G)$$ be the set of C.I. relations for a DAG $$G$$ corresponding to d-separation,
and let $$I(p)$$ be the set of C.I. relations for distribution $$p$$.

__Claim__: $$\forall G = (V,E), \exists p$$ such that $$p$$ factorizes according to $$G$$
 and $$I(G) = I(p)$$. Additionally, $$\exists p $$ for which no DAG exists satisfying
 $$I(G)= I(p)$$.
 
__Claim__: For two DAGs $$G_1, G_2$$, $$I(G_1) = I(G_2)$$ if and only if (1) both have 
the same skeleton (i.e. same edges, regardless of direction) and (2) same
v-structures (also called immoralities or common causes). 