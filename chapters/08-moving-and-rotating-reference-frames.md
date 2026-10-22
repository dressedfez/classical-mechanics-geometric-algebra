---
title: "8. Moving and Rotating Reference Frames"
description: "Develop reflections and rotors, then use them to describe velocities, accelerations, and forces in moving and rotating frames."
---

Many useful descriptions of motion use axes that move with an object: axes fixed to a turning wheel, a rotating planet, or a rigid body. The price is that the axes themselves change direction. A velocity or acceleration measured in the moving frame is therefore not generally the same as the one measured by a stationary observer.

This chapter begins with the geometric-algebra tools for reflections and rotations. We then derive the transport formulas that relate moving and inertial frames, including the Coriolis, centrifugal, and Euler accelerations. In three dimensions the cross product is often the quickest notation for these terms; the rotor description shows how the rotation acts geometrically and composes without choosing Euler angles.

## 8.1 Mathematical tools: reflections and rotors

Let $\mathbf n$ be a unit vector. Reflection of a vector $\mathbf a$ in the plane perpendicular to $\mathbf n$ is

$$
\mathbf a'=-\mathbf n\mathbf a\mathbf n.
$$

To verify the formula, split $\mathbf a=\mathbf a_{\parallel}+\mathbf a_{\perp}$, with $\mathbf a_{\parallel}=(\mathbf a\cdot\mathbf n)\mathbf n$. Parallel vectors commute with $\mathbf n$, while perpendicular vectors anticommute with it. Thus

$$
\mathbf n\mathbf a\mathbf n
=\mathbf n\mathbf a_{\parallel}\mathbf n+\mathbf n\mathbf a_{\perp}\mathbf n
=\mathbf a_{\parallel}-\mathbf a_{\perp},
$$

and the leading minus sign gives $-\mathbf a_{\parallel}+\mathbf a_{\perp}$, as required for reflection in the perpendicular plane. For example, if $\mathbf n=\mathbf e_1$, then $a_1\mathbf e_1+a_2\mathbf e_2$ is reflected to $-a_1\mathbf e_1+a_2\mathbf e_2$.

Two reflections compose to a rotation. Reflect first with normal $\mathbf n_1$, then with normal $\mathbf n_2$:

$$
\mathbf a''=\mathbf n_2\mathbf n_1\,\mathbf a\,\mathbf n_1\mathbf n_2
=R\mathbf a\widetilde R,
\qquad R=\mathbf n_2\mathbf n_1.
$$

Here $\widetilde R$ is the reverse of $R$. For unit normals, $R\widetilde R=1$. The even multivector $R$ is a **rotor**, and the sandwich $R\mathbf a\widetilde R$ rotates the vector while preserving its length and inner products. In a plane with unit bivector $I$ and $I^2=-1$, a rotation through angle $\theta$ is represented by

$$
R=\exp\left(-\frac{1}{2} I\theta\right)
=\cos\frac{\theta}{2}-I\sin\frac{\theta}{2},
\qquad \mathbf a'=R\mathbf a\widetilde R.
$$

The half-angle is a consequence of the sandwich: the angle in $R$ appears once on each side of the vector. In 3D, a rotation through $\theta$ in a plane with unit bivector $B$ has the same form $R=\exp(-B\theta/2)$. A bivector therefore describes the plane of rotation directly. The corresponding axis is a convenient 3D dual description.

For a concrete check, set $R=\cos(\theta/2)-I\sin(\theta/2)$ and apply it to $\mathbf e_1$. Using $I\mathbf e_1=-\mathbf e_2$ and $\mathbf e_1I=\mathbf e_2$ gives

$$
R\mathbf e_1\widetilde R
=\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2.
$$

The result has unit length for every angle. A rotation matrix gives the same answer by multiplying components; the rotor packages the rotation and the plane of rotation in one object.

Rotors compose by multiplication. If $R_1$ acts first and $R_2$ second, the combined action is $R_2R_1\,\mathbf a\,\widetilde R_1\widetilde R_2$. In general, the order matters: finite rotations about different axes do not commute. This is one reason a single set of three rotation angles can become awkward for describing arbitrary changing orientations.

```{note} Keep the sign convention visible

We use $\mathbf a'=R\mathbf a\widetilde R$ and $R=\exp(-B\theta/2)$. In the $\mathbf e_1\mathbf e_2$ plane this rotates $\mathbf e_1$ toward $\mathbf e_2$ for positive $\theta$. Other books may choose the opposite sign in the exponential; the physical result is the same when the convention is used consistently.
```

## 8.2 A time-dependent orientation

Let $R(t)$ describe the orientation of axes attached to a moving body relative to fixed inertial axes. A vector with components $\boldsymbol\rho(t)$ in the body frame is represented in space by

$$
\mathbf r(t)=R(t)\boldsymbol\rho(t)\widetilde R(t).
$$

Differentiate the rotor normalization $R\widetilde R=1$. The quantity

$$
\boldsymbol\Omega=-2\dot R\widetilde R
$$

is a bivector in the fixed frame; it is the angular velocity bivector in our convention. Differentiate $\mathbf r=R\boldsymbol\rho\widetilde R$ term by term. The first term can be written $(\dot R\widetilde R)\mathbf r=-\boldsymbol\Omega\mathbf r/2$. From $R\widetilde R=1$, its reverse gives $R\dot{\widetilde R}=\boldsymbol\Omega/2$, so the last term is $\mathbf r\boldsymbol\Omega/2$. The result is

$$
\dot{\mathbf r}
=R\dot{\boldsymbol\rho}\widetilde R
+\frac{1}{2}(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r).
$$

The first term is the body's own change of the vector as seen in its frame. The second is the change caused by rotation of the frame. The commutator of a bivector and a vector is a vector, so it has the correct geometric type.

In three dimensions write $\boldsymbol\Omega=I_3\boldsymbol\omega$, where $I_3=\mathbf e_1\mathbf e_2\mathbf e_3$ is the unit pseudoscalar and $\boldsymbol\omega$ is the usual angular-velocity vector. Then

$$
\frac{1}{2}(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r)
=\boldsymbol\omega\times\mathbf r.
$$

This recovers the familiar rule for the velocity of a point carried by a rotating body. The bivector form works directly with the plane of rotation; the cross product is often more familiar for three-dimensional components.

## 8.3 The transport theorem

For any vector $\mathbf A$ described in a frame rotating with angular velocity $\boldsymbol\omega$, its inertial derivative is

$$
\left(\frac{d\mathbf A}{dt}\right)_{\!I}
=\left(\frac{d\mathbf A}{dt}\right)_{\!R}
+\boldsymbol\omega\times\mathbf A.
$$

The subscripts indicate inertial and rotating observers. The extra term is present because the rotating basis vectors change direction. Apply this relation to the position vector of a particle relative to an origin fixed in the rotating frame. Its inertial velocity is

$$
\mathbf v_I=\mathbf v_R+\boldsymbol\omega\times\mathbf r,
$$

and differentiating once more gives

$$
\mathbf a_I=\mathbf a_R
+2\boldsymbol\omega\times\mathbf v_R
+\dot{\boldsymbol\omega}\times\mathbf r
+\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r).
$$

To see where the two Coriolis terms come from, differentiate $\mathbf v_I=\mathbf v_R+\boldsymbol\omega\times\mathbf r$. The inertial derivative of $\mathbf v_R$ is itself $\mathbf a_R+\boldsymbol\omega\times\mathbf v_R$, by the same transport rule. Differentiating the second term gives $\dot{\boldsymbol\omega}\times\mathbf r+\boldsymbol\omega\times\mathbf v_I$. Substituting $\mathbf v_I=\mathbf v_R+\boldsymbol\omega\times\mathbf r$ yields the displayed expression, including two copies of $\boldsymbol\omega\times\mathbf v_R$.

If the moving origin has inertial acceleration $\mathbf a_O$, add $\mathbf a_O$ to the right-hand side. Each term has a distinct origin:

- $\mathbf a_R$ is the acceleration measured in the rotating frame.
- $2\boldsymbol\omega\times\mathbf v_R$ is the Coriolis acceleration.
- $\dot{\boldsymbol\omega}\times\mathbf r$ is the Euler acceleration when the rotation rate changes.
- $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)$ is the inward centripetal acceleration associated with the rotation.

Newton's law still holds in the inertial frame, $m\mathbf a_I=\mathbf F$. To write an equation using the rotating observer's acceleration, move the frame terms to the force side:

$$
m\mathbf a_R=\mathbf F
-m\mathbf a_O
-2m\boldsymbol\omega\times\mathbf v_R
-m\dot{\boldsymbol\omega}\times\mathbf r
-m\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r).
$$

These additional terms are called **inertial forces** or **fictitious forces** in the rotating description. They do not arise from another body interacting with the particle. They account for using accelerating axes. On the outer side of a rotating platform, the last term points outward and is called the centrifugal force in the rotating frame.

## 8.4 Worked example: a bead on a rotating radial rod

A bead slides without friction along a straight rod that rotates at constant angular speed $\omega$ in a horizontal plane. Let $r$ be its distance from the axis. In the rotating frame, the bead has no angular velocity relative to the rod, so $\mathbf v_R=\dot r\mathbf e_r$ and $\mathbf a_R=\ddot r\mathbf e_r$. The rod's angular velocity is perpendicular to the plane. The centrifugal term is outward and has magnitude $\omega^2r$, while the Coriolis term is perpendicular to the rod and is balanced by the rod's sideways contact force.

If no force acts along the rod, the radial equation seen in the rotating frame is

$$
m\ddot r=m\omega^2r.
$$

Starting from rest relative to the rod at radius $r_0$, the solution of $\ddot r=\omega^2r$ is

$$
r(t)=r_0\cosh(\omega t),
\qquad
\dot r(t)=\omega r_0\sinh(\omega t).
$$

For example, with $r_0=0.20\,\mathrm m$, $\omega=2.0\,\mathrm{rad\,s^{-1}}$, and $t=0.50\,\mathrm s$, the bead has moved to about $0.31\,\mathrm m$ and has radial speed about $0.47\,\mathrm{m\,s^{-1}}$. It accelerates outward relative to the rod. In inertial axes this is not mysterious: its tangential speed $\omega r$ grows as it slides outward, and the rod must redirect its motion continuously. The rotating-frame centrifugal term packages this effect into an apparent force.

If the bead is held at a fixed radius, then $\mathbf a_R=0$ and $\mathbf v_R=0$. The rod must exert an inward force $m\omega^2r$ in the inertial frame to provide the centripetal acceleration. The rotating observer describes the same balance as an outward centrifugal inertial force opposed by the rod's inward contact force.

## 8.5 Earth and other rotating frames

The Earth's surface is approximately a rotating frame. The centrifugal term slightly reduces apparent weight, with the largest effect at the equator. The Coriolis term deflects large-scale moving air and ocean currents to the right in the northern hemisphere and to the left in the southern hemisphere. Its magnitude depends on both latitude and velocity; it is usually negligible for a small object moving briefly in a room, but important for long-range motion over a rotating planet.

The Euler term matters when the rotation rate itself changes, for example during the spin-up of a platform. A translating origin contributes the additional $-m\mathbf a_O$ inertial force. Keeping these terms separate helps diagnose which approximation is appropriate for a particular problem.

## 8.6 Worked example: the Foucault pendulum

A long pendulum provides a direct way to observe Earth's rotation. Its bob swings back and forth in an almost fixed vertical plane in inertial space. Viewed from the ground, that plane slowly turns. The effect is strongest at the poles and vanishes at the equator.

At latitude $\phi$, let $\mathbf e_E$, $\mathbf e_N$, and $\mathbf e_U$ point east, north, and up. The local vertical component of Earth's angular velocity is $\Omega_s=\Omega_E\sin\phi$, where $\Omega_E$ is Earth's rotation rate. For small swings, write the bob's horizontal displacement from its equilibrium point as $\boldsymbol\rho=x\mathbf e_E+y\mathbf e_N$. The small-angle restoring acceleration is $-\omega_0^2\boldsymbol\rho$, with $\omega_0=\sqrt{g/\ell}$ for pendulum length $\ell$.

The horizontal part of the Coriolis acceleration is $-2\Omega_s\mathbf e_U\times\dot{\boldsymbol\rho}$. In the east-north plane, define the unit bivector $I_h=\mathbf e_E\mathbf e_N$, with $I_h^2=-1$. Its action on a horizontal vector gives $I_h\dot{\boldsymbol\rho}=\dot y\mathbf e_E-\dot x\mathbf e_N$, so the Coriolis term can be written without a three-dimensional cross product. The linearized equation is

$$
\ddot{\boldsymbol\rho}+\omega_0^2\boldsymbol\rho
=2\Omega_s I_h\dot{\boldsymbol\rho}.
$$

In components, this is

$$
\ddot x+\omega_0^2x=2\Omega_s\dot y,
\qquad
\ddot y+\omega_0^2y=-2\Omega_s\dot x.
$$

These familiar equations show how the horizontal component of velocity produces a sideways Coriolis acceleration. The GA form packages the same pair of component couplings as multiplication by the oriented plane element $I_h$.

The rotor description makes the slow turning of the swing plane explicit. Set

$$
\boldsymbol\rho=Q\mathbf q\widetilde Q,
\qquad
Q(t)=\exp\left(\frac{1}{2} I_h\Omega_s t\right).
$$

With our convention $\mathbf a'=Q\mathbf a\widetilde Q$, this rotor turns vectors through angle $-\Omega_s t$. Substitution into the pendulum equation gives

$$
\ddot{\mathbf q}+\left(\omega_0^2+\Omega_s^2\right)\mathbf q=0.
$$

Since Earth's rotation rate is tiny compared with a pendulum's oscillation frequency, the correction $\Omega_s^2$ is negligible in the swing frequency. A pendulum that oscillates nearly along a fixed line in the $\mathbf q$ description therefore has a swing plane that turns relative to the ground at the leading rate

$$
\dot\theta=-\Omega_E\sin\phi.
$$

In the northern hemisphere the turn is clockwise when viewed from above; in the southern hemisphere it is counterclockwise. At the equator there is no leading precession, while at either pole the plane makes one turn per sidereal day. The magnitude of the precession period is

$$
T_{\mathrm{prec}}=\frac{T_{\mathrm{sid}}}{|\sin\phi|}.
$$

For example, at latitude $45^\circ$ the period is about $1.41$ sidereal days. The Foucault pendulum is a useful synthesis: ordinary mechanics supplies the restoring force, the rotating-frame law supplies the Coriolis term, and the GA plane element and rotor make the orientation and its slow change visible. For numerical component work, the two scalar equations above are often the most direct route.

```{figure} ../figures/foucault-pendulum.svg
:name: fig-foucault-pendulum
:alt: Top-down view of the Foucault pendulum's swing line turning clockwise relative to the ground in the northern hemisphere.

The vertical component of Earth's rotation produces the leading Coriolis effect. The swing plane turns slowly relative to the ground, with a rate proportional to the sine of latitude.
```

## 8.7 What geometric algebra contributes

Reflections give a simple construction of rotations, and rotors compose rotations as products of algebraic objects. Their sandwich action preserves vector lengths automatically. For a time-varying orientation, the rotor derivative yields the angular-velocity bivector and the frame-transport formula. These are useful geometric statements when the plane of rotation or composition of rotations matters.

For calculating a Coriolis acceleration in a chosen three-dimensional coordinate system, the cross product and components are usually shorter. Euler angles and rotation matrices are also useful, especially in engineering software. The GA approach earns its place by representing rotations in any plane with one consistent operation and by making orientation composition explicit.

## 8.8 What to remember

- Reflection in the plane normal to a unit vector $\mathbf n$ is $\mathbf a'=-\mathbf n\mathbf a\mathbf n$.
- A rotor rotates vectors by $\mathbf a'=R\mathbf a\widetilde R$; a plane rotation through $\theta$ uses a half-angle in $R$.
- A time-dependent frame adds $\boldsymbol\omega\times\mathbf A$ to the derivative of a vector.
- The rotating-frame acceleration includes Coriolis, Euler, and centripetal terms.
- Inertial forces appear when Newton's law is expressed in accelerating axes; they represent the frame choice.
- For a Foucault pendulum, the vertical component of Earth's rotation gives a leading swing-plane precession rate $-\Omega_E\sin\phi$ relative to the ground.
- Rotors clarify composition and geometry, while cross products and matrices remain efficient in standard 3D calculations.

### Exercises

1. Use $\mathbf a'=-\mathbf n\mathbf a\mathbf n$ to show that a vector parallel to $\mathbf n$ reverses and one perpendicular to $\mathbf n$ is unchanged.
2. In the $\mathbf e_1\mathbf e_2$ plane, apply $R=\exp(-I\theta/2)$ to $\mathbf e_1$ and show that it becomes $\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2$.
3. A point is fixed at radius $0.40\,\mathrm m$ on a turntable rotating at $2.0\,\mathrm{rad\,s^{-1}}$. Find its inertial speed and centripetal acceleration.
4. A particle moves north relative to Earth's surface in the northern hemisphere. Use the Coriolis term to determine the direction of its apparent horizontal deflection.
5. Explain which inertial terms vanish when a frame rotates at constant angular speed and the particle is stationary in that frame.
6. Describe one benefit and one limitation of using rotors instead of rotation matrices for a changing 3D orientation.
7. **Synthesis.** For a bead at $\mathbf r=r(t)\mathbf e_r(t)$ on a rod rotating at constant rate $\omega$, differentiate twice to find its inertial acceleration. Set the real radial force to zero and show that $\ddot r=\omega^2r$; identify the tangential acceleration that the rod must supply.
8. A Foucault pendulum is at latitude $60^\circ$ north. Find the leading precession rate and period relative to the ground. State the direction of turn when viewed from above.

## Further reading

- John R. Taylor, *Classical Mechanics*, chapters on non-inertial reference frames and rotations.
- David Hestenes, *New Foundations for Classical Mechanics*, for rotor-based kinematics and dynamics.
- Chris Doran and Anthony Lasenby, *Geometric Algebra for Physicists*, for reflections and rotor representations.
- J. Wolfe, [“Foucault's pendulum: the physics (and maths) explained”](https://www.physics.unsw.edu.au/~jw/pendulumdetails.html), for a fuller treatment of the latitude-dependent precession.
