# 03 — Aberration correction (in progress)

Lecture notes for this chapter are still being written. The interactive widget is available now and can be used on its own.

## Widget

| Widget | What it covers |
|--------|----------------|
| [Aberration Explorer](widgets/aberration-explorer.html) | The aberration function χ(ω) and the probe it forms: defocus, two- and three-fold astigmatism, axial coma, C₃/C₅ spherical aberration, and chromatic focal spread. Includes the π/4 criterion, Strehl ratio and probe size, the HRTEM phase-contrast transfer function, and a simulated ADF-STEM image of Si ⟨110⟩ dumbbells. |

It is self-contained HTML: open it directly in a browser, with no server or install needed. Presets walk from an uncorrected 300 kV lens through C<sub>s</sub> correction to the chromatic limit at 60 kV. The "Try this" section at the bottom of the page has guided exercises.

Adapted from the [aberration visualisation tool](https://vivekdevulapalli07.github.io/website/tools/aberration-visualisation) on the course author's website, which now runs this same widget. Compared with the original version:

- **The probe is the real point spread function.** It is computed as |F⁻¹[A(ω) e^(−iχ)]|² rather than with a phenomenological intensity formula.
- **The coefficients are in physical units.** Voltage, aperture and the aberrations are set in kV, mrad and nm/µm/mm, and the electron wavelength is relativistic.
- **New terms are included.** Defocus, C₅ and C<sub>c</sub> are added, along with C₁/C₃ balancing.
- **The coma description is corrected.** In the aberration function, coma is axial coma (C₂₁ = 3B₂), caused by beam tilt.
- **Missing example images are replaced.** A simulated Si ⟨110⟩ ADF image takes their place.

## Planned scope

- Spherical and chromatic aberration in the electron optical system
- The aberration function and phase plate; Zemlin tableau / C<sub>s</sub> measurement
- Hexapole and quadrupole-octupole correctors
- Practical effect on resolution and contrast transfer in HRTEM/STEM
