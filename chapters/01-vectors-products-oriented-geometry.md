---
title: "1. Vectors, Products, and Oriented Geometry"
description: "A gentle first look at the kinds of geometric quantities used in physics and the ideas behind geometric algebra."
---

Classical physics describes the world with quantities of different kinds. Some are numbers; others have a direction; still others describe geometric features such as an oriented area. These distinctions are already present in the mechanics you know. Geometric algebra gives us a way to work with them together.

## 1.1 Numbers and arrows in physics

A **scalar** is specified by a number, together with its unit when appropriate. Mass, energy, electric charge, and elapsed time are familiar examples. A scalar does not point in a spatial direction.

A **vector** has both magnitude and direction. Displacement, velocity, acceleration, and force are examples. A force of a given magnitude can act east or west; its direction changes the physical situation even when its magnitude does not.

These examples show why physics needs more than numbers alone. They also show that physical quantities do not all have the same mathematical character. Many laws relate scalars to scalars and vectors to vectors, while geometric algebra will let us describe additional geometric quantities in the same calculation.

## 1.2 An oriented area

Take two vectors in a plane and draw them from the same point. They span a parallelogram. The area tells us how far apart the directions are, but it does not tell us their order: turning from the first vector to the second is opposite to turning from the second to the first.

Let the plane have perpendicular unit directions $\mathbf e_1$ and $\mathbf e_2$. Write two vectors as

$$
\mathbf a=a_1\mathbf e_1+a_2\mathbf e_2,
\qquad
\mathbf b=b_1\mathbf e_1+b_2\mathbf e_2.
$$

The signed area of their parallelogram is

$$
A_{\mathrm{oriented}}=a_1b_2-a_2b_1.
$$

This is the two-dimensional coordinate form of the outer product; for a geometric-algebra treatment of the directed-area interpretation and this formula, see [Doran and Lasenby, *Geometric Algebra for Physicists*, §1.6.1](https://www.cambridge.org/core/books/geometric-algebra-for-physicists/FB8D3ACB76AB3AB10BA7F27505925091).

Its magnitude is the ordinary area. Its sign records orientation: exchanging $\mathbf a$ and $\mathbf b$ reverses the sign. For example, if $\mathbf a=2\mathbf e_1+\mathbf e_2$ and $\mathbf b=\mathbf e_1+3\mathbf e_2$, the signed area is $2\cdot3-1\cdot1=5$ in the chosen orientation.

An oriented area is not a scalar area, because it also remembers a direction of turning. It is not an ordinary vector either: it lies in the plane spanned by the two vectors. In geometric algebra, an oriented plane element of this kind is called a **bivector**. We will develop that idea from first principles in the next chapter.

## 1.3 Back to familiar mechanics

You already know how scalar and vector quantities work together in Newtonian mechanics. The net force and acceleration are vectors, while mass is a scalar:

$$
\mathbf F_{\mathrm{net}}=m\mathbf a,
\qquad
\mathbf a=\frac{d\mathbf v}{dt}.
$$

These equations are an excellent starting point. The goal of learning geometric algebra is not to replace familiar mechanics with unfamiliar notation. It is to give us a compact way to express geometric relationships that otherwise require several separate rules.

For instance, work depends on the component of a force along a displacement, while angular momentum is tied to the oriented plane spanned by position and momentum. The familiar dot product handles the first idea; in three dimensions the cross product is commonly used for the second. Geometric algebra will show how both fit into one product of vectors.

## 1.4 A preview of the geometric product

The dot product of two vectors is a scalar. It measures their alignment:

$$
\mathbf a\cdot\mathbf b=|\mathbf a|\,|\mathbf b|\cos\theta.
$$

The outer product, written $\mathbf a\wedge\mathbf b$, describes the oriented area spanned by the vectors. In the plane chosen above, it is the signed area multiplied by the unit oriented area of that plane.

The geometric product is defined for vectors in the metric vector space used to represent the geometry—the ambient or **embedding space**. For any two vectors in that space, it combines the scalar alignment and oriented-plane information:

$$
\mathbf a\mathbf b=\mathbf a\cdot\mathbf b+\mathbf a\wedge\mathbf b.
$$

This decomposition holds in any dimension, not just in the plane used for our examples. The result has a scalar part and a bivector part representing the oriented plane spanned by the vectors. A single product can therefore retain different kinds of geometric information without confusing them. Chapter 2 will define the product, explain its algebraic rules, and show how to calculate with it.

## 1.5 A glimpse beyond the plane

In three dimensions, two vectors still span an oriented plane. The usual cross product represents that plane by a vector perpendicular to it, using a chosen orientation of space. A bivector represents the plane itself. These descriptions carry equivalent information in ordinary three-dimensional Euclidean space, but they emphasize different geometry.

This distinction matters in mechanics. The angular momentum of a particle is associated with the plane of its position and momentum. The cross-product notation is often convenient; the bivector description makes the plane and its orientation explicit. We will compare the two when we reach angular momentum and rotations.

## 1.6 The route ahead

Chapter 2 develops geometric algebra step by step: vector spaces and their metric, inner and outer products, the geometric product, and the language of grades, blades, and multivectors. We start with a plane because its geometry is easy to draw, then extend the rules to three dimensions.

The rest of the book returns to familiar mechanics. We will use GA where it clarifies spatial geometry, especially angular momentum and rotations, and use ordinary scalar equations, coordinates, matrices, and calculus whenever they are more direct.

### Exercises

1. Give two examples of scalar quantities and two examples of vector quantities from mechanics or another area of physics. State the units and, for each vector, what its direction means.
2. Draw two vectors in a plane that span a parallelogram. Reverse their order and describe what changes and what stays the same.
3. For $\mathbf a=2\mathbf e_1+\mathbf e_2$ and $\mathbf b=\mathbf e_1+3\mathbf e_2$, calculate the signed area $a_1b_2-a_2b_1$. What is the signed area if the vectors are exchanged?
4. In your own words, explain why an oriented area is not simply an ordinary scalar area or an ordinary vector.
