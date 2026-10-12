---
title: "2. Foundations of Geometric Algebra"
description: "A systematic introduction to the geometric product, grades, blades, multivectors, and the basic operations used later in mechanics."
---

Chapter 1 introduced an oriented area as a geometric quantity in its own right. We now build the algebra that lets us calculate with areas, vectors, and numbers together. The presentation begins with definitions, but each definition is followed by a calculation in the plane. We will then see how the same rules extend to three-dimensional space.

Throughout the mechanics chapters, space is ordinary three-dimensional Euclidean space unless we say otherwise. Starting in two dimensions will make the algebra easier to see without changing its essential rules.

## 2.1 Vector spaces and the metric

A **real vector space** is a collection of vectors that can be added and multiplied by real numbers. The resulting objects obey the familiar rules of vector arithmetic. In a plane, for example, if $\mathbf e_1$ and $\mathbf e_2$ are perpendicular unit directions, every vector has a decomposition

$$
\mathbf a=a_1\mathbf e_1+a_2\mathbf e_2.
$$

The coefficients $a_1$ and $a_2$ depend on the chosen directions; the vector does not. A basis is a set of independent vectors that lets us specify every vector this way.

To describe lengths and angles, we equip the vector space with a **metric**. In Euclidean mechanics this metric is the inner product, a symmetric bilinear operation on vectors with

$$
\mathbf a\cdot\mathbf b=\mathbf b\cdot\mathbf a,
\qquad
\mathbf a\cdot\mathbf a>0\quad\text{for }\mathbf a\ne 0.
$$

Bilinearity means the product distributes over vector addition and real factors can be taken outside. The length of a vector is $|\mathbf a|=\sqrt{\mathbf a\cdot\mathbf a}$, and the angle $\theta$ between nonzero vectors satisfies

$$
\mathbf a\cdot\mathbf b=|\mathbf a|\,|\mathbf b|\cos\theta.
$$

For an orthonormal basis, the basis vectors satisfy

$$
\mathbf e_i\cdot\mathbf e_j=\delta_{ij},
$$

where $\delta_{ij}$ equals one when $i=j$ and zero otherwise. Thus, in the plane,

$$
\mathbf a\cdot\mathbf b=a_1b_1+a_2b_2.
$$

The dot product is the part of vector multiplication that measures alignment. The metric supplies this information to geometric algebra.

## 2.2 The outer product and oriented geometry

The **outer product** of vectors, written $\mathbf a\wedge\mathbf b$, is bilinear and antisymmetric:

$$
\mathbf a\wedge\mathbf b=-\mathbf b\wedge\mathbf a,
\qquad
\mathbf a\wedge\mathbf a=0.
$$

Geometrically, it represents the oriented parallelogram spanned by the two vectors. Its magnitude is the parallelogram’s area; exchanging the vectors reverses its orientation. Parallel vectors span no area, so their outer product vanishes.

For an orthonormal basis in the plane, define the unit oriented area

$$
\mathbf I=\mathbf e_1\wedge\mathbf e_2.
$$

Then

$$
\mathbf a\wedge\mathbf b=(a_1b_2-a_2b_1)\mathbf I.
$$

For the example from Chapter 1, $\mathbf a=2\mathbf e_1+\mathbf e_2$ and $\mathbf b=\mathbf e_1+3\mathbf e_2$, we get

$$
\mathbf a\wedge\mathbf b=(2\cdot3-1\cdot1)\mathbf I=5\mathbf I.
$$

The signed number gives the oriented area in the chosen basis; the factor $\mathbf I$ identifies the geometric plane element itself.

## 2.3 Grades, blades, and multivectors

Geometric algebra keeps track of different kinds of geometric quantities by their **grade**. A scalar has grade zero, a vector has grade one, an oriented plane element has grade two, and an oriented volume element has grade three.

A **blade** is a simple oriented element formed as the outer product of vectors. One vector is a grade-one blade. The product $\mathbf a\wedge\mathbf b$ is a grade-two blade. Three vectors can form a grade-three blade $\mathbf a\wedge\mathbf b\wedge\mathbf c$.

A **$k$-vector** is a sum of terms of grade $k$. A **multivector** is a sum of terms of different grades. In a two-dimensional Euclidean space, a general multivector has the form

$$
M=\alpha+a_1\mathbf e_1+a_2\mathbf e_2+\beta\mathbf I,
$$

where $\alpha$ and $\beta$ are real numbers. Its four independent basis elements are $1$, $\mathbf e_1$, $\mathbf e_2$, and $\mathbf I$. A vector is one part of a multivector; a scalar plus a vector plus a bivector is a multivector with three grades present.

We can select the grade-$k$ part of a multivector $M$ using the notation $\langle M\rangle_k$. For instance, $\langle M\rangle_0$ is its scalar part and $\langle M\rangle_2$ is its bivector part. This notation will let us refer precisely to components of products.

| Grade | Name | Example in Euclidean space |
|---|---|---|
| 0 | Scalar | $\alpha$ |
| 1 | Vector | $a_1\mathbf e_1+a_2\mathbf e_2$ |
| 2 | Bivector | $\beta\mathbf I$ in the plane |
| 3 | Trivector | An oriented volume element in three dimensions |

In $n$ dimensions, the basis blades span grades from zero through $n$. Their total number is $2^n$: each basis blade corresponds to a choice of which basis vectors take part in it. This gives four basis elements in the plane and eight in three dimensions.

## 2.4 The geometric product

The **geometric product** of two vectors is defined by combining the metric and the outer product:

$$
\mathbf a\mathbf b=\mathbf a\cdot\mathbf b+\mathbf a\wedge\mathbf b.
$$

The result is a multivector with a scalar part and a bivector part. The two parts have different grades, so they remain distinct. The geometric product is extended to sums by distributivity and to products of more vectors by associativity.

Because the inner product is symmetric and the outer product is antisymmetric, reversing the order gives

$$
\mathbf b\mathbf a=\mathbf a\cdot\mathbf b-\mathbf a\wedge\mathbf b.
$$

Adding and subtracting these equations recovers the two pieces:

$$
\mathbf a\cdot\mathbf b=\frac{1}{2}(\mathbf a\mathbf b+\mathbf b\mathbf a),
\qquad
\mathbf a\wedge\mathbf b=\frac{1}{2}(\mathbf a\mathbf b-\mathbf b\mathbf a).
$$

Equivalently, the defining relation for vectors is

$$
\mathbf a\mathbf b+\mathbf b\mathbf a=2\,\mathbf a\cdot\mathbf b.
$$

For a vector multiplied by itself, the outer product vanishes. Therefore

$$
\mathbf a^2=\mathbf a\cdot\mathbf a=|\mathbf a|^2.
$$

The square of a vector is a nonnegative scalar in Euclidean space.

## 2.5 Calculating with a planar basis

Let $\mathbf e_1$ and $\mathbf e_2$ be perpendicular unit vectors. Their geometric products follow from the defining relation:

$$
\mathbf e_1^2=\mathbf e_2^2=1,
\qquad
\mathbf e_1\mathbf e_2=-\mathbf e_2\mathbf e_1.
$$

Since the vectors are perpendicular, their inner product is zero, so their product is entirely the outer product:

$$
\mathbf e_1\mathbf e_2=\mathbf e_1\wedge\mathbf e_2=\mathbf I.
$$

Using $\mathbf I=\mathbf e_1\mathbf e_2$, we can calculate its square:

$$
\mathbf I^2
=\mathbf e_1\mathbf e_2\mathbf e_1\mathbf e_2
=-\mathbf e_1^2\mathbf e_2^2
=-1.
$$

Now multiply the vectors from the earlier example. Distributivity gives

$$
\begin{aligned}
\mathbf a\mathbf b
&=(2\mathbf e_1+\mathbf e_2)(\mathbf e_1+3\mathbf e_2)\\
&=2+6\mathbf e_1\mathbf e_2+\mathbf e_2\mathbf e_1+3\\
&=5+5\mathbf I.
\end{aligned}
$$

The scalar part is the inner product $\mathbf a\cdot\mathbf b=5$; the bivector part is the outer product $\mathbf a\wedge\mathbf b=5\mathbf I$. Reversing the vector order changes only the sign of the bivector part:

$$
\mathbf b\mathbf a=5-5\mathbf I.
$$

This calculation illustrates how the geometric product gathers two familiar answers into one object and lets us recover either answer by taking its grade.

## 2.6 Reversion and inverses

The **reverse** of a product reverses the order of its vector factors. We write the reverse of a multivector $M$ as $\widetilde M$. Scalars and vectors are unchanged, while a bivector changes sign:

$$
\widetilde{\alpha}=\alpha,
\qquad
\widetilde{\mathbf a}=\mathbf a,
\qquad
\widetilde{\mathbf I}=-\mathbf I.
$$

For a homogeneous grade-$k$ element, reversion has the sign

$$
\widetilde M=(-1)^{k(k-1)/2}M.
$$

For products, $\widetilde{MN}=\widetilde N\,\widetilde M$. Reversion will be useful when we study rotations and rotors.

An element $M$ has an **inverse** $M^{-1}$ if multiplication by it undoes multiplication by $M$, so $M^{-1}M=MM^{-1}=1$. Every nonzero Euclidean vector has an inverse. Since $\mathbf a^2=|\mathbf a|^2$,

$$
\mathbf a^{-1}=\frac{\mathbf a}{|\mathbf a|^2},
\qquad \mathbf a\ne0.
$$

Indeed, $\mathbf a\,\mathbf a^{-1}=\mathbf a^2/|\mathbf a|^2=1$. Not every multivector is invertible; whenever we use an inverse, its existence will be clear from the construction or stated explicitly.

## 2.7 From two dimensions to three

In three-dimensional Euclidean space, choose three mutually perpendicular unit vectors. The basis rules are

$$
\mathbf e_i^2=1,
\qquad
\mathbf e_i\mathbf e_j=-\mathbf e_j\mathbf e_i\quad(i\ne j).
$$

The basis blades are

$$
1;\quad
\mathbf e_1,\mathbf e_2,\mathbf e_3;\quad
\mathbf e_1\mathbf e_2,\mathbf e_2\mathbf e_3,\mathbf e_3\mathbf e_1;\quad
\mathbf I=\mathbf e_1\mathbf e_2\mathbf e_3.
$$

They represent scalars, vectors, bivectors, and trivectors, respectively. The trivector $\mathbf I$ is the **pseudoscalar** of the oriented three-dimensional space; it represents its unit oriented volume. In the plane, $\mathbf I=\mathbf e_1\mathbf e_2$ is the unit oriented area and is also that space’s pseudoscalar. In both cases $\mathbf I^2=-1$ for these Euclidean orthonormal bases.

In three dimensions the cross product is related to the outer product by a duality: with a right-handed orthonormal basis, $\mathbf a\times\mathbf b=(\mathbf a\wedge\mathbf b)\mathbf I^{-1}$. For example, $\mathbf e_1\wedge\mathbf e_2=\mathbf e_1\mathbf e_2$ corresponds to $\mathbf e_3$. The cross product is often convenient, especially in familiar calculations. The outer product emphasizes the oriented plane, while duality turns that plane into its perpendicular vector.

The dimension changes the list of grades and basis blades, but the geometric product still combines the metric information with the oriented information. That consistency is what makes the planar examples a reliable guide to three-dimensional mechanics.

## 2.8 What to remember

- The metric defines lengths and angles through the inner product.
- The outer product records oriented area or, in higher dimensions, oriented higher-grade geometry.
- The geometric product combines inner and outer products: $\mathbf a\mathbf b=\mathbf a\cdot\mathbf b+\mathbf a\wedge\mathbf b$.
- Grades identify the geometric type of each part; blades are simple elements, and multivectors can contain several grades.
- Reversion reverses product order, and nonzero Euclidean vectors have inverses.
- A pseudoscalar represents the oriented unit volume of a space; in three dimensions, duality connects bivectors with the familiar cross product.

### Exercises

1. For $\mathbf a=3\mathbf e_1-2\mathbf e_2$ and $\mathbf b=\mathbf e_1+4\mathbf e_2$, calculate $\mathbf a\cdot\mathbf b$, $\mathbf a\wedge\mathbf b$, and $\mathbf a\mathbf b$.
2. Starting from $\mathbf e_1\mathbf e_2=-\mathbf e_2\mathbf e_1$ and $\mathbf e_1^2=\mathbf e_2^2=1$, show that $(\mathbf e_1\mathbf e_2)^2=-1$.
3. Write the reverse of $M=2+3\mathbf e_1-\mathbf e_2+4\mathbf I$ in the plane.
4. Find the inverse of $\mathbf a=2\mathbf e_1+\mathbf e_2$ and verify by multiplication that $\mathbf a\mathbf a^{-1}=1$.
5. In three dimensions, list how many independent basis blades have grades zero, one, two, and three. What geometric objects do they represent?
6. Explain in words what the cross product’s perpendicular vector has to do with the oriented plane represented by the outer product.
