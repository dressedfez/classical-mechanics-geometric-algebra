---
title: "16. Hamilton–Jacobi Theory and Integrable Motion"
description: "Introduce Hamilton–Jacobi theory, separation of variables, action-angle variables, and an optional extended-time formulation."
---

Hamilton's equations evolve a state through phase space. Hamilton–Jacobi theory asks a different question: can we find a function whose derivatives encode a complete family of solutions? When the method works, it transforms the dynamics into a problem of integration and can reveal the regular structure of an integrable system.

We will develop the basic equation, solve it for familiar one-dimensional motion, and introduce action-angle variables. These methods are mathematically more advanced than Newton's laws, but the oscillator and central-force examples keep the physical meaning in view. GA remains useful for spatial orbital planes; the action variables belong to phase-space geometry.

## 16.1 The Hamilton–Jacobi equation

Let $S(q,t)$ be Hamilton's principal function. If its coordinate derivatives are identified with canonical momenta,

$$
p_i=\frac{\partial S}{\partial q^i},
$$

then Hamilton's equations can be transformed to a new set of constant coordinates if $S$ solves the Hamilton–Jacobi equation

$$
\frac{\partial S}{\partial t}+H\left(q,\frac{\partial S}{\partial q},t\right)=0.
$$

The equation is a first-order partial differential equation. A **complete integral** contains enough independent constants to describe the general motion. Once found, differentiating it with respect to those constants supplies the remaining integration relations.

For a time-independent Hamiltonian, seek a solution of the form

$$
S(q,t)=W(q)-Et.
$$

Then $W$ obeys the time-independent Hamilton–Jacobi equation

$$
H\left(q,\frac{dW}{dq}\right)=E.
$$

The function $W$ is called Hamilton's characteristic function. In one dimension it is the integral of momentum along the motion, $W(q)=\int p(q;E)\,dq$.

## 16.2 Worked example: the harmonic oscillator

For $H=p^2/(2m)+kx^2/2$, the characteristic equation is

$$
\frac{1}{2m}\left(\frac{dW}{dx}\right)^2+\frac12kx^2=E.
$$

Thus

$$
p=\frac{dW}{dx}=\pm\sqrt{2m\left(E-\frac12kx^2\right)}.
$$

Let $\omega=\sqrt{k/m}$ and $A=\sqrt{2E/k}$. On the branch with positive momentum, $p=m\omega\sqrt{A^2-x^2}$, so one convenient integral is

$$
W(x;E)=\int_0^x p(x';E)\,dx'
=\frac{m\omega}{2}\left[x\sqrt{A^2-x^2}+A^2\arcsin(\frac{x}{A})\right].
$$

The turning points are $x=\pm A$, where $p=0$; the negative-momentum branch has the opposite sign for $dW/dx$. To recover the time, differentiate the integral with respect to its parameter $E$ while holding $x$ fixed:

$$
\frac{\partial W}{\partial E}
=\int_0^x\frac{\partial p}{\partial E}\,dx'
=\int_0^x\frac{m}{p}\,dx'
=\frac{1}{\omega}\arcsin\left(\frac{x}{A}\right).
$$

On this branch, $\partial W/\partial E$ is the elapsed time from the origin crossing. Solving gives $x=A\sin(\omega t)$; the other momentum branch completes the oscillation. The quadrature therefore recovers the familiar periodic motion rather than introducing a new trajectory.

The integral need not always have an elementary form. The method is useful even when it produces a quadrature, because it separates the dynamics into an explicit integral that can be evaluated analytically or numerically.

## 16.3 Separation of variables in a central potential

For a particle moving in a plane under a central potential,

$$
H=\frac{p_r^2}{2m}+\frac{p_\theta^2}{2mr^2}+U(r).
$$

The angle $\theta$ is cyclic, so $p_\theta=L$ is constant. Seek a separated characteristic function

$$
W(r,\theta)=W_r(r)+L\theta.
$$

The radial part satisfies

$$
\frac{1}{2m}\left(\frac{dW_r}{dr}\right)^2+\frac{L^2}{2mr^2}+U(r)=E.
$$

This is the same effective-potential equation derived in Chapter 7. The radial action comes from integrating the radial momentum between turning points; the angular part records the conserved angular momentum. In three dimensions, the constant angular-momentum bivector also identifies the orbital plane. Thus GA gives a compact geometric statement about the orbit, while Hamilton–Jacobi separation uses scalar canonical coordinates to solve for it.

## 16.4 Action-angle variables

For a periodic degree of freedom, define the **action variable**

$$
J=\frac{1}{2\pi}\oint p\,dq,
$$

where the integral is taken once around a closed orbit in its phase plane. The conjugate angle variable $\vartheta$ increases uniformly in time for an integrable system. The transformed Hamiltonian depends only on the actions, $H=H(J_1,\ldots,J_n)$, and

$$
\dot J_i=0,
\qquad
\dot\vartheta_i=\frac{\partial H}{\partial J_i}=\omega_i.
$$

The actions stay fixed, while the angles advance linearly. This is a powerful description of regular motion: complicated coordinates may oscillate in a complicated way, even though the angles on the invariant torus move uniformly.

For a one-dimensional harmonic oscillator, the phase-space orbit is an ellipse. Its enclosed area is $\oint p\,dx=2\pi E/\omega$, so

$$
J=\frac{E}{\omega},
\qquad H(J)=\omega J,
\qquad \dot\vartheta=\omega.
$$

The area can be checked from its semiaxes. The largest displacement and momentum are $A=\sqrt{2E/k}=\sqrt{2E/m}/\omega$ and $p_{\max}=\sqrt{2mE}$. Hence the ellipse area is $\pi A p_{\max}=2\pi E/\omega$. Dividing by $2\pi$ gives $J=E/\omega$. This shows why the action has units of angular momentum and why it is unchanged as the oscillator moves around its phase-space ellipse.

The angle variable is precisely the oscillator phase, and its uniform increase matches the rotating state-plane picture from Chapter 6. The phase plane here is a canonical $(x,p)$ plane; its area and symplectic form should not be confused with a physical-space bivector, even though both use oriented two-dimensional geometry.

## 16.5 Integrability and limits

For a system with $n$ degrees of freedom, complete integrability requires $n$ independent conserved quantities that are in involution: their pairwise Poisson brackets vanish. Then, under suitable regularity conditions, the motion can be described by action-angle variables on invariant tori.

Not every system is integrable. Some systems have too few conserved quantities to reduce all motion to quadratures, and small perturbations can create regions of irregular motion. Chapter 17 introduces phase portraits and numerical tools for examining such cases. Hamilton–Jacobi theory remains valuable because it identifies exactly what structure makes a system solvable.

## 16.6 Optional extension: time as a coordinate

The usual formulation uses time $t$ to label a path. We can instead regard time as one coordinate of an **extended configuration space**, alongside the generalized coordinates. This is sometimes called an event-space formulation. It is a variational change of parameter, not a new GA product, but it makes the relation between time-translation symmetry and energy especially direct.

Let $\alpha$ be any parameter that increases monotonically with time, and write

$$
x^0=t,\qquad x^i=q^i,\qquad
t'=\frac{dt}{d\alpha}>0,\qquad q'^i=\frac{dq^i}{d\alpha}.
$$

The physical velocity is $\dot q^i=q'^i/t'$. Define an extended Lagrangian

$$
\Lambda(t,q,t',q')
=t' L\left(t,q,\frac{q'}{t'}\right).
$$

Then the action has the same value in either parameter:

$$
S=\int L(t,q,\dot q)\,dt
=\int\Lambda(t,q,t',q')\,d\alpha.
$$

Changing $\alpha$ changes how quickly the path is traced, but not the physical path or its action. The Euler–Lagrange equation for $q^i$ reproduces the usual one. If $p_i=\partial L/\partial\dot q^i$, then

$$
\frac{\partial\Lambda}{\partial q'^i}=p_i,
\qquad
\frac{\partial\Lambda}{\partial q^i}
=t'\frac{\partial L}{\partial q^i},
\qquad
\frac{d p_i}{d\alpha}=t'\frac{\partial L}{\partial q^i}.
$$

Since $d/d\alpha=t'\,d/dt$, the last relation is $dp_i/dt=\partial L/\partial q^i$.

The equation for the time coordinate gives the energy balance. Define the Lagrangian energy

$$
E_L=\sum_i p_i\dot q^i-L.
$$

Direct differentiation of $\Lambda$ yields

$$
\frac{\partial\Lambda}{\partial t}=t'\frac{\partial L}{\partial t},
\qquad
\frac{\partial\Lambda}{\partial t'}=-E_L.
$$

The Euler–Lagrange equation for $t$ therefore becomes

$$
\frac{dE_L}{dt}=-\frac{\partial L}{\partial t}.
$$

When the Lagrangian has no explicit time dependence, $E_L$ is conserved. For a regular Lagrangian this is the Hamiltonian; for the usual $T-V$ systems it is the mechanical energy. The lecture's central-force example uses spherical coordinates to show both the cyclic azimuth and this time-translation conservation in the extended description. The ordinary polar-coordinate calculation in Chapter 7 is easier for finding an orbit; this formulation is useful for understanding how the choice of time parameter fits into the variational picture.

## 16.7 What to remember

- Hamilton's principal function solves $\partial S/\partial t+H(q,\partial S/\partial q,t)=0$.
- For a time-independent Hamiltonian, $S=W-Et$ reduces the equation to an energy relation for $W$.
- Separation of variables reuses conserved quantities such as angular momentum to reduce the problem.
- Action variables are phase-space areas divided by $2\pi$; their conjugate angles advance uniformly for integrable motion.
- The oscillator has $J=E/\omega$ and a uniformly increasing phase angle.
- Physical-space GA and phase-space action variables describe related but distinct geometric structures.

### Exercises

1. Substitute $S=W-Et$ into the Hamilton–Jacobi equation and derive the time-independent equation.
2. For a one-dimensional particle with $H=p^2/(2m)+U(q)$, write the integral for $W(q;E)$.
3. For a central potential, show how setting $W=W_r(r)+L\theta$ reduces the Hamilton–Jacobi equation to radial motion.
4. Use the area of the harmonic oscillator's phase-space ellipse to derive $J=E/\omega$.
5. Explain what it means for conserved quantities to be in involution.
6. Distinguish the physical orbital-plane bivector from the symplectic area used to define an action variable.
7. **Synthesis.** For a central potential $U(r)$, use $W(r,\theta)=W_r(r)+L\theta$ to derive the radial momentum as a function of $r$ and $E$. Find the turning points from that expression and explain how the same effective potential appears in Chapter 7.
8. In the extended formulation, verify that $\partial\Lambda/\partial t'=-E_L$. Explain why the equation for the time coordinate makes $E_L$ constant when $L$ has no explicit time dependence.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on Hamilton–Jacobi theory and action-angle variables.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for separability and integrable systems.
- V. I. Arnold, *Mathematical Methods of Classical Mechanics*, for action-angle variables and invariant tori.
- H. Krüger, *Vorlesung Mechanik*, Winter Semester 1996–97, unpublished lecture notes (private copy); see the extended-time formulation.
