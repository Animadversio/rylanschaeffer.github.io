# Bernoulli Process

The Bernoulli process is a tricky thing to explain because there isn't an exact
finite-dimensional distribution to use for analogy. Intuitively, the Bernoulli
process is a random measure consisting of a set of Bernoulli random variables at different locations
in some sample space $$\Omega$$. The number of random variables and their locations
are determined by a probability distribution or measure on $$\Omega$$. 

## Definitions

### Point Process Definition

A point process is a collection of points from some space. One definition of the Bernoulli
process is as a point process. Let $$P$$ be a probability distribution on a sample space $$\Omega$$
and $$n \in \mathbb{N}$$. If $$\omega_1, ..., \omega_N \sim_{i.i.d.} P$$, then a binomial process 
$$X \sim BeP(P)$$ is a random measure

$$X = \sum_{n=1}^N \delta_{\omega_n}$$

where $$\delta_{\omega_n}(A) = 1$$ if $$\omega_n \in A$$ and $$0$$ otherwise. The connection to the Binomial
distribution (and the source of the name) is that for all measurable sets $$A$$, the random variable

$$X(A) \sim Binomial(N, P(A))$$

### As a Levy Process Definition

Let $$B$$ be a measure on $$\Omega$$. A Bernoulli process with hazard measure $$B$$, denoted $$X \sim
BeP(B)$$ is a [Levy process](levy_process.md) with Levy measure

$$\mu(dp, d\omega) = \delta_1(dp) B(d\omega) $$

If $$B$$ is continuous, then $$X$$ is a Poisson process with intensity $$B$$:

$$X = \sum_{n=1}^N \delta_{\omega_n}$$

where $$N \sim Poisson(B(\Omega))$$ and $$\omega_i \sim_{i.i.d.} B/B(\Omega)$$. 
If $$B$$ is discrete, of the form $$B = \sum_i p_i \delta_{\omega_i}$$, then

$$X = \sum_{n=1}^N b_i \delta_{\omega_i}$$

where $$b_i \sim_{i.i.d.} Bernoulli(p_i)$$. For those familiar with the Poisson process,
the Bernoulli process is identical except it gives weight/measure 1 or 0 to each singleton.
The intuition is that $$X$$ is an object defined by a set of binary features it possesses,
while $$B$$ encodes the probability that $$X$$ possesses each feature.

## Properties

### Conjugacy with the Beta Process

See [beta process](beta_process.md) for details.

### Marginalizing Out Beta Process Prior

Analogous to how the [Beta-Bernoulli Compound Distribution](../probability/beta_binomial_distribution.md)
describes marginalizing out a Beta distribution prior over a Bernoulli / Binomial distribution's parameter,
we can similarly place a Beta Process prior on a Bernoulli process and marginalize it out. Doing so yields
a predictive distribution over the next Bernoulli process. That is, suppose $$B \sim BP(c, B_0)$$ is a 
[beta process](beta_process.md) and $$X_1, ..., X_N \sim_{i.i.d.} BeP(B)$$. Then the predictive distribution
for $$X_{N+1}$$ is given by

$$X_{N+1} | X_1, ..., X_N \sim BeP(\frac{c}{c+N} B_0 + \frac{1}{c+n} \sum_{n=1}^N X_n)$$

or equivalently

$$X_{N+1} | X_1, ..., X_N \sim BeP(\frac{c}{c+N} B_0 + \frac{1}{c+n} \sum_j m_{N, j} \delta_{\omega_j})$$

where $$m_{Nj}$$ is the integer number of $$\{X_n\}_{n=1}^N$$ with Dirac measure $$\delta_{\omega_j}$$. 