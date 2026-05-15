# Chapter 5 — Thermodynamic Processes and PV Diagrams

*Four canonical paths, the area under the curve, and the first thermodynamic cycle.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Draw isothermal, isochoric, isobaric, and adiabatic processes on a PV diagram with correct shapes.
2. **(Apply)** Compute work for each process type, recognizing $W = \int P\,dV$ as the area under the curve.
3. **(Analyze)** Identify which process curve is steeper at a given point on a PV diagram (adiabatic vs. isothermal).
4. **(Apply)** Compute net work for a thermodynamic cycle as the area enclosed on the PV diagram.
5. **(Apply)** Analyze the Otto cycle as an idealized model of a gasoline engine.
6. **(Apply)** Build an animated PV diagram simulator with all four process types and cycle chains.

---

## Opening case: the four-stroke engine

A gasoline engine in a typical car cycles through four "strokes" per crankshaft rotation pair:
1. **Intake** — piston moves down, drawing in fuel-air mixture. (Approximately isobaric, atmospheric pressure.)
2. **Compression** — piston moves up; the closed cylinder's contents are compressed. (Approximately adiabatic.)
3. **Power** — spark plug ignites fuel; combustion adds heat; piston pushed down. (Approximately isochoric heat addition, then adiabatic expansion.)
4. **Exhaust** — piston moves up, expelling burned products.

Idealized, this is the **Otto cycle**: two adiabats + two isochors on a PV diagram. The enclosed area is the net work per cycle. Real engines deviate from the ideal Otto (friction, incomplete combustion, finite-time effects), but the idealized cycle is the conceptual foundation of *every* gasoline engine.

The chapter ahead is the PV diagram — the central visual tool of classical thermodynamics. Each thermodynamic process becomes a curve; each cycle a closed path; net work the enclosed area. Once you can read PV diagrams, you can analyze any heat engine.

---

## Core concept

### The PV diagram

A point on the PV diagram is a state (a specific $P$, $V$, $T$). A curve is a process — a quasi-static path between states. A closed curve is a cycle — a sequence of processes that returns to the start.

**Work** done by the gas during any quasi-static process: $W = \int_{V_1}^{V_2} P\,dV$. Geometrically: area under the $P(V)$ curve between $V_1$ and $V_2$.

For a cycle (closed curve): net work = enclosed area. Clockwise cycle: net work positive (engine). Counterclockwise: negative (refrigerator).

### The four canonical processes

**Isothermal** ($T$ = constant):
- Equation: $PV = nRT$ = constant — hyperbola.
- Work: $W = nRT \ln(V_f/V_i)$.
- For ideal gas: $\Delta U = 0$, so $Q = W$.

**Isochoric** ($V$ = constant):
- Equation: vertical line on PV diagram.
- Work: $W = 0$.
- $Q = \Delta U = nC_V \Delta T$.

**Isobaric** ($P$ = constant):
- Equation: horizontal line on PV diagram.
- Work: $W = P\Delta V$.
- $Q = nC_P \Delta T$. $\Delta U = nC_V \Delta T$. $Q = \Delta U + W$.

**Adiabatic** ($Q$ = 0): no heat exchange.
- Equation: $PV^\gamma$ = constant, equivalently $TV^{\gamma-1}$ = constant, where $\gamma = C_P/C_V$ is the heat-capacity ratio.
- Monatomic gas: $\gamma = 5/3 \approx 1.67$.
- Diatomic gas (moderate $T$): $\gamma = 7/5 = 1.40$.
- Work: $W = (P_i V_i - P_f V_f)/(\gamma - 1) = -\Delta U = -nC_V \Delta T$.
- For *expansion*: $T$ drops; $W > 0$.

### Adiabatic vs. isothermal: which is steeper?

At any given point on the PV diagram, *adiabatic curves are steeper than isothermal curves*.

Why: isothermal $P = nRT/V$ has slope $-P/V$ on PV. Adiabatic $P = P_0 V_0^\gamma/V^\gamma$ has slope $-\gamma P/V$. Since $\gamma > 1$, adiabatic is steeper.

Physically: in an adiabatic expansion, the gas cools (no heat to replace what's lost to work), so pressure drops faster than in an isothermal expansion at the same final volume.

This is the key visual that distinguishes the two processes on a PV diagram.

### Thermodynamic cycles

A cycle is a sequence of processes returning to the initial state. For a complete cycle: $\Delta U = 0$. Therefore $Q_{\text{net}} = W_{\text{net}}$ — net heat absorbed equals net work done.

**Net work** = enclosed area on PV diagram. For a clockwise cycle (proceeding from low $V$ to high $V$ at the top of the loop, then back at lower $P$): net work is positive. The cycle is a *heat engine*.

For a counterclockwise cycle: net work is negative — i.e., work is done *on* the gas. The cycle is a *refrigerator* or *heat pump*.

### The Otto cycle (idealized gasoline engine)

Four processes, all on the PV diagram:
1. **Adiabatic compression** (1→2): air-fuel mixture is compressed without heat exchange. Steep, going up and to the left on the PV diagram.
2. **Isochoric heat addition** (2→3): spark ignites the fuel; pressure rises at constant volume. Vertical line, going up.
3. **Adiabatic expansion** (3→4): the hot, high-pressure gas drives the piston. Curve going down and to the right.
4. **Isochoric heat rejection** (4→1): exhaust phase, modeled as cooling at constant volume. Vertical line, going down.

**Compression ratio** $r = V_1/V_2 = V_4/V_3$. The bigger the $r$, the higher the engine's efficiency.

**Otto cycle efficiency** (from first principles using $\Delta U$, $Q$, $W$ for each leg):

$$\eta_{\text{Otto}} = 1 - \frac{1}{r^{\gamma-1}}$$

For $r = 10$, $\gamma = 1.4$: $\eta \approx 1 - 10^{-0.4} \approx 1 - 0.398 = 60\%$. Real gasoline engines reach only 25–30% — far below the Otto ideal, because real combustion and exhaust are highly irreversible.

### Refrigeration cycle (preview)

Run the cycle counterclockwise. Work is *added* to the gas; heat is *extracted from* the cold reservoir and *deposited in* the hot reservoir. This is how refrigerators and air conditioners work — but with vapor-compression cycles rather than pure ideal-gas processes. Chapter 9 develops the real-world version.

---

## Worked example: Otto cycle analysis

A simplified Otto engine: $r = 8$ (compression ratio), $\gamma = 1.4$ (diatomic air), initial conditions at state 1: $T_1 = 300$ K, $P_1 = 1$ atm = $101{,}325$ Pa, $V_1 = 1$ L = $10^{-3}$ m³.

Heat added during isochoric heating (2→3): $Q_H = 1000$ J per cycle. Find $T$ at each state and the cycle efficiency.

**State 2** (after adiabatic compression, $V_2 = V_1/r$):
$T_2 = T_1 r^{\gamma-1} = 300 \cdot 8^{0.4} \approx 300 \cdot 2.30 = 690$ K.
$V_2 = V_1/8 = 1.25 \times 10^{-4}$ m³.
$P_2 = P_1 r^\gamma = 101{,}325 \cdot 8^{1.4} \approx 101{,}325 \cdot 18.4 = 1.86 \times 10^6$ Pa.

**State 3** (after isochoric heat addition):
Need to know $n$ first. From state 1: $n = P_1V_1/(RT_1) = 101325 \cdot 10^{-3}/(8.314 \cdot 300) \approx 0.0406$ mol.
$C_V = (5/2)R = 20.79$ J/(mol·K) (diatomic).
$\Delta T = Q_H/(nC_V) = 1000/(0.0406 \cdot 20.79) \approx 1185$ K.
$T_3 = T_2 + 1185 = 690 + 1185 = 1875$ K.
$V_3 = V_2 = 1.25 \times 10^{-4}$ m³.
$P_3 = nRT_3/V_3 = 0.0406 \cdot 8.314 \cdot 1875 / (1.25 \times 10^{-4}) \approx 5.07 \times 10^6$ Pa.

**State 4** (after adiabatic expansion back to $V_4 = V_1$):
$T_4 = T_3 / r^{\gamma-1} = 1875 / 2.30 \approx 815$ K.
$V_4 = V_1 = 10^{-3}$ m³.
$P_4 = nRT_4/V_4 = 0.0406 \cdot 8.314 \cdot 815 / 10^{-3} \approx 2.75 \times 10^5$ Pa.

**Heat rejected** (during 4→1 isochoric cooling): $Q_C = nC_V(T_4 - T_1) = 0.0406 \cdot 20.79 \cdot (815-300) = 435$ J.

**Net work** per cycle: $W = Q_H - Q_C = 1000 - 435 = 565$ J.

**Efficiency:** $\eta = W/Q_H = 565/1000 = 56.5\%$.

**Check against formula:** $\eta_{\text{Otto}} = 1 - 1/r^{\gamma-1} = 1 - 1/2.30 = 56.5\%$. ✓

**The lesson.** The Otto cycle efficiency depends only on the compression ratio (and $\gamma$). Higher $r$ gives higher efficiency. Modern gasoline engines push $r$ to 10–12 (limited by autoignition — "knocking"); diesel engines push $r$ to 15–22 (no spark plugs, ignition by compression).

**The limit.** Real engines run far from the ideal Otto cycle: finite combustion time (not instantaneous), turbulent gas dynamics, friction losses, heat conduction to cylinder walls, exhaust flow restrictions. Real efficiencies: 25–30% for gasoline, 40–45% for diesel.

---

## Common misconceptions

**"Isothermal and adiabatic curves look the same."** Both are curves going down-right on the PV diagram, but adiabatic is always *steeper*. At the same point, $|dP/dV|_{\text{adiabatic}} = \gamma |dP/dV|_{\text{isothermal}}$, with $\gamma > 1$. The two curves diverge as $V$ increases.

**"Work done = area under the curve, always."** Yes, for *quasi-static* processes. The formula $W = \int P\,dV$ assumes the gas is in equilibrium at each step. For non-equilibrium processes (free expansion into vacuum, rapid pressure changes), the integral isn't directly meaningful, but the first law still applies — you just have to compute $W$ from external constraints (e.g., $W = 0$ for free expansion).

**"The area enclosed by any cycle is the heat added."** No — it's the *net work*. Heat added depends on the path: total $Q$ added over the cycle equals total $W$ done (since $\Delta U = 0$ for a complete cycle), and these are both equal to the enclosed area.

**"Otto cycle efficiency is what real engines achieve."** Real engines fall well short. The Otto formula sets the *upper bound* assuming everything is ideal; friction, finite-time combustion, and heat losses reduce real efficiency to ~half the ideal Otto value.

**"Cycles must go clockwise."** Cycles can go either way. Clockwise = engine (does net positive work). Counterclockwise = refrigerator (work input is positive; heat is moved from cold to hot).

---

## Exercises

**Warm-up (Apply).** A gas at $P = 2$ atm, $V = 5$ L expands isobarically to $V = 8$ L. Find $W$ in joules.

**Apply.** 1 mol of monatomic ideal gas at $V_1 = 10$ L, $T_1 = 300$ K expands isothermally to $V_2 = 30$ L. Find $W$, $Q$, $\Delta U$, $\Delta T$.

**Apply.** Same gas at the same initial conditions undergoes *adiabatic* expansion to $V_2 = 30$ L. Find $T_2$, $W$, $Q$, $\Delta U$. Compare to the isothermal case.

**Apply.** Otto cycle: $r = 9$, $\gamma = 1.4$, $T_1 = 350$ K, $V_1 = 0.5$ L. Heat added per cycle $Q_H = 800$ J. Find $T_2$, $T_3$, $T_4$, $\eta_{\text{Otto}}$, $W_{\text{net}}$.

**Apply + Analyze.** A cyclic process on the PV diagram traces a rectangle with corners at $(V_1, P_1) = (10$ L, 1 atm), $(V_2, P_1) = (30$ L, 1 atm), $(V_2, P_2) = (30$ L, 3 atm), $(V_1, P_2) = (10$ L, 3 atm). Compute net work, going clockwise.

**Challenge.** A diesel cycle: 1 mol gas, adiabatic compression $r_c = 18$, isobaric heat addition until $V_3 = 2 V_2$, then adiabatic expansion back to $V_1$, then isochoric cooling. Find the cycle's efficiency. (Diesel efficiencies for $r_c = 18$: ~62%.)

---

## LLM Exercises

### Build the PV diagram simulator (`05-pv-diagram.html`)

> **Show.** Four processes: isothermal $PV = $ const, isochoric $V$ = const, isobaric $P$ = const, adiabatic $PV^\gamma$ = const. Work = area under curve.
>
> **Say.** Build an interactive PV-diagram simulator with all four process types and cycle chains.
>
> **Constrain.** D3 v7. PV axes with isothermal hyperbolas drawn as background grid (at several reference temperatures). Initial state controls (sliders for $P_0, V_0, T_0$, and $n$). Process selector (isothermal/isochoric/isobaric/adiabatic). Final-state slider. The process plays as an animated curve on the diagram; work computed as shaded area; $Q, \Delta U$, $W$ displayed numerically. Cycle mode: chain up to 4 processes; show the closed path; net work = enclosed area. Preset: Otto cycle. Filename: `05-pv-diagram.html`.
>
> **Verify.** (a) Isothermal: hyperbola. (b) Adiabatic: steeper than isothermal at any point. (c) Isobaric: horizontal. (d) Isochoric: vertical. (e) Otto cycle enclosed area = work computed analytically.

### Exploration

- Build an Otto cycle. Vary $r$ from 5 to 15. Plot efficiency vs. $r$. Compare to $1 - 1/r^{\gamma-1}$.
- Run two cycles starting from the same state: isothermal expansion then isochoric heating then isobaric compression vs. adiabatic expansion then isochoric heating then isobaric compression. Which produces more net work? Both end at the same final state, but the paths differ.
- Reverse a cycle (go counterclockwise). The same shape, but work is now negative — work is done on the gas. This is a refrigerator.

### Extension prompt (chapter bridge)

> **Show.** I've analyzed thermodynamic cycles that do net work. Now I want to understand the *limit* on how efficient any cycle can be — and why no engine can convert all heat to work.
>
> **Say.** Build a Carnot cycle simulator showing the upper bound on heat-engine efficiency.
>
> **Constrain.** Two isothermals (at $T_H$ and $T_C$) connected by two adiabats. Show the cycle on both PV and TS diagrams. Display Carnot efficiency $\eta_C = 1 - T_C/T_H$. Slider for $T_H$ and $T_C$.
>
> **Verify.** Carnot efficiency $< 1$ for any finite $T_H$. As $T_C/T_H \to 0$, $\eta \to 1$ (impossible to reach). As $T_C/T_H \to 1$, $\eta \to 0$ (no heat differential = no work).

Save as `05b-carnot-preview.html`. Bridge to Chapter 6.

---

## What would change my mind

The PV diagram is a geometric tool — its validity is just the ideal-gas law applied to quasi-static processes. The work formula $W = \int P \, dV$ is an exact identity for any quasi-static process. The process formulas (isothermal, adiabatic, etc.) for an ideal gas have been confirmed in countless experiments. None of this is contested.

What's missing is the *direction* of allowed processes. The PV diagram tells you what's possible algebraically; it doesn't tell you which direction is spontaneous. That's the second law's job (Chapter 6).

## Still puzzling

- *Why $PV^\gamma$ for adiabatic?* Derived from the first law applied to an adiabatic process: $dU = -P dV$ with $dU = nC_V dT$ and $PV = nRT$. The math is standard; the *physics* is that no heat enters, so internal energy changes only by the work done.
- *What's a "quasi-static" process really?* A process slow enough that the gas is in equilibrium at every instant — effectively a sequence of equilibrium states. Real processes aren't quasi-static; they have finite-time effects. The PV diagram only handles the quasi-static idealization.
- *What happens at the corners of a cycle?* Where two processes meet (e.g., adiabatic → isochoric in the Otto cycle), there's an instantaneous change in the slope of the path. Real engines can't make instantaneous transitions; there's a smoothing at every corner. The idealized PV diagram is a useful approximation.

---

**Tags:** PV diagram, isothermal, isochoric, isobaric, adiabatic, thermodynamic cycle, Otto cycle, compression ratio, heat engine, work as area

