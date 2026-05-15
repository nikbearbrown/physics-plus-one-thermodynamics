# Chapter 9 — Thermodynamics in the Real World

*Where Carnot bounds meet engineering reality: real cycles, real losses, real applications.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Analyze the Rankine cycle (steam power plant) computing efficiency and identifying superheat/reheat improvements.
2. **(Apply)** Analyze the Brayton cycle (gas turbine, jet engine) using pressure ratio and compute efficiency.
3. **(Apply)** Analyze the vapor-compression refrigeration cycle and compute real-world COP.
4. **(Analyze)** Identify sources of irreversibility in real devices and quantify their efficiency cost.
5. **(Understand)** Apply thermodynamic reasoning to data centers, climate systems, and combined-heat-and-power plants.
6. **(Apply)** Build a real-engine efficiency explorer.

---

## Opening case: why your house's heat pump might cost less than your gas furnace

A typical natural-gas furnace converts 90–96% of the chemical energy in the gas into heat. Sounds efficient. A typical air-source heat pump (a refrigerator running in reverse) consumes 1 kWh of electricity and delivers 3–4 kWh of heat to your house. Sounds *more* efficient — but it's pulling 2–3 kWh out of the cold outdoor air, not creating energy.

In a region with cheap electricity and mild winters, the heat pump's *cost-per-heat* is far below the gas furnace's. In a region with expensive electricity and very cold winters (where the heat pump struggles below freezing), gas wins.

The chapter ahead is *real-world thermodynamic engineering*. Not the textbook idealizations of Chapters 5–7, but the cycles real plants and refrigerators actually run, with the irreversibilities that make their efficiencies fall short of the Carnot bound. By the end, you'll be able to read efficiency specs for power plants, refrigerators, and engines — and understand why the numbers are what they are.

---

## Core concept

### The Rankine cycle: steam power plants

The Rankine cycle is the standard for steam-based power generation (coal, oil, nuclear, geothermal, concentrated solar). Four processes on a PV diagram:

1. **Isothermal boiling** (in the boiler): liquid water at high pressure is heated and vaporized. Heat $Q_H$ added.
2. **Adiabatic expansion** (through the turbine): high-pressure steam expands, driving the turbine. Work $W_T$ output.
3. **Isothermal condensation** (in the condenser): low-pressure steam condenses back to liquid. Heat $Q_C$ rejected.
4. **Adiabatic compression** (through the pump): liquid is pumped back to high pressure. Work $W_P$ input.

Net work: $W_{\text{net}} = W_T - W_P$. Efficiency: $\eta = W_{\text{net}}/Q_H$.

**Typical operating conditions** in a modern fossil-fuel plant:
- Boiler $T_H$: 600°C (873 K).
- Condenser $T_C$: 40°C (313 K).
- Carnot bound: $\eta_C = 1 - 313/873 = 64\%$.
- Actual efficiency: 35–45%. So real plants achieve ~60–70% of the Carnot limit.

**Superheat and reheat:** practical modifications. Superheat raises the steam's temperature above saturation; reheat does another partial expansion-and-superheat cycle. Both push efficiency closer to Carnot.

### The Brayton cycle: gas turbines and jet engines

The Brayton cycle is the gas-turbine cycle, used for stationary power generation, jet engines, and recently in combined cycles. Four processes:

1. **Adiabatic compression** (compressor): inlet air is compressed adiabatically to high pressure.
2. **Isobaric combustion** (combustion chamber): fuel is injected and burned; heat is added at constant pressure.
3. **Adiabatic expansion** (turbine): hot gas expands through the turbine, doing work.
4. **Isobaric exhaust** (open cycle): or for closed cycle, isobaric heat rejection.

**Ideal Brayton efficiency:**
$$\eta = 1 - r_p^{(1-\gamma)/\gamma}$$

where $r_p = P_{\text{high}}/P_{\text{low}}$ is the pressure ratio. For $r_p = 20$, $\gamma = 1.4$ (air): $\eta \approx 1 - 20^{-0.286} = 58\%$.

**Real gas turbines:** simple-cycle gas turbines achieve ~35-40% efficiency. **Combined cycle gas turbines** (CCGT) — using the gas turbine's exhaust to drive a Rankine bottom cycle — achieve 60-62% efficiency. The DOE Advanced Turbine Program targets 65%.

**Jet engines:** essentially Brayton cycles with the addition of a *fan stage* and ducted exhaust. Bypass ratio matters for fuel efficiency at cruise.

### Vapor-compression refrigeration

The standard cycle for refrigerators and air conditioners. A refrigerant alternates between liquid and vapor phases:

1. **Adiabatic compression**: low-pressure vapor compressed to high-pressure vapor. Work $W$ in.
2. **Isobaric condensation**: high-pressure vapor cools and condenses to liquid; heat $Q_H$ rejected to the surroundings.
3. **Throttling expansion** (irreversible): liquid pressure drops sharply; some vaporization; significant cooling.
4. **Isobaric evaporation**: refrigerant absorbs $Q_C$ from the refrigerated space and vaporizes.

**COP for refrigerator:** $\text{COP}_{\text{ref}} = Q_C/W$. Carnot COP: $T_C/(T_H - T_C)$.

For a household refrigerator:
- Freezer at $T_C = 255$ K, kitchen at $T_H = 295$ K.
- Carnot COP: $255/40 = 6.4$.
- Actual COP: 2–4. Real refrigerators run at 30–60% of Carnot.

**Refrigerant history.** R-12 (a chlorofluorocarbon, CFC) was phased out by the Montreal Protocol (1987) because of ozone depletion. R-134a (HFC) replaced it, but HFCs have high global-warming potential. Current transition: low-GWP refrigerants like R-32, propane (R-290), CO₂ (R-744 — a *natural* refrigerant).

### Sources of irreversibility in real devices

Real engines fall short of Carnot for specific, identifiable reasons:

1. **Finite-temperature heat exchange.** Real heat exchangers operate with $\Delta T > 0$. The entropy generation rate from heat $\dot{Q}$ flowing across $\Delta T$: $\dot{S}_{\text{gen}} = \dot{Q}(1/T_C - 1/T_H) > 0$. Smaller $\Delta T$ = lower irreversibility = larger heat-exchanger area (more capital cost).

2. **Turbine and compressor inefficiency.** Real turbines extract less work than the isentropic ideal. Real compressors require more work than ideal. Quantified by **isentropic efficiency**: $\eta_T = W_{\text{actual}}/W_{\text{isentropic}}$ for turbines; $\eta_C = W_{\text{isentropic}}/W_{\text{actual}}$ for compressors. Modern turbines: 85–95%; compressors: 80–90%.

3. **Pressure drops in heat exchangers**. Friction in pipes and coils means pressure can't be raised exactly to the design point.

4. **Combustion inefficiency**. Real combustion is incomplete (unburned fuel in the exhaust), and reaches less than the theoretical adiabatic flame temperature.

5. **Heat leaks.** Thermal contact between hot and cold parts of the system that isn't part of the intended cycle. Insulation can never be perfect.

### Combined heat and power (CHP)

If a power plant's "waste heat" is captured and used for building heating or industrial process heat, the *overall energy utilization* can reach 80–90%. The electrical efficiency might drop slightly (operating at lower $T_H$ for the steam), but the rejected heat becomes useful.

CHP is widespread in:
- Northern European district heating (Copenhagen, much of Eastern Europe).
- Industrial parks where process heat is needed nearby.
- Increasingly: large data centers, hospital campuses.

Net result: more efficient use of primary energy compared to separate electricity generation + dedicated boilers.

### Data centers as thermal machines

A modern data center operates on the order of 100 MW to 1 GW of electrical power. Essentially all of this becomes heat — CPU/GPU operations are thermodynamically "free" at present (see Ch 10 for the Landauer limit), so the data center is essentially a giant resistive heater plus pumps and refrigeration.

**Power Usage Effectiveness (PUE)** = (Total facility power) / (IT equipment power). PUE = 1.0 is the ideal. Modern hyperscale data centers (Google, Microsoft, Meta) report PUEs of 1.1–1.2. Older facilities run 1.5–2.0.

**Free cooling:** in cold climates, outdoor air can directly cool data-center server inlets, eliminating chiller energy. Major driver of data-center site selection (Iceland, Pacific Northwest, Sweden).

### Climate thermodynamics

The Earth's climate is a giant heat engine. Solar power (~1366 W/m² at top of atmosphere) is absorbed primarily at the equator; thermal IR is emitted everywhere, peaking at higher latitudes. The temperature differential drives atmospheric circulation (winds), ocean currents, and the hydrological cycle. The work extracted by the climate system (kinetic energy of winds and ocean currents) is eventually dissipated by friction back into heat.

A back-of-the-envelope Carnot analysis: $T_H = 300$ K (equator surface), $T_C = 220$ K (upper troposphere). $\eta_C = 1 - 220/300 = 27\%$. The actual conversion of solar heat to kinetic energy of climate is around 2–4% (much less than Carnot). The rest is dissipated directly as heat re-radiated to space.

Climate change shifts the boundary conditions: more IR absorption by greenhouse gases means more heat trapped, higher equilibrium temperatures, modified circulation patterns. The thermodynamic principles are exact; the application is complex.

---

## Worked example: a modern combined-cycle power plant

A combined-cycle plant has a gas turbine (Brayton) cycle with pressure ratio $r_p = 20$, inlet $T_1 = 290$ K, $\gamma = 1.4$. The gas turbine exhaust then drives a steam Rankine cycle with $T_{\text{boiler}} = 600$ K and $T_{\text{condenser}} = 310$ K.

**Gas turbine Brayton efficiency (ideal):**
$$\eta_B = 1 - r_p^{(1-\gamma)/\gamma} = 1 - 20^{-0.286} = 58\%$$

Real gas turbine: 38% (real isentropic efficiency, combustion losses, pressure drops).

**Rankine bottom cycle:**
$$\eta_R = 1 - T_C/T_H = 1 - 310/600 = 48\% \text{ (Carnot ideal)}$$

Real Rankine: 35%.

**Combined efficiency.** Heat input to gas turbine: $Q_{\text{fuel}}$. Gas turbine output: $0.38 Q_{\text{fuel}}$. Heat rejected by gas turbine (= input to Rankine): $0.62 Q_{\text{fuel}}$. Rankine output: $0.35 \times 0.62 Q_{\text{fuel}} = 0.22 Q_{\text{fuel}}$. Total electrical output: $0.38 + 0.22 = 0.60$, or **60%** of fuel energy.

Modern advanced combined-cycle plants do reach about this number. DOE Advanced Turbine Program targets 65%.

**Heat rejection:** $0.62 \times (1 - 0.35) Q_{\text{fuel}} = 0.40 Q_{\text{fuel}}$ rejected to the environment (typically a cooling tower or river).

**The lesson.** Combining cycles in series captures progressively more useful work from the heat stream. Each cycle alone is limited by Carnot; combining them captures more of the original heat as work.

**The limit.** This is for an idealized combined cycle. Real plants have additional losses: pressure drops in interconnect ducts, heat losses through insulation, parasitic loads (pumps, fans). Real combined-cycle efficiencies are typically 58–62%.

---

## Common misconceptions

**"All heat engines work the same way."** The Otto, Diesel, Rankine, Brayton, and refrigeration cycles all differ in process sequence. Each is optimized for different operating conditions.

**"CHP gives 'free' energy."** It captures *waste* heat that would otherwise be rejected. The electrical work is still bound by Carnot; the heat is just put to use rather than dumped.

**"Heat pumps create energy."** No. They move heat from outside (cool) to inside (warm). The work input is the cost; the heat delivered is greater than the work because most of it came from outdoors.

**"Carbon-free electricity solves the climate problem."** It addresses the *combustion* portion. Electricity generation accounts for ~25% of global greenhouse-gas emissions. Industry, agriculture, transportation, and buildings need parallel efforts.

**"Refrigerators violate the second law."** They don't. Work input is required. The total entropy of the universe (refrigerator + cold space + room) still increases.

---

## Exercises

**Warm-up (Apply).** A Rankine plant operates with $T_H = 850$ K (steam boiler) and $T_C = 320$ K (cooling tower). Find the Carnot efficiency limit. If the actual plant achieves 38%, what fraction of Carnot is that?

**Apply.** A gas turbine has $r_p = 15$, $\gamma = 1.4$, intake $T_1 = 300$ K. (a) Find the ideal Brayton efficiency. (b) After compression, what is the temperature? (Assume isentropic.) (c) If the actual isentropic efficiency of the compressor is 88%, what is the actual compressor outlet temperature?

**Apply.** A household refrigerator: $T_C = -10°$C (in the freezer compartment), $T_H = 25°$C (kitchen). (a) Find the Carnot COP. (b) If the actual COP is 2.5, find the electrical power needed to remove 1 kW of heat from the freezer. (c) Where does the extra energy go?

**Apply + Analyze.** A modern combined-cycle gas turbine plant burns $10^{12}$ Joules of natural gas per day. It achieves 60% overall efficiency. (a) Daily electrical output. (b) Daily heat rejected to the cooling tower. (c) Entropy generated per second by the heat rejection ($T_H = 600$ K, $T_C = 300$ K — simplified).

**Apply (Heat pump vs. resistance heat).** A house needs 5 kW of heat to maintain temperature against losses. Compare: (a) electrical resistance heating: cost in electricity? (b) Air-source heat pump with COP = 3.5: cost in electricity? Assume electricity is $\$0.15$/kWh.

**Challenge.** Climate thermodynamics estimate. The Earth absorbs about 175 PW of solar power (after albedo). The atmospheric heat engine converts about 4 PW (2.3%) of this into kinetic energy of winds. (a) Compute the average Carnot efficiency of this heat engine assuming $T_H = 290$ K, $T_C = 220$ K. (b) Why is the actual efficiency so much smaller? (Hint: not all the absorbed heat is "high temperature" in a sense that allows work extraction.)

---

## LLM Exercises

### Build the heat-engine efficiency explorer (`09-heat-engine-explorer.html`)

> **Show.** Various cycle efficiencies: Carnot ($1 - T_C/T_H$), Otto ($1 - 1/r^{\gamma-1}$), Rankine (depends on superheat, pressure), Brayton ($1 - r_p^{(1-\gamma)/\gamma}$).
>
> **Say.** Build an engine-efficiency comparison tool.
>
> **Constrain.** D3 v7. Engine selector (Carnot, Otto, Rankine simplified, Brayton, Vapor-compression refrigeration). Sliders for the relevant parameters: $T_H, T_C, r, r_p, \gamma$. Display: ideal efficiency from formula; actual efficiency (irreversibility slider, 0=ideal, 1=maximum losses); entropy generation rate; comparison Sankey diagram. Filename: `09-heat-engine-explorer.html`.
>
> **Verify.** (a) Carnot at $T_H = 600, T_C = 300$: 50% efficiency. (b) Otto at $r=10$, $\gamma=1.4$: 60% ideal. (c) Brayton at $r_p=20$, $\gamma=1.4$: 58% ideal. (d) Real engines at full irreversibility setting: half the ideal.

### Exploration

- Compare Otto and Brayton at the same compression ratio. Brayton is typically more efficient at lower pressure ratios; Otto wins at high.
- Build a refrigerator at $T_C = -18°$C, $T_H = 25°$C. The Carnot COP is 6.4; real COP 2.5–4.0. Why the gap?
- Try a CHP scenario (high-efficiency cycle followed by waste-heat recovery). Total energy utilization can exceed 80%.

### Extension prompt (chapter bridge)

> **Show.** Real engines lose efficiency to irreversibility. But where does the deepest irreversibility come from? Maxwell's demon suggests there might be a thermodynamic cost for *information*.
>
> **Say.** Build a Maxwell's-demon simulator showing the second law surviving information-processing.
>
> **Constrain.** A box with N particles, a "demon" at a door that opens for fast particles going one way. After M cycles, the demon's memory has stored M bits. Compute the entropy reduction of the gas; compare to the entropy cost of erasing the demon's memory at Landauer's bound.
>
> **Verify.** When you include memory erasure, total entropy of (gas + memory + environment) is non-negative — second law holds.

Save as `09b-maxwells-demon-preview.html`. Bridge to Chapter 10.

---

## What would change my mind

The thermodynamic cycle formulas (Rankine, Brayton, vapor-compression) are standard engineering tools, confirmed by power-plant and refrigeration performance for over a century. The Carnot bound has never been exceeded. Real engines fall short of Carnot for identifiable reasons; engineering progress reduces (but never eliminates) the gap.

What changes: refrigerants, fuels, turbine materials, control systems, manufacturing precision. The *physics* (Carnot, entropy generation, isentropic efficiency) is stable.

## Still puzzling

- *How far can combined cycles go?* DOE targets are pushing 65% electric efficiency. Beyond that requires materials and engineering breakthroughs (higher firing temperatures, fewer pressure losses). The theoretical limit for the chosen $T_H, T_C$ is Carnot.
- *Climate as a heat engine.* The Earth converts a small fraction of absorbed solar power into kinetic energy of winds. The detailed budget — how much goes to kinetic energy vs. radiation vs. various heat transfers — is an active climate-science topic. The thermodynamic *framework* is settled.
- *Quantum advantages.* Quantum engines (cooling using laser cooling, harvesting quantum coherence) are an active research frontier. Whether they can practically exceed classical engines in some regime is not yet clear.

---

**Tags:** Rankine cycle, Brayton cycle, vapor-compression refrigeration, combined cycle, isentropic efficiency, combined heat and power, PUE, data center, climate thermodynamics

