---
title: "4. Work, Energy, and Conservative Forces"
description: "Derive the work-energy theorem from Newton's laws, use energy to solve motion problems, and interpret conservative forces and potential-energy diagrams."
---

In Chapter 3, we used forces to predict acceleration and then followed how position and velocity changed in time. There is another way to organize many of the same problems. Instead of tracking the full motion, we can ask how much work a force does and how that work changes the kinetic energy.

Energy methods are especially useful when we want to find a speed at a particular position, a maximum height, or whether a particle can pass a barrier. They often avoid solving for the motion at every intermediate time. The methods begin with Newton's second law, so they complement rather than replace the force-based approach.

## 4.1 Work: force along a displacement

In everyday language, work can mean effort. In mechanics, work has a precise meaning: a force does work on a body when it transfers energy through a displacement. For a constant force, if it is perpendicular to the displacement, it does no work. More generally, a force perpendicular to the instantaneous displacement throughout the motion does no work.

For a constant force $\mathbf F$ and a displacement $\Delta\mathbf r$, the work is

$$
W=\mathbf F\cdot\Delta\mathbf r
=F\,\Delta r\cos\theta,
$$

where $\theta$ is the angle between the force and the displacement. Work is a scalar. Its sign records whether the force tends to increase or decrease the body's kinetic energy:

- If the force points partly along the displacement, it does positive work.
- If it points partly against the displacement, it does negative work.
- If it is perpendicular to the displacement, it does zero work.

Work is measured in joules: $1\,\mathrm{J}=1\,\mathrm{N\,m}$. A joule is the work done by a one-newton force acting through a one-metre displacement in its direction.

### Worked example: pulling a suitcase

A person pulls a suitcase with a force of $40\,\mathrm{N}$ directed $30^\circ$ above the horizontal. The suitcase moves $5.0\,\mathrm{m}$ horizontally. The work done by the pulling force is

$$
W_{\mathrm{pull}}
=F\,\Delta r\cos\theta
=(40\,\mathrm{N})(5.0\,\mathrm{m})\cos 30^\circ
\approx 1.7\times10^2\,\mathrm{J}.
$$

Only the horizontal component of the pull contributes. The suitcase also experiences gravity and an upward normal force from the floor. Since its displacement is horizontal, those vertical forces do no work. If friction acts, its work is negative and must be included when finding the **net** work.

The force that keeps an object moving in a circle provides a useful connection to Chapter 3. In uniform circular motion, the inward net force is perpendicular to the instantaneous velocity and displacement. It therefore does no work: it changes the direction of the velocity, but not its speed.

## 4.2 Work when the force changes

For a force that varies with position or direction, divide the path into many short displacements. Over a sufficiently short piece, the force is nearly constant, so the small amount of work is $dW=\mathbf F\cdot d\mathbf r$. Adding these contributions and taking the limit gives the work along a path $C$:

$$
W_{A\to B}=\int_C\mathbf F\cdot d\mathbf r.
$$

The dot product selects the component of force along the path. In one dimension, where motion is along the $x$ axis, this becomes

$$
W_{x_A\to x_B}=\int_{x_A}^{x_B}F_x(x)\,dx.
$$

On a graph of $F_x$ against $x$, this integral is the signed area between the force curve and the horizontal axis. Area above the axis contributes positive work; area below it contributes negative work. In {numref}`fig-work-area`, the force $F_x=4.0x\,\mathrm{N}$ acts from $x=0$ to $x=2.0\,\mathrm{m}$, so the work is the triangular area, $8.0\,\mathrm{J}$.

```{figure} ../figures/work-force-graph.svg
:label: fig-work-area
:enumerator: "4.1"
:alt: Graph of a linearly increasing force against position, with the positive area under the curve shaded to represent work.
:width: 85%

For motion along one axis, work is the signed area under the graph of force component $F_x$ against position $x$. The example shown has $F_x=4.0x\,\mathrm{N}$ from $0$ to $2.0\,\mathrm{m}$.
```

If a force changes along a path, the work may depend on the path taken. We will soon identify an important class of forces for which it depends only on the endpoints.

## 4.3 The work-energy theorem

The **kinetic energy** of a particle of mass $m$ and speed $v$ is

$$
K=\frac{1}{2} mv^2.
$$

Kinetic energy is a scalar, even though velocity is a vector. It depends on speed, not direction. The work-energy theorem follows directly from Newton's second law for a particle of constant mass. The chain rule gives

$$
\frac{dK}{dt}
=\frac{d}{dt}\left(\frac{1}{2}m\,\mathbf v\cdot\mathbf v\right)
=m\mathbf v\cdot\frac{d\mathbf v}{dt}
=m\mathbf v\cdot\mathbf a
=\mathbf F_{\mathrm{net}}\cdot\mathbf v.
$$

Since $d\mathbf r=\mathbf v\,dt$, multiplying by $dt$ identifies the last expression with the rate of work. Integrating between an initial state $i$ and a final state $f$ gives

```{note} Work-energy theorem

The net work done on a particle equals its change in kinetic energy:

$$
W_{\mathrm{net}}=K_f-K_i=\Delta K.
$$
```

This result does not require the net force to be constant, and it does not require the path to be straight. It relates the total work over the motion to the speeds at the endpoints. To find the force or acceleration at each instant, Newton's second law is still the direct tool; to find a speed after a known displacement, work and energy may be simpler.

### Worked example: a force that varies with position

A particle moves along the $x$ axis under the force $F_x=4.0x\,\mathrm{N}$, with $x$ measured in metres. As it moves from $x=0$ to $x=2.0\,\mathrm{m}$, the force does

$$
W=\int_0^{2.0\,\mathrm{m}}(4.0\,\mathrm{N\,m^{-1}})x\,dx
=\frac{1}{2}(4.0\,\mathrm{N\,m^{-1}})(2.0\,\mathrm{m})^2
=8.0\,\mathrm{J}.
$$

If the particle has mass $2.0\,\mathrm{kg}$ and starts from rest, then $K_f=8.0\,\mathrm{J}$. Its final speed is

$$
v_f=\sqrt{\frac{2K_f}{m}}
=\sqrt{\frac{2(8.0\,\mathrm{J})}{2.0\,\mathrm{kg}}}
=2.8\,\mathrm{m\,s^{-1}}.
$$

The graph in {numref}`fig-work-area` lets us evaluate the same work geometrically. The theorem avoids solving the time-dependent equation of motion for this example.

## 4.4 Power: how quickly work is done

Work tells us the amount of energy transferred. **Power** tells us how quickly that transfer occurs. The average power over a time interval is the work done divided by elapsed time:

$$
P_{\mathrm{avg}}=\frac{\Delta W}{\Delta t}.
$$

Instantaneous power is

$$
P=\frac{dW}{dt}.
$$

For a force acting on a moving particle, $dW=\mathbf F\cdot d\mathbf r$ and $d\mathbf r/dt=\mathbf v$, so

$$
P=\mathbf F\cdot\mathbf v.
$$

Power is measured in watts, where $1\,\mathrm{W}=1\,\mathrm{J\,s^{-1}}$. A force can do a given amount of work slowly or quickly; the work is the same, but the power differs.

### Worked example: lifting a box at constant speed

A motor lifts a $15\,\mathrm{kg}$ box vertically at a steady speed of $0.50\,\mathrm{m\,s^{-1}}$. The motor's upward force balances the weight, so the power it supplies is

$$
P=\mathbf F\cdot\mathbf v=mgv
=(15\,\mathrm{kg})(9.8\,\mathrm{m\,s^{-2}})(0.50\,\mathrm{m\,s^{-1}})
\approx 74\,\mathrm{W}.
$$

The box's kinetic energy does not change, because its speed is constant. The motor's positive work and gravity's negative work cancel in the work-energy theorem. The motor still transfers energy to the box-Earth system by increasing its gravitational potential energy.

## 4.5 Conservative forces and potential energy

For some forces, the work from point A to point B is independent of the route. Such a force is called **conservative**. Equivalently, the work done by a conservative force around any closed path is zero. In ordinary introductory mechanics, gravity and the ideal spring force are the main examples.

For a conservative force, we define the change in potential energy by the negative of the work done by that force:

$$
\Delta U=U_f-U_i=-W_{\mathrm{cons},\,i\to f}.
$$

If the force does positive work, the potential energy of the chosen system decreases. Potential energy belongs to an interaction or system: gravitational potential energy describes the object-Earth system, while elastic potential energy describes the spring-object system. Its zero is a reference choice. Adding a constant to every value of $U$ changes no force and no prediction of motion.

In one dimension, an infinitesimal displacement gives $dW_{\mathrm{cons}}=F_x\,dx$. It follows that

$$
F_x=-\frac{dU}{dx}.
$$

The force points in the direction in which potential energy decreases most rapidly. In three dimensions this relation is written $\mathbf F=-\boldsymbol\nabla U$. The gradient $\boldsymbol\nabla U$ is a vector whose components give the rate at which potential energy changes along each coordinate direction. We will rely mainly on the one-dimensional form in this chapter.

### Gravitational potential energy near Earth

Choose the vertical coordinate $y$ to point upward and set $U_g=0$ at a convenient reference height. Near Earth's surface, the gravitational force is $F_y=-mg$. Since $F_y=-dU_g/dy$, integrating with respect to height gives

$$
U_g(y)=mgy,
$$

up to the arbitrary additive constant just discussed. Raising an object increases the gravitational potential energy of the object-Earth system. Lowering it decreases that energy, and gravity can do positive work.

### Elastic potential energy of a spring

For an ideal spring displaced by $x$ from its relaxed position, Hooke's law gives $F_x=-kx$, where $k$ is the spring constant. The corresponding potential energy is

$$
U_s(x)=\frac{1}{2}kx^2,
$$

again choosing zero at $x=0$. Compressing or stretching the spring stores energy in the spring-object system. On release, the spring force can transfer that energy to kinetic energy.

## 4.6 Mechanical energy and nonconservative work

Separate the net work into conservative and nonconservative parts:

$$
W_{\mathrm{net}}=W_{\mathrm{cons}}+W_{\mathrm{noncons}}.
$$

The work-energy theorem says $W_{\mathrm{net}}=\Delta K$, while the definition of potential energy gives $W_{\mathrm{cons}}=-\Delta U$. Combining these relations yields

$$
\Delta(K+U)=W_{\mathrm{noncons}}.
$$

The sum $E_{\mathrm{mech}}=K+U$ is the **mechanical energy**. If nonconservative forces do no work, mechanical energy stays constant:

```{note} Conservation of mechanical energy

When only conservative forces do work on a system,

$$
K_i+U_i=K_f+U_f.
$$
```

Friction often does negative work on the moving part of a system, reducing its mechanical energy. The energy has not vanished: some has become thermal energy and microscopic deformation in the surfaces. If we enlarge the system to include those internal forms, total energy is conserved. Which system we choose determines which energy transfers appear explicitly in our equation.

### Worked example: a spring launcher

A $0.50\,\mathrm{kg}$ cart is released from rest while a spring of constant $k=200\,\mathrm{N\,m^{-1}}$ is compressed by $0.15\,\mathrm{m}$. Assume a level track and negligible friction. Initially the energy is spring potential energy; as the cart passes the spring's relaxed position, that energy has become kinetic:

$$
\frac{1}{2}kx^2=\frac{1}{2}mv^2.
$$

Thus,

$$
v=x\sqrt{\frac{k}{m}}
=(0.15\,\mathrm{m})\sqrt{\frac{200\,\mathrm{N\,m^{-1}}}{0.50\,\mathrm{kg}}}
=3.0\,\mathrm{m\,s^{-1}}.
$$

The energy method gives the speed at the relaxed position directly. A force-based solution would also work, but it would require solving the spring's equation of motion.

### Worked example: a sled with friction

A $2.0\,\mathrm{kg}$ sled starts from rest and descends a track with a vertical drop of $2.5\,\mathrm{m}$. Friction does $-9.0\,\mathrm{J}$ of work. Choose the bottom of the track as the zero of gravitational potential energy. The change in gravitational potential energy is $-mgh$, and the mechanical-energy equation gives

$$
\begin{aligned}
K_f+U_f-(K_i+U_i)&=W_{\mathrm{fr}},\\
K_f&=mgh+W_{\mathrm{fr}}\\
&=(2.0\,\mathrm{kg})(9.8\,\mathrm{m\,s^{-2}})(2.5\,\mathrm{m})-9.0\,\mathrm{J}\\
&=40\,\mathrm{J}.
\end{aligned}
$$

The sled's speed at the bottom is therefore

$$
v_f=\sqrt{\frac{2K_f}{m}}
=\sqrt{\frac{2(40\,\mathrm{J})}{2.0\,\mathrm{kg}}}
\approx6.3\,\mathrm{m\,s^{-1}}.
$$

The friction work depends on the distance traveled along the track, while the work by gravity depends only on the vertical drop. We do not need the detailed shape of the track to find the final speed, as long as the stated work by friction is known.

## 4.7 Reading a potential-energy diagram

A graph of $U(x)$ can reveal how a particle moves without first solving its full equation of motion. If only conservative forces act, its total mechanical energy $E=K+U$ is constant, so

$$
K(x)=E-U(x).
$$

Since kinetic energy cannot be negative, the particle can be found only where $U(x)\le E$. Where the potential curve rises to the energy level, $K=0$: these positions are **turning points** for ordinary one-dimensional motion. Between them, the difference $E-U$ determines the kinetic energy and hence the speed.

Equilibrium positions occur where the force is zero, or $dU/dx=0$. A small displacement from a local minimum produces a force back toward the minimum, so that equilibrium is stable. A small displacement from a local maximum produces a force away from the maximum, so that equilibrium is unstable. {numref}`fig-energy-diagrams` shows these ideas for a spring-like potential well and for local minima and maxima.

```{figure} ../figures/potential-energy-diagrams.svg
:label: fig-energy-diagrams
:enumerator: "4.2"
:alt: Potential-energy diagrams showing a total-energy line and turning points in a well, plus stable equilibrium at a minimum and unstable equilibrium at a maximum.
:width: 80%

Left: a particle with total energy $E$ is confined between turning points where $U=E$; it moves where $U\le E$. Right: a local minimum is stable, while a local maximum is unstable.
```

### Worked example: the maximum height of a thrown ball

A ball is thrown vertically upward from ground level at $v_0=10.0\,\mathrm{m\,s^{-1}}$. Neglect air resistance and choose $U_g=0$ at the launch point. At the top, the speed is zero, so conservation of mechanical energy gives

$$
\frac{1}{2}mv_0^2=mgh_{\max}.
$$

The mass cancels, leaving

$$
h_{\max}=\frac{v_0^2}{2g}
=\frac{(10.0\,\mathrm{m\,s^{-1}})^2}{2(9.8\,\mathrm{m\,s^{-2}})}
\approx5.1\,\mathrm{m}.
$$

This gives the maximum height without finding the time of flight. Chapter 3's constant-acceleration equations give the same answer and also provide the time; the energy method is more direct for this particular question.

## 4.8 Choosing between force and energy methods

Newton's second law gives the acceleration at each instant once the force is known. It is the natural method when the question asks for acceleration, force, or the time-dependent trajectory. The energy method relates endpoints and is often quicker when the forces are conservative or when the nonconservative work is known.

Work uses the scalar product $\mathbf F\cdot d\mathbf r$. In geometric algebra, this is the scalar part of the geometric product:

$$
\mathbf F\cdot d\mathbf r=\left\langle\mathbf F\,d\mathbf r\right\rangle_0.
$$

## 4.9 What to remember

- Work measures energy transferred by a force through displacement; only the force component along the path contributes.
- The net work equals the change in kinetic energy: $W_{\mathrm{net}}=\Delta K$.
- Power is the rate of work and, for a particle, $P=\mathbf F\cdot\mathbf v$.
- A conservative force has path-independent work and can be described by a potential energy, with $F_x=-dU/dx$.
- Mechanical energy $K+U$ is conserved when nonconservative work is zero. Friction can reduce mechanical energy while total energy remains conserved.
- A potential-energy graph shows allowed positions, turning points, and the stability of equilibrium positions.

### Exercises

1. A force of $30\,\mathrm{N}$ pulls a crate $4.0\,\mathrm{m}$ along a horizontal floor. Find the work if the force is directed (a) along the motion, (b) at $60^\circ$ above the horizontal, and (c) perpendicular to the motion.
2. A $5.0\,\mathrm{kg}$ box is lifted vertically by $2.0\,\mathrm{m}$ at constant speed. Find the work done by the lifting force and by gravity. What is the net work?
3. A particle moves along the $x$ axis under the force $F_x=(3.0\,\mathrm{N\,m^{-1}})x+2.0\,\mathrm{N}$. Find the work done as it moves from $x=0$ to $x=2.0\,\mathrm{m}$.
4. Starting from Newton's second law for constant mass, derive the work-energy theorem using $d\mathbf r=\mathbf v\,dt$.
5. A $1200\,\mathrm{kg}$ car travels at $20\,\mathrm{m\,s^{-1}}$ on a level road. Its engine's forward force balances a $500\,\mathrm{N}$ resistive force. What power does the engine supply to maintain this speed?
6. A spring with $k=300\,\mathrm{N\,m^{-1}}$ is compressed by $0.10\,\mathrm{m}$. Find its elastic potential energy relative to the relaxed position. How much work does the spring do as it returns to that position?
7. A $0.80\,\mathrm{kg}$ block slides from rest down a frictionless ramp through a vertical drop of $1.2\,\mathrm{m}$. Find its speed at the bottom. Would the ramp's length affect your answer?
8. A $1.0\,\mathrm{kg}$ sled starts from rest and descends through $3.0\,\mathrm{m}$ vertically. Friction does $-8.0\,\mathrm{J}$ of work. Find its speed at the bottom and state where the lost mechanical energy has gone in a more complete description.
9. A ball is thrown upward at $14\,\mathrm{m\,s^{-1}}$. Use an energy diagram or conservation of energy to find its maximum height above the launch point, neglecting air resistance.
10. Sketch $U(x)=\frac{1}{2}kx^2$ and draw a total-energy line above its minimum. Mark the turning points and identify where the particle has greatest speed.
11. For each equilibrium shown in {numref}`fig-energy-diagrams`, state whether a small displacement produces a restoring force or drives the particle farther away. Explain using $F_x=-dU/dx$.
12. In uniform circular motion, the inward net force is perpendicular to the velocity. Use $P=\mathbf F\cdot\mathbf v$ to show that the force does no instantaneous work. Explain how the speed can remain constant while the velocity changes.

## Further reading

- OpenStax, [*University Physics, Volume 1*, Chapter 7: Work and Kinetic Energy](https://openstax.org/books/university-physics-volume-1/pages/7-introduction), especially its sections on [work](https://openstax.org/books/university-physics-volume-1/pages/7-1-work), the [work-energy theorem](https://openstax.org/books/university-physics-volume-1/pages/7-3-work-energy-theorem), and [power](https://openstax.org/books/university-physics-volume-1/pages/7-4-power).
- OpenStax, [*University Physics, Volume 1*, Chapter 8: Potential Energy and Conservation of Energy](https://openstax.org/books/university-physics-volume-1/pages/8-introduction), especially [potential energy](https://openstax.org/books/university-physics-volume-1/pages/8-1-potential-energy-of-a-system), [conservation of energy](https://openstax.org/books/university-physics-volume-1/pages/8-3-conservation-of-energy), and [potential-energy diagrams and stability](https://openstax.org/books/university-physics-volume-1/pages/8-4-potential-energy-diagrams-and-stability).
- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), for a more extended undergraduate treatment of Newtonian mechanics and energy methods.
