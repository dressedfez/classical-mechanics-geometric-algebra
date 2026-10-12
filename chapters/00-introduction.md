---
title: "0. Introduction: A Map of the Book"
description: "What this book assumes, why it uses geometric algebra, and what each chapter will help you understand."
---

You already know the basic language of mechanics. You have met force, mass, velocity, acceleration, momentum, and energy, and you recognize equations such as $\mathbf F_{\mathrm{net}}=m\mathbf a$ and $\mathbf a=d\mathbf v/dt$. This book starts from that foundation and develops the subject toward Newtonian, Lagrangian, and Hamiltonian mechanics.

Along the way, we will learn geometric algebra (GA), a way to calculate with geometric objects such as vectors and oriented planes. GA is useful when it makes the geometry clearer—for example, when describing rotations or angular momentum. It does not make every calculation shorter. Ordinary vector formulas, coordinates, matrices, and calculus remain valuable, and we will use them whenever they are the more direct tools.

No previous experience with GA, Lagrangian mechanics, or Hamiltonian mechanics is assumed. We introduce the GA vocabulary near the start, build ideas in the plane before extending them to three dimensions, and bring in the calculus needed for later chapters as it arises. Optional Python examples, including marimo notebooks, will let you explore selected systems numerically; the main explanations do not depend on running code.

## The route through the book

### Part I — The mathematical language

We first learn enough geometry and algebra to read the mechanics chapters, then connect that language to motion.

1. **Vectors, products, and oriented geometry.** We begin with familiar scalars and vectors, then meet oriented area as a preview of a new kind of geometric quantity. A few simple examples motivate the algebra without asking us to master it all at once.
2. **Foundations of geometric algebra.** We build the algebra carefully, starting from vector spaces and their metric, then developing the outer and geometric products, grades, blades, and multivectors. Plane examples lead into three dimensions and provide tools used throughout the mechanics chapters.
3. **Calculus and kinematics.** We use position, velocity, and acceleration to connect the algebra to actual motion. Differentiating vector-valued functions and studying circular motion prepare us for equations of motion.

### Part II — Newtonian mechanics

We take the laws and quantities you know from school mechanics and use them to solve increasingly rich problems.

4. **Newton’s laws and simple dynamical systems.** Inertial frames, forces, and initial conditions turn Newton’s laws into a method for predicting motion, from projectiles to motion with drag.
5. **Work, energy, and conservative forces.** Energy often solves a problem more directly than force components do. We use work and potential energy to study conservation, equilibrium, and one-dimensional motion.
6. **Systems of particles and momentum.** Momentum and centre-of-mass motion simplify collisions and many-particle systems. Angular momentum provides a first major mechanics application of bivectors.
7. **Oscillations.** Oscillators model springs, small pendulum motions, and many other systems. Comparing real, complex, and GA descriptions helps explain phase, damping, and resonance.
8. **Central forces and orbital motion.** Central forces lead to Kepler orbits and scattering. Conservation of angular momentum explains why the motion stays in a plane and makes orbital geometry explicit.

### Part III — Rotation and rigid bodies

Here we study motion in rotating frames and the motion of objects whose parts keep fixed distances from one another. Chapter 9 begins with a short mathematical-tools section on reflections and rotors, so the rotation mathematics is in place before its mechanics applications.

9. **Moving and rotating reference frames.** We learn how time-dependent axes change the description of velocity and acceleration, and where centrifugal and Coriolis terms come from.
10. **Rigid-body geometry and inertia.** A rigid body’s orientation and mass distribution determine how it responds to rotation. We connect the geometric inertia operator to the familiar inertia tensor and matrix calculations.
11. **Rigid-body dynamics.** Euler’s equations explain free rotation, gyroscopes, and the stability of spinning bodies. We apply the rotor tools developed earlier to represent a body’s changing orientation.

### Part IV — Lagrangian mechanics

Lagrangian mechanics is useful when constraints make force-by-force equations awkward and when we want to expose the role of symmetry.

12. **Constraints and generalized coordinates.** We choose coordinates adapted to a system, such as the angle of a pendulum, and derive equations that handle constraints systematically.
13. **Action, symmetry, and conservation.** Hamilton’s principle derives the Euler–Lagrange equations from an action. Symmetries then explain conservation laws, including linear and angular momentum.
14. **Small oscillations and normal modes.** Near a stable equilibrium, coupled motion can be approximated by normal modes. This chapter shows how the motions of a complicated system can be understood as simpler patterns.

### Part V — Hamiltonian mechanics

Hamiltonian mechanics recasts motion in terms of positions and momenta, opening the door to phase-space geometry and several powerful methods.

15. **Momentum, the Legendre transform, and phase space.** We move from a Lagrangian to Hamilton’s equations and learn when the Hamiltonian represents the system’s energy.
16. **Poisson brackets and canonical transformations.** Poisson brackets describe how observables change and identify generators of motion. Canonical transformations reveal the structure preserved by Hamiltonian dynamics.
17. **Hamilton–Jacobi theory and integrable motion.** The Hamilton–Jacobi equation can turn dynamics into a problem of solving for a function. Separation of variables and action–angle coordinates show how this works in important solvable systems.
18. **Nonlinear dynamics and numerical mechanics.** Phase portraits help us understand motion that cannot be solved in closed form. Numerical methods let us explore such systems, and symplectic integrators show why preserving the structure of the equations matters over long simulations. This chapter is an optional extension of the core sequence.

## A note on the different geometries

Geometric algebra describes metric and rotational geometry, including vectors, planes, and rotations. Hamiltonian mechanics also relies on symplectic geometry in phase space. These ideas can work together, but they describe different structures; the book will make their roles clear rather than treating one as a substitute for the other.
