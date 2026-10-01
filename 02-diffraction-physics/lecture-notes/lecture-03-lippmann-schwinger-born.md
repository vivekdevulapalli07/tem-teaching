---
title: "Lecture 3 — The Lippmann–Schwinger Equation, the Born Approximation, and Scattering as a Fourier Transform"
subtitle: "Scattering Theory for Electron Microscopy, Module 1"
---

# Learning objectives

By the end of this lecture you should be able to:

1. Combine the Schrödinger-as-driven-Helmholtz result (Lecture 1) with the Green's-function superposition result (Lecture 2) to write down the Lippmann–Schwinger equation, and explain why it is an *implicit* equation rather than a closed-form solution.
2. Apply the Born approximation and explain, physically, what assumption it makes and when that assumption is reasonable.
3. Take the far-field limit of the scattered wave and show that the scattering amplitude is the Fourier transform of the potential, evaluated at the momentum transfer $\mathbf{q}$.
4. Explain why this result is the reason electron diffraction patterns can be interpreted directly in terms of reciprocal space.

---

# 1. Assembling the pieces: the Lippmann–Schwinger equation

Lecture 1 put the time-independent Schrödinger equation into driven-Helmholtz form:

$$
\nabla^2\psi(\mathbf{r}) + k^2\psi(\mathbf{r}) = \frac{2m}{\hbar^2}\,V(\mathbf{r})\,\psi(\mathbf{r}), \qquad k^2 = \frac{2mE}{\hbar^2}.
$$

Lecture 2 showed that *any* driven Helmholtz equation, $(\nabla^2+k^2)u = f$, has general solution $u = u_h + u_p$, with $u_h$ the freely incident wave and

$$
u_p(\mathbf{r}) = \int G(\mathbf{r},\mathbf{r}')\, f(\mathbf{r}')\, d\mathbf{r}', \qquad G(\mathbf{r},\mathbf{r}') = -\frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{4\pi|\mathbf{r}-\mathbf{r}'|}.
$$

Substitute $f(\mathbf{r}') = \frac{2m}{\hbar^2}V(\mathbf{r}')\psi(\mathbf{r}')$ and take the incident field to be a free electron plane wave, $\psi_0(\mathbf{r}) = e^{i\mathbf{k}_0\cdot\mathbf{r}}$ (beam direction $\mathbf{k}_0$, $|\mathbf{k}_0|=k$, before it has met the specimen). The result is the **Lippmann–Schwinger equation**:

$$
\boxed{\ \psi(\mathbf{r}) = e^{i\mathbf{k}_0\cdot\mathbf{r}} - \frac{m}{2\pi\hbar^2}\int \frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{|\mathbf{r}-\mathbf{r}'|}\, V(\mathbf{r}')\,\psi(\mathbf{r}')\, d\mathbf{r}'\ }.
$$

Look carefully at what kind of equation this is. It is not "$\psi(\mathbf{r})$ equals some explicit function" — the unknown $\psi$ appears *inside the integral on the right*, evaluated everywhere the potential is nonzero. This is the self-consistency issue flagged in Lecture 1: you can't evaluate the right-hand side until you already know $\psi$ throughout the specimen, which is the very thing you're solving for. Equations of this shape — unknown function appearing under an integral sign — are called **integral equations**, and Lippmann–Schwinger is the integral-equation form of the Schrödinger equation, exact and fully equivalent to it, with the boundary condition (incident plane wave far away, outgoing scattered wave) already built in rather than imposed separately.

**Why bother, if it's implicit?** Because unlike the differential form, this equation is naturally solved by *iteration*, and the first iterate — using only quantities you already know — is exactly the Born approximation, Section 2.

---

# 2. The Born approximation: scattering is weak

Iterating means: start from a guess for $\psi(\mathbf{r}')$ under the integral, use it to compute a better $\psi(\mathbf{r})$, feed that back in, and repeat. The zeroth guess is the only thing you know for certain before any scattering has happened: the incident wave itself never got attenuated or redirected,

$$
\psi(\mathbf{r}') \approx \psi_0(\mathbf{r}') = e^{i\mathbf{k}_0\cdot\mathbf{r}'}.
$$

Substituting this single guess into the right-hand side of Lippmann–Schwinger — and then stopping, rather than iterating further — is the **first Born approximation**:

$$
\psi_{\text{Born}}(\mathbf{r}) = e^{i\mathbf{k}_0\cdot\mathbf{r}} - \frac{m}{2\pi\hbar^2}\int \frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{|\mathbf{r}-\mathbf{r}'|}\, V(\mathbf{r}')\, e^{i\mathbf{k}_0\cdot\mathbf{r}'}\, d\mathbf{r}'.
$$

**Physical content of this approximation:** it assumes each electron scatters, at most, *once* before leaving the specimen — the wave that reaches a given point of the potential is (to good approximation) still just the original incident beam, undiminished. This is reasonable when the potential is weak and/or the specimen is thin, so that the amplitude scattered out of the direct beam is a small correction rather than a substantial redirection of the wave. It is exactly the same approximation, applied to the same equation, that gives Rutherford scattering in nuclear physics and the kinematical theory of X-ray diffraction. It will fail — and we will see exactly how and why — once specimens get thick enough that an electron can scatter more than once; that breakdown is what dynamical diffraction theory exists to fix.

Everything for the rest of *this* lecture assumes the Born approximation holds.

---

# 3. The far field: distances collapse to a direction

A detector (or your eye, or a diffraction pattern on a screen) sits at $\mathbf{r}$ far outside the specimen, at a distance $r=|\mathbf{r}|$ enormously larger than the size of the region where $V(\mathbf{r}')$ is nonzero. This lets us simplify $|\mathbf{r}-\mathbf{r}'|$, which appears twice: once inside the phase $e^{ik|\mathbf{r}-\mathbf{r}'|}$, and once in the $1/|\mathbf{r}-\mathbf{r}'|$ prefactor.

**The prefactor** can simply be replaced by $1/r$: since $r' \ll r$, the fractional correction to $1/|\mathbf{r}-\mathbf{r}'|$ is negligible.

**The phase cannot be treated so casually.** Even a small correction to $|\mathbf{r}-\mathbf{r}'|$ gets multiplied by the large number $k$, and $k\times(\text{small correction})$ need not be small. So keep the leading correction: writing $\hat{\mathbf{r}} = \mathbf{r}/r$ for the unit vector toward the detector,

$$
|\mathbf{r}-\mathbf{r}'| = \sqrt{r^2 - 2\mathbf{r}\cdot\mathbf{r}' + r'^2} \approx r - \hat{\mathbf{r}}\cdot\mathbf{r}' \qquad (r'\ll r).
$$

Geometrically: from far away, all the little path-length differences from different points $\mathbf{r}'$ in the source collapse to a single number, the projection of $\mathbf{r}'$ onto the line of sight $\hat{\mathbf{r}}$ — exactly the geometry behind Fraunhofer diffraction in any optics course, now derived for the *same reason* it always is: distant observation turns spherical wavefronts locally into plane wavefronts.

With this, the outgoing spherical wave factorises:

$$
e^{ik|\mathbf{r}-\mathbf{r}'|} \approx e^{ikr}\, e^{-ik\hat{\mathbf{r}}\cdot\mathbf{r}'}.
$$

Substituting both simplifications into $\psi_{\text{Born}}$:

$$
\psi_{\text{Born}}(\mathbf{r}) \;\longrightarrow\; e^{i\mathbf{k}_0\cdot\mathbf{r}} + \frac{e^{ikr}}{r}\, f(\hat{\mathbf{r}}), \qquad
f(\hat{\mathbf{r}}) = -\frac{m}{2\pi\hbar^2}\int V(\mathbf{r}')\, e^{-ik\hat{\mathbf{r}}\cdot\mathbf{r}'}\, e^{i\mathbf{k}_0\cdot\mathbf{r}'}\, d\mathbf{r}'.
$$

The scattered wave, far away, is an outgoing spherical wave $e^{ikr}/r$ (exactly the Green's function's radial dependence — no surprise, since that's where it came from) modulated by an amplitude $f(\hat{\mathbf{r}})$ that depends only on *direction*, not on distance. $f(\hat{\mathbf{r}})$ is the **scattering amplitude**, and everything a detector measures — the diffraction pattern, the intensity as a function of angle — is built from it.

---

# 4. The scattering amplitude is a Fourier transform of the potential

Collect the exponentials in $f(\hat{\mathbf{r}})$:

$$
e^{-ik\hat{\mathbf{r}}\cdot\mathbf{r}'}\, e^{i\mathbf{k}_0\cdot\mathbf{r}'} = e^{i(\mathbf{k}_0 - k\hat{\mathbf{r}})\cdot\mathbf{r}'}.
$$

Define the **momentum transfer** (more precisely, $\hbar\mathbf{q}$ is the momentum transferred to the electron by the scattering event):

$$
\mathbf{q} \equiv k\hat{\mathbf{r}} - \mathbf{k}_0.
$$

($|\hat{\mathbf{r}}|=1$ and elastic scattering — Born approximation conserves energy — mean the outgoing wavevector $k\hat{\mathbf{r}}$ has the same magnitude $k$ as $\mathbf{k}_0$; only its *direction* changes.) Then

$$
\boxed{\ f(\mathbf{q}) = -\frac{m}{2\pi\hbar^2}\int V(\mathbf{r}')\, e^{-i\mathbf{q}\cdot\mathbf{r}'}\, d\mathbf{r}' = -\frac{m}{2\pi\hbar^2}\,\tilde{V}(\mathbf{q})\ }
$$

where $\tilde{V}(\mathbf{q})$ is exactly the ordinary 3D Fourier transform of the potential. This is the central result of the lecture, and worth stating in words on its own: **within the Born approximation, the amplitude scattered into direction $\hat{\mathbf{r}}$ is (up to constants) the Fourier component of the specimen's potential at wavevector $\mathbf{q} = k\hat{\mathbf{r}} - \mathbf{k}_0$.** Scanning the detector over all directions $\hat{\mathbf{r}}$ is the same thing as scanning $\mathbf{q}$ over the accessible region of Fourier space, and reading off $|f(\mathbf{q})|^2$ as intensity is — directly — reading off $|\tilde V(\mathbf{q})|^2$.

This is *why* diffraction patterns are said to live in "reciprocal space": it is not a metaphor or an approximation on top of the physics, it is the literal, derived statement that the scattering amplitude and the potential are Fourier conjugates of each other. Everything about interpreting a diffraction pattern — spot positions encoding periodicities, the reciprocal lattice, systematic absences from specific arrangements of atoms — is what happens when you evaluate this one Fourier transform for a periodic $V(\mathbf{r}')$, which is exactly where we're headed.

---

# 5. Recitation / self-check questions

1. Show that $|\mathbf{q}|$ depends only on $k$ and the scattering angle $\theta$ (the angle between $\hat{\mathbf{r}}$ and $\mathbf{k}_0$), via $|\mathbf{q}| = 2k\sin(\theta/2)$. (Hint: use $|k\hat{\mathbf{r}}|=|\mathbf{k}_0|=k$ and the law of cosines.) What does this tell you about the maximum $|\mathbf{q}|$ reachable at a fixed beam energy?
2. For a spherically symmetric potential $V(r')$, show the 3D Fourier transform reduces to a 1D integral, $\tilde V(q) = \dfrac{4\pi}{q}\displaystyle\int_0^\infty r'\,V(r')\sin(qr')\,dr'$. (This is the standard trick: do the angular integral first using $\hat{\mathbf{q}}$ as the polar axis.)
3. Explain, without new calculation, why the Born approximation and the far-field approximation are logically independent steps — i.e. why you could in principle keep multiple-scattering (beyond Born) while still being in the far field, or stay within Born while still being close enough to the specimen that the far-field simplification of Section 3 fails. Which of the two approximations is responsible for turning the scattering amplitude into *exactly* a Fourier transform, versus something else?
4. The Born approximation assumed $\psi(\mathbf{r}')\approx\psi_0(\mathbf{r}')$ under the integral. Sketch (in words, or by writing the next term explicitly) what the *second* Born approximation would look like if you substituted $\psi_{\text{Born}}(\mathbf{r}')$ back into the right-hand side of Lippmann–Schwinger instead of stopping. What does each successive term in this series represent physically, in terms of number of scattering events?
