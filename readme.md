# Quantum Computation and Quantum Information  (Michael A. Nielsen, Isaac L. Chuang) notes

## 0 Nomenclature and notation
https://www.mathsisfun.com/physics/bra-ket-notation.html 

> Bra-Ket Notation is sometimes called Dirac Notation.  

Ket:  column vector

$$
|0\rangle =
\begin{pmatrix}
1 \\
0
\end{pmatrix},
\quad
|1\rangle =
\begin{pmatrix}
0 \\
1
\end{pmatrix}
$$

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

> By convention, $\psi \equiv \ket{\psi}$, required for understanding but not recommended in formal writing.

Bra: row vector, Hermitian conjugate (complex conjugate transpose) (aka adjoint) of a Ket. 

$$\bra{\psi} = \begin{pmatrix}\alpha^* & \beta^*\end{pmatrix} = (\psi^*)^T = \psi^\dagger $$
Bra-ket: inner product

$$
\langle \psi | A | \psi \rangle = \psi^\dagger A \psi
$$ 

positive operator

positive definite operator

support: the vector space orthogonal to its kernel. 
- For a Hermitian operator, this means the vector space spanned by eigenvectors of the operator with non-zero eigenvalues.

| Property               | Unitary              | Involutory               |
| ---------------------- | -------------------- | ------------------------ |
| Definition             | $(U^\dagger U = I)$    | $(A^2 = I)$                |
| Inverse                | $(U^{-1} = U^\dagger)$ | $(A^{-1} = A)$            |
| Physical meaning       | Rotation / symmetry  | Reflection-type symmetry |
| Always preserves norm? | Yes                  | Not necessarily          |

> Unitary = preserves length.
> Involutory = self-inverse.

U: unitary operator or matrix

H is usually used to denote:

- Hadamard gate

- Hamiltonian for a quantum system

Pauli Sigma matrices

$$
I = \sigma_0 = 
\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}
\quad
\sigma_x = \sigma_1 = 
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
\quad
\sigma_y = \sigma_2 = 
\begin{pmatrix}
0 & -i \\
i & 0
\end{pmatrix}
\quad
\sigma_z = \sigma_3 =
\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}
$$

Key properties of Pauli matrices:
- determinant = -1, trace = 0
- Hermitian: $\sigma_i^\dagger = \sigma_i$
- Unitary: $\sigma_i^2 = I$
- Eigenvalues: $\pm 1$
- Not commuting: $\sigma_x \sigma_y = i \sigma_z$
- Generate rotations, (Lie algebra of SU(2)), to be added

Applications of each
- $\sigma_x$ looks symmetrical to the identity matrix, so it is Bit-flipping, more precisely
    - $\sigma_1 \ket{0} = \ket{1}, \quad \sigma_1 \ket{1} = \ket{0}$
        - $\therefore \ket{0}$ and $\ket{1}$ are ***not*** eigenvectors of $\sigma_x$
- $\sigma_z$ is the phase flip operator, it leaves $\ket{0}$ unchanged but flips $\ket{1}$, more precisely
    - $\sigma_z \ket{0} = \ket{0}, \quad \sigma_z \ket{1} = - \ket{1}$
        - $\therefore \ket{0}$ and $\ket{1}$ are eigenvectors of $\sigma_z$ with eigenvalues 1 and -1, respectively.
> For information theorists, always log base two unless otherwise noted.

relative entropy of a positive operator A with respect to a positive operator B: 

$$S(A||B) \equiv tr(A \log A) - tr (A \log B)$$

> Classical entropy is a sum of probabilities, but in quantum mechanics, a state is a density matrix $\rho$, not a probability vector. every density matrix can be diagonalized: $\lambda_i \ket{i}\bra{i}$. where $\lambda_i$ are eigenvalues which behave like probabilities.(https://quantum.cloud.ibm.com/learning/en/courses/general-formulation-of-quantum-information/density-matrices/density-matrix-basics)
> Quantum entropy is defined as 
> $$S(\rho) = - tr(\rho \log \rho)$$
> Exactly the classical Shannon entropy — but applied to eigenvalues.

where $tr$ is the trace that adds up the diagonals: $tr(A) = \sum_{i} A_{ii}$.
- It measures how distinguishable two quantum states are.
- Trace has a key cyclic property, $tr(AB) = tr(BA)$.
- The trace of a matrix equals the sum of its eigenvalues:


$\oplus$ denotes XOR or modulo two addition.
- The CNOT gate acts like $\ket{a} \ket{b} \implies \ket{a} \ket{a \oplus b}$. So the second qubit flips only if the first qubit is 1.

## 1.1

### 1.1.1 

no-cloning theorem: clone an unknown quantum state turns out not to be possible in general in
quantum mechanics. (1980s)

complete control over single quantum systems:

Moore’s law, which states that computer power will double for constant cost
roughly once every two years.

With classical computers, simulating quantum computers has no efficient fashion.
- efficient: polynomial time 
- inefficient: super-polynomial time(typically exponential)

Strong Turing-Church Thesis: Any algorithmic process can be simulated **efficiently** using a Turing machine.

Thus, unlike analog computation, quantum computation can in principle tolerate a finite
amount of noise and still retain its computational advantages, by the development
of a theory of quantum error-correcting codes and fault-tolerant quantum computation.

Solovay–Strassen test for primality, using randomized algorithms.

modified Strong Turing-Church Thesis: Any algorithmic process can be simulated efficiently using a **probablisitic** Turing machine.

Shor’s 1994 demonstration
- finding the prime factors of an integer
- ‘discrete logarithm’ problem

Grover’s algorithm

Algorithm design for quantum computers is hard because of 2 problems:
1. First, our human intuition is rooted in the classical world.
2. The quantum algorithm developed must be better than any existing classical algorithm!

Now on the information theory side.

Shannon’s noiseless channel coding theorem: quantifies
the physical resources required to store the output from an information source.

Shannon’s noisy channel coding theorem:
- To achieve reliable transmission in the presence of noise, **error-correcting codes** could be used. This theorem gives an upper theoretical limit on the protection afforded by error-correcting codes.

superdense coding: transmit two
classical bits of information, while only transmitting one quantum bit from sender to
receiver

distributed quantum computation: exponentially less communication to solve certain problems, but under technical restrictions and only few applications.

networked information theory

### 1.1.2 Future directions

Quantum computation and quantum information has taught us to **think physically**
about computation, and we have discovered that this approach yields many new and
exciting capabilities for information processing and communication.

we can also learn to think computationally about
physics.

<!-- Classical: power source -> electricity -> classical computation 

New: power source -> (directly) -> computation
 -->
## 1.2 Quantum bits

> we mostly treat qubits as abstract mathematical objects rather than physical objects.

A classical bit can only have 2 states, but a qubit can be in states **other** than $\ket{0} \text{or} \ket{1}$.

It is also possible to form *linear combinations* of states, often
called *superpositions*, using the two computational basis states $\ket{0}, \ket{1}$:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1} \quad \alpha,\beta \in \Complex \tag{1.1}
$$

Remarkably, we **cannot** examine a qubit to determine its quantum state, the values of $\alpha$ and $\beta$.

When we measure a qubit we get either the result 0, with probability $|\alpha|^2$ , or the result 1, with probability $|\beta|^2$. $|\alpha|^2 + |\beta|^2 = 1$, since the probabilities must sum to one.

By contrast, a qubit can exist in a **continuum** of states between $\ket{0}$ and $\ket{1}$ – until it is observed.


$$\ket{\psi} = e^{i\gamma}( \cos \frac{\theta}{2} \ket{0} + e^{i\phi} \sin \frac{\theta}{2} \ket{1} ) \tag{1.3}$$

$e^{i\gamma}$, the *global phase* can be ignored because it has no observable effects.
- Observables depend on $\bra{\psi}A\ket{\psi}$. Because bra and ket are complex conjugates, they result in $(e^{i\gamma}) (e^{-i\gamma})$, cancelling each other out.

$$\ket{\psi} = \cos \frac{\theta}{2} \ket{0} + e^{i\phi} \sin \frac{\theta}{2} \ket{1} \tag{1.4}$$

> Recall Euler's formula

### 1.2.1 Multiple qubits

Two classical bits: 00, 01, 10, 11

Two qubits: $\ket{00}, \ket{01}, \ket{10}, \ket{11}$, and the superpositions of them four.

Thus, quantum state of two qubits involves associating a complex coefficient called **amplitude** with each of the four basis state, such that 

$$\ket{\psi} = \alpha_{00} \ket{00} + \alpha_{01} \ket{01} + \alpha_{10} \ket{10} + \alpha_{11} \ket{11} \tag{1.5}$$

Similar to the case for a single qubit, the probability $|\alpha_x|^2$

Normalization condition $\sum_{x\in\{0,1\}^2} |\alpha_x|^2 = 1$

re-normalized post-measurement state

> When you measure the first qubit, you project the global state onto the subspace compatible with the observed result; renormalization gives the new conditional state. And, if the qubits were entangled, that projection necessarily changes the second qubit’s state too.

An important two qubit state is the *Bell state* or *EPR pair*,

$$\frac{1}{\sqrt{2}} (\ket{00} + \ket{11}) \tag{1.7}$$

Thanks to entanglement, measuring the first qubit can ensure the state of the second qubit. 

Generally, for a quantum states with $n$ qubits, the number of amplitudes is $2^n$.

## 1.3 Quantum computation

Changes occurring to a quantum state can be described using the language of quantum
computation.

A quantum computer is built from a quantum circuit
containing wires and elementary quantum gates to carry around and manipulate the
quantum information.

### 1.3.1 Single qubit gates

Quantum NOT gate: from $\alpha \ket{0} + \beta \ket{1}$ to $\alpha \ket{1} + \beta \ket{0}$. 
- This linear behavior is a general property of quantum mechanics

Quantum gates on a single qubit can be described by two-by-two matrices.

The *only* Requirement for such matrices, is being unitary, where $U^\dagger U = I$, where $U^\dagger$ is the adjoint of U(obtained by transposing and then complex conjugating
U).
- This follows that the total probability sum is 1.

Pauli-Z and Hadamard gate are the most 2 useful quantum gates:

$$H \equiv \frac{1}{\sqrt{2}} \begin{bmatrix}
    1 & 1 \\
    1 & -1
\end{bmatrix} \tag{1.14}$$

The Hadamard gate is sometimes described like "square-root of NOT gate",

$H$ is a rotation of the sphere about the ŷ axis by 90◦, followed by a rotation about the x̂ axis by 180◦

<!-- Yielding the result  -->

Summary(and a review) of X, Z, H on $\ket{\psi} = \alpha \ket{0} + \beta \ket{1}$
- X
- Z
- H

> A diagonal matrix is
a square matrix in which all elements outside the main diagonal (from top-left to bottom-right) are zero.

15

$$\begin{bmatrix}
    \cos\frac{\gamma}{2} & - \sin{\frac{\gamma}{2}} \\
    \sin{\frac{\gamma}{2}} & \cos{\frac{\gamma}{2}}
\end{bmatrix}
\tag{1.15}$$

16

$$\begin{bmatrix}
    e^{-i\beta/2}   & 0 \\
    0 & e^{i\beta/2}
\end{bmatrix}
\tag{1.16}
$$

Together with a global phase shift, a constant scalar $e^{i\alpha}$

an arbitrary quantum
computation on any number of qubits can be generated by a **finite set of gates** that is said
to be *universal* for quantum computation.


> When we apply a sequence of operations to a quantum state, the last operation in the product (on the far right) is applied first to the quantum state by the convention of matrix multiplication in linear algebra.

Box 1.1: Decomposing single qubit operations

$$
U = e^{i\alpha}
\begin{bmatrix}
    e^{-i\beta/2}   & 0 \\
    0 & e^{i\beta/2}
\end{bmatrix}
\begin{bmatrix}
    \cos\frac{\gamma}{2} & - \sin{\frac{\gamma}{2}} \\
    \sin{\frac{\gamma}{2}} & \cos{\frac{\gamma}{2}}
\end{bmatrix} 
, 
\begin{bmatrix}
    e^{-i\delta/2}   & 0 \\
    0 & e^{i\delta/2}
\end{bmatrix}

\tag{1.17}
$$

Notice that the second matrix is just an
ordinary rotation. 

It turns out that the first and last matrices can also be understood as rotations in a different plane. 

This decomposition can be used to give an exact
prescription for performing an arbitrary single qubit quantum logic gate.

### 1.3.2 Multiple qubit gates

The prototypical multi-qubit quantum logic gate is the controlled-NOT or CNOT gate.

This gate has two input qubits, known as the control qubit and the target qubit, respectively.

The action of the gate may be described as follows. 
- If the control qubit is set to
0, then the target qubit is left alone. 
- If the control qubit is set to 1, then the target qubit is flipped. In equations:


Another way of describing theis as a generalization of the classical
XOR gate, 
since the action of the gate may be summarized as $\ket{A, B} \implies \ket{A, A \oplus B}$

Classical NAND and XOR are essentially irreversible or non-invertible, which means the input cannot be determined given the result because of an irretrievable loss of information.

unitary quantum gates are always invertible, 
- since the inverse of a unitary matrix is also a unitary matrix, 
    - thus a quantum gate can always be inverted by another quantum gate. (more in 1.4.1)

CNOT and single qubit gates yield universality result: Any multiple qubit
logic gate may be composed from CNOT and single qubit gates.

### 1.3.3 Measurements in bases other than the computational basis
Other than $\ket{0}, \ket{1}$, there are another pair of basis states

$$\ket{+} = \frac{1}{2}(\ket{0} + \ket{1})$$

$$\ket{-} = \frac{1}{2}(\ket{0} - \ket{1})$$

$$\ket{\psi} = \alpha \ket{0} + \beta \ket{1} 

= \alpha \frac{\ket{+} + \ket{-}}{\sqrt{2}} + \beta \frac{\ket{+} - \ket{-}}{\sqrt{2}} 

= \frac{\alpha + \beta}{\sqrt{2}}\ket{+} + \frac{\alpha - \beta}{\sqrt{2}}\ket{-}  \tag{1.19}$$

Natually, probability for $\ket{+}$ is $\frac{|\alpha + \beta|^2}{2}$, for $\ket{-}$ is $\frac{|\alpha - \beta|^2}{2}$

Basis states can be arbitrary but they must be *ortho-normal* to perform a measurement, following probability sum to 1.

> two vectors in an inner product space are orthonormal if they are orthogonal unit vectors.

This new formalism is the best for describing observed experimental results, such as in the Stern–Gerlach experiment.

### 1.3.4 Quantum circuits

3 features not allowed in quantum circuits
1. no loops allowed 
2. FANIN(classical circuit wires to be ‘joined’ together) not allowed.
   1. Obviously this operation is not reversible and therefore not unitary,
3. FANOUT(whereby several copies of a bit are produced) not allowed

Suppose U is any unitary matrix(quantum gate) on $n$ qubits, then controlled-U naturally has a definition that has a single control qubit(indicated by the line with the black dot) and n target qubits.
- If the control qubit is set to 0 then nothing happens to the target qubits.
- If the control qubit is set to 1 then the gate U is applied to the target qubits.

Measurement: converts a single qubit state into a probabilistic classical bit M, with a probability ...

### 1.3.5 Copying Qubits 

No cloning theorem: It is impossible to copy an unknown quantum state.
- Because determining a state instantly collapses its hidden information.

If we try to "copy" using a CNOT gate, we get:

$$\ket{\psi}\ket{\psi} = a^2 \ket{00} + ab \ket{01} + ab \ket{10} + b^2 \ket{11} \tag{1.22}$$

> $\ket{\psi} \ket{\psi} \equiv \ket{\psi} \otimes \ket{\psi}$, the tensor product, (NOT the matrix multiplication).

### 1.3.6 Bell states

Bell states(or sometimes the EPR states or EPR pairs)
- Maximally entangled: If you measure one qubit, the other is perfectly determined.
- not separable: If write this as a product of two separate qubit states, won’t get the same expression because the qubits are correlated in a way that cannot be separated.
  - A state is separable if it can be written as a product of individual states.
  - Assume it is separable as $\ket{\Phi^+} = \ket{A} \otimes \ket{B}$, where $\ket{A} = \alpha \ket{0} + \beta \ket{1}$, $\ket{B} = \theta \ket{0} + \delta \gamma{1}$
  - Compute the product: $\ket{A} \otimes \ket{B} =$
  - Distribute the terms: $\ket{A} \otimes \ket{B} = \alpha\gamma \ket{00} + \alpha \delta \ket{01} + \beta \gamma \ket{10} +\beta \delta \ket{11}$
  - But in $\ket{\Phi^+}$ there is no term $\ket{01}$ or $\ket{10}$, contradiction.
- Bell basis(orthonormal) of the 2 qubit Hilbert space


Their creation follows this idea: Hadamard creates superposition, then as a control state of CNOT which creates entanglement.

$$\ket{\beta_{00}} = \ket{\Phi^+} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11}) \tag{1.23}$$

$$\ket{\beta_{01}} = \ket{\Psi^+} = \frac{1}{\sqrt{2}}(\ket{01} + \ket{10}) \tag{1.24}$$

$$\ket{\beta_{10}} = \ket{\Phi^-} = \frac{1}{\sqrt{2}}(\ket{00} - \ket{11}) \tag{1.25}$$

$$\ket{\beta_{11}} = \ket{\Psi^-} = \frac{1}{\sqrt{2}}(\ket{01} - \ket{10}) \tag{1.26}$$

General formula: $x,y \in (0,1)$, $\bar{y}$ is the negation of y ($y = 1 \implies \bar{y} = 0$)

$$\ket{\beta_xy} = \frac{1}{\sqrt{2}} = (\ket{0y}+ (-1)^{x}\ket{1\bar{y}}), $$

### 1.3.7 Example: quantum teleportation

**Quantum teleportation** is a
technique for moving quantum states around, even in the absence of a quantum communications channel linking the sender of the quantum state to the recipient.
- quantum teleportation is a way of utilizing the
entangled EPR pair in order to send "almost" (up to a known Pauli error) $\ket{\psi}$ to Bob, with only a small overhead of classical communication.


| Alice sends | Bob applies |
| ----------- | ----------- |
| 00          | ( I )       |
| 01          | ( X )       |
| 10          | ( Z )       |
| 11          | ( XZ )      |

Summing up, Bob needs to apply the transformation $Z^{M_1} X^{M_2}$


Many interesting features of quantum teleporation:
1. no communication theorem: It does not enable faster than light communication. Because the classical bit is still transmitted over a classical communications channel.
2. no-cloning theorem not violated. After teleportation, target qubit is in state $\ket{\psi}$ and the original qubit has already collapsed.

Quantum teleportation emphasizes the interchangeability of **different** resources in quantum mechanics, showing that 
one shared EPR pair together with two classical bits of communication is a resource at least the equal of one qubit of communication.

## 1.4 Quantum Algorithms 
### 1.4.1 Classical computations on a quantum computer
the reason quantum circuits cannot be used to directly simulate classical circuits
is because unitary quantum logic gates are inherently reversible, whereas many classical
logic gates such as the NAND gate are inherently irreversible.

A classical Toffoli gate has 3 bits, 2 control bits and 1 target bit which is only filpped when both of the control bits are 1.

The quantum Toffoli gate can be used to simulate **irreversible** classical logic gates, ensures that quantum computers are capable of performing any
computation which a classical (deterministic) computer may do.

Quantum computers can efficiently simulate non-deterministic classical computers(e.g., random number generation).

### 1.4.2 Quantum parallelism

Quantum parallelism is a fundamental feature of many quantum algorithms.

$U_f$ can be thought as a blackbox $\ket{x, y} \rarr \ket{x, y \oplus f(x)}$
- the first register is called the ‘data’ register, 
- the second register the ‘target’ register.

Walsh–Hadamard transform: generalizing the previous procedures on arbitrary number of bits.

$H^{\otimes2}$ to denote the parallel action of two Hadamard gates ($\otimes$ read as "tensor")

> the Hadamard transform produces an equal superposition of all computational basis states. Moreover, it does this extremely efficiently, producing a superposition of $2^n$
states using just n gates.

> It changes basis from Computational basis (bit states) to Phase basis (interference patterns of $\pm 1$). It’s like a simplified Fourier transform over binary strings. It spreads amplitude evenly across states, enabling interference.

To be useful, we need to *extract* information about more than one f(x) value from the superposition states. Quantum algorithms use interference to amplify the correct answer before measurement.

### 1.4.3 Deutsch’s algorithm

Deutsch’s algorithm combines quantum parallelism with interference.


Quantum circuits enable determining a global property of f(x), namely $f(0) \oplus f(1)$, using only 1 evaluation of f(x)

### 1.4.4 The Deutsch–Jozsa algorithm

### 1.4.5 Quantum algorithms summarized

3 classes of problems that quantum computers have advandage on 
- quantum versions of the Fourier transform
- quantum versions of the Fourier transform
- quantum simulation, whereby a quantum computer is used to simulate a quantum system.

## 2.1 Linear algebra

### 2.1.1 Bases and linear independence

Spanning set

Linear independence

$$\tag{2.9}$$

Basis: set of linearly independent vectors which span a vector space $V$. Any two basis of $V$ have the same number of elements.

Dimension: the number of element in the basis

> Here we will only be interested in finite dimensional vector spaces. 

### 2.1.2 Linear operators and matrices

A linear operator between vector spaces V and W is defined to be any function A :V → W which is linear in its inputs

$$
\tag{2.10}
$$

zero operator, denoted as $0$, $0\ket{v} \equiv 0$

Suppose two linear operators, $A: V \mapsto W, B: W \mapsto X$.

The composition of B with A is denoted BA, $BA\ket{v} \equiv (BA)\ket{v} \equiv B(A\ket{v})$. (Remember the convention of right to left)

### 2.1.4 Inner products

Inner product is a function from $V \times V \rarr \Complex$ if it satisfies the 3 requirements 
1. linear in term of second argument 
$$
\tag{2.13}
$$
2. $\bra{v} \ket{v} = (\ket{v} \bra{v})^*$
3. $\bra{v} \ket{v} \geq 0$ with equality iff $\bra{v} = 0$

> In short, the input: 2 vectors, the output: a complex number

$\bra{v}$ is a dual vector of $\ket{v}$

inner product space: a vector space equipped with an inner product

> Hilbert space here is just inner product space

<!-- Orthogonal: inner product is 0. -->

Norm of a vector $\ket{v}$

$$
||\ket{v}|| \equiv \sqrt{\bra{v}\ket{v}}
\tag{2.16}
$$

A unit (normalized) vector has norm equal to 1.

normalizing: dividing by its norm.

Gram–Schmidt procedure takes independent vectors and makes them orthogonal by subtracting projections, then normalizes them to create an orthonormal basis. (https://youtu.be/zHbfZWZJTGc?si=9l8N-sr7TEf_kpv0)

> The dot product of a vector with itself equals the square of its length, not the other way around.

Outer product: representing linear operators which makes use of the inner product

$$
(\ket{w} \bra{v})(\ket{v'}) \equiv (\ket{w})(\bra{v}\ket{v'}) = (\bra{v}\ket{v'}) \ket{w}\tag{2.20}
$$

Two interpretations of 2.20
- operator $\ket{w} \bra{v}$ acts on $\ket{v'}$
- multiplying $\ket{w}$ by the complex number $\bra{v}\ket{v'}$.

completeness relation:

#### Box 2.1: The Cauchy-Schwarz inequality

Cauchy–Schwarz inequality is an important geometric fact about Hilbert spaces.



equality occurs iff $\ket{v}$ and $\ket{w}$ are linearly related.

### 2.1.5

> $v$ is here used to represent both an eigenvector and an eigenvalue.

characteristic function: $c(\lambda) \equiv \det|A - \lambda I|$

eigenspace corresponding to an eigenvalue v is the set of vectors which have eigenvalue v. It is a vector subspace of the vector space on which A acts.

diagonal representation(aka orthonormal decompositions) for an operator A: $A = \sum_i \ket{i}\bra{i}$, where $\ket{i}$ orthonormal set.

degenerate: When an eigenspace is more than one dimensional


