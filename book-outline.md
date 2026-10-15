# Classical Mechanics with Geometric Algebra

## Book idea

An introductory textbook in classical mechanics that teaches geometric algebra (GA) early, then develops mechanics along a recognizable path: Newtonian mechanics, Lagrangian mechanics, and Hamiltonian mechanics. GA should clarify geometry and unify useful ideas, while the book should also show when conventional vector, coordinate, matrix, and calculus methods are preferable.

The intended reader knows school-level classical mechanics, including Newton's laws and the meanings of velocity and acceleration, and is comfortable with derivative notation such as $a=dv/dt$. No prior geometric algebra or analytical mechanics is assumed. Calculus needed for later chapters will be introduced or reviewed as it arises.

## Possible structure

0. **Introduction: a map of the book** — State the assumed background, explain what GA adds (and where familiar methods remain preferable), and briefly motivate every chapter.

### Part I — The mathematical language

1. **Vectors, products, and oriented geometry** — A gentle first look at scalars, vectors, and oriented area, with familiar examples from mechanics and other areas of physics. Motivate the inner, outer, and geometric products without developing the full algebra. Keep explanations and calculations in the plane, with one short preview of three-dimensional geometry.
2. **Foundations of geometric algebra** — A self-contained mathematical introduction, beginning with vector spaces and a metric, then defining the inner, outer, and geometric products. Develop grades, blades, multivectors, basis calculations, reversion, inverses, and pseudoscalars through concrete two-dimensional examples before generalizing to three dimensions.

Keep Chapter 1 concise and orienting; reserve systematic definitions and algebraic rules for Chapter 2. In later chapters, when a physics application requires a GA concept not yet developed, place a concise **Mathematical tools** section at the beginning of that chapter, before the physics. Introduce only the tools needed there and do not repeat foundations already established.

### Part II — Newtonian mechanics

3. **From Galileo to Newton: laws of motion** — Motivate the laws historically through Galileo's studies of falling bodies, inclined planes, inertia, and projectile motion, then explain Newton's synthesis. Review vector-valued time derivatives and inertial frames; state and distinguish all three Newtonian laws in prominent callouts; develop force diagrams, momentum, free fall, projectiles, linear drag, and uniform circular motion. Use the planar bivector to express the tangent direction in circular motion, while showing why component calculations are often the most direct method.
4. **Work, energy, and conservative forces** — Work and power, kinetic and potential energy, conservation laws, equilibria, and effective one-dimensional motion.
5. **Systems of particles and momentum** — Linear momentum, centre-of-mass motion, impulse, collisions, angular momentum, and torque. Compare angular momentum as a bivector, $\mathbf L=\mathbf r\wedge\mathbf p$, with its usual axial-vector representation.
6. **Oscillations** — Harmonic motion, damping, driving, resonance, and energy transfer. Compare real-variable, complex-number, and GA descriptions of phase.
7. **Central forces and orbital motion** — The two-body problem, conservation of the orbital plane, effective potentials, Kepler motion, and elementary scattering. A brief spherical-coordinate example will show how a cyclic azimuth gives the same angular momentum as the GA bivector.

GA is especially useful here for angular momentum and orbital geometry. Scalar equations remain the most direct tools for many energy, drag, and oscillation problems.

### Part III — Rotation and rigid bodies

8. **Moving and rotating reference frames** — Begin with a **Mathematical tools** section that develops reflections and rotors, their action on vectors, and composition of rotations. Then introduce time-dependent bases, angular velocity, centrifugal and Coriolis terms, and examples, including the Foucault pendulum. Derive the link between a rotor's time evolution and angular velocity before using it in applications.
9. **Rigid-body geometry and inertia** — Orientation, body and space frames, the inertia operator, principal axes, and the conventional inertia tensor. Relate the operator description to matrix calculations.
10. **Rigid-body dynamics** — Apply the rotor and orientation tools from Chapter 8 alongside Euler's equations to study free rotation, stability about principal axes, gyroscopes, and the symmetric top. Use accessible examples in the main text and reserve longer treatments for optional sections.

Rotation and orientation are the clearest extended applications of GA. Matrices remain useful for numerical work and for finding principal moments of inertia.

### Part IV — Lagrangian mechanics

11. **Constraints and generalized coordinates** — Configuration space, holonomic constraints, virtual work, d'Alembert's principle, and Lagrange's equations, with examples such as pendulums and coupled systems.
12. **Action, symmetry, and conservation** — Hamilton's principle, the Euler–Lagrange equations, cyclic coordinates, and an introductory Noether theorem. Revisit translational and rotational symmetry, including bivector angular momentum.
13. **Small oscillations and normal modes** — Linearization near equilibrium, quadratic kinetic and potential energies, generalized eigenvalue problems, and normal coordinates.

For Chapter 11, use GA selectively to make the geometry of constraints visible, not to rewrite the whole Lagrangian formalism. Compare eliminating constraints through adapted coordinates with retaining Cartesian coordinates and using Lagrange multipliers; briefly extend the fixed-constraint treatment to a translating support. A particle's position is a vector-valued function of generalized coordinates, $\mathbf r=\mathbf r(q^1,\ldots,q^n)$, so an infinitesimal or virtual displacement is

$$
\delta\mathbf r=\sum_i\frac{\partial\mathbf r}{\partial q^i}\,\delta q^i.
$$

The vectors $\partial\mathbf r/\partial q^i$ point along the allowed coordinate directions. For a holonomic constraint $f(\mathbf r)=0$, the gradient is normal to the constraint surface and allowed virtual displacements obey $\nabla f\cdot\delta\mathbf r=0$. A pendulum of fixed length is a compact example: $\mathbf r^2=\ell^2$ implies $\mathbf r\cdot\delta\mathbf r=0$ and $\mathbf r\cdot\dot{\mathbf r}=0$, so its virtual displacement and velocity lie tangent to the circle.

Use the inner product to connect applied forces to generalized forces and virtual work:

$$
\delta W_{\mathrm{app}}=\sum_a\mathbf F_a^{\mathrm{app}}\cdot\delta\mathbf r_a
=\sum_i Q_i\,\delta q^i,
\qquad
Q_i=\sum_a\mathbf F_a^{\mathrm{app}}\cdot\frac{\partial\mathbf r_a}{\partial q^i}.
$$

Then present d'Alembert's principle, $\sum_a(\mathbf F_a^{\mathrm{app}}+\mathbf R_a-m_a\ddot{\mathbf r}_a)\cdot\delta\mathbf r_a=0$. For ideal constraints, the reaction forces obey $\sum_a\mathbf R_a\cdot\delta\mathbf r_a=0$, so they disappear from the virtual-work equation. Use this to derive Lagrange's equations in the usual scalar-coordinate notation. A worked pendulum can carry the thread from the constraint geometry through its generalized force and energy to its equation of motion; a coupled-mass example can show the efficiency of choosing coordinates adapted to constraints.

The chapter's GA tools are therefore vector-valued position maps, inner products, constraint normals and tangents, and—if helpful—a brief reuse of the rotor description of the pendulum from Chapter 8. Do not force the wedge product or bivectors into the derivation; angular momentum and rotational symmetry have a more natural place in Chapters 5 and 12. Keep configuration-space calculus and coupled equations in familiar coordinate and matrix notation, since the configuration space is not generally the same thing as physical three-dimensional space. Lead with generalized coordinates and d'Alembert's principle here; reserve Hamilton's principle and the Euler–Lagrange variational derivation for Chapter 12.

One possible section sequence is: why constraints complicate Newton's equations; generalized coordinates and configuration space; constraint surfaces and admissible motion; virtual work and generalized forces; d'Alembert's principle; deriving Lagrange's equations; the simple pendulum; and a coupled system with a comparison of Newtonian and Lagrangian approaches.

Use matrix methods for the coupled equations and later normal-mode calculations.

For Chapter 12, connect stationary action to the Euler–Lagrange equations with a short endpoint-fixed variation and integration-by-parts derivation. Make the gradient, directional derivative, and time derivative of vector- and multivector-valued functions explicit, including the product rule. Use the harmonic oscillator as a first check against Newton's law, then use a central-force particle in polar coordinates to show how a cyclic angle gives conserved angular momentum and reduces the radial motion to an effective potential. Close by connecting time-translation symmetry with energy conservation and by representing angular momentum as the bivector $\mathbf r\wedge\mathbf p$.

### Part V — Hamiltonian mechanics

14. **Momentum, the Legendre transform, and phase space** — Canonical momentum, regular Lagrangians, Hamilton's equations, and when the Hamiltonian equals mechanical energy.
15. **Poisson brackets and canonical transformations** — Observables, generators of motion, conservation laws, canonical transformations, and an accessible introduction to symplectic geometry.
16. **Hamilton–Jacobi theory and integrable motion** — The Hamilton–Jacobi equation, separation of variables, and an introduction to action–angle variables through simple examples. An optional advanced section can treat time as a coordinate and derive the energy balance in an extended configuration space.
17. **Nonlinear dynamics and numerical mechanics** — Phase portraits, separatrices, qualitative chaos, numerical integration, and energy behaviour under standard and symplectic integrators. Numerical rotor evolution can provide a final GA application. This chapter may be optional.

Make clear that GA describes metric and rotational geometry, while Hamiltonian mechanics brings in symplectic structure on phase space. Explain their relationship without treating a GA commutator as interchangeable with a Poisson bracket.

## Appendices and teaching approach

Possible appendices: a GA notation dictionary and identity sheet; essential differential-equation methods; linear algebra; and selected exercise solutions. Full geometric calculus, conformal GA, and spacetime algebra can remain outside the core scope.

Use a small set of recurring examples—the oscillator, pendulum, Kepler problem, and rotating rigid body—under Newtonian, Lagrangian, and Hamiltonian descriptions. Include short discussions of which mathematical representation is most useful for each task, and exercises in physical reasoning, calculation, and translation between GA and conventional notation.

## Computational examples

Use **Python with marimo** for optional numerical explorations. Keep the main exposition and its figures self-contained, with no code execution required to follow the book. Marimo notebooks can serve as companion material, with static plots included in the chapters and interactive versions offered separately. Keep the MyST book build independent of notebook execution while MyST's build-time execution remains in beta.

## References to compare against

- David Hestenes, [*New Foundations for Classical Mechanics*](https://davidhestenes.net/geocalc/html/NFCM.html), a substantial GA treatment of classical mechanics.
- Chris Doran and Anthony Lasenby, [*Geometric Algebra for Physicists*](https://www.cambridge.org/core/books/geometric-algebra-for-physicists/FB8D3ACB76AB3AB10BA7F27505925091), which includes classical mechanics and places GA in a broader physics context.

