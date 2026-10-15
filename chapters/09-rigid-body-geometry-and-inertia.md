---
title: "9. Rigid-Body Geometry and Inertia"
description: "Describe rigid-body orientation and mass distribution, relating a geometric inertia operator to the familiar inertia tensor and principal axes."
---

A rigid body's motion combines translation of a chosen reference point with rotation about that point. The body's shape and mass distribution determine how difficult each rotation is. A long rod, for example, is easy to spin about its long axis and much harder to spin about an axis through its centre and perpendicular to its length.

This chapter separates orientation from mass distribution. Rotors from Chapter 8 describe orientation without committing to three angles. The inertia tensor remains the most convenient tool for many calculations, while its geometric-algebra form shows how angular velocity and angular momentum are related as planes.

## 9.1 Orientation of a rigid body

For a rigid body, distances between all pairs of its points remain fixed. Choose a reference point $O$, such as the centre of mass, and describe each material point by a constant body-fixed vector $\boldsymbol\rho$. Its position relative to inertial axes is

$$
\mathbf r=\mathbf R_O+Q\boldsymbol\rho\widetilde Q,
$$

where $\mathbf R_O$ is the position of the reference point and $Q$ is the body's orientation rotor. Since $Q\widetilde Q=1$, the rotor preserves lengths and angles. The orientation has three independent degrees of freedom in three dimensions, but a rotor uses four scalar components constrained by one normalization condition. This redundancy avoids the coordinate singularities that can occur with Euler angles.

The velocity of a point follows by differentiating. If the reference point is fixed and the angular-velocity bivector is $\boldsymbol\Omega=-2\dot Q\widetilde Q$, then

$$
\mathbf v=\frac12(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r).
$$

For a translating reference point, add $\mathbf V_O$. In three-dimensional vector notation this is the familiar rigid-body formula $\mathbf v=\mathbf V_O+\boldsymbol\omega\times\mathbf r$.

## 9.2 Rotational kinetic energy and the inertia tensor

Consider a rigid body made of particles indexed by $a$, with masses $m_a$ and positions $\mathbf r_a$ relative to its centre of mass. Its rotational kinetic energy is

$$
T_{\mathrm{rot}}=\frac12\sum_a m_a\,\mathbf v_a^2.
$$

Using $\mathbf v_a=\boldsymbol\omega\times\mathbf r_a$ gives

$$
T_{\mathrm{rot}}=\frac12\boldsymbol\omega\cdot\mathsf I\boldsymbol\omega,
$$

where the conventional inertia tensor is

$$
\mathsf I=\sum_a m_a\left(r_a^2\mathsf 1-\mathbf r_a\mathbf r_a^{\mathsf T}\right).
$$

For a continuous body, replace the sum with $\int dm$. In components,

$$
I_{ij}=\int\left(r^2\delta_{ij}-x_i x_j\right)dm.
$$

This form follows from

$$
\mathbf r\times(\boldsymbol\omega\times\mathbf r)
=r^2\boldsymbol\omega-\mathbf r(\mathbf r\cdot\boldsymbol\omega).
$$

Integrating the identity gives $\mathbf L=\mathsf I\boldsymbol\omega$. For the kinetic energy, use $|\boldsymbol\omega\times\mathbf r|^2=\omega^2r^2-(\boldsymbol\omega\cdot\mathbf r)^2$. The same tensor therefore supplies both angular momentum and rotational energy: $T_{\mathrm{rot}}=\tfrac12\boldsymbol\omega\cdot\mathsf I\boldsymbol\omega$.

The tensor depends on the chosen reference point and axes. It converts angular velocity into angular momentum,

$$
\mathbf L=\mathsf I\boldsymbol\omega,
$$

and it is symmetric. Its diagonal entries in a particular basis are not always enough: for a body whose axes are poorly chosen, the off-diagonal products of inertia couple rotations about different directions.

## 9.3 Mathematical tools: the geometric inertia operator

The same relation can be written using bivectors. For a point at $\mathbf r$ rotating with angular-velocity bivector $\boldsymbol\Omega$, its velocity relative to the centre is

$$
\mathbf v=\frac12(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r).
$$

Its angular momentum is $\mathbf r\wedge\mathbf v\,dm$. Summing over the body defines a linear map from angular-velocity bivectors to angular-momentum bivectors:

$$
\mathcal J=\mathsf I_{\mathrm{GA}}(\boldsymbol\Omega),
\qquad
\mathsf I_{\mathrm{GA}}(\boldsymbol\Omega)
=\int \mathbf r\wedge\frac12(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r)\,dm.
$$

This is an inertia operator on the three-dimensional space of rotation planes. In 3D, duality turns those bivectors into axial vectors, and this operator is equivalent to the usual inertia tensor. The bivector form keeps the plane of angular momentum visible; the tensor matrix is usually better for numerical calculation and for finding principal axes.

To check the correspondence for a point mass, consider rotation about $\mathbf e_3$. Set $\boldsymbol\Omega=\omega\mathbf e_1\mathbf e_2$ and write $\mathbf r=x\mathbf e_1+y\mathbf e_2+z\mathbf e_3$. The commutator gives

$$
\mathbf v=\frac12(\mathbf r\boldsymbol\Omega-\boldsymbol\Omega\mathbf r)
=\omega(-y\mathbf e_1+x\mathbf e_2),
$$

and hence

$$
\mathbf r\wedge\mathbf v\,dm
=\omega\left[(x^2+y^2)\mathbf e_1\mathbf e_2
+xz\,\mathbf e_3\mathbf e_2-yz\,\mathbf e_3\mathbf e_1\right]dm.
$$

For a body symmetric about the $\mathbf e_3$ axis, the last two terms cancel in the integral. The remaining coefficient is $I_3\omega$, where $I_3=\int(x^2+y^2)dm$, so $\mathcal J=I_3\omega\mathbf e_1\mathbf e_2$. This is the axial-vector result $L_3=I_3\omega$ written as an oriented plane.

The rotational kinetic energy can also be recovered from the pairing of angular momentum and angular velocity:

$$
T_{\mathrm{rot}}=\frac12\boldsymbol\omega\cdot\mathbf L
=\frac12\left\langle\widetilde{\mathcal J}\,\boldsymbol\Omega\right\rangle_0.
$$

Here $\langle\cdot\rangle_0$ means take the scalar part of a multivector. In the axial-vector representation, the first expression is immediately familiar. The second makes explicit that both rotational quantities can be represented in the same bivector space.

## 9.4 Principal axes

Because $\mathsf I$ is a real symmetric matrix, it has three mutually perpendicular eigenvectors. These are the **principal axes**, and the corresponding eigenvalues $I_1,I_2,I_3$ are the principal moments of inertia. In body-fixed principal-axis coordinates,

$$
\mathbf L=I_1\omega_1\mathbf e_1+I_2\omega_2\mathbf e_2+I_3\omega_3\mathbf e_3,
\qquad
T_{\mathrm{rot}}=\frac12(I_1\omega_1^2+I_2\omega_2^2+I_3\omega_3^2).
$$

The matrix diagonalization is ordinary linear algebra. GA does not replace it; it gives a basis-independent description of the rotation planes and makes the body-versus-space orientation explicit.

### Worked example: a thin uniform rod

Take a thin rod of length $\ell$ and mass $M$ centred at the origin along the $x$ axis. For rotation about the rod, each point lies on the axis, so the ideal thin-rod moment is $I_x=0$. About a perpendicular axis through the centre,

$$
I_y=I_z=\int_{-\ell/2}^{\ell/2}x^2\,dm
=\frac{M}{\ell}\int_{-\ell/2}^{\ell/2}x^2 dx
=\frac{1}{12}M\ell^2.
$$

The same mass therefore responds very differently depending on the rotation axis. A real rod has a small but nonzero axial moment because its cross-section has finite width.

### Worked example: a uniform rectangular lamina

Take a thin rectangular plate of sides $a$ and $b$, mass $M$, centred in the $xy$-plane. Its surface density is $\sigma=M/(ab)$. Integrating over the rectangle gives

$$
I_x=\sigma\int_{-a/2}^{a/2}\int_{-b/2}^{b/2}y^2\,dy\,dx
=\frac{Mb^2}{12},
\qquad
I_y=\frac{Ma^2}{12}.
$$

For rotation about the perpendicular $z$ axis,

$$
I_z=\sigma\int_{-a/2}^{a/2}\int_{-b/2}^{b/2}(x^2+y^2)\,dy\,dx
=\frac{M(a^2+b^2)}{12}=I_x+I_y.
$$

This calculation verifies the perpendicular-axis theorem for this lamina and shows how the tensor reduces to familiar scalar moments when the axes match the body's symmetries.

## 9.5 Changing the reference point

The inertia tensor depends on its reference point. If the centre of mass is displaced from a point $O$ by vector $\mathbf d$, the parallel-axis theorem gives

$$
\mathsf I_O=\mathsf I_{\mathrm{cm}}+M\left(d^2\mathsf 1-\mathbf d\mathbf d^{\mathsf T}\right).
$$

To see why, write each position from $O$ as $\mathbf r_a=\boldsymbol\rho_a+\mathbf d$, where $\boldsymbol\rho_a$ is measured from the centre of mass. In the inertia integral, the terms linear in $\boldsymbol\rho_a$ vanish because $\int\boldsymbol\rho\,dm=0$. The remaining terms are the centre-of-mass inertia plus $\int(d^2\mathsf 1-\mathbf d\mathbf d^{\mathsf T})dm$, which gives the stated result.

For a specified axis with unit direction $\mathbf n$, this reduces to the scalar formula

$$
I_O=I_{\mathrm{cm}}+Md_\perp^2,
$$

where $d_\perp$ is the perpendicular distance between the axes. The full tensor expression accounts for all directions at once.

For a planar body lying in the $xy$-plane, the perpendicular-axis theorem states $I_z=I_x+I_y$ about a common point. It follows because every mass element has $z=0$ and $x^2+y^2$ is its squared distance from the perpendicular axis. Such relations are useful checks on calculated moments.

## 9.6 When each description is useful

Use the inertia tensor when computing angular momentum from angular velocity, finding principal axes, or implementing a rigid-body calculation. Use a rotor when tracking orientation or composing rotations. Use the bivector angular momentum when the plane of rotation is itself the important geometric quantity, especially when comparing angular momentum with torque.

These are complementary descriptions of one rigid body. A rotor encodes orientation; an inertia operator encodes how the mass distribution responds to angular velocity; and angular momentum describes the resulting rotational state. Keeping these roles distinct prevents a compact notation from hiding the physical assumptions.

## 9.7 What to remember

- A rigid body's orientation can be represented by a rotor acting on its body-fixed vectors.
- The inertia tensor relates angular velocity to angular momentum and determines rotational kinetic energy.
- In GA, the inertia operator maps an angular-velocity bivector to an angular-momentum bivector.
- Principal axes diagonalize the symmetric inertia tensor; eigenvalues are the principal moments.
- The parallel-axis theorem adjusts inertia when the reference point changes.
- Matrices remain the practical choice for many calculations; rotors and bivectors make orientation and rotation planes explicit.

### Exercises

1. A thin rod has mass $2.0\,\mathrm{kg}$ and length $1.2\,\mathrm m$. Find its moment of inertia about its centre and a perpendicular axis.
2. Explain why an ideal thin rod has zero moment of inertia about its long axis, and why a real rod does not.
3. A body has principal moments $I_1=2$, $I_2=3$, and $I_3=5\,\mathrm{kg\,m^2}$. Find its rotational kinetic energy when its body-frame angular velocity is $(1,2,1)\,\mathrm{rad\,s^{-1}}$.
4. State what physical information is encoded by a rotor, an inertia tensor, and an angular-momentum bivector.
5. Use the parallel-axis theorem to find the moment of inertia of a uniform rod about an axis through one endpoint and perpendicular to it.
6. For a planar lamina, explain why its moment about the perpendicular axis is the sum of the two in-plane moments about the same point.
7. **Synthesis.** A rectangular lamina has sides $a,b$ and centre of mass at the origin. Use its principal moments to find the moment about an axis parallel to its $z$ axis through a point displaced by $d$ in the plane. State the corresponding parallel-axis result using the inertia tensor and describe the same rotation plane with a bivector.

## Further reading

- John R. Taylor, *Classical Mechanics*, sections on rigid-body rotation and the inertia tensor.
- Herbert Goldstein, Charles Poole, and John Safko, *Classical Mechanics*, for a broader treatment of rigid-body kinematics.
- David Hestenes, *New Foundations for Classical Mechanics*, for geometric-algebra descriptions of rotations and angular momentum.
