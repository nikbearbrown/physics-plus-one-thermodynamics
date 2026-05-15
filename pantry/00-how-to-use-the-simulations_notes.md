# Research Notes: Chapter 00 — How to Use the Simulations

**Source:** TIKTOC.md chapter entry (Chapter 00)
**Notes file:** 00-how-to-use-the-simulations_notes.md
**Corresponding chapter:** chapters/00-how-to-use-the-simulations.md (not yet written)
**Generated:** 2026-05-14

---

## Chapter summary (from TIKTOC.md)

Get the student to a working, modifiable D3 thermodynamics simulation before any physics. First simulation is an ideal gas in a 2D box: N molecules bouncing elastically, with temperature computed from mean kinetic energy and pressure computed from momentum transfer to the walls. Makes the central claim of kinetic theory immediately visible — temperature is molecular motion — before it is stated as a law.

---

## A. Conceptual foundations

### The Brutalist three-file system, adapted for thermodynamics

`CLAUDE.md`, `DESIGN.md`, `PROJECT.md` — same architecture as in earlier volumes, but with **thermodynamics-specific conventions** in `DESIGN.md`:
- Particle color encodes speed (cool blue for slow, warm red for fast)
- Heat flow rendered as orange arrows
- Work as green arrows
- PV diagram curves in purple
- Entropy as a gold running total
- Thermal reservoirs as gray gradient blocks

`CLAUDE.md` names: D3 v7, single HTML, requestAnimationFrame loops for particle physics, elastic collision detection, periodic boundary or wall reflection, real-time computed thermodynamic quantities (T from ⟨KE⟩, P from wall impulse).

### The four-move prompt structure

Show / Say / Constrain / Verify — same scaffold as the other Physics +1 volumes. The Verify move is critical for thermodynamics simulations because the physics is statistical and easy to get wrong (e.g., not enforcing elastic collisions properly leads to runaway energy gain).

### Why "ideal gas in a box" is the right first simulation

The ideal gas simulation is the cleanest possible introduction to thermodynamics. With N=50 particles bouncing elastically:
- Temperature: $T = m\langle v^2 \rangle/(2 k_B)$ in 2D (or $/3k_B$ in 3D)
- Pressure: $P = \sum |\Delta p_{\text{wall}}|/(A \Delta t)$ — running average of momentum transfer per unit area per unit time

When the student adds energy by speeding up the particles via a slider, $T$ visibly rises. When they shrink the box, $P$ rises. The PV behavior of an ideal gas — $PV = NkT$ — is *visible* before it is stated.

**Common misconception**: that "temperature" and "heat" are interchangeable. The simulation distinguishes them visually: temperature is a single number (computed from the molecular speeds); heat is shown later as energy *flowing* between objects.

**Worked example**: 50 particles, all initially with the same speed $v_0 = 100$ m/s. Temperature: $T = (1/2)(1.66 \times 10^{-26})(100)^2/(1.38 \times 10^{-23}) = 6$ K (very cold). After elastic collisions equilibrate the distribution toward Maxwell-Boltzmann, $\langle v^2 \rangle$ stays the same (energy conservation), so $T$ stays at 6 K. But the *distribution* of speeds changes — some particles slow, some speed up. This is the Maxwell-Boltzmann distribution emerging from collisions.

### Elastic collision physics

Two particles of equal mass colliding elastically: along the line of centers at the moment of contact, they exchange velocity components. Perpendicular components are unchanged. The math:
1. Compute normal direction $\hat{n}$ from particle A to particle B.
2. Decompose each velocity into $v_n$ (along $\hat{n}$) and $v_t$ (perpendicular).
3. Swap normal components: $v_{n,A}' = v_{n,B}$, $v_{n,B}' = v_{n,A}$.
4. Reconstruct velocities.

Wall collisions: reverse the velocity component normal to the wall.

Numerical care: time steps must be small enough that particles don't tunnel through each other or through walls between updates. Adaptive step size or simple small-step Euler suffices for visualization.

---

## B. Domain examples and cases

### Case 1: PhET Gas Properties as benchmark
The University of Colorado PhET simulation "Gas Properties" (https://phet.colorado.edu/en/simulations/gas-properties) is the canonical reference for an intro-level gas simulator. The +1 layer adds student-built modifiability — the student can extend the simulation themselves for any problem they encounter.

### Case 2: Molecular dynamics in research
Industrial molecular-dynamics simulations (LAMMPS, GROMACS) use the same elastic-collision framework, scaled to millions of particles, for real chemistry and materials research. The intro version teaches the principles.

### Case 3: The Stern-Gerlach experiment connection
Later in this book (and in the QM volume), individual-particle statistical behavior recurs. The ideal-gas-in-a-box is the prototype: many particles, statistical macroscopic quantities, no individual trajectory predictable.

### Failure case: prompting without verification
Without the Verify move in the prompt, an LLM can produce a simulation where particles slowly gain energy (numerical instability) or lose it (inelastic collisions inadvertently). The result is a simulation where T drifts upward or downward over time — invisible without explicit checking.

---

## C. Connections and dependencies

**Prerequisites:** Basic terminal/file literacy. Algebra. Awareness that LLMs can generate code.

**Unlocks:** Every subsequent chapter's LLM Exercise depends on the Brutalist files being in place.

**Adjacent chapter connections:**
- Ch 1 (Temperature): the simulation visually demonstrates the molecular-motion definition of temperature before Ch 1 states it as a postulate.
- Ch 3 (Ideal gas + kinetic theory): same simulation framework, now with the Maxwell-Boltzmann distribution overlaid.

---

## D. Current state of the field

**Settled:**
- D3 v7 is the right tool for browser-based thermodynamics visualization.
- LLM-assisted code generation reliably produces working ideal-gas simulators.
- The four-move prompt scaffolding produces consistent output across LLM providers.

**Contested or emerging:**
- The pedagogical value of student-built sims vs. PhET-style pre-built sims is actively researched; no clean consensus.

**Key references:**
1. PhET Interactive Simulations — "Gas Properties": https://phet.colorado.edu/en/simulations/gas-properties
2. Bostock, M. D3.js v7 documentation: https://d3js.org/
3. Çengel & Boles, *Thermodynamics: An Engineering Approach* — Ch 1 for the molecular framing.

**Recent developments:**
- LLM coding quality continues to improve; the four-move prompt remains reliable across model generations.

---

## E. Teaching considerations

**Where students get stuck:**
- Confusing temperature with heat. The simulation can make this concrete by showing temperature as a current state variable vs. heat as a flux.
- Numerical drift in particle simulations — invisible without explicit verification.
- Sign conventions for momentum transfer at walls — sometimes students get pressure with the wrong sign.

**Analogies and framings that work:**
- *"The simulation runs the gas; you read the macroscopic quantities."* Anchors the student as observer of an autonomous system.
- *"Temperature is a single number; the particles are doing the actual work."* Distinguishes macroscopic from microscopic.

**Exercises that build the target skill:**
- *Verify the equipartition theorem* (Bloom: Apply) — average kinetic energy per particle should be $(1/2)k_B T$ per degree of freedom. Compute this from the simulation; verify.
- *Pressure scaling with N* — double the number of particles at fixed temperature; verify pressure doubles (ideal gas law).
- *Heat addition* — increase the speed of all particles by 10%; verify T increases by 21% ($T \propto v^2$).

---

## F. Library files relevant to this chapter

None. Shared MD library is non-physics.

---

## G. Gaps and flags

- FLAG: Brutalist system is the author's framework; cite as Bear's work.
- FLAG: 2D vs. 3D temperature formula — be explicit about which the simulation uses (2D: $T = m\langle v^2 \rangle / (2 k_B)$; 3D: $/(3 k_B)$).
- GAP: Numerical integration choice for the particle dynamics matters. Simple Euler suffices for visualization but accumulates energy drift; verlet or symplectic methods are better for long simulations. Probably beyond the scope of Ch 0; mention in passing.
