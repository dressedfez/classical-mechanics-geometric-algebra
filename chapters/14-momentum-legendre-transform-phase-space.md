---
title: "14. Momentum, the Legendre Transform, and Phase Space"
description: "Pass from Lagrangian mechanics to Hamilton's equations using canonical momentum and the Legendre transform."
---

Lagrangian mechanics describes a system using coordinates and velocities. Hamiltonian mechanics instead uses coordinates and momenta. This change is more than a relabeling: it turns the equations into a first-order flow on phase space and makes several powerful structures visible.

The central mathematical step is the Legendre transform. We will derive Hamilton's equations, work through the harmonic oscillator, and distinguish the Hamiltonian from mechanical energy. Geometric algebra continues to describe physical-space vectors and rotations, while phase space has a separate symplectic structure.

## 14.1 Canonical momentum

For a Lagrangian $L(q,\dot q,t)$ with coordinates $q^i$, define the **canonical momentum** conjugate to $q^i$ by

$$
p_i=\frac{\partial L}{\partial\dot q^i}.
$$

The momentum is conjugate to the coordinate because it is the variable paired with $q^i$ in the Hamiltonian description. It equals the usual linear momentum for a Cartesian coordinate and a standard kinetic energy, but in general coordinates it may include geometric factors or velocity-dependent potentials.

To use $(q,p)$ as independent variables, we must be able to solve these equations for the velocities $\dot q^i$ as functions of $q,p,t$. This is possible locally when the velocity Hessian

$$
W_{ij}=\frac{\partial^2L}{\partial\dot q^i\partial\dot q^j}
$$

is invertible. Such a Lagrangian is called **regular**. If it is singular, constraints among the momenta arise and a more advanced constrained-Hamiltonian treatment is needed; we will restrict the main development to regular systems.

## 14.2 The Legendre transform

For a regular Lagrangian, define the Hamiltonian by

$$
H(q,p,t)=\sum_i p_i\dot q^i-L(q,\dot q,t),
$$

where the velocities on the right are expressed in terms of $q,p,t$. This is the Legendre transform with respect to the velocities. Differentiating gives

$$
dH=\sum_i\left(\dot q^i\,dp_i-\dot p_i\,dq^i\right)-\frac{\partial L}{\partial t}dt,
$$

after using the Euler–Lagrange equations. To see the cancellations, differentiate $H=\sum_i p_i\dot q^i-L$: the terms $p_i\,d\dot q^i$ cancel against $(\partial L/\partial\dot q^i)d\dot q^i$ because $p_i=\partial L/\partial\dot q^i$. The remaining coordinate term becomes $-\dot p_i\,dq^i$ by the Euler–Lagrange equation. Comparing with

$$
dH=\sum_i\left(\frac{\partial H}{\partial q^i}dq^i+\frac{\partial H}{\partial p_i}dp_i\right)+\frac{\partial H}{\partial t}dt
$$

leads to **Hamilton's equations**:

```{note} Hamilton's equations

$$
\dot q^i=\frac{\partial H}{\partial p_i},
\qquad
\dot p_i=-\frac{\partial H}{\partial q^i}.
$$

The second-order equations of Lagrangian mechanics become a first-order system in the $2n$ variables $(q^i,p_i)$.
```

The state $(q,p)$ is a point in **phase space**. A solution traces a curve through this space. The coordinate $q$ and momentum $p$ are independent state variables, even though along a physical solution they are related by the equations of motion.

## 14.3 Worked example: the harmonic oscillator

For a mass on a spring,

$$
L=\frac{1}{2}m\dot x^2-\frac{1}{2}kx^2,
\qquad p=\frac{\partial L}{\partial\dot x}=m\dot x.
$$

Solving for the velocity, $\dot x=p/m$, and forming the Legendre transform gives

$$
H=p\dot x-L=\frac{p^2}{2m}+\frac{1}{2}kx^2.
$$

Hamilton's equations are

$$
\dot x=\frac{p}{m},
\qquad
\dot p=-kx.
$$

Combining them gives $m\ddot x=-kx$, the same equation obtained from Newton's and Lagrange's laws. In this example the Hamiltonian equals the total mechanical energy.

### Worked example: a simple pendulum

For a pendulum of length $\ell$ and bob mass $m$, use the angle $\theta$ as the coordinate. Its speed is $\ell\dot\theta$, so

$$
T=\frac{1}{2}m\ell^2\dot\theta^2,
\qquad U=mg\ell(1-\cos\theta),
\qquad L=T-U.
$$

The canonical momentum is the angular momentum about the pivot,

$$
p_\theta=\frac{\partial L}{\partial\dot\theta}=m\ell^2\dot\theta,
\qquad \dot\theta=\frac{p_\theta}{m\ell^2}.
$$

Substitute this velocity into the Legendre transform $H=p_\theta\dot\theta-L$:

$$
H(\theta,p_\theta)=\frac{p_\theta^2}{2m\ell^2}+mg\ell(1-\cos\theta).
$$

Hamilton's equations now give

$$
\dot\theta=\frac{p_\theta}{m\ell^2},
\qquad
\dot p_\theta=-mg\ell\sin\theta.
$$

Differentiating the first equation and inserting the second recovers $\ddot\theta+(g/\ell)\sin\theta=0$. The phase-space formulation is first order, but it contains exactly the same dynamics as the second-order pendulum equation.

## 14.4 When is the Hamiltonian the energy?

For a natural mechanical system with $L=T-U$, where $T$ is a quadratic function of the velocities and $U$ is independent of velocity, the Legendre transform gives $H=T+U$. But this equality is not automatic. If the Lagrangian depends explicitly on time, the Hamiltonian can change along a trajectory. Velocity-dependent interactions can also change the relation between $H$ and the familiar kinetic-plus-potential energy.

Along a solution of Hamilton's equations,

$$
\frac{dH}{dt}=\frac{\partial H}{\partial t}.
$$

Indeed, the chain rule gives $dH/dt=\sum_i(H_{q^i}\dot q^i+H_{p_i}\dot p_i)+H_t$. The first two terms cancel after using $\dot q^i=H_{p_i}$ and $\dot p_i=-H_{q^i}$. Thus an explicitly time-independent Hamiltonian is conserved. For a standard natural system, this conserved quantity is mechanical energy. Chapter 12 reached energy conservation from time-translation symmetry; here it follows directly from Hamilton's equations.

## 14.5 Phase space and symplectic geometry

Phase space is not generally ordinary physical space. Even for one particle moving in three dimensions, its phase point has six coordinates: three positions and three momenta. Its geometry is organized by the canonical pairing of each coordinate with its momentum. For $n$ degrees of freedom the fundamental two-form is

$$
\omega=\sum_i dq^i\wedge dp_i.
$$

This is a **symplectic form**. It is not the Euclidean metric of physical space and should not be confused with the GA outer product used to represent physical oriented areas. A system can have both structures: GA describes distances, planes, and rotations in physical space; symplectic geometry describes the canonical structure of phase space.

## 14.6 What to remember

- Canonical momentum is $p_i=\partial L/\partial\dot q^i$.
- A regular Lagrangian allows velocities to be solved in terms of coordinates and momenta.
- The Legendre transform $H=\sum_i p_i\dot q^i-L$ gives Hamilton's first-order equations.
- Phase space has one coordinate and one conjugate momentum for every degree of freedom.
- For natural, time-independent systems, $H$ is mechanical energy; in general, interpret it from its definition.
- Phase space is symplectic; GA's physical-space metric and outer product describe a different geometry.

### Exercises

1. Starting from $L=\tfrac12m\dot x^2-U(x)$, derive $p$ and $H$, then obtain Newton's equation from Hamilton's equations.
2. Find the Hamiltonian of a simple pendulum with coordinate $\theta$, length $\ell$, and bob mass $m$.
3. Explain why the phase space of a particle moving in ordinary 3D space has six dimensions.
4. For $H=p^2/(2m)+U(x,t)$, show that $dH/dt=\partial H/\partial t$ along a solution.
5. Give an example of a canonical momentum that is not simply mass times velocity, and identify the extra term.
6. Explain why a phase-space symplectic form should not be identified with a physical-space bivector.
7. **Synthesis.** For $L=\tfrac12m\dot x^2+\alpha x\dot x-U(x)$, find the canonical momentum and Hamiltonian in terms of $x,p$. Identify the mechanical momentum and use Hamilton's equations to recover the force law. Explain why the velocity-dependent term changes canonical momentum without changing that force law.

## Further reading

- John R. Taylor, *Classical Mechanics*, chapters on Hamiltonian mechanics.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for Legendre transforms and phase space.
- OpenStax, *University Physics, Volume 1*, for the Lagrangian and Hamiltonian formulations.
