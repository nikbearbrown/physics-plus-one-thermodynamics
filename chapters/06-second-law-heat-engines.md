# Chapter 6 — The Second Law and Heat Engines

*The Carnot bound, the arrow of time, and why heat engines are limited.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Understand)** State the second law in two equivalent forms (Clausius, Kelvin-Planck) and explain why they are equivalent.
2. **(Apply)** Compute the Carnot efficiency $\eta_C = 1 - T_C/T_H$ for given hot and cold reservoir temperatures.
3. **(Analyze)** Distinguish reversible and irreversible processes and identify sources of irreversibility.
4. **(Apply)** Use the Carnot theorem to bound real-engine efficiency and compute COPs for refrigerators and heat pumps.
5. **(Understand)** Recognize the TS diagram and interpret areas as heat exchanged.
6. **(Apply)** Build a Carnot cycle simulator with adjustable irreversibility.

---

## Opening case: why your refrigerator can't be more efficient

A household refrigerator at home: freezer at −18°C (255 K), kitchen at 22°C (295 K). The Carnot COP for moving heat from cold to hot:
$$\text{COP}_{\text{Carnot}} = \frac{T_C}{T_H - T_C} = \frac{255}{40} = 6.4$$

This means, ideally, every joule of electrical work removes 6.4 J of heat from the freezer. A perfect refrigerator running at the Carnot limit needs 1 J of electricity to do the job of cooling that 6.4 J would do.

Real refrigerators have COP around 2–4. They're about half as efficient as the thermodynamic upper bound. The reasons: heat exchangers operate with finite temperature differences (irreversible), compressors are not isentropic, throttling valves introduce free expansion, friction in moving parts.

You could *in principle* build a refrigerator approaching the Carnot limit — but you'd need infinitely-large heat exchangers, frictionless compressors, and infinitely slow operation. Practical engineering trades off Carnot-approach for finite size and operating speed.

This chapter is about the bound: why no heat engine or refrigerator can exceed Carnot. Carnot's 1824 result — that efficiency depends only on temperatures, not on substance or design — is one of the deepest in physics. It's the foundation of the second law.

---

## Core concept

### The second law: two equivalent statements

**Kelvin-Planck statement:** No cyclic device can convert all input heat into work. There must always be a portion of heat rejected to a cold reservoir.

**Clausius statement:** Heat cannot spontaneously flow from a colder object to a hotter object.

These two are *equivalent*: violating either one would let you build a perpetual-motion machine of the second kind. The proof: assume one is false; combine it with the other in a clever way; derive a violation of energy conservation (or the other statement). The argument is technical but constructive.

In neither form is the second law a *force* law. It's a statement about *direction* — which processes happen spontaneously, which don't. Energy conservation alone doesn't pick a direction; the second law does.

### Heat engines

A heat engine takes in heat $Q_H$ from a hot reservoir, does work $W$, and rejects heat $Q_C$ to a cold reservoir:
- First law (cycle): $W = Q_H - Q_C$
- Efficiency: $\eta = W/Q_H = 1 - Q_C/Q_H$

The Kelvin-Planck statement implies $Q_C > 0$, hence $\eta < 1$ — *no engine can achieve 100% efficiency*.

### The Carnot cycle

The Carnot cycle is the *ideal reversible heat engine* — composed of two reversible isothermals (at $T_H$ and $T_C$) connected by two reversible adiabatics.

**The four legs:**
1. Isothermal expansion at $T_H$: heat $Q_H$ absorbed from hot reservoir.
2. Adiabatic expansion from $T_H$ to $T_C$: no heat, but work done; temperature drops.
3. Isothermal compression at $T_C$: heat $Q_C$ rejected to cold reservoir.
4. Adiabatic compression from $T_C$ to $T_H$: temperature rises back to $T_H$.

**Carnot efficiency:**
$$\eta_C = 1 - \frac{T_C}{T_H}$$

(Temperatures in Kelvin — absolute scale.)

This depends *only on the temperatures of the reservoirs*, not on the working substance, not on the engine's geometry, not on anything else.

For a Carnot engine between $T_H = 600$ K and $T_C = 300$ K: $\eta_C = 1 - 0.5 = 50\%$. Half the input heat becomes work.

### Carnot's theorem

*No engine operating between two reservoirs can exceed the Carnot efficiency $\eta_C = 1 - T_C/T_H$.*

Proof: Suppose an engine exists with $\eta > \eta_C$. Run a Carnot engine in reverse (as a refrigerator) using the work output of the super-Carnot engine. The combined system extracts net heat from the cold reservoir while doing no work overall — violating the Clausius statement of the second law.

**Corollary:** *All reversible engines operating between the same reservoirs have the same efficiency*, equal to $\eta_C$. The working substance doesn't matter; the geometry doesn't matter.

This is the deepest result. Carnot proved it 1824 — *before* the first law was even formulated. His original argument used caloric theory (which is wrong about heat being a substance), yet his conclusion is correct. The result is robust because it follows from the impossibility of perpetual motion.

### Reversible vs. irreversible

A *reversible* process is one that can be run backwards by an infinitesimal change in conditions. Quasi-static + no friction + no heat conduction across finite $\Delta T$.

An *irreversible* process is everything real:
- Friction: irreversible dissipation of kinetic energy as heat.
- Heat conduction across a finite temperature difference: spontaneous direction is hot → cold.
- Free expansion of a gas into vacuum: no work done, but gas spreads (entropy generation).
- Mixing of two different gases: irreversible by demixing without work input.

Real processes are always irreversible to some degree; reversibility is an idealization useful for the Carnot bound.

### Refrigerators and heat pumps

A *refrigerator* is a heat engine run in reverse: work input drives heat from cold to hot.

**COP (Coefficient of Performance) for refrigerator:**
$$\text{COP}_{\text{ref}} = \frac{Q_C}{W}$$

Carnot bound: $\text{COP}_{\text{Carnot,ref}} = T_C/(T_H - T_C)$.

A *heat pump* is also reversed; the goal is delivering $Q_H$ (heating a room).
$$\text{COP}_{\text{HP}} = \frac{Q_H}{W} = \text{COP}_{\text{ref}} + 1$$

Carnot bound: $\text{COP}_{\text{Carnot,HP}} = T_H/(T_H - T_C)$.

Always $\text{COP} > 1$ for both (you get more heat moved than work in). That's why heat pumps are far more energy-efficient than resistance heating.

### The TS diagram

An alternative way to display thermodynamic cycles. Plot temperature $T$ vs. entropy $S$ (Chapter 7).
- Isothermal process: horizontal line.
- Adiabatic reversible (isentropic) process: vertical line.
- Carnot cycle: rectangle.

Area enclosed by the cycle on the TS diagram = net heat absorbed = net work done (since $\Delta U = 0$ for a cycle).

The TS diagram is the natural representation for analyzing entropy changes; the PV diagram is the natural representation for analyzing work. Real engineering analysis uses both.

---

## Worked example: Carnot vs. real engine

A real heat engine operates between $T_H = 800$ K (steam) and $T_C = 400$ K (condenser). It absorbs $Q_H = 1000$ J per cycle.

**(a) Carnot efficiency:** $\eta_C = 1 - 400/800 = 0.5 = 50\%$. Maximum possible work per cycle: $W_C = 500$ J. Heat rejected: $Q_{C,\text{Carnot}} = 500$ J.

**(b) Real engine with $\eta = 0.35$ (35%):** Actual work: $W = 350$ J. Heat rejected: $Q_C = 1000 - 350 = 650$ J.

**(c) Entropy generated** by the real engine per cycle. The hot reservoir loses 1000 J at 800 K, gaining entropy $\Delta S_H = -1000/800 = -1.25$ J/K. The cold reservoir gains 650 J at 400 K, gaining entropy $\Delta S_C = +650/400 = +1.625$ J/K. Net universe: $\Delta S_{\text{universe}} = -1.25 + 1.625 = +0.375$ J/K per cycle.

For the *Carnot engine*: $\Delta S_H = -1.25$, $\Delta S_C = +500/400 = +1.25$. Net universe: 0. Carnot is reversible.

**The lesson.** Carnot is the upper bound. Real engines fall short. The amount they fall short — measured as entropy generated per cycle — quantifies the irreversibility.

**The limit.** This treatment assumes the reservoirs are at fixed temperatures and the engine operates quasi-statically. Real engines operate in finite time and run against finite-size reservoirs whose temperatures drift. Chapter 9 develops the real-world picture.

---

## Common misconceptions

**"More efficient engines just need better engineering."** No. The Carnot limit is fundamental. No engineering breakthrough can exceed $\eta_C = 1 - T_C/T_H$. Engineering can *approach* the Carnot bound, but never exceed it.

**"Refrigerators violate the second law by making cold regions colder."** They don't. They move heat from cold to hot, but *only with work input from outside*. The total entropy of the universe (refrigerator + room + freezer contents) still increases.

**"100% efficiency is impossible because of friction."** Friction is one source of irreversibility, but Carnot's bound applies even with no friction. The fundamental limit is the *impossibility of completely converting heat into work in a cyclic process* — it doesn't depend on friction.

**"Carnot efficiency is achievable in practice."** No. Carnot requires reversible processes — no finite temperature gradients, no friction, infinitely slow operation. Practical engines must operate in finite time and so generate entropy. Real efficiencies are typically 50–80% of Carnot.

**"Heat pumps create energy."** They move energy from a cool place (outdoors) to a warmer place (your room). The energy isn't created; it's collected. The work input is the cost; the heat delivered to the room is greater than the work input because most of the heat came from outside.

---

## Exercises

**Warm-up (Apply).** A Carnot engine operates between $T_H = 600$ K and $T_C = 300$ K. Find $\eta_C$.

**Apply.** A real heat engine absorbs 2000 J from a hot reservoir at 500°C and rejects 1300 J to a cold reservoir at 20°C. (a) Find its actual efficiency. (b) Find the Carnot efficiency for these temperatures. (c) What fraction of the Carnot ideal does the real engine achieve?

**Apply.** A heat pump warms a house at 20°C from outdoor air at 0°C. Find the Carnot COP for the heat pump. If the real heat pump has COP = 3.5, and the house loses 5000 W to the cold outdoors, find the electrical power needed.

**Apply.** A car engine running on a 4-stroke gasoline cycle with $T_H \approx 2000$ K (peak combustion temperature) and $T_C \approx 400$ K (exhaust). (a) Carnot efficiency. (b) Real gasoline engines achieve ~25%. What fraction of Carnot is this?

**Apply + Analyze.** A power plant burns coal to generate electricity. Heat input from coal: 100 MW. Plant operates with $T_H = 850$ K, $T_C = 320$ K. (a) Find $\eta_C$. (b) If real plant efficiency is 35%, find the electric power generated and the waste heat. (c) Find the entropy generated by the plant per second.

**Challenge.** Show that the Clausius and Kelvin-Planck statements of the second law are logically equivalent. (Hint: assume Clausius is false; construct a perpetual-motion machine of the second kind that violates Kelvin-Planck. Then assume Kelvin-Planck is false; construct one that violates Clausius.)

---

## LLM Exercises

### Build the Carnot cycle simulator (`06-carnot-cycle.html`)

> **Show.** Carnot cycle: two isothermals + two adiabats. Carnot efficiency $\eta_C = 1 - T_C/T_H$. No real engine can exceed this.
>
> **Say.** Build a Carnot cycle simulator with irreversibility control.
>
> **Constrain.** D3 v7. Split screen: PV diagram (left) and TS diagram (right). PV diagram shows two isotherms (at $T_H$, $T_C$) connected by two adiabats. TS diagram shows the rectangle. Controls: sliders for $T_H, T_C$ (both in K); slider for "irreversibility factor" (0 = Carnot ideal, 1 = maximally irreversible). At irreversibility > 0, the actual efficiency drops; show the gap as a red bar on a Sankey diagram of $Q_H, W, Q_C$. Numerical readouts: $\eta_C$, actual $\eta$, entropy generated per cycle. Filename: `06-carnot-cycle.html`.
>
> **Verify.** (a) $T_H = 600, T_C = 300$ K: $\eta_C = 0.5$. (b) Increasing $T_C$ toward $T_H$ reduces $\eta_C$ toward 0. (c) Irreversibility factor 1: efficiency drops dramatically; entropy generation rises.

### Exploration

- A Carnot engine between $T_H = 600$ K and $T_C = 300$ K has $\eta = 50\%$. Lower $T_C$ to 100 K: now $\eta = 83\%$. But to use $T_C = 100$ K, you need a cryogenic refrigerator that consumes more power than the engine produces. Real plants compromise.
- Run the cycle counterclockwise (reverse direction). The same shape, but now work is *added* (refrigerator mode). Compute the refrigerator's COP from the Sankey display.
- Compare Carnot efficiency for two power plants: a steam plant at $T_H = 870$ K / $T_C = 320$ K (a typical fossil plant) and an OTEC ocean-thermal plant at $T_H = 300$ K / $T_C = 280$ K (deep-ocean cold water vs. warm surface). OTEC efficiency is much lower because $\Delta T$ is small.

### Extension prompt (chapter bridge)

> **Show.** The Carnot cycle introduces a quantity that is conserved in reversible processes and *increases* in irreversible ones — entropy.
>
> **Say.** Build an entropy-counting simulator: a box of particles, plot the entropy as a function of distribution.
>
> **Constrain.** N=20 particles randomly hop between two halves of a box at each time step. Count microstates: $\Omega(n_{\text{left}}) = \binom{N}{n_{\text{left}}}$. Compute $S = k_B \ln \Omega$. Plot $S$ vs. time and watch it tend to the maximum.
>
> **Verify.** Starting with all 20 particles on the left ($\Omega = 1$, $S = 0$), the system evolves to about 10 particles per side ($\Omega = 184756$, $S = k_B \ln 184756 \approx 12 k_B$). Maximum entropy state.

Save as `06b-entropy-preview.html`. Bridge to Chapter 7.

---

## What would change my mind

The Carnot theorem follows from the impossibility of perpetual motion. Every claimed violation of the second law over two centuries has been wrong (or undetectable). A reproducible experimental result violating the Carnot bound — say, an engine genuinely achieving efficiency above $1 - T_C/T_H$ with proper accounting of all heat inputs — would force a rewrite of thermodynamics. None has appeared.

What changes with engineering: real engines *approach* Carnot more closely as technology improves. Steam plants in the 1900s reached ~10% efficiency; modern combined-cycle gas plants reach 60%+; theoretical limits push higher. We're approaching the bound, not breaking it.

## Still puzzling

- *Why does the universe have an arrow of time?* The second law gives a direction; the underlying microscopic laws (Newtonian and quantum) are time-symmetric. The asymmetry comes from initial conditions — the universe started in a low-entropy state and is evolving toward higher entropy. *Why* the initial conditions were low-entropy is one of the deepest open questions in physics.
- *Can quantum effects beat Carnot?* Some research suggests certain quantum protocols can extract work in ways that classical engines can't — but always within the second law when properly accounted for. Quantum thermodynamics is an active frontier (Chapter 10 previews).
- *Maxwell's demon.* The thought experiment that's seemingly violates the second law. Resolved in Chapter 10: the demon's memory is itself an entropy-generating element when erased.

---

**Tags:** second law, Kelvin-Planck statement, Clausius statement, Carnot cycle, Carnot efficiency, Carnot theorem, reversible process, irreversible process, refrigerator, heat pump, COP, TS diagram

