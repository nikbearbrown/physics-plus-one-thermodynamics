# Chapter 7 — Thermodynamics

**Suggested titles**

1. Thermodynamics
2. The Engine, the Refrigerator, and the One-Way Arrow
3. Why Your Car Engine Wastes Two-Thirds of Its Fuel by Law

**TL;DR.** Thermodynamics is the discipline of accounting for energy when heat is one of the currencies. Three laws do almost all the work: energy is conserved (the first), heat refuses to flow uphill on its own (the second), and entropy — a count of microscopic arrangements — only increases in any closed process. By the end of the chapter you should be able to compute an engine's efficiency, a refrigerator's coefficient of performance, and the entropy change of a process you can describe.

---

## A Texas refinery, gasoline, and a 30%-efficient engine

A barrel of crude oil holds about 6.1 GJ of chemical energy. Refine it, ship it to a station, and pump 50 liters into a typical 2025-model gasoline car. That tank holds roughly 1.7 GJ of chemical energy — enough, in principle, to lift the car 60,000 m straight up. The car uses it to go about 700 km on a highway.

Where did most of the energy go?

Almost two-thirds of it left the engine as heat — in the radiator, in the exhaust, in the warm undercarriage you can feel after a long drive. The car turned only about 25–35% of the chemical energy into useful work moving the vehicle forward. This is not because gasoline engineers have been lazy or because the auto industry is hiding a better engine. It is because *no engine that takes in heat at one temperature and exhausts it at another can do better than a specific, calculable maximum efficiency*, and modern car engines already operate close to that maximum.

The maximum was first computed in 1824 by a 28-year-old French military engineer named Sadi Carnot, watching the coal-burning steam engines that were transforming the British economy. Carnot worked it out before the words *energy* and *thermodynamics* even existed in their modern form. His answer, simplified to its essence, is

$$\text{Eff}_\text{max} = 1 - \frac{T_c}{T_h},$$

where $T_h$ is the absolute temperature at which the engine takes in heat and $T_c$ is the temperature at which it exhausts it. For a gasoline engine running at about 2200 K combustion and exhausting near 600 K, the maximum is about 73%. Real engines lose another 40 percentage points to friction, incomplete combustion, and unrecoverable expansion, leaving the 25–35% the car actually delivers. The hard ceiling is set by the law. The gap below the ceiling is set by the engineering.

This chapter is about that law and what flows from it.

**Learning objectives.** By the end of this chapter you should be able to:

1. State the first law of thermodynamics ($\Delta E_\text{int} = Q - W$) and apply it to a gas, an engine, or a biological organism.
2. Identify isobaric, isochoric, isothermal, and adiabatic processes on a $PV$ diagram, and compute the work done in each.
3. State the second law in three equivalent forms (Kelvin: heat→work limited; Clausius: heat won't flow uphill; entropy: $\Delta S \geq 0$ in a closed system).
4. Compute the efficiency of a heat engine and the Carnot maximum for given $T_h, T_c$.
5. Compute the coefficient of performance of a refrigerator or heat pump.
6. Compute entropy changes for simple reversible heat transfers and reason about microstate counts.

**Prerequisites.** Chapter 7 (work, energy), Chapter 13 (ideal gas, kinetic theory), Chapter 14 (heat transfer modes, $Q = mc\Delta T$).

**Why this chapter matters.** Almost every conversion of energy from one form to another in your life involves a heat-engine cycle — the engine in your car, the turbine in the power plant, the air conditioner in the room you are in, the metabolism that keeps you at 37 °C. The laws below are the operating manual.

---

## Concept 1 — The first law: bookkeeping for heat and work

### Lavoisier's calorimeter, 1782, and the guinea pig that warmed it

In the winter of 1782, Antoine Lavoisier and Pierre-Simon Laplace built a contraption in a Paris laboratory that looked like a nested set of metal buckets. The inner bucket held an animal — a guinea pig, in their famous version — surrounded by a layer of ice. As the animal's body heat melted the ice, water dripped out, and Lavoisier measured the dripped water. The mass of melted water times the latent heat of fusion told him how many calories the animal had given off in the time of the experiment.

Then he had the animal eat a measured mass of food, and a separate apparatus burned an identical mass of the same food in pure oxygen, measuring the heat released by combustion. The two heat outputs — animal metabolism, oxidative combustion — agreed to within his measurement uncertainty.

Lavoisier had stumbled into the first law of thermodynamics half a century before it was named. *Energy in equals energy out.* The animal was not a magical heat source; it was a slow-burning piece of food. The chemical energy of the food, oxidized by breathing, came out as heat at exactly the rate the chemistry predicted.

This is the bookkeeping principle the rest of this concept formalizes.

### The mechanism — the first law

The **first law of thermodynamics** states that the change in the internal energy of a system equals the net heat transferred *into* the system minus the net work done *by* the system:

$$\Delta E_\text{int} = Q - W.$$

The sign convention: $Q$ is positive when heat flows *in*, and $W$ is positive when the system does work on the surroundings. So heat in raises the internal energy, work done by the system lowers it.

**Internal energy** $E_\text{int}$ is the sum of all the kinetic and potential energies of every molecule inside the system. For an ideal gas, it depends only on temperature: $E_\text{int} = \frac{3}{2} N k_B T$ for a monatomic gas. For real substances it depends on temperature, pressure, and what molecular bonds are doing.

The first law is just energy conservation, with heat and work as the two channels of transfer. It does not say which direction energy will flow. It does not say what fraction of heat can be turned into work. It is the bare ledger: input minus output equals change in storage.

### The trade-off

The first law trades **direction for universality.** It applies to every system in every situation — a gas in a piston, a battery in a flashlight, a person on a treadmill, a galaxy emitting starlight. Its price is silence on direction. The first law is satisfied by *every* process, including ones that never happen. A puddle freezing on a hot sidewalk does not violate the first law; it just doesn't happen. We need the second law to forbid it.

### Worked example — the metabolic ledger

A 70-kg cyclist climbs a hill, gaining 100 m of elevation, in 30 minutes. Her body runs at about 25% mechanical efficiency. How much chemical energy did she burn? How much heat did her body release?

**Reasoning.** Useful work done against gravity: $W = mgh = (70)(9.80)(100) = 6.86 \times 10^4 \text{ J} \approx 68.6 \text{ kJ}$.

If 25% of the burned chemical energy became work, the total chemical energy burned was $E_\text{chem} = W/0.25 = 274 \text{ kJ}$.

The remaining 75% became heat: $Q_\text{heat} = E_\text{chem} - W = 206 \text{ kJ}$, released over 30 minutes (1800 s), giving a heat rate of about $114 \text{ W}$ — comfortably above sedentary metabolism (~100 W) and consistent with sweating during exercise.

**Sanity check.** 274 kJ is about 65 food kcal — the energy in a small banana. A short uphill commute "costs" about a banana. That is not far off published metabolic estimates, which is a good sign.

### Common misconceptions

- *"The first law tells you how efficient an engine can be."* It does not. The first law says you cannot output more than you input. The second law sets the actual ceiling on efficiency.
- *"Internal energy and heat are the same thing."* They are not. Internal energy is a *property* of a system (it has a definite value at each state). Heat is a *process* — energy in transit across a boundary. The same internal energy can be reached by adding heat or by doing work.

↳ **Dig Deeper — Why work and heat are not state variables**

*The first law looks innocuous, but it conceals a subtle distinction. Internal energy depends only on the current state of the system; heat and work depend on how you got there. This difference shapes the entire mathematical structure of thermodynamics — it is why we write $\Delta E_\text{int}$ but never $\Delta Q$ or $\Delta W$.*

**Prompt:**
> Explain the distinction between state functions (like internal energy, temperature, pressure) and path functions (like heat and work) in thermodynamics. Use the example of a gas being expanded from state A to state B by two different paths (e.g., isothermal vs. adiabatic-then-isobaric). Show that ΔE_int is the same for both paths, but Q and W are not. End with one sentence on why this distinction is the mathematical reason we never write "the heat content of an object."

**What to do with the output:** Save it. The state vs. path distinction is the conceptual key to enthalpy, free energy, and chemical thermodynamics in any later course.

---

## Concept 2 — The PV diagram, processes, and the heat engine

### Watt's separate condenser, Glasgow 1765

The James Watt steam engine was not the first steam engine. Newcomen's atmospheric engine had been pumping water out of British coal mines since 1712. What Watt did, walking across Glasgow Green in 1765, was figure out *why* Newcomen engines wasted so much fuel — and his answer was the seed of an entire science.

A Newcomen engine cooled its working cylinder with a spray of cold water on every stroke, condensing the steam to pull the piston down. That meant the cylinder had to be reheated by the next charge of steam — and most of the fuel went into reheating cold metal. Watt's insight: condense the steam in a *separate* chamber, kept cold continuously, while keeping the working cylinder hot continuously. Same temperature difference between hot and cold; far less energy wasted reheating.

Watt's separate condenser was a 200% improvement in fuel efficiency, more or less, and it ushered in the era of practical steam power. But the deeper move — *the working substance moves through a cycle, taking in heat at high temperature and releasing it at low temperature, doing useful work in between* — is the universal architecture of every heat engine ever built. Cars, jets, coal plants, your refrigerator running backwards: all the same diagram.

To draw the diagram, we use a $PV$ plot.

### The mechanism — the $PV$ diagram and the four canonical processes

A gas at any instant has a pressure $P$ and a volume $V$. Plot $P$ vertical, $V$ horizontal, and any state is a point. Any process — slow enough to be quasi-static — is a path on the plane. The work done *by* the gas in a process is the area under that path:

$$W = \int P \, dV.$$

(For introductory problems, we will compute this geometrically rather than with calculus.)

Four idealized processes recur:

**Isobaric** — constant pressure. The path is a horizontal line. Work: $W = P \Delta V$.

**Isochoric** (or isovolumetric) — constant volume. The path is a vertical line. Work: $W = 0$ (no volume change, no displacement).

**Isothermal** — constant temperature. For an ideal gas, $PV = nRT$ is constant, so the path is a hyperbola. Internal energy doesn't change ($\Delta E_\text{int} = 0$ since $T$ is constant), so by the first law, $Q = W$. Whatever heat goes in comes out as work.

**Adiabatic** — no heat transfer ($Q = 0$). Common when a process is fast, so heat doesn't have time to flow. By the first law, $W = -\Delta E_\text{int}$. If the gas does work, its internal energy (and temperature) drops. This is why a bicycle pump gets warm when you compress air rapidly, and why expanding gas (a CO₂ fire extinguisher, the air leaving an aerosol can) feels cold.

A **heat engine** is a system that runs in a closed loop in the $PV$ plane: a working substance is heated, expands and does work, then is cooled and compressed back to its starting state. The net work per cycle is the *area enclosed by the loop*. The efficiency is

$$\text{Eff} = \frac{W}{Q_h} = \frac{Q_h - Q_c}{Q_h} = 1 - \frac{Q_c}{Q_h},$$

where $Q_h$ is heat in from the hot reservoir and $Q_c$ is heat out to the cold reservoir. The first law guarantees the total heat in minus total heat out equals the work done. The second law, in a moment, will tell us how much $Q_c$ we cannot avoid throwing away.

### The trade-off

The $PV$-diagram description trades **microscopic detail for macroscopic clarity.** Every dot on a $PV$ plane represents a vast collection of molecular states; we are summing over them and tracking only the bulk properties. The cost: we cannot see, on a $PV$ diagram, *why* a process is irreversible — we only see that it is. The benefit: we can compute the work and heat for a real engine by looking at the area of a loop on a graph.

### Worked example — Otto cycle (the gasoline engine, idealized)

A simplified four-stroke gasoline engine cycle:

1. **Intake (isobaric):** piston moves down, gas-air mixture enters at atmospheric pressure.
2. **Compression (adiabatic):** piston moves up, compressing the mixture rapidly.
3. **Combustion (isochoric):** spark ignites mixture; pressure shoots up at ~constant volume.
4. **Power stroke (adiabatic):** hot high-pressure gas expands, pushing piston down.
5. **Exhaust (isobaric):** spent gas pushed out, returning to start.

The adiabatic steps are where the temperature swings are large and where most of the work is exchanged. The work output per cycle is the enclosed area. The thermodynamic efficiency of an idealized Otto cycle (assuming an ideal gas):

$$\text{Eff}_\text{Otto} = 1 - \frac{1}{r^{\gamma - 1}},$$

where $r$ is the compression ratio (volume at bottom of stroke / volume at top) and $\gamma$ is the ratio of specific heats (about 1.4 for air). For a typical car with $r = 10$:

$$\text{Eff}_\text{Otto} = 1 - \frac{1}{10^{0.4}} \approx 1 - 0.398 \approx 0.602 = 60.2\%.$$

Real Otto-cycle gas engines deliver more like 25–35%. The gap is friction, incomplete combustion, heat loss through cylinder walls, and the fact that the cycle is not actually quasi-static. The 60% is an aspiration; the 30% is the engineering reality.

### Common misconceptions

- *"Adiabatic means insulated."* Not necessarily. Adiabatic means no heat *transferred* during the process. A fast process can be adiabatic even if no insulation is in place — the heat just doesn't have time to flow.
- *"Work done is just $P\Delta V$."* Only when $P$ is constant. For varying pressure, work is the *area under the curve* on a $PV$ diagram, which requires integration.
- *"A cycle returns to the same state, so no net change."* True for the gas — but heat has flowed in from a hot reservoir and out to a cold one, and net work has been done on the surroundings. The gas didn't change. The world around it did.

↳ **Dig Deeper — The $PV$ diagram and the area-equals-work theorem**

*The claim that work done equals the area under a $PV$ curve is one of the most useful results in thermodynamics, but seeing exactly why takes a moment of geometric reasoning. It also explains why the area enclosed by a closed cycle equals the net work per cycle.*

**Prompt:**
> Walk me through why the work done by a gas during a process equals the area under the curve on a $PV$ diagram. Start from the definition $dW = F\,dx = PA\,dx = P\,dV$ and integrate. Then show that for a closed cyclical process (a loop on the $PV$ plane), the net work per cycle equals the *enclosed* area, and that the sign depends on whether you traverse the loop clockwise (engine) or counterclockwise (refrigerator). End with one sentence on why this geometric reasoning is the basis for designing efficient engine cycles.

**What to do with the output:** Save it. The same area-equals-work logic underlies the Carnot cycle (next concept) and any thermodynamic cycle a chemical engineer or aerospace engineer will design.

---

## Concept 3 — The second law, Carnot, and entropy

### A drop of ink in a glass of water

Drop a single drop of black ink into a tall glass of still water. Watch it for ten minutes. The ink unfolds into a delicate plume, then a swirl, then a haze, and eventually disappears into uniform light gray. Now wait. Wait an hour. Wait a year. The ink will not, on its own, regroup into a drop. The molecular motions that mixed it are still happening — every individual collision is microscopically reversible — but the bulk un-mixing never occurs.

This is the second law of thermodynamics, in a glass of water.

The first law forbids you from getting more energy out than you put in. The second law forbids the un-mixing. Both are universally true, both have been tested to extraordinary precision, and the second one is the one with mood: it specifies the direction of time as a thermodynamic concept.

### The mechanism — three statements of the second law

The second law has been stated three different ways, all equivalent:

**Kelvin–Planck statement:** *No heat engine can operate in a complete cycle and have its sole result be the conversion of heat from a single reservoir entirely into work.* You cannot run an engine off a single bath of warm water; you need two reservoirs at different temperatures, and you must dump some heat into the cold one.

**Clausius statement:** *Heat does not spontaneously flow from a colder body to a hotter body.* It can be made to flow that way (a refrigerator does it), but only with work input — the cold body and the hot body together cannot lose entropy without that input.

**Entropy statement:** *In any spontaneous process, the total entropy of an isolated system increases or stays the same: $\Delta S \geq 0$.* Reversible processes have $\Delta S = 0$. Real processes have $\Delta S > 0$. There is no process with $\Delta S < 0$ in an isolated system.

All three are saying the same thing in different words. The third (Boltzmann's) reformulation is the most powerful, because it lets you compute.

### Carnot's bound on efficiency

Sadi Carnot showed in 1824 that the maximum possible efficiency of any heat engine operating between hot reservoir at $T_h$ and cold reservoir at $T_c$ is

$$\text{Eff}_\text{Carnot} = 1 - \frac{T_c}{T_h},$$

with both temperatures in *kelvin*. This is independent of the working substance — gas, liquid, or anything else. It is set by the second law alone.

For a steam plant with $T_h = 825 \text{ K}$ (550 °C steam) and $T_c = 300 \text{ K}$ (room temperature exhaust):

$$\text{Eff}_\text{Carnot} = 1 - \frac{300}{825} = 1 - 0.364 = 0.636 = 63.6\%.$$

Modern coal plants achieve about 35–45%, slightly above half of Carnot. The remaining gap is irreversibility — friction, turbulence, finite-temperature heat transfer.

### Refrigerators and heat pumps

A refrigerator is a heat engine run backward. You put in work $W$, the device pumps heat $Q_c$ from a cold reservoir (the inside of the fridge) to a hot reservoir (the kitchen), with total heat dumped to the kitchen $Q_h = Q_c + W$ (first law). Its **coefficient of performance** is

$$\text{COP}_\text{ref} = \frac{Q_c}{W},$$

the ratio of cooling delivered to work paid for. For a Carnot refrigerator,

$$\text{COP}_\text{ref,Carnot} = \frac{T_c}{T_h - T_c}.$$

Notice that COP is *not* bounded by 1. A typical kitchen refrigerator (cold = 277 K, hot = 300 K) has Carnot COP ≈ 12; real refrigerators run around 2–4. A heat pump used for home heating uses the same hardware to deliver $Q_h$ to the warm interior:

$$\text{COP}_\text{HP} = \frac{Q_h}{W} = \frac{T_h}{T_h - T_c} \quad \text{(Carnot limit)}.$$

A heat pump moving heat from 0 °C outside to 20 °C inside has Carnot COP ≈ 14, real COP ~3-4 — meaning every joule of electricity delivers 3–4 joules of heating. This is the physics that makes heat pumps so much more efficient than baseboard electric heaters (which convert 1 J of electricity to 1 J of heating, COP = 1).

### Entropy, in the form Clausius wrote it

For a reversible heat transfer of $Q$ at temperature $T$ (in kelvin), the entropy change of the system is

$$\Delta S = \frac{Q}{T}.$$

If 1000 J of heat flows reversibly from a reservoir at $T_h = 600 \text{ K}$ to one at $T_c = 300 \text{ K}$:

- Hot reservoir loses entropy: $\Delta S_h = -1000/600 = -1.67 \text{ J/K}$.
- Cold reservoir gains entropy: $\Delta S_c = +1000/300 = +3.33 \text{ J/K}$.
- Total: $\Delta S_\text{universe} = +1.67 \text{ J/K}$.

Heat naturally flowed from hot to cold and the total entropy increased. This is the second law at work, computed in joules per kelvin.

### Boltzmann's microstate count

The deepest statement: entropy is the (logarithm of the) number of microscopic arrangements consistent with the macroscopic state.

$$S = k_B \ln \Omega,$$

where $\Omega$ is the number of microstates, $k_B = 1.38 \times 10^{-23} \text{ J/K}$ is Boltzmann's constant, and the formula is on Boltzmann's tombstone in Vienna. A drop of ink mixed into water has astronomically more microstates than a drop of ink concentrated in one spot. The second law says: systems evolve toward more probable arrangements. Always. Because there are vastly more disordered states than ordered ones.

### The trade-off

Entropy as a tool trades **intuitive accessibility for predictive power.** The word *entropy* is famously slippery; it is "disorder" only loosely, and "unavailable energy to do work" only in some contexts. But once you have the formula $S = k_B \ln \Omega$, you can compute. You can predict that an isolated gas will spread to fill its container, that a hot cup of coffee in a cool room will cool, and that the universe taken as a whole evolves toward higher entropy. The conceptual fuzz at the edges is the price of one of the most accurate predictions physics makes.

### Worked example — Carnot efficiency for a nuclear plant

A pressurized-water nuclear reactor delivers steam at $T_h = 575 \text{ K}$ (about 300 °C) and exhausts to a cooling tower at $T_c = 308 \text{ K}$ (about 35 °C, river or lake water with some warming). The Carnot maximum:

$$\text{Eff}_\text{Carnot} = 1 - \frac{308}{575} = 1 - 0.536 = 0.464 = 46.4\%.$$

Real US nuclear plants achieve about 32–34% thermal efficiency. The 12-point gap below Carnot is friction, heat exchanger inefficiency, and the fact that plant operators run the cycle below the absolute maximum to keep reliability high. The Carnot bound is not an embarrassment; it is the law that makes the engineering question "how close to Carnot can we get?" well-posed.

### Common misconceptions

- *"Entropy is disorder."* Useful metaphor, slippery technical claim. Entropy is the (logarithm of the) count of microstates. A "disordered" room has more arrangements than a "tidy" one, which is why the metaphor works — but a perfectly ordered crystal at 0 K has zero entropy, and a slightly less ordered crystal at 1 K has tiny but nonzero entropy. Count microstates, don't argue about tidiness.
- *"The universe is running down to heat death."* The second law does predict that an isolated universe evolves toward maximum entropy ("heat death"), but the timescale is enormous and the assumptions about cosmology are not airtight. We will revisit this with appropriate uncertainty in later cosmology chapters.
- *"You can't compress a gas without heating it."* You can — slowly, through an isothermal process with a heat reservoir absorbing the heat. The fast (adiabatic) compression heats the gas because there is no time to dump the heat.

↳ **Dig Deeper — Why the Carnot bound depends on temperature ratios**

*The Carnot formula $\text{Eff} = 1 - T_c/T_h$ is striking in its simplicity. It depends only on the two reservoir temperatures and not at all on the working substance. Understanding why takes a careful look at the entropy bookkeeping during a Carnot cycle.*

**Prompt:**
> Walk me through why the Carnot efficiency depends only on $T_c$ and $T_h$ and not on the working substance. Start with the entropy balance: in a reversible cycle, entropy in equals entropy out, so $Q_h/T_h = Q_c/T_c$. Combine with the first-law statement $W = Q_h - Q_c$ to derive $W/Q_h = 1 - T_c/T_h$. Then explain why no real engine can do better: any irreversibility generates extra entropy that must be dumped to the cold reservoir, increasing $Q_c$ and lowering efficiency. End with one sentence on what this means practically — why running the hot reservoir hotter (turbine inlet temperature) is the single highest-leverage variable in power-plant design.

**What to do with the output:** Save it. The Carnot bound governs everything from your refrigerator to a fusion reactor. Worth carrying in your head.

---

## Synthesis — three laws, one architecture

Step back. Three laws, related but distinct:

1. **First law: $\Delta E_\text{int} = Q - W$.** Energy is conserved; heat and work are two channels of transfer. Says nothing about direction.

2. **Second law: $\Delta S_\text{universe} \geq 0$.** Heat flows from hot to cold; engines cannot exceed Carnot efficiency; entropy of an isolated system never decreases. Says everything about direction.

3. **(Implied third law, mentioned for completeness): $S \to 0$ as $T \to 0 \text{ K}$.** A perfect crystal at absolute zero has zero entropy. We will not use this in this chapter; mention it now so it doesn't surprise you in chemistry.

Together, the first and second laws govern every heat engine, refrigerator, and metabolic process you will ever encounter. The first sets the energy ledger. The second sets the direction and the maximum efficiency.

### A worked example combining all three concepts — a coal plant's CO₂ output

A 1 GW coal plant burns coal at $T_h = 800 \text{ K}$ and exhausts to $T_c = 300 \text{ K}$. It delivers electricity at 35% thermal efficiency. Coal has heat of combustion about 30 MJ/kg, and burning 1 kg of coal releases about 2.5 kg of CO₂. How much CO₂ does this plant emit per second?

**Step 1 — Carnot bound check.** $\text{Eff}_\text{Carnot} = 1 - 300/800 = 0.625$. The plant's 35% is comfortably below this — physically allowed.

**Step 2 — Heat input rate.** The plant outputs $W = 1 \text{ GW} = 10^9 \text{ J/s}$ of electricity. At 35% efficiency, the heat input rate is

$$\frac{Q_h}{t} = \frac{W/t}{\text{Eff}} = \frac{10^9}{0.35} \approx 2.86 \times 10^9 \text{ J/s}.$$

**Step 3 — Coal burn rate.** Coal energy density 30 MJ/kg = $3 \times 10^7$ J/kg, so

$$\frac{m_\text{coal}}{t} = \frac{2.86 \times 10^9}{3 \times 10^7} \approx 95 \text{ kg/s}.$$

**Step 4 — CO₂ rate.** $\frac{m_{\text{CO}_2}}{t} = 2.5 \times 95 \approx 240 \text{ kg/s}$ — roughly 20,000 metric tons per day, or 7 million metric tons per year.

**Step 5 — Heat to the cold reservoir.** $Q_c/t = Q_h/t - W/t = 2.86 \times 10^9 - 10^9 \approx 1.86 \times 10^9$ W = 1.86 GW dumped into a river or cooling tower. That is why coal plants need so much cooling water, and why their physical footprint includes those huge concrete cooling towers.

**Scale shift.** That same arithmetic, scaled down by a factor of $10^9$, governs the 1 W metabolic heat output and 0.5 W mechanical output of a small bird. The first law balances the energy budget; the second law sets the maximum work fraction; the metabolic efficiency falls below it for the same reason coal plants fall below Carnot. Engines and animals obey the same laws.

---

## Exercises

### Warm-up

**15.1** *(LO 1)* A gas absorbs 200 J of heat and does 150 J of work on its surroundings. What is the change in its internal energy?

**15.2** *(LO 2)* A gas at 1.0 atm pressure expands isobarically from 2.0 L to 5.0 L. How much work does it do? (1 atm·L ≈ 101.3 J.)

**15.3** *(LO 4)* A Carnot engine operates between 600 K and 300 K. What is its maximum efficiency?

**15.4** *(LO 5)* A refrigerator extracts 500 J of heat from its cold interior using 100 J of electrical work. What is its coefficient of performance?

### Application

**15.5** *(LO 1, 4)* A car engine burns 1 L of gasoline (energy density 32 MJ/L) at 30% efficiency. How much useful mechanical work was done? How much heat was rejected to the environment?

**15.6** *(LO 4)* A geothermal power plant operates with hot brine at 200 °C and cold cooling water at 25 °C. (a) What is the Carnot maximum efficiency? (b) If the actual plant achieves half of Carnot, what fraction of the input heat becomes electricity?

**15.7** *(LO 2)* Sketch (or describe) the four-step cycle of an idealized Stirling engine: isothermal expansion at $T_h$, isochoric cooling to $T_c$, isothermal compression at $T_c$, isochoric heating back to $T_h$. Indicate where heat is added and removed, and where work is done by/on the gas.

**15.8** *(LO 5, 6)* A heat pump delivers 5000 W of heating to a house when the outside is at 0 °C and inside is 20 °C. (a) Compute the Carnot COP. (b) If the actual COP is 3.5, how much electrical power is the pump drawing?

### Synthesis

**15.9** *(LO 1, 4)* The human body burns food at about 25% mechanical efficiency for sustained cycling. A cyclist riding for 1 hour at 200 W mechanical output. (a) How much chemical energy was burned? (b) How much heat must be dissipated by sweating and other means? (c) Express the chemical energy in dietary kilocalories — does the answer match a typical "calories burned" estimate?

**15.10** *(LO 6)* 1.00 kg of water at 100 °C is poured into a very large reservoir at 0 °C. Compute the entropy change of (a) the water, (b) the reservoir, (c) the universe. Use approximations as needed; show your reasoning.

**15.11** *(LO 4, 6)* "Heat death of the universe" is the prediction that the universe's entropy will reach a maximum and useful work will become impossible. Explain in one paragraph why this is a *probabilistic* statement, not a *forbidden-by-conservation-of-energy* statement. What would have to happen physically for the prediction to be wrong?

### Challenge

**15.12** *(LO 4, beyond chapter)* A combined-cycle natural gas power plant uses a gas turbine with $T_h = 1700 \text{ K}$ exhausting at 850 K, and the 850 K exhaust drives a steam turbine cycling between 850 K and 310 K. Compute the Carnot maxima for each cycle and the *combined* maximum if both stages are reversible. Modern combined-cycle plants achieve about 60% thermal efficiency in practice — how does that compare to your computed combined Carnot maximum?

**15.13** *(LO 6, beyond chapter)* A small set of N coins is tossed simultaneously. (a) For N = 4, list every macrostate (number of heads) and its multiplicity. (b) For N = 100, the most probable macrostate is 50 heads. Roughly how much more probable is 50 heads than 25 heads? (Use Stirling's approximation or a computer.) (c) Connect this to the second law: why does this combinatorial fact imply that gas molecules in a box will spread out and never spontaneously congregate in one corner?

---

## LLM Exercise — Chapter 15: Efficiency and Entropy in Your Anchor Phenomenon

**Project:** Physics Reality Check Logbook
**What you're building this chapter:** An efficiency calculation (and ideally an entropy estimate) for one heat-engine-like or work-conversion process inside your anchor phenomenon.
**Tool:** Claude Project.

### The Prompt

```
I'm continuing my Physics Reality Check Logbook for College Physics with LLMs. My anchor phenomenon is [paste from Chapter 1].

For Chapter 15 (Thermodynamics), I want to identify ONE energy-conversion moment in my phenomenon that operates as some kind of heat engine, refrigerator, or biological metabolism, and compute an efficiency for it.

Please:

1. Identify the conversion. Examples:
   - Coffee maker: how much electricity → heat in coffee → heat lost to air?
   - Bike commute: chemical energy in food → mechanical work pedaling → heat dumped from body. What's the metabolic efficiency?
   - Marathon: same, integrated over 4 hours.
   - Car commute: chemical energy in gasoline → mechanical work moving the car → waste heat in radiator/exhaust.
   - Espresso machine: electrical energy → boiler heat → pressure → kinetic energy of water through grounds. Where does most of the energy go?

2. Identify the relevant temperatures (T_hot reservoir, T_cold reservoir if applicable). Compute the Carnot bound. Compare to the actual efficiency.

3. Estimate the entropy generated per use. Use ΔS = Q/T for the heat dumped to the cold reservoir. Report in J/K.

4. State the inputs you used (sources, uncertainty).

5. Sanity check against published efficiency for a comparable system.

6. Identify the single most leveraged variable for improving the efficiency — usually T_hot. Explain why.

7. Connect to Chapter 16 (Oscillations) if there's a periodic component to your phenomenon — e.g., the cycle frequency of the coffee maker's heating, or the cadence of cycling.

Save the output as logbook/chapter-15-thermodynamics.md.
```

### What this produces

Your fifteenth Logbook entry — an efficiency and entropy budget for the energy-conversion in your phenomenon. By the end of Chapter 15, your Logbook has fifteen entries built on Chapter 1's anchor.

### How to adapt this prompt

- *For phenomena without an obvious heat engine* (a static phenomenon like a building): focus on heat losses through the envelope and the COP of any HVAC system. The "engine" is the HVAC, not the building.
- *For biological phenomena* (your own cycling, running, breathing): the body is the engine; food is the fuel; metabolic heat is the waste.
- *For Claude Code:* If you have measured power input and output traces, fit them and compute time-averaged efficiency directly.

### Connection to previous chapters

Builds on Chapter 14's heat-transfer rates ($Q$ values) and Chapter 7's work-energy bookkeeping. The temperatures must be in kelvin (Chapter 13). The first-law balance is the budget; the second-law bound is the ceiling.

### Preview of next chapter

Chapter 16 introduces oscillations and waves — periodic motion, springs, pendulums, simple harmonic motion. The Chapter 16 LLM Exercise will ask you to find a periodic component of your phenomenon (a pedal stroke, a coffee-maker heating cycle, a wave on a surface) and analyze its period and amplitude.

---

## Chapter summary

Thermodynamics is energy bookkeeping when heat is one of the currencies. Three commitments:

1. **Energy is conserved.** $\Delta E_\text{int} = Q - W$ for any thermodynamic system. Heat in and work done out are the two channels of energy transfer; the difference is stored as internal energy.

2. **Heat flows downhill, and that constrains every engine.** The Kelvin–Planck statement (no engine extracts work from a single-temperature bath), the Clausius statement (heat doesn't flow uphill on its own), and the entropy statement ($\Delta S \geq 0$ in an isolated system) are three sides of the same coin. The Carnot efficiency $1 - T_c/T_h$ is the ceiling no real engine can exceed.

3. **Entropy is microstate counting.** $S = k_B \ln \Omega$. The second law is true because there are vastly more disordered microscopic arrangements than ordered ones, and physics evolves toward the more probable.

The one idea that matters most: **direction in physics is set by the second law, not the first.** Energy is conserved in both directions of every process. What forbids the unmixing, the un-cooling, the un-burning is entropy.

The common mistake to watch for: **using Celsius or Fahrenheit in the Carnot formula.** $T_c$ and $T_h$ must be in kelvin, or you get nonsense. A 0 °C cold reservoir is 273 K, not zero.

---

## What would change my mind

The chapter argues that the Carnot bound is a hard upper limit on any heat-to-work conversion. The argument would need revision if a future experimental device — perhaps exploiting quantum coherence in a structured working substance — were shown to deliver work-from-heat above the Carnot bound for a given $T_h, T_c$ pair. No such device has been demonstrated, and the second law is among the most thoroughly tested generalizations in all of physics.

## Still puzzling

The deepest puzzle this chapter raises and does not resolve: *why does the universe's entropy seem to have started so low?* If the second law just says systems evolve toward more probable arrangements, then the natural prior is *high entropy from the start* — but the early universe, by every cosmological measurement, was in an extraordinarily low-entropy state. This is sometimes called the "past hypothesis" and is one of the open problems at the intersection of thermodynamics and cosmology. We can apply the second law beautifully going forward in time. Why time has the direction it does in the first place — that we cannot yet say.

---

## Connections forward

Chapter 16 begins **oscillations and waves** — periodic motion in mechanical systems, simple harmonic motion, springs, pendulums. The energy bookkeeping habits installed here reappear: in an oscillator, kinetic and potential energies trade back and forth, with damping (entropy generation) draining the system over time. Chapter 17 extends to sound waves. Much later, in quantum mechanics (Chapter 29) and statistical mechanics (an extension of this chapter), the microstate-counting interpretation of entropy you saw here becomes the central organizing principle. The second law you met in this chapter is, in a deep sense, the law that selects which direction time runs.

---

**Tags:** thermodynamics, Carnot, entropy, heat-engines, second-law

---

## AI Wayback Machine

**Sadi Carnot** wrote *Reflections on the Motive Power of Fire* in 1824 — establishing the theoretical limits of heat-engine efficiency before the laws of thermodynamics were formalized. He died of cholera at 36, leaving the field to Clausius and Kelvin.

**Run this:**

```
Who was Sadi Carnot, and how does the Carnot cycle connect to the thermodynamics we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about his career or ideas.
```

→ Search **"Nicolas Léonard Sadi Carnot"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to walk through the four steps of the Carnot cycle and explain why no real engine can exceed its efficiency.
- Ask it about how Carnot's notebooks anticipated parts of the second law decades before it was formalized.

What changes? What gets better? What gets worse?
