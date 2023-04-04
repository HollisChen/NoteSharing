# Mathematics Notes

## Linear Algebra

### Associative law of matrix multiplication

There is a premise for matrix multiplication: when the number of columns of matrix $A$ is equal to the number of rows of matrix $B$, $A$ and $B$ can be multiplied. So for the column vectors $w$ and $x$, we will find that $w^Txx≠w^T(xx)$, this is not because the associative law of matrix multiplication, i.e., $(AB)C=A(BC)$, fails, but the premise of matrix multiplication is destroyed. As long as the matrix can be multiplied, the associative law must be satisfied. Here, because $x$ is a column vector, it cannot be multiplied by itself. This situation is caused by a row vector right multiplied by a column vector with the same length makes a scalar, or we can split a scalar into the multiplication of a row vector and of a same length column vector, but the resulting row and column vectors may not necessarily be able to be multiplied by the matrix before or after them (does not satisfy the above premise); if not, the associative law cannot be used. Sometimes. the associative law of matrix multiplication can be successfully used by adjusting the position of the scalar, like $w^T x$ in $w^Txx≠w^T(xx)$. We can put $w^T x$ after the second $x$ so that $w^T x x = x (w^T x)$, then $w^T x x = x (w^T x) = x (w^T x)^T = x (x^T w) = x x^T w$, where $x (w^T x) = x (w^T x)^T$ because $w^T x$ is a scalar and $x (x^T w) = x x^T w$ because $x$ and $x^T$ satisfy the premise of matrix multiplication then the associative law holds.

### Algebraic and geometric multiplicities

Consider a matrix that has an eigenvalue with larger algebraic multiplicity than geometric multiplicity. This means that there are fewer linearly independent eigenvectors associated with the eigenvalue than would be expected based on the degree of the polynomial.

Geometrically, this means that the eigenvectors corresponding to the eigenvalue are not "spread out" evenly across the space, but rather are clustered together in some way. When we say that the eigenvectors corresponding to an eigenvalue are "clustered together," what we mean is that they are not linearly independent, and therefore they do not span a full subspace of the matrix's vector space. In other words, there is some kind of degeneracy or exceptional behavior associated with the eigenvalue that is not captured by the standard eigenvectors.

For example, consider the matrix $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$. The characteristic polynomial of $A$ is $(1-λ)^2$, which has a repeated root at $λ = 1$. Thus, the algebraic multiplicity of the eigenvalue $λ = 1$ is $2$.

To find the eigenvectors of $A$ corresponding to $λ = 1$, we solve the equation $(A - λI)x = 0$, which shows that the eigenvectors of $A$ corresponding to $λ = 1$ are of the form $x = \begin{bmatrix} -t \\ t \end{bmatrix}$ for some scalar $t$. Thus, there is only one linearly independent eigenvector corresponding to $λ = 1$, which means that the geometric multiplicity of $λ = 1$ is $1$. Here, $A$ has at least one "same-direction axis" as the original coordinate system, which is a situation where the algebraic multiplicity larger than the geometric multiplicity will happen.

This means that the algebraic multiplicity of $λ = 1$ is larger than its geometric multiplicity, which implies that there must be a generalized eigenvector corresponding to $λ = 1$ that is not an eigenvector.

Generalized eigenvectors are different from standard eigenvectors. The concept "Jordan basis" from the matrix theory will be involved. These are not included here.

## Statistics

### Characteristic functions

The form of the characteristic function arises from the definition of the expected value of a complex-valued function of a random variable.

Let X be a random variable and let $g$ be a complex-valued function, then the expected value of $g(X)$ is given by:

$E[g(X)] = ∫g(x) f(x) dx$

where $f(x)$ is the probability density function of $X$.

Now, if we consider the function $g(X) = e^{itX}$, where t is a real number, we can compute its expected value as:

$E[e^{itX}] = ∫e^{itx} f(x) dx$

This expression is known as the characteristic function of $X$.

Using the definition of the characteristic function, we have:

$ϕ_{X+Y}(t) = E[e^{it(X+Y)}]$

$= E[e^{itX} · e^{itY}]$ (by the properties of exponents)

Since $X$ and $Y$ are independent, we can factorize the joint probability distribution:

$= E[e^{itX}] · E[e^{itY}]$

$= ϕ_X(t) · ϕ_Y(t)$

Thus, we have shown that the characteristic function of the sum of two independent random variables is simply the product of their individual characteristic functions.

### Law of total variance

In probability theory, **the law of total variance** or **variance decomposition formula** or **conditional variance formulas** or **law of iterated variances**, also known as **Eve's law**, states that if $X$ and $Y$ are random variables on the same probability space, and the variance of  $X$ is finite, then

$\operatorname{Var}_X[X]=\mathrm{E}_Y[\operatorname{Var}_X[X \mid Y]]+\operatorname{Var}_Y[\mathrm{E}_X[X \mid Y]]$

Proof:

The law of total variance can be proved using **the law of total expectation** ($\mathrm{E}_X[X]=\mathrm{E}_Y[\mathrm{E}_X[X \mid Y]]$).  First,

$\operatorname{Var}[X]=\mathrm{E}\left[X^{2}\right]-\mathrm{E}[X]^{2}$

from the definition of variance. Again, from the definition of variance, and applying the law of total expectation, we have

$\mathrm{E}\left[X^{2}\right]=\mathrm{E}_Y\left[\mathrm{E}_X\left[X^{2} \mid Y\right]\right]=\mathrm{E}_Y\left[\operatorname{Var}_X[X \mid Y]+[\mathrm{E}_X[X \mid Y]]^{2}\right]$

Now we rewrite the conditional second moment of  $X$  in terms of its variance and first moment, and apply the law of total expectation on the right hand side:

$\mathrm{E}\left[X^{2}\right]-\mathrm{E}[X]^{2}=\mathrm{E}_Y\left[\operatorname{Var}_X[X \mid Y]+[\mathrm{E}_X[X \mid Y]]^{2}\right]-[\mathrm{E}_Y[\mathrm{E}_X[X \mid Y]]]^{2}$

Since the expectation of a sum is the sum of expectations, the terms can now be regrouped:

$=(\mathrm{E}_Y[\operatorname{Var}_X[X \mid Y]])+\left(\mathrm{E}_Y\left[\mathrm{E}_X[X \mid Y]^{2}\right]-[\mathrm{E}_Y[\mathrm{E}_X[X \mid Y]]]^{2}\right)$

Finally, we recognize the terms in the second set of parentheses as the variance of the conditional expectation  $\mathrm{E}[X \mid Y]$:

$=\mathrm{E}_Y[\operatorname{Var}_X[X \mid Y]]+\operatorname{Var}_Y[\mathrm{E}_X[X \mid Y]]$

## Topology

### Manifold

(also refer to [Manifold-Wikipedia](https://en.wikipedia.org/wiki/Manifold))

In mathematics, a manifold is a topological space that looks locally like Euclidean space, meaning that it is locally homeomorphic to an open subset of Euclidean space. Informally, a manifold is a space that is "locally flat," but may have curvature or other interesting properties globally.

More specifically, a manifold is a topological space that is Hausdorff, second countable, and locally Euclidean. This means that each point in the manifold has a neighborhood that is homeomorphic to an open subset of Euclidean space of a fixed dimension, called the dimension of the manifold.

 One important class of manifolds are differentiable manifolds; their differentiable structure allows calculus to be done.

Manifolds are fundamental objects in many areas of mathematics and physics, including differential geometry, topology, algebraic geometry, and theoretical physics. They provide a natural framework for studying spaces with curvature and other geometric properties, and they have applications in fields such as computer graphics, robotics, and data analysis.

PS: 

The definition of a manifold as "a topological space that is Hausdorff, second countable, and locally Euclidean" can be broken down as follows:

- Hausdorff: This means that any two distinct points in the manifold can be separated by disjoint open sets. In other words, for any two points on the manifold, there exist open sets around each point that do not contain the other point.
- Second countable: This means that there exists a countable basis for the topology of the manifold. In other words, the manifold can be covered by a countable collection of open sets.
- Locally Euclidean: This means that each point in the manifold has a neighborhood that is homeomorphic to some open subset of Euclidean space. In other words, the manifold "looks like" Euclidean space near each of its points.

Taken together, these conditions ensure that a manifold is a well-behaved space that can be studied using tools from topology and geometry. The Hausdorff condition ensures that the manifold has some separation between its points, the second countable condition ensures that the topology is not too complicated, and the locally Euclidean condition ensures that the manifold has a well-defined geometry.

### Diffeomorphism

In mathematics, a diffeomorphism is an isomorphism of smooth manifolds. It is an invertible function that maps one differentiable manifold to another such that both the function and its inverse are differentiable.

"Diffeomorphic" is a term used in mathematics to describe a relationship between two objects that can be transformed into each other by a smooth, continuous and invertible transformation. More specifically, two objects are said to be diffeomorphic (or one object is diffeomorphic to another) if there exists a bijective function between them that is differentiable, with a differentiable inverse. This means that the two objects are essentially the same from a geometric standpoint, although they may look different.

For example, a sphere and a cube are not diffeomorphic, since there is no smooth and invertible transformation that can turn one into the other without distorting or tearing the surface. However, a sphere and a spheroid (an ellipsoid obtained by stretching or compressing a sphere in one or more directions) are diffeomorphic, since they can be smoothly and invertibly transformed into each other.

Since every diffeomorphism is a homeomorphism, given a pair of manifolds which are diffeomorphic to each other they are in particular homeomorphic to each other.



