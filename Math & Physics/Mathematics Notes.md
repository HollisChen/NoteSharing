# Mathematics Notes

[TOC]

## Linear Algebra

### Associative law of matrix multiplication

There is **a premise for matrix multiplication**: when the number of columns of matrix $A$ is equal to the number of rows of matrix $B$, $A$ and $B$ can be multiplied. So for the column vectors $w$ and $x$, we will find that $w^Txx≠w^T(xx)$, this is not because the associative law of matrix multiplication, i.e., $(AB)C=A(BC)$, fails, but the premise of matrix multiplication is destroyed. As long as the matrix can be multiplied, the associative law must be satisfied. Here, because $x$ is a column vector, it cannot be multiplied by itself. This situation is caused by a row vector right multiplied by a column vector with the same length makes a scalar, or we can split a scalar into the multiplication of a row vector and of a same length column vector, but the resulting row and column vectors may not necessarily be able to be multiplied by the matrix before or after them (does not satisfy the above premise); if not, the associative law cannot be used. Sometimes. the associative law of matrix multiplication can be successfully used by adjusting the position of the scalar, like $w^T x$ in $w^Txx≠w^T(xx)$. We can put $w^T x$ after the second $x$ so that $w^T x x = x (w^T x)$, then $w^T x x = x (w^T x) = x (w^T x)^T = x (x^T w) = x x^T w$, where $x (w^T x) = x (w^T x)^T$ because $w^T x$ is a scalar and $x (x^T w) = x x^T w$ because $x$ and $x^T$ satisfy the premise of matrix multiplication then the associative law holds.

### Algebraic and geometric multiplicities

Consider a matrix that has an eigenvalue with larger algebraic multiplicity than geometric multiplicity. This means that there are fewer linearly independent eigenvectors associated with the eigenvalue than would be expected based on the degree of the polynomial.

Geometrically, this means that the eigenvectors corresponding to the eigenvalue are not "spread out" evenly across the space, but rather are clustered together in some way. When we say that the eigenvectors corresponding to an eigenvalue are "clustered together," what we mean is that they are not linearly independent, and therefore they do not span a full subspace of the matrix's vector space. In other words, there is some kind of degeneracy or exceptional behavior associated with the eigenvalue that is not captured by the standard eigenvectors.

For example, consider the matrix $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$. The characteristic polynomial of $A$ is $(1-λ)^2$, which has a repeated root at $λ = 1$. Thus, the algebraic multiplicity of the eigenvalue $λ = 1$ is $2$.

To find the eigenvectors of $A$ corresponding to $λ = 1$, we solve the equation $(A - λI)x = 0$, which shows that the eigenvectors of $A$ corresponding to $λ = 1$ are of the form $x = \begin{bmatrix} -t \\ t \end{bmatrix}$ for some scalar $t$. Thus, there is only one linearly independent eigenvector corresponding to $λ = 1$, which means that the geometric multiplicity of $λ = 1$ is $1$. Here, $A$ has at least one "same-direction axis" as the original coordinate system, which is a situation where the algebraic multiplicity larger than the geometric multiplicity will happen.

This means that the algebraic multiplicity of $λ = 1$ is larger than its geometric multiplicity, which implies that there must be a generalized eigenvector corresponding to $λ = 1$ that is not an eigenvector.

Generalized eigenvectors are different from standard eigenvectors. The concept "Jordan basis" from the matrix theory will be involved. These are not included here.

## Statistics

### Logit function and expit function

The logit function is a mathematical function that maps probabilities (values between 0 and 1) to real numbers (values between negative infinity and positive infinity). It is defined as follows:
$$
\mathrm{logit}(p)=\mathrm{log}\left(\frac{p}{1-p}\right)
$$
The name "logit" is a portmanteau of "logistic unit".  

Note: In 1944, Joseph Berkson used log of odds and called this function logit, abbreviation for "logistic unit" following the analogy for probit (see [Wikipedia](https://en.wikipedia.org/wiki/Logit#:~:text=.-,History,-%5Bedit%5D)). Today, the logit function is commonly used in statistics and machine learning for modeling binary outcomes, such as whether a customer will buy a product or not.

The inverse of the logit function is the expit function (also known as the logistic sigmoid function), which can be written as: 
$$
\mathrm{expit}(x) = \frac{1}{1+e^{-x}}=\frac{e^x}{e^x+1}
$$
The expit function is a sigmoid function that maps any real-valued number to the range of 0 to 1. It is commonly used in machine learning and statistics for tasks such as binary classification. The name "expit" comes from the combination of "exponential" and "logit".

(quantile function and logistic function?)

### Logistic regression

Logistic regression is a statistical method for analyzing a dataset in which there are one or more independent variables (predictors) that determine the dependent variable (outcome), which is a binary variable, taking the values 0 or 1.  It is a type of generalized linear model (GLM) that is used for predicting the probability of an outcome.

Let $\eta$ be the output value of the logit function, where $O =\frac{p}{1-p}$ is called the odds.
$$
\eta = \mathrm{logit}(p)=\mathrm{log}\left(\frac{p}{1-p}\right)
$$
You can go backwards from the logit function to the probability with the expit function, as shown in [Logit function and expit function](#Logit-function-and-expit-function).
$$
p=\frac{e^\eta}{e^\eta+1}= \frac{1}{1+e^{-\eta}}
$$
We model the log of the odds as linear. This is called **logistic regression**.
$$
\eta=\mathrm{logit}\left\{P(Y=1\mid X)\right\}=\beta_{0}+\beta_{1}X
$$
The nice part about this model is that $e^{\beta_1 X}$ has the nice interpretation of the odds ratio associated with a one unit change in $X$. Actually, we can have $\boldsymbol{X}=[X_1, X_2, \dots, X_N]$, then 
$$
\begin{array}{l}
\eta&=\mathrm{logit}\left\{P(Y=1\mid \boldsymbol{X})\right\}\\
&=\mathrm{logit}\left\{P(Y=1\mid X_1,X_2,\dots,X_N)\right\}\\
&=\beta_{0}+\beta_{1}X_1+\beta_{2}X_2+\dots+\beta_{N}X_N
\end{array}
$$
where we can see that  $P(Y = 1 | \boldsymbol{X})$ is the probability of the binary outcome being $1$ given the predictor variables $\boldsymbol{X}$, and $\eta$ is a linear combination of the predictor variables.

In the following, we consider the simple form $\eta=\mathrm{logit}\left\{P(Y=1\mid X)\right\}=\beta_{0}+\beta_{1}X$.

Consider a dataset $y_1,y_2,\dots,y_n$ and $x_1,x_2,\dots,x_n$. 

We need a function of the probabilities to optimize the problem to obtain the optimal $\boldsymbol{\beta}=[\beta_{0},\beta_{1}]$. It is the **cross entropy**.
$$
\begin{array}{l}
&\mathrm{Cross\,\,Entropy}\\
&=-\sum_{i=1}^{n}\left[y_{i}\log\{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})\}+(1-y_{i})\log\{P(Y=1-y_{i}\mid X=x_{i},\boldsymbol{\beta})\}\right] \\
&=-\sum_{i=1}^{n}\left[y_{i}\log\{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})\}+(1-y_{i})\log\{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})\}\right]\\
&=-\sum_{i=1}^{n}\left[y_{i}\log\left\{\frac{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})}{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})}\right\}+\log\{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})\}\right]\\
&= -\sum_{i=1}^{n}\left[y_i\eta_i + \log{\dfrac{1}{1+e^{\eta_i}}}\right]\\
\end{array}
$$
where $y_i=0$ or $1$. Note when $y_i=1$, $\log\left\{\frac{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})}{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})}\right\}=\eta_i$, then $y_i\log\left\{\frac{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})}{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})}\right\}=y_i\eta_i$; when $y_i=0$,  $y_i\log\left\{\frac{P(Y=y_i\mid X=x_{i},\boldsymbol{\beta})}{1-P(Y=y_{i}\mid X=x_{i},\boldsymbol{\beta})}\right\}=y_i\eta_i=0$

We will show that the above result is same as the one resulting from the maximum likelihood estimation (MLE). 

First, we have
$$
P(Y=y_i|X=x_{i})=p_{i}^{y_i}(1-p_{i})^{1-y_i}\;\;\;y_i\in\{0,1\}
$$

where $p_{i}=P(Y=1|X=x_{i})$ and $1-p_{i}=P(Y=0|X=x_{i})$.

Then, the joint probability of the data is
$$
\begin{align*}
&\prod_{i=1}^n p_{i}^{y_i}(1-p_{i})^{1-y_i} \\
=&\prod_{i=1}^n \left(\frac{e^{\beta_{0}+\beta_{1}x_{i}}}{1+e^{\beta_{0}+\beta_{1}x_{i}}}\right)^{y_{i}}\left(\frac{1}{1+e^{\beta_{0}+\beta_{1}x_{i}}}\right)^{1-y_{i}} \\
=&\exp\left\{\beta_{0}\sum_{i=1}^{n}y_{i}+\beta_{1}\sum_{i=1}^{n}y_{i}x_{i}\right\}\times\prod_{i=1}^{n}\left({\frac{1}{1+e^{\beta_{0}+\beta_{1}x_{i}}}}\right)
\end{align*}
$$

where we take the joint probability and plug in the actual $y_i$ and $x_i$ that we observed and view it as a function of $\beta_0$ and $\beta_1$, it’s called a **likelihood**. A likelihood is the joint probability with the observed data plugged in and maximum likelihood finds the values of the parameters that makes the data that we observed most likely.

Generally, since sums are more convenient than products, we take the natural logarithm. Then, this works out to be:
$$
\beta_{0}\sum_{i=1}^{n}y_{i}+\beta_{1}\sum_{i=1}^{n}y_{i}x_{i}-\sum_{i=1}^{n}\log\left(1+e^{\beta_{0}+\beta_{1}x_{i}}\right)
$$
This is the function that we maximizes over $\beta_0$ and $\beta_1$ to obtain the estimates. It is equivalent to (same as) minimizing the cross entropy.

**Linear regression is also MLE**: Linear regression can be viewed as an MLE problem when we assume the error term follows a normal distribution with a mean of zero and constant variance.

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

(What if $X$ and $Y$ are not independent? There should be a generalized formula including covariances.)

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

Finally, we recognize the terms in the second set of parentheses as the variance of the conditional expectation  $\mathrm{E}_X[X \mid Y]$:

$=\mathrm{E}_Y[\operatorname{Var}_X[X \mid Y]]+\operatorname{Var}_Y[\mathrm{E}_X[X \mid Y]]$

### Random field

A random field is a mathematical concept used in probability theory and statistics to describe a collection of random variables indexed by a spatial or temporal domain. Unlike a sequence of random variables, where the index set is typically the set of natural numbers, a random field has an index set that is a more complex mathematical space, such as a region of space or time.

In the case of a spatial random field, the index set may be a subset of Euclidean space, such as a two-dimensional plane, and the random variables may represent physical quantities such as temperature or pressure at different locations in the domain. In the case of a temporal random field, the index set may be a subset of the real line, and the random variables may represent values of a time-varying process at different points in time.

Random fields are useful for modeling and analyzing complex data that have a spatial or temporal structure, such as climate data, geostatistical data, and image data. They are also used in machine learning and artificial intelligence applications such as image and signal processing, where the input data is often structured as a random field.

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

## Harmonic Analysis

### Fourier series

First, let us introduce what is the trigonometric series.

Trigonometric series is a more general term, representing an infinite series of sine and cosine functions combined with coefficients. The general form of a trigonometric series is:
$$
f(t) = a_0 + \sum\limits_{n=1}^{∞} \left[a_n  \cos(nωt) + b_n \sin(nωt)\right]
$$
The so-called Fourier series (**the trigonometric form** of the Fourier series) has the same form as the trigonometric series. The distinction between the Fourier series and trigonometric series lies in the context and the method used to determine the coefficients. In a general trigonometric series, the coefficients $a_0$, $a_n$, and $b_n$ can be arbitrary, while in a Fourier series, the coefficients are determined by specific formulas to represent a periodic function or approximate a non-periodic function over a specific interval.

How are the coefficient determined in the Fourier series?
$$
a_0 = (1 / T) ∫_{-T/2}^{T/2} f(t) dt\\
a_n = (2 / T) ∫_{-T/2}^{T/2} f(t) \cos(nωt) dt\\
b_n = (2 / T) ∫_{-T/2}^{T/2} f(t) \sin(nωt) dt\\
$$
The Fourier series has another form: **the exponential form**. The exponential form of the Fourier series is:
$$
f(t) = \sum\limits_{n=-∞}^{∞} c_n e^{jnωt}
$$
where the coefficients can be determined by:
$$
c_n = (1 / T) ∫_{-T/2}^{T/2} f(t)  e^{-j nωt} dt
$$
Note: for the inner product of complex numbers or functions, their inner product (also called dot product) is defined as the product of one number (function) and the complex conjugate of the other number (function), like $⟨z₁, z₂⟩ = z₁ · \mathrm{conj}(z₂)$ and $⟨f, g⟩ = ∫ f(t) · \mathrm{conj}(g(t)) \,\mathrm{d}t$. That's why we use $e^{-j nωt}$ but not $e^{j nωt}$ in the above equation.

Note: for the trigonometric form, we only have single-sided spectrum -- only positive frequencies are present. The coefficients $a_n$ and $b_n$ correspond to the amplitudes of the cosine and sine terms at each frequency, respectively (**sine-cosine form**). We can also represent the cosine and sine terms at a same frequency only using a sine or cosine term in the form of $A \cos(nωt - \phi)$ or $A \sin(nωt - \phi)$ (**amplitude-phase form**), like $\sin(nωt) + \cos(nωt) = \sqrt 2 \cos(nωt - \pi/4)$, then we can use the two diagrams -- amplitude and phase diagrams to represent the results in frequency domain. But for the exponential form of the Fourier series, the two pieces of  information for a frequency $ω$ (the amplitudes of the cosine and sine terms at a frequency, or the amplitude and phase for the sine or cosine term) are represented by the frequency $ω$ and $-ω$ -- that is why the exponential form of the Fourier series has a double-sided spectrum but no phase diagram.

**Dirichlet conditions**:

(see [this video](https://www.bilibili.com/video/BV1Uv4y127cR/?spm_id_from=333.788&vd_source=967f24091b4dff8d77184edf51434a3c) for interpretation )

Dirichlet's conditions, also known as the Dirichlet conditions, provide a set of criteria that must be satisfied by a function for its Fourier series to converge. The conditions are as follows:

1. The function $f(t)$ must be periodic, with period $T$.

2. The function $f(t)$ must be absolutely integrable over one period, meaning that the integral of the absolute value of $f(t)$ is finite:

   $∫_{-T/2}^{T/2} |f(t)| dt < ∞$

3. The function $f(t)$ must have a finite number of discontinuities within one period. Moreover, the discontinuities must be finite in magnitude (i.e., no infinite jumps).

4. The function $f(t)$ must have a finite number of maxima and minima within one period.

If a function satisfies these conditions, its Fourier series will converge pointwise to the function $f(t)$ at points of continuity and to the average of the left and right limits at points of discontinuity.

It is worth noting that these conditions are sufficient but not necessary for the convergence of the Fourier series. There are functions that do not strictly satisfy the Dirichlet conditions but still have convergent Fourier series. The Dirichlet conditions provide a useful starting point for determining whether a Fourier series converges, but they do not cover all possible cases.

Note: the necessary and sufficient conditions for the convergence of a Fourier series have not been completely established.

### Fourier transform

The Fourier transform is the generalization of the Fourier series representation of a periodic function to a non-periodic function using the limit as the period approaches infinity. 

The Fourier transform $F(ξ)=F(\frac{nω}{2 \pi})=\lim\limits_{ω \to 0} \frac{2 \pi F'(nω)}{ω}=\lim\limits_{T \to \infty}F'(nω)T=\lim\limits_{freq \to 0} \frac{F'(nω)}{freq}$, where $freq=\frac{ω}{2 \pi}$ is the frequency (not the angular frequency), $2 \pi ξ= n ω$ is the frequency with unit Hertz (Hz) and $F'(nω)=(1 / T) ∫_{-T/2}^{T/2} f(t)  e^{-j nωt} dt$ is the equation calculating the coefficients in the exponential form of the Fourier series (see [Fourier series](#Fourier-series)). 

Note that the value (amplitude, y-axis) of the Fourier transform $F(ξ)$ represents the contribution of each frequency component to the original signal and is expressed in terms of frequency (Hz) but not angular frequency (rad/s) even if you use $ω$ as the input (x-axis), i.e., $F_1(ω) = F(\frac{ω}{2 \pi})$ ($F_1$ is the **angular frequency** form and $F$ is the **ordinary frequency** form -- the only change is the unit of input). 

That is, the units of the amplitude (y-axis) is always considered to be "per hertz" both in the angular frequency form and the ordinary frequency form. If the input signal $f$ has units of volts, then the amplitude of the Fourier transform is expressed in volts per hertz (V/Hz).

The Fourier transform equation is
$$
F(ξ) = ∫_{-∞}^{∞} f(t) e^{-j2πξt} dt
$$
The inverse Fourier transform equation is (like using Fourier series to represent a function, so the following equation intuitively holds, but I still give the derivation from the Fourier transform equation to the inverse Fourier transform equation in the later text which is actually not necessary)
$$
f(t) = ∫_{-∞}^{∞} F(ξ) e^{j2πξt} dξ
$$
$F(ξ)$ gives the "frequency-domain representation" or "spectrum" of a time-domain signal in signal processing (but in image processing, the Fourier transform is applied to spatial-domain images and the result represents the amplitude of each spatial frequency in the image). 

The angular frequency form ($ω = 2 π ξ$, $dω =2 π dξ$) is 
$$
F_1(ω) = ∫_{-∞}^{∞} f(t) e^{-jωt} dt \\
f(t) = \frac{1}{2π} ∫_{-∞}^{∞} F_1(ω) e^{jωt} dω
$$
See [wikipedia](https://en.wikipedia.org/wiki/Fourier_transform#:~:text=Variations%20of%20all%20three%20conventions) for details.

**How to derive the inverse Fourier transform equation?**

To derive the inverse Fourier transform equation, we start with the Fourier transform equation, which relates a function $f(t)$ to its frequency-domain representation $F(ξ)$:

$F(ξ) = ∫_{-∞}^{∞} f(t) e^{-j2πξt} dt$

Now we want to prove (use $u$ to replace $t$ inside the parentheses to distinguish it from the one outside):

$f(t) = ∫_{-∞}^{∞} F(ξ) e^{j2πξt} dξ= ∫_{-∞}^{∞} \left(∫_{-∞}^{∞} f(u) e^{-j2πξu} du \right) e^{j2πξt} dξ$

Change the order of integration:

$∫_{-∞}^{∞} \left(∫_{-∞}^{∞} f(u) e^{-j2πξu} du \right) e^{j2πξt} dξ = ∫_{-∞}^{∞} \left(∫_{-∞}^{∞}  e^{j2πξ(t-u)} dξ \right) f(u) du$

We can use the orthogonality property of complex exponentials (the inner product of two complex exponential functions with different frequencies is zero, while the inner product of a complex exponential function with itself is non-zero):

$∫_{-∞}^{∞} e^{j2πξ(t-u)} dξ = δ(t - u)$ 

Why the above holds? We cannot use the inverse Fourier transform to prove it here. Think that equivalently we only need to prove $∫_{-∞}^{∞} 1 dx = δ(t)$ where you can think of $δ(t)$ as a rectangular pulse or square wave with a width of 'x' and a height of '1/x' centered around the origin with x approaching zero, meaning $\infty=\frac 1 x=δ(t)$ and $x \frac 1 x=1$ so that $∫_{-∞}^{∞} 1 dx = \infty · 1 = \frac 1 x·1=\frac 1 x=δ(t)$. (maybe we need a better interpretation for this)

Using this property, we get:

$∫_{-∞}^{∞} \left(∫_{-∞}^{∞}  e^{j2πξ(t-u)} dξ \right) f(u) du =∫_{-∞}^{∞} δ(t-u) f(u) du=f(t)$

Q.E.D.

### Autocorrelation

Autocorrelation of deterministic signals: In signal processing, the autocorrelation function (ACF) is often used without the normalization, that is, without subtracting the mean and dividing by the variance. When the autocorrelation function is normalized by mean and variance, it is sometimes referred to as the autocorrelation coefficient or autocovariance function.

Autocorrelation of continuous-time signal: given a signal $f(t)$, the continuous autocorrelation $R_{ff}(\tau)$ is most often defined as the continuous cross-correlation integral of $f(t)$ with itself, at lag $\tau$.
$$
R_{ff}(\tau) = \int_{-\infty}^{\infty}f(t+\tau)\overline{f(t)}\,\mathrm{d}t=\int_{-\infty}^{\infty}f(t)\overline{f(t-\tau)}\,\mathrm{d}t = \left.(f(t) * \overline{f(-t)})\right|_{t=\tau}
$$
where $\overline{f(t)}$ represents the complex conjugate of $f(t)$ and $*$ represents the convolution operation. Note that the parameter $t$ in the integral is a dummy variable and is only necessary to calculate the integral. It has no specific meaning.

Auto-correlation of discrete-time signal: the discrete autocorrelation $R$ at lag $l$ for a discrete-time signal $y(n)$ is
$$
R_{yy}(l) = \sum_{n \in Z} y(n)\overline{y(n-l)}
$$
The above definitions work for signals that are square integrable, or square summable, that is, of finite energy. Signals that "last forever" are treated instead as random processes, in which case different definitions are needed, based on expected values. For wide-sense-stationary random processes (see the following text), the autocorrelations are defined as
$$
R_{ff}(\tau) = \mathrm{E}\left[f(t)\overline{f(t-\tau)}\right]\\
R_{yy}(l) = \mathrm{E}\left[y(n)\overline{y(n-l)}\right]
$$

For white noise, the autocorrelation is 
$$
R_{nn}(\tau)=\mathrm{E}\left.[n(t)n(t-\tau)\right.]=\delta(\tau)
$$
For cross-correlation, it is similar, just replacing the second $f$ function in above formulas with another function $g$.

**Wide-sense stationary (WSS) process**:

A wide-sense stationary (WSS) process is a type of random process (or stochastic process) with specific statistical properties that remain constant over time. In a WSS process, the first and second-order moments (mean and autocorrelation) do not depend on the absolute time but only on the time difference.

A random process $X(t)$ is considered wide-sense stationary if it satisfies the following two conditions:

1. Constant mean: The mean or expected value of the process remains constant over time. Mathematically, this is expressed as:

   $E[X(t)] = \mu$, for all $t$

   where $E[X(t)]$ denotes the expected value of the process at time $t$ and $\mu$ is a constant.

2. Time-invariant autocorrelation: The autocorrelation function of the process depends only on the time difference ($τ = t_2 - t_1$) and not on the absolute time values. Mathematically, this is expressed as:

   $R_X(t_1, t_2) = E[X(t_1)\overline{X(t_2)}] = R_X(τ)$

   where $R_X(t_1, t_2)$ is the autocorrelation function, $\overline{X(t_2)}$ denotes the complex conjugate of $X(t_2)$, and $τ = t_2 - t_1$.

A wide-sense stationary process is a simpler form of stationarity compared to strict-sense stationarity, which requires all the statistical properties of the process to be time-invariant. WSS processes are often used in the analysis of random signals, as their time-invariant autocorrelation function and constant mean make them more tractable for mathematical analysis and practical applications, such as filtering and system identification.

### Power spectrum and power spectral density

Refer to this [video](https://www.bilibili.com/video/BV1E44y1D7mw/?spm_id_from=333.880&vd_source=967f24091b4dff8d77184edf51434a3c)'s first several minutes.

Note: understanding the orthogonality property of complex exponentials is essential when working with the power spectrum and power spectral density (PSD). The orthogonality property states that the inner product of two complex exponential functions with different frequencies is zero, while the inner product of a complex exponential function with itself is non-zero. Mathematically, this can be expressed as:

$∫_{-∞}^{∞} e^{j2πνt} · e^{-j2πν' t} dt = δ(ν - ν')$

Where $ν$ and $ν'$ are the frequencies of the complex exponentials, and $δ(ν - ν')$ is the Dirac delta function.

**Wiener-Khinchin theorem**:

The theorem establishes a relationship between the autocorrelation function of a wide-sense stationary random process (see [Autocorrelation](#Autocorrelation)) and its power spectral density.

The Wiener-Khinchin theorem states that the autocorrelation function $R(τ)$ and the power spectral density $S(ω)$ of a wide-sense stationary random process are a Fourier transform pair. In other words, the power spectral density is the Fourier transform of the autocorrelation function, and the autocorrelation function is the inverse Fourier transform of the power spectral density.

Mathematically, the Wiener-Khinchin theorem can be expressed as:

$S(ω) = ∫_{-∞}^{∞} R(τ) e^{-jωτ} dτ$

and

$R(τ) = (1/2π) ∫_{-∞}^{∞} S(ω) e^{jωτ} dω$

It's important to note that $R(0)$ has a specific meaning in the context of PSD. $R(0)$ represents the total power (or energy, for energy signals) of the signal, which is equal to the integral of the PSD over all frequencies:

$R(0) = ∫_{-∞}^{∞} S(ω) dω$

However, this does not mean that $τ = 0$ is required when calculating the PSD from the autocorrelation function. But for a white noise, $R(\tau)=\mathrm{E}\left.[n(t)n(t-\tau)\right.]=\delta(\tau)$, that is, $R(\tau)=0$ if $\tau \neq 0$.

(What is the definition of the PSD? It should not be related to Winer-Khinchin theorem. Then how to understand the  Winer-Khinchin theorem. from the perspective of the definition.)

### Parseval's theorem