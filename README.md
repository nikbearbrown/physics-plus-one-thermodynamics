# Physics +1: Thermodynamics

**Author:** Nik Bear Brown
**Series:** Physics +1 (Volume 2)
**Publisher:** Bear Brown, LLC
**Status:** Draft

---

## About this book

*Thermodynamics as process physics — cycles, distributions, irreversibility.* This volume teaches the laws that govern energy bookkeeping (the first law) and the direction of time (the second law). Statistical mechanics enters where it earns its place — when many-particle systems demand a different kind of reasoning than single-particle mechanics — and the connection between entropy and information is treated as a feature, not a footnote.

The +1 layer makes the processes visible: a D3 PV-diagram animator for isothermal/adiabatic/isochoric/isobaric paths; a Maxwell-Boltzmann distribution the student can heat and cool in real time; a Carnot-cycle simulator with the irreversibility losses called out; a heat-engine-efficiency explorer that connects the abstract Carnot bound to real refrigerators and power plants. The book also names what classical thermodynamics still does not solve — the turbulence problem, the foundations of the second law from microscopic reversibility.

Audience: students who have completed classical mechanics and have working algebra and calculus. The 7 chapter drafts in `chapters/` cover the standard thermodynamics-plus-fluids sequence (OpenStax-derived); `outline.md` proposes an 8-chapter published volume including two new chapters (*Statistical Mechanics and Entropy*; *Thermodynamics in the Real World*).

## How this directory is organized

```
book.md              ← one-sentence pitch, argument, gap, reader, high-level outline (planning)
outline.md           ← working TOC with D3 simulation notes per chapter
vision.md            ← Tic TOC Phase 1: vision and positioning
architecture.md      ← Tic TOC Phase 2: learning architecture
chapters-spec.md     ← Tic TOC Phase 3: per-chapter specifications
risks.md             ← Tic TOC Phase 4: scope, comparables, adoption risks
pantry/              ← scratch storage for fragments and snippets
chapters/            ← drafts (this is where the book lives)
images/              ← figures and hero images per chapter
styles/              ← Kindle-bound CSS (shared base + book-specific overrides)
build.sh             ← compile the EPUB
graphs.sh            ← process figure-placeholder comments into images/tables
```

## Detailed Table of Contents

### Front Matter

| File | Section |
|------|---------|
| `chapters/00-frontmatter.md` | Title page, copyright, dedication, preface |
| `chapters/00b-introduction.md` | Book-level introduction (template placeholder) |

### Chapters

| # | File | Title |
|---|------|-------|
| 1 | `chapters/01-fluid-statics.md` | Fluid Statics |
| 2 | `chapters/02-thermal-energy-heat-and-work.md` | Thermal Energy, Heat, and Work: What Temperature Actually Measures |
| 3 | `chapters/03-fluid-dynamics-and-its-biological-and-medical-applications.md` | Fluid Dynamics and Its Biological and Medical Applications |
| 4 | `chapters/04-thermodynamics.md` | Thermodynamics: Energy's One-Way Street |
| 5 | `chapters/05-temperature-kinetic-theory-and-the-gas-laws.md` | Temperature, Kinetic Theory, and the Gas Laws |
| 6 | `chapters/06-heat-and-heat-transfer-methods.md` | Heat and Heat Transfer Methods |
| 7 | `chapters/07-thermodynamics.md` | Thermodynamics |

### Back Matter

| File | Section |
|------|---------|
| `chapters/99-back-matter.md` | Acknowledgments, About the Author, References, Index |

## Notes on the chapter set

Ch. 4 and ch. 7 are parallel *Thermodynamics* drafts from different source textbooks; the curated published outline (see `outline.md`) collapses them and adds two new chapters — *Statistical Mechanics and Entropy* and *Thermodynamics in the Real World*. Fluid statics and fluid dynamics share two of the seven slots here because thermodynamics and fluids are taught together in the source corpus; the curation reduces fluids coverage.

## Build

```bash
./build.sh
```

Output lands in `output/` (gitignored).

## Figures

```bash
./graphs.sh
```

Processes `<!-- → [TYPE: description] -->` comments throughout the chapters:
tabular figures become classed markdown tables; non-tabular figures become
placeholder images in `images/`, ready to replace; CSS log appends to
`styles/kindle-book.css` on each run.

## Publish

Upload `output/physics-plus-one-thermodynamics.epub` to [KDP](https://kdp.amazon.com).
