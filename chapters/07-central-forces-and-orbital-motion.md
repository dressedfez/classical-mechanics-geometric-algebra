---
title: "7. Central Forces and Orbital Motion"
description: "Use angular momentum, effective potentials, and Kepler's laws to understand central-force motion and the geometry of orbits."
---

A planet does not move in a straight line, but its changing direction does not mean that every part of its motion is complicated. When the force always points toward a fixed centre, the torque about that centre is zero. Angular momentum is then conserved, the motion stays in one plane, and a three-dimensional problem reduces to motion in that plane. This is the starting point for understanding planetary orbits, satellite motion, and classical scattering.

We will derive these results using familiar polar-coordinate mechanics. Geometric algebra makes the conserved orbital plane especially clear: angular momentum is a bivector, and a fixed bivector identifies the plane in which the trajectory lies. For solving the radial equation, scalar energy and effective-potential methods are usually the most efficient tools.

## 7.1 What makes a force central?

A **central force** points along the line from a fixed centre to the particle and has magnitude depending only on distance. It can be written

$$
\mathbf F=F(r)\mathbf e_r,
\qquad r=|\mathbf r|,
\qquad \mathbf e_r=\frac{\mathbf r}{r}.
$$

The force may point inward or outward; the sign of $F(r)$ specifies which. If it derives from a potential $U(r)$, then $F(r)=-dU/dr$. Examples include gravity and electrostatic forces outside a spherically symmetric source.

The torque bivector about the centre is

$$
\mathcal T=\mathbf r\wedge\mathbf F=\mathbf 0,
$$

because the position and force are parallel. By Chapter 5, $\dot{\mathcal J}=\mathcal T$, so

$$
\mathcal J=\mathbf r\wedge\mathbf p=\text{constant}.
$$

If $\mathcal J\ne0$, the fixed plane it represents contains both $\mathbf r$ and $\mathbf p$ at every instant. Since $\mathbf v=\mathbf p/m$, the trajectory remains in this plane. This is a geometric fact in three dimensions, not an assumption that the orbit is planar. If $\mathcal J=0$, the position and momentum are parallel and the motion is radial along a line.

Choose a fixed oriented plane for the nonradial motion, with unit bivector $I$ satisfying $I^2=-1$. Define the radial and tangential unit vectors by

$$
\mathbf e_r=\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2,
\qquad \mathbf e_\theta=\mathbf e_r I.
$$

The polar-coordinate derivative rules are $\dot{\mathbf e}_r=\dot\theta\mathbf e_\theta$ and $\dot{\mathbf e}_\theta=-\dot\theta\mathbf e_r$. They give

$$
\mathbf r=r\mathbf e_r,
\qquad
\mathbf v=\dot r\mathbf e_r+r\dot\theta\mathbf e_\theta.
$$

The angular momentum bivector is therefore

$$
\mathcal J=\mathbf r\wedge m\mathbf v
=mr^2\dot\theta\,I.
$$

The cancellation is visible directly: substituting $\mathbf r=r\mathbf e_r$ and $\mathbf v=\dot r\mathbf e_r+r\dot\theta\mathbf e_\theta$ gives a radial term $mr\dot r(\mathbf e_r\wedge\mathbf e_r)=0$. Only the tangential motion contributes. Its constant signed magnitude in this plane is denoted by $L=mr^2\dot\theta$. Hence

$$
r^2\dot\theta=\frac{L}{m}=h,
$$

where $h$ is the **specific angular momentum**, angular momentum per unit mass. The bivector $\mathcal J=LI$ records the plane; the scalar $L$ records the signed amount of angular momentum within the chosen orientation.

```{note} A Lagrangian preview: the cyclic azimuth

In three-dimensional spherical coordinates $(r,\vartheta,\varphi)$, the kinetic energy is

$$
T=\frac12m\left(\dot r^2+r^2\dot\vartheta^2+r^2\sin^2\vartheta\,\dot\varphi^2\right).
$$

For a central potential $U(r)$, the coordinate Lagrangian is $\mathcal L=T-U(r)$. The azimuth $\varphi$ does not appear in it, so it is cyclic. Its conjugate momentum

$$
p_\varphi=\frac{\partial\mathcal L}{\partial\dot\varphi}
=mr^2\sin^2\vartheta\,\dot\varphi
$$

The Euler–Lagrange equation gives $\dot p_\varphi=\partial\mathcal L/\partial\varphi=0$. Choose the polar axis along the normal to the orbital plane. The orbit then lies at $\vartheta=\pi/2$, and $p_\varphi=mr^2\dot\varphi=L$. This is the coordinate expression of the same conserved orbital bivector $\mathcal J=LI$. Chapter 12 will derive the broader connection between cyclic coordinates, symmetry, and conservation.
```

## 7.2 Equal areas and the radial equation

In a short time $dt$, the particle sweeps out a small sector whose area, to first order, is the area of a triangle: $dA=\tfrac12r^2d\theta$. Thus the areal velocity is

$$
\frac{dA}{dt}=\frac12r^2\dot\theta=\frac{L}{2m}.
$$

It is constant. Equal areas are swept out in equal times. This is Kepler's second law, and here it follows directly from zero torque, before specifying the form of the central force.

Projecting Newton's equation onto the radial and tangential directions gives

$$
m(\ddot r-r\dot\theta^2)=F(r),
\qquad
m(r\ddot\theta+2\dot r\dot\theta)=0.
$$

The second equation is equivalent to $d(mr^2\dot\theta)/dt=0$. Using $\dot\theta=L/(mr^2)$ in the first equation reduces the orbit to one radial coordinate:

$$
m\ddot r=F(r)+\frac{L^2}{mr^3}.
$$

For a conservative force, the same equation follows from the total energy

$$
E=\frac12m\dot r^2+\frac{L^2}{2mr^2}+U(r)
=\frac12m\dot r^2+U_{\mathrm{eff}}(r),
$$

where

$$
U_{\mathrm{eff}}(r)=U(r)+\frac{L^2}{2mr^2}
$$

is the **effective potential**. The extra positive term is sometimes called the centrifugal barrier. It is not an additional physical force; it appears when the angular motion is accounted for while studying the radial coordinate. The radial motion is allowed where $E\ge U_{\mathrm{eff}}(r)$, and turning points occur where equality holds.

```{figure} ../figures/central-orbit.svg
:label: fig-central-orbit
:enumerator: "7.1"
:alt: A central-force orbit with the radius vector, tangential velocity, fixed orbital plane, and swept area marked.
:width: 76%

The central force is radial, while the velocity generally has both radial and tangential components. The constant bivector $\mathcal J$ represents the oriented orbital plane, and equal angular momentum gives equal swept areas in equal times.
```

### Worked example: circular orbit and stability

For a circular orbit of radius $r_0$, the radius is constant, so $\ddot r=0$. The inward force must provide the centripetal acceleration:

$$
F(r_0)=-\frac{L^2}{mr_0^3},
\qquad
\frac{mv^2}{r_0}=-F(r_0),
$$

where the second expression assumes the force is inward. Equivalently, $r_0$ is a stationary point of $U_{\mathrm{eff}}$. Its stability is determined by the curvature there: a local minimum gives restoring radial acceleration after a small disturbance; a local maximum gives an instability. We will check this explicitly for gravity next.

## 7.3 Kepler's inverse-square law

For gravity from a fixed spherical source of mass $M$, the force on a particle of mass $m$ is

$$
\mathbf F=-\frac{GMm}{r^2}\mathbf e_r,
\qquad
U(r)=-\frac{GMm}{r}.
$$

Write $\kappa=GMm$ for the positive strength of the gravitational potential, so $U(r)=-\kappa/r$. We reserve $\mu$ for the reduced mass introduced below. The effective potential is

$$
U_{\mathrm{eff}}(r)=\frac{L^2}{2mr^2}-\frac{\kappa}{r}.
$$

It falls to a minimum and rises at small $r$ because of the angular-momentum term. The stationary point satisfies

$$
\frac{dU_{\mathrm{eff}}}{dr}=-\frac{L^2}{mr^3}+\frac{\kappa}{r^2}=0,
\qquad
r_0=\frac{L^2}{m\kappa}=\frac{h^2}{GM}.
$$

Its curvature is $U_{\mathrm{eff}}''(r_0)=\kappa/r_0^3>0$, confirming stability against small radial disturbances. The corresponding small radial oscillation frequency is

$$
\omega_r^2=\frac{U_{\mathrm{eff}}''(r_0)}{m}=\frac{GM}{r_0^3},
$$

equal to the square of the circular orbit's angular frequency.

The same orbit can be derived without an energy diagram. Let $h=L/m=r^2\dot\theta$ and $u=1/r$. A prime will denote differentiation with respect to $\theta$. Since $\dot\theta=hu^2$ and $dr/d\theta=-u'/u^2$, the radial speed is

$$
\dot r=\frac{dr}{d\theta}\dot\theta=-hu'.
$$

Differentiating once more gives $\ddot r=-h^2u^2u''$. The polar radial equation also contains $-r\dot\theta^2=-h^2u^3$, so

$$
\ddot r-r\dot\theta^2=-h^2u^2(u''+u).
$$

Equating this with $F(r)/m$ gives Binet's equation:

$$
\frac{d^2u}{d\theta^2}+u=-\frac{F(1/u)}{mh^2u^2}
=-\frac{m}{L^2u^2}F(1/u).
$$

For the inverse-square force $F(r)=-\kappa/r^2$, this becomes

$$
\frac{d^2u}{d\theta^2}+u=\frac{m\kappa}{L^2}.
$$

The solution of the linear equation is a constant plus a sinusoid,

$$
u(\theta)=\frac{m\kappa}{L^2}\left[1+e\cos(\theta-\theta_0)\right].
$$

Taking its reciprocal yields a conic section with the force centre at a focus:

$$
r(\theta)=\frac{p}{1+e\cos(\theta-\theta_0)},
\qquad
p=\frac{L^2}{m\kappa}.
$$

The eccentricity $e$ determines the orbit: $0\le e<1$ gives an ellipse (including a circle at $e=0$), $e=1$ a parabola, and $e>1$ a hyperbola. Substituting the orbit and its derivative into the conserved energy gives

$$
e^2=1+\frac{2EL^2}{m\kappa^2}.
$$

Negative energy gives a bound ellipse, zero energy a parabolic escape trajectory, and positive energy a hyperbolic flyby. These formulas assume a fixed source.

### Worked example: reduce the two-body problem

For two bodies of masses $m_1$ and $m_2$, let their positions be $\mathbf r_1$ and $\mathbf r_2$. Define the centre-of-mass position, total mass, relative position, and reduced mass by

$$
\mathbf R=\frac{m_1\mathbf r_1+m_2\mathbf r_2}{m_1+m_2},
\qquad M=m_1+m_2,
\qquad \mathbf r=\mathbf r_1-\mathbf r_2,
\qquad \mu=\frac{m_1m_2}{m_1+m_2}.
$$

Solving for the individual positions gives

$$
\mathbf r_1=\mathbf R+\frac{m_2}{M}\mathbf r,
\qquad
\mathbf r_2=\mathbf R-\frac{m_1}{M}\mathbf r.
$$

Substitute their time derivatives into $T=\tfrac12m_1\dot{\mathbf r}_1^{\,2}+\tfrac12m_2\dot{\mathbf r}_2^{\,2}$. The cross terms cancel because $m_1(m_2/M)=m_2(m_1/M)$, leaving the kinetic energy as a centre-of-mass part and a relative-motion part:

$$
T=\frac12M\dot{\mathbf R}^{\,2}+\frac12\mu\dot{\mathbf r}^{\,2}.
$$

If the interaction depends only on the separation $r=|\mathbf r|$, the centre of mass moves uniformly when no external force acts. The relative coordinate behaves like a single particle of mass $\mu$ in the interaction potential. For gravity, write $\kappa=Gm_1m_2$ for the strength of this relative potential:

$$
U(r)=-\frac{Gm_1m_2}{r}=-\frac{\kappa}{r},
\qquad
\mu\ddot{\mathbf r}=-\frac{\kappa}{r^2}\mathbf e_r.
$$

Thus the orbit results above apply with reduced mass $\mu$. The two bodies move around their common centre of mass on similar conic orbits, while their relative separation follows the Kepler conic. The period law for this relative orbit follows from the area argument in the next section. The fixed-source approximation follows when one mass is much larger than the other.

## 7.4 Kepler's laws and their meaning

The inverse-square force explains the empirical regularities Johannes Kepler found in planetary observations. The equal-area law followed already from centrality. The orbit equation shows that planets follow ellipses with the Sun at a focus. To derive the period law, write the ellipse area as $\pi ab$ and divide by the constant areal velocity $L/(2m)$:

$$
T=\frac{\pi ab}{L/(2m)}=\frac{2\pi mab}{L}.
$$

For an ellipse, $p=b^2/a$, and the orbit equation gives $L^2=m\kappa p$. In the fixed-source problem $\kappa=GMm$, so squaring the period expression and substituting gives

$$
T^2=\frac{4\pi^2a^2b^2m^2}{L^2}
=\frac{4\pi^2a^3}{GM}.
$$

For two comparable masses, use $m=\mu=m_1m_2/(m_1+m_2)$ and $\kappa=Gm_1m_2$. Since $\kappa/\mu=G(m_1+m_2)$, the result is

$$
T^2=\frac{4\pi^2}{G(m_1+m_2)}a^3.
$$

Thus the square of the orbital period is proportional to the cube of the semi-major axis for bodies orbiting the same dominant mass. Kepler's laws describe the observed pattern; Newton's inverse-square law explains why that pattern holds and predicts departures when other bodies perturb an orbit.

### Worked example: an Earth satellite

For a circular orbit just above Earth's surface, take $r\approx6.37\times10^6\,\mathrm m$ and $GM\approx3.986\times10^{14}\,\mathrm{m^3\,s^{-2}}$. The circular speed and period are

$$
v=\sqrt{\frac{GM}{r}}\approx7.9\times10^3\,\mathrm{m\,s^{-1}},
\qquad
T=2\pi\sqrt{\frac{r^3}{GM}}\approx84\,\mathrm{min}.
$$

The satellite is continuously falling toward Earth, but its tangential speed makes the surface curve away beneath it. The estimate ignores the atmosphere, Earth's rotation and nonspherical shape, and the fact that a low orbit would rapidly lose altitude to drag.

## 7.5 Scattering by a central force

Not every central-force trajectory is bound. In a scattering experiment, an incoming particle approaches from far away, is deflected by the force, and departs again. For a repulsive inverse-square force with potential $U(r)=\kappa/r$, the unbound orbit is a hyperbola. If the incoming speed is $v_\infty$ and its impact parameter is $b$, then $L=mbv_\infty$. The deflection angle $\chi$ is

$$
\tan\frac{\chi}{2}=\frac{\kappa}{m b v_\infty^2}.
$$

The angle follows from the hyperbola's eccentricity. Far from the source, $E=\tfrac12mv_\infty^2$ and $L=mbv_\infty$, so the inverse-square orbit relation gives

$$
e^2=1+\frac{2EL^2}{m\kappa^2}
=1+\left(\frac{mbv_\infty^2}{\kappa}\right)^2.
$$

The geometry of the incoming and outgoing asymptotes gives $\sin(\chi/2)=1/e$. Combining this with $e^2-1=(mbv_\infty^2/\kappa)^2$ yields the displayed tangent formula. It predicts a small deflection for large impact parameter or high incoming speed, and a large deflection for a stronger interaction.

This relation underlies the classical analysis of Rutherford scattering, in which the angular distribution of scattered particles revealed that positive charge is concentrated in a small atomic nucleus. The ideal formula assumes a point source, a pure inverse-square force, and no energy loss.

## 7.6 What geometric algebra contributes

The important GA statement in this chapter is compact:

$$
\mathbf r\wedge\mathbf F=0
\quad\Longrightarrow\quad
\mathcal J=\mathbf r\wedge\mathbf p\text{ is constant}.
$$

In three dimensions, $\mathcal J$ identifies the fixed plane of motion without first choosing an axial-vector convention. The cross product $\mathbf r\times\mathbf p$ remains convenient for numerical calculations and for readers already comfortable with it. Once the orbital plane is chosen, polar coordinates, scalar energy, and the effective potential are clearer for finding orbit shapes and turning points. GA exposes the geometric reason the problem is planar; it does not make the standard conic calculation unnecessary.

## 7.7 What to remember

- A central force has zero torque about its centre, so angular momentum is conserved.
- A nonzero conserved angular-momentum bivector identifies a fixed plane of motion.
- Constant angular momentum gives constant areal velocity, Kepler's second law.
- Angular motion can be included in a radial effective potential, $U_{\mathrm{eff}}=U+L^2/(2mr^2)$.
- Under an inverse-square force, bound orbits are ellipses and unbound trajectories are parabolas or hyperbolas.
- GA is especially clear about the orbital plane; scalar energy methods are usually simpler for radial motion.

### Exercises

1. Show that $\mathbf r\wedge\mathbf F=0$ for any central force. Use $\dot{\mathcal J}=\mathbf r\wedge\mathbf F$ to explain why the orbit stays in a plane.
2. A particle has mass $0.50\,\mathrm{kg}$, radius $2.0\,\mathrm m$, and tangential speed $3.0\,\mathrm{m\,s^{-1}}$. Find the magnitude of its angular momentum and areal velocity.
3. Sketch $U_{\mathrm{eff}}(r)$ for an attractive inverse-square potential at nonzero angular momentum. Identify the circular orbit and explain which energies produce bound motion.
4. A satellite moves in a circular orbit of radius $4r_0$, where $r_0$ is the radius of another circular orbit about the same planet. Compare their speeds and periods.
5. For the inverse-square orbit equation, explain how the sign of total energy distinguishes ellipse, parabola, and hyperbola.
6. Explain what information is represented by $\mathcal J=LI$ and how it is related to the conventional vector $\mathbf L=\mathbf r\times\mathbf p$ in 3D.
7. **Synthesis.** Starting from the two-body relative equation with reduced mass $\mu$, derive $T^2=4\pi^2a^3/[G(m_1+m_2)]$. State the limit in which the fixed-source formula is recovered and explain which mass then plays the role of the source.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on central forces and planetary motion.
- OpenStax, *University Physics, Volume 1*, sections on gravitation and satellite orbits.
- David Hestenes, *New Foundations for Classical Mechanics*, for geometric-algebra treatments of orbital mechanics.
