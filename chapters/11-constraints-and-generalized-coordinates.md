---
title: "11. Constraints and Generalized Coordinates"
description: "Describe constrained motion with generalized coordinates, virtual work, d'Alembert's principle, and Lagrange's equations, using geometric algebra to clarify the geometry of allowed motion."
---

Newton's laws apply to constrained systems, but a direct calculation can require many unknown constraint forces. A pendulum bob, for example, is pulled by gravity and by the string tension. If we want only its angular motion, solving first for the tension is unnecessary work. Lagrangian mechanics provides a systematic way to choose coordinates that already respect the constraints.

Geometric algebra (GA) has a focused role in this chapter. It helps us describe positions, tangent directions, and constraint surfaces without tying the geometry to a particular component basis. The virtual-work and Lagrange equations themselves remain ordinary scalar mechanics. This distinction will let us see what GA contributes without changing a clear derivation just for the sake of new notation.

## 11.1 Why introduce generalized coordinates?

Consider a bob attached to a light, inextensible string of length $\ell$. If we describe its position in a plane by Cartesian coordinates $(x,y)$, the string imposes

$$
x^2+y^2=\ell^2.
$$

The two coordinates cannot vary independently. Newton's second law also includes the tension, whose direction changes as the bob moves. We can solve for both the angle and tension, but if our main goal is to find the motion, the tension is an extra unknown.

Instead, describe the bob by one coordinate, its angle $\theta$. The length constraint is then satisfied by the way we define the position. The equation of motion will involve $\theta$ alone, and the tension need not be calculated unless we specifically want it. This is the basic strategy of generalized coordinates: choose variables that describe the allowed configurations directly.

The same idea applies to systems with many particles. A collection of connected masses may have many Cartesian coordinates but only a few independent ways to move. Choosing coordinates adapted to those possibilities can eliminate constraint forces and reduce the number of equations.

## 11.2 Configuration space and constraints

A **configuration** specifies the positions of all particles in a system at one instant. For $N$ particles in ordinary three-dimensional space, their Cartesian positions require $3N$ numbers. Constraints restrict which combinations of those numbers are possible. If there are $k$ independent constraints, the system typically has $n=3N-k$ degrees of freedom, provided the constraints are regular in the region being considered.

We call the set of allowed configurations the **configuration space**. It is not generally the same space as the physical space in which the particles move. A pendulum bob moves in a two-dimensional plane, but its allowed configurations form a circle, which has one degree of freedom. Two connected particles may each move in physical three-dimensional space while their combined system has only one independent coordinate.

We label the independent coordinates by

$$
q^1,q^2,\ldots,q^n.
$$

These are called **generalized coordinates**. They need not be lengths: they may be angles, distances, or any convenient parameters that uniquely describe the configurations in the range of interest. The position of particle $a$ can then be written as a function of them:

$$
\mathbf r_a=\mathbf r_a(q^1,\ldots,q^n).
$$

A constraint that can be written as an equation among positions and time, such as $f(\mathbf r_1,\ldots,\mathbf r_N,t)=0$, is called **holonomic**. A fixed-length pendulum is holonomic. The main derivation will use constraints that do not move explicitly with time; Section 11.9 returns to a simple moving constraint and shows what changes.

## 11.3 Mathematical tools: the geometry of allowed motion

For a small change in the coordinates, the change in particle $a$'s position is

$$
d\mathbf r_a=\sum_i\frac{\partial\mathbf r_a}{\partial q^i}\,dq^i.
$$

The vectors $\partial\mathbf r_a/\partial q^i$ point in the directions in which the particle moves when one coordinate changes and the others are held fixed. They are tangent directions to the allowed configurations. The velocity follows by taking $dq^i=\dot q^i dt$:

$$
\mathbf v_a=\dot{\mathbf r}_a
=\sum_i\frac{\partial\mathbf r_a}{\partial q^i}\,\dot q^i.
$$

This is ordinary differentiation of a vector-valued function. GA keeps the positions and tangent directions as geometric vectors; it does not require a new kind of derivative.

For a constraint surface described by $f(\mathbf r)=0$, the gradient $\boldsymbol\nabla f$ is perpendicular to the surface wherever it is nonzero. A permitted displacement tangent to the surface therefore obeys

$$
\boldsymbol\nabla f\cdot\delta\mathbf r=0.
$$

For the pendulum, the fixed-length condition has a particularly simple GA form. A vector squared is its geometric product with itself, which is the scalar squared length:

$$
\mathbf r^2=\mathbf r\mathbf r=\ell^2.
$$

Differentiating with respect to time and using the product rule gives

$$
\frac{d}{dt}(\mathbf r^2)
=\dot{\mathbf r}\,\mathbf r+\mathbf r\,\dot{\mathbf r}
=2\,\mathbf r\cdot\dot{\mathbf r}=0.
$$

Thus $\mathbf r\cdot\dot{\mathbf r}=0$: the velocity is tangent to the circle, as the fixed-length constraint requires. The same reasoning for a permitted virtual displacement gives $\mathbf r\cdot\delta\mathbf r=0$. Here the geometric product helps by packaging the length constraint and its derivative in a compact way; the result is the familiar statement that radial and tangent directions are perpendicular.

{numref}`fig-pendulum-constraint` shows the position vector, the allowed tangent direction, and the forces on the bob. The string tension is radial, whereas a change in the angle moves the bob along the tangent.

```{figure} ../figures/pendulum-constraint.svg
:label: fig-pendulum-constraint
:enumerator: "11.1"
:alt: A pendulum bob with its radius vector, vertical reference, tangent direction, gravity, and string tension.
:width: 75%

At a fixed instant, the bob can move virtually only along the tangent to its circular path. The tension is perpendicular to that allowed displacement.
```

If we reuse the rotor $R$ introduced for rotations, we can also describe the bob's position as $\mathbf r=R\mathbf r_0\widetilde R$, where $\mathbf r_0$ is a fixed vector of length $\ell$ and $\widetilde R$ is the reverse of the unit rotor. A rotor preserves lengths, so this parametrization builds the pendulum constraint in automatically. The angle $\theta$ is still the simpler coordinate for deriving the equation of motion; the rotor is a useful geometric description, not a replacement for that calculation.

The kinetic energy also reveals a connection between physical geometry and generalized coordinates. Substituting the velocity expression into $T=\tfrac12\sum_a m_a\mathbf v_a^2$ gives

$$
T=\frac{1}{2}\sum_{i,j}g_{ij}(q)\,\dot q^i\dot q^j,
\qquad
g_{ij}(q)=\sum_a m_a\frac{\partial\mathbf r_a}{\partial q^i}\cdot\frac{\partial\mathbf r_a}{\partial q^j}.
$$

The numbers $g_{ij}$ form the mass matrix, also called the kinetic-energy metric in these coordinates. GA contributes the ordinary Euclidean inner products of the physical tangent vectors. For calculations with several coordinates, the matrix $g_{ij}$ is the clearest way to organize the resulting equations.

## 11.4 Virtual work and generalized forces

A **virtual displacement** $\delta\mathbf r_a$ is an imagined infinitesimal change from the current configuration that is compatible with the constraints, considered at the same instant. It is not the displacement that actually occurs during a time interval. A virtual displacement helps us compare forces along the directions the system is allowed to move.

The **virtual work** of the applied forces is

$$
\delta W_{\mathrm{app}}
=\sum_a\mathbf F_a^{\mathrm{app}}\cdot\delta\mathbf r_a.
$$

Since $\delta\mathbf r_a=\sum_i(\partial\mathbf r_a/\partial q^i)\delta q^i$, we can collect the coefficient of each independent coordinate variation:

$$
\delta W_{\mathrm{app}}=\sum_i Q_i\,\delta q^i,
\qquad
Q_i=\sum_a\mathbf F_a^{\mathrm{app}}\cdot\frac{\partial\mathbf r_a}{\partial q^i}.
$$

The quantity $Q_i$ is the **generalized force** associated with $q^i$. It measures how strongly the applied forces act along the motion produced by a change in that coordinate. For a length coordinate it has units of force; for an angular coordinate it has units of energy per radian. The inner product is the direct bridge from the ordinary force vectors in physical space to the scalar equations in generalized coordinates.

For a smooth, frictionless surface, the contact force is normal to the surface while every allowed virtual displacement is tangent to it. Their dot product is zero. More generally, we call constraints **ideal** when the combined constraint forces do no virtual work:

$$
\sum_a\mathbf R_a\cdot\delta\mathbf r_a=0.
$$

This condition is satisfied by many familiar constraints, such as ideal strings and frictionless supports. It is an assumption about the constraint forces; it is not true of every physical contact, especially when friction acts along the allowed motion.

## 11.5 d'Alembert's principle and Lagrange's equations

Newton's second law for particle $a$ can be written as

$$
\mathbf F_a^{\mathrm{app}}+\mathbf R_a=m_a\ddot{\mathbf r}_a,
$$

where $\mathbf R_a$ is the constraint force. Rearranging and taking the dot product with an allowed virtual displacement, then summing over the particles, gives **d'Alembert's principle**:

```{note} d'Alembert's principle

For an ideal constrained system, the applied, constraint, and inertial forces satisfy

$$
\sum_a\left(\mathbf F_a^{\mathrm{app}}+\mathbf R_a-m_a\ddot{\mathbf r}_a\right)\cdot\delta\mathbf r_a=0.
$$

Because ideal constraint forces do no virtual work, their terms vanish in this sum.
```

Using $\delta\mathbf r_a=\sum_i(\partial\mathbf r_a/\partial q^i)\delta q^i$ and the ideal-constraint condition, we obtain

$$
\sum_i\left[
Q_i-\sum_a m_a\ddot{\mathbf r}_a\cdot\frac{\partial\mathbf r_a}{\partial q^i}
\right]\delta q^i=0.
$$

The generalized coordinate variations are independent, so the coefficient of each $\delta q^i$ must vanish. We now express the inertial term using the kinetic energy. For fixed constraints, the position $\mathbf r_a$ depends on $q^i$ but not explicitly on time, and

$$
T=\frac{1}{2}\sum_a m_a\dot{\mathbf r}_a^2.
$$

Differentiation gives

$$
\frac{\partial T}{\partial\dot q^i}
=\sum_a m_a\dot{\mathbf r}_a\cdot\frac{\partial\mathbf r_a}{\partial q^i}.
$$

Taking its time derivative and subtracting $\partial T/\partial q^i$ cancels the terms that differentiate the coordinate tangent vectors. Explicitly,

$$
\frac{d}{dt}\left(\frac{\partial T}{\partial\dot q^i}\right)
=\sum_a m_a\ddot{\mathbf r}_a\cdot\frac{\partial\mathbf r_a}{\partial q^i}
+\sum_{a,j}m_a\dot{\mathbf r}_a\cdot
\frac{\partial^2\mathbf r_a}{\partial q^j\partial q^i}\,\dot q^j,
\qquad
\frac{\partial T}{\partial q^i}
=\sum_{a,j}m_a\dot{\mathbf r}_a\cdot
\frac{\partial^2\mathbf r_a}{\partial q^i\partial q^j}\,\dot q^j.
$$

The mixed derivatives agree for a smooth position map, so the second sums cancel. We obtain

$$
\frac{d}{dt}\left(\frac{\partial T}{\partial\dot q^i}\right)
-\frac{\partial T}{\partial q^i}
=\sum_a m_a\ddot{\mathbf r}_a\cdot\frac{\partial\mathbf r_a}{\partial q^i}.
$$

Therefore d'Alembert's principle becomes

```{note} Lagrange's equations with generalized forces

For each independent generalized coordinate,

$$
\frac{d}{dt}\left(\frac{\partial T}{\partial\dot q^i}\right)
-\frac{\partial T}{\partial q^i}=Q_i.
$$

Here $Q_i$ is the generalized force from the applied forces. Ideal constraint forces have been eliminated.
```

If the applied forces are conservative, they can be derived from a potential energy $U(q)$, and $Q_i=-\partial U/\partial q^i$. Define the **Lagrangian** $L=T-U$. The equations then take their familiar form:

$$
\frac{d}{dt}\left(\frac{\partial L}{\partial\dot q^i}\right)
-\frac{\partial L}{\partial q^i}=0.
$$

If nonconservative applied forces are also present, their generalized components appear on the right-hand side:

$$
\frac{d}{dt}\left(\frac{\partial L}{\partial\dot q^i}\right)
-\frac{\partial L}{\partial q^i}=Q_i^{\mathrm{nc}}.
$$

This derivation used Newton's laws and virtual work, not Hamilton's principle. In Chapter 12 we will derive the same equations from the principle of stationary action and study how symmetry leads to conservation laws.

## 11.6 Worked example: the simple pendulum

A bob of mass $m$ hangs from a fixed pivot on a light string of length $\ell$. Let $\theta$ be measured from the downward vertical, so $\theta=0$ at the lowest point. Choose perpendicular unit vectors $\mathbf e_1$ horizontally to the right and $\mathbf e_2$ vertically upward. The position is

$$
\mathbf r(\theta)=\ell\left(\sin\theta\,\mathbf e_1-\cos\theta\,\mathbf e_2\right).
$$

Its square is $\mathbf r^2=\ell^2$, so the length constraint is satisfied for every value of $\theta$. Differentiating gives

$$
\frac{\partial\mathbf r}{\partial\theta}
=\ell\left(\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2\right),
\qquad
\dot{\mathbf r}=\frac{\partial\mathbf r}{\partial\theta}\,\dot\theta.
$$

The coordinate tangent vector is perpendicular to $\mathbf r$ and has length $\ell$. Thus

$$
\dot{\mathbf r}^{\,2}=\ell^2\dot\theta^2,
\qquad
T=\frac{1}{2}m\ell^2\dot\theta^2.
$$

The gravitational potential energy, chosen to be zero at the bottom, is

$$
U=mg\ell(1-\cos\theta).
$$

The Lagrangian is

$$
L=\frac{1}{2}m\ell^2\dot\theta^2-mg\ell(1-\cos\theta).
$$

The two derivatives needed in Lagrange's equation are

$$
\frac{\partial L}{\partial\dot\theta}=m\ell^2\dot\theta,
\qquad
\frac{\partial L}{\partial\theta}=-mg\ell\sin\theta.
$$

Consequently,

$$
m\ell^2\ddot\theta+mg\ell\sin\theta=0,
\qquad
\ddot\theta+\frac{g}{\ell}\sin\theta=0.
$$

The tension does not appear. It is directed along the string, perpendicular to every allowed virtual displacement, so its virtual work is zero. If we want the tension afterward, we can substitute this angular motion into Newton's radial equation.

The GA description makes the tangent direction especially compact. In the plane let $\mathbf I=\mathbf e_1\mathbf e_2$, with $\mathbf I^2=-1$. Because the pendulum's position lies in this plane,

$$
\frac{\partial\mathbf r}{\partial\theta}=\mathbf r\mathbf I.
$$

Right multiplication by the plane bivector turns the radius vector into the tangent vector. The kinetic energy and equation of motion are still easiest to calculate as above; GA makes the relation between radial and tangent directions explicit without changing the scalar Lagrange calculation.

We can also find the generalized gravitational force directly. Since $\mathbf F_g=-mg\mathbf e_2$,

$$
Q_\theta=\mathbf F_g\cdot\frac{\partial\mathbf r}{\partial\theta}
=-mg\ell\sin\theta.
$$

This agrees with $Q_\theta=-\partial U/\partial\theta$. The tension contributes zero because $\mathbf T$ is parallel to $\mathbf r$ while $\partial\mathbf r/\partial\theta$ is perpendicular to $\mathbf r$.

## 11.7 Worked example: two masses connected by a string

Two masses $m_1$ and $m_2$ hang on opposite sides of a light string passing over an ideal, frictionless pulley. Choose one coordinate $q$: positive $q$ moves $m_2$ downward and $m_1$ upward. If vertical position is measured upward, their positions can be written

$$
y_1=y_{1,0}+q,
\qquad
y_2=y_{2,0}-q.
$$

The string constraint is already built into these expressions. Their speeds have equal magnitude, $|\dot q|$, so the kinetic energy is

$$
T=\frac{1}{2}m_1\dot q^2+\frac{1}{2}m_2\dot q^2
=\frac{1}{2}(m_1+m_2)\dot q^2.
$$

The potential energy is

$$
U=m_1gy_1+m_2gy_2
=\text{constant}+(m_1-m_2)gq.
$$

Discarding the irrelevant constant, the Lagrangian is

$$
L=\frac{1}{2}(m_1+m_2)\dot q^2-(m_1-m_2)gq.
$$

Lagrange's equation gives

$$
(m_1+m_2)\ddot q=(m_2-m_1)g,
\qquad
\ddot q=\frac{m_2-m_1}{m_1+m_2}g.
$$

For $m_1=2.0\,\mathrm{kg}$ and $m_2=3.0\,\mathrm{kg}$, the acceleration is $g/5\approx1.96\,\mathrm{m\,s^{-2}}$, with $m_2$ moving downward. The string tension is absent because its upward force on $m_1$ and its upward force on $m_2$ do equal and opposite virtual work for the chosen coordinate. Newton's method can find the same result, but it requires writing one equation for each mass and solving for the tension as an additional unknown.

```{figure} ../figures/atwood-constraint.svg
:label: fig-atwood-constraint
:enumerator: "11.2"
:alt: Two masses connected by a string over a pulley, with one generalized coordinate q describing their linked motion.
:width: 65%

The inextensible string restricts the two masses to one independent coordinate. Choosing $q$ along the string builds that constraint into their positions.
```

In the generalized-coordinate language, the effective mass coefficient is $g_{qq}=m_1+m_2$: both masses contribute to the inertia associated with changing $q$. This is the same mass matrix formula from Section 11.3, here reduced to a single coordinate.

## 11.8 An alternative: Lagrange multipliers

Choosing independent coordinates eliminates a constraint by building it into the position. Another method keeps redundant coordinates and adds one multiplier for each constraint. This is useful when solving a constraint explicitly for independent coordinates is awkward, or when we also want the constraint force.

For the pendulum, keep Cartesian coordinates $(x,y)$ and impose $x^2+y^2=\ell^2$. With $y$ measured upward, the Lagrangian with a multiplier is

$$
\widetilde L
=\frac{1}{2}m(\dot x^2+\dot y^2)-mgy
+\frac{\lambda(t)}{2}(x^2+y^2-\ell^2).
$$

The Euler–Lagrange equations, together with the constraint, are

$$
m\ddot x=\lambda(t)x,
\qquad
m\ddot y+mg=\lambda(t)y,
\qquad
x^2+y^2=\ell^2.
$$

The multiplier term supplies the reaction force $\mathbf R=\lambda(t)\mathbf r$. It is normal to the circle because the gradient of $\tfrac12(\mathbf r^2-\ell^2)$ is $\mathbf r$. With this sign convention, a tension directed inward has $\lambda(t)<0$ and magnitude $T=|\lambda(t)|\ell$. Eliminating the constraint with the angle $\theta$ gave the same motion without this extra unknown; retaining $(x,y)$ and $\lambda(t)$ also lets us recover the reaction force directly. The sign of $\lambda$ depends on the sign convention used in the augmented Lagrangian.

For several constraints $\phi_\alpha(\mathbf r_1,\ldots,\mathbf r_N,t)=0$, add $\sum_\alpha\lambda_\alpha\phi_\alpha$ to the Lagrangian while retaining the particle positions as coordinates. The reaction on particle $a$ is then a sum of constraint normals,

$$
\mathbf R_a=\sum_\alpha\lambda_\alpha\nabla_{\mathbf r_a}\phi_\alpha.
$$

Coordinate elimination and multipliers are complementary choices: the first reduces the number of variables, while the second keeps the original coordinates and makes reaction forces available.

## 11.9 A constraint that moves

For a moving holonomic constraint, a position map may depend explicitly on time, $\mathbf r=\mathbf r(q,t)$. The actual velocity then contains both the motion along the allowed curve and the motion of the curve itself:

$$
\dot{\mathbf r}
=\sum_i\frac{\partial\mathbf r}{\partial q^i}\dot q^i
+\frac{\partial\mathbf r}{\partial t}.
$$

If the constraint is $f(\mathbf r,t)=0$, differentiating it along the actual motion gives

$$
\boldsymbol\nabla f\cdot\dot{\mathbf r}+\frac{\partial f}{\partial t}=0.
$$

A virtual displacement is still defined at one instant, so time is held fixed and

$$
\boldsymbol\nabla f\cdot\delta\mathbf r=0.
$$

These equations express different facts: the actual velocity follows a constraint that may itself move, while the virtual displacement points along the constraint's instantaneous allowed directions.

```{note} Example: a bead on a translating wire

Let a straight vertical wire translate horizontally with prescribed position $s(t)$. A bead on it has position

$$
\mathbf r(t,y)=s(t)\,\mathbf e_1+y\,\mathbf e_2,
$$

so its actual velocity and virtual displacement are

$$
\dot{\mathbf r}=\dot s\,\mathbf e_1+\dot y\,\mathbf e_2,
\qquad
\delta\mathbf r=\delta y\,\mathbf e_2.
$$

The wire's normal reaction is horizontal and does no virtual work. If there are no other horizontal forces, it is $\mathbf R=m\ddot s\,\mathbf e_1$; its power on the bead is $\mathbf R\cdot\dot{\mathbf r}=m\ddot s\,\dot s$, which changes the bead's horizontal kinetic energy as the support accelerates. In generalized coordinates, substitute $\mathbf r(q,t)$ into the kinetic and potential energies and use the usual Lagrange equations with their explicit time dependence. Energy need not be conserved when the constraint moves.
```

This extension explains why the main examples assumed fixed constraints: the geometry of allowed virtual motion is unchanged in spirit, but the actual velocity and energy balance now include the motion of the constraint.

## 11.10 When each description is useful

Eliminating constraints with generalized coordinates is especially effective when the constraint forces are not the quantities we seek. Lagrange multipliers are useful when we want to keep redundant coordinates or calculate those forces. Both methods avoid solving a separate Newton equation for every coordinate and reaction force.

Newton's laws remain more direct when a problem asks for a particular contact force, when collisions and impulses dominate, or when the constraints are difficult to encode as coordinates. Lagrangian mechanics does not remove the need to understand forces; it organizes their work along the allowed motions.

GA is useful here for positions, tangent directions, constraint normals, and the inner products that define virtual work and kinetic energy. It can also reuse rotors to represent rotations while preserving lengths and angles. The coordinate derivatives, generalized forces, and Lagrange equations are already clear in ordinary notation, so we keep them there. The configuration-space mass matrix is still a matrix, and no bivector product is needed in the main derivation. Chapter 12 will turn to action and symmetry, where the relation between rotational symmetry and bivector angular momentum becomes relevant.

## 11.11 What to remember

- Generalized coordinates describe only the independent ways a constrained system can move.
- A virtual displacement is an allowed infinitesimal change at a fixed time; it is not an actual displacement over time.
- The vectors $\partial\mathbf r_a/\partial q^i$ are tangent to the allowed motions, and inner products project physical forces onto these coordinate directions.
- Ideal constraint forces do no virtual work and therefore disappear from d'Alembert's equations.
- Lagrange multipliers retain redundant coordinates and make the constraint forces available; adapted coordinates eliminate the constraints from the equations.
- For a moving constraint, the actual velocity includes the motion of the constraint, while virtual displacements remain tangent at fixed time.
- For conservative forces, Lagrange's equations follow from $L=T-U$; nonconservative generalized forces appear on the right-hand side.
- GA can clarify the geometry of positions and constraints, while ordinary calculus and matrices remain effective for deriving and solving the coordinate equations.

### Exercises

1. A bead slides without friction on a circular wire of radius $R$. Choose an angle as a generalized coordinate. Write its position vector, verify the constraint, and find the tangent vector $\partial\mathbf r/\partial\theta$.
2. For the pendulum in Section 11.6, show directly that $\mathbf r\cdot\partial\mathbf r/\partial\theta=0$. Explain why this means the string tension does no virtual work.
3. A particle is constrained to the plane curve $y=x^2/a$, where $a$ is a positive length. Use $x$ as a generalized coordinate and write $d\mathbf r/dx$. What is the squared speed in terms of $\dot x$?
4. A mass $m$ moves on a frictionless horizontal table and is attached to a fixed-length string whose other end is at the origin. Use polar coordinates $(r,\theta)$ to write its kinetic energy. Which coordinate appears in the string constraint?
5. Two blocks of masses $m_1$ and $m_2$ are connected over an ideal pulley as in Section 11.7. Derive their acceleration using Newton's laws, including the tension, and compare the number of unknowns with the Lagrangian calculation.
6. In the two-mass system, calculate the generalized gravitational force $Q_q$ by summing $\mathbf F_a\cdot\partial\mathbf r_a/\partial q$. Check that it equals $-dU/dq$.
7. A pendulum bob has mass $0.50\,\mathrm{kg}$ and string length $0.80\,\mathrm{m}$. Find its angular acceleration when released from rest at $\theta=30^\circ$. State the direction of its initial motion.
8. A generalized coordinate $q$ measures length, while another coordinate $\phi$ is an angle. What are the units of their generalized forces? Explain from $\delta W=Q_i\delta q^i$.
9. A frictionless surface exerts a normal force on a particle. Explain why this force does no virtual work for displacements allowed by the surface, and distinguish virtual work from the work accumulated over a finite motion.
10. A bead is constrained to a sphere of radius $R$ in three-dimensional space. Write the fixed-length condition and show that any allowed velocity is perpendicular to the position vector. How many independent coordinates are needed locally?
11. Starting from the augmented pendulum Lagrangian in Section 11.8, derive the two Cartesian equations and identify the tension magnitude in terms of $\lambda$ and $\ell$.
12. For the translating wire in Section 11.9, verify that $\dot{\mathbf r}$ satisfies the time derivative of the constraint while $\delta\mathbf r$ satisfies the fixed-time virtual constraint. Show that the normal-force power is $d(\tfrac12m\dot s^2)/dt$.

## Further reading

- David Hestenes, [*New Foundations for Classical Mechanics*](https://davidhestenes.net/geocalc/html/NFCM.html), especially its treatments of conservative forces and constraints, Lagrange's method, and rigid-body mechanics.
- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), for a conventional undergraduate development of generalized coordinates and Lagrangian mechanics.
- H. Krüger, *Vorlesung Mechanik*, Winter Semester 1996–97, unpublished lecture notes (private copy), for the constraint geometry and multiplier formulation.
