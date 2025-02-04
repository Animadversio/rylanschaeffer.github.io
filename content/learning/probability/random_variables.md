# Random Variables

At the heart of probability is the notion of a _random variable_. Intuitively, a random variable
is a variable whose value depends on the outcome of some random process (e.g. a coin flip).

### Independence

Two random variables are __independent__ if their joint probability is equal to the product
of the marginal probabilities:

$$P(A, B) = P(A) P(B)$$

If $$A, B$$ are independent, then so are the following:

$$
\begin{align*}
P(A, B^c) &= P(A) - P(A, B)\\
&= P(A) - P(A) P(B)\\
&= P(A)(1 - P(B))\\
&= P(A) P(B^c)\\
P(A^c, B) &= P(B) - P(A, B)\\
&= P(B)(1 - P(A))\\
&= P(B)P(A^c)\\
P(A^c, B^c) &= P(A^c) - P(A^c, B^c)\\
&= P(A^c) - P(A^c)P(B)\\
&= P(A^c)(1 - P(B))\\
&= P(A^c)P(B^c)
\end{align*}
$$

# Properties

- Law of Total Expectation

$$\mathbb{E}_{p(X)}[X] = \mathbb{E}_{p(Y)}[\mathbb{E}_{p(X \lvert Y)}[X]] $$

Proof:

$$
\begin{align*}
\mathbb{E}_{p(X)}[X] &= \int_{X} X p(X) dX\\
&= \int_{X} X \int_{Y} p(X, Y) dX dY\\
&= \int_{Y} p(Y) \int_{X} X  p(X\lvert Y) dX dY\\
&= \int_{Y} p(Y) \mathbb{E}_{p(X \lvert Y)}[X]\\
&\mathbb{E}_{p(Y)}[\mathbb{E}_{p(X \lvert Y)}[X]]
\end{align*}
$$