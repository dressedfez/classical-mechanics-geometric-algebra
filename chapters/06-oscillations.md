---
title: "6. Oscillations"
description: "Introduce simple harmonic motion, energy exchange, phase, damping, driving, and resonance, with a geometric-algebra view of oscillator phase space."
---

A spring stretches when a mass is pulled from its resting position. When released, it pulls the mass back; the mass passes the resting position, stretches the spring in the other direction, and returns. The motion repeats because the restoring force reverses as the displacement reverses.

This simple pattern appears in pendulums, vibrating structures, musical instruments, and many systems close to a stable equilibrium. We will first derive the motion of an ideal spring and learn what amplitude, period, frequency, and phase mean. Then we will add energy, damping, and an external drive. Geometric algebra has a focused role: it represents the oscillator's changing state as a vector rotating in a two-dimensional phase plane. That plane is a mathematical picture of position and velocity, not an extra physical path through space.

## 6.1 A restoring force produces simple harmonic motion

Let $x$ measure the displacement of a mass from its equilibrium position. For an ideal spring, Hooke's law says that the spring force is proportional to the displacement and points back toward equilibrium:

$$
F=-kx,
$$

where $k>0$ is the spring constant. The minus sign expresses the restoring direction. Applying Newton's second law gives

$$
m\ddot{x}=-kx,
\qquad
\ddot{x}+\omega_0^2 x=0,
\qquad
\omega_0=\sqrt{\frac{k}{m}}.
$$

Here $\ddot{x}=d^2x/dt^2$ is the acceleration, and $\omega_0$ is the oscillator's **natural angular frequency**. The equation says that the acceleration is proportional to the displacement and opposite in direction. Motion with this property is called **simple harmonic motion** (SHM).

The cosine function solves the equation because differentiating it twice returns the negative of the same function. The general motion can therefore be written

$$
x(t)=A\cos(\omega_0 t+\phi),
$$

where $A\geq 0$ is the **amplitude**, the greatest distance from equilibrium, and $\phi$ is the **phase constant**, which specifies where in the cycle the motion begins at $t=0$. The phase at time $t$ is $\theta(t)=\omega_0t+\phi$.

One full cycle takes the **period** $T$. Since the phase advances by $2\pi$ radians in one cycle,

$$
T=\frac{2\pi}{\omega_0},
\qquad
f=\frac{1}{T}=\frac{\omega_0}{2\pi}.
$$

The frequency $f$ is measured in hertz, or cycles per second. Angular frequency $\omega_0$ is measured in radians per second. They describe the same repetition rate but are not numerically the same.

The velocity and acceleration follow by differentiating:

$$
v(t)=-A\omega_0\sin(\omega_0t+\phi),
\qquad
a(t)=-A\omega_0^2\cos(\omega_0t+\phi)=-\omega_0^2x(t).
$$

At the endpoints $x=\pm A$, the velocity is zero and the acceleration points toward the equilibrium position. As the mass passes through equilibrium, its speed is greatest and its acceleration is zero. This exchange between position and velocity is central to understanding the oscillator.

```{figure} ../figures/oscillation-phase-plane.svg
:label: fig-oscillation-phase-plane
:enumerator: "6.1"
:alt: A cosine displacement plotted over time beside a circular trajectory of the oscillator's state vector in the position and scaled-velocity plane.
:width: 100%

The displacement is the horizontal projection of a uniform rotation in the oscillator's state plane. The vertical coordinate is $-v/\omega_0$, scaled so it has the same units as $x$; it is not a second physical displacement.
```

### Worked example: a spring released from rest

A $0.50\,\mathrm{kg}$ mass is attached to a spring with $k=200\,\mathrm{N\,m^{-1}}$. It is pulled $0.040\,\mathrm m$ from equilibrium and released from rest. The natural angular frequency is

$$
\omega_0=\sqrt{\frac{200\,\mathrm{N\,m^{-1}}}{0.50\,\mathrm{kg}}}
=20\,\mathrm{rad\,s^{-1}}.
$$

Because the mass starts at its positive maximum displacement, $A=0.040\,\mathrm m$ and $\phi=0$. Thus

$$
x(t)=(0.040\,\mathrm m)\cos\bigl((20\,\mathrm{rad\,s^{-1}})t\bigr),
\qquad
T=\frac{2\pi}{20\,\mathrm{rad\,s^{-1}}}\approx0.31\,\mathrm s.
$$

After one quarter of a period, the mass passes equilibrium with its greatest speed, $v_{\max}=A\omega_0=0.80\,\mathrm{m\,s^{-1}}$.

## 6.2 Initial conditions determine amplitude and phase

The equation of motion has many solutions because the mass can start at different positions and with different velocities. The initial position $x_0$ and velocity $v_0$ fix the constants $A$ and $\phi$:

$$
x_0=A\cos\phi,
\qquad
v_0=-A\omega_0\sin\phi.
$$

Squaring these equations after dividing the second by $\omega_0$ gives

$$
A=\sqrt{x_0^2+\left(\frac{v_0}{\omega_0}\right)^2}.
$$

The phase is set by both initial values. Its quadrant matters, so it is safer to determine it from the signs of $x_0$ and $v_0$ than to use an inverse tangent without checking the signs. For example, starting at equilibrium with velocity in the positive direction means $x_0=0$ and $v_0>0$, so $\phi=-\pi/2$ is one valid choice.

The amplitude is therefore determined by the oscillator's initial state, not just by how far it is pulled. A smaller initial displacement can still give a large amplitude if the mass is launched quickly.

## 6.3 Energy moves between spring and mass

The spring's potential energy, measured relative to equilibrium, is $U=\tfrac12kx^2$. The mass's kinetic energy is $K=\tfrac12mv^2$. For the ideal oscillator, their sum is constant:

$$
E=K+U=\frac{1}{2}mv^2+\frac{1}{2}kx^2.
$$

At a turning point, the energy is entirely spring potential energy; at equilibrium, it is entirely kinetic energy. At intermediate positions, it is shared. Substituting the expressions for $x(t)$ and $v(t)$ shows the conservation directly:

$$
E=\frac{1}{2}mA^2\omega_0^2\sin^2(\omega_0t+\phi)
+\frac{1}{2}kA^2\cos^2(\omega_0t+\phi)
=\frac{1}{2}kA^2,
$$

because $k=m\omega_0^2$ and $\sin^2\theta+\cos^2\theta=1$. This is the energy method from Chapter 4 applied to a repeating motion.

## 6.4 Phase as a rotation: complex numbers and geometric algebra

The real-variable solution $x(t)=A\cos(\omega_0t+\phi)$ is usually the clearest way to calculate the physical displacement. A second description packages the position and velocity into a single rotating phase.

In complex notation, define

$$
z_{\mathbb C}=x-i\frac{v}{\omega_0}.
$$

For simple harmonic motion this becomes $z_{\mathbb C}=A e^{i(\omega_0t+\phi)}$, so $\dot z_{\mathbb C}=i\omega_0z_{\mathbb C}$. The real part gives the displacement, while the imaginary part carries the velocity information with the scaling needed to give both components the same units.

First define a vector in an abstract two-dimensional **state plane**:

$$
\mathbf q(t)=x(t)\mathbf e_1-\frac{v(t)}{\omega_0}\mathbf e_2,
$$

where $\mathbf e_1$ and $\mathbf e_2$ are perpendicular unit directions in that plane. The factor $v/\omega_0$ has units of length, so both components can be compared. The state plane is not physical space: its first coordinate records displacement, while its second records scaled velocity.

The physical variables can be recovered by projection: $x=\mathbf q\cdot\mathbf e_1$ and $v=-\omega_0\,\mathbf q\cdot\mathbf e_2$.

For an ideal oscillator, $a=-\omega_0^2x$. Differentiating the state vector gives

$$
\dot{\mathbf q}
=v\mathbf e_1-\frac{a}{\omega_0}\mathbf e_2
=v\mathbf e_1+\omega_0x\mathbf e_2.
$$

Let $\mathbf I=\mathbf e_1\mathbf e_2$ be the unit bivector of this plane. From Chapter 2, $\mathbf e_1\mathbf I=\mathbf e_2$ and $\mathbf e_2\mathbf I=-\mathbf e_1$. Therefore

$$
\dot{\mathbf q}=\omega_0\mathbf q\mathbf I.
$$

This equation says that the state vector turns uniformly in its plane. Its solution can be written

$$
\mathbf q(t)=\mathbf q(0)\exp(\mathbf I\omega_0t),
\qquad
\exp(\mathbf I\theta)=\cos\theta+\mathbf I\sin\theta.
$$

The exponential has the same algebraic form as a complex phase, with the plane bivector $\mathbf I$ playing the role of $i=\sqrt{-1}$. Since

$$
\mathbf q^2=x^2+\left(\frac{v}{\omega_0}\right)^2=A^2,
$$

the ideal oscillator's state moves around a circle of radius $A$ in this plane. The conserved energy can also be read from that radius:

$$
E=\frac{1}{2}m\omega_0^2\mathbf q^2.
$$

The three descriptions emphasize different things. The real equation gives the physical displacement directly. A complex number makes sinusoidal phase calculations compact. The GA state vector shows that phase evolution is a rotation in a plane and connects its magnitude to energy. For a one-dimensional spring calculation, the real equation is normally quickest; the GA representation is useful when we want to understand the geometry of phase or connect oscillations with rotations.

## 6.5 A pendulum as an approximate oscillator

A simple pendulum of length $\ell$ and bob mass $m$ is not an exact harmonic oscillator at every amplitude. If $\theta$ is its angle from the downward vertical, the tangential component of gravity gives

$$
\ddot{\theta}+\frac{g}{\ell}\sin\theta=0.
$$

For small angles measured in radians, $\sin\theta\approx\theta$. The equation then becomes

$$
\ddot{\theta}+\frac{g}{\ell}\theta=0,
\qquad
\omega_0=\sqrt{\frac{g}{\ell}},
\qquad
T\approx2\pi\sqrt{\frac{\ell}{g}}.
$$

To this approximation, the period does not depend on the bob's mass. At larger amplitudes the approximation fails, and the period increases slightly with amplitude. This is a useful example of how SHM describes motion close to equilibrium rather than every possible motion of a system.

## 6.6 Damping: why real oscillations die away

In a real oscillator, friction or resistance transfers mechanical energy to the surroundings. A common model for a small mass moving through a fluid or attached to a dashpot is a damping force proportional to velocity and opposite to the motion:

$$
F_{\mathrm d}=-b\dot{x},
\qquad
m\ddot{x}+b\dot{x}+kx=0,
$$

where $b>0$ is the damping coefficient. This is a model of **viscous damping**; dry friction, which is approximately independent of speed, needs a different model.

For weak damping, the motion continues to oscillate while its amplitude decays:

$$
x(t)=A_0e^{-\gamma t}\cos(\omega_{\mathrm d}t+\phi),
\qquad
\gamma=\frac{b}{2m},
\qquad
\omega_{\mathrm d}=\sqrt{\omega_0^2-\gamma^2}.
$$

This **underdamped** case requires $\gamma<\omega_0$. The oscillation frequency is slightly lower than the undamped natural frequency, and the envelope $A_0e^{-\gamma t}$ shrinks with time. At critical damping, the mass returns to equilibrium as quickly as possible without oscillating. With stronger, overdamping, it returns without oscillating but more slowly.

In the state plane from the previous section, weak damping turns the circular path into an inward spiral: the oscillator loses amplitude as it loses energy.

The energy lost per unit time follows from the work done by the damping force:

$$
\frac{dE}{dt}=F_{\mathrm d}v=-bv^2\leq0.
$$

The minus sign shows that damping removes mechanical energy for either direction of motion. The energy is transferred to internal energy in the damper and surroundings.

## 6.7 Driving and resonance

An external force can keep an oscillator moving. Suppose the force varies sinusoidally with angular frequency $\Omega$:

$$
m\ddot{x}+b\dot{x}+kx=F_0\cos(\Omega t).
$$

After an initial transient has died away, the oscillator moves at the drive frequency. Its steady-state displacement can be written $x(t)=A(\Omega)\cos(\Omega t-\delta)$, where the amplitude is

$$
A(\Omega)=\frac{F_0}{\sqrt{(k-m\Omega^2)^2+(b\Omega)^2}}.
$$

To compare different oscillators, define the dimensionless drive frequency $r=\Omega/\omega_0$ and damping ratio $\zeta=b/(2m\omega_0)$. The amplitude relative to the static displacement $F_0/k$ is

$$
\frac{A}{F_0/k}=\frac{1}{\sqrt{(1-r^2)^2+(2\zeta r)^2}}.
$$

The phase lag $\delta$ depends on the drive frequency and damping. At low frequency the mass nearly follows the force; near resonance the displacement lags by about a quarter cycle; at high frequency it is nearly opposite in phase to the drive.

When $\zeta<1/\sqrt{2}$, the displacement amplitude has a peak at

$$
\Omega_{\mathrm r}=\omega_0\sqrt{1-2\zeta^2}.
$$

For weak damping this frequency is close to the natural frequency. With stronger damping, the nonzero-frequency peak disappears. A strong response near the peak is called **resonance**: a periodic force transfers energy especially effectively when it pushes in step with the oscillator's motion. Damping limits the amplitude. For an ideal undamped oscillator driven exactly at its natural frequency, no finite steady-state amplitude exists; the amplitude grows over time as energy continues to accumulate.

```{figure} ../figures/oscillation-resonance.svg
:label: fig-oscillation-resonance
:enumerator: "6.2"
:alt: Normalized steady-state amplitude of a driven oscillator versus drive frequency for three damping levels, with a sharper and higher peak for weaker damping.
:width: 90%

The normalized amplitude $A/(F_0/k)$ is plotted against $\Omega/\omega_0$. Weaker damping produces a taller, narrower resonance peak. The plotted curves use the linear viscous-damping model.
```

Resonance can be useful, as in musical instruments, or damaging, as in a structure driven strongly near one of its natural frequencies. Engineers often reduce unwanted motion by adding damping or by changing a structure's mass and stiffness so its natural frequency moves away from likely driving frequencies.

## 6.8 What to remember

- A linear restoring force $F=-kx$ produces SHM, with $\omega_0=\sqrt{k/m}$ and $T=2\pi/\omega_0$.
- In $x=A\cos(\omega_0t+\phi)$, amplitude sets the maximum displacement and phase sets the initial state.
- In ideal SHM, energy moves between kinetic and potential forms while $E=\tfrac12mv^2+\tfrac12kx^2$ stays constant.
- The GA state vector $\mathbf q=x\mathbf e_1-(v/\omega_0)\mathbf e_2$ rotates uniformly in an abstract phase plane; its squared magnitude is $A^2$.
- Viscous damping removes mechanical energy. Weak damping gives decaying oscillations; critical and strong damping return the system to equilibrium without oscillation.
- A periodic drive produces a steady response at its own frequency. Near resonance, the amplitude is large, with damping limiting its size.

### Exercises

1. A $0.25\,\mathrm{kg}$ mass is attached to a spring with $k=100\,\mathrm{N\,m^{-1}}$. Find its natural angular frequency, frequency, and period.
2. An oscillator has $\omega_0=5.0\,\mathrm{rad\,s^{-1}}$, initial position $x_0=0.030\,\mathrm m$, and initial velocity $v_0=-0.20\,\mathrm{m\,s^{-1}}$. Find its amplitude. Determine a phase $\phi$ consistent with these initial conditions.
3. For $x(t)=A\cos(\omega_0t+\phi)$, derive the velocity and acceleration, and verify that $\ddot{x}=-\omega_0^2x$.
4. A $0.40\,\mathrm{kg}$ mass on a spring with $k=160\,\mathrm{N\,m^{-1}}$ is released from rest at $x=0.050\,\mathrm m$. Find its maximum speed and total mechanical energy.
5. A simple pendulum has length $0.90\,\mathrm m$. Estimate its period for small oscillations using $g=9.81\,\mathrm{m\,s^{-2}}$. Explain why its mass does not appear in the result.
6. For the state vector $\mathbf q=x\mathbf e_1-(v/\omega_0)\mathbf e_2$, use $\mathbf e_1\mathbf I=\mathbf e_2$ and $\mathbf e_2\mathbf I=-\mathbf e_1$ to show that $\dot{\mathbf q}=\omega_0\mathbf q\mathbf I$.
7. Show that $\mathbf q^2=A^2$ for an undamped oscillator. Use this result to write its energy in terms of $\mathbf q^2$.
8. A damped oscillator has $m=0.50\,\mathrm{kg}$, $k=50\,\mathrm{N\,m^{-1}}$, and $b=2.0\,\mathrm{kg\,s^{-1}}$. Find $\gamma$ and $\omega_{\mathrm d}$, and state whether the system is underdamped.
9. Explain why the amplitude of a driven, damped oscillator is largest near its natural frequency. What happens to the peak as damping increases?
10. A structure has a natural frequency of $2.0\,\mathrm{Hz}$ and is subject to a periodic force at $1.9\,\mathrm{Hz}$. Explain why this may produce a larger response than a force at $5.0\,\mathrm{Hz}$. Name two ways to reduce the response.

## Further reading

- OpenStax, [*University Physics, Volume 1*, Chapter 15: Oscillations](https://openstax.org/books/university-physics-volume-1/pages/15-introduction), covering simple harmonic motion, energy, pendulums, damping, and forced oscillations.
- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), for a more extended undergraduate treatment of oscillations and forced motion.
- David Hestenes, [*New Foundations for Classical Mechanics*](https://davidhestenes.net/geocalc/html/NFCM.html), for geometric-algebra perspectives on oscillatory motion and rotations.
