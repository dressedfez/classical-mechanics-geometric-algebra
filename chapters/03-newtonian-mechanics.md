---
title: "3. From Galileo to Newton: Laws of Motion"
description: "A student-oriented introduction to kinematics, inertial frames, Newton's three laws, simple force models, and a geometric-algebra view of circular motion."
---

You already know the basic laws of mechanics from school. This chapter revisits them with a broader question in mind: why are the laws written in this particular way, and what do they let us predict?

The story begins before Newton. Galileo studied falling bodies, inclined planes, and projectiles, and used idealized reasoning to understand motion when friction is reduced or set aside. Newton brought such work, along with the work of other predecessors, into a mathematical framework. His three laws describe how motion behaves, how forces change it, and how bodies interact.

We will first review the language of motion and vector derivatives. Then we will examine each of Newton's laws, one at a time, with examples. Finally, we will return to circular motion and see how the geometric algebra developed in Chapter 2 expresses its geometry compactly.

## 3.1 Why motion needs explanation

Push a book across a table and it soon stops. It is tempting to conclude that motion requires a continuing force. But while the book slides, the table exerts friction on it. If the surface is made smoother, the book travels farther before slowing down. The observation suggests a different question: what would the motion be like if the opposing effects could be reduced still further?

Galileo combined experiments with idealized arguments. In his inclined-plane experiment, he rolled a ball down a smooth, grooved board raised by a small angle. The shallow slope made the motion slow enough to time: Galileo estimated elapsed time from the amount of water that flowed from a vessel and could then be weighed. He reported that the distance traveled from rest was proportional to the square of the elapsed time. One comparison in his account is especially memorable: the ball traveled one quarter of the track in half the time needed for the whole track. The plot in {numref}`fig-galileo-incline` illustrates that reported relation; it is a schematic, not a reproduction of Galileo's measurements.

```{figure} ../figures/galileo-inclined-plane.svg
:label: fig-galileo-incline
:enumerator: "3.1"
:alt: Schematic of Galileo's inclined-plane timing method and the quadratic distance-time relation he reported.
:width: 100%

Galileo's inclined-plane experiment used a shallow grooved board to slow a rolling ball. Water collected during the run served as a timing measure. The normalized curve illustrates the reported relation $s\propto t^2$; its markers are not raw historical data.
```

This was evidence for a mathematical account of accelerated motion, under the assumptions that the ball rolled smoothly and the timing method was adequate. It was not a direct experimental test of all three laws Newton would later formulate. Galileo also used a separate idealized argument: a ball that descends one slope and climbs a second tends to regain its original height. As the second slope becomes shallower, it must travel farther; in the horizontal, frictionless limit, it would keep moving. {numref}`fig-galileo-inertia` distinguishes this inertia argument from the timed experiment. In both cases, real observations guide an idealization, and the idealization lets us ask what remains when friction and other complications are reduced.

```{figure} ../figures/galileo-inertia.svg
:label: fig-galileo-inertia
:enumerator: "3.2"
:alt: Diagram of Galileo's idealized two-incline argument, with shallower rising tracks requiring longer travel to regain the same height.
:width: 100%

An idealized two-incline argument for inertia. The horizontal, frictionless case is a limiting extrapolation, not a track on which all resistance has literally been removed.
```

Galileo's work on falling bodies and projectiles likewise treated motion mathematically and separated ideal motion from effects such as air resistance. His *Two New Sciences* is a primary source for this approach; an accessible translation is available through the [University of Virginia's Galileo collection](https://galileoandeinstein.phys.virginia.edu/tns_draft/).

Newton's *Mathematical Principles of Natural Philosophy*, first published in 1687, set out three laws of motion and used them in a much wider account of terrestrial and celestial motion. The development was not a single leap by one person: Newton built on a long line of work, including Galileo's. The laws are principles in a physical model. Their usefulness comes from how well that model predicts observations within its domain.

The first law will formalize the ideal of motion without a net force. The second will tell us how a net force changes momentum. The third will describe the mutual character of interactions. Before stating them, we need a precise language for describing motion.

## 3.2 Describing motion and differentiating vectors

Choose a reference frame and an origin. The position of a particle at time $t$ is represented by a vector $\mathbf r(t)$. The vector contains both the particle's distance from the origin and its direction from the origin.

The average velocity over a time interval $\Delta t$ is the displacement divided by the elapsed time. The instantaneous velocity is the limit as that interval becomes small:

$$
\mathbf v(t)=\frac{d\mathbf r}{dt}.
$$

Velocity tells us the direction and rate at which position changes. Acceleration is the rate of change of velocity:

$$
\mathbf a(t)=\frac{d\mathbf v}{dt}
=\frac{d^2\mathbf r}{dt^2}.
$$

A vector can change in magnitude, direction, or both. Acceleration records any such change. A particle moving at constant speed around a circle, for example, is accelerating because its velocity direction changes continuously.

To calculate a derivative, choose a fixed orthonormal basis $\mathbf e_1,\mathbf e_2,\mathbf e_3$ and write

$$
\mathbf r(t)=x(t)\mathbf e_1+y(t)\mathbf e_2+z(t)\mathbf e_3.
$$

Because the basis vectors are fixed in this frame, differentiating the vector means differentiating its scalar components:

$$
\mathbf v(t)=\dot x(t)\mathbf e_1+\dot y(t)\mathbf e_2+\dot z(t)\mathbf e_3,
\qquad
\mathbf a(t)=\ddot x(t)\mathbf e_1+\ddot y(t)\mathbf e_2+\ddot z(t)\mathbf e_3.
$$

A dot denotes differentiation with respect to time. For instance, if

$$
\mathbf r(t)=(x_0+ut)\mathbf e_1+(y_0+wt)\mathbf e_2,
$$

where $u$ and $w$ are constants, then

$$
\mathbf v=u\mathbf e_1+w\mathbf e_2,
\qquad
\mathbf a=\mathbf 0.
$$

The particle moves with constant velocity along a straight line. This is a vector calculation, but it requires only familiar scalar derivatives of the components.

The same idea applies to a time-dependent multivector written in a fixed geometric-algebra basis. If $M(t)=\sum_A m_A(t)E_A$, where each $E_A$ is a fixed basis scalar, vector, or higher-grade element, then

$$
\frac{dM}{dt}=\sum_A \frac{dm_A}{dt}E_A.
$$

We will use this only when it helps. In this chapter the basis is fixed. Differentiating in a rotating or otherwise time-dependent basis requires extra terms; we will develop that subject when we study moving frames.

## 3.3 Forces, systems, and free-body diagrams

A **force** describes an interaction between bodies. A push from a hand, the pull of a spring, friction from a surface, and Earth's gravitational pull are different physical interactions. In Newtonian mechanics, force is a vector: it has both magnitude and direction.

When several forces act on the same body, their vector sum is the **net force**,

$$
\mathbf F_{\mathrm{net}}=\sum_i \mathbf F_i.
$$

The sum matters. Two forces can both be nonzero and yet have zero net force if they balance. A book resting on a table, for example, is pulled downward by gravity and pushed upward by the table. The book's acceleration is zero, even though each of those forces is present.

A free-body diagram helps keep track of this sum. Choose the body or system being studied, represent it simply, and draw the forces exerted on it by objects outside the chosen system. Forces that the chosen body exerts on its surroundings do not belong on that body's free-body diagram. We will return to this distinction when we discuss Newton's third law.

The choice of system is part of the reasoning. If we study a single book, the book-table contact force acts on the book. If we study the book and table together, that contact force is internal to the combined system. A clear system boundary prevents us from mixing forces on different objects.

## 3.4 Newton's first law: inertia and inertial frames

Everyday motion is observed from a reference frame: perhaps the floor of a laboratory, a moving train, or the surface of Earth. Newton's first law applies in a special class of frames called **inertial frames**.

```{note} Newton's First Law: the law of inertia

In an inertial reference frame, a body remains at rest or continues to move with constant velocity in a straight line when the net external force on it is zero.
```

The law gives a precise meaning to **inertia**: a body's velocity does not change by itself. A net force is associated with a change in velocity; it is not needed to maintain uniform straight-line motion.

Why state this as a separate law? Because it tells us which frames count as inertial. In such a frame, a force-free body has constant velocity. A frame accelerating or rotating relative to an inertial frame generally does not have this property. For example, when a bus brakes, a passenger appears to move forward relative to the bus. From the road's approximately inertial frame, the passenger's forward motion does not need a mysterious forward force: the bus slows while the passenger tends to keep the velocity they had. The backward force from the seat changes that velocity.

The first law also explains why the second law is not simply a definition of force in any frame. To infer forces from observed accelerations, we need a frame in which the laws take their stated form. In many classroom problems, the laboratory or ground is a good approximation to an inertial frame. For precise work, Earth's rotation and motion may matter.

An air track or low-friction cart gives a modern, approximate test of the idea. After a glider receives a brief push, it coasts; improving the track or bearings reduces the measured slowing. The residual force is never exactly zero, so the force-free case is inferred by reducing friction and extrapolating. Galileo's idealized argument in {numref}`fig-galileo-inertia` gives a way to think about this limit. The first law also provides a criterion for an inertial frame: in a suitable frame, bodies with negligible net force move at nearly constant velocity. These experiments support the ideal model within measurement limits rather than proving an exactly force-free motion.

## 3.5 Newton's second law: force changes momentum

A body's **momentum** is its mass multiplied by its velocity:

$$
\mathbf p=m\mathbf v.
$$

Momentum is a vector, so it contains information about both the amount and direction of motion. Newton's second law relates the net force to the rate at which momentum changes.

```{note} Newton's Second Law

In an inertial reference frame, the net external force on a body equals the rate of change of its momentum:
$$
\mathbf F_{\mathrm{net}}=\frac{d\mathbf p}{dt}.
$$
```

For a body of constant mass, $\mathbf p=m\mathbf v$, so

$$
\mathbf F_{\mathrm{net}}
=\frac{d(m\mathbf v)}{dt}
=m\frac{d\mathbf v}{dt}
=m\mathbf a.
$$

This is the familiar form $\mathbf F_{\mathrm{net}}=m\mathbf a$. The momentum form makes the general structure visible: force changes momentum. The acceleration form follows when the body's mass is constant. In this chapter we consider bodies of constant mass; variable-mass problems require care about how matter enters or leaves the system.

The equation is a vector equation. It represents three scalar equations in three dimensions, one along each independent direction. If the forces are known, we can resolve them into components, add the components, and solve for the acceleration.

### Testing the second law with a cart

The second law makes quantitative predictions that can be compared with measurements. On a level, low-friction track, keep a cart's mass fixed, vary the measured net pulling force, and determine the cart's acceleration from its velocity-time graph. The model predicts a straight-line relation between acceleration and net force, with slope $1/m$. Then keep the net force fixed and vary the cart's mass; plotting acceleration against $1/m$ should again give a straight line, now with slope $F_{\mathrm{net}}$. {numref}`fig-second-law-tests` shows these ideal predictions.

```{figure} ../figures/newton-second-law-tests.svg
:label: fig-second-law-tests
:enumerator: "3.3"
:alt: Two ideal graphs: acceleration versus net force at fixed mass, and acceleration versus inverse mass at fixed force.
:width: 100%

Ideal predictions for two tests of $a=F_{\mathrm{net}}/m$. The straight lines are theoretical guides, not measured data; real points scatter and may show an offset from friction or sensor bias.
```

In an actual experiment, one must estimate the **net** force, account for track tilt and friction, calibrate the force and motion sensors, and report uncertainty. Agreement over a range of forces and masses supports the law and the experimental model; a systematic offset or curvature is evidence to investigate the setup or the assumptions. As with Galileo's experiment, empirical support is always tied to how well the apparatus realizes the ideal conditions.

### Worked example: a constant horizontal force

A $2.0\,\mathrm{kg}$ cart is acted on by a constant net horizontal force of $6.0\,\mathrm{N}$. Its acceleration is

$$
a=\frac{F_{\mathrm{net}}}{m}
=\frac{6.0\,\mathrm{N}}{2.0\,\mathrm{kg}}
=3.0\,\mathrm{m\,s^{-2}}.
$$

If it starts from rest and the force acts for $4.0\,\mathrm{s}$, then its velocity change is

$$
\Delta v=a\Delta t
=(3.0\,\mathrm{m\,s^{-2}})(4.0\,\mathrm{s})
=12\,\mathrm{m\,s^{-1}}.
$$

We used a scalar calculation because the force has one known direction. If the force pointed in another direction, the vector equation would still apply, and the same reasoning would be carried out along the relevant components.

### Worked example: falling near Earth's surface

Near Earth's surface, an object in free fall experiences gravitational force. Neglect air resistance and choose the vertical unit vector $\mathbf e_y$ to point upward. If the object's mass is $m$, its weight is

$$
\mathbf F_g=-mg\mathbf e_y,
$$

where $g$ is the magnitude of the gravitational acceleration. Newton's second law gives

$$
m\mathbf a=-mg\mathbf e_y,
\qquad
\mathbf a=-g\mathbf e_y.
$$

Starting from position $y_0$ with vertical velocity $v_{0y}$, constant acceleration gives

$$
v_y(t)=v_{0y}-gt,
\qquad
y(t)=y_0+v_{0y}t-\frac{1}{2}gt^2.
$$

The mass cancels. In this idealized model, objects of different masses have the same free-fall acceleration when air resistance is negligible. The vector form says that the acceleration points downward; the component equations let us calculate the height and velocity.

## 3.6 Newton's third law: forces are mutual

Forces arise from interactions. If body A acts on body B, body B also acts on body A. The two forces have equal magnitude and opposite direction.

```{note} Newton's Third Law: action and reaction

If body A exerts a force $\mathbf F_{A\to B}$ on body B, then body B exerts a force
$$
\mathbf F_{B\to A}=-\mathbf F_{A\to B}
$$
on body A.
```

The two forces act on **different bodies**. They therefore do not cancel on the free-body diagram of either one. A hand pushes a wall, and the wall pushes the hand. The hand may be compressed or move backward even though the forces in the pair are equal and opposite.

### Worked example: two skaters push apart

Suppose two skaters, of masses $m_A$ and $m_B$, push against one another on nearly frictionless ice. During the push, the forces satisfy

$$
\mathbf F_{A\to B}=-\mathbf F_{B\to A}.
$$

Using the second law for each skater,

$$
m_B\mathbf a_B=-m_A\mathbf a_A.
$$

The skaters accelerate in opposite directions. The lighter skater has the greater acceleration magnitude. If there is no significant external horizontal force on the two-skater system, the internal forces cancel in the total momentum equation, so the system's total momentum remains constant. We will study this consequence systematically in Chapter 5.

The equal-and-opposite pair is not a cancellation within one body's equation. It is a relationship between the force on A and the force on B. Keeping track of which body each force acts on is essential.

A simple modern test uses two low-friction carts fitted with force sensors and pushed apart while they interact. The sensors record forces of opposite sign and, within their uncertainties, equal magnitude. The carts can have different masses and therefore different acceleration magnitudes; this does not contradict the third law, because the law compares the forces, not the accelerations. {numref}`fig-third-law-carts` shows the arrangement schematically.

```{figure} ../figures/newton-third-law-carts.svg
:label: fig-third-law-carts
:enumerator: "3.4"
:alt: Two carts on a track push apart through a spring or paired force sensors; equal and opposite arrows act on different carts.
:width: 100%

In a cart interaction, compare simultaneous sensor readings and identify which cart each force acts on. The arrows are a schematic force pair; the carts need not have equal accelerations.
```

## 3.7 Applying the laws: projectile motion

A projectile is an object that moves under gravity alone after launch, with air resistance neglected. This is an idealization, but often a useful first model. Choose horizontal and vertical unit vectors $\mathbf e_x$ and $\mathbf e_y$, with $\mathbf e_y$ upward. Newton's second law gives

$$
\mathbf a=-g\mathbf e_y.
$$

The horizontal and vertical motions can be treated separately because the acceleration has no horizontal component. If the projectile starts at $(x_0,y_0)$ with velocity

$$
\mathbf v_0=v_{0x}\mathbf e_x+v_{0y}\mathbf e_y,
$$

then

$$
x(t)=x_0+v_{0x}t,
\qquad
y(t)=y_0+v_{0y}t-\frac{1}{2}gt^2.
$$

For a launch speed $v_0$ at angle $\theta$ above the horizontal,

$$
v_{0x}=v_0\cos\theta,
\qquad
v_{0y}=v_0\sin\theta.
$$

Eliminating time gives the trajectory

$$
y-y_0=(x-x_0)\tan\theta
-\frac{g(x-x_0)^2}{2v_0^2\cos^2\theta}.
$$

It is a parabola. This result combines the three ingredients we need: a model of the force, Newton's second law, and the initial position and velocity. The first law identifies the inertial frame in which the model is being used; the third law concerns the gravitational interaction between the projectile and Earth, even though only the force on the projectile appears in this single-body calculation.

For many problems, resolving the vector equation into components is the most efficient method. Geometric algebra does not remove the need to solve the differential equations. Its advantage will be clearer when the geometry of the motion itself is central.

## 3.8 A simple model of drag

A falling object moving through air experiences a resistive force. At low speeds, a simple model takes this force to be proportional to velocity and opposite its direction. To see how a force model changes the motion, let downward be positive and write

$$
F_{\mathrm{net}}=mg-bv,
$$

where $b>0$ is a drag coefficient. Newton's second law becomes

$$
m\frac{dv}{dt}=mg-bv.
$$

If the object is released from rest, $v(0)=0$, solving this first-order differential equation gives

$$
v(t)=\frac{mg}{b}\left(1-e^{-bt/m}\right).
$$

At first the speed increases, but the drag grows with speed. Eventually the forces balance and the acceleration approaches zero. The limiting speed is the **terminal speed**

$$
v_{\mathrm{term}}=\frac{mg}{b}.
$$

This model is not a universal law of air resistance: at higher speeds, drag is often closer to proportional to the square of speed. It is a useful example of the role of a force law. Newton's second law tells us how to turn the chosen model into an equation of motion; experiment and physical judgment tell us whether that model is appropriate.

## 3.9 Circular motion and a geometric-algebra expression

Circular motion gives a first mechanics example in which the geometric algebra from Chapter 2 makes a geometric feature explicit. We begin with the standard coordinate derivation so the new notation has a familiar comparison.

Consider motion around a circle of fixed radius $R$ in the $\mathbf e_1,\mathbf e_2$ plane. Let the angle be $\theta=\omega t$, where $\omega$ is constant. The position is

$$
\mathbf r(t)=R\cos(\omega t)\mathbf e_1
+R\sin(\omega t)\mathbf e_2.
$$

Differentiating the components gives

$$
\mathbf v(t)=-R\omega\sin(\omega t)\mathbf e_1
+R\omega\cos(\omega t)\mathbf e_2,
$$

and

$$
\mathbf a(t)=-R\omega^2\cos(\omega t)\mathbf e_1
-R\omega^2\sin(\omega t)\mathbf e_2
=-\omega^2\mathbf r(t).
$$

The velocity is tangent to the circle, and the acceleration points toward its center.

Now let

$$
\mathbf I=\mathbf e_1\mathbf e_2
$$

be the unit bivector for this oriented plane. From the basis rules of Chapter 2,

$$
\mathbf e_1\mathbf I=\mathbf e_2,
\qquad
\mathbf e_2\mathbf I=-\mathbf e_1,
\qquad
\mathbf I^2=-1.
$$

Right multiplication by $\mathbf I$ turns a vector in this plane through a quarter-turn in the positive orientation. Applying it to the position vector gives

$$
\mathbf r\mathbf I
=-R\sin(\omega t)\mathbf e_1
+R\cos(\omega t)\mathbf e_2.
$$

Therefore the velocity and acceleration can be written

$$
\mathbf v=\omega\mathbf r\mathbf I,
\qquad
\mathbf a=\omega\mathbf v\mathbf I
=\omega^2\mathbf r\mathbf I^2
=-\omega^2\mathbf r.
$$

The expression $\mathbf v=\omega\mathbf r\mathbf I$ says directly that velocity is obtained by turning the radius vector into the tangent direction, with its size scaled by the angular rate. The square $\mathbf I^2=-1$ then gives the inward acceleration.

Newton's second law tells us what net force is required:

$$
\mathbf F_{\mathrm{net}}=m\mathbf a=-m\omega^2\mathbf r.
$$

The minus sign points toward the center. “Centripetal force” names this inward net force; it is not an additional kind of force. The actual force might be tension, gravity, a normal force, or a combination, depending on the physical system.

The frame matters here. We have described the circular motion from an inertial frame, such as a suitable laboratory frame. A reference frame that rotates with the object is **not** inertial: in that frame, a force-free body would not in general appear to move with constant velocity, so it fails the first-law test. To use Newton's laws in rotating coordinates, we must account for apparent inertial forces, including centrifugal and Coriolis forces. We will derive these terms in Chapter 8. The inward net force above is the real force required in the inertial-frame description; it should not be confused with the outward centrifugal force used in a rotating-frame description.

This calculation assumes a fixed circle and constant angular rate. It does not yet develop the general mathematics of rotations or moving frames. The basis vectors and $\mathbf I$ are fixed, and ordinary component differentiation remains the most direct way to find the trajectory. The GA expression is useful because it makes the turning geometry visible in one line. In three dimensions, the plane of a particular circular motion can still be represented by a bivector; later chapters will use that viewpoint for angular momentum and rotations.

## 3.10 What the laws do, and what they leave to us

Newton's laws do not by themselves specify every force. To solve a problem, we also need a **force model**: gravity near Earth's surface, a spring force, drag, tension, or a contact force. We choose a system, draw the external forces on it, apply the laws in an inertial frame, and supply initial conditions. The resulting equations can then be solved analytically or numerically.

The laws also have a domain of validity. Newtonian mechanics is an excellent approximation for many everyday systems when speeds are far below the speed of light and quantum effects are negligible. It is not the final description of all physical phenomena. Within its domain, though, it is extraordinarily effective, and its structure leads naturally to the energy, momentum, Lagrangian, and Hamiltonian methods developed later in this book.

The three laws play complementary roles:

- The **first law** characterizes inertial frames and describes force-free motion.
- The **second law** predicts how the net force changes a body's momentum.
- The **third law** relates the forces that two interacting bodies exert on one another.

The geometric algebra has not changed these laws. In translation problems, ordinary vectors and components are often the clearest language. In circular motion, multiplying by the plane bivector packages a quarter-turn and makes the geometry of the tangent direction explicit. We will look for this kind of payoff throughout the book: use GA when its geometric structure helps, and use familiar tools when they are more direct.

## Further reading

- Galileo Galilei, *Dialogues Concerning Two New Sciences* (1638), especially the [Third Day discussion of naturally accelerated motion](https://galileoandeinstein.phys.virginia.edu/tns_draft/tns_160to243.html) and the [Fourth Day discussion of projectile motion](https://galileoandeinstein.phys.virginia.edu/tns_draft/tns_244to279.html). These are primary-source translations.
- Isaac Newton, *The Mathematical Principles of Natural Philosophy* (first published 1687), especially the opening definitions and laws of motion. The [Library of Congress collection page](https://www.loc.gov/item/2021667054/) provides historical context and access to a digitized edition.
- OpenStax, [*University Physics, Volume 1*, Chapter 5: Newton's Laws of Motion](https://openstax.org/books/university-physics-volume-1/pages/5-introduction), for a freely available modern treatment.
- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), Chapter 1, for a more extended undergraduate treatment of Newton's laws, inertial frames, and trajectories.

### Exercises

1. A particle has position $\mathbf r(t)=(3t)\mathbf e_1+(4t-t^2)\mathbf e_2$. Find its velocity and acceleration. At what time, if any, is its vertical velocity zero?
2. Explain in your own words why a book sliding across a table does not contradict the first law. Identify the interaction that changes its motion.
3. In an inertial frame, a $1.5\,\mathrm{kg}$ object experiences a constant net force $(3.0\mathbf e_1-6.0\mathbf e_2)\,\mathrm{N}$. Find its acceleration vector and magnitude.
4. A $0.20\,\mathrm{kg}$ ball is dropped from rest. Neglect air resistance and take $g=9.8\,\mathrm{m\,s^{-2}}$. Find its velocity and displacement after $1.5\,\mathrm{s}$, taking downward as positive.
5. Two skaters of masses $50\,\mathrm{kg}$ and $75\,\mathrm{kg}$ push apart. If the lighter skater's acceleration during the push has magnitude $1.2\,\mathrm{m\,s^{-2}}$, what is the acceleration magnitude of the heavier skater? State the assumptions you use.
6. A projectile is launched from ground level at speed $20\,\mathrm{m\,s^{-1}}$ and angle $30^\circ$ above the horizontal. Neglect air resistance. Find its time of flight and horizontal range. Use $g=9.8\,\mathrm{m\,s^{-2}}$.
7. In the linear-drag model, show that $v_{\mathrm{term}}=mg/b$ is reached only as a limiting value as $t$ grows. What is the characteristic time in the exponential?
8. For uniform circular motion, verify directly from $\mathbf r=R(\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2)$ that $\mathbf r\mathbf I$ is tangent to the circle. Why does the acceleration point inward?
9. A stone moves in a horizontal circle on a string. Draw separate free-body diagrams for the stone and for the hand holding the string. Identify the third-law pair and explain why its forces do not cancel in the stone's equation of motion.
10. Galileo reported that a ball traveled one quarter of an inclined track in half the time required for the whole track. Check that this is consistent with $s\propto t^2$. What assumptions about the motion and timing are needed to interpret this as evidence for uniform acceleration?
11. Design a cart experiment to test the second law. State what you would hold fixed, what you would vary, what you would measure, which graph you would make, and at least two sources of uncertainty or systematic error.
