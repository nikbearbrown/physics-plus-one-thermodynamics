# TIKTOC.md — Physics +1: Thermodynamics
## A Simulation-First Thermodynamics Textbook

**Working title:** Physics +1: Thermodynamics — Interactive Process Simulators with Claude and D3
**Series:** Physics +1 Series (Volume 2)
**Author:** Nik Bear Brown · ni.brown@neu.edu · Bear Brown & Company
**Repo:** physics-plus-one-thermodynamics
**Version:** 1.0
**Status:** TIKTOC complete — ready for research gathering and chapter drafting

---

## Book Concept

This book teaches thermodynamics — from temperature and heat through the laws of thermodynamics, entropy, and statistical mechanics — to students who have completed classical mechanics, by pairing each conceptual chapter with LLM-generated D3.js simulations that make invisible processes visible. A PV diagram that animates as the gas expands. A Maxwell-Boltzmann distribution the student heats and cools in real time. A Carnot cycle that shows exactly where the irreversibility losses occur. An entropy simulator that counts microstates and watches the second law emerge from probability.

**The narrative arc runs from process to law to arrow of time.** The book begins with what temperature physically is (kinetic energy of molecules) and ends with why the universe has a preferred direction in time — and what that has to do with information, computation, and quantum mechanics. A student who finishes this book understands not just how a heat engine works but why no engine can beat Carnot, why entropy always increases, and why Maxwell's demon cannot violate the second law without erasing a memory.

**The +1 is the process visualization layer.** Thermodynamic processes are invisible in the classical presentation — PV diagrams are static curves. The simulations make them dynamic: isothermal, adiabatic, isochoric, isobaric paths animate as the gas changes state; heat flow is shown as a quantity moving between reservoirs; entropy is computed and displayed as a running total. Students develop process intuition that static diagrams cannot provide.

**Series position:** This volume follows Physics +1: Mechanics. The capstone chapter bridges forward to the Quantum Mechanics volume by connecting classical entropy (Boltzmann) to quantum entropy (von Neumann) and previewing quantum statistical mechanics.

**Fluids note:** Fluid statics and dynamics appear in the source chapter set but belong to the mechanics volume. This book retains only what thermodynamics needs from fluids — buoyancy as a thermal-density effect, pressure as a thermodynamic variable — and drops the rest.

---

## Book Type and Deployment

**Primary type:** Course textbook — adopted for a semester, chapter = roughly one week.

**Target course:** Thermodynamics module within calculus-based introductory physics sequence, or standalone thermodynamics course. Junior/senior physics and engineering students.

**Prerequisites assumed:** Classical mechanics (energy, work, momentum). Calculus (derivatives, integrals — used throughout). Algebra and trigonometry fluent. Basic chemistry helpful but not required (ideal gas law is derived, not assumed).

**Prerequisites explicitly not required:** Statistical mechanics (developed from scratch in Chapter 8). Quantum mechanics (previewed only in Chapter 10). Partial differential equations (first-order ODEs sufficient).

**Semester format:** 15 weeks. Chapter 0 assigned Week 1 alongside Chapter 1. Chapters 1–10 map to Weeks 1–10. Weeks 11–15 flex for lab integration, problem sessions, review, and final.

**What this book is not:** A graduate statistical mechanics text. A chemical thermodynamics text (no Gibbs free energy, no chemical potential beyond a preview). A fluid mechanics text. A pure computation course.

---

## The +1 System

Each chapter ends with an **LLM Exercise** block:
1. **The simulation prompt** — four-move (Show / Say / Constrain / Verify) prompt producing a working D3 visualization
2. **Exploration tasks** — specific parameter changes and questions answered by observation
3. **Extension prompt** — adds one feature or bridges to the next chapter

Chapter 0 generates `CLAUDE.md`, `DESIGN.md`, and `PROJECT.md`. These travel with the student through the book.

---

## Three-Act Learning Arc

**ACT ONE — Energy and Temperature (Chapters 1–3)**
*From "I know temperature exists" to "I understand what temperature physically is, how energy moves as heat, and how an ideal gas behaves."*
Temperature as mean kinetic energy → heat transfer mechanisms → the ideal gas and kinetic theory. The simulations make molecules visible: bouncing particles, speed distributions, heat flowing between objects. Students develop molecular intuition before encountering the laws.

**ACT TWO — The Laws (Chapters 4–7)**
*From "I understand individual processes" to "I can analyze any thermodynamic cycle and compute its entropy change."*
First law → thermodynamic processes and PV diagrams → second law and heat engines → entropy. Each simulation makes a law physically concrete: energy conservation enforced in real time, the Carnot cycle running with efficiency displayed, entropy increasing as a counted quantity.

**ACT THREE — From Statistics to Information (Chapters 8–10)**
*From "I know the laws" to "I understand where the laws come from and what they imply about information, computation, and quantum mechanics."*
Statistical mechanics (Boltzmann's derivation of the second law from probability) → thermodynamics in real devices → capstone connecting entropy to information and quantum mechanics. The student who completes Act Three understands why the second law is statistical not absolute, why Maxwell's demon cannot work, and how Boltzmann entropy connects to von Neumann entropy.

---

## Chapter List

---

### CHAPTER 00 — How to Use the Simulations
**Filename:** `00-how-to-use-the-simulations.md`
**Arc position:** Pre-chapter / setup

**One-line:** Students build the three Brutalist governing files and produce their first thermodynamics simulation — an ideal gas in a box with bouncing molecules — before reading any physics content.

**Chapter description:**
One job: get the student to a working, modifiable D3 thermodynamics simulation before any new physics. The first simulation is an ideal gas in a 2D box: N molecules bouncing elastically, with temperature computed from mean kinetic energy and pressure computed from momentum transfer to the walls. This is the right first simulation because it makes the central claim of kinetic theory immediately visible — temperature is molecular motion — before it is stated as a law.

**Core concepts:**
- The Brutalist system: CLAUDE.md, DESIGN.md, PROJECT.md
- The four-move prompt structure: Show / Say / Constrain / Verify
- D3 v7 for thermodynamics simulation: SVG canvas, particle animation via requestAnimationFrame, elastic collision physics, real-time computed quantities
- The ideal gas box as first simulation: N particles, elastic wall collisions, T from ⟨KE⟩, P from wall impulse
- The verification stack: physics check (does T increase when you add energy?), format check, browser test

**Key vocabulary:** ideal gas, kinetic energy, temperature, pressure, elastic collision, D3, SVG, four-move prompt

**What the student builds:**
- `CLAUDE.md` — thermodynamics simulation coding constitution (D3 v7, SVG canvas, particle simulation via requestAnimationFrame, elastic collision detection, real-time thermodynamic quantity computation, slider-driven parameter updates)
- `DESIGN.md` — visual constitution (particles: colored by speed blue→red; slow particles cool blue, fast particles warm red; heat flow arrows: orange; work arrows: green; PV curve: purple; entropy: gold; reservoirs: gray gradient blocks; dark mode support)
- `PROJECT.md` — project state
- `00-ideal-gas-box.html` — ideal gas simulator: N=50 particles bouncing in a box; sliders for N and total energy; displays T (computed from mean KE), P (computed from wall impulse rate), mean speed; particles colored by speed

**Simulation physics:**
Each particle: position **r**ᵢ, velocity **v**ᵢ. Update: **r**ᵢ → **r**ᵢ + **v**ᵢ Δt. Wall collision: reverse appropriate velocity component. Particle-particle: elastic collision when |**r**ᵢ - **r**ⱼ| < 2r. Temperature: T = m⟨v²⟩/(3k_B) (2D: T = m⟨v²⟩/(2k_B)). Pressure: P = Σ |Δp_wall|/(A·Δt) running average.

**Color conventions for DESIGN.md:**
- Particle speed: blue (#457b9d) for v < v_rms, red (#e63946) for v > 2v_rms, gradient in between
- Heat flow Q: orange arrows (#e76f51), width proportional to magnitude
- Work W: green arrows (#2a9d8f), width proportional to magnitude
- PV diagram curves: purple (#7b2d8b), 2px stroke
- Isothermal curves: dashed purple
- Adiabatic curves: solid purple
- Entropy ΔS: gold (#f4a261) running total display
- Thermal reservoirs: gray gradient blocks (#adb5bd to #6c757d)
- Dark mode: backgrounds to #1a1a1a

**Connection to Chapter 1:** The simulation shows temperature as molecular motion. Chapter 1 makes this precise — what temperature actually measures, and how it differs from heat.

---

### CHAPTER 01 — Temperature and Thermal Energy
**Filename:** `01-temperature-thermal-energy.md`
**Arc position:** Act One, Chapter 1

**One-line:** Students learn what temperature physically means at the molecular level, how thermal energy differs from heat, and how thermal expansion works — building a molecular speed simulator that shows the connection between temperature and kinetic energy directly.

**Chapter description:**
The opening chapter establishes the conceptual foundation that everything else builds on. Temperature is not heat — it is the average kinetic energy per molecule. Heat is energy in transit due to a temperature difference. Thermal energy is the total internal kinetic and potential energy of a system. These three concepts are routinely conflated by students; this chapter separates them carefully. Thermal expansion follows from molecular kinetic energy: higher temperature means more vigorous vibration, which means larger average separation. The ideal gas thermometer and the absolute temperature scale (Kelvin) are introduced. The simulation shows the molecular speed distribution at two temperatures — students see directly that higher temperature means a broader, faster-shifted distribution.

**Core concepts:**
- Temperature as average translational kinetic energy per molecule: ½m⟨v²⟩ = (3/2)k_BT
  - Boltzmann constant: k_B = 1.38×10⁻²³ J/K
  - Absolute zero: T=0 means no thermal motion (quantum zero-point energy noted as a preview)
- The Kelvin scale: T(K) = T(°C) + 273.15; why absolute scale is required for gas laws
- Thermal energy U_thermal: total internal energy of all molecules; distinguishes from T (intensive) and Q (transit)
- Heat Q vs. temperature T: heat is energy transferred due to ΔT; temperature is a state variable; heat is a process variable
- Thermal equilibrium and the Zeroth Law: if A is in equilibrium with C and B is in equilibrium with C, then A is in equilibrium with B — the foundation of thermometry
- Thermal expansion: linear: ΔL = αL₀ΔT; volume: ΔV = βV₀ΔT; β ≈ 3α for isotropic solids
  - Thermal stress: ΔT with constrained expansion → F = EAαΔT
  - Anomalous expansion of water: maximum density at 4°C; why ice floats
- Specific heat capacity: Q = mcΔT; c depends on material and phase
- Calorimetry: Q_lost = Q_gained; measuring specific heat

**Key vocabulary:** temperature, heat, thermal energy, zeroth law, thermal equilibrium, Kelvin scale, absolute zero, thermal expansion, specific heat, calorimetry, Boltzmann constant

**Common misconceptions:**
- "Temperature and heat are the same thing" — temperature is a state; heat is energy in transit; a large cold object can transfer more heat than a small hot one
- "Heat flows from objects with more heat to objects with less heat" — heat flows from higher temperature to lower temperature, regardless of total thermal energy content
- "Absolute zero means no energy" — it means no thermal (kinetic) energy; quantum zero-point energy remains

**Worked examples:**
1. Compute rms speed of nitrogen molecules at 20°C: v_rms = √(3k_BT/m) = √(3RT/M) ≈ 511 m/s
2. Thermal expansion: steel rail 10m at 20°C; find length at 50°C; find thermal stress if constrained (α_steel = 12×10⁻⁶/°C, E = 200 GPa)
3. Calorimetry: 200g copper (c=385 J/kg·K) at 80°C added to 500g water at 20°C; find equilibrium temperature

**What the student builds:**
`01-temperature-kinetic.html` — molecular speed and temperature visualizer. Controls: temperature T slider (50K–1000K), molecular mass selector (H₂, N₂, O₂, Ar). Display: 2D box with animated particles colored by speed; below the box, a histogram of particle speeds updating in real time; overlaid: the Maxwell-Boltzmann curve at the current T (preview of Chapter 3); v_rms, v_avg, v_mp computed and displayed as vertical lines on the histogram. Students raise T and watch the distribution broaden and shift right.

**Simulation physics:**
Initialize N=100 particles with speeds drawn from Maxwell-Boltzmann distribution at T. Color each particle by v/v_rms. Compute T_display = m⟨v²⟩/(3k_B). When slider changes T: rescale all velocities by √(T_new/T_old). Overlay the Maxwell-Boltzmann curve f(v) = 4π(m/2πk_BT)^(3/2) v² exp(-mv²/2k_BT).

**Key references for research agent:**
- Serway & Jewett, Chapter 19 (temperature) and Chapter 21 (kinetic theory)
- History of thermometry: Fahrenheit, Celsius, Kelvin; the absolute scale
- Anomalous expansion of water: physical explanation and ecological consequences
- Physics Education Research: temperature vs. heat misconceptions (the most studied misconception in thermodynamics PER)
- Boltzmann's constant: the 2019 SI redefinition (now exact: k_B = 1.380649×10⁻²³ J/K)

**Bridge to Chapter 2:** Temperature differences drive heat flow. Chapter 2 asks how — the three mechanisms of heat transfer (conduction, convection, radiation) and the rates at which they operate.

---

### CHAPTER 02 — Heat Transfer
**Filename:** `02-heat-transfer.md`
**Arc position:** Act One, Chapter 2

**One-line:** Students learn the three mechanisms of heat transfer — conduction, convection, and radiation — compute heat flow rates for each, and build a thermal conduction simulator showing temperature profiles through composite materials.

**Chapter description:**
Heat moves by three mechanisms: conduction (molecular collisions through a material), convection (bulk fluid motion carrying thermal energy), and radiation (electromagnetic waves emitted by all objects above absolute zero). This chapter gives the quantitative law for each and applies it to practical problems: insulation R-values, Newton's law of cooling, the Stefan-Boltzmann law. The simulation shows steady-state temperature profiles through a composite wall — a direct application of Fourier's law — and lets students vary material thicknesses and conductivities to minimize heat loss. This is the most engineering-relevant chapter in Act One.

**Core concepts:**
- Conduction: Fourier's law: P = kA(ΔT/Δx) = kA(T_H - T_C)/L
  - Thermal conductivity k: metals (high), insulators (low), air (very low)
  - Thermal resistance: R = L/(kA); analogous to electrical resistance
  - Composite walls in series: R_total = Σ Rᵢ; temperature profile piecewise linear
  - R-value in construction: R = L/k in SI; US customary units (ft²·°F·h/BTU)
- Convection: Newton's law of cooling: P = hA(T_surface - T_fluid)
  - Convection coefficient h: depends on geometry, fluid properties, flow velocity
  - Natural vs. forced convection; the boundary layer
  - Why wind makes you feel colder (increased h)
- Radiation: Stefan-Boltzmann law: P = εσAT⁴
  - σ = 5.67×10⁻⁸ W/(m²·K⁴); ε = emissivity (0 for perfect reflector, 1 for blackbody)
  - Net radiation: P_net = εσA(T⁴ - T_surr⁴)
  - Wien's displacement law: λ_max T = 2.898×10⁻³ m·K; peak emission wavelength
  - The greenhouse effect: atmosphere transparent to visible, absorbs IR
- Steady-state heat flow: when all three mechanisms are in balance; the concept of thermal equilibrium in engineering

**Key vocabulary:** conduction, convection, radiation, Fourier's law, thermal conductivity, thermal resistance, R-value, Newton's law of cooling, Stefan-Boltzmann law, emissivity, blackbody, Wien's law

**Common misconceptions:**
- "Warm clothes generate heat" — they insulate; they reduce heat loss, not generate heat
- "Dark objects are always hotter in sunlight" — dark objects absorb more and emit more; equilibrium temperature depends on both absorption and emission rates
- "Radiation requires a medium" — it is the only heat transfer mechanism that works in vacuum

**Worked examples:**
1. Composite wall: brick (k=0.8, L=20cm) + insulation (k=0.04, L=10cm) + drywall (k=0.17, L=1.5cm); find total R; find heat loss per m² at ΔT=25°C
2. Cooling coffee: T₀=90°C, T_room=20°C, h=15 W/m²K, A=0.02m²; find initial cooling rate; find time to reach 60°C (Newton's law of cooling ODE)
3. Blackbody radiation: human body (T=37°C, ε=0.97, A=1.8m²); find radiated power; find net radiation loss in a 20°C room

**What the student builds:**
`02-heat-conduction.html` — composite wall thermal conduction simulator. Controls: number of layers (1–4), each layer's material (selector: copper, glass, brick, wood, aerogel — sets k), thickness L, cross-sectional area A; T_hot and T_cold boundary temperatures. Display: wall cross-section with layers drawn to scale; temperature profile T(x) as a line across the wall — piecewise linear with slope ∝ 1/k; heat flux P computed and displayed; each layer's thermal resistance Rᵢ and total R_total shown. Students minimize heat loss by choosing optimal insulation layers.

**Simulation physics:**
Steady-state 1D conduction: T(x) piecewise linear in each layer. At each interface: T is continuous and P = kᵢA(dT/dx) is continuous. Compute interface temperatures from R-network: T_interface = T_hot - P·ΣRᵢ (up to that interface). P = (T_hot - T_cold)/R_total.

**Key references for research agent:**
- Serway & Jewett, Chapter 20
- Building insulation: R-values, energy codes, passive house standards
- Greenhouse effect: atmospheric absorption of IR; climate science connection
- Wien's law applications: stellar temperature from color; infrared thermometers
- Phase change materials: latent heat for thermal storage in buildings

**Bridge to Chapter 3:** Chapters 1–2 treated heat macroscopically. Chapter 3 goes microscopic: the ideal gas model gives a precise molecular picture of temperature, pressure, and the gas laws.

---

### CHAPTER 03 — The Ideal Gas and Kinetic Theory
**Filename:** `03-ideal-gas-kinetic-theory.md`
**Arc position:** Act One, Chapter 3

**One-line:** Students derive the ideal gas law from molecular collisions, understand the Maxwell-Boltzmann speed distribution, and build a distribution simulator that shows how temperature and molecular mass shape the distribution.

**Chapter description:**
This chapter makes the connection between the molecular picture and the macroscopic gas laws rigorous. The ideal gas law PV = nRT is derived from molecular mechanics — not postulated — by computing the pressure from the average momentum transfer of molecules to a wall. The Maxwell-Boltzmann speed distribution follows from statistical mechanics (introduced here informally; Chapter 8 gives the full derivation). The equipartition theorem — each quadratic degree of freedom carries ½k_BT of energy — connects molecular structure to heat capacity. The chapter ends with the limits of the ideal gas model: real gases, van der Waals corrections, and the conditions under which the ideal gas approximation breaks down. The simulation is the Maxwell-Boltzmann distribution explorer that students can heat, cool, and change the molecular mass.

**Core concepts:**
- Ideal gas model: point particles, elastic collisions, no intermolecular forces
- Deriving PV = nRT from molecular mechanics:
  - Pressure from momentum transfer: P = Nmv²_x/(3V) → P = (2/3)(N/V)(½mv²) = nk_BT/V
  - Ideal gas law: PV = Nk_BT = nRT where R = k_BNₐ = 8.314 J/(mol·K)
- Dalton's law of partial pressures: P_total = Σ Pᵢ for a mixture of ideal gases
- The Maxwell-Boltzmann speed distribution:
  - f(v) = 4π(m/2πk_BT)^(3/2) v² exp(-mv²/2k_BT)
  - Three characteristic speeds: v_mp = √(2k_BT/m), v_avg = √(8k_BT/πm), v_rms = √(3k_BT/m)
  - v_mp < v_avg < v_rms (asymmetric distribution)
  - Effect of temperature: distribution broadens and peak shifts right as T increases
  - Effect of molecular mass: heavier molecules have slower distribution (same T)
- The equipartition theorem: each quadratic degree of freedom has energy ½k_BT
  - Monatomic ideal gas: 3 translational DOF → U = (3/2)Nk_BT → Cᵥ = (3/2)R
  - Diatomic gas: 3 translational + 2 rotational → U = (5/2)Nk_BT → Cᵥ = (5/2)R
  - Vibrational modes: frozen out at low T (quantum effect — preview of QM volume)
- Real gases and van der Waals equation: (P + an²/V²)(V - nb) = nRT
  - a accounts for intermolecular attraction; b for finite molecular volume
  - When ideal gas approximation fails: high P, low T, near phase transition

**Key vocabulary:** ideal gas law, molar gas constant, Boltzmann constant, Maxwell-Boltzmann distribution, most probable speed, mean speed, rms speed, equipartition theorem, degrees of freedom, van der Waals equation

**Common misconceptions:**
- "All molecules in a gas at temperature T have the same speed" — they have a distribution; T determines the mean, not a single value
- "Heavier gases are hotter at the same T" — temperature depends on mean KE, not speed; heavier molecules are slower at the same T
- "The ideal gas law is always accurate" — it fails near phase transitions, at high pressure, and for polar molecules

**Worked examples:**
1. Compute v_mp, v_avg, v_rms for O₂ at 300K; verify the ordering v_mp < v_avg < v_rms
2. Equipartition: find Cᵥ and Cₚ for a monatomic ideal gas; for a diatomic ideal gas; compare to measured values for Ar and N₂
3. Van der Waals: CO₂ at 300K in 1L with n=1mol; find P from ideal gas law and van der Waals; compare (a=3.64 L²atm/mol², b=0.0427 L/mol)

**What the student builds:**
`03-maxwell-boltzmann.html` — Maxwell-Boltzmann distribution explorer. Controls: temperature T slider (100K–2000K), molecular mass selector (H₂=2, He=4, N₂=28, O₂=32, Ar=40, CO₂=44 g/mol). Display: f(v) curve as a D3 line chart with filled area; vertical lines for v_mp, v_avg, v_rms (labeled, color-coded); numerical values displayed; fraction of molecules above escape velocity (11.2 km/s) shown — explains atmospheric escape. Two-temperature mode: overlay two curves to compare T₁ and T₂ distributions.

**Simulation physics:**
f(v) = 4π(m/2πk_BT)^(3/2) v² exp(-mv²/2k_BT). Compute on a grid of v from 0 to 5v_rms. v_mp = √(2k_BT/m), v_avg = √(8k_BT/πm), v_rms = √(3k_BT/m). Fraction above v_esc: 1 - CDF(v_esc) computed numerically.

**Key references for research agent:**
- Serway & Jewett, Chapter 21
- Maxwell's 1860 derivation of the speed distribution; Boltzmann's generalization
- Atmospheric escape: why Mars lost its atmosphere (lower gravity, solar wind)
- Equipartition and the ultraviolet catastrophe: why classical physics failed for blackbody radiation (preview of QM)
- van der Waals: Nobel Prize 1910; modern equation of state research

**Bridge to Chapter 4:** The ideal gas is fully characterized. Chapter 4 introduces the first law of thermodynamics — the energy accounting that governs every process a gas undergoes.

---

### CHAPTER 04 — The First Law of Thermodynamics
**Filename:** `04-first-law.md`
**Arc position:** Act Two, Chapter 4

**One-line:** Students learn that internal energy, heat, and work are related by energy conservation — ΔU = Q - W — and apply the first law to compute energy changes in thermodynamic processes.

**Chapter description:**
The first law is conservation of energy applied to thermodynamic systems. It introduces three precisely defined quantities: internal energy U (a state function), heat Q (energy transferred due to ΔT), and work W (energy transferred by mechanical means). The sign convention (Q > 0 for heat added to system; W > 0 for work done by system) is established and used consistently. The key insight is that U is a state function — it depends only on the current state, not the path taken to reach it — while Q and W are path-dependent. This distinction sets up the difference between reversible and irreversible processes in Chapter 6. The simulation shows the first law enforced in real time: as heat is added and work is extracted, ΔU is computed and displayed, and energy conservation is verified.

**Core concepts:**
- Internal energy U: the total microscopic kinetic and potential energy of a system; a state function
- Heat Q: energy transferred due to a temperature difference; positive when added to system
- Work W: W = ∫P dV for a gas; positive when done by the system (expansion)
  - Graphical interpretation: W = area under the PV curve
- The first law: ΔU = Q - W (for a closed system)
  - For an ideal gas: ΔU = nCᵥΔT (U depends only on T for ideal gas)
- Quasi-static processes: slow enough that the system is always in equilibrium; PV curve is well-defined
- Specific processes (detailed in Chapter 5):
  - Isothermal (ΔT=0): ΔU=0 → Q=W
  - Adiabatic (Q=0): ΔU=-W
  - Isochoric (ΔV=0): W=0 → ΔU=Q
  - Isobaric (ΔP=0): W=PΔV
- State functions vs. path functions: U, T, P, V are state functions; Q and W are not
- Enthalpy: H = U + PV; ΔH = Q at constant pressure; relevant for chemistry

**Key vocabulary:** internal energy, state function, path function, quasi-static process, first law, isothermal, adiabatic, isochoric, isobaric, enthalpy

**Common misconceptions:**
- "Heat and work are stored in a system" — only internal energy is stored; Q and W describe energy in transit
- "A system that absorbs heat always increases in temperature" — if work is done simultaneously, ΔU can be zero (isothermal process)
- "Adiabatic means no temperature change" — it means no heat exchange; temperature changes as work is done

**Worked examples:**
1. 1 mol ideal gas absorbs 500 J of heat and does 200 J of work on the surroundings; find ΔU, ΔT (monatomic gas)
2. Isochoric process: 2 mol monatomic ideal gas heated from 300K to 400K at constant volume; find Q, W, ΔU
3. Isobaric process: same gas expanded at constant P=2 atm from V=10L to V=15L; find W, then ΔU if ΔT=120K

**What the student builds:**
`04-first-law.html` — first law energy balance visualizer. Controls: process type selector (isothermal/adiabatic/isochoric/isobaric), initial state (T₀, P₀, V₀), process parameter (final T or V or P), n moles, γ (monatomic=5/3, diatomic=7/5). Display: energy bar chart showing U, Q, W before and after the process; the first law equation displayed with numerical values; ΔU = Q - W verified. PV diagram panel showing the process as a curve (preview of Chapter 5). Students verify that ΔU = 0 for isothermal, Q = 0 for adiabatic.

**Simulation physics:**
For each process type, compute Q, W, ΔU from the ideal gas equations. Isothermal: W = nRT ln(V_f/V_i), ΔU=0, Q=W. Adiabatic: TV^(γ-1) = const; W = (P_iV_i - P_fV_f)/(γ-1), Q=0. Isochoric: W=0, Q=ΔU=nCᵥΔT. Isobaric: W=PΔV, Q=nCₚΔT, ΔU=nCᵥΔT. Display as animated bar transitions.

**Key references for research agent:**
- Serway & Jewett, Chapter 22
- History of the first law: Joule's experiments (1843–1850); Mayer's earlier proposal
- Joule's paddle-wheel experiment: mechanical equivalent of heat
- Enthalpy in chemistry: why chemists use H instead of U for constant-pressure reactions
- Physics Education Research: sign convention confusion in the first law (Q-W vs. Q+W)

**Bridge to Chapter 5:** The first law describes energy bookkeeping for a single process. Chapter 5 shows what PV diagrams look like for each process type and how thermodynamic cycles — sequences of processes that return to the start — extract work from heat.

---

### CHAPTER 05 — Thermodynamic Processes and PV Diagrams
**Filename:** `05-pv-diagrams-processes.md`
**Arc position:** Act Two, Chapter 5

**One-line:** Students learn to read and draw PV diagrams for isothermal, adiabatic, isochoric, and isobaric processes, compute work as the area under the curve, and build an animated PV diagram simulator showing all four process types.

**Chapter description:**
The PV diagram is the central visual tool of classical thermodynamics. It encodes the complete state of an ideal gas in a single point and represents every quasi-static process as a curve. This chapter systematizes all four standard process types on the PV diagram, derives the equations for each curve, and introduces the concept of a thermodynamic cycle — a closed path on the PV diagram that returns the gas to its initial state. The work done in a cycle equals the enclosed area. The Otto cycle (idealized gasoline engine) and the refrigeration cycle are introduced as examples. The simulation animates all four process types simultaneously, making their different PV curve shapes immediately distinguishable.

**Core concepts:**
- PV diagram basics: state = point; process = curve; work = area under curve; cycle = closed path
- Isothermal process (T = const): PV = const (hyperbola); W = nRT ln(V_f/V_i)
  - Requires slow process in contact with a thermal reservoir
- Isochoric process (V = const): vertical line; W = 0; Q = ΔU = nCᵥΔT
- Isobaric process (P = const): horizontal line; W = PΔV; Q = nCₚΔT
- Adiabatic process (Q = 0): PV^γ = const (steeper than isothermal); TV^(γ-1) = const
  - γ = Cₚ/Cᵥ = 5/3 (monatomic), 7/5 (diatomic)
  - Adiabatic curves are always steeper than isothermal curves through the same point — key visual
- Work in a cycle: W_net = area enclosed by the cycle on the PV diagram; positive for clockwise (engine), negative for counterclockwise (refrigerator)
- The Otto cycle: two adiabatic + two isochoric processes; model for gasoline engine
  - Compression ratio r = V_max/V_min; efficiency η = 1 - r^(1-γ)
- The refrigeration cycle (preview): counterclockwise on PV diagram; work input moves heat from cold to hot

**Key vocabulary:** PV diagram, isothermal, adiabatic, isochoric, isobaric, compression ratio, Otto cycle, thermodynamic cycle, net work, heat engine

**Common misconceptions:**
- "Isothermal and adiabatic curves look the same" — both are curves on the PV diagram, but adiabatic is always steeper (larger magnitude slope) at any point
- "The area under any curve is the heat exchanged" — it is always the work done; heat requires applying the first law separately
- "A cycle does net work only if it's a heat engine" — any closed clockwise cycle does net work; the question is where the energy comes from

**Worked examples:**
1. Draw the four process types starting from the same state (P=2atm, V=10L, T=243K); compute W for each to a final volume of 20L
2. Otto cycle: r=8, γ=1.4, T₁=300K; compute T at all four states; net work per cycle per mole; efficiency
3. Refrigeration cycle: clockwise vs counterclockwise — same shape, opposite sign of W_net; explain physically

**What the student builds:**
`05-pv-diagram.html` — animated PV diagram process simulator. Controls: initial state (P₀, V₀, T₀), process type selector (all four), final state parameter slider, γ selector (5/3 or 7/5). Display: PV axes with isothermal curves (hyperbolas) drawn as background reference grid; the chosen process animated as a moving point tracing the curve; work computed as shaded area under the curve, updating in real time; Q and ΔU displayed alongside. Cycle mode: chain up to 4 processes; show total net work = enclosed area; Otto cycle preset.

**Simulation physics:**
Isothermal: P = nRT₀/V (hyperbola). Adiabatic: P = P₀(V₀/V)^γ. Isochoric: vertical line. Isobaric: horizontal line. Animate by stepping V (or P) from initial to final, computing the current P from the process equation, updating the shaded area incrementally.

**Key references for research agent:**
- Serway & Jewett, Chapter 22
- History of the steam engine and thermodynamic cycles: Watt, Carnot
- Otto cycle: Nikolaus Otto's engine (1876); modern engine efficiency
- Diesel cycle: comparison to Otto cycle; why diesel is more efficient at high compression
- Adiabatic lapse rate in atmosphere: why temperature drops with altitude

**Bridge to Chapter 6:** PV diagrams show what processes are possible. Chapter 6 asks which are preferred — and why heat always flows from hot to cold, never the reverse. The second law sets the direction.

---

### CHAPTER 06 — The Second Law and Heat Engines
**Filename:** `06-second-law-heat-engines.md`
**Arc position:** Act Two, Chapter 6

**One-line:** Students learn that the second law establishes the direction of thermodynamic processes, derive the Carnot efficiency as the maximum possible efficiency for any heat engine, and build a Carnot cycle simulator showing where irreversibility losses occur.

**Chapter description:**
The second law is the deepest law in physics. It is the only fundamental law that distinguishes past from future — the arrow of time. This chapter introduces the second law through its most practical consequence: no heat engine can convert all input heat to work. The Carnot cycle is the reversible engine — the theoretical upper bound. Its efficiency η_Carnot = 1 - T_C/T_H depends only on the temperatures of the reservoirs, not on the working substance. Real engines are always less efficient because real processes are irreversible. The chapter introduces the Clausius statement and Kelvin-Planck statement of the second law, shows their equivalence, and derives the Carnot efficiency from reversibility arguments. The simulation shows the Carnot cycle on a PV and TS diagram simultaneously.

**Core concepts:**
- The second law: two equivalent statements
  - Clausius: heat cannot spontaneously flow from cold to hot
  - Kelvin-Planck: no engine operating in a cycle can convert all heat to work
- Heat engines: take in heat Q_H from a hot reservoir, do work W, reject heat Q_C to a cold reservoir
  - First law for a cycle: W = Q_H - Q_C (ΔU=0 for complete cycle)
  - Efficiency: η = W/Q_H = 1 - Q_C/Q_H
- Reversible vs. irreversible processes: reversible = quasi-static + no friction/dissipation; irreversible = everything real
- The Carnot cycle: two reversible isothermals + two reversible adiabatics
  - Carnot efficiency: η_Carnot = 1 - T_C/T_H (temperatures in Kelvin!)
  - Carnot theorem: no engine can exceed Carnot efficiency operating between the same reservoirs
- Refrigerators and heat pumps: reversed heat engines; work input moves heat from cold to hot
  - COP (refrigerator): COP = Q_C/W = T_C/(T_H - T_C) at Carnot limit
  - COP (heat pump): COP = Q_H/W = T_H/(T_H - T_C) at Carnot limit
- The TS diagram: temperature vs. entropy; area = heat exchanged; Carnot cycle is a rectangle
- Sources of irreversibility: friction, heat transfer across finite ΔT, free expansion, mixing

**Key vocabulary:** second law, heat engine, efficiency, Carnot cycle, Carnot efficiency, reversible process, irreversible process, refrigerator, heat pump, COP, TS diagram

**Common misconceptions:**
- "More efficient engines just need better engineering" — the Carnot limit is fundamental; no amount of engineering overcomes it
- "Refrigerators violate the second law by making cold regions colder" — they require work input; the total entropy of the universe still increases
- "100% efficiency is impossible because of friction" — it is impossible even with no friction; the Carnot limit is more fundamental

**Worked examples:**
1. Carnot engine: T_H=600K, T_C=300K; find η_Carnot; if Q_H=1000J per cycle, find W and Q_C
2. Real engine: same temperatures, η=0.35; find how much extra heat is rejected compared to Carnot; find entropy generated per cycle
3. Heat pump: T_H=20°C (inside), T_C=0°C (outside); find Carnot COP; if actual COP=3, find power needed to heat 5kW

**What the student builds:**
`06-carnot-cycle.html` — Carnot cycle simulator with irreversibility. Controls: T_H and T_C reservoir temperature sliders; efficiency slider (from η_Carnot down to lower values to model irreversibility); Q_H input. Display: split screen — left: PV diagram with the four Carnot steps animated; right: TS diagram (rectangle for reversible Carnot); energy flow Sankey diagram showing Q_H, W, Q_C as flow widths; η_Carnot computed and displayed as the upper bound; actual η shown; entropy generated by irreversibility shown in red.

**Simulation physics:**
Carnot PV cycle: two isothermals (T=T_H and T=T_C) connected by two adiabatics. Isothermal: PV = nRT_H (or T_C). Adiabatic: PV^γ = const. Compute intersection points. W_net = area enclosed (computed by integration). η_Carnot = 1 - T_C/T_H. Irreversible case: reduce W by (1-η/η_Carnot) factor; show extra Q_C.

**Key references for research agent:**
- Serway & Jewett, Chapter 22
- Carnot's original paper (1824): *Réflexions sur la puissance motrice du feu*
- History: Carnot died at 36; his work was largely ignored until Clausius and Kelvin
- Real engine efficiency: gasoline engines ~25–30%; diesel ~40–45%; combined cycle gas turbines ~60%
- Heat pumps: why heat pumps are more efficient than resistance heating; ground-source heat pumps

**Bridge to Chapter 7:** The Carnot cycle introduces a new quantity that is conserved in reversible processes and increases in irreversible ones. Chapter 7 names and defines that quantity: entropy.

---

### CHAPTER 07 — Entropy
**Filename:** `07-entropy.md`
**Arc position:** Act Two, Chapter 7

**One-line:** Students learn to compute entropy changes for any thermodynamic process, understand entropy as a measure of disorder and available microstates, and build an entropy simulator that counts microstates and shows the second law emerging from probability.

**Chapter description:**
Entropy is the most profound concept in thermodynamics and the most commonly misunderstood. This chapter develops entropy from two directions simultaneously: the macroscopic (Clausius) definition dS = δQ_rev/T, and the microscopic (Boltzmann) definition S = k_B ln Ω. They give the same answer — and showing that they agree is the deepest result in classical thermodynamics. The chapter computes entropy changes for every standard process, establishes the entropy form of the second law (ΔS_universe ≥ 0), and shows entropy as a measure of the number of available microstates. The simulation directly counts microstates — showing the second law as a statement about probability, not absolute prohibition.

**Core concepts:**
- Clausius definition of entropy: dS = δQ_rev/T; ΔS = ∫δQ_rev/T
  - Units: J/K
  - State function: ΔS depends only on initial and final states, not the path (for reversible processes)
- Entropy changes for standard processes:
  - Isothermal: ΔS = Q/T = nRT ln(V_f/V_i)/T = nR ln(V_f/V_i)
  - Isochoric: ΔS = nCᵥ ln(T_f/T_i)
  - Isobaric: ΔS = nCₚ ln(T_f/T_i)
  - Adiabatic reversible: ΔS = 0 (isentropic)
  - Free expansion (irreversible): ΔS = nR ln(V_f/V_i) but W=0, Q=0 (not via Clausius directly)
- Second law in entropy form: ΔS_universe = ΔS_system + ΔS_surroundings ≥ 0
  - Equality for reversible; strict inequality for irreversible
- Boltzmann's entropy: S = k_B ln Ω
  - Ω = number of microstates consistent with the macrostate
  - Why Ω is always increasing: overwhelmingly more disordered than ordered states
  - Boltzmann's tombstone equation
- Simple microstate counting: N particles in two halves of a box; Ω = 2^N; entropy of mixing
- The third law: S → 0 as T → 0; absolute entropy; why perfect crystals at 0K have S=0
- Entropy and irreversibility: free expansion, heat conduction, mixing — all increase entropy

**Key vocabulary:** entropy, Clausius definition, Boltzmann entropy, microstate, macrostate, second law (entropy form), third law, irreversibility, entropy of mixing, isentropic

**Common misconceptions:**
- "Entropy is disorder" — this is a useful analogy but not a definition; entropy is log of the number of microstates; disorder is a consequence, not a definition
- "Entropy always increases everywhere" — only the total entropy of the universe increases; local entropy can decrease (refrigerators, living organisms) at the cost of increasing entropy elsewhere
- "Reversible processes don't change entropy" — they don't change the entropy of the universe; entropy is transferred from system to surroundings without net creation

**Worked examples:**
1. Free expansion: 1 mol ideal gas expands into vacuum, doubling volume; find ΔS. Why can't we use dS = δQ/T directly? Use S = k_B ln Ω or entropy of isothermal expansion.
2. Heat conduction: 100J flows from T_H=400K to T_C=300K; find ΔS_H, ΔS_C, ΔS_universe; verify ΔS_universe > 0
3. Microstate counting: 4 particles distributed between two halves of a box; enumerate all microstates; find most probable macrostate; compute S for each macrostate

**What the student builds:**
`07-entropy-microstates.html` — entropy and microstate simulator. Controls: N particles (slider 4–20), simulation mode (gas expansion / heat transfer). Display: box divided into two halves; N dots that hop randomly between halves at each time step (equal probability); histogram of number in left half showing convergence to N/2; entropy S = k_B ln(N!/(n!(N-n)!)) computed and displayed; running maximum entropy shown. Students watch: starting with all particles in the left half, the system evolves to the most probable state and stays there. The second law visualized as probability.

**Simulation physics:**
At each time step: each particle hops to the other half with probability p=0.5. Count n_left. Compute Ω(n_left) = N!/(n_left!(N-n_left)!) using log-factorials (Stirling for large N). S = k_B ln Ω. Animate the histogram of n_left over time; overlay the theoretical binomial distribution.

**Key references for research agent:**
- Serway & Jewett, Chapter 22
- Boltzmann's biography: the tragic story; his tombstone in Vienna
- The third law: Nernst (1906); implications for cooling toward absolute zero
- Entropy in information theory: Shannon entropy H = -Σ pᵢ log pᵢ (preview of Chapter 10)
- Gibbs paradox: entropy of mixing identical gases; resolution via quantum indistinguishability

**Bridge to Chapter 8:** The microstate counting is the beginning of statistical mechanics. Chapter 8 makes it systematic — deriving the Boltzmann distribution and the partition function that connects microscopic physics to macroscopic thermodynamics.

---

### CHAPTER 08 — Statistical Mechanics
**Filename:** `08-statistical-mechanics.md`
**Arc position:** Act Three, Chapter 8

**One-line:** Students learn how the Boltzmann distribution emerges from maximizing entropy subject to energy conservation, compute partition functions for simple systems, and build a two-level system simulator showing the Boltzmann distribution in action.

**Chapter description:**
Statistical mechanics is the bridge between microscopic physics and macroscopic thermodynamics. This chapter derives the Boltzmann distribution — the probability of finding a system in a state of energy E is proportional to e^(-E/k_BT) — from the maximum entropy principle. The partition function Z = Σ e^(-Eᵢ/k_BT) encodes all thermodynamic information. Average energy, heat capacity, and entropy are all computed from Z. The Maxwell-Boltzmann speed distribution (Chapter 3) is re-derived as a special case. The chapter ends with quantum statistical mechanics as a preview: Fermi-Dirac and Bose-Einstein distributions, which replace Boltzmann statistics when quantum indistinguishability matters. This is the bridge chapter to the QM volume.

**Core concepts:**
- The fundamental postulate: all microstates of equal energy are equally probable
- Derivation of the Boltzmann distribution: maximize entropy S = -k_B Σ pᵢ ln pᵢ subject to Σpᵢ=1 and Σpᵢ Eᵢ = ⟨E⟩
  - Result: pᵢ = e^(-Eᵢ/k_BT) / Z where Z = Σⱼ e^(-Eⱼ/k_BT)
- The partition function Z: Z = Σᵢ e^(-Eᵢ/k_BT) = Σᵢ gᵢ e^(-Eᵢ/k_BT) with degeneracy gᵢ
- Thermodynamic quantities from Z:
  - Average energy: ⟨E⟩ = -∂(ln Z)/∂β where β = 1/k_BT
  - Helmholtz free energy: F = -k_BT ln Z
  - Entropy: S = -∂F/∂T = k_B(ln Z + βU)
  - Heat capacity: C = ∂⟨E⟩/∂T
- Two-level system (spin-1/2 in magnetic field): E = ±μB; Z = 2cosh(μB/k_BT)
  - Heat capacity shows a Schottky anomaly: peak at k_BT ~ ΔE
- The classical limit: when k_BT >> ΔE, quantum systems behave classically
- Maxwell-Boltzmann as a special case: translational energy of molecules; ideal gas derived
- Quantum statistics preview:
  - Fermi-Dirac distribution: f(E) = 1/(e^((E-μ)/k_BT) + 1); for fermions (electrons, protons)
  - Bose-Einstein distribution: f(E) = 1/(e^((E-μ)/k_BT) - 1); for bosons (photons, He-4 atoms)
  - Why quantum statistics matter: metals, semiconductors, Bose-Einstein condensation
  - Connection to QM volume: the partition function in QM is the trace of e^(-βĤ)

**Key vocabulary:** Boltzmann distribution, partition function, Helmholtz free energy, Schottky anomaly, classical limit, Fermi-Dirac distribution, Bose-Einstein distribution, quantum statistics, degeneracy

**Common misconceptions:**
- "The Boltzmann distribution says high-energy states are never occupied" — they are occupied with probability e^(-E/k_BT); they become negligible only when E >> k_BT
- "Statistical mechanics is an approximation" — for large N, it gives exact thermodynamic results; the fluctuations scale as 1/√N

**Worked examples:**
1. Two-level system: energy gap ΔE = 0.01 eV; find occupation probabilities at T=100K, 300K, 1000K; find heat capacity peak temperature
2. Harmonic oscillator: Z = 1/(1-e^{-hν/k_BT}); find ⟨E⟩; show equipartition ⟨E⟩→k_BT for k_BT >> hν and quantum suppression for k_BT << hν
3. Ideal gas partition function: Z_1 = V(2πmk_BT/h²)^(3/2) (translational); show that ⟨E⟩ = (3/2)k_BT recovers equipartition

**What the student builds:**
`08-boltzmann-distribution.html` — Boltzmann distribution and partition function simulator. Controls: number of energy levels N_levels (2–10), energy spacing ΔE (in units of k_B), temperature T slider. Display: energy level diagram with occupation probability shown as bar width at each level (proportional to e^(-Eᵢ/k_BT)/Z); Z computed and displayed; ⟨E⟩ vs. T curve; heat capacity C = d⟨E⟩/dT vs. T showing Schottky peak for two-level system. Students watch the higher levels populate as T increases; watch the heat capacity peak and fall.

**Simulation physics:**
Eᵢ = i·ΔE for i=0,...,N-1. pᵢ = e^(-Eᵢ/k_BT) / Z. Z = Σ e^(-Eᵢ/k_BT). ⟨E⟩ = Σ Eᵢpᵢ. C = (⟨E²⟩ - ⟨E⟩²)/(k_BT²) (fluctuation formula). Compute all vs. T on a grid; display selected-T occupation and the full ⟨E⟩(T) and C(T) curves.

**Key references for research agent:**
- Kittel & Kroemer, *Thermal Physics* — the standard statistical mechanics text at this level
- Mandl, *Statistical Physics* — accessible undergraduate treatment
- History: Boltzmann vs. Mach and Ostwald; the atomism debate
- Bose-Einstein condensation: first experimental realization (Cornell, Wieman, Ketterle — Nobel 2001)
- Fermi-Dirac statistics: electrons in metals; semiconductor physics

**Bridge to Chapter 9:** Statistical mechanics explains why thermodynamics works. Chapter 9 applies both to real systems — power plants, refrigerators, engines — where irreversibility is not a theoretical concern but a design parameter.

---

### CHAPTER 09 — Thermodynamics in the Real World
**Filename:** `09-thermodynamics-real-world.md`
**Arc position:** Act Three, Chapter 9

**One-line:** Students apply thermodynamic laws to real heat engines, refrigerators, and power plants — computing actual vs. Carnot efficiencies, identifying irreversibility sources, and building a heat engine efficiency explorer.

**Chapter description:**
This chapter is where thermodynamic theory meets engineering reality. Real heat engines — steam turbines, internal combustion engines, jet engines — operate well below their Carnot limits because every real process is irreversible. The chapter quantifies how much efficiency is lost to each source of irreversibility: heat transfer across finite temperature differences, friction, turbulence, incomplete combustion. The Rankine cycle (steam power plants), Brayton cycle (gas turbines, jet engines), and vapor-compression refrigeration cycle are analyzed as case studies. The chapter also addresses climate-relevant applications: the thermodynamics of heat pumps for building heating, the efficiency of data centers as thermal machines, and the thermodynamics of the Earth's climate system.

**Core concepts:**
- The Rankine cycle: the standard steam power plant cycle
  - Four processes: isothermal boiling (Q_H in), adiabatic expansion through turbine (W out), isothermal condensation (Q_C out), adiabatic compression through pump (W in)
  - Efficiency: η = W_net/Q_H; Carnot limit T_C/T_H for typical plants: ~40% Carnot → ~35% actual
  - Superheat and reheat: practical modifications to improve efficiency
- The Brayton cycle: gas turbines and jet engines
  - Four processes: adiabatic compression, isobaric combustion, adiabatic expansion, isobaric exhaust
  - Efficiency: η = 1 - r^((1-γ)/γ) where r is the pressure ratio
- Vapor-compression refrigeration: the standard refrigerator cycle
  - Refrigerant properties: why R-134a replaced R-12 (ozone depletion)
  - COP in practice: household refrigerators COP~2–4 vs. Carnot COP~10–15
- Sources of irreversibility in real devices:
  - Heat exchange across finite ΔT: entropy generation rate = Q·(1/T_C - 1/T_H)
  - Turbine and compressor isentropic efficiency: actual vs. ideal
  - Pressure drop in heat exchangers
- Combined heat and power (CHP): using waste heat; overall efficiency up to 80–90%
- Data centers as thermal machines: power usage effectiveness (PUE); cooling as thermodynamics
- Climate thermodynamics: the Earth as a heat engine; the atmosphere as a fluid subject to thermodynamic laws; why weather is irreversible

**Key vocabulary:** Rankine cycle, Brayton cycle, vapor-compression refrigeration, isentropic efficiency, combined heat and power, PUE, irreversibility rate, exergy

**Worked examples:**
1. Rankine cycle: steam at T_H=600°C, condenser at T_C=40°C; η_Carnot = 65%; actual η=33%; find entropy generated per kJ of heat input
2. Jet engine: pressure ratio r=20, T_inlet=250K, γ=1.4; find η_Brayton; find T after compression; find T after combustion for T_max=1400K
3. Household refrigerator: T_freezer=-18°C, T_room=25°C; η_Carnot COP=5.6; actual COP=2.5; find electricity cost to remove 1 kWh of heat

**What the student builds:**
`09-heat-engine-explorer.html` — heat engine efficiency explorer. Controls: engine type selector (Carnot, Otto, Rankine simplified, Brayton); T_H and T_C sliders; compression/pressure ratio; irreversibility slider (0=ideal, 1=maximum losses). Display: cycle on PV diagram (animated); Sankey energy flow diagram showing Q_H, W, Q_C as flow widths; η_Carnot shown as the theoretical ceiling; actual η shown below it; entropy generation rate displayed; interactive comparison of two engines side-by-side.

**Simulation physics:**
For each cycle type: compute Q_H, W, Q_C from the thermodynamic cycle equations. η = W/Q_H. For irreversibility: reduce η by factor (1 - irreversibility × (1 - η_Carnot)). Entropy generation: Ṡ_gen = W_lost/T = Q_H(η_Carnot - η)/T_H. Render as Sankey: line widths proportional to Q_H, W, Q_C.

**Key references for research agent:**
- Çengel & Boles, *Thermodynamics: An Engineering Approach* — the standard engineering thermodynamics text
- Real steam plant efficiency: combined cycle plants reaching 60%+ efficiency
- Refrigerant history: CFC phase-out, HFC regulation, natural refrigerants
- Data center thermodynamics: Google/Microsoft PUE data; free cooling
- Climate system thermodynamics: the Earth's energy budget; Lorenz energy cycle

**Bridge to Chapter 10:** Real engines are inefficient because of irreversibility — entropy generation. Chapter 10 asks the deepest question: why does irreversibility exist at all? The answer connects entropy to information, computation, and quantum mechanics.

---

### CHAPTER 10 — Capstone: Irreversibility, Information, and the Quantum
**Filename:** `10-capstone-entropy-information-quantum.md`
**Arc position:** Act Three, Chapter 10

**One-line:** Students trace the connections between thermodynamic entropy, information entropy, Maxwell's demon, the Landauer principle, and von Neumann entropy — building a Maxwell's demon simulator and arriving at the threshold of quantum statistical mechanics.

**Chapter description:**
The capstone chapter asks the question the book has been building toward: why is the second law true? The answer runs through one of the most productive thought experiments in physics. Maxwell's demon appears to violate the second law by sorting molecules — until Szilard (1929) and Landauer (1961) showed that erasing the demon's memory necessarily generates entropy. Information is physical. The Landauer principle (erasing one bit of information generates at least k_B T ln 2 of heat) connects thermodynamic entropy to Shannon's information entropy. This connection is not an analogy — they are the same quantity, measured in different units. The chapter then takes one step further: quantum mechanics replaces the classical microstate count with the density matrix, and Boltzmann entropy S = k_B ln Ω becomes von Neumann entropy S = -k_B Tr(ρ ln ρ). The quantum partition function Z = Tr(e^{-βĤ}) generalizes the classical sum. This is the bridge to the QM volume.

**Core concepts:**

**Part 1 — Maxwell's Demon and the Landauer Principle:**
- Maxwell's demon (1867): a thought experiment; a demon sorts fast and slow molecules; apparently decreases entropy without doing work; seems to violate the second law
- Szilard's engine (1929): a single-molecule gas; the demon measures which side the molecule is on; extracts k_BT ln 2 of work per measurement; where does the entropy come from?
- Bennett's resolution (1982): the demon's memory accumulates information; erasing the memory generates entropy; the second law is saved
- Landauer's principle (1961): erasing one bit of information requires dissipating at least k_BT ln 2 of heat; the minimum heat generated per bit erased at temperature T
  - k_BT ln 2 at 300K ≈ 2.87×10⁻²¹ J per bit; modern computers dissipate ~10⁶× more per operation
  - Landauer limit as the fundamental thermodynamic cost of computation
- Reversible computation: can computation be done without energy cost? Reversible logic gates; quantum computation as fundamentally reversible

**Part 2 — Shannon Entropy and Thermodynamic Entropy:**
- Shannon entropy: H = -Σ pᵢ log₂ pᵢ (in bits); a measure of uncertainty or information content
- The connection: S_Boltzmann = k_B ln Ω = k_B ln 2 × H (when all states equally probable)
- In general: S = -k_B Σ pᵢ ln pᵢ (Gibbs entropy); identical in form to Shannon entropy
- Entropy as missing information: the entropy of a system is the number of bits of information needed to specify its microstate, given knowledge of its macrostate
- Physical consequences: why information has thermodynamic cost; why the universe's entropy is increasing as information is erased

**Part 3 — Von Neumann Entropy and Quantum Statistical Mechanics:**
- The density matrix ρ: generalizes the pure state |ψ⟩ to mixed states; ρ = Σ pᵢ |ψᵢ⟩⟨ψᵢ|
  - Pure state: ρ² = ρ; Tr(ρ²) = 1
  - Mixed state: Tr(ρ²) < 1; represents classical uncertainty about the quantum state
- Von Neumann entropy: S_vN = -k_B Tr(ρ ln ρ) = -k_B Σ λᵢ ln λᵢ (λᵢ = eigenvalues of ρ)
  - Reduces to Boltzmann entropy for classical probability distributions
  - Pure states have S_vN = 0; maximally mixed state has maximum entropy
- Quantum partition function: Z = Tr(e^{-βĤ}) where Ĥ is the Hamiltonian operator
  - Recovers classical Z = Σ e^{-βEᵢ} in the energy eigenbasis
  - Thermodynamic quantities: F = -k_BT ln Z; U = -∂ ln Z/∂β; S = -∂F/∂T
- Quantum corrections to classical thermodynamics:
  - Specific heat of solids: Einstein model (1907), Debye model (1912) — quantum oscillators, not classical
  - Electronic heat capacity of metals: Fermi-Dirac suppression at T << T_F
  - Photon gas: Planck distribution derived from Bose-Einstein statistics
- Entanglement entropy: entropy of a subsystem of an entangled state; S > 0 even for a pure state
  - Connection to quantum information and the next volume

**Key vocabulary:** Maxwell's demon, Szilard engine, Landauer principle, Shannon entropy, Gibbs entropy, density matrix, von Neumann entropy, quantum partition function, entanglement entropy, reversible computation

**Worked examples:**
1. Landauer principle: a hard drive erases 1 TB of data at T=300K; find the minimum heat generated; compare to actual heat generated by a real drive
2. Von Neumann entropy: compute S_vN for a maximally mixed qubit (ρ = I/2); for a pure state (ρ = |0⟩⟨0|); for a partially mixed state ρ = 0.7|0⟩⟨0| + 0.3|1⟩⟨1|
3. Einstein solid: N oscillators of frequency ν; Z = (1/(1-e^{-hν/k_BT}))^N; find ⟨E⟩; show that Cᵥ → 3Nk_B (Dulong-Petit) for k_BT >> hν and → 0 for k_BT << hν

**What the student builds:**
`10-maxwells-demon.html` — Maxwell's demon simulator. Display: box divided into two halves with a door; N=40 particles colored by speed (blue=slow, red=fast); a "demon" icon at the door. Modes: (1) Free mode — door always open; Maxwell-Boltzmann distribution maintained; entropy computed. (2) Demon mode — door opens only when a fast particle approaches from left or slow particle from right; after M=50 measurements, the left side becomes hotter; entropy of gas decreases; demon's memory fills up (shown as a memory register of M bits); (3) Erasure mode — erase the demon's memory; show that heat generated by erasure ≥ k_BT ln 2 per bit; total entropy of universe increases; second law restored. Students see the demon work, then fail when erasure is included.

**Simulation physics:**
Particles: same as Chapter 0 simulation. Demon: checks each particle approaching the door; if fast (v > v_rms) and moving left→right: open door; if slow and moving right→left: open door; otherwise: closed. Track memory register (array of bits). Compute gas entropy from Maxwell-Boltzmann fit to current speed distribution. Erasure: heat generated = k_BT ln(2) × (number of bits erased). Display entropy of gas, entropy of demon's memory, total entropy; show total always increasing after erasure.

**Final project options:** (A) Complete annotated simulation gallery for all 10 chapters with written exploration notes; (B) Thermodynamic analysis of a real device (heat pump, data center, internal combustion engine) — compute actual vs. Carnot efficiency, identify irreversibility sources, estimate entropy generation rate; (C) A simulation-based exploration of one quantum thermodynamics topic: Einstein solid heat capacity, electronic heat capacity of a metal, or photon gas (Planck distribution), with written derivation connecting it to the classical chapters.

**Key references for research agent:**
- Maxwell's demon: Leff & Rex, *Maxwell's Demon 2* (comprehensive anthology)
- Szilard's 1929 paper: "On the Decrease of Entropy in a Thermodynamic System by the Intervention of Intelligent Beings"
- Landauer's 1961 paper: "Irreversibility and Heat Generation in the Computing Process"
- Bennett's 1982 resolution: "The Thermodynamics of Computation — A Review"
- Experimental verification of Landauer's principle: Bérut et al., *Nature* (2012)
- Shannon's 1948 paper: "A Mathematical Theory of Communication"
- Von Neumann entropy: von Neumann, *Mathematical Foundations of Quantum Mechanics* (1932)
- Quantum thermodynamics: recent review — Vinjanampathy & Anders (2016)
- Entanglement entropy: Eisert, Cramer & Plenio (2010) review

---

## Assessment Structure

| Component | Chapters | Notes |
|-----------|---------|-------|
| Weekly simulation builds (9 × 15 pts) | 2–10 | One simulation per chapter; graded on correctness and exploration documentation |
| Chapter 0 setup (25 pts) | 0 | CLAUDE.md, DESIGN.md, PROJECT.md present and correct |
| Act One checkpoint: energy and temperature (75 pts) | 1–3 | Maxwell-Boltzmann problems, heat transfer, ideal gas law |
| Act Two checkpoint: the laws (75 pts) | 4–7 | First law, PV diagrams, Carnot efficiency, entropy calculations |
| Simulation exploration reports (3 × 25 pts) | 3, 6, 9 | Short written report: what did you change, what did you observe, what does it mean |
| Final exam: statistical mechanics and information (100 pts) | 8–10 | Boltzmann distribution, partition function, Landauer principle, von Neumann entropy |
| Final project (150 pts) | 10 | See Chapter 10 options above |

---

## Simulation Stack Reference

All simulations use D3 v7, single HTML files with inline CSS and JS.

**Standard thermodynamics simulation elements defined in CLAUDE.md:**
- SVG canvas: 700×500px for particle simulations; 700×400px for PV diagrams and distribution plots
- Particle simulation: requestAnimationFrame loop; elastic collision detection; periodic boundary or wall reflection
- PV diagram: D3 line chart with axes P (y) and V (x); process curves computed analytically; shaded area for work
- Distribution plots: D3 area charts with overlaid analytical curves
- Energy flow Sankey: horizontal flow diagram with bar widths proportional to Q_H, W, Q_C
- Physics constants (defined once in CLAUDE.md): k_B=1.38e-23, R=8.314, N_A=6.022e23, h=6.626e-34, σ=5.67e-8
- Dark mode: `prefers-color-scheme` media query

---

## Consolidation Map
*(For research agent: how existing chapter files map to this TIKTOC)*

| Existing file | Maps to | Notes |
|--------------|---------|-------|
| `01-fluid-statics.md` | Dropped | Fluids belongs to mechanics volume; buoyancy appears as a thermal-density note in Ch01 only |
| `02-thermal-energy-heat-and-work.md` | Ch01 + Ch04 | Temperature/thermal energy → Ch01; heat and work → Ch04 |
| `03-fluid-dynamics-and-its-biological-and-medical-applications.md` | Dropped | Fluids belongs to mechanics volume |
| `04-thermodynamics.md` | Ch04 + Ch05 + Ch06 | Split into first law, PV diagrams, second law |
| `05-temperature-kinetic-theory-and-the-gas-laws.md` | Ch01 + Ch03 | Temperature → Ch01; kinetic theory and gas laws → Ch03 |
| `06-heat-and-heat-transfer-methods.md` | Ch02 | Direct source for heat transfer chapter |
| `07-thermodynamics.md` | Ch04 + Ch05 + Ch06 + Ch07 | Second parallel thermodynamics draft; merge with Ch04 source |

*New chapters with no existing source: Ch08 (Statistical Mechanics), Ch09 (Real World), Ch10 (Capstone)*

---

*TIKTOC.md v1.0 — 11 chapters (Chapter 0 + Chapters 1–10)*
*Ready for: research gathering (Cowork research prompt), chapter drafting*
*Repo: physics-plus-one-thermodynamics*
*Two fluids chapters dropped; thermodynamics parallel drafts merged; three new chapters added*
*Capstone bridges to Quantum Mechanics volume via von Neumann entropy and quantum partition function*
