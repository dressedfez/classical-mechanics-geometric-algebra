---
title: Classical Mechanics with Geometric Algebra
description: A web-first introduction to classical mechanics for readers familiar with school-level Newtonian mechanics.
---

This book is for readers who know the school-level ideas of classical mechanics: force, momentum, energy, and equations such as $\mathbf F=m\mathbf a$ and $\mathbf a=d\mathbf v/dt$. It introduces geometric algebra (GA) from the beginning, then develops Newtonian, Lagrangian, and Hamiltonian mechanics.

The book will show where GA clarifies geometric structure and where conventional vector, coordinate, matrix, and calculus methods are more direct. It assumes no previous experience with GA. We will introduce or review the calculus needed for later chapters as it arises. Optional numerical explorations will use Python with marimo.

Download the [current book draft as a PDF](/classical-mechanics-with-geometric-algebra.pdf). The PDF is rebuilt automatically alongside the website.

The intended publication format is a navigable website built from this MyST project. Chapters, figures, equations, and references will be organized for online reading; a hosting provider can be chosen when the manuscript is ready to publish.

[Start with the introduction](./chapters/00-introduction.md), which maps the route through the book. Chapters [1](./chapters/01-vectors-products-oriented-geometry.md) and [2](./chapters/02-geometric-algebra-foundations.md) develop the motivation and foundations of GA. [Chapter 3 introduces Newtonian mechanics](./chapters/03-newtonian-mechanics.md), beginning with Galileo's work and Newton's three laws.

[Chapter 4 develops work and energy methods](./chapters/04-work-energy-conservative-forces.md), deriving the work-energy theorem, introducing conservative forces and potential energy, and using energy diagrams to understand motion and equilibrium.

[Chapter 5 develops systems of particles and momentum](./chapters/05-systems-of-particles-and-momentum.md). It connects momentum conservation to the centre of mass and collisions, then introduces angular momentum and torque as bivectors while comparing them with the familiar cross-product form.

[Chapter 6 develops oscillations](./chapters/06-oscillations.md), from ideal spring motion through damping and resonance. It compares real, complex, and GA descriptions of phase, including a state-plane picture of the oscillator.

[Chapter 7 develops central-force and orbital motion](./chapters/07-central-forces-and-orbital-motion.md). Angular momentum fixes the orbital plane, while effective potentials and Kepler's laws describe the radial motion.

[Chapter 8 develops moving and rotating frames](./chapters/08-moving-and-rotating-reference-frames.md). Reflections and rotors provide the GA tools for rotations, followed by the transport theorem and inertial forces.

[Chapter 9 develops rigid-body geometry and inertia](./chapters/09-rigid-body-geometry-and-inertia.md), connecting rotor orientation and a geometric inertia operator to the inertia tensor and principal axes.

[Chapter 10 develops rigid-body dynamics](./chapters/10-rigid-body-dynamics.md), including Euler's equations, the intermediate-axis instability, and gyroscopic precession.

[Chapter 11 develops constraints and generalized coordinates](./chapters/11-constraints-and-generalized-coordinates.md). It introduces virtual work, d'Alembert's principle, and Lagrange's equations, with GA used to clarify constraint geometry.

[Chapter 12 derives Lagrange's equations from stationary action](./chapters/12-action-symmetry-conservation.md), then uses cyclic coordinates and symmetries to explain conservation of energy and angular momentum.

[Chapter 13 develops small oscillations and normal modes](./chapters/13-small-oscillations-and-normal-modes.md), showing how coupled motion near equilibrium separates into independent patterns.

[Chapter 14 introduces Hamiltonian mechanics](./chapters/14-momentum-legendre-transform-phase-space.md) through canonical momentum, the Legendre transform, and phase space.

[Chapter 15 develops Poisson brackets and canonical transformations](./chapters/15-poisson-brackets-and-canonical-transformations.md), explaining how observables evolve and how symmetries generate motion.

[Chapter 16 develops Hamilton–Jacobi theory](./chapters/16-hamilton-jacobi-theory-and-integrable-motion.md) and introduces action-angle variables for integrable motion.

[Chapter 17 explores nonlinear dynamics and numerical mechanics](./chapters/17-nonlinear-dynamics-and-numerical-mechanics.md), including phase portraits, chaos, symplectic integration, and an optional Python example.
