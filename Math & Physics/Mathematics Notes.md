<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>


# Mathematics Notes

## Linear Algebra

### Associative law of matrix multiplication

There is a premise for matrix multiplication: when the number of columns of matrix $A$ is equal to the number of rows of matrix $B$, $A$ and $B$ can be multiplied. So for the column vectors $w$ and $x$, we will find that $w^Txx≠w^T(xx)$, this is not because the associative law of matrix multiplication ($(AB)C=A(BC)$) fails, but the premise of matrix multiplication is destroyed. As long as the matrix can be multiplied, the associative law must be satisfied. Here, because $x$ is a column vector, it cannot be multiplied by itself. This situation is caused by a row vector right multiplied by a column vector with the same length makes a scalar, or we can split a scalar into the multiplication of a row vector and of a same length column vector, but the resulting row and column vectors may not necessarily be able to be multiplied by the matrix before or after them (does not satisfy the above premise); if not, the associative law cannot be used. Sometimes. the associative law of matrix multiplication can be successfully used by adjusting the position of the scalar, like $w^T x$ in $w^Txx≠w^T(xx)$. We can put $w^T x$ after the second $x$ so that $w^T x x = x (w^T x)$, then $w^T x x = x (w^T x) = x (w^T x)^T = x (x^T w) = x x^T w$, where $x (w^T x) = x (w^T x)^T$ because $w^T x$ is a scalar and $x (x^T w) = x x^T w$ because $x$ and $x^T$ satisfy the premise of matrix multiplication then the associative law holds.

### Algebraic and geometric multiplicities

Consider a matrix that has an eigenvalue with larger algebraic multiplicity than geometric multiplicity. This means that there are fewer linearly independent eigenvectors associated with the eigenvalue than would be expected based on the degree of the polynomial.

Geometrically, this means that the eigenvectors corresponding to the eigenvalue are not "spread out" evenly across the space, but rather are clustered together in some way. When we say that the eigenvectors corresponding to an eigenvalue are "clustered together," what we mean is that they are not linearly independent, and therefore they do not span a full subspace of the matrix's vector space. In other words, there is some kind of degeneracy or exceptional behavior associated with the eigenvalue that is not captured by the standard eigenvectors.

For example, consider the matrix $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$. The characteristic polynomial of $A$ is $(1-λ)^2$, which has a repeated root at $λ = 1$. Thus, the algebraic multiplicity of the eigenvalue $λ = 1$ is $2$.

To find the eigenvectors of $A$ corresponding to $λ = 1$, we solve the equation $(A - λI)x = 0$, which shows that the eigenvectors of $A$ corresponding to $λ = 1$ are of the form $x = \begin{bmatrix} -t \\ t \end{bmatrix}$ for some scalar $t$. Thus, there is only one linearly independent eigenvector corresponding to $λ = 1$, which means that the geometric multiplicity of $λ = 1$ is $1$. Here, $A$ has at least one "same-direction axis" as the original coordinate system, which is a situation where the algebraic multiplicity larger than the geometric multiplicity will happen.

This means that the algebraic multiplicity of $λ = 1$ is larger than its geometric multiplicity, which implies that there must be a generalized eigenvector corresponding to $λ = 1$ that is not an eigenvector.

Generalized eigenvectors are different from standard eigenvectors. The concept "Jordan basis" from the matrix theory will be involved. These are not included here.



