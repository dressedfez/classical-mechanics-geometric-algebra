---
title: "10. Rigid-Body Dynamics"
description: "Use torque and inertia to study free rigid-body rotation, principal-axis stability, and the motion of gyroscopes."
---

Knowing a body's inertia and orientation is not enough to predict its motion; we also need to know how torque changes its angular momentum. A rigid body can rotate in ways that are surprising even when no external torque acts. In particular, steady rotation about the axis with an intermediate principal moment is unstable, while rotation about the largest or smallest moment is stable.

We develop the body-frame equations that explain this behaviour, then use them to understand a spinning top. The calculations are most transparent in the conventional vector and principal-axis notation. Geometric algebra remains useful for following the body's orientation and for describing angular momentum as an oriented plane.

## 10.1 Angular momentum and torque

For a body rotating about its centre of mass, the total angular momentum bivector is

$$
\mathcal J=\int \mathbf r\wedge\mathbf v\,dm,
$$

and the net torque bivector is

$$
\mathcal T=\int \mathbf r\wedge d\mathbf F.
$$

The angular form of Newton's second law is

$$
\left(\frac{d\mathcal J}{dt}\right)_{\!I}=\mathcal T,
$$

where the derivative is taken in inertial axes. In three-dimensional vector notation this is $d\mathbf L/dt=\boldsymbol\tau$. A torque-free body conserves its angular momentum in space, but its angular velocity need not remain fixed in the body.

Let $Q(t)$ describe body orientation and let $\mathbf L_b$ be angular momentum components in body-fixed axes. Applying the transport theorem to a body-fixed vector gives

$$
\left(\frac{d\mathbf L}{dt}\right)_{\!I}
=Q\left(\dot{\mathbf L}_b+\boldsymbol\omega_b\times\mathbf L_b\right)\widetilde Q.
$$

Thus the body-frame equation is

$$
\boldsymbol\tau_b=\dot{\mathbf L}_b+\boldsymbol\omega_b\times\mathbf L_b.
$$

The extra term can be derived by differentiating the inertial vector directly. Write $\mathbf L=Q\mathbf L_b\widetilde Q$ and use $\dot Q=-\tfrac12\boldsymbol\Omega Q$ and $\dot{\widetilde Q}=\tfrac12\widetilde Q\boldsymbol\Omega$. The product rule gives

$$
\dot{\mathbf L}=Q\dot{\mathbf L}_b\widetilde Q+
\frac{1}{2}(\mathbf L\boldsymbol\Omega-\boldsymbol\Omega\mathbf L).
$$

The commutator term is the vector $\boldsymbol\omega\times\mathbf L$. It accounts for the change of the body axes themselves, so the rotating-frame correction is required even when no physical torque acts.

## 10.2 Euler's equations

Choose body-fixed principal axes, so $\mathbf L_b=\mathsf I\boldsymbol\omega_b$ with diagonal inertia matrix. Writing components gives **Euler's equations**:

$$
\begin{aligned}
I_1\dot\omega_1+(I_3-I_2)\omega_2\omega_3&=\tau_1,\\
I_2\dot\omega_2+(I_1-I_3)\omega_3\omega_1&=\tau_2,\\
I_3\dot\omega_3+(I_2-I_1)\omega_1\omega_2&=\tau_3.
\end{aligned}
$$

For example, the first component of $\boldsymbol\omega_b\times\mathbf L_b$ is $\omega_2 I_3\omega_3-\omega_3 I_2\omega_2=(I_3-I_2)\omega_2\omega_3$; the other two components follow by cycling the indices. The equations couple the angular-velocity components even when the applied torque is zero. They express the fact that angular momentum and angular velocity point in the same direction only when the body rotates about a principal axis or has suitable symmetry.

## 10.3 Torque-free rotation and the intermediate-axis instability

With no external torque, both the inertial angular momentum and rotational kinetic energy are constant:

$$
\mathbf L^2=\text{constant},
\qquad
T=\frac{1}{2}(I_1\omega_1^2+I_2\omega_2^2+I_3\omega_3^2)=\text{constant}.
$$

Suppose $I_1<I_2<I_3$. Consider steady rotation about the second principal axis, $\omega_2=\Omega$ and $\omega_1=\omega_3=0$. To test its stability, add small components $\delta\omega_1$ and $\delta\omega_3$. Linearizing Euler's equations yields

$$
I_1\dot{\delta\omega}_1+(I_3-I_2)\Omega\,\delta\omega_3=0,
\qquad
I_3\dot{\delta\omega}_3+(I_2-I_1)\Omega\,\delta\omega_1=0.
$$

Combining them gives

$$
\ddot{\delta\omega}_1=
\frac{(I_3-I_2)(I_2-I_1)}{I_1I_3}\,\Omega^2\delta\omega_1.
$$

To see the time dependence, call the positive coefficient $\lambda^2$. The solutions are $\delta\omega_1=Ae^{\lambda t}+Be^{-\lambda t}$, with $\delta\omega_3$ fixed by the first linearized equation. A generic small disturbance contains a growing part, so the intermediate-axis rotation is unstable. If instead the steady rotation is about axis 1, the corresponding second-order equation has a negative coefficient,

$$
\ddot{\delta\omega}_2=-\frac{(I_2-I_1)(I_3-I_1)}{I_2I_3}\,\Omega^2\delta\omega_2,
$$

and perturbations oscillate. Rotation about axis 3 is likewise stable to small disturbances. This is the **intermediate-axis theorem**, sometimes demonstrated by tossing a book or a tennis racket. The linear analysis predicts behaviour only while the disturbance stays small; it does not give the full tumbling motion.

The instability does not violate angular-momentum conservation. The angular momentum is fixed in space, but the body's orientation changes relative to it. The body-frame components can therefore evolve even though the inertial vector is constant.

## 10.4 Symmetric tops

A symmetric top has $I_1=I_2=I_\perp$ and $I_3$ about its symmetry axis. A torque-free top has a particularly simple structure: its angular momentum is constant in space, while its symmetry axis generally precesses around that fixed vector. A rapidly spinning top has angular momentum dominated by its spin component along the symmetry axis.

When gravity acts on a top supported at a point a distance $\ell$ from its centre of mass, the torque magnitude is

$$
\tau=M g\ell\sin\theta,
$$

where $M$ is the top's mass and $\theta$ is the angle between its symmetry axis and the vertical. For a rapidly spinning top, take $L\approx I_3\omega_3$ along the symmetry axis. The relation $d\mathbf L/dt=\boldsymbol\tau$ then gives the approximate steady precession rate

$$
\Omega_p\approx\frac{\tau}{L\sin\theta}
=\frac{M g\ell}{I_3\omega_3}.
$$

During a small precession angle $d\phi$, the tip of $\mathbf L$ moves along a circle of radius $L\sin\theta$, so $|d\mathbf L|/dt=L\sin\theta\,\dot\phi$. Equating this rate to the gravitational torque $Mg\ell\sin\theta$ gives the estimate above. This vector argument also explains why the torque changes the direction of the large spin angular momentum rather than substantially changing its magnitude.

The top precesses more slowly when it spins faster. This approximation assumes the spin is large compared with the precession rate and neglects the small nutation that can accompany the motion. A complete symmetric-top solution has two angular motions and is better treated with Euler angles or the Lagrangian method.

### Worked estimate: a rapidly spinning top

Take a top with mass $M=0.40\,\mathrm{kg}$, centre of mass $\ell=0.080\,\mathrm m$ from the pivot, symmetry-axis moment $I_3=1.2\times10^{-3}\,\mathrm{kg\,m^2}$, and spin $\omega_3=100\,\mathrm{rad\,s^{-1}}$. With $g=9.81\,\mathrm{m\,s^{-2}}$, the approximate precession rate is

$$
\Omega_p\approx\frac{(0.40)(9.81)(0.080)}{(1.2\times10^{-3})(100)}
=2.62\,\mathrm{rad\,s^{-1}}.
$$

The estimate is independent of the tilt angle because both the gravitational torque and the rate at which the angular-momentum direction turns contain the same factor $\sin\theta$. The assumed spin angular momentum is $I_3\omega_3=0.12\,\mathrm{kg\,m^2\,s^{-1}}$; the approximate precession is much slower than the $100\,\mathrm{rad\,s^{-1}}$ spin, as required. If the initial conditions excite appreciable nutation, or the spin is not dominant, the full symmetric-top equations are needed.

## 10.5 A geometric-algebra view of orientation

The body's orientation rotor acts on each body-fixed vector, $\mathbf r=Q\boldsymbol\rho\widetilde Q$. Angular velocity is a bivector, and torque changes the angular-momentum bivector. In an inertial frame the concise law is $\dot{\mathcal J}=\mathcal T$; in a body frame, the rotating axes require the transport correction that produced Euler's equations.

This separation is valuable: a rotor keeps orientation updates geometrically valid, while the inertia matrix and Euler equations provide efficient component dynamics. The GA notation does not remove the need to solve the nonlinear coupled equations. Numerical integration is often required for a general asymmetric body; Chapter 17 returns to that task and shows why preserving geometric structure matters.

## 10.6 What to remember

- Torque is the inertial time derivative of angular momentum; a torque-free rigid body's angular momentum is fixed in space.
- Body-frame derivatives include a transport term $\boldsymbol\omega\times\mathbf L$.
- Euler's equations couple angular-velocity components through the principal moments.
- Torque-free rotation about the largest or smallest principal moment is stable; rotation about the intermediate moment is unstable.
- A rapidly spinning top precesses at an approximate rate inversely proportional to its spin angular momentum.
- Rotors track orientation, while inertia matrices and component equations remain practical calculation tools.

### Exercises

1. For a torque-free body, explain why $\mathbf L$ can be constant in inertial space while its body-frame components change.
2. A rigid body has $I_1<I_2<I_3$. Use the linearized equations to explain why a small disturbance to rotation about axis 2 grows.
3. A top has mass $0.40\,\mathrm{kg}$, centre-of-mass distance $0.080\,\mathrm m$ from its pivot, $I_3=1.2\times10^{-3}\,\mathrm{kg\,m^2}$, and spin $100\,\mathrm{rad\,s^{-1}}$. Estimate its steady precession rate using $g=9.81\,\mathrm{m\,s^{-2}}$.
4. State the assumptions behind the fast-top precession formula. Why does the precession slow when the spin increases?
5. Describe what the orientation rotor does during a numerical simulation of a rigid body's motion.
6. **Synthesis.** Starting from Euler's equations, linearize torque-free motion about each principal axis for $I_1<I_2<I_3$. Show which two perturbations oscillate and which grows exponentially, and explain why this does not contradict conservation of inertial angular momentum.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on Euler's equations and the spinning top.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for rigid-body dynamics and the asymmetric top.
- David Hestenes, *New Foundations for Classical Mechanics*, for geometric-algebra treatments of angular momentum and rotation.
