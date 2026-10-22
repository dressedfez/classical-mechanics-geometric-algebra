---
title: "13. Small Oscillations and Normal Modes"
description: "Linearize coupled motion near equilibrium and use mass and stiffness matrices to find normal modes and their frequencies."
---

Chapter 6 studied one oscillator. Many real systems have several coordinates that move together: two masses joined by springs, a molecule with many atoms, or a structure that can bend in multiple ways. Near a stable equilibrium, the equations often become linear, and the motion separates into a set of independent normal modes.

The main tools here are the mass and stiffness matrices and a generalized eigenvalue problem. Geometric algebra contributes a clear description of the physical displacement vectors and of tangent directions when constraints are present. The modes themselves live in configuration space, however, and matrix methods are the direct language for calculating them.

## 13.1 Linearizing near equilibrium

Let a system have generalized coordinates $q^1,\ldots,q^n$ and a stable equilibrium at $q=q_0$. Define the small displacement column vector

$$
\boldsymbol\eta=q-q_0.
$$

For sufficiently small $\boldsymbol\eta$, expand the potential energy in a Taylor series. At equilibrium its first derivatives vanish, leaving

$$
U(q)=U(q_0)+\frac12\boldsymbol\eta^{\mathsf T}K\boldsymbol\eta+\text{higher-order terms},
$$

where the **stiffness matrix** is the Hessian

$$
K_{ij}=\left[\frac{\partial^2U}{\partial q^i\partial q^j}\right]_{q_0}.
$$

In components, this expansion is $U(q_0+\eta)=U(q_0)+\sum_i U_i\eta_i+\tfrac12\sum_{ij}U_{ij}\eta_i\eta_j+\cdots$. Equilibrium means $U_i=0$, and equality of mixed partial derivatives makes $K$ symmetric. At a nondegenerate stable equilibrium, the curvature is positive in every allowed direction, so $\boldsymbol\eta^{\mathsf T}K\boldsymbol\eta>0$ for every nonzero small displacement. If a constraint removes a direction, stability is tested only among the remaining allowed displacements. When a curvature vanishes, higher-order terms decide stability and the quadratic normal-mode approximation may not suffice.

For small displacements, the kinetic energy can also be evaluated at equilibrium to leading order:

$$
T=\frac12\dot{\boldsymbol\eta}^{\mathsf T}M\dot{\boldsymbol\eta},
$$

where $M$ is the mass matrix. For simple particle coordinates it may be constant; for curvilinear generalized coordinates it is the kinetic-energy metric from Chapter 11 evaluated at equilibrium.

If the mass matrix depends on position, replacing it by its equilibrium value is valid at this order. The next term in its expansion multiplies $\eta$ by two velocity factors, and is therefore beyond the quadratic approximation in small displacement and velocity.

Lagrange's equations become the linear system

$$
M\ddot{\boldsymbol\eta}+K\boldsymbol\eta=0.
$$

The approximation neglects terms quadratic and higher in the displacement or velocity. It works best for small motion near a stable equilibrium, where the neglected terms remain small over the interval of interest.

## 13.2 Normal modes as a generalized eigenvalue problem

Look for a solution in which every coordinate oscillates with the same angular frequency and fixed relative amplitudes:

$$
\boldsymbol\eta(t)=\mathbf a\cos(\omega t+\phi).
$$

Substitution yields

$$
K\mathbf a=\omega^2M\mathbf a.
$$

This is a generalized eigenvalue problem. Its eigenvalues are the squared angular frequencies, and its eigenvectors give the relative displacement pattern of each **normal mode**. For $n$ independent coordinates there are, in general, $n$ modes. A general small motion is a superposition of them.

An equivalent way to find the frequencies is to set $\det(K-\omega^2M)=0$. For two coordinates this is a quadratic equation in $\omega^2$, so it gives two modes. The determinant finds the allowed frequencies; solving $(K-\omega^2M)\mathbf a=0$ at each root then finds the corresponding pattern. A zero determinant is necessary because a nonzero mode vector must lie in the null space of that matrix.

If $M$ is symmetric and positive definite and $K$ is symmetric, the frequencies are real for a stable system and modes with distinct frequencies are orthogonal in the mass-weighted inner product:

$$
\mathbf a_i^{\mathsf T}M\mathbf a_j=0\qquad(i\ne j).
$$

If a squared frequency is negative, the equilibrium is unstable in that direction: the corresponding solution grows or decays exponentially rather than oscillating. A zero frequency can indicate a free translation or another symmetry direction, rather than a restoring mode.

To solve the problem with ordinary symmetric-matrix methods, factor the positive mass matrix or introduce mass-weighted coordinates $\mathbf y=M^{1/2}\boldsymbol\eta$. Then

$$
\ddot{\mathbf y}+M^{-1/2}KM^{-1/2}\mathbf y=0.
$$

The matrix $M^{-1/2}KM^{-1/2}$ is symmetric and can be diagonalized by an orthogonal transformation. This gives independent coordinates $Q_i$, each satisfying $\ddot Q_i+\omega_i^2Q_i=0$.

## 13.3 Worked example: two coupled masses

Two equal masses $m$ move horizontally. Each is attached to a wall by a spring of constant $k$, and a third spring of constant $k_c$ connects the masses. Let $x_1,x_2$ be their displacements from equilibrium.

The potential energy is

$$
U=\frac12kx_1^2+\frac12k_c(x_2-x_1)^2+\frac12kx_2^2
=\frac12(k+k_c)x_1^2-k_cx_1x_2+\frac12(k+k_c)x_2^2.
$$

Taking its second derivatives with respect to $x_1,x_2$ gives the stiffness matrix below. The off-diagonal entries are negative because moving one mass in the positive direction pulls the other mass toward it through the connecting spring.

$$
M=m\begin{pmatrix}1&0\\0&1\end{pmatrix},
\qquad
K=\begin{pmatrix}k+k_c&-k_c\\-k_c&k+k_c\end{pmatrix}.
$$

For the in-phase mode, $x_1=x_2$. The connecting spring does not change length, so

$$
\mathbf a_+=(1,1)^{\mathsf T},
\qquad \omega_+^2=\frac{k}{m}.
$$

For the out-of-phase mode, $x_1=-x_2$. The central spring stretches as well as the outer springs, giving

$$
\mathbf a_-=(1,-1)^{\mathsf T},
\qquad \omega_-^2=\frac{k+2k_c}{m}.
$$

Since $k_c>0$, the out-of-phase mode has the larger frequency. If one mass is displaced while the other starts at rest, the motion is generally a superposition of both modes, producing a changing pattern of energy exchange between the masses.

We can make that superposition explicit. Normalize the mode vectors so their mass-weighted lengths are one:

$$
\mathbf a_+=\frac{1}{\sqrt{2m}}\begin{pmatrix}1\\1\end{pmatrix},
\qquad
\mathbf a_-=\frac{1}{\sqrt{2m}}\begin{pmatrix}1\\-1\end{pmatrix}.
$$

If initially $x_1=A$, $x_2=0$, and both masses are at rest, each mode starts with the same amplitude. Reconstructing the positions gives

$$
x_1(t)=\frac A2\bigl(\cos\omega_+t+\cos\omega_-t\bigr),
\qquad
x_2(t)=\frac A2\bigl(\cos\omega_+t-\cos\omega_-t\bigr).
$$

For $m=1.0\,\mathrm{kg}$, $k=100\,\mathrm{N\,m^{-1}}$, and $k_c=25\,\mathrm{N\,m^{-1}}$, the frequencies are $10.0$ and $12.25\,\mathrm{rad\,s^{-1}}$. The identity $\cos a+\cos b=2\cos[(a+b)/2]\cos[(a-b)/2]$ shows the slow amplitude envelope directly: energy moves between the masses on a timescale set by the difference of their mode frequencies. Within this linear model, the solution is the sum of two normal modes; the envelope is a useful description when those frequencies are close.

## 13.4 The geometry behind the matrices

For particle positions described by generalized coordinates, a small coordinate displacement produces physical displacements

$$
\delta\mathbf r_a=\sum_i\frac{\partial\mathbf r_a}{\partial q^i}\,\delta q^i.
$$

The mass matrix is built from inner products of these physical tangent vectors. GA is a natural way to keep each $\delta\mathbf r_a$ as a vector and to express the constraint geometry that determines which directions are allowed. Around equilibrium, those allowed infinitesimal changes form a linear space, and $M$ and $K$ describe the kinetic and restoring quadratic forms on that space.

The normal-mode amplitudes are coordinate columns, not physical vectors in ordinary three-dimensional space. Treating them as spatial vectors would mix two different geometries. For solving the coupled oscillations, the generalized eigenvalue problem is the clear and efficient method; GA explains how the physical tangent directions and their metric arise.

## 13.5 Modal energy and response

Choose mode vectors normalized so that $\mathbf a_i^{\mathsf T}M\mathbf a_j=\delta_{ij}$. Write $\boldsymbol\eta=\sum_i Q_i\mathbf a_i$. The quadratic Lagrangian separates:

$$
L=\frac12\sum_i\left(\dot Q_i^2-\omega_i^2Q_i^2\right).
$$

Each normal coordinate behaves like an independent oscillator. The total energy is a sum of modal energies,

$$
E=\frac12\sum_i\left(\dot Q_i^2+\omega_i^2Q_i^2\right).
$$

This decomposition explains why a complicated small motion can be understood by identifying a few basic patterns and their frequencies. If a system is driven near one mode's frequency, the response can be large, just as for the single oscillator in Chapter 6.

## 13.6 What to remember

- Near a stable equilibrium, expand the potential to quadratic order and evaluate the kinetic metric at equilibrium.
- Small motion obeys $M\ddot{\boldsymbol\eta}+K\boldsymbol\eta=0$.
- Normal modes solve $K\mathbf a=\omega^2M\mathbf a$; the eigenvector is the shape of a mode and the eigenvalue gives its frequency.
- Distinct modes are orthogonal with respect to the mass matrix.
- Negative squared frequency indicates instability; zero frequency can reflect a symmetry or free motion.
- GA helps describe physical displacement and constraint geometry, while matrices are best for the modal calculation.

### Exercises

1. For the two-mass system, verify both eigenvectors and frequencies by multiplying by the stiffness matrix.
2. Let $m=1.0\,\mathrm{kg}$, $k=100\,\mathrm{N\,m^{-1}}$, and $k_c=25\,\mathrm{N\,m^{-1}}$. Find the two angular frequencies.
3. Explain physically why the connecting spring is unstretched in the in-phase mode and stretches most in the out-of-phase mode.
4. Show that eigenvectors of a symmetric generalized eigenproblem with distinct eigenvalues are orthogonal in the $M$ inner product.
5. What does a negative eigenvalue $\omega^2$ imply for the time dependence of that mode?
6. Explain why a normal-mode eigenvector is not necessarily a physical-space vector.
7. **Synthesis.** For the two-mass example, let the initial displacements be $x_1(0)=A$, $x_2(0)=B$ and the initial velocities be $u_1,u_2$. Project these four initial data onto the in-phase and out-of-phase modes, write the resulting motion, and identify the special initial data that excite only one mode.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on coupled oscillators and normal modes.
- OpenStax, *University Physics, Volume 1*, material on coupled oscillations and resonance.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for small oscillations in generalized coordinates.
