# Norm

## Definition: Norm

Let $$X$$ be a space. A norm is a function $$f: X \rightarrow \mathbb{R}$$ satisfying the 
three following properties for $$x_1, x_2 \in X$$ and for $$\alpha \in \mathbb{R}$$:

1. Positive-definiteness: $$f(x_1) \geq 0$$ and $$f(x_1) = 0 \Leftrightarrow x_1 = 0$$
   
2. Absolute homogeneity: $$f(\alpha x_1) = |\alpha| f(x_1)$$

3. Triangle inequality: $$f(x_1 + x_2) \leq f(x_2) + f(x_2)$$

## Normed Vector Space

A __normed vector space__ is a vector space equipped with a norm. Frequently, if we
are dealing with an [inner product space](inner_product.md#inner-product-space)
(i.e. a vector space equipped with an inner product), we can define a norm as the
square root of the inner product:

$$\lvert \lvert x \lvert \lvert_2 := \sqrt{ \langle x, x \rangle } $$
