---
title: "17. Nonlinear Dynamics and Numerical Mechanics"
description: "Explore nonlinear motion with phase portraits and numerical integration, including why symplectic methods matter for long-term mechanics simulations."
---

Many mechanical systems cannot be solved exactly, and their motion may change qualitatively with energy or initial conditions. A pendulum swings through large angles, a driven system can become chaotic, and a rigid body's orientation may need numerical integration. Numerical methods let us study these systems, but a plausible-looking trajectory is not automatically a reliable one.

This chapter introduces phase portraits, separatrices, sensitivity to initial conditions, and practical integration methods. We finish by returning to GA: rotors can keep numerically updated orientations on the rotation group, while symplectic integrators preserve the canonical structure of Hamiltonian phase space. These are different geometric preservation tasks.

## 17.1 Nonlinear motion: the large-angle pendulum

For a pendulum of length $\ell$, the exact angular equation is

$$
\ddot\theta+\frac{g}{\ell}\sin\theta=0.
$$

The small-angle approximation $\sin\theta\approx\theta$ produces simple harmonic motion, but the full equation is nonlinear. Its energy is

$$
E=\frac{1}{2}m\ell^2\dot\theta^2+mg\ell(1-\cos\theta).
$$

Plotting angular velocity against angle gives a **phase portrait**. Low-energy trajectories are closed curves around the stable hanging equilibrium. At a particular energy, the bob approaches the upright position with its speed tending to zero. This boundary trajectory separates oscillations from full rotations and is called the **separatrix**. Near it, the period grows without bound: the bob spends a long time near the unstable upright position.

The threshold follows directly from energy. At the upright position $\theta=\pi$, the potential is $2mg\ell$, so the separatrix has $E_{\mathrm{sep}}=2mg\ell$. At the bottom, where the potential is zero, that same energy is kinetic:

$$
\frac{1}{2}m\ell^2\dot\theta^2=2mg\ell,
\qquad
|\dot\theta|=2\sqrt{\frac g\ell}.
$$

Thus a bob launched upward from the bottom more slowly than this threshold turns around and swings back; at the threshold it approaches the upright position asymptotically; above it, it continues over the top. This energy argument predicts the three kinds of phase curves without solving the nonlinear equation in closed form.

```{figure} ../figures/pendulum-phase-portrait.svg
:label: fig-pendulum-phase-portrait
:enumerator: "17.1"
:alt: Phase portrait of a nonlinear pendulum with closed librations below a separatrix and rotating trajectories above it.
:width: 82%

The portrait shows angle and angular velocity, not the bob's physical path. The separatrix divides oscillations from continuous rotations and passes through the unstable upright equilibrium.
```

Phase portraits show what a time series can hide: distinct kinds of motion, equilibria, and boundaries between them. They are also useful for interpreting numerical results, because energy contours provide a check on whether a computed trajectory is behaving plausibly.

## 17.2 Sensitivity and chaos

In a nonlinear system, nearby initial states can sometimes separate rapidly. If their distance grows approximately as

$$
\delta(t)\approx\delta(0)e^{\lambda t},
$$

with positive $\lambda$, the motion is sensitive to initial conditions. In a chaotic regime, long-term prediction of one exact trajectory becomes limited by finite measurement and rounding precision, even though the equations are deterministic.

Chaos does not mean that all motion is random or that every nonlinear system is chaotic. The undriven pendulum is integrable; adding periodic forcing and damping can create complex, sometimes chaotic motion. A useful diagnostic is a **Poincaré section**: sample a trajectory whenever it crosses a chosen surface in the same direction. Regular motion often gives a finite set of points or smooth curves; chaotic motion can fill a region in a structured way.

Numerical trajectories must be interpreted with care. A solver can introduce artificial energy growth, erase a real separatrix, or make a chaotic orbit diverge from the physical trajectory after a long time. Convergence checks, energy monitoring, and comparison across step sizes are part of the physics, not just software hygiene.

## 17.3 Time-stepping a simple Hamiltonian system

For a separable Hamiltonian $H(q,p)=T(p)+V(q)$, Hamilton's equations are

$$
\dot q=\frac{\partial T}{\partial p},
\qquad
\dot p=-\frac{\partial V}{\partial q}.
$$

Forward Euler updates both variables from their old values:

$$
q_{n+1}=q_n+h\frac{\partial T}{\partial p}(p_n),
\qquad
p_{n+1}=p_n-h\frac{\partial V}{\partial q}(q_n).
$$

It is simple and only first-order accurate, but for an oscillator its energy error tends to drift systematically. A symplectic Euler step updates momentum first and position second:

$$
p_{n+1}=p_n-h\frac{\partial V}{\partial q}(q_n),
\qquad
q_{n+1}=q_n+h\frac{\partial T}{\partial p}(p_{n+1}).
$$

This method is also first-order accurate, but it preserves the symplectic form. A widely used second-order method for mechanical systems is velocity Verlet:

$$
\begin{aligned}
p_{n+1/2}&=p_n-\frac{h}{2}\frac{\partial V}{\partial q}(q_n),\\
q_{n+1}&=q_n+h\frac{\partial T}{\partial p}(p_{n+1/2}),\\
p_{n+1}&=p_{n+1/2}-\frac{h}{2}\frac{\partial V}{\partial q}(q_{n+1}).
\end{aligned}
$$

For a harmonic oscillator, symplectic methods usually keep the energy error bounded and oscillatory over long runs, rather than allowing an artificial secular drift. They do not conserve the exact energy at every discrete step, and a step that is too large can still give a poor result. Their advantage is long-term structural behaviour.

Here is a concrete comparison for $m=1\,\mathrm{kg}$, $k=4\,\mathrm{N\,m^{-1}}$, initial state $x=1\,\mathrm m$, $v=0$, and step $h=0.01\,\mathrm s$, integrated for $10\,\mathrm s$. The exact energy is $2\,\mathrm J$. Forward Euler raises it to about $2.98\,\mathrm J$; symplectic Euler keeps it between about $1.980$ and $2.020\,\mathrm J$; velocity Verlet keeps it between about $1.9998$ and $2.0000\,\mathrm J$. These numbers depend on the chosen step and initial state, but they show why local accuracy alone does not describe a method's long-term behaviour.

### Optional Python example: velocity Verlet

The following short Python routine advances a one-dimensional particle under a force that depends on position:

```python
def velocity_verlet(x, v, h, mass, force):
    a = force(x) / mass
    x_next = x + h * v + 0.5 * h**2 * a
    a_next = force(x_next) / mass
    v_next = v + 0.5 * h * (a + a_next)
    return x_next, v_next

mass = 1.0
stiffness = 4.0
force = lambda x: -stiffness * x
x, v = 1.0, 0.0
dt = 0.01
for _ in range(1000):
    x, v = velocity_verlet(x, v, dt, mass, force)
```

To examine accuracy, calculate $E_n=\tfrac12mv_n^2+\tfrac12kx_n^2$ at every step and compare it with the initial energy. Then repeat with a larger and smaller step, and compare with forward Euler. The code is an optional exploration; the structural reasoning applies independently of Python.

## 17.4 Integrating orientation with rotors

A numerical rigid-body calculation must update both angular velocity and orientation. Updating three Euler angles independently can produce singularities and can allow rounding error to violate orthogonality. A rotor stores orientation with the normalization condition $Q\widetilde Q=1$.

If the spatial angular-velocity bivector is approximately constant over a short interval $h$, the convention used in Chapter 8 gives

$$
Q_{n+1}=\exp\left(-\frac{h}{2}\boldsymbol\Omega\right)Q_n.
$$

The exponential rotor is unit length, so this step preserves the rotor norm in exact arithmetic. For changing angular velocity, a midpoint or higher-order update is needed; in floating-point arithmetic, occasional normalization can control small drift. The angular velocity itself must still be advanced using the torque and inertia equations.

A unit rotor preserves the geometry of orientation. It does not by itself preserve the Hamiltonian symplectic form or the body's energy. For long simulations, one may need a method that respects both the rotational constraints and the relevant dynamical structure.

## 17.5 What to remember

- Nonlinear phase portraits reveal equilibria, distinct motion types, and separatrices.
- A positive Lyapunov exponent signals exponential sensitivity, but nonlinearity alone does not imply chaos.
- Numerical step size and method affect the apparent energy and long-term trajectory.
- Symplectic integrators preserve phase-space structure and usually control long-term energy error better for conservative systems.
- Rotors provide a natural way to update orientation while preserving unit length.
- Rotor normalization and symplectic preservation address different geometric constraints.

### Exercises

1. Sketch the potential energy of a pendulum as a function of angle and identify the stable and unstable equilibria.
2. Explain why the separatrix separates oscillatory and rotating pendulum motion.
3. Compare forward Euler and symplectic Euler updates for the harmonic oscillator. Which variable uses the newly updated value in symplectic Euler?
4. In a velocity-Verlet simulation, calculate total energy at each time step. Describe how reducing the step size changes the result.
5. Explain why a chaotic trajectory cannot be predicted accurately for arbitrarily long times from finite-precision initial data.
6. What condition does a rotor update preserve? What important Hamiltonian structure does that condition not preserve by itself?
7. **Synthesis.** Use the oscillator parameters in the energy comparison to integrate for $10\,\mathrm s$ with velocity Verlet at $h=0.02\,\mathrm s$ and $h=0.01\,\mathrm s$. Record the largest energy error for each run, compare with the stated forward-Euler result, and explain how the step-size change affects the trajectory and energy.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on nonlinear oscillations and numerical methods.
- Ernst Hairer, Christian Lubich, and Gerhard Wanner, *Geometric Numerical Integration*, for symplectic methods and long-term simulation.
- Edward Ott, *Chaos in Dynamical Systems*, for phase-space views and sensitive dependence.
- marimo documentation, for interactive Python notebooks that can accompany numerical experiments.
