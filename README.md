**Introduction**

In this notebook, we introduce a new variational quantum linear solver algorithm, with application to Poisson equation. This algorithm consists of employing the parallelism advantage that offers quantum computers to speedup the convergence to the target state( solution). Below is the detailed mathematics.

**Problem setup**

Let's assume that we want to solve a system of $N\times N$ linear equation ($N=2^n$, where $n$ is the number of qubits, $N$ the Hilbert space dimension), of the form:

$$
A\ket X =\ket b,
$$
with $A$ a $2^n\times2^n$ matrix and $\ket X the solution vector. Our algorithm to solve this equation is described as follows:

- [x] From the system above we first construct a positive semi-definite operator **$H$** such that $H = \frac{1}{N}[A^\dagger(I_N - \ket b \bra b )A]$ or a local Hamiltonian following the work of Bravo et al  as $H = \frac{1}{N}[A^\dagger U_b(I_N - \sum_{k=0}^{n} \ket 0_k \bra 0 )U_b^\dagger A]$.
