# Research Notes: Chapter 09 — Thermodynamics in the Real World

**Source:** TIKTOC.md chapter entry (Chapter 09)
**Notes file:** 09-thermodynamics-real-world_notes.md
**Corresponding chapter:** chapters/09-thermodynamics-real-world.md (not yet written)
**Generated:** 2026-05-14

---

## Chapter summary (from TIKTOC.md)

Where theory meets engineering. Real heat engines operate well below their Carnot limits because every real process is irreversible. The chapter quantifies efficiency losses, analyzes Rankine (steam) and Brayton (gas-turbine) cycles, vapor-compression refrigeration, and addresses climate-relevant applications (heat pumps, data centers, Earth's climate as a heat engine).

---

## A. Conceptual foundations

### The Rankine cycle (steam power plants)

The Rankine cycle is the standard steam power plant cycle. Four processes:
1. **Isobaric heat addition (boiler):** liquid water is heated and vaporized at high pressure. $Q_H$ added.
2. **Adiabatic expansion (turbine):** steam expands through a turbine, doing work $W_T$.
3. **Isobaric heat rejection (condenser):** steam condenses to liquid at low pressure. $Q_C$ rejected.
4. **Adiabatic compression (pump):** liquid is pumped back to high pressure. Work $W_P$ in.

Net work: $W_{\text{net}} = W_T - W_P$. Efficiency: $\eta = W_{\text{net}}/Q_H$.

**Modern Rankine plants:** With superheat (heating steam above saturation) and reheat (re-heating after partial expansion), commercial steam plants reach 35–45% efficiency. The Carnot limit at typical operating temperatures ($T_H = 600$°C boiler, $T_C = 40$°C condenser): $\eta_{\text{Carnot}} = 1 - 313/873 \approx 64\%$. So real plants run at ~60% of the Carnot limit.

The 1–$\eta$ fraction (60–65% of input energy) is rejected as low-temperature heat — either to a cooling tower, a river, or the atmosphere. This is why power plants need cooling water and why waste-heat utilization is a frontier.

**Source:** Çengel & Boles, *Thermodynamics: An Engineering Approach*, Ch 10 (Rankine cycle).

### The Brayton cycle (gas turbines and jet engines)

The Brayton cycle is the gas-turbine and jet-engine cycle. Four processes:
1. **Adiabatic compression** (in the compressor).
2. **Isobaric combustion** (heat added at high pressure in the combustion chamber).
3. **Adiabatic expansion** (through the turbine; some work drives the compressor; the rest is net output).
4. **Isobaric heat rejection** (exhaust; for an open cycle, this is replaced by intake of fresh air).

Efficiency (ideal): $\eta = 1 - r_p^{(1-\gamma)/\gamma}$, where $r_p = P_{\text{high}}/P_{\text{low}}$ is the **pressure ratio** and $\gamma$ is the gas's heat-capacity ratio ($\sim 1.4$ for air).

**Modern combined-cycle plants:** A gas turbine (Brayton) generates electricity, and its exhaust heat drives a Rankine bottom cycle. Combined-cycle efficiencies reach ~61% as of recent state-of-the-art (DOE, 2020s data); targets are reaching 65%. This is one of the cleanest reductions to practice of thermodynamic principles in engineering.

**Source:** DOE — How Gas Turbine Power Plants Work, https://www.energy.gov/hgeo/how-gas-turbine-power-plants-work

### Vapor-compression refrigeration

Standard refrigerator and air-conditioner cycle. A refrigerant (R-134a, R-410a, propane in modern designs) cycles between liquid and vapor:
1. **Compression** (adiabatic): refrigerant compressed from low-pressure vapor to high-pressure vapor; $W$ in.
2. **Condensation** (isobaric): refrigerant cools and condenses at high pressure; $Q_H$ rejected to surroundings.
3. **Expansion** (throttling, irreversible): refrigerant pressure drops sharply; partial vaporization; some cooling.
4. **Evaporation** (isobaric): refrigerant absorbs $Q_C$ from refrigerated space and vaporizes.

**COP (Coefficient of Performance):** $\text{COP}_{\text{ref}} = Q_C/W$. Carnot COP: $T_C/(T_H - T_C)$. For a typical household refrigerator: $T_C \approx -18$°C (255 K), $T_H \approx 25$°C (298 K), Carnot COP ≈ 5.9. Actual COP: ~2–4 — about half of Carnot.

**Refrigerant history:** R-12 (Freon, CFC) was phased out (Montreal Protocol 1987, ozone-depleting). R-134a (HFC) replaced it but has high global warming potential. R-410a is being phased out in favor of low-GWP refrigerants (R-32, hydrocarbons, CO₂).

### Sources of irreversibility

Real engines fall short of Carnot because real processes are irreversible. The main mechanisms:

1. **Finite-temperature heat exchange.** Real heat exchangers operate with $\Delta T > 0$ — finite temperature differences between hot stream and cold stream. The entropy generation rate: $\dot{S}_{\text{gen}} = \dot{Q} \cdot (1/T_C - 1/T_H)$. To reduce, use larger heat-exchanger surface area (more expensive).

2. **Turbine and compressor inefficiency.** Real turbines extract less work than the isentropic ideal; real compressors require more work. Quantified by **isentropic efficiency** $\eta_{\text{isen}} = W_{\text{actual}}/W_{\text{isen}}$ (turbine) or $W_{\text{isen}}/W_{\text{actual}}$ (compressor). Typical modern turbines: 85–95%; compressors 80–90%.

3. **Pressure drop in heat exchangers and ducts.** Friction in pipes and coils means pressure must be raised more than the ideal cycle requires.

4. **Combustion inefficiency.** Real combustion is incomplete; some fuel doesn't burn; the products are not at the theoretical adiabatic-flame temperature.

5. **Heat leaks.** Any thermal contact between hot and cold parts of the system that isn't part of the intended cycle.

### Combined heat and power (CHP)

If a power plant's "waste heat" is captured and used for building heating or industrial process heat, the *overall energy utilization* can reach 80–90%. The plant's *electrical* efficiency might be 35–40% (lower than a pure-power plant because it operates at lower $T_H$ for the steam), but the rejected heat is no longer wasted. Net carbon advantage over separate electric grid + boiler heating.

CHP is widespread in district-heating cities (Copenhagen, much of Eastern Europe), industrial parks, and increasingly large data centers.

### Data centers as thermal machines

Modern data centers operate on the order of 100 MW to 1 GW of electrical power. Essentially all of this becomes heat — server CPUs convert essentially 100% of electrical power into heat (computation is thermodynamically nearly free at present; see Ch 10 for the Landauer limit). The data center is a giant heat engine running in reverse: electrical work → heat → must be removed.

**Power Usage Effectiveness (PUE)** = (Total facility power) / (IT equipment power). PUE = 1.0 is the ideal (all power goes to computing). Modern hyperscale data centers (Google, Microsoft, Meta) report PUEs of 1.1–1.2. Older facilities run 1.5–2.0.

**Free cooling:** at cold climates, outdoor air can directly cool data center server inlet to acceptable temperatures, reducing chiller energy. Major driver of data-center site selection (Iceland, Sweden, Pacific Northwest).

### Climate thermodynamics

The Earth's climate is a heat engine. Solar power ($\sim 1366$ W/m²) is absorbed mostly at the equator; heat is transported toward the poles by the atmosphere and oceans; long-wavelength IR is emitted back to space. The *temperature differential* between equator and pole drives circulation. The work extracted (kinetic energy of winds, ocean currents) is dissipated by friction. The whole system is a very inefficient heat engine operating between $\sim 300$ K (equator surface) and $\sim 220$ K (upper troposphere); Carnot-like upper bound on extractable work.

Climate change shifts the boundary conditions: changing the IR opacity of the atmosphere changes the equilibrium temperatures. The thermodynamic principles are exact; the application is complex.

---

## B. Domain examples and cases

### Case 1: Combined-cycle gas turbine power
A modern combined-cycle plant: 60+% electrical efficiency (DOE target 65%). The gas turbine operates at very high temperatures (1400°C+) — pushing close to material limits; the steam bottoming cycle uses the exhaust heat for additional power. The energy converted to electrons is roughly 60% of the chemical energy in the fuel; the rest is rejected to the atmosphere via cooling.

### Case 2: Combined Heat and Power district heating
Copenhagen's district heating system, built on CHP plants, achieves overall efficiencies > 80% by using both the electricity generated and the waste heat for building heating. Major reduction in fuel use compared to separate electricity grid + individual boilers.

### Case 3: Modern aircraft engines
The CFM LEAP engine (used in Boeing 737 MAX, Airbus A320neo) has a Brayton-cycle efficiency around 40%+ at cruise — among the highest of any deployed jet engine. Higher bypass ratios, ceramic-matrix-composite hot-section components, and improved compressor designs all push the cycle efficiency upward.

### Failure case: misapplication of the second law
A startup claims to have built a "thermodynamic anomaly" — a device that produces more energy than it consumes. Without exception, every such claim either (a) is wrong (the device is overunity only because some input is being mismeasured), or (b) doesn't actually work (the device's claimed performance is not reproducible).

The second law is the bedrock; engineering claims that violate it should be assumed wrong until proven otherwise.

---

## C. Connections and dependencies

**Prerequisites:** First law (Ch 4), PV diagrams (Ch 5), second law and Carnot (Ch 6), entropy (Ch 7), statistical mechanics (Ch 8).

**Unlocks:** Engineering thermodynamics careers, climate science thermodynamics, energy policy.

**Adjacent chapter connections:**
- Ch 8: statistical mechanics underlies the macroscopic engine behavior.
- Ch 10: the next chapter asks the deepest "why" question about irreversibility.

---

## D. Current state of the field

**Settled:**
- Rankine, Brayton, and vapor-compression cycles in their standard forms.
- Carnot efficiency as the upper bound on any heat engine.
- The principle: real engines are less efficient than ideal cycles because of irreversibility.

**Contested or emerging:**
- Supercritical CO₂ power cycles (vs. traditional steam Rankine): potentially higher efficiencies, more compact equipment. Active research at Sandia, DOE programs.
- Heat-pump refrigerants: ongoing transition from high-GWP HFCs to low-GWP alternatives.
- Direct air capture of CO₂: a thermodynamic process where you spend energy to concentrate CO₂. Climate-relevant emerging technology.

**Key references:**
1. Çengel & Boles, *Thermodynamics: An Engineering Approach* — the standard engineering thermodynamics textbook.
2. Moran, Shapiro, Boettner & Bailey, *Fundamentals of Engineering Thermodynamics* — alternative standard.
3. DOE Combined Heat and Power Technology fact sheet: https://betterbuildingssolutioncenter.energy.gov/sites/default/files/attachments/CHP_Steam_Turbines.pdf
4. DOE Gas Turbine Power Plants: https://www.energy.gov/hgeo/how-gas-turbine-power-plants-work
5. IEA reports on power generation efficiency.

**Recent developments:**
- Combined-cycle efficiencies pushing 65% (DOE Advanced Turbine Program targets).
- Supercritical CO₂ cycles approaching commercial deployment.
- Heat pumps for building electrification: rapid market growth, COP improvements.

---

## E. Teaching considerations

**Where students get stuck:**
- Distinguishing different cycle types — Rankine vs. Otto vs. Brayton. The standardized cycle-on-PV-diagram is the right tool.
- Why CHP isn't "free energy" — students sometimes think it violates the second law because the overall efficiency exceeds 50%. It doesn't; the *electrical* efficiency is still bounded by Carnot, but the rejected heat is no longer wasted.
- Sign conventions for refrigerator COP vs. heat-pump COP — they're not the same quantity, but they have a simple relation: COP_HP = COP_ref + 1.

**Analogies and framings that work:**
- *"Real engines are Carnot machines with handicaps."* Frames irreversibility as efficiency-loss-to-Carnot-bound.
- *"Cooling is just heating, run backwards, with work added."* Connects refrigerator and heat pump as the same physics.

**Exercises that build the target skill:**
- *Rankine efficiency at varying conditions* (Bloom: Apply) — compute $\eta$ for several $T_H, T_C$ pairs.
- *Combined cycle plant analysis* (Bloom: Apply + Analyze) — show why combining Brayton (top) + Rankine (bottom) gives higher overall efficiency than either alone.
- *Heat pump vs. electric resistance heating* (Bloom: Synthesize) — given typical heat-pump COP and grid efficiency, compute primary-energy savings.

---

## F. Library files relevant to this chapter

None.

---

## G. Gaps and flags

- FLAG: Refrigerant choices are a moving target (regulatory phase-outs, new low-GWP alternatives). Recommend writing in terms of generic refrigerant properties rather than naming specific compounds that may be obsolete.
- FLAG: Combined-cycle efficiency frontiers are pushing 65% as of mid-2020s. Numbers will date; flag with "[as of 2026]".
- GAP: Climate-thermodynamics treatment is necessarily brief in an intro chapter. The Earth's heat-engine framing is correct but pedagogically demanding; recommend a sidebar rather than a full subsection.
