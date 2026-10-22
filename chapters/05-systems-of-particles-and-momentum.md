---
title: "5. Systems of Particles and Momentum"
description: "Develop linear and angular momentum for systems of particles, collisions, and torque, using bivectors to represent angular momentum geometrically."
---

A collision can change the motion of each object dramatically while leaving the motion of the pair, taken together, almost unchanged. A spinning or orbiting particle presents a different question: how do we describe its motion around a chosen point? These two questions lead to linear momentum and angular momentum.

The first part of the chapter extends Newton's laws from one particle to a system. We will see why the centre of mass follows a simple equation even when the particles inside the system interact in complicated ways. The second part develops angular momentum and torque. Here geometric algebra gives us a useful change of viewpoint: angular momentum is naturally an oriented plane, represented by a bivector. The familiar three-dimensional cross product encodes the same information as a vector perpendicular to that plane.

## 5.1 Choosing a system

Before applying a conservation law, decide what objects belong to the **system**. The objects outside it make up the surroundings. A force exerted by the surroundings on the system is an **external force**. Forces that parts of the system exert on one another are **internal forces**.

The distinction depends on the system boundary. If we study one cart during a collision, the force from the other cart is external. If we study both carts together, that same interaction is internal. Internal forces can be large and can change the motion of each cart, even when they do not change the total momentum of the pair.

In this chapter, systems have fixed membership and constant total mass. We will also assume an inertial reference frame when applying Newton's laws.

## 5.2 Total momentum and the centre of mass

For particle $a$ of mass $m_a$, position $\mathbf r_a$, and velocity $\mathbf v_a$, the linear momentum is

$$
\mathbf p_a=m_a\mathbf v_a.
$$

The total momentum of $N$ particles is the vector sum

$$
\mathbf P=\sum_{a=1}^N\mathbf p_a.
$$

Newton's second law says that the rate of change of each particle's momentum is the net force on it. When we add these equations over the system, the internal forces cancel in equal-and-opposite pairs, as required by Newton's third law. The result is

$$
\frac{d\mathbf P}{dt}=\mathbf F_{\mathrm{ext}},
\qquad
\mathbf F_{\mathrm{ext}}=\sum_a\mathbf F_a^{\mathrm{ext}}.
$$

This equation does not say that every particle's momentum is constant. Internal forces can redistribute momentum among the particles. It says that the total momentum changes only through the net external force.

```{note} Conservation of linear momentum

If the net external force on a system is zero, its total linear momentum is constant:

$$
\mathbf F_{\mathrm{ext}}=\mathbf 0
\quad\Longrightarrow\quad
\mathbf P=\text{constant}.
$$
```

The **centre of mass** is the mass-weighted average position of the system. If $M=\sum_a m_a$ is its total mass, then

$$
\mathbf R_{\mathrm{cm}}=\frac{1}{M}\sum_a m_a\mathbf r_a.
$$

For fixed masses, differentiating gives the centre-of-mass velocity and acceleration:

$$
\mathbf V_{\mathrm{cm}}=\frac{1}{M}\sum_a m_a\mathbf v_a
=\frac{\mathbf P}{M},
\qquad
M\mathbf A_{\mathrm{cm}}=\mathbf F_{\mathrm{ext}}.
$$

So the centre of mass moves as if the system's entire mass were concentrated there and the net external force acted at that point. The particles may move around inside the system, but their internal interactions cannot accelerate the centre of mass of an isolated system.

### Worked example: locating a centre of mass

Two small masses lie on the $x$ axis. A $2.0\,\mathrm{kg}$ mass is at $x=-1.0\,\mathrm m$, and a $3.0\,\mathrm{kg}$ mass is at $x=2.0\,\mathrm m$. Their centre of mass is

$$
x_{\mathrm{cm}}
=\frac{(2.0\,\mathrm{kg})(-1.0\,\mathrm m)+(3.0\,\mathrm{kg})(2.0\,\mathrm m)}
{2.0\,\mathrm{kg}+3.0\,\mathrm{kg}}
=0.80\,\mathrm m.
$$

The centre lies closer to the heavier mass. It need not coincide with any material in the system. If the masses move while no net external force acts, this point continues at constant velocity even as their separation changes.

## 5.3 Impulse and collisions

A force acting over a time interval can produce a substantial change in momentum even if the interval is short. The **impulse** of a force is its time integral:

$$
\mathbf J=\int_{t_i}^{t_f}\mathbf F(t)\,dt.
$$

Integrating Newton's second law for one particle gives the impulse-momentum theorem,

$$
\mathbf J_{\mathrm{net}}=\Delta\mathbf p.
$$

For a system, the corresponding result is

$$
\Delta\mathbf P=\int_{t_i}^{t_f}\mathbf F_{\mathrm{ext}}\,dt.
$$

During a collision, the forces between the colliding objects may be very large. If the collision lasts a short time and the external impulse is small compared with the interaction impulse, we can approximate the system's total momentum as conserved during the collision.

```{note} Momentum in a collision

When the net external impulse on a system is negligible,

$$
\mathbf P_{\mathrm{before}}\approx\mathbf P_{\mathrm{after}}.
$$

This is a statement about the total momentum of the chosen system. It does not say that each object's momentum is unchanged.
```

Momentum conservation alone does not determine every final velocity. We also need information about the collision. In an **elastic collision**, total kinetic energy is conserved as well as momentum. In an **inelastic collision**, some kinetic energy is converted into internal energy, sound, or deformation. In a **perfectly inelastic collision**, the bodies remain joined after impact.

### Worked example: carts that stick together

A $2.0\,\mathrm{kg}$ cart moves to the right at $3.0\,\mathrm{m\,s^{-1}}$. It collides with a $1.0\,\mathrm{kg}$ cart moving left at $1.0\,\mathrm{m\,s^{-1}}$. They stick together. Take rightward as positive and neglect the external impulse during impact. Conservation of momentum gives

$$
(2.0)(3.0)+(1.0)(-1.0)=(2.0+1.0)v_f,
\qquad
v_f=\frac{5}{3}\,\mathrm{m\,s^{-1}}\approx1.7\,\mathrm{m\,s^{-1}}.
$$

The positive sign means that the joined carts move to the right. Their initial kinetic energy is

$$
K_i=\frac{1}{2}(2.0)(3.0)^2+\frac{1}{2}(1.0)(1.0)^2=9.5\,\mathrm J,
$$

whereas their final kinetic energy is

$$
K_f=\frac{1}{2}(3.0)\left(\frac{5}{3}\right)^2\,\mathrm J\approx4.2\,\mathrm J.
$$

The missing kinetic energy has not vanished. It has become internal energy, sound, and deformation. This is why momentum conservation applies to the collision while kinetic energy conservation does not.

## 5.4 Angular momentum of a particle

Linear momentum describes translation. To describe motion relative to a chosen origin $O$, take the particle's position vector $\mathbf r$ from that origin and form the outer product with its momentum:

$$
\mathcal J=\mathbf r\wedge\mathbf p.
$$

We call the bivector $\mathcal J$ the particle's **angular momentum about $O$**. The outer product records the oriented plane spanned by $\mathbf r$ and $\mathbf p$. Its magnitude is

$$
|\mathcal J|=|\mathbf r|\,|\mathbf p|\sin\theta,
$$

where $\theta$ is the angle between them. If momentum points directly toward or away from the origin, the two vectors are parallel and $\mathcal J=0$. If momentum is perpendicular to the position vector, the magnitude is largest for the given $|\mathbf r|$ and $|\mathbf p|$.

The parallelogram spanned by $\mathbf r$ and $\mathbf p$ is a geometric way to see both the magnitude and orientation of angular momentum. In three dimensions, the plane itself is the bivector; the familiar cross product describes the same plane by a perpendicular vector.

```{figure} ../figures/angular-momentum-bivector.svg
:label: fig-angular-momentum-bivector
:enumerator: "5.1"
:alt: Position and momentum span an oriented parallelogram; in three dimensions the same plane can be represented by a perpendicular axial vector.
:width: 85%

The outer product $\mathbf r\wedge\mathbf p$ records the oriented plane and the area of the parallelogram spanned by position and momentum. The ordinary three-dimensional angular-momentum vector points perpendicular to this plane and carries the same magnitude and orientation information once a spatial orientation is chosen.
```

In three-dimensional Euclidean space, choose a right-handed orthonormal basis and its unit pseudoscalar $\mathbf I=\mathbf e_1\mathbf e_2\mathbf e_3$. If the conventional axial vector is defined as $\mathbf L=\mathbf r\times\mathbf p$, then

$$
\mathcal J=\mathbf r\wedge\mathbf p=\mathbf I\mathbf L.
$$

For example, $\mathbf e_1\wedge\mathbf e_2=\mathbf e_1\mathbf e_2=\mathbf I\mathbf e_3$. Thus the cross product is a convenient three-dimensional representation of the bivector after a handed orientation has been chosen. The bivector representation keeps the plane and its orientation explicit, and it also works directly in two dimensions without introducing a vector that points outside the plane.

The origin matters. If we choose a different fixed origin displaced by $\mathbf a$, then $\mathbf r'=\mathbf r-\mathbf a$ and

$$
\mathcal J'=\mathbf r'\wedge\mathbf p
=\mathcal J-\mathbf a\wedge\mathbf p.
$$

Angular momentum is therefore defined **about an origin or axis**. In a three-dimensional calculation, this dependence is familiar from $\mathbf r\times\mathbf p$; the bivector formula makes it just as explicit.

## 5.5 Torque changes angular momentum

The **torque bivector** of a force $\mathbf F$ about the origin $O$ is

$$
\mathcal T=\mathbf r\wedge\mathbf F.
$$

In three dimensions, if the conventional torque vector is $\boldsymbol{\tau}=\mathbf r\times\mathbf F$, then $\mathcal T=\mathbf I\boldsymbol{\tau}$, using the same right-handed orientation as for angular momentum.

It measures the force's rotational effect about that origin. If the force acts along the line from the origin to the particle, the vectors span no area and the torque is zero. A perpendicular force has the greatest torque magnitude for a given position and force. More generally, the magnitude is $rF\sin\theta$, or the force times its perpendicular lever arm.

For a particle of constant mass, differentiate its angular momentum:

$$
\frac{d\mathcal J}{dt}
=\dot{\mathbf r}\wedge\mathbf p+\mathbf r\wedge\dot{\mathbf p}
=\mathbf v\wedge m\mathbf v+\mathbf r\wedge\mathbf F
=\mathbf r\wedge\mathbf F
=\mathcal T.
$$

The first term vanishes because a vector's outer product with itself is zero. This is the angular form of Newton's second law: torque changes angular momentum.

```{note} Angular impulse and conservation

The time integral of torque is the change in angular momentum:

$$
\int_{t_i}^{t_f}\mathcal T\,dt=\Delta\mathcal J.
$$

If the net torque about the chosen origin is zero, angular momentum about that origin is constant.
```

### Worked example: a force with a lever arm

A particle is at $\mathbf r=(2.0\,\mathrm m)\mathbf e_1$. A force $\mathbf F=(3.0\,\mathrm N)\mathbf e_2$ acts on it. The torque is

$$
\mathcal T=\mathbf r\wedge\mathbf F
=(6.0\,\mathrm{N\,m})\mathbf e_1\wedge\mathbf e_2.
$$

Its magnitude is $6.0\,\mathrm{N\,m}$, the force multiplied by the $2.0\,\mathrm m$ perpendicular lever arm. In a right-handed three-dimensional description, the associated axial vector points along $+\mathbf e_3$. If the same force instead pointed along $\mathbf e_1$, the torque would be zero: the line of action would pass through the origin.

## 5.6 Angular momentum of a system

For a system of particles, add the angular momenta of its members about the same origin:

$$
\mathcal J_{\mathrm{tot}}=\sum_a\mathbf r_a\wedge\mathbf p_a.
$$

Differentiating gives the sum of the torques from all forces. External forces contribute the net external torque,

$$
\mathcal T_{\mathrm{ext}}=\sum_a\mathbf r_a\wedge\mathbf F_a^{\mathrm{ext}}.
$$

For an internal pair, Newton's third law gives $\mathbf F_{ab}=-\mathbf F_{ba}$. Their combined torque is

$$
\mathbf r_a\wedge\mathbf F_{ab}+\mathbf r_b\wedge\mathbf F_{ba}
=(\mathbf r_a-\mathbf r_b)\wedge\mathbf F_{ab}.
$$

This pair torque vanishes when the internal force lies along the line joining the particles, as it does for central pair forces. Under that condition, internal torques cancel in pairs, and

$$
\frac{d\mathcal J_{\mathrm{tot}}}{dt}=\mathcal T_{\mathrm{ext}}.
$$

```{warning} Equal and opposite does not always mean zero total torque

Newton's third law says that two interaction forces are equal and opposite. For their torques about an origin to cancel as well, the forces must also act along the same line. Central forces have this property. In ordinary introductory mechanics, this is usually included in the interaction model; it is the extra geometric fact that makes internal torque cancellation work.
```

If the net external torque is zero, the system's total angular momentum about the chosen origin is conserved. If there is an external torque, its time integral gives the change. As with linear momentum, individual particles may change their angular momentum while the total remains fixed.

The origin dependence of a system's angular momentum follows directly from its definition. Under a shift by a fixed vector $\mathbf a$,

$$
\mathcal J'_{\mathrm{tot}}
=\sum_a(\mathbf r_a-\mathbf a)\wedge\mathbf p_a
=\mathcal J_{\mathrm{tot}}-\mathbf a\wedge\mathbf P.
$$

When the total linear momentum is zero, the angular momentum has the same value about every fixed origin. In other cases, specifying the origin is part of specifying the angular momentum.

## 5.7 When each description is useful

For the centre of mass, impulse, and most collision calculations, vector components are usually the most direct language. The momentum equations are already compact, and geometric algebra adds little to a one-dimensional cart problem.

Angular momentum is a more substantial case for GA. The expression $\mathbf r\wedge\mathbf p$ identifies the plane associated with the motion and its orientation. The torque law then has the same form as the linear momentum law: force changes linear momentum, and torque changes angular momentum. In three dimensions, the cross product remains useful when a perpendicular vector is the most convenient representation. It is the same information in a different form.

The purpose of GA here is not to make every calculation shorter. It is to keep the geometry of angular momentum visible and to give a representation that carries naturally from planar motion to three dimensions. We will use this viewpoint again for central-force orbits and for rotations.

## 5.8 What to remember

- The rate of change of a system's total linear momentum is its net external force: $\dot{\mathbf P}=\mathbf F_{\mathrm{ext}}$.
- The centre of mass obeys $M\mathbf A_{\mathrm{cm}}=\mathbf F_{\mathrm{ext}}$ and moves at constant velocity when the net external force is zero.
- Impulse equals change in momentum. During a short collision, total momentum is approximately conserved when the external impulse is negligible.
- Momentum is conserved in elastic and inelastic collisions; kinetic energy is conserved only in elastic collisions.
- Angular momentum about an origin is the bivector $\mathcal J=\mathbf r\wedge\mathbf p$. In three dimensions it is dual to the conventional vector $\mathbf L=\mathbf r\times\mathbf p$.
- Torque is $\mathcal T=\mathbf r\wedge\mathbf F$, and $\dot{\mathcal J}=\mathcal T$ for a particle of constant mass.
- For a system, internal torques cancel for central pair forces. With zero net external torque, the system's angular momentum about the chosen origin is conserved.

### Exercises

1. Three particles of masses $1.0\,\mathrm{kg}$, $2.0\,\mathrm{kg}$, and $3.0\,\mathrm{kg}$ move along a line with velocities $4.0\,\mathrm{m\,s^{-1}}$, $-1.0\,\mathrm{m\,s^{-1}}$, and $0.50\,\mathrm{m\,s^{-1}}$. Find their total momentum and centre-of-mass velocity.
2. Starting from the definition of $\mathbf R_{\mathrm{cm}}$, derive $M\mathbf A_{\mathrm{cm}}=\mathbf F_{\mathrm{ext}}$ for fixed masses.
3. A $0.15\,\mathrm{kg}$ ball moving at $20\,\mathrm{m\,s^{-1}}$ is caught and brought to rest in $0.050\,\mathrm s$. Find the impulse on the ball and the average force exerted on it. State your sign convention.
4. A $0.40\,\mathrm{kg}$ cart moving at $2.0\,\mathrm{m\,s^{-1}}$ collides with a stationary $0.60\,\mathrm{kg}$ cart. They stick together. Find their final speed, assuming negligible external impulse. Compare the initial and final kinetic energies.
5. A firework initially at rest breaks into two pieces. One piece has mass $0.30\,\mathrm{kg}$ and velocity $(8.0\mathbf e_1+2.0\mathbf e_2)\,\mathrm{m\,s^{-1}}$. The other has mass $0.20\,\mathrm{kg}$. Find the second piece's velocity, neglecting external impulse during the explosion.
6. In a plane with $\mathbf I=\mathbf e_1\mathbf e_2$, a particle has $\mathbf r=(2\mathbf e_1+\mathbf e_2)\,\mathrm m$ and $\mathbf p=(3\mathbf e_1+4\mathbf e_2)\,\mathrm{kg\,m\,s^{-1}}$. Calculate $\mathcal J=\mathbf r\wedge\mathbf p$. What is its magnitude and orientation?
7. In the same plane, a force $\mathbf F=(-2\mathbf e_1+5\mathbf e_2)\,\mathrm N$ acts at $\mathbf r=(1.5\mathbf e_1)\,\mathrm m$. Find the torque bivector and its magnitude. Which component of the force contributes to it?
8. A particle moves in a circle of radius $R$ at constant speed $v$ about the origin. Show that its angular momentum magnitude is $mRv$ and that the inward force produces zero torque about the origin.
9. Show that shifting the origin by $\mathbf a$ changes a system's angular momentum by $-\mathbf a\wedge\mathbf P$. Under what condition is the angular momentum independent of the origin?
10. Two particles exert equal and opposite forces on one another. Explain why their total torque vanishes if the forces lie along the line joining the particles. Does the equal-and-opposite condition alone guarantee this?
11. A puck moves freely across a frictionless table. A short force pulse is applied at a point away from the puck's centre. Describe separately how the pulse changes the puck's linear momentum and its angular momentum about the centre. Which mathematical quantity represents the rotational effect?

## Further reading

- OpenStax, [*University Physics, Volume 1*, Chapter 9: Linear Momentum and Collisions](https://openstax.org/books/university-physics-volume-1/pages/9-introduction), including impulse, conservation of momentum, collision types, and centre of mass.
- OpenStax, [*University Physics, Volume 1*, Section 11.2: Angular Momentum](https://openstax.org/books/university-physics-volume-1/pages/11-2-angular-momentum) and [Section 11.3: Conservation of Angular Momentum](https://openstax.org/books/university-physics-volume-1/pages/11-3-conservation-of-angular-momentum), for the standard vector formulation.
- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), for a more extended undergraduate treatment of momentum, collisions, and angular momentum.
- David Hestenes, [*New Foundations for Classical Mechanics*](https://davidhestenes.net/geocalc/html/NFCM.html), for a geometric-algebra treatment of mechanics and angular momentum.
