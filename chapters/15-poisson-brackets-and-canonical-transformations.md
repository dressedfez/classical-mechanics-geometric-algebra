---
title: "15. Poisson Brackets and Canonical Transformations"
description: "Use Poisson brackets to describe time evolution and generators, then introduce canonical transformations and symplectic structure."
---

Hamilton's equations describe how coordinates and momenta evolve. Poisson brackets package that evolution into a rule that applies to any observable, such as position, momentum, energy, or angular momentum. They also identify which quantities generate translations and rotations and which transformations preserve Hamiltonian mechanics.

The bracket is a structure on phase-space functions. Although GA also has products and commutators, those operations act on physical multivectors and are not the same as a Poisson bracket. We will keep these geometries distinct and connect them only where a physical symmetry gives a clear bridge.

## 15.1 The Poisson bracket

For two functions $f(q,p,t)$ and $g(q,p,t)$, define the Poisson bracket by

$$
\{f,g\}=\sum_i\left(
\frac{\partial f}{\partial q^i}\frac{\partial g}{\partial p_i}
-\frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q^i}
\right).
$$

It is antisymmetric, $\{f,g\}=-\{g,f\}$, and obeys a product rule in each argument. The fundamental brackets are

$$
\{q^i,q^j\}=0,
\qquad \{p_i,p_j\}=0,
\qquad \{q^i,p_j\}=\delta^i_j.
$$

For an observable $f$, the chain rule and Hamilton's equations give

$$
\frac{df}{dt}=\{f,H\}+\frac{\partial f}{\partial t}.
$$

For one degree of freedom, this follows by writing $df/dt=f_q\dot q+f_p\dot p+f_t$, then substituting $\dot q=H_p$ and $\dot p=-H_q$. The result is $f_qH_p-f_pH_q+f_t$, exactly the bracket above plus explicit time dependence. The same argument adds one such pair of terms for every coordinate.

An observable with no explicit time dependence is conserved when its bracket with the Hamiltonian vanishes. This is a quick test that often avoids solving the equations of motion.

### Example: the oscillator

For $H=p^2/(2m)+kx^2/2$, the bracket gives

$$
\dot x=\{x,H\}=\frac{p}{m},
\qquad
\dot p=\{p,H\}=-kx.
$$

Also $\{H,H\}=0$, so the time-independent Hamiltonian is conserved. The Poisson-bracket formulation reproduces Hamilton's equations and extends them to any function of the state.

## 15.2 Generators of transformations

Let $G(q,p)$ generate an infinitesimal transformation with parameter $\epsilon$. Its action on any observable is

$$
\delta f=\epsilon\{f,G\}.
$$

For the one-dimensional translation generator $G=p$, this gives $\delta x=\epsilon$ and $\delta p=0$. Momentum generates translations of position. For a planar particle, the scalar angular momentum about the perpendicular axis is

$$
L_z=xp_y-yp_x.
$$

Its bracket action is

$$
\{x,L_z\}=-y,
\qquad
\{y,L_z\}=x,
\qquad
\{p_x,L_z\}=-p_y,
\qquad
\{p_y,L_z\}=p_x.
$$

These are the infinitesimal changes under a rotation in the plane. In GA, the physical angular momentum is the bivector $\mathcal J=\mathbf r\wedge\mathbf p$; in a chosen plane it corresponds to the scalar component $L_z$ multiplying the plane bivector. The Poisson bracket describes the generator's action on phase-space observables, while the bivector describes the physical rotation plane.

If the Hamiltonian is invariant under a generated transformation, then $\{G,H\}=0$ and $G$ is conserved. This is the Hamiltonian expression of the symmetry-conservation relation introduced in Chapter 12.

## 15.3 Canonical transformations

A change of phase-space variables $(q,p)\mapsto(Q,P)$ is **canonical** if it preserves the Hamiltonian form of the equations. Equivalently, the new variables have the same fundamental Poisson brackets:

$$
\{Q^i,Q^j\}=0,
\qquad \{P_i,P_j\}=0,
\qquad \{Q^i,P_j\}=\delta^i_j.
$$

For a linear transformation $z'=Az$ with $z=(q,p)^{\mathsf T}$, the condition is

$$
A^{\mathsf T}\mathbb S A=\mathbb S,
\qquad
\mathbb S=\begin{pmatrix}0&I\\-I&0\end{pmatrix}.
$$

Such a matrix is called symplectic. It preserves the phase-space two-form $\sum_i dq^i\wedge dp_i$ and phase-space volume. Preserving ordinary distances is not required; canonical transformations preserve a different structure from orthogonal transformations in physical space.

One systematic way to construct canonical transformations is with a generating function. For a function $F_2(q,P,t)$,

$$
p_i=\frac{\partial F_2}{\partial q^i},
\qquad
Q^i=\frac{\partial F_2}{\partial P_i},
\qquad
K=H+\frac{\partial F_2}{\partial t}.
$$

Here $K(Q,P,t)$ is the Hamiltonian in the new variables. The identity transformation follows from $F_2=\sum_iq^iP_i$. More useful choices can simplify a problem, reveal constants of motion, or lead toward Hamilton–Jacobi theory.

### Worked example: rescaling a canonical pair

Choose a constant dimensionless scale $a\ne0$ and set $F_2(q,P)=a qP$. The generating-function rules give

$$
p=\frac{\partial F_2}{\partial q}=aP,
\qquad Q=\frac{\partial F_2}{\partial P}=aq,
$$

so $Q=aq$ and $P=p/a$. Directly,

$$
\{Q,P\}=\{aq,p/a\}=1,
\qquad \{Q,Q\}=\{P,P\}=0.
$$

The coordinate is stretched by $a$ while its conjugate momentum is reduced by the same factor. This preserves the canonical pairing, even though the transformation does not preserve the ordinary Euclidean distance in the $(q,p)$ diagram. For a Hamiltonian $H(q,p)$, the new Hamiltonian is obtained by substituting $q=Q/a$ and $p=aP$.

## 15.4 What GA does and does not add here

Poisson brackets use derivatives with respect to canonical coordinates and momenta. The geometric product combines physical multivectors according to a metric. A GA commutator can generate a rotation of a vector, but it is not interchangeable with the Poisson bracket that generates a canonical transformation in phase space.

The two descriptions meet when a physical symmetry acts on a mechanical system. For example, a spatial rotation has a rotor acting on position vectors and a canonical generator given by angular momentum. The rotor describes how physical vectors rotate; the Poisson bracket describes how all phase-space observables change. This distinction lets the book use GA honestly without suggesting that it replaces symplectic mechanics.

## 15.5 What to remember

- The Poisson bracket packages Hamiltonian time evolution: $\dot f=\{f,H\}+\partial f/\partial t$.
- A conserved observable with no explicit time dependence has zero bracket with $H$.
- A generator $G$ acts by $\delta f=\epsilon\{f,G\}$.
- Canonical transformations preserve the fundamental brackets and the symplectic form.
- A GA rotor acts on physical vectors; a Poisson bracket acts on phase-space functions.
- Spatial angular momentum connects these descriptions as both a physical bivector and a canonical generator of rotations.

### Exercises

1. Use the definition of the Poisson bracket to calculate $\{x,p\}$, $\{x,H\}$, and $\{p,H\}$ for the harmonic oscillator.
2. Show that a function $f(q)$ with no explicit time dependence is conserved for a Hamiltonian $H$ if $\{f,H\}=0$.
3. Verify that $L_z=xp_y-yp_x$ generates an infinitesimal rotation of $x$ and $y$.
4. Explain why a Euclidean rotation of physical space is not automatically the same thing as an arbitrary canonical transformation.
5. In one dimension, use $F_2(q,P)=qP$ to recover the identity transformation.
6. Explain the different roles of the angular-momentum bivector and the Poisson bracket in a spatial rotation.
7. **Synthesis.** Treat $L_z=xp_y-yp_x$ as a generator with parameter $\epsilon$. Integrate the bracket equations for $x,y,p_x,p_y$ to obtain the finite planar rotation, then explain how the same spatial rotation acts on a position vector by a GA rotor.

## Further reading

- John R. Taylor, *Classical Mechanics*, chapters on Poisson brackets and canonical transformations.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for symplectic and canonical methods.
- V. I. Arnold, *Mathematical Methods of Classical Mechanics*, for a geometric treatment of Hamiltonian systems.
