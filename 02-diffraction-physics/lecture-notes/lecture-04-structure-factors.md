---
title: "Lecture 4 — Structure Factors, Atomic Scattering Factors, and Systematic Absences"
subtitle: "Scattering Theory for Electron Microscopy, Module 1"
---

# Learning objectives

By the end of this lecture you should be able to:

1. Use the convolution theorem to split the Fourier transform of a crystal's potential into a lattice sum (which forces diffraction onto discrete reciprocal-lattice points) and a structure factor (which sets each point's intensity).
2. Define the reciprocal lattice properly, and state the von Laue / Bragg condition in terms of it.
3. Write the structure factor $F(hkl)$ as a sum over atoms in the unit cell, each weighted by an atomic scattering factor.
4. Derive systematic absences for a given crystal structure directly from $F(hkl)$, and predict which reflections vanish.

---

# 1. From "a potential" to "a crystal": periodicity forces the Fourier transform to concentrate

Lecture 3 showed the scattering amplitude is the Fourier transform of the specimen's potential, $f(\mathbf{q}) \propto \tilde V(\mathbf{q})$, evaluated at momentum transfer $\mathbf{q}$. That result holds for *any* $V(\mathbf{r})$ — a single atom, an amorphous blob, anything. A crystal is the special case where $V(\mathbf{r})$ is periodic: built from one repeating unit, translated over and over,

$$
V(\mathbf{r}) = \sum_{\mathbf{R}_n} V_{\text{cell}}(\mathbf{r} - \mathbf{R}_n),
$$

where $\mathbf{R}_n = n_1\mathbf{a}_1 + n_2\mathbf{a}_2 + n_3\mathbf{a}_3$ runs over every lattice translation ($n_1,n_2,n_3$ integers, $\mathbf{a}_1,\mathbf{a}_2,\mathbf{a}_3$ the unit cell vectors), and $V_{\text{cell}}(\mathbf{r})$ is the potential of *one* unit cell's worth of atoms, repeated at every $\mathbf{R}_n$.

This sum is a **convolution**: $V(\mathbf{r}) = \big[\text{lattice of points } \delta(\mathbf{r}-\mathbf{R}_n)\big] * V_{\text{cell}}(\mathbf{r})$. The convolution theorem says a convolution in real space becomes a *product* in Fourier space:

$$
\tilde V(\mathbf{q}) = \underbrace{\left[\sum_{\mathbf{R}_n} e^{-i\mathbf{q}\cdot\mathbf{R}_n}\right]}_{\text{lattice sum } L(\mathbf{q})} \times \underbrace{\tilde V_{\text{cell}}(\mathbf{q})}_{\text{unit-cell transform}}.
$$

Everything interesting about *where* diffraction spots appear versus *how bright* each one is comes from separating these two factors, so treat them one at a time.

---

# 2. The lattice sum forces diffraction onto discrete points: the reciprocal lattice

$L(\mathbf{q}) = \sum_{\mathbf{R}_n} e^{-i\mathbf{q}\cdot\mathbf{R}_n}$ is exactly the Laue interference factor from Lecture 3's widget, generalized to three dimensions and an infinite (or very large) crystal. For a finite crystal of $N_1\times N_2\times N_3$ cells, $|L(\mathbf{q})|^2$ is a product of three factors like $\sin^2(N_i\pi x_i)/\sin^2(\pi x_i)$, each of which is essentially zero unless $x_i$ is an integer — and sharpens into a genuine Dirac comb as $N_i\to\infty$. So in the large-crystal limit,

$$
L(\mathbf{q}) \neq 0 \quad\text{only when}\quad \mathbf{q}\cdot\mathbf{a}_i = 2\pi\times(\text{integer}) \text{ for } i=1,2,3.
$$

The set of $\mathbf{q}$ satisfying all three conditions simultaneously is itself a lattice — the **reciprocal lattice** — spanned by vectors $\mathbf{b}_1,\mathbf{b}_2,\mathbf{b}_3$ defined by

$$
\mathbf{a}_i \cdot \mathbf{b}_j = 2\pi\,\delta_{ij}.
$$

(This is precisely the relation you used, without yet naming it, when you defined $\mathbf{b}_1,\mathbf{b}_2$ for the two-atom-basis widget in the last lecture — the same construction just extended to three dimensions.) Any reciprocal lattice vector is $\mathbf{G}_{hkl} = h\mathbf{b}_1+k\mathbf{b}_2+l\mathbf{b}_3$ with integers $h,k,l$ — the **Miller indices** — and the condition for a non-vanishing lattice sum is exactly

$$
\boxed{\ \mathbf{q} = \mathbf{G}_{hkl}\ } \qquad\text{(the von Laue condition).}
$$

Recall $\mathbf{q} = k\hat{\mathbf{r}} - \mathbf{k}_0$ was the momentum transfer between incident and scattered beams (Lecture 3, elastic so $|k\hat{\mathbf{r}}|=|\mathbf{k}_0|=k$). Setting $\mathbf{q}=\mathbf{G}_{hkl}$ and taking the magnitude of both sides recovers the familiar Bragg law $2d_{hkl}\sin\theta = \lambda$ — von Laue's condition is the same physical statement, just written as a vector equation rather than a scalar one, and it is the form that generalizes cleanly to any crystal symmetry.

**Physical picture:** the lattice sum is what turns "a diffuse Fourier transform of one blob" into "sharp spots" — it is a purely geometric statement about *where* the atoms are repeated, and knows nothing about what those atoms are. It answers *only* "which $\mathbf{q}$ are allowed by periodicity." Whether a given allowed spot is bright, weak, or completely dark is the job of the second factor.

---

# 3. The structure factor: what's actually inside the unit cell

At an allowed reciprocal lattice point $\mathbf{q}=\mathbf{G}_{hkl}$, the diffracted amplitude is proportional to $\tilde V_{\text{cell}}(\mathbf{G}_{hkl})$ — the Fourier transform of one unit cell's potential, evaluated exactly there. If the unit cell contains atoms at positions $\mathbf{r}_j = u_j\mathbf{a}_1+v_j\mathbf{a}_2+w_j\mathbf{a}_3$ (fractional coordinates $u_j,v_j,w_j$), and $V_{\text{cell}}(\mathbf{r}) = \sum_j V_j(\mathbf{r}-\mathbf{r}_j)$ (each atom's potential centred on its own site), the transform of a sum of shifted functions is a sum of phase-shifted transforms:

$$
\tilde V_{\text{cell}}(\mathbf{G}_{hkl}) = \sum_j \tilde V_j(\mathbf{G}_{hkl})\, e^{-i\mathbf{G}_{hkl}\cdot\mathbf{r}_j}.
$$

Using $\mathbf{G}_{hkl}\cdot\mathbf{r}_j = 2\pi(hu_j+kv_j+lw_j)$ (same identity as Lecture 3's widget: reciprocal vectors dotted into fractional real-space coordinates always collapse to $2\pi\times$integer combinations, independent of the unit cell's shape), this is the **structure factor**:

$$
\boxed{\ F(hkl) = \sum_j f_j(\mathbf{G}_{hkl})\; e^{-2\pi i (hu_j+kv_j+lw_j)}\ }
$$

where $f_j(\mathbf{G}_{hkl}) \equiv \tilde V_j(\mathbf{G}_{hkl})$ is the **atomic scattering factor** of atom $j$: the Fourier transform of a single isolated atom's potential, evaluated at that reciprocal lattice vector. Physically, $f_j(\mathbf{q})$ falls off with increasing $|\mathbf{q}|$ (larger scattering angle) because it is essentially the Fourier transform of the atom's electron-density-shaped potential — a smooth, extended charge distribution transforms into an amplitude that dies away at high spatial frequency, exactly as a blurrier real-space object has a narrower Fourier spectrum. Heavier atoms (more electrons, deeper potential) have larger $f_j$ at every $\mathbf{q}$, which is why heavy atoms dominate diffracted intensity — the same statement, again, as "a stronger source drives a stronger response" from Lecture 1.

$F(hkl)$ is exactly the quantity the widget computed as $S(h,k)$ for a two-dimensional basis with equal-strength atoms; here it is the general, three-dimensional statement with atom-and-angle-dependent scattering strengths $f_j(\mathbf{G}_{hkl})$ built in.

**Measured intensity** at each allowed spot is $I(hkl) \propto |F(hkl)|^2$ — this is the single formula a diffraction experiment actually measures, and everything about interpreting a pattern is either "which $(hkl)$ are geometrically allowed" (Section 2) or "how bright is this particular one" (this section).

---

# 4. Systematic absences: when $F(hkl)=0$ for a whole family of reflections

A reflection is *geometrically* allowed (it sits on the reciprocal lattice) but can still be **systematically absent** if the atoms inside the unit cell happen to interfere destructively for that entire class of $(hkl)$ — exactly what you saw directly in the widget's "two identical atoms" preset. Work it out for a concrete, important case: a **body-centred** structure, with atoms at $(0,0,0)$ and $(\tfrac12,\tfrac12,\tfrac12)$ (same atom, same $f$, so the same physics as the widget's checkerboard basis, now in 3D):

$$
F(hkl) = f\Big[1 + e^{-2\pi i(h/2+k/2+l/2)}\Big] = f\Big[1 + e^{-i\pi(h+k+l)}\Big] = f\big[1+(-1)^{h+k+l}\big].
$$

$$
F(hkl) = \begin{cases} 2f & h+k+l \text{ even} \\ 0 & h+k+l \text{ odd} \end{cases}.
$$

Every reflection with $h+k+l$ odd is exactly, completely dark — not weak, not hard to see, *zero* — regardless of how strongly the atom itself scatters. This is precisely the widget's rule, generalized from "$h+k$ odd in 2D" to "$h+k+l$ odd in 3D," and it is why real diffraction patterns from BCC metals (iron, tungsten, ...) show a very specific, recognisable subset of spots and not others: you are looking at destructive interference, derived from first principles, not an empirical rule to memorize.

The same method — write $F(hkl)$, substitute the actual atomic positions of the structure, and see what factors out — derives the absence rules for every centring type (face-centred: all of $h,k,l$ must be the same parity; and for structures with *different* atoms at the centring-related sites, as in the widget's "two different atoms" preset, the reflection is weak rather than exactly absent). There is nothing else to memorize: every "selection rule" you'll meet in a textbook is this one calculation, run once per structure.

---

# 5. Where this leaves us

We now have a complete kinematical (single-scattering, Born-approximation) theory of diffraction: geometry (the lattice sum) says which reciprocal lattice points are reachable at all, and the structure factor says how bright each one is, including when it is forced to exactly zero. This is genuinely the working theory behind indexing a diffraction pattern and identifying a crystal structure from it. What it cannot yet explain is *why* real diffraction patterns from reasonably thick specimens show effects — intensities that depend on specimen thickness, "forbidden" spots that show up faintly anyway from double diffraction, rings and lines that shift with orientation — that no amount of refining $F(hkl)$ will produce, because they come from the Born approximation itself breaking down once an electron scatters more than once on its way through the specimen.

---

# Recitation / self-check questions

1. Derive the structure factor and absence rule for a **face-centred** cubic structure: one atom at each of $(0,0,0)$, $(\tfrac12,\tfrac12,0)$, $(\tfrac12,0,\tfrac12)$, $(0,\tfrac12,\tfrac12)$, all the same species. Show $F(hkl)=4f$ when $h,k,l$ are all even or all odd, and $F(hkl)=0$ otherwise.
2. NaCl has Na$^+$ and Cl$^-$ ions on two interpenetrating FCC lattices (Cl at the FCC positions above, Na at the same positions shifted by $(\tfrac12,0,0)$). Write $F(hkl)$ in terms of $f_{\text{Na}}$ and $f_{\text{Cl}}$, and show that reflections with mixed parity (some indices even, some odd) are absent, while reflections with all-even or all-odd indices split into two intensity classes depending on the *sign* of $f_{\text{Na}}\pm f_{\text{Cl}}$. Which class would you expect to be weaker, and why does it not vanish exactly (contrast with the pure-FCC case in Q1)?
3. In the widget from last lecture, the "two different atoms" preset made the $h+k$-odd spots weak but not zero. Using the atomic-scattering-factor language of Section 3, explain precisely what would have to be true of $f_1(\mathbf q)$ and $f_2(\mathbf q)$ for those spots to vanish exactly at *some* scattering angles but not others — is this physically achievable for two different elements?
4. The atomic scattering factor $f_j(\mathbf{q})$ was described as falling off with $|\mathbf q|$ because it is the transform of a smooth, extended charge distribution. Sketch (words are fine) what you'd expect $f_j(\mathbf q)$ to look like in the limit $\mathbf q\to 0$, and connect this to the total number of electrons in the atom. (Hint: what is $\tilde V_j(0) = \int V_j(\mathbf r)\,d\mathbf r$ physically?)
