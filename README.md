# TEM Teaching

An open, interactive course on transmission electron microscopy — built from the ground up as worked notebooks, derivation-based lecture notes, and interactive widgets rather than slides. See [ROADMAP.md](ROADMAP.md) for the full chapter plan.

## How to use this repo

Each chapter is a numbered top-level folder, meant to be worked through in order. Inside a chapter you'll typically find:

- **Notebooks** (`.ipynb`) — run these yourself; most contain a slider or interactive plot you need to touch to get the result, not a pre-rendered figure.
- **Lecture notes** (`.md` + `.pdf`) — the same source rendered two ways: `.md` for reading on GitHub, `.pdf` for printing/offline use.
- **Widgets** (`.html`) — standalone interactive pages, no install required. Open the file directly in a browser.

## Chapters

| # | Chapter | Status | Contents |
|---|---------|--------|----------|
| 01 | [Describing the instrument](01-describing-the-instrument/) | Available | Electron wavelength vs. accelerating potential; diffraction-limited resolution |
| 02 | [Diffraction physics](02-diffraction-physics/) | Available | 6-lecture module: wave equation → Howie-Whelan/multislice, with 4 interactive widgets |
| 03 | [Aberration correction](03-aberration-correction/) | Planned | — |
| 04 | [In-situ electron microscopy](04-in-situ-electron-microscopy/) | Planned | — |

## Running the notebooks

```bash
pip install numpy scipy matplotlib ipywidgets jupyter
jupyter notebook
```
