# Chapter 0 — How to Use the Simulations

*Get from zero to an ideal-gas-in-a-box simulation before any new physics.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Generate the three Brutalist governing files (`CLAUDE.md`, `DESIGN.md`, `PROJECT.md`) adapted for thermodynamics-specific simulation conventions.
2. **(Apply)** Write a four-move prompt (Show / Say / Constrain / Verify) and produce a working D3 ideal-gas simulator.
3. **(Analyze)** Verify a simulation: it opens, the physics is right at limits (T rises with energy added; P falls when V grows), and conventions match `DESIGN.md`.
4. **(Apply)** Modify the simulation: change particle count, raise temperature, halve the box width, and predict the change in pressure and temperature before reloading.

---

## Opening case: temperature as molecular motion, visible

A student is learning thermodynamics for the first time. The textbook defines temperature as $T = (2/3)\langle KE\rangle / k_B$. Algebraically clean. Physically opaque. Temperature *is* the mean translational kinetic energy of molecules. But the molecules are invisible. The textbook diagram is a static cartoon. The student memorizes the equation and moves on without seeing what it means.

Now imagine a simulation: 50 dots in a 2D box, bouncing off walls and each other. The dots are colored by speed — slow ones blue, fast ones red. A slider raises the average kinetic energy. The dots speed up; the colors shift toward red. Temperature, computed from $\langle v^2\rangle$ in real time, climbs from 200 K to 800 K as the slider moves.

This is what kinetic theory says, made visible.

The chapter ahead teaches you to build that simulation. By Chapter 1, you will look at the molecular speeds in your own working simulator and understand temperature in your bones. Without the simulation, you're stuck with the equation.

---

## Core concept

### The Brutalist three-file system, adapted for thermodynamics

Three governing files travel with the project across all 10 chapters. They are not documentation. They are **active prompts loaded with each interaction**.

**`CLAUDE.md` — coding constitution.** Names the library (D3 v7), file conventions (single HTML, inline CSS+JS, no external dependencies), physics constants ($k_B = 1.38 \times 10^{-23}$ J/K, $R = 8.314$ J/(mol·K), $N_A = 6.022 \times 10^{23}$/mol, $h = 6.626 \times 10^{-34}$ J·s, $\sigma_{\text{SB}} = 5.67 \times 10^{-8}$ W/(m²·K⁴)), numerical methods (particle dynamics via `requestAnimationFrame`, elastic collisions, real-time T and P computation), and a verification checklist.

**`DESIGN.md` — visual constitution.** Thermodynamics-specific:
- Particle speed colored blue → red (cool to hot)
- Heat flow Q: orange arrows
- Work W: green arrows
- PV curves: purple (isothermals dashed, adiabats solid)
- Entropy: gold running total
- Reservoirs: gray gradient blocks
- Canvas: 700×500 for particle sims; 700×400 for PV diagrams and distribution plots

**`PROJECT.md` — project state.** Scratch ledger updated by the student after each chapter.

### The four-move prompt structure

Show / Say / Constrain / Verify — the same scaffold the Physics +1 series uses across volumes. The Verify move is especially important for thermodynamics simulations because the physics is statistical (you can't tell from one snapshot whether everything is right) and the numerical methods can introduce subtle bugs (energy drift, lossy collisions).

### The ideal gas in a box

The simplest possible thermodynamics simulation. $N$ point particles in a 2D box, bouncing elastically off walls and each other. From the molecular state, compute macroscopic quantities:

**Temperature** (2D ideal gas):
$$T = \frac{m \langle v^2 \rangle}{2 k_B}$$

In 3D: divide by $3 k_B$ instead. The factor counts the *degrees of freedom* in each direction; in 2D each particle has 2 translational degrees of freedom, in 3D it has 3. Either is fine for visualization.

**Pressure** (running average of momentum transfer to walls):
$$P = \frac{1}{A} \cdot \frac{\sum |\Delta p_{\text{wall}}|}{\Delta t}$$

The simulation tracks the average momentum transferred to a wall per unit area per unit time and reports it.

**Worked example.** A simulation with 50 nitrogen molecules ($m = 28 \times 1.66 \times 10^{-27}$ kg = $4.65 \times 10^{-26}$ kg) in a 100 nm × 100 nm box, with initial average speed 400 m/s.

Temperature (2D): $T = (4.65 \times 10^{-26}) \times (400)^2 / (2 \times 1.38 \times 10^{-23}) \approx 269$ K. Close to room temperature, plausibly.

Pressure (rough estimate): each particle hits each wall about $v/(2L) = 400/(2 \times 10^{-7}) = 2 \times 10^9$ times per second. Momentum transfer per collision $\sim 2mv \approx 3.7 \times 10^{-23}$ kg·m/s. Per-wall force per particle: $\sim 7.4 \times 10^{-14}$ N. With 50 particles and wall area $A = L = 10^{-7}$ m (2D area is just length × 1 in convention): $P \sim 50 \times 7.4 \times 10^{-14} / 10^{-7} = 3.7 \times 10^{-5}$ Pa. Real ideal-gas pressure at 269 K from $NkT/V$ in this volume: $50 \times 1.38 \times 10^{-23} \times 269 / (10^{-7})^2 = 1.86 \times 10^{-5}$ Pa. Within a factor of 2 — close enough for a 50-particle visualization.

**The lesson.** The simulation lets you *measure* macroscopic quantities from the molecular state. Compare to the ideal gas law and watch them agree.

**The limit.** 50 particles is far below thermodynamic limit; fluctuations dominate. Real ideal gases have $\sim 10^{20}$ particles; statistical fluctuations are $\sim 1/\sqrt{N} \sim 10^{-10}$ of the mean. The simulation's $\sim 1/\sqrt{50} \sim 14\%$ fluctuations are visible and instructive — they're what statistical mechanics is *about*.

### Elastic collision physics

Particle-particle elastic collisions:
1. Detect contact: $|\vec{r}_i - \vec{r}_j| \leq 2r$.
2. Compute normal direction $\hat{n}$.
3. Decompose velocities into $v_n$ (along $\hat{n}$) and $v_t$ (perpendicular).
4. Swap normal components: $v_{n,i}' = v_{n,j}$, $v_{n,j}' = v_{n,i}$.
5. Reconstruct.

Wall collisions: reverse the velocity component perpendicular to the wall.

Energy is conserved by the swap rule (elastic collision). With enough collisions, the speed distribution evolves toward Maxwell-Boltzmann automatically — the simulation is *itself* a demonstration of statistical mechanics.

---

## Common misconceptions

**"Temperature is the average speed of molecules."** Almost. Temperature is proportional to the *average kinetic energy* — and kinetic energy is $(1/2)mv^2$, so temperature is the *mean of $v^2$*, not mean of $v$. The two are different ($\langle v^2 \rangle \neq \langle v \rangle^2$). Distinguishing them matters in Chapter 3 when the Maxwell-Boltzmann distribution shows three different speeds: most probable, mean, and root-mean-square.

**"All molecules at temperature T have the same speed."** They have a distribution. Chapter 3 plots it. Temperature is a property of the *distribution* (specifically the second moment, $\langle v^2\rangle$), not of individual molecules.

**"The simulation is exact."** The simulation has 50 particles when real gases have $10^{20}$. Statistical fluctuations are large. The simulation is a *toy* — exact at the level of its 50 particles, but a noisy approximation of macroscopic thermodynamics.

**"Brutalist files are documentation."** They are prompts. Tell Claude to read them in every conversation.

---

## Exercises

**Warm-up (Apply).** State the three Brutalist files and what each is for. Then write the four moves of the prompt structure with no formulas.

**Apply.** Run the ideal-gas simulation. Set N = 50, raise the energy slider. Predict before observing: does the *average speed* of the particles double when the temperature doubles?

**Apply.** With N = 50 particles, shrink the box width by half. Predict the new pressure (should double — ideal gas $PV = NkT$ at constant $T$). Verify.

**Apply + Analyze.** Track the simulation's measured pressure $P$ over 10 seconds. Plot the running average. Notice the noise (fluctuations of order $1/\sqrt{N}$, ~14% for $N=50$). With $N = 200$, are the fluctuations smaller? By what factor? (Answer: $\sqrt{4} = 2$ smaller.)

**Challenge.** The simulation defaults to 2D. Rewrite the temperature formula for 3D — $T = m\langle v^2\rangle / (3k_B)$. What changes in the simulation code? Why is 2D pedagogically useful?

---

## LLM Exercises

### Part 1 — Generate `CLAUDE.md`

> **Show.** I am building D3.js v7 thermodynamics simulations: a single HTML file each, with particle physics via `requestAnimationFrame`, elastic collision detection, and real-time computation of T, P, S.
>
> **Say.** Generate a `CLAUDE.md` coding constitution.
>
> **Constrain.** Sections: (1) Library/file conventions (D3 v7, single HTML, inline CSS+JS); (2) Physics constants ($k_B$, $R$, $N_A$, $h$, $\sigma_{SB}$); (3) Particle dynamics methods (elastic collision detection, wall reflection, small-step Euler integration); (4) Macroscopic-quantity computations (T from $\langle KE\rangle$, P from wall impulse rate, S from microstate count or process integration); (5) PV diagram conventions (P on y, V on x, area = work); (6) Animation idioms; (7) Verification checklist.
>
> **Verify.** ~60 lines. With this file loaded, Claude should produce a working ideal-gas simulator.

Save to `CLAUDE.md`.

### Part 2 — Generate `DESIGN.md`

> **Show.** Thermo simulations have specific visual conventions across chapters.
>
> **Say.** Generate `DESIGN.md`.
>
> **Constrain.** Particle color by speed (cool blue to warm red, gradient at $v/v_{rms}$). Heat Q: orange arrows. Work W: green arrows. PV curves purple (isotherm dashed, adiabat solid). Entropy ΔS: gold display. Reservoirs: gray gradient blocks. Canvas: 700×500 particles, 700×400 PV/distributions. Dark mode via `prefers-color-scheme`.
>
> **Verify.** All colors distinct; dimensions explicit; particle color formula stated.

Save to `DESIGN.md`.

### Part 3 — Generate `PROJECT.md`

Three lines: project name, current chapter, simulations completed (empty so far).

### Part 4 — Build the ideal-gas simulator (`00-ideal-gas-box.html`)

With `CLAUDE.md` and `DESIGN.md` loaded:

> **Show.** Ideal gas: $N$ point particles with mass $m$ bouncing elastically. Temperature $T = m\langle v^2\rangle / (2 k_B)$ in 2D. Pressure $P = \sum |\Delta p_{\text{wall}}|/(A \Delta t)$.
>
> **Say.** Build an ideal-gas-in-a-box simulator.
>
> **Constrain.** D3 v7. 2D box (700×500 canvas). $N=50$ particles, $m = 4.65 \times 10^{-26}$ kg (N₂). Initial Maxwell-Boltzmann distribution at $T_0 = 300$ K. Slider for "energy" (rescales all velocities by same factor). Slider for box width. Render: particles as circles colored by speed (DESIGN.md gradient). Live readouts: T (computed from $\langle v^2\rangle$), P (running 5-second average of wall impulse rate), $v_{rms}$, $v_{avg}$. Filename: `00-ideal-gas-box.html`.
>
> **Verify.** (a) At rest: T ≈ 0; particles stationary; P ≈ 0. (b) Add energy → T rises; particles speed up; colors shift red. (c) Shrink box → P rises (ideal gas law $PV = NkT$). (d) Wait 10s with no parameter change: T and P fluctuate by ~14% (consistent with $1/\sqrt{N}$).

Save to `00-ideal-gas-box.html`. Open in browser.

### Part 5 — Exploration

- Slowly raise the energy slider. Watch T climb. Verify the rate: doubling kinetic energy doubles temperature.
- Halve the box width while keeping energy constant. Pressure should double. Verify.
- Start with all particles at exactly $v = 400$ m/s in the same direction. Watch how collisions randomize the directions and broaden the speed distribution over time. This is the Maxwell-Boltzmann distribution emerging from collisions.

### Part 6 — Extension prompt (chapter bridge)

> **Show.** I have a working ideal gas simulator. Now I want to look at the *molecular speed distribution* explicitly — a histogram of speeds with the Maxwell-Boltzmann curve overlaid.
>
> **Say.** Modify the simulator to add a real-time speed histogram below the box.
>
> **Constrain.** Bin particle speeds into 20 bins from 0 to 1500 m/s. Update histogram every animation frame. Overlay the theoretical Maxwell-Boltzmann curve at the current T.
>
> **Verify.** With $T = 300$ K, peak of the distribution is at $v_{mp} = \sqrt{2k_BT/m} \approx 423$ m/s for N₂. Heat to 800 K: peak shifts right to about $\sqrt{2 \cdot 1.38 \cdot 800/4.65}\cdot 10^{1.5}\approx 690$ m/s.

Save as `00b-speed-distribution-preview.html`. This is the bridge into Chapter 1.

---

## What would change my mind

The simulation's central claim is that a small particle simulation (50–200 particles) faithfully demonstrates the central kinetic-theory results: $T \propto \langle KE\rangle$, $PV = NkT$, Maxwell-Boltzmann distribution emerging from elastic collisions. If a controlled experiment showed that students using the simulation produced no better intuition about thermodynamics than students using only textbook diagrams, the framework would need revision. I have not done that controlled experiment. The qualitative claim — that *seeing* molecular motion at the scale of dozens of particles builds intuition faster than reading static diagrams — is supported by physics-education-research literature (Wieman et al. on PhET; mounting evidence on interactive simulation pedagogy).

## Still puzzling

- *2D vs. 3D simulations.* This book uses 2D for visualization. Real gases are 3D. The temperature formula has a factor of 2 vs. 3. The qualitative physics is identical; the numbers differ.
- *Numerical integration drift.* Simple Euler integration accumulates small errors that, over long simulations, drift the total kinetic energy. Better methods (Verlet, symplectic integrators) are standard in research molecular dynamics. For visualization at the second-scale, Euler suffices.
- *How many particles are "enough" to teach intuition?* 50 shows the structure but with large fluctuations. 200 is smoother. 1000+ is essentially smooth but slower to render. The book's choice (50–100) is a balance; the trade-off is pedagogically interesting.

---

**Tags:** ideal gas, Brutalist files, four-move prompt, D3 v7, particle simulation, elastic collisions, kinetic theory, temperature, pressure

