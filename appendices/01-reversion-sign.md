---
title: "Appendix A. The sign of reversion"
description: "A short derivation of the reversion sign for a homogeneous multivector grade."
---

## A.1 Reversing a basis blade

Choose an orthonormal basis and write a grade-$k$ basis blade in increasing order:

$$
B=\mathbf e_{i_1}\mathbf e_{i_2}\cdots\mathbf e_{i_k},
\qquad i_1<i_2<\cdots<i_k.
$$

Reversion reverses the order of the vector factors:

$$
\widetilde B=\mathbf e_{i_k}\cdots\mathbf e_{i_2}\mathbf e_{i_1}.
$$

To put these factors back into increasing order, we must swap every pair once. There are

$$
\binom{k}{2}=\frac{k(k-1)}{2}
$$

such pairs. Distinct vectors in an orthonormal basis anticommute, so each swap contributes a factor of $-1$. Therefore

$$
\widetilde B=(-1)^{k(k-1)/2}B.
$$

Every grade-$k$ element is a linear combination of grade-$k$ basis blades. Reversion is linear, and each of those blades acquires the same sign, so for every homogeneous grade-$k$ element $M_k$,

$$
\widetilde M_k=(-1)^{k(k-1)/2}M_k.
$$

For example, the sign is positive for scalars and vectors, negative for bivectors and trivectors, and positive again for grade-four elements.
