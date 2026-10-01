---
title: "Lecture 1 — From the Wave Equation to a Driven Helmholtz Equation"
subtitle: "Scattering Theory for Electron Microscopy, Module 1"
---

# Learning objectives

By the end of this lecture you should be able to:

1. Derive the (homogeneous) Helmholtz equation from the classical wave equation by separating out time-harmonic dependence.
2. Explain the physical difference between the homogeneous and non-homogeneous Helmholtz equation, with at least two everyday examples of each.
3. Write the time-independent Schrödinger equation in Helmholtz form and identify the potential $V(\mathbf{r})$ as a *source term* that drives scattering of the electron wave — the idea the rest of the module is built on.

---

# 1. Why a "wave equation" at all

Many physical quantities that oscillate in space and time — the displacement of a string, pressure in air, the transverse electric field, the electron wavefunction — obey a second-order PDE of the same generic shape:

$$
\nabla^2 U(\mathbf{r}, t) - \frac{1}{c^2}\,\frac{\partial^2 U(\mathbf{r}, t)}{\partial t^2} = S(\mathbf{r}, t) .
$$

Here $U$ is whatever field we're tracking, $c$ is the speed at which disturbances propagate in the medium, and $S(\mathbf{r}, t)$ is a **source** — something external injecting energy or disturbance into the field. If $S = 0$ the field only ever does what it was already doing (initial conditions ringing out); if $S \neq 0$, something is actively driving it.

This single equation describes wildly different physics depending on what $U$, $c$, and $S$ represent — that universality is exactly why it's worth studying the equation once, abstractly, rather than re-deriving "wave behaviour" separately for sound, light, and electrons.

---

# 2. Time-harmonic fields: separating out the clock

In a microscope (or a lab, or an antenna range) we are almost never interested in a wave that switches on once and dies away. We care about a **steady-state, single-frequency** field: the electron gun runs continuously at one energy, the laser runs at one wavelength, the loudspeaker plays one tone. Mathematically, "single frequency" means we assume the field factorises into a spatial part and a fixed oscillation in time:

$$
U(\mathbf{r}, t) = u(\mathbf{r})\, e^{-i\omega t}.
$$

This is not an approximation — it is a choice of what question to ask. We are asking "what does the field look like *once it has settled into* steady oscillation at frequency $\omega$?", and deferring transients entirely.

Substitute into the wave equation. The spatial derivative only acts on $u(\mathbf{r})$:

$$
\nabla^2 u(\mathbf{r})\, e^{-i\omega t} - \frac{1}{c^2}\, u(\mathbf{r})\,\frac{\partial^2}{\partial t^2} e^{-i\omega t} = S(\mathbf{r}, t).
$$

The time derivative is easy: $\dfrac{\partial^2}{\partial t^2} e^{-i\omega t} = -\omega^2 e^{-i\omega t}$. If the source is also time-harmonic at the same frequency, $S(\mathbf{r}, t) = f(\mathbf{r})\, e^{-i\omega t}$, the common factor $e^{-i\omega t}$ cancels from every term, leaving a purely spatial equation:

$$
\boxed{\ \nabla^2 u(\mathbf{r}) + k^2 u(\mathbf{r}) = f(\mathbf{r})\ } \qquad \text{with } k^2 \equiv \frac{\omega^2}{c^2}.
$$

This is **the non-homogeneous Helmholtz equation**. We have not added any new physics — we have simply asked the wave equation what it looks like for one clean frequency, and the clock ($e^{-i\omega t}$) has dropped out entirely. Everything from here on is a statement about *shape in space*, at fixed $k$.

**Key quantity: the wavenumber.** $k = \omega/c = 2\pi/\lambda$ sets the spatial scale of the oscillation — how tightly the wave wiggles in space. Different physical systems put different things into $k$ (we'll see this explicitly for the electron below), but geometrically $k$ always plays the same role.

---

# 3. Homogeneous vs. non-homogeneous: what the source term *means*

Set $f \equiv 0$:

$$
\nabla^2 u + k^2 u = 0 \qquad \text{(homogeneous Helmholtz equation).}
$$

This describes a field that is oscillating in space with wavenumber $k$ but has **nothing currently pushing on it** — like a plane wave travelling through empty space, or a string plucked once and left to ring at its natural frequency. Solutions are plane waves $u = A e^{i\mathbf{k}\cdot\mathbf{r}}$, spherical waves, or combinations — whatever satisfies the boundary conditions, with no external forcing anywhere.

Keep $f(\mathbf{r})$: something at each point $\mathbf{r}$ is actively injecting field. Three examples, same equation:

| System | $u(\mathbf{r})$ | Source $f(\mathbf{r})$ |
|---|---|---|
| Loudspeaker in a room | acoustic pressure | the driven speaker cone |
| Dipole antenna | radiated E-field component | oscillating charge/current in the antenna |
| Electron hitting an atom | electron wavefunction $\psi$ | the atomic potential $V(\mathbf{r})$ (Section 4) |

The mathematical structure is identical in all three: a field obeying the *free* wave equation everywhere **except** where the source term is nonzero, and matching smoothly onto free waves far from the source. This is precisely the situation you are in every time an electron beam hits a specimen: free propagation in vacuum, then a localized region (the atom, the crystal) where the field is being "pushed" by the potential.

*(This is where the general theory earns its keep for us: once we know how to solve $(\nabla^2+k^2)u=f$ for **any** localized source $f$, we can plug in $f = -\text{(atomic potential term)}$ and get scattered electron waves for free — no separate theory needed. That derivation is Lecture 2.)*

---

# 4. The time-independent Schrödinger equation *is* a driven Helmholtz equation

This is today's punchline, and the reason this whole module exists.

Start from the time-independent Schrödinger equation for an electron of energy $E$ in a potential $V(\mathbf{r})$:

$$
-\frac{\hbar^2}{2m}\nabla^2 \psi(\mathbf{r}) + V(\mathbf{r})\,\psi(\mathbf{r}) = E\,\psi(\mathbf{r}).
$$

Rearrange purely algebraically — move everything except the Laplacian to the right, then divide through by $-\hbar^2/2m$:

$$
\nabla^2 \psi(\mathbf{r}) + \frac{2m}{\hbar^2}\big(E - V(\mathbf{r})\big)\,\psi(\mathbf{r}) = 0.
$$

Now split $E - V(\mathbf{r})$ into a constant piece and a spatially-varying piece — this is the only conceptual step in the whole derivation. Define

$$
k^2 \equiv \frac{2mE}{\hbar^2} \qquad\text{(the free-electron wavenumber, set by the beam energy)},
$$

and move the potential-dependent remainder to the right-hand side:

$$
\boxed{\ \nabla^2 \psi(\mathbf{r}) + k^2 \psi(\mathbf{r}) = \frac{2m}{\hbar^2}\, V(\mathbf{r})\,\psi(\mathbf{r})\ }.
$$

This **is** the non-homogeneous Helmholtz equation, with

$$
f(\mathbf{r}) = \frac{2m}{\hbar^2}\, V(\mathbf{r})\, \psi(\mathbf{r}).
$$

Read this the way you'd read Section 3's table: $k$ is fixed by how fast the electron is (its beam energy — a knob you control at the gun), and the potential $V(\mathbf{r})$ of every atom in the specimen is the *source* driving deviations away from a free plane wave. Where $V=0$ (vacuum), $\psi$ just satisfies the homogeneous equation and propagates as a free wave. Where $V\neq0$ (inside/near an atom), the atom acts exactly like the loudspeaker or the antenna in Section 3: it locally drives the field, and that driving is what produces a scattered wave radiating outward from the atom.

**Two things to notice, because they matter for every later lecture:**

- The source term $f(\mathbf{r}) = \frac{2m}{\hbar^2}V(\mathbf{r})\psi(\mathbf{r})$ contains $\psi$ itself. This is *not* an external, prescribed source like the loudspeaker — the field drives itself, self-consistently, wherever it overlaps a potential. That self-consistency is exactly why Lippmann–Schwinger (Lecture 3) has to be an *integral equation* rather than a simple convolution: you cannot write down $f$ until you already know $\psi$ everywhere the potential is nonzero.
- $k^2 = 2mE/\hbar^2$ depends only on the beam energy, not on position — so the "medium" (vacuum) is uniform, and *all* of the spatial structure of the scattered wave comes from $V(\mathbf{r})$. This is why diffraction patterns encode the specimen's potential (and hence its atomic structure) so directly.

---

# 5. Where this leaves us

We now have one equation, $(\nabla^2 + k^2)u = f$, that:

- reduces to free-wave propagation when $f=0$,
- describes a driven field — sound, radiation, or an electron wave — wherever $f\neq0$,
- and, for an electron in a specimen, has $f$ built from the very potential we're trying to image.

What we don't have yet is a way to *solve* it for a given $f$. That is the single job of Lecture 2: build the Green's function $G$ for the Helmholtz operator, so that $u = u_{\text{free}} + \int G(\mathbf{r},\mathbf{r}')f(\mathbf{r}')\,d\mathbf{r}'$ — and see the spherical outgoing wave $e^{ikr}/r$ appear as the universal "response to a point push," whether that push is a loudspeaker driver, a radiating dipole, or a single atom.

---

# Recitation / self-check questions

1. Starting from $U(\mathbf{r},t)=u(\mathbf{r})e^{-i\omega t}$, show explicitly why a source at a *different* frequency than $\omega$ cannot be absorbed into the same time-independent equation. (This is why "monochromatic" mattered in Section 2.)
2. For the electron case, write $f(\mathbf{r})$ for a square-well potential $V(\mathbf{r}) = -V_0$ inside a sphere of radius $a$, zero outside. Where is the homogeneous equation satisfied, and where is the driven (non-homogeneous) equation needed?
3. Convince yourself the Schrödinger source term is *linear* in $\psi$ (i.e. $f = (2m/\hbar^2)V\psi$, not some independent function). What does this imply about doubling the incoming beam intensity — does the scattered pattern's *shape* change, or only its overall magnitude?
4. In the loudspeaker analogy, what physical quantity plays the role of $k$? What would it mean, physically, for $k$ to be *complex* (this is a preview of absorption/attenuation, not required to answer fully — just reason about it).
