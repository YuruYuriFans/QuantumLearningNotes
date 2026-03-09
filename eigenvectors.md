## e

https://www.mathsisfun.com/algebra/eigenvalue.html 

If $Av = \lambda v$

Meaning:
Applying $A$ does not change the direction of  $v$, only its scale.

Eigenvectors reveal:
- The natural directions of a transformation
- How the transformation stretches or compresses space
- How to diagonalize a matrix

A general transformation rotates and stretches space.

Eigenvectors are the directions that are not rotated.

Eigenvalues tell you:

- Stretch (>1)
- Shrink (<1)
- Reflect (negative)
- Preserve length (=1)

Big idea in quantum mechanics:
- Operators represent measurements.
- Eigenvalues are the possible numbers you can get.
- Eigenvectors are the special states where the answer is definite (no randomness).

In Quantum Mechanics, Eigenvalues = possible measurement outcomes. Eigenvectors = states that give definite measurement results.
- $A\ket{v} = \lambda \ket{v}$ means If the system is in $\ket{v}$, measuring $A$ gives $\lambda$ with certainty.

Measurement probabilities reflect how aligned the state is with each eigenvector.
- Equal alignment = equal probability.
- Unequal alignment = unequal probability.

Scalar matrix: has all main diagonal entries the same, with zero everywhere else

Symmetric matrix matching entries either side of the main diagonal are equal, like this:

Lower triangular is when all entries above the main diagonal are zero

Upper triangular is when all entries below the main diagonal are zero

A singular matrix has no inverse because it has a determinant of 0. This means the system of equations either has no solution or infinitely many solutions.

Only square matrices have determinants. 

$$
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}^{-1}
=
\frac{1}{Det(A)}
\begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix}
$$

Gauss-Jordan method