---
title: "Lecture 6 — The Howie–Whelan Equations, Pendellösung, and the Road to Multislice"
subtitle: "Scattering Theory for Electron Microscopy, Module 2"
---

# Learning objectives

By the end of this lecture you should be able to:

1. Derive the Howie–Whelan equations for the transmitted and diffracted beam amplitudes as they evolve with depth in a two-beam crystal.
2. Solve them for a perfect crystal and obtain the Pendellösung (thickness-fringe) oscillation, and relate its period to the dispersion-surface branch separation from the previous lecture.
3. Explain how the same coupled equations generalize, beam by beam and slice by slice, into the multislice algorithm.
4. Connect multislice output to what is actually measured in CBED, 4D-STEM, and precession electron diffraction (PED).

---

# 1. From Bloch waves to a depth-propagation equation

Lecture 5 solved the two-beam problem as a static eigenvalue equation: for a chosen orientation, find the two allowed wavevectors $\mathbf K^{(1)}, \mathbf K^{(2)}$ on the dispersion surface, and the true wave inside the crystal is a fixed superposition of the two corresponding Bloch waves. That is complete and exact (within two beams), but it hides the question a microscopist actually asks: *given a beam that enters the top surface as pure transmitted amplitude, how do the transmitted and diffracted intensities evolve as you go deeper into the crystal?* Howie and Whelan's equations answer exactly this, by repackaging the same physics as an initial-value problem in depth $z$ rather than an eigenvalue problem in $\mathbf{K}$.

Write the wavefunction inside the crystal, restricted to the two beams that matter, as

$$
\psi(\mathbf r) = \phi_0(z)\, e^{i\mathbf{K}_0\cdot\mathbf r} + \phi_g(z)\, e^{i(\mathbf{K}_0+\mathbf{g})\cdot\mathbf r},
$$

where now $\phi_0(z)$ and $\phi_g(z)$ are allowed to vary slowly with depth $z$ (the direction into the specimen) — this is the same idea as Lecture 5's Bloch expansion, except we no longer demand a single fixed $\mathbf K$; instead the *amplitudes* of the two beams are left free to evolve, and the equation of motion for that evolution is what we derive. Substituting this ansatz into the Schrödinger equation, keeping only the two beams (exactly as in Lecture 5, Section 4), and dropping the second derivatives of the slowly-varying $\phi_0,\phi_g$ (they vary on the scale of the crystal thickness, not the electron wavelength — the same slowly-varying-envelope step used whenever you turn a wave equation into a beam-propagation equation) gives the **Howie–Whelan equations**:

$$
\boxed{\ \frac{d\phi_0}{dz} = \frac{i\pi}{\xi_g}\,\phi_g, \qquad \frac{d\phi_g}{dz} = \frac{i\pi}{\xi_g}\,\phi_0 + 2\pi i\, s_g\, \phi_g\ }
$$

with two physical constants doing all the work:

- $\xi_g = \pi k /|U_g|$ (up to convention-dependent constants), the **extinction distance** — the depth over which the transmitted and diffracted beams exchange amplitude, set directly by the structure factor coupling $U_g$ from Lectures 4–5. A strong reflection (large $F(hkl)$) has a *short* extinction distance: strong coupling exchanges amplitude quickly.
- $s_g$, the **excitation error** from Lecture 5 — how far the chosen orientation is from the exact Bragg condition. It appears here as a phase term precessing $\phi_g$ relative to $\phi_0$, and vanishes exactly at the Bragg condition.

Read the equations physically: the first says the transmitted beam loses amplitude to the diffracted beam at a rate set by $1/\xi_g$; the second says the diffracted beam gains from the transmitted beam at the same rate, but also accumulates a phase from being off exact Bragg orientation. This is literally "two coupled beams continuously scattering into each other as they propagate," which is exactly the multiple-scattering physics Lecture 5 identified as missing from Born — now written as a depth-evolution equation you can integrate.

---

# 2. Pendellösung: the exact solution for a perfect crystal

For a perfect crystal (uniform $\xi_g, s_g$ with depth) and the physical boundary condition that all the amplitude starts in the transmitted beam at the entrance surface, $\phi_0(0)=1,\ \phi_g(0)=0$, the coupled linear ODEs of Section 1 solve exactly (they are just a $2\times2$ constant-coefficient linear system — the same kind of problem as coupled pendulums or two-level quantum systems, and it is no accident that it looks like a two-level Rabi-oscillation problem: it is one). The diffracted beam intensity comes out as

$$
\boxed{\ I_g(z) = |\phi_g(z)|^2 = \frac{1}{1+(s_g\xi_g)^2}\, \sin^2\!\left(\pi z\sqrt{s_g^2 + 1/\xi_g^2}\right)\ }, \qquad I_0(z) = 1 - I_g(z).
$$

This is **Pendellösung** ("pendulum solution" — Ewald's original name for it): as the electron travels deeper into a perfect crystal, intensity does not simply build up in the diffracted beam and stay there; it sloshes periodically between transmitted and diffracted beams, exactly like energy sloshing between two coupled pendulums or population oscillating in a two-level Rabi problem. At the exact Bragg condition ($s_g=0$) the oscillation runs at its full contrast, period $\xi_g$, and reaches complete transfer ($I_g=1$) at $z=\xi_g/2$; away from Bragg, the oscillation both speeds up and loses contrast, exactly as $s_g\xi_g$ grows.

**This single formula is the quantitative answer to both symptoms flagged in Lecture 5, Section 1.** Thickness-dependent, oscillatory intensity is not a complication on top of the theory — it is the theory's central, exact prediction, and it shows up directly as **thickness fringes**: in a wedge-shaped specimen (thickness varying smoothly with position), $I_g(z)$ traces out a series of bright and dark bands running parallel to the wedge edge, each band corresponding to a thickness where $z\sqrt{s_g^2+1/\xi_g^2}$ passes through successive half-integers. Measuring the fringe spacing in a wedge is, in fact, one of the standard ways to measure $\xi_g$ — and therefore the structure factor $U_g$ — experimentally.

**Connecting back to the dispersion surface (Lecture 5):** the oscillation frequency $\sqrt{s_g^2+1/\xi_g^2}$ is exactly the separation between the two dispersion-surface branches at that excitation error. Two Bloch waves travelling together with slightly different $K^{(1)}, K^{(2)}$ beat against each other as they propagate — the beat period is the branch separation, and Pendellösung is nothing but that beat, made visible as oscillating diffracted intensity. Every piece of Section 1's physical picture ("two Bloch waves excited simultaneously, propagating with slightly different wavevectors") and this section's picture ("periodic exchange of amplitude with depth") are the same solution, described in two equivalent languages — eigenvalue/static versus initial-value/dynamic — exactly as normal modes and beat phenomena are two descriptions of the same coupled-oscillator physics anywhere else in physics.

---

# 3. Beyond two beams and beyond a perfect crystal: multislice

Howie–Whelan, as derived, assumes exactly two beams and a perfect, defect-free crystal. Real specimens have many strongly excited beams at once (particularly at higher voltage or in orientations chosen deliberately to activate many reflections, as in CBED — Section 4), have thickness-varying structure, bending, defects, and interfaces, and none of that fits a clean $2\times2$ analytic solution. The fix is to stop trying to solve the coupled-beam equations analytically at all, and instead do numerically, slice by slice, exactly what Howie–Whelan does analytically for two beams:

1. **Slice the specimen** into thin layers along $z$, each thin enough that within one slice the potential can be treated as if concentrated onto a single plane (a "phase grating").
2. **Transmission through one slice**: within a slice, the electron wave simply acquires a phase shift set by the projected potential of that slice — exactly the driven-Helmholtz picture from Lecture 1, applied over an infinitesimally thin source region, multiplying the wavefunction by a transmission function $t(\mathbf{r}_\perp) = e^{i\sigma V_{\text{proj}}(\mathbf{r}_\perp)}$.
3. **Propagation between slices**: in the (locally) vacuum gap between one slice and the next, the wave just propagates freely — precisely the free-space Green's-function propagation of Lecture 2, implemented efficiently via a Fourier-transform (Fresnel propagator) rather than a real-space convolution integral.
4. **Repeat**: transmit, propagate, transmit, propagate, once per slice, all the way through the specimen thickness.

Every step here is a direct reappearance of something already derived in this module: slice transmission is the driven-Helmholtz source term from Lecture 1 (now spatially thin rather than a smooth 3D potential); propagation between slices is exactly the Green's-function convolution from Lecture 2; and the whole procedure, run with enough slices and a fine enough real-space/reciprocal-space sampling, is mathematically equivalent to solving *all* of the infinite coupled-beam equations from Lecture 5 simultaneously, to all orders of multiple scattering — Howie–Whelan's two-beam analytic solution is the special case of multislice where only $\phi_0$ and $\phi_g$ are kept and the crystal is perfect. Nothing new is being postulated; the whole module has been building toward exactly this numerical procedure being *derivable*, not just plausible.

---

# 4. What actually gets measured: CBED, 4D-STEM, and PED

Multislice does not just reproduce Howie–Whelan in the two-beam limit — it is what makes several standard modern TEM techniques interpretable at all, because each of them depends on many-beam, non-perfect-crystal physics that two-beam theory cannot capture:

- **Convergent-beam electron diffraction (CBED)** deliberately illuminates the specimen with a convergent cone of angles rather than a single plane wave, so each diffraction "spot" becomes a disc, and — crucially — many reflections are excited simultaneously across the range of angles in the cone. The fine intensity structure *within* each disc directly encodes multi-beam dynamical diffraction (thickness, symmetry, even absolute structure), which is exactly why CBED patterns are simulated with multislice (or full Bloch-wave many-beam calculations) rather than read off a kinematical $|F(hkl)|^2$ table.
- **4D-STEM** scans a focused probe across the specimen and records a full diffraction pattern (effectively a small CBED pattern) at every probe position, building a 4D dataset (2D real-space position $\times$ 2D reciprocal-space pattern). Simulating what such a probe produces at each position — a converged, many-beam, dynamically-diffracting calculation for a beam only nanometres wide — is a direct, natural application of slice-by-slice multislice propagation of a localized probe wavefunction.
- **Precession electron diffraction (PED)** rocks (precesses) the incident beam around the optic axis during acquisition, integrating the pattern over many slightly different orientations. This averages over many different excitation errors $s_g$ for each reflection, which — looking back at Section 2's Pendellösung formula — is precisely a way to average out the strong, orientation-sensitive dynamical oscillation and recover intensities that behave *more* like the simple kinematical $|F(hkl)|^2$ from Lecture 4. PED is, in this module's language, an experimental trick for pushing a dynamical measurement back toward the Born-approximation regime that Lecture 5 explained was otherwise invalid at practical thicknesses.

Each of these techniques, in other words, is best understood as choosing a specific way of exciting and sampling the same coupled-beam physics developed across this module — never a different physical theory, just a different experimental slice through the same dispersion-surface/multislice framework.

---

# Recitation / self-check questions

1. Starting from the Howie–Whelan equations, verify by direct substitution that $I_0(z)+I_g(z)=1$ for all $z$ (probability/current conservation between the two beams) using the exact solution in Section 2.
2. At the exact Bragg condition ($s_g=0$), the diffracted intensity reaches $I_g=1$ at $z=\xi_g/2$ and returns to $I_g=0$ at $z=\xi_g$. Sketch $I_g(z)$ and $I_0(z)$ over $0\le z\le 2\xi_g$, and mark where a wedge-shaped specimen would show its first two bright thickness fringes.
3. In multislice, the transmission step uses the *projected* potential of a slice, $V_{\text{proj}}(\mathbf r_\perp) = \int_{\text{slice}} V(\mathbf r_\perp,z)\,dz$ — i.e. it throws away information about exactly where within the thin slice each atom sits along $z$. Under what condition on the slice thickness (relative to the atomic spacing along the beam direction) is this a good approximation, and what would you expect to go wrong if slices were made much thicker than that?
4. Explain, using the extinction-distance formula $\xi_g = \pi k/|U_g|$ and Lecture 4's statement that $U_g$ is built from atomic scattering factors, why a strongly diffracting reflection from a heavy-atom structure produces *thinner*, more closely spaced thickness fringes than a weak reflection from a light-atom structure at the same specimen thickness.
