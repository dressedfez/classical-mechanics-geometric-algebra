---
title: "12. Action, Symmetry, and Conservation"
description: "Derive Lagrange's equations from vector-valued path variations and connect continuous symmetries with conserved energy, momentum, and angular momentum."
---

Chapter 11 derived Lagrange's equations by applying d'Alembert's principle to virtual displacements. Here we reach the equations from a different direction: we vary an entire path while holding its endpoints fixed. We will first write the calculation directly with geometric vectors in physical space, then express it in generalized coordinates. This makes the geometric content visible before introducing coordinate components.

The central objects are a position vector $\mathbf r(t)$, a Lagrangian $L$, and its vector derivative with respect to position and velocity. The same notation works in any fixed orthonormal basis. Generalized coordinates then describe which paths are allowed by constraints.

## 12.1 Mathematical tools: vector derivatives

Let $F(\mathbf r)$ be a scalar-valued function of a vector in Euclidean space. In a fixed orthonormal basis $\{\mathbf e_a\}$, write $\mathbf r=\sum_a x^a\mathbf e_a$. Its vector derivative is

$$
\partial_{\mathbf r}=\sum_a\mathbf e_a\frac{\partial}{\partial x^a},
\qquad
\partial_{\mathbf r}F=\sum_a\mathbf e_a\frac{\partial F}{\partial x^a}.
$$

The lecture notation places arrows over vector symbols; here we use boldface for vectors and write the vector derivative as $\partial_{\mathbf r}$.

For a scalar function this is the familiar gradient, written in geometric-algebra notation. Its defining practical property is that it gives the rate of change in any chosen direction $\mathbf a$:

$$
\left[\frac{d}{d\epsilon}F(\mathbf r+\epsilon\mathbf a)\right]_{\epsilon=0}
=\mathbf a\cdot\partial_{\mathbf r}F.
$$

Thus $\partial_{\mathbf r}F$ is a vector, while the directional derivative along $\mathbf a$ is a scalar. We will write the latter as

$$
D_{\mathbf a}F
:=\left[\frac{d}{d\epsilon}F(\mathbf r+\epsilon\mathbf a)\right]_{\epsilon=0}
=\mathbf a\cdot\partial_{\mathbf r}F.
$$

The lecture notes label a directional derivative by the direction in which it acts. The notation $D_{\mathbf a}$ makes that role explicit and keeps it distinct from the full vector derivative $\partial_{\mathbf r}$. If $A(\mathbf r)$ is vector- or multivector-valued, define $D_{\mathbf a}A$ by differentiating its components in the same way. For example, if $\mathbf r$ and $\mathbf a$ lie in the plane of a fixed unit bivector $I$ and $A(\mathbf r)=\mathbf r I$, then

$$
D_{\mathbf a}A=\mathbf a I.
$$

For a fixed direction $\mathbf a$, the directional derivative obeys the usual product rule for the geometric product:

$$
D_{\mathbf a}(AB)=(D_{\mathbf a}A)B+A(D_{\mathbf a}B).
$$

Along an actual path $\mathbf r(t)$, this same directional derivative gives the ordinary time derivative. If $A$ also depends explicitly on time, then

$$
\frac{d}{dt}A(\mathbf r(t),t)
=\frac{\partial A}{\partial t}+D_{\dot{\mathbf r}}A.
$$

For scalar functions of velocity we use the corresponding gradient $\partial_{\dot{\mathbf r}}F$. This notation will let us differentiate vector-valued quantities while keeping clear whether a symbol is a gradient, a directional change, or a time rate of change.

For a scalar Lagrangian $L(t,\mathbf r,\dot{\mathbf r})$, a small change $\delta\mathbf r$ in position changes the velocity by $\delta\dot{\mathbf r}=d(\delta\mathbf r)/dt$. The first-order change in $L$ is

$$
\delta L=
\delta\mathbf r\cdot\partial_{\mathbf r}L+
\delta\dot{\mathbf r}\cdot\partial_{\dot{\mathbf r}}L.
$$

The derivatives act on the indicated vector arguments. The dot products produce a scalar change in the Lagrangian. This is ordinary differentiation of scalar functions, expressed without choosing separate component equations.

## 12.2 The action and nearby paths

Let a particle follow a path $\mathbf r(t)$ from time $t_0$ to $t_1$. We write the action functional as

$$
S[\mathbf r]=\int_{t_0}^{t_1}L(t,\mathbf r,\dot{\mathbf r})\,dt.
$$

For the mechanical systems in this part of the book, $L=T-V$, kinetic energy minus potential energy. The action has units of energy multiplied by time.

Vary the path while keeping its endpoints fixed:

$$
\mathbf r_\epsilon(t)=\mathbf r(t)+\epsilon\boldsymbol\eta(t),
\qquad
\boldsymbol\eta(t_0)=\boldsymbol\eta(t_1)=\mathbf 0.
$$

Here $\boldsymbol\eta(t)$ is an arbitrary smooth vector-valued variation that vanishes at the endpoints, and $\epsilon$ is a small scalar. The first variation is the derivative of the action with respect to this parameter:

```{important} Hamilton's principle

Among nearby paths with the same endpoints and elapsed time, the physical path makes the action stationary:

$$
\delta S=\left[\frac{d}{d\epsilon}S[\mathbf r_\epsilon]\right]_{\epsilon=0}=0.
$$

Stationary does not necessarily mean that the action is a minimum. It can also be a maximum or a saddle point.
```

The endpoint condition will remove a boundary term when we integrate by parts. The variation $\boldsymbol\eta$ is otherwise free to point in any direction at each intermediate time.

## 12.3 The vector Euler–Lagrange equation

Apply the directional-derivative rule from Section 12.1 to the action. Since $\delta\dot{\mathbf r}=\dot{\boldsymbol\eta}$,

$$
\delta S=
\int_{t_0}^{t_1}
\left(
\boldsymbol\eta\cdot\partial_{\mathbf r}L+
\dot{\boldsymbol\eta}\cdot\partial_{\dot{\mathbf r}}L
\right)dt.
$$

Define the vector momentum

$$
\mathbf p=\partial_{\dot{\mathbf r}}L.
$$

Integrating the second term by parts gives

$$
\delta S=
\left[\boldsymbol\eta\cdot\mathbf p\right]_{t_0}^{t_1}
+\int_{t_0}^{t_1}\boldsymbol\eta\cdot
\left(\partial_{\mathbf r}L-\dot{\mathbf p}\right)dt.
$$

The boundary term vanishes because $\boldsymbol\eta$ is zero at both endpoints. Since its values at intermediate times are arbitrary vectors, the remaining integrand must vanish:

```{note} Euler–Lagrange equation in physical space

For a path in unconstrained Euclidean space,

$$
\partial_{\mathbf r}L-\frac{d}{dt}\left(\partial_{\dot{\mathbf r}}L\right)=\mathbf 0,
\qquad\text{or equivalently}\qquad
\dot{\mathbf p}=\partial_{\mathbf r}L.
$$
```

This is one vector equation, equivalent to one scalar equation per independent spatial direction. It is the coordinate-free form of the Euler–Lagrange equations. For constrained motion, only variations tangent to the allowed configurations are free; the equations then give the tangent projections, while constraint forces can act in the normal directions.

### Example: a particle in a potential

For a particle of constant mass $m$ in a scalar potential $V(\mathbf r)$,

$$
L=\frac12m\dot{\mathbf r}^{,2}-V(\mathbf r),
\qquad
\dot{\mathbf r}^{,2}=\dot{\mathbf r}\cdot\dot{\mathbf r}.
$$

The vector derivatives are

$$
\partial_{\dot{\mathbf r}}L=m\dot{\mathbf r}=\mathbf p,
\qquad
\partial_{\mathbf r}L=-\partial_{\mathbf r}V.
$$

The vector Euler–Lagrange equation therefore becomes

$$
m\ddot{\mathbf r}=-\partial_{\mathbf r}V=\mathbf F.
$$

So Newton's second law follows directly from stationary action for this Lagrangian. The kinetic energy uses the squared length of a vector, while the force is the vector derivative of the potential. In geometric algebra, the geometric square of a Euclidean vector is precisely that scalar squared length.

## 12.4 Generalized coordinates as tangent directions

Suppose the allowed positions are described by independent generalized coordinates $q^1,\ldots,q^n$ through a smooth map

$$
\mathbf r=\mathbf f(q^1,\ldots,q^n).
$$

The coordinate tangent vectors are

$$
\mathbf g_i=\frac{\partial\mathbf f}{\partial q^i}.
$$

A small coordinate change gives $d\mathbf r=\sum_i\mathbf g_i\,dq^i$, and a motion gives

$$
\dot{\mathbf r}=\sum_i\mathbf g_i\dot q^i.
$$

The tangent vectors need not have unit length or be mutually perpendicular. Their inner products contain the metric of the chosen coordinates; for a particle,

$$
\dot{\mathbf r}^{,2}=\sum_{i,j}(\mathbf g_i\cdot\mathbf g_j)\dot q^i\dot q^j.
$$

Substitute the position map and velocity into the physical-space Lagrangian to obtain the coordinate Lagrangian

$$
\mathcal L(t,q,\dot q)=
L\left(t,\mathbf f(q),\sum_i\mathbf g_i\dot q^i\right).
$$

The generalized momentum conjugate to $q^i$ is the projection of the physical momentum onto the corresponding tangent direction:

$$
p_i=\frac{\partial\mathcal L}{\partial\dot q^i}
=\mathbf g_i\cdot\mathbf p.
$$

This relation is a useful bridge between the two notations. The vector $\mathbf p$ belongs to physical space; each $p_i$ is a scalar component along a coordinate tangent. The generalized Euler–Lagrange equations are

$$
\frac{d}{dt}\left(\frac{\partial\mathcal L}{\partial\dot q^i}\right)
-\frac{\partial\mathcal L}{\partial q^i}=0,
\qquad i=1,\ldots,n.
$$

To see their geometric meaning, differentiate the pulled-back Lagrangian. For a fixed position map $\mathbf f(q)$,

$$
\frac{\partial\mathcal L}{\partial q^i}
=\mathbf g_i\cdot\partial_{\mathbf r}L+\dot{\mathbf g}_i\cdot\mathbf p,
\qquad
\frac{d p_i}{dt}=\dot{\mathbf g}_i\cdot\mathbf p+\mathbf g_i\cdot\dot{\mathbf p}.
$$

Subtracting cancels the terms that arise from the changing tangent direction:

$$
\dot p_i-\frac{\partial\mathcal L}{\partial q^i}
=\mathbf g_i\cdot\left(\dot{\mathbf p}-\partial_{\mathbf r}L\right)=0.
$$

Thus the coordinate equations are the projections of the physical-space equation onto the allowed tangent directions. If the coordinate map describes a constrained surface, the unprojected normal component is supplied by the constraint force. This is why generalized coordinates can eliminate ideal constraint forces without losing the geometry of the motion.

## 12.5 Example: the harmonic oscillator

For a mass $m$ attached to an ideal spring, motion is along a fixed unit vector $\mathbf e_1$. Write $\mathbf r=x\mathbf e_1$ and let $x=0$ be the equilibrium position. The potential and Lagrangian are

$$
V=\frac12kx^2,
\qquad
L=\frac12m\dot{\mathbf r}^{,2}-\frac12kx^2.
$$

The derivatives in vector form are

$$
\partial_{\dot{\mathbf r}}L=m\dot x\mathbf e_1,
\qquad
\partial_{\mathbf r}L=-kx\mathbf e_1.
$$

The vector equation gives

$$
m\ddot x\mathbf e_1=-kx\mathbf e_1,
\qquad
\ddot x+\omega_0^2x=0,
\qquad
\omega_0=\sqrt{\frac{k}{m}}.
$$

Projecting onto $\mathbf e_1$ recovers the familiar scalar oscillator equation. Here the vector notation adds little computational work, but it makes clear how the scalar force law is the one-dimensional case of the vector equation.

## 12.6 Rotational symmetry in a plane

Now consider a particle moving in a plane under a central potential $V(r)$, where $r=|\mathbf r|$. Choose a fixed orthonormal basis $\mathbf e_1,\mathbf e_2$ for the plane and define its unit bivector

$$
I=\mathbf e_1\mathbf e_2=\mathbf e_1\wedge\mathbf e_2,
\qquad I^2=-1.
$$

Write the radial and tangential unit vectors as

$$
\mathbf e_r=\cos\theta\,\mathbf e_1+\sin\theta\,\mathbf e_2,
\qquad
\mathbf e_\theta=\mathbf e_r I.
$$

The position and its coordinate tangent vectors are

$$
\mathbf r=r\mathbf e_r,
\qquad
\mathbf g_r=\frac{\partial\mathbf r}{\partial r}=\mathbf e_r,
\qquad
\mathbf g_\theta=\frac{\partial\mathbf r}{\partial\theta}=r\mathbf e_\theta.
$$

Consequently,

$$
\dot{\mathbf r}=\dot r\mathbf e_r+r\dot\theta\mathbf e_\theta,
\qquad
\dot{\mathbf r}^{,2}=\dot r^2+r^2\dot\theta^2.
$$

The coordinate Lagrangian and angular generalized momentum are

$$
\mathcal L=\frac12m\left(\dot r^2+r^2\dot\theta^2\right)-V(r),
\qquad
p_\theta=\frac{\partial\mathcal L}{\partial\dot\theta}
=\mathbf g_\theta\cdot\mathbf p=mr^2\dot\theta.
$$

The potential is independent of $\theta$, so $\theta$ is cyclic and $p_\theta$ is constant. In three dimensions, angular momentum is naturally the bivector

$$
\mathcal J=\mathbf r\wedge\mathbf p
$$

Its time derivative is

$$
\dot{\mathcal J}
=\dot{\mathbf r}\wedge\mathbf p+\mathbf r\wedge\dot{\mathbf p}
=\mathbf r\wedge\mathbf F,
$$

because $\dot{\mathbf r}=\mathbf p/m$ makes the first term zero. A central force is parallel to $\mathbf r$, so $\mathbf r\wedge\mathbf F=\mathbf 0$ and $\mathcal J$ is conserved. This single statement works in three dimensions: the constant bivector records the fixed plane of the orbit. In three-dimensional Euclidean space its dual is the familiar axial vector $\mathbf r\times\mathbf p$.

For motion in the plane above, $\mathbf e_r\wedge\mathbf e_\theta=I$, so the bivector becomes

$$
\mathcal J=\mathbf r\wedge\mathbf p
=mr^2\dot\theta\,I=p_\theta I.
$$

Because $I$ is fixed, conservation of $p_\theta$ is exactly conservation of $\mathcal J$. The scalar generalized momentum is convenient in the polar-coordinate equation; the bivector records the oriented plane of the motion.

The radial equation is

$$
m\ddot r-mr\dot\theta^2+V'(r)=0.
$$

Using $\dot\theta=p_\theta/(mr^2)$ reduces it to one-dimensional motion in the effective potential

$$
m\ddot r=-\frac{dV_{\mathrm{eff}}}{dr},
\qquad
V_{\mathrm{eff}}(r)=V(r)+\frac{p_\theta^2}{2mr^2}.
$$

The extra term is the radial effect of the conserved angular motion. No cross product is needed to identify the orbital plane: the bivector $\mathcal J$ represents that plane directly.

## 12.7 Time translation, energy, and Noether's theorem

For a particle described in physical space, define

$$
E=\dot{\mathbf r}\cdot\mathbf p-L.
$$

Along a solution of the vector Euler–Lagrange equation, differentiation gives

$$
\frac{dE}{dt}=-\frac{\partial L}{\partial t}.
$$

Therefore $E$ is conserved if the Lagrangian has no explicit time dependence. For $L=T-V$ with kinetic energy quadratic in velocity and a velocity-independent potential,

$$
E=\dot{\mathbf r}\cdot m\dot{\mathbf r}-\left(T-V\right)=T+V.
$$

In generalized coordinates the same quantity is

$$
E=\sum_i\dot q^i p_i-\mathcal L.
$$

This is the energy function of the Lagrangian. It equals mechanical energy for the usual $T-V$ systems considered here. If the setup changes explicitly with time, energy need not be conserved.

The connection between symmetry and conserved quantities is the introductory form of **Noether's theorem**. If the Lagrangian is unchanged by translating the origin, it has no position dependence and the vector equation gives $\dot{\mathbf p}=\mathbf 0$: linear momentum is conserved. If the Lagrangian is unchanged by rotations, angular momentum is conserved. For a central potential, the plane bivector calculation above makes that rotational conservation explicit. In the next part of the book, the generalized momenta $p_i$ become coordinates on phase space.

## 12.8 What the Lagrangian view adds

The vector form keeps position, momentum, and tangent directions as geometric objects. It makes the Euler–Lagrange equation compact and shows directly how generalized-coordinate equations arise by projecting onto allowed directions. GA contributes a clear language for vector derivatives, squared lengths, oriented planes, and angular momentum.

Coordinates remain valuable. The scalar Euler–Lagrange equations are often the quickest way to solve a particular problem, while component and matrix calculations organize systems with many coordinates. We use both descriptions: the vector equation to expose the geometry, and generalized coordinates when they simplify the mechanics.

### Exercises

1. For a scalar function $F(\mathbf r)$, verify from its component definition that $\left[\frac{d}{d\epsilon}F(\mathbf r+\epsilon\mathbf a)\right]_{0}=\mathbf a\cdot\partial_{\mathbf r}F$.
2. In a plane with fixed unit bivector $I$, verify from the definition that $D_{\mathbf a}(\mathbf r I)=\mathbf a I$. Then use the product rule to differentiate $(\mathbf r I)\mathbf r$ in a fixed direction.
3. For $F(\mathbf r,t)=\tfrac12k\mathbf r^2+ct$, use the chain rule to find $dF/dt$ along a path $\mathbf r(t)$.
4. Starting from the action in Section 12.2, show each step of the integration by parts that gives the vector Euler–Lagrange equation.
5. For $L=\tfrac12m\dot{\mathbf r}^{,2}-V(\mathbf r)$, derive Newton's second law and identify the force as the vector derivative of the potential.
6. For a smooth coordinate map $\mathbf r=\mathbf f(q)$, verify that $p_i=\mathbf g_i\cdot\mathbf p$ and that the generalized equations are tangent projections of the vector equation.
7. For a particle in a central potential, derive the conserved $p_\theta$ and the effective radial potential. Show that $\mathcal J=\mathbf r\wedge\mathbf p=p_\theta I$.
8. Show that if $L$ has no explicit time dependence, then $E=\dot{\mathbf r}\cdot\mathbf p-L$ is constant along a solution.

## Further reading

- John R. Taylor, [*Classical Mechanics*](https://uscibooks.aip.org/books/classical-mechanics/), for a clear development of the Lagrangian formulation and central-force motion.
- David Hestenes, [*New Foundations for Classical Mechanics*](https://davidhestenes.net/geocalc/html/NFCM.html), for geometric treatments of mechanics, rotations, and angular momentum.
