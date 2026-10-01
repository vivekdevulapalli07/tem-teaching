---
title: "Lecture 2 — Green's Functions for the Helmholtz Equation"
subtitle: "Scattering Theory for Electron Microscopy, Module 1"
---

# Learning objectives

By the end of this lecture you should be able to:

1. State what a Green's function is, and why solving the single "point-source" problem solves the equation for *any* source.
2. Derive the outgoing-wave Green's function for the 3D Helmholtz equation, $G(\mathbf{r},\mathbf{r}') = -\dfrac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{4\pi|\mathbf{r}-\mathbf{r}'|}$, and explain physically why it is a spherical wave.
3. Explain the radiation condition, and why it is what picks the outgoing solution over the equally valid incoming one.
4. Write the general solution of $(\nabla^2+k^2)u=f$ as a superposition (convolution) integral over the source.

---

# 1. The point-source idea

We ended last time with one equation to solve for an arbitrary source:

$$
\nabla^2 u(\mathbf{r}) + k^2 u(\mathbf{r}) = f(\mathbf{r}).
$$

$f(\mathbf{r})$ could be anything — a whole loudspeaker cone, an extended antenna, every atom in a crystal. Solving the equation separately for each possible shape of $f$ would be hopeless. Instead, notice that the equation is **linear**: if $u_1$ solves it for source $f_1$ and $u_2$ solves it for source $f_2$, then $u_1+u_2$ solves it for source $f_1+f_2$. This is the superposition principle, and it means we only ever need to solve the equation once — for the simplest possible source, a single point — and then build up any $f(\mathbf{r})$ as a (continuous) sum of points.

A single point source at position $\mathbf{r}'$ is represented by the Dirac delta function $\delta(\mathbf{r}-\mathbf{r}')$: zero everywhere except at $\mathbf{r}=\mathbf{r}'$, and normalised so that $\int \delta(\mathbf{r}-\mathbf{r}')\,d\mathbf{r} = 1$. The response of the field to *this* unit point source is called the **Green's function** $G(\mathbf{r},\mathbf{r}')$, defined by

$$
\boxed{\ \big(\nabla^2 + k^2\big)\, G(\mathbf{r},\mathbf{r}') = \delta(\mathbf{r}-\mathbf{r}')\ }.
$$

Physically: $G(\mathbf{r},\mathbf{r}')$ is "the field you'd measure at $\mathbf{r}$ if you placed an idealised unit point source at $\mathbf{r}'$." Once you know that for *every pair* of points, you know the field for *any* distribution of sources, by superposition — which is exactly Section 4.

---

# 2. Solving for $G$: why a point source radiates a spherical wave

By symmetry, put the source at the origin ($\mathbf{r}'=0$) and look for a solution that depends only on the distance $r=|\mathbf{r}|$, since nothing in the problem picks out a preferred direction. Away from the origin ($r\neq 0$), $G$ satisfies the *homogeneous* Helmholtz equation, and the radial part of the Laplacian acting on a function of $r$ alone is

$$
\nabla^2 G(r) = \frac{1}{r}\frac{d^2}{dr^2}\big(r\,G(r)\big).
$$

So for $r>0$:

$$
\frac{1}{r}\frac{d^2}{dr^2}\big(r G\big) + k^2 G = 0 \quad\Longrightarrow\quad \frac{d^2}{dr^2}\big(rG\big) + k^2 (rG) = 0.
$$

This is just the ordinary 1D wave equation for the new variable $\chi(r) \equiv rG(r)$, whose general solution is a superposition of $e^{ikr}$ and $e^{-ikr}$:

$$
G(r) = \frac{A\, e^{ikr} + B\, e^{-ikr}}{r}.
$$

Both terms are perfectly good solutions of the homogeneous equation away from the origin — the delta function on the right-hand side only constrains behaviour *at* $r=0$ (fixing the overall normalisation $A+B$, via the same divergence argument used for the Coulomb/Poisson Green's function), and does not by itself pick between the two terms. Something else has to select the physical one.

**Recovering the time dependence tells you which term is physical.** Remember the full field is $U(\mathbf{r},t) = u(\mathbf{r})e^{-i\omega t}$. So:

$$
\frac{e^{ikr}}{r}\, e^{-i\omega t} = \frac{e^{i(kr-\omega t)}}{r}, \qquad \frac{e^{-ikr}}{r}\, e^{-i\omega t} = \frac{e^{-i(kr+\omega t)}}{r}.
$$

Look at the surfaces of constant phase. For the first term, phase is constant when $kr-\omega t = \text{const}$, i.e. $r$ *increases* with $t$ — a wavefront expanding outward from the source. For the second term, $r$ *decreases* with $t$ — a wavefront converging inward, arriving at the source from infinity, timed perfectly to vanish exactly as it gets there. The second solution isn't wrong mathematically; it's just not what a real source does. A real source (a speaker turning on, an atom scattering a beam) creates disturbance that spreads *away* from it, not disturbance that was already converging in from the universe beforehand.

This causality requirement — *waves radiate outward from their sources, not inward from infinity* — is called the **Sommerfeld radiation condition**, and it is what selects $A=1,\ B=0$:

$$
\boxed{\ G(\mathbf{r},\mathbf{r}') = -\frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{4\pi\,|\mathbf{r}-\mathbf{r}'|}\ }.
$$

(The $-1/4\pi$ normalisation is fixed by integrating the equation over a small sphere around $\mathbf{r}'$ and using the same divergence-theorem trick you used for $\nabla^2(1/r) = -4\pi\delta(\mathbf{r})$ in electrostatics — the $k^2G$ term is negligible on a vanishingly small sphere, so the normalisation is exactly the electrostatic one.)

**Physical reading:** a unit point source produces a spherical wave, centred on the source, whose amplitude falls off as $1/r$ (so that the power flowing outward through a sphere of radius $r$, which scales as amplitude² × area $\propto (1/r)^2 \times r^2$, stays constant — energy conservation) and whose phase advances outward at speed matching $k$.

---

# 3. Sanity checks

- **Far from the source**, $G$ locally looks like $e^{ikr}$ times a slowly-varying $1/r$ envelope — a wave moving radially outward with wavenumber $k$, exactly as intuition demands.
- **Units.** $\delta(\mathbf{r}-\mathbf{r}')$ has dimensions of (length)$^{-3}$ (it integrates to 1 over a volume), so $G$ must have dimensions of (length)$^{-1}$ — consistent with the explicit $1/|\mathbf{r}-\mathbf{r}'|$.
- **$k\to 0$ limit.** As $k\to 0$ the Helmholtz equation reduces to Poisson's equation $\nabla^2 G = \delta$, and indeed $G \to -1/4\pi r$, the familiar electrostatic Green's function. This is a useful check to run on any Green's function you derive: does it collapse to something you already trust in a limiting case?

---

# 4. Superposition: solving for *any* source

Now use linearity as promised. Multiply the defining equation for $G$ by $f(\mathbf{r}')$ and integrate over all $\mathbf{r}'$:

$$
\int \big(\nabla^2+k^2\big)G(\mathbf{r},\mathbf{r}')\, f(\mathbf{r}')\, d\mathbf{r}' = \int \delta(\mathbf{r}-\mathbf{r}')\, f(\mathbf{r}')\, d\mathbf{r}' = f(\mathbf{r}).
$$

The Laplacian and $k^2$ act only on $\mathbf{r}$, so they can be pulled outside the $\mathbf{r}'$-integral:

$$
\big(\nabla^2+k^2\big) \underbrace{\int G(\mathbf{r},\mathbf{r}')\, f(\mathbf{r}')\, d\mathbf{r}'}_{\displaystyle u_{p}(\mathbf{r})} = f(\mathbf{r}).
$$

So a particular solution of the driven Helmholtz equation, for *any* source distribution $f$, is just the convolution of $f$ with the point-source response:

$$
\boxed{\ u_p(\mathbf{r}) = \int G(\mathbf{r},\mathbf{r}')\, f(\mathbf{r}')\, d\mathbf{r}' = -\frac{1}{4\pi}\int \frac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{|\mathbf{r}-\mathbf{r}'|}\, f(\mathbf{r}')\, d\mathbf{r}'\ }.$$

Read this as: *the field is a sum, over every point in the source, of an outgoing spherical wavelet launched from that point, weighted by how strong the source is there.* This is exactly the Huygens picture of wave propagation — every point a source of its own expanding spherical wavelet, all interfering — except now it is not a hand-wavy construction but an exact, derived consequence of linearity.

The most general solution adds any solution of the *homogeneous* equation, $u_h$, satisfying $(\nabla^2+k^2)u_h=0$:

$$
u(\mathbf{r}) = u_h(\mathbf{r}) + u_p(\mathbf{r}).
$$

$u_h$ is fixed by whatever is incident from outside the source region — e.g. the incoming plane-wave electron beam, before it reaches the specimen — while $u_p$ is entirely the field generated by the source itself. This split, "incident wave plus wave radiated by the source," is the exact structure you will use in every scattering calculation from here on.

---

# 5. Where this leaves us

We now have, in closed form, the response of the Helmholtz operator to a point push, and a recipe for turning *any* extended source into a field via a single integral. Two loose ends remain before this becomes a scattering theory: the source $f$ in the electron case was itself proportional to $\psi$ — the very thing we're solving for — so the convolution integral above is not yet an explicit solution, only a self-consistency relation; and we have only used the source to build $u_p$ far from *any* boundaries. Both of those are the natural next problem to tackle.

---

# Recitation / self-check questions

1. Verify the $k\to0$ limit explicitly: take $G(\mathbf{r},\mathbf{r}')=-\dfrac{e^{ik|\mathbf{r}-\mathbf{r}'|}}{4\pi|\mathbf{r}-\mathbf{r}'|}$ and confirm it reduces to the electrostatic Green's function as $k\to 0$.
2. Suppose two point sources of equal strength sit a distance $d$ apart, both driven at the same frequency (in phase). Using the superposition integral, write down $u_p(\mathbf{r})$ explicitly as a sum of two spherical wavelets, and identify the condition on $d$, $k$, and the observation direction under which the two wavelets interfere constructively far away. (This is the two-slit/two-atom interference pattern, derived from first principles rather than assumed.)
3. Redo the radial derivation in Section 2 for the 1D Helmholtz equation, $u''(x) + k^2 u(x) = \delta(x)$. You should find $G(x) = \dfrac{i}{2k}e^{ik|x|}$ (no $1/r$ decay, because energy spreads over a point in 1D rather than a growing sphere). Confirm this is finite everywhere, unlike the 3D case which diverges at $r=0$ — why is that divergence not a physical problem?
4. Explain, in one or two sentences and without equations, why "outgoing" is the physically sensible choice for a Green's function but would *not* necessarily be the sensible choice if you were instead solving a *time-reversed* problem (e.g. designing a lens that focuses a wave down onto a point).
