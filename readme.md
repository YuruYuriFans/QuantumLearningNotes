# Quantum Computation and Quantum Information  (Michael A. Nielsen, Isaac L. Chuang) notes

## 0 Nomenclature and notation

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

Bra: row vector, Hermitian conjugate (complex conjugate transpose) of a Ket.

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
        - $\therefore ket{0}$ and $\ket{1}$ are not eigenvectors of $\sigma_z$
- $\sigma_z$ is the phase flip operator, it leaves $\ket{0}$ unchanged but flips $\ket{1}$, more precisely
    - $\sigma_z \ket{0} = \ket{0}, \quad \sigma_z \ket{1} = - \ket{1} $
        - $\therefore \ket{0}$ and $\ket{1}$ are eigenvectors of $\sigma_z$ with eigenvalues 1 and -1, respectively.
> For information theorists, always log base two unless otherwise noted.

relative entropy of a positive operator A with respect to a positive operator B: 

$$S(A||B) \equiv tr(A \log A) - tr (A \log B)$$

where $tr$ is the trace that adds up the diagonals: $tr(A) = \sum_{i} A_{ii}$ 

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

Quantum computation and quantum information has taught us to think physically
about computation, and we have discovered that this approach yields many new and
exciting capabilities for information processing and communication.

we can also learn to think computationally about
physics.

Classical: power source -> electricity -> classical computation 

New: power source -> (directly) -> computation

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

a product of rotations(1.15)

rotation about the ẑ axis (1.16)

an arbitrary quantum
computation on any number of qubits can be generated by a **finite set of gates** that is said
to be *universal* for quantum computation.

Box 1.1: Decomposing single qubit operations

### 1.3.2 Multiple qubit gates

The prototypical multi-qubit quantum logic gate is the controlled-NOT or CNOT gate.

This gate has two input qubits, known as the control qubit and the target qubit, respec-
tively.

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