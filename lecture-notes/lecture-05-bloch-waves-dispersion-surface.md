---
title: "Lecture 5 — Beyond the Born Approximation: Bloch Waves and the Dispersion Surface"
subtitle: "Scattering Theory for Electron Microscopy, Module 2"
---

# Learning objectives

By the end of this lecture you should be able to:

1. Estimate when the Born approximation stops being trustworthy, in terms of specimen thickness and scattering strength.
2. Write the Bloch-wave ansatz for an electron in a periodic potential, and explain why periodicity guarantees this form is exact.
3. Derive the coupled-beam equations from the Schrödinger equation, and identify the coupling coefficients as the structure factors from the previous lecture.
4. Reduce the coupled equations to the two-beam case, and describe what a dispersion surface is and why it has two branches.

---

# 1. Quantifying when Born breaks down

The Born approximation (Lecture 3) assumed the wave hitting every point of the potential was still, essentially, the undisturbed incident beam — i.e. that the *scattered* amplitude is a small correction to the incident amplitude. Make that comparison explicit. The fractional amplitude scattered by traversing a thickness $t$ of crystal scales, from the Lippmann–Schwinger integral, roughly as

$$
\frac{\psi_{\text{scattered}}}{\psi_{\text{incident}}} \sim \frac{m}{2\pi\hbar^2 k}\, U_g\, t,
$$

where $U_g$ is the relevant Fourier component of the potential (a structure factor, in the units of Lecture 4) and $t$ is the path length through the specimen. Born is self-consistent only while this ratio stays $\ll 1$. For X-rays this holds almost always — the potential X-rays see is weak. For electrons in a solid, the electrostatic potential is not weak, and this ratio reaches order unity for perfectly ordinary TEM specimen thicknesses, often tens of nanometres. This is not a subtle correction: **for essentially every specimen thick enough to be practical to make, cut, or find, Born is not valid**, and diffracted intensities do not simply track $|F(hkl)|^2$ from a single scattering event.

Two experimental symptoms tell you Born has failed, both worth keeping in mind as motivation:

- **Intensities depend on thickness in an oscillatory way**, not just growing monotonically as "more crystal, more scattering." An electron can scatter from the transmitted beam into a diffracted beam, and then scatter *again* back into the transmitted beam — multiple scattering — and interference between these multiply-scattered paths is what produces oscillation with $t$.
- **Reflections that Section 4 of the last lecture proved are exactly, geometrically forbidden are sometimes weakly visible anyway** ("double diffraction": scattering twice, via two allowed reflections whose indices add up to the forbidden one, can populate it even though no single scattering event can).

Both symptoms point to the same fix: stop treating the specimen as a source that only gets to act once, and instead solve the wave equation *exactly* inside a periodic potential, to all orders of scattering at once.

---

# 2. Bloch's theorem: why periodicity fixes the form of the exact solution

We need $\psi(\mathbf{r})$ satisfying the *exact* Schrödinger equation inside the crystal potential $V(\mathbf{r})$, which — being built from a repeating unit cell — has the full translational symmetry of the lattice: $V(\mathbf{r}+\mathbf{R}_n) = V(\mathbf{r})$ for every lattice vector $\mathbf{R}_n$.

**Claim (Bloch's theorem): any solution of the Schrödinger equation in such a potential can be written as**

$$
\boxed{\ \psi(\mathbf{r}) = e^{i\mathbf{K}\cdot\mathbf{r}}\, u(\mathbf{r}), \qquad u(\mathbf{r}+\mathbf{R}_n) = u(\mathbf{r})\ }
$$

**for some wavevector $\mathbf{K}$** — a plane wave envelope modulating a function with exactly the periodicity of the lattice.

This is worth pausing on, because it is not an approximation — it follows from symmetry alone, the same way "energy eigenstates of a symmetric double well are either even or odd" follows from symmetry alone. Translating $\psi$ by a lattice vector $\mathbf{R}_n$ must map a solution to another solution of the *same* equation (since $V$ is unchanged by the translation), so translation by $\mathbf{R}_n$ acts on the space of solutions as some number $\lambda(\mathbf{R}_n)$ (a phase, for a physically sensible bounded wave: $|\lambda|=1$). Consistency of translating first by $\mathbf{R}_1$ then $\mathbf{R}_2$, versus directly by $\mathbf{R}_1+\mathbf{R}_2$, forces $\lambda(\mathbf{R}_n) = e^{i\mathbf{K}\cdot\mathbf{R}_n}$ for some fixed $\mathbf{K}$. Writing $\psi(\mathbf{r}) = e^{i\mathbf{K}\cdot\mathbf{r}}u(\mathbf{r})$ and demanding $\psi(\mathbf{r}+\mathbf{R}_n) = e^{i\mathbf{K}\cdot\mathbf{R}_n}\psi(\mathbf{r})$ is then exactly the statement that $u(\mathbf{r})$ is periodic. That's the whole proof — periodicity of $V$ is the only ingredient.

Because $u(\mathbf{r})$ has the lattice's periodicity, it has its own Fourier series using only reciprocal lattice vectors (Lecture 4, Section 2) as the allowed frequencies:

$$
u(\mathbf{r}) = \sum_{\mathbf{g}} C_{\mathbf{g}}\, e^{i\mathbf{g}\cdot\mathbf{r}}, \qquad \mathbf{g} \in \{\text{reciprocal lattice vectors}\}.
$$

So the exact wavefunction inside the crystal is a superposition of plane waves,

$$
\psi(\mathbf{r}) = \sum_{\mathbf{g}} C_{\mathbf{g}}\, e^{i(\mathbf{K}+\mathbf{g})\cdot\mathbf{r}},
$$

each with wavevector $\mathbf{K}+\mathbf{g}$ differing from the next by a reciprocal lattice vector. Physically: **the beam that enters as one plane wave splits, inside the crystal, into a discrete family of plane waves travelling in the directions of the transmitted beam and every allowed diffracted beam simultaneously**, and it is coherent superposition of *all* of them — not any one alone — that constitutes the exact solution.

---

# 3. The coupled-beam equations, and why structure factors are exactly the coupling

Substitute this Bloch expansion, plus the crystal potential written as its own Fourier series $V(\mathbf{r}) = \sum_{\mathbf{g}} U_{\mathbf{g}}\, e^{i\mathbf{g}\cdot\mathbf{r}}$ (each $U_{\mathbf{g}}$ is exactly a structure factor from Lecture 4, up to the same $2m/\hbar^2$ scaling used since Lecture 1), into the Schrödinger equation $\nabla^2\psi + \frac{2m}{\hbar^2}(E-V)\psi=0$. Each term in the double sum over $\mathbf{g}$ and $\mathbf{g}'$ produces a plane wave $e^{i(\mathbf{K}+\mathbf{g})\cdot\mathbf{r}}$; since plane waves of different wavevector are linearly independent, the coefficient of *each* $\mathbf{g}$ must vanish separately. That gives one algebraic equation per reciprocal lattice vector $\mathbf{g}$:

$$
\boxed{\ \Big[K_g^2 - |\mathbf{K}+\mathbf{g}|^2\Big]\, C_{\mathbf{g}} = -\sum_{\mathbf{g}'\neq \mathbf{g}} U_{\mathbf{g}-\mathbf{g}'}\, C_{\mathbf{g}'}\ }, \qquad K_g^2 \equiv \frac{2mE}{\hbar^2} + U_0.
$$

Read the structure of this equation rather than just its algebra: on the left, $C_{\mathbf{g}}$ multiplies how far the plane wave $\mathbf{K}+\mathbf{g}$ is from *automatically* satisfying the free-particle dispersion relation — i.e. how far that beam is from the Bragg condition of Lecture 4. On the right, every *other* beam $C_{\mathbf{g}'}$ feeds into $C_{\mathbf{g}}$, weighted by exactly the structure factor connecting them, $U_{\mathbf{g}-\mathbf{g}'}$. **This is multiple scattering, written explicitly**: beam $\mathbf{g}'$ feeds beam $\mathbf{g}$ at a rate set by the same $F(hkl)$-type quantity that, in the Born approximation, only ever got to act once. Here every beam feeds every other beam, indefinitely, to all orders — which is exactly the missing physics identified in Section 1. Note also that if a structure factor $U_{\mathbf{g}-\mathbf{g}'}$ is systematically absent (Lecture 4, Section 4), that particular direct coupling vanishes — but $\mathbf{g}$ can still be fed *indirectly*, via an intermediate beam $\mathbf{g}''$ with two nonzero couplings $U_{\mathbf{g}-\mathbf{g}''}$ and $U_{\mathbf{g}''-\mathbf{g}'}$. That is the double-diffraction symptom from Section 1, now visible directly in the equations rather than asserted.

There is one such equation for every reciprocal lattice vector — infinitely many, coupling infinitely many beams. Solving the full set is exactly what multislice simulation eventually does numerically. For a lecture, and for genuine physical insight, we truncate.

---

# 4. The two-beam approximation and the dispersion surface

Suppose the incident beam is oriented so that only *one* diffracted beam, $\mathbf{g}$, is close to satisfying the Bragg condition (every other reciprocal lattice point is far from the sphere/geometry that would activate it — an orientation you *choose*, by tilting the specimen). Then keep only two terms: the transmitted beam ($\mathbf{g}=0$) and this one strong diffracted beam. The infinite system in Section 3 collapses to two coupled equations in $C_0$ and $C_g$:

$$
(K^2 - |\mathbf{K}|^2)\,C_0 = -U_{-g}\,C_g, \qquad (K^2 - |\mathbf{K}+\mathbf{g}|^2)\,C_g = -U_{g}\,C_0.
$$

This is a $2\times2$ eigenvalue problem: for a chosen direction of the incident beam, it does not have one solution but **two**, $\mathbf{K}^{(1)}$ and $\mathbf{K}^{(2)}$ — two distinct, simultaneously valid ways for the crystal to support a self-consistent two-beam wave. Physically: the electron travelling through the crystal does not pick one; the actual state inside the crystal is a superposition of *both* Bloch waves, each propagating with its own slightly different wavevector, and it is the beating between these two slightly-mismatched waves that will turn out, in the next lecture, to be the origin of intensity oscillating with thickness.

Plot the allowed $\mathbf{K}$ as a function of the incident beam direction (equivalently, as a function of how far the incident beam is mistilted from the exact Bragg condition — the **excitation error**, $s_g$): instead of a single free-electron sphere $|\mathbf{K}|=\text{const}$, you get **two branches**, close together, that repel each other exactly where the free-electron spheres for the two beams would have crossed (at $s_g=0$, exact Bragg condition). This surface of allowed $\mathbf{K}(s_g)$ — really two sheets, one per branch — is the **dispersion surface**. Its defining feature is the *gap* between the two branches at $s_g=0$: instead of the two free-electron circles crossing, the coupling $U_g$ pushes them apart, by an amount set directly by $|U_g|$. No coupling ($U_g\to0$, Section 1's Born-approximation limit) collapses the two branches back onto the single free-electron sphere, with no gap — consistent with kinematical theory being the $U_g\to0$ limit of this exact treatment.

---

# 5. Where this leaves us

We now have an exact (within two beams) description of how an electron wave actually propagates through a periodic potential: two Bloch waves, with two distinct wavevectors set by the dispersion surface, both excited simultaneously and travelling together through the specimen. The separation between the two branches has units of inverse length, so it sets a natural length scale in the specimen — and the interference between two waves that travel together but accumulate a slightly different phase over a distance $t$ is precisely the mechanism that turns thickness into an oscillating diffracted intensity, which is the direct, quantitative form the two symptoms from Section 1 take once you follow the two Bloch waves all the way through a specimen of finite thickness.

---

# Recitation / self-check questions

1. Show that in the limit $U_g \to 0$, the two-beam eigenvalue problem of Section 4 reduces to $\mathbf{K}^{(1)} = \mathbf{K}_0$ (undeviated) and a second solution requiring $|\mathbf{K}+\mathbf{g}|=|\mathbf{K}_0|$ — i.e. exactly the von Laue/Bragg condition from Lecture 4, with no gap. This is the check that the dynamical theory correctly contains the kinematical theory as a limit.
2. The estimate in Section 1 for when Born fails involved $U_g\, t / k$. Using typical accelerating voltages (Lecture 1's relativistic wavelength notebook gives you $k$ at any voltage) and typical electron structure factors, would you expect a 2 nm specimen to be safely in the Born/kinematical regime? A 200 nm specimen? What does this imply about interpreting diffraction patterns from thick versus thin specimens differently?
3. Section 3 noted that a systematically absent reflection can still be weakly populated by double diffraction through an intermediate beam. Using the coupled-beam equation, write the explicit two-step condition (in terms of two nonzero $U$'s) under which a reflection with $U_{\mathbf g}=0$ nonetheless receives amplitude at second order. Does this require the *intermediate* beam to itself be strongly excited, or merely nonzero?
4. Explain, physically and without new equations, why choosing a specimen orientation with *three* strong beams (rather than two) would require the analysis of Section 4 to be redone as a $3\times3$ problem, and predict qualitatively how many branches the corresponding dispersion surface would then have.
