---
title: "1. Vectors, Products, and Oriented Geometry"
description: "The first geometric algebra ideas: vectors, the inner and outer products, grades, blades, and the geometric product."
---

Newton's second law can be written in the familiar form

$$
\mathbf F_{\mathrm{net}}=m\mathbf a,
\qquad
\mathbf a=\frac{d\mathbf v}{dt}.
$$

Here force, acceleration, and velocity are vectors; mass is a scalar. This notation works very well. Geometric algebra extends the ways we can combine vectors, especially when a calculation involves both a scalar quantity such as work and an oriented plane such as the one associated with angular momentum. We will first build that language, then use it to revisit familiar mechanics.

Vectors are already part of the mechanics you know: they describe displacement, velocity, acceleration, momentum, and force. Each has magnitude and direction. In this chapter we mostly use free vectors, such as force and velocity, whose arrows can be shifted parallel to themselves without changing the quantity. A position vector is tied to the chosen origin, a distinction we will keep when it matters.

Ordinary vector algebra gives us several ways to multiply vectors. The dot product measures alignment. The cross product in three dimensions points perpendicular to the plane spanned by its two input vectors. Geometric algebra combines the useful information in these products into one operation, the **geometric product**. To understand that product, we first need a language for oriented areas.

## 1.1 Vectors and directions

For calculation, choose two perpendicular unit vectors $\mathbf e_1$ and $\mathbf e_2$ in a plane. They give us directions for measuring components. Any vector in the plane can be written

$$
\mathbf a = a_1\mathbf e_1+a_2\mathbf e_2,
$$

where $a_1$ and $a_2$ are ordinary numbers. The basis vectors are a useful way to calculate, but the vector itself does not depend on our choice of axes.

A scalar is an ordinary real number, such as a mass, a time interval, a temperature difference, or work. It has no direction and may carry a sign. We will combine scalars and vectors with new geometric objects as we develop the algebra.

## 1.2 The inner product: how much one vector points along another

The familiar dot product is also called the **inner product**. For vectors $\mathbf a$ and $\mathbf b$ with angle $\theta$ between them,

$$
\mathbf a\cdot\mathbf b = |\mathbf a|\,|\mathbf b|\cos\theta.
$$

It is a scalar. If the vectors point in the same direction, the dot product is positive and large. If they are perpendicular, it is zero. If they point in opposite directions, it is negative.

The inner product appears throughout mechanics. For example, the work done by a constant force $\mathbf F$ during a displacement $\mathbf s$ is

$$
W=\mathbf F\cdot\mathbf s.
$$

Only the part of the force along the displacement contributes to the work. The dot product captures that projection in one number.

## 1.3 The outer product: the oriented area between two vectors

Now place the tails of $\mathbf a$ and $\mathbf b$ at the same point. Together they span a parallelogram. Its area is

$$
|\mathbf a|\,|\mathbf b|\,|\sin\theta|.
$$

But area alone does not tell us the order in which the vectors turn around the parallelogram. The **outer product**, written $\mathbf a\wedge\mathbf b$, keeps this orientation as well as the area. In a plane with a chosen positive orientation, write $\mathbf I$ for the unit oriented area. Then

$$
\mathbf a\wedge\mathbf b = |\mathbf a|\,|\mathbf b|\sin\theta\,\mathbf I,
$$

where $\theta$ is the directed angle from $\mathbf a$ to $\mathbf b$.

Swapping the vectors reverses the orientation:

$$
\mathbf b\wedge\mathbf a=-\mathbf a\wedge\mathbf b.
$$

If the vectors are parallel, the parallelogram collapses to a line and the outer product is zero. If they are perpendicular, its area is as large as possible for their given lengths.

The result of an outer product is not another vector. It is an oriented piece of plane, called a **bivector**. In two dimensions, a bivector records signed area in the plane. In three dimensions, a bivector records a plane with an orientation and an area scale.

## 1.4 The geometric product

The geometric product of two vectors combines their inner and outer products:

$$
\mathbf a\mathbf b = \mathbf a\cdot\mathbf b+\mathbf a\wedge\mathbf b.
$$

The right side has a scalar part and a bivector part. We have not mixed unlike quantities into one number: the geometric product is an algebraic object with distinct **grades**. The grade tells us what kind of geometric quantity a part of the result represents.

The order of the vectors matters. The inner product is unchanged when its arguments are swapped, while the outer product changes sign. Therefore

$$
\mathbf b\mathbf a = \mathbf a\cdot\mathbf b-\mathbf a\wedge\mathbf b.
$$

Adding these two products gives twice the inner product; subtracting them gives twice the outer product. So the geometric product contains both pieces of information, and we can recover either one when we need it.

For a vector multiplied by itself, the outer product vanishes because a vector spans no area with itself. Thus

$$
\mathbf a^2=\mathbf a\cdot\mathbf a=|\mathbf a|^2.
$$

This is a compact way to express the familiar fact that a vector’s square gives its length squared.

## 1.5 A two-dimensional example

Let $\mathbf e_1$ and $\mathbf e_2$ be perpendicular unit vectors, with $\mathbf e_1$ followed by $\mathbf e_2$ defining the positive orientation of the plane. Define

$$
\mathbf I=\mathbf e_1\wedge\mathbf e_2.
$$

Because the basis vectors are perpendicular, their inner product is zero, so their geometric product is just their outer product:

$$
\mathbf e_1\mathbf e_2=\mathbf I,
\qquad
\mathbf e_2\mathbf e_1=-\mathbf I.
$$

The unit bivector $\mathbf I$ represents the plane’s oriented unit area. The geometric product of the basis vectors has captured that orientation directly.

Consider

$$
\mathbf a=2\mathbf e_1+\mathbf e_2,
\qquad
\mathbf b=\mathbf e_1+3\mathbf e_2.
$$

Their inner product is

$$
\mathbf a\cdot\mathbf b=2\cdot1+1\cdot3=5.
$$

Their outer product is

$$
\begin{aligned}
\mathbf a\wedge\mathbf b
&=(2\mathbf e_1+\mathbf e_2)\wedge(\mathbf e_1+3\mathbf e_2)\\
&=6\,\mathbf e_1\wedge\mathbf e_2+\mathbf e_2\wedge\mathbf e_1\\
&=5\mathbf I.
\end{aligned}
$$

The geometric product keeps both results together:

$$
\mathbf a\mathbf b=5+5\mathbf I,
\qquad
\mathbf b\mathbf a=5-5\mathbf I.
$$

The scalar part tells us about alignment; the bivector part tells us about the oriented area. Neither piece replaces the other.

## 1.6 Grades, blades, and multivectors

The grades we meet first are summarized here.

| Grade | Name | Geometric meaning |
|---|---|---|
| 0 | Scalar | A real number, which may be positive, negative, or zero |
| 1 | Vector | A directed quantity with magnitude and direction |
| 2 | Bivector | An oriented plane element with an area scale |
| 3 | Trivector | An oriented volume element in three dimensions |

A product such as $\mathbf a\wedge\mathbf b$ is a simple example of a **blade**: an oriented geometric element built from vectors using the outer product. Two independent vectors make a bivector blade. Three independent vectors can make a trivector blade.

A **multivector** is a sum of terms with different grades. The geometric product of two vectors is our first example: it contains a scalar and a bivector. Geometric algebra lets us calculate with these different geometric quantities in a common system while keeping their grades distinct.

The highest-grade unit blade in a space is called its **pseudoscalar**. In a plane this role is played by $\mathbf I=\mathbf e_1\mathbf e_2$. In three-dimensional space the corresponding unit volume element is $\mathbf I=\mathbf e_1\mathbf e_2\mathbf e_3$. We will use the pseudoscalar to describe orientation and rotations in the next chapter.

## 1.7 A first mechanics connection: angular momentum

For a particle at position $\mathbf r$ with momentum $\mathbf p=m\mathbf v$, form the outer product

$$
\mathbf L=\mathbf r\wedge\mathbf p.
$$

This is angular momentum written as a bivector. It records the oriented plane spanned by the particle’s position and momentum, with a magnitude that depends on their lengths and the angle between them.

If the momentum points directly toward or away from the origin, $\mathbf r$ and $\mathbf p$ are parallel and $\mathbf L=0$. If they are perpendicular, the magnitude is greatest for the given $|\mathbf r|$ and $|\mathbf p|$.

In planar mechanics, the familiar scalar expression is $L_z=xp_y-yp_x$. The bivector form writes the same information as

$$
\mathbf r\wedge\mathbf p=(xp_y-yp_x)\mathbf I.
$$

In three-dimensional vector notation, angular momentum is usually written $\mathbf r\times\mathbf p$. The right-hand rule represents the same oriented plane by a vector perpendicular to it. The bivector keeps the plane itself, while the cross product uses this perpendicular vector representation. We will compare these descriptions when we study rotations in more detail.

This is a useful example of the book’s approach. When the geometric object is an oriented plane, GA can represent it directly. When a scalar calculation or a familiar vector formula is simpler, we will use that instead.

## 1.8 What to remember

- The inner product $\mathbf a\cdot\mathbf b$ is a scalar that measures alignment.
- The outer product $\mathbf a\wedge\mathbf b$ is a bivector that records oriented area.
- The geometric product combines both: $\mathbf a\mathbf b=\mathbf a\cdot\mathbf b+\mathbf a\wedge\mathbf b$.
- Grade identifies the geometric type of each part of a multivector.
- The outer product gives a direct geometric form for angular momentum.

### Exercises

1. Draw two non-parallel vectors from a common point. Show their parallelogram and indicate how its orientation changes when you exchange the vectors.
2. For $\mathbf a=2\mathbf e_1+\mathbf e_2$ and $\mathbf b=\mathbf e_1+3\mathbf e_2$, verify the inner product, outer product, and geometric product calculated above.
3. Let $\mathbf r=2\mathbf e_1$ metres and $\mathbf p=3\mathbf e_2$ kilogram-metres per second. Find $\mathbf r\wedge\mathbf p$ and state its units.
4. Describe what happens to $\mathbf r\wedge\mathbf p$ when $\mathbf r$ and $\mathbf p$ are parallel. Relate your answer to the line of motion of a particle.
5. In the plane, define $\mathbf I=\mathbf e_1\mathbf e_2$, with $\mathbf e_1^2=\mathbf e_2^2=1$ and $\mathbf e_2\mathbf e_1=-\mathbf e_1\mathbf e_2$. Show that $\mathbf I^2=-1$.
