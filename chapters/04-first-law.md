# Chapter 4 — The First Law of Thermodynamics

*Energy conservation, applied. Internal energy is a state function; heat and work are not.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Understand)** State the first law $\Delta U = Q - W$ with proper sign conventions ($Q > 0$ for heat *added* to system; $W > 0$ for work *done by* system).
2. **(Apply)** Compute $\Delta U$, $Q$, $W$ for ideal-gas processes (isothermal, adiabatic, isochoric, isobaric).
3. **(Analyze)** Distinguish state functions ($U$, $T$, $P$, $V$, $S$, $H$) from path functions ($Q$, $W$).
4. **(Apply)** Use $\Delta U = nC_V \Delta T$ for any ideal-gas process (since $U$ depends only on $T$ for ideal gas).
5. **(Apply)** Define enthalpy $H = U + PV$ and use $\Delta H = Q$ for isobaric processes.
6. **(Apply)** Build a first-law energy-balance visualizer.

---

## Opening case: a battery doing work

A car battery, fully charged, holds about 1 kWh = 3.6 × 10⁶ J of internal chemical energy. You start the engine. The starter motor draws ~200 A at 12 V — about 2.4 kW. After about 5 seconds of cranking, the engine starts. The battery has lost roughly 12 kJ — about 0.3% of its capacity.

Where did that 12 kJ go? Mechanical work on the engine's crankshaft (some). Heat from the wires and the starter motor's windings (some). Heat from chemical reactions inside the battery (some). Heat radiated into the engine compartment (some). All of it accounted for. None of it disappeared.

This is the first law of thermodynamics: *energy is conserved*. Internal energy changes equal heat added minus work done.

The first law is the bookkeeping that constrains every thermodynamic process. Chapter 5 specializes it to ideal-gas processes; Chapter 6 introduces the *direction* of allowed processes (the second law); Chapter 7 introduces entropy. But the foundation is energy conservation, and that's this chapter.

---

## Core concept

### The first law

For a closed system (no matter crossing the boundary):

$$\Delta U = Q - W$$

where:
- $\Delta U$ = change in internal energy of the system (state function — depends only on initial and final states)
- $Q$ = heat added *to* the system (process quantity, path-dependent)
- $W$ = work done *by* the system (process quantity, path-dependent)

**Sign conventions (physics, this book):**
- $Q > 0$ when heat is added to the system.
- $W > 0$ when the system does work on its surroundings (expansion).
- $Q < 0$ when heat is removed; $W < 0$ when work is done on the system.

(Some chemistry texts use $\Delta U = Q + W$ with $W$ being "work done on the system." Same physics, different sign convention. The chapter sticks with the physics convention.)

The first law is *conservation of energy applied to a thermodynamic system*. Internal energy can change by exchanging heat with the surroundings, or by doing work, or both. Energy cannot be created or destroyed.

### State functions vs. path functions

A *state function* depends only on the current state, not on the path taken to reach it. State functions:
- $U$ (internal energy)
- $T$, $P$, $V$ (state variables)
- $S$ (entropy — Chapter 7)
- $H$ (enthalpy)

A *path function* depends on the path taken between states.
- $Q$ (heat) — different amounts depending on the process.
- $W$ (work) — same.

**The distinction matters because** state functions allow you to compute $\Delta f$ from any two endpoints without caring about the intermediate path. For path functions, you must specify the path.

### Internal energy of an ideal gas

For an ideal gas, $U$ depends only on $T$ (and $N$), not on $P$ or $V$:

$$U_{\text{ideal gas}} = n C_V T = \frac{f}{2} N k_B T$$

where $f$ is the number of degrees of freedom (3 for monatomic, 5 for diatomic at moderate $T$).

Consequence: for *any* ideal-gas process — isothermal, adiabatic, isochoric, isobaric — the internal energy change is

$$\Delta U = n C_V \Delta T$$

regardless of how the gas was driven from $T_1$ to $T_2$. (Important: $C_V$ here is the *molar* heat capacity at constant volume.)

### Work done by a gas

For a quasi-static process (slow enough that the gas is always in equilibrium):

$$W = \int_{V_1}^{V_2} P \, dV$$

Graphically: the area under the $P(V)$ curve on a PV diagram. (Chapter 5 develops this.)

For specific processes (ideal gas):
- **Isothermal** ($T$ constant): $W = nRT \ln(V_2/V_1)$.
- **Isobaric** ($P$ constant): $W = P \Delta V = P(V_2 - V_1)$.
- **Isochoric** ($V$ constant): $W = 0$.
- **Adiabatic** ($Q = 0$): $W = -\Delta U = -nC_V(T_2 - T_1)$.

### Applying the first law to each process type

**Isothermal expansion** of an ideal gas: $\Delta U = 0$ (since $T$ constant). So $Q = W$. All the heat absorbed goes into work done by the gas.

**Adiabatic expansion**: $Q = 0$. So $\Delta U = -W$. The gas does work at the expense of internal energy; $T$ drops.

**Isochoric heating**: $W = 0$ (no volume change). So $\Delta U = Q$. All heat absorbed raises internal energy; $T$ rises.

**Isobaric expansion** at constant $P$: $W = P\Delta V$; $\Delta U = nC_V\Delta T$; $Q = \Delta U + W = nC_V\Delta T + P\Delta V$.

### Enthalpy: a useful state function for chemistry

Define **enthalpy**:
$$H = U + PV$$

$H$ is a state function. For an *isobaric* process:
$$\Delta H = \Delta U + P\Delta V = Q$$ (at constant $P$)

So $\Delta H$ is the heat absorbed at constant pressure. Chemists use $H$ instead of $U$ because most chemical reactions happen at constant atmospheric pressure (not constant volume).

For an ideal gas:
$$\Delta H = nC_P \Delta T$$

with $C_P = C_V + R$ (the Mayer relation, derivable from $PV = nRT$).

---

## Worked example: heating air in a sealed cylinder

A sealed cylinder contains $n = 2$ mol of air (treated as diatomic ideal gas, $C_V = (5/2)R$). The gas is initially at $T_1 = 300$ K, $P_1 = 1$ atm, $V_1 = 2 \cdot 8.314 \cdot 300 / (101325) \approx 0.049$ m³.

The gas is heated to $T_2 = 400$ K. Two scenarios.

**Scenario A — sealed cylinder (isochoric).**

$V$ stays at 0.049 m³ (rigid container). $W = 0$.

$\Delta U = nC_V \Delta T = 2 \cdot (5/2)(8.314)(100) = 4157$ J.

$Q = \Delta U = 4157$ J. All the heat goes into internal energy; the gas's temperature rises 100 K, but it does no work.

Final pressure: $P_2 = nRT_2/V = 2 \cdot 8.314 \cdot 400 / 0.049 \approx 135{,}900$ Pa = 1.34 atm.

**Scenario B — frictionless piston (isobaric).**

$P$ stays at 1 atm (piston free to move). The gas expands.

$V_2 = nRT_2/P = 2 \cdot 8.314 \cdot 400 / 101325 \approx 0.0656$ m³. $\Delta V = 0.0164$ m³.

$W = P\Delta V = 101{,}325 \cdot 0.0164 \approx 1665$ J. The gas does positive work on the piston.

$\Delta U = nC_V \Delta T = 4157$ J (same as before — $U$ depends only on $T$ for ideal gas).

$Q = \Delta U + W = 4157 + 1665 = 5822$ J.

**Compare.** Both scenarios end at the same $T_2 = 400$ K. Internal energy change is the same (4157 J). But the second scenario required *more heat input* (5822 J vs. 4157 J), because some of the heat went into doing work on the piston. The "extra" heat is exactly the work done.

**The lesson.** $\Delta U$ depends only on initial and final $T$ — *not on the path*. But $Q$ and $W$ are path-dependent. Different paths to the same final state require different amounts of heat input.

**The limit.** This assumed ideal gas behavior; real gases would deviate (especially at high density or near phase transitions). Also assumed the piston has zero mass and is frictionless. Real systems include friction (irreversible heat generation) that's not in this calculation.

---

## Common misconceptions

**"Heat and work are stored in a system."** Only internal energy is stored. $Q$ and $W$ describe energy *in transit*, not energy held by the system.

**"A system that absorbs heat always increases in temperature."** Not necessarily. If the heat absorbed equals the work done (isothermal process), $\Delta U = 0$ and $T$ is unchanged. The gas expands instead.

**"Adiabatic means no temperature change."** Adiabatic means *no heat exchange*. The temperature *can change*, because work is being done. An adiabatic expansion *cools* the gas; an adiabatic compression *heats* it. This is how a diesel engine ignites: rapid (adiabatic) compression of air raises its temperature high enough to ignite injected fuel.

**"Internal energy and heat are the same thing."** Internal energy is a state function — the total microscopic kinetic + potential energy. Heat is a process quantity — energy flowing into or out of the system due to temperature difference.

**"The sign of $W$ depends on the process direction."** $W > 0$ when the *system* does work on its surroundings (expansion against a piston). $W < 0$ when work is done *on* the system (compression). The sign matters for the first law.

---

## Exercises

**Warm-up (Apply).** A gas absorbs 500 J of heat and does 200 J of work. Find $\Delta U$.

**Apply.** 1 mol of monatomic ideal gas at $V_1 = 10$ L, $T_1 = 300$ K expands isothermally to $V_2 = 20$ L. Find $W$, $Q$, $\Delta U$.

**Apply.** 2 mol of diatomic ideal gas at $V_1 = 10$ L, $T_1 = 300$ K is heated at constant volume to $T_2 = 500$ K. Find $W$, $Q$, $\Delta U$.

**Apply + Analyze.** Same 2 mol of diatomic ideal gas at $T_1 = 300$ K, $V_1 = 10$ L is heated to $T_2 = 500$ K at constant *pressure* of 4.99 atm. Find the final volume, $W$, $Q$, $\Delta U$. Compare to the isochoric case.

**Apply.** A gas undergoes an adiabatic expansion: initial $T_1 = 400$ K, $V_1 = 5$ L; final $V_2 = 15$ L. The gas is monatomic ($\gamma = 5/3$). Use $TV^{\gamma-1} = $ const to find $T_2$. Then compute $W$ and verify $\Delta U = -W$.

**Challenge (Synthesize).** Derive $C_P - C_V = R$ (Mayer's relation) for an ideal gas. Hint: write $H = U + PV$; for an ideal gas $PV = nRT$ and $U$ is a function of $T$ alone. Differentiate with respect to $T$.

---

## LLM Exercises

### Build the first-law visualizer (`04-first-law.html`)

> **Show.** First law: $\Delta U = Q - W$. For ideal gas: $\Delta U = nC_V \Delta T$. Process-specific formulas: isothermal $W = nRT \ln(V_f/V_i)$; adiabatic $W = -\Delta U$; isochoric $W = 0$; isobaric $W = P\Delta V$.
>
> **Say.** Build an interactive first-law energy-balance visualizer.
>
> **Constrain.** D3 v7. Controls: process type (isothermal/adiabatic/isochoric/isobaric), $n$ (mol), gas type (monatomic/diatomic — sets $\gamma$ and $C_V$), initial $T_0$, $P_0$, $V_0$, and a slider for the final-state parameter (final $T$, $V$, or $P$ depending on process type). Compute $\Delta U$, $Q$, $W$ for the process. Display: animated energy bar chart showing $U_{\text{initial}}$, $U_{\text{final}}$, and $Q$, $W$ as arrows in/out of the system. The first law $\Delta U = Q - W$ displayed with numerical values, verifying that the equation holds. Filename: `04-first-law.html`.
>
> **Verify.** Isothermal: $\Delta U = 0$, $Q = W$. Adiabatic: $Q = 0$, $\Delta U = -W$. Isochoric: $W = 0$, $\Delta U = Q$. Isobaric: $Q - W = \Delta U$.

### Exploration

- Run an adiabatic expansion of a monatomic gas, going from $T_1 = 600$ K to $V_2 = 2V_1$. Find $T_2$ and verify $T V^{\gamma-1}$ const.
- Compare isothermal and adiabatic expansions of the same gas with the same initial state to the same final volume. Which one absorbs more heat? Which one does more work? Why?
- Verify Mayer's relation: $C_P - C_V = R$ in the simulation by comparing $Q$ for isobaric and isochoric processes that produce the same $\Delta T$.

### Extension prompt (chapter bridge)

> **Show.** I've computed $\Delta U$, $Q$, $W$ for individual processes. Now I want to visualize them on a PV diagram and chain multiple processes into a thermodynamic cycle.
>
> **Say.** Build an animated PV diagram showing process curves and computing work as area under the curve.
>
> **Constrain.** Plot the gas's state point on the PV diagram. Animate the process from initial to final state. The work $W = \int P\,dV$ should be shown as the shaded area under the curve. Cycle mode: chain 4 processes returning to the initial state; net work = enclosed area.
>
> **Verify.** Isothermal expansion: hyperbolic curve, positive work. Adiabatic expansion: steeper hyperbola, less work for the same $\Delta V$. Isochoric: vertical line, $W = 0$. Cycle: enclosed area = net work.

Save as `04b-pv-cycle-preview.html`. Bridge to Chapter 5.

---

## What would change my mind

The first law is *conservation of energy* — one of the most precisely tested principles in physics. Every measurement of internal energy in a closed system has confirmed the bookkeeping. A confirmed violation would force the rewriting not just of thermodynamics but of all of physics. None has occurred.

The ideal-gas formulas $\Delta U = nC_V \Delta T$ depend on the ideal-gas assumption. Real gases have small deviations (van der Waals corrections, Chapter 3). These are quantitative corrections, not falsifications.

## Still puzzling

- *Why is internal energy a function of $T$ alone for an ideal gas?* Because by definition, an ideal gas has no intermolecular potential energy (point particles, no forces). All the internal energy is in molecular kinetic energy and (for molecules with internal structure) rotational/vibrational modes — all functions of $T$ alone. Real gases have intermolecular forces and therefore a $U(T, V)$ dependence.
- *What about open systems?* The first law as stated is for closed systems (no matter crossing boundaries). For open systems (flow processes — turbines, pipes, etc.), an additional term for the work done by *flowing matter* must be included. This is the *flow work* $PV$, leading naturally to the use of enthalpy $H = U + PV$ in flow analyses. Chapter 9 addresses this.
- *What is the relationship between $U$ and $H$?* $U$ measures internal energy strictly. $H$ measures internal energy *plus the work that would be done by the gas at the current pressure if it expanded against a piston*. Useful for chemistry at constant pressure.

---

**Tags:** first law of thermodynamics, internal energy, heat, work, state function, path function, ideal gas, enthalpy, Mayer's relation, sign conventions

