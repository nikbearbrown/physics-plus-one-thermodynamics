# Chapter 5 — Temperature, Kinetic Theory, and the Gas Laws

**Suggested titles**

1. Temperature, Kinetic Theory, and the Gas Laws
2. Why Hot Means "Atoms Moving Fast"
3. The Ideal Gas Law and What Lives Underneath It

**TL;DR.** Temperature, at the macroscopic scale, is what a thermometer measures. At the microscopic scale, it's the average kinetic energy of randomly-moving molecules. **Kinetic theory** connects the two: $\tfrac{1}{2} m \overline{v^2} = \tfrac{3}{2} k_B T$, where $T$ is in kelvin and $k_B$ is Boltzmann's constant. From kinetic theory, the **ideal gas law** $PV = nRT$ falls out — pressure, volume, and temperature of a gas are linked because pressure is the time-averaged momentum transfer of trillions of molecules to the container walls. This chapter installs temperature scales, thermal expansion, the gas law, and the kinetic-theory bridge between the macroscopic and microscopic worlds.

---

## A railroad track buckling on a hot day, summer 2002

July 2002, Maryland, USA. A CSX freight train is rolling along a stretch of straight track. The day is unusually hot — air temperature in the upper 90s Fahrenheit, the steel rails baking under direct sun. As the train passes over a particular section, the lead engineer suddenly feels the locomotive lurch. Behind him, a few cars come off the rails. The track had buckled — sun-kinked, in railroad terminology — bending sideways out of its straight alignment because the steel had expanded in the heat and had nowhere to go.

The numbers are unforgiving. Steel has a thermal expansion coefficient of about $1.2 \times 10^{-5}$ per degree Celsius. A $1{,}000 \text{ m}$ stretch of continuously welded track, going from a winter low of $-20°\text{C}$ to a summer high of $+50°\text{C}$, expands by:

$$\Delta L = \alpha L_0 \Delta T = (1.2 \times 10^{-5})(1000)(70) = 0.84 \text{ m}.$$

Almost a meter of expansion across one kilometer. If the rail is constrained at both ends (welded, ballasted, spiked) and can't grow longitudinally, that expansion has to go *somewhere*. It goes sideways. The rail buckles into a snake-like S-curve, several meters of lateral displacement — and a train passing over it derails.

Modern continuous welded rail is engineered with this in mind: the rail is laid at a "neutral temperature" where it's neither under tension (winter) nor compression (summer); ballast is packed tightly to prevent lateral movement; and tracks in hot climates use stress-monitoring sensors. But the underlying physics is that solid materials expand when heated, and the expansion is a relentless function of temperature and material properties. You can engineer around it, but you can't make it go away.

This chapter is about temperature: what it measures, how it relates to the kinetic energy of atoms, how it expands solids and changes the pressure-volume properties of gases. By the end you'll be able to compute thermal expansion, apply the ideal gas law, and understand why "hot" is a statement about the average kinetic energy of microscopic motion.

**Learning objectives.** By the end of this chapter you should be able to:

1. Convert temperatures between Celsius, Fahrenheit, and Kelvin scales; explain why Kelvin is "absolute."
2. Compute thermal expansion of solids using $\Delta L = \alpha L_0 \Delta T$ and volume expansion using $\Delta V = \beta V_0 \Delta T$.
3. Apply the ideal gas law $PV = nRT$ (or $PV = N k_B T$) to compute changes in any one variable when the others change.
4. Apply kinetic theory: $\tfrac{1}{2} m \overline{v^2} = \tfrac{3}{2} k_B T$ to connect temperature to molecular kinetic energy.
5. Interpret phase diagrams qualitatively and identify triple points and critical points.

**Prerequisites.** Chapter 7 (kinetic energy). Chapter 11 (pressure, density). Chapter 12 (fluids in motion — gases as fluids).

**Why this chapter matters.** Temperature is the bridge from mechanics to thermodynamics. The gas laws underlie meteorology, refrigeration, internal combustion engines, scuba diving, and almost every chemical process. Kinetic theory is one of physics's deepest unifications: it shows that the macroscopic concept of "temperature" is microscopically just average kinetic energy. The chapter sets up everything that comes next: heat (Ch. 14), thermodynamic laws (Ch. 15), thermal radiation, entropy, and statistical mechanics.

---

## Concept 1 — Temperature, scales, and thermal expansion

### A platinum-iridium bar in a vault, then an alcohol thermometer

Until 2019, the kilogram was defined by a piece of metal in a vault near Paris (Chapter 1). Until 1967, the second was defined by the rotation of the Earth. Temperature has had a similar history of moving from artifact-based definitions to fundamental-constant definitions. In 2019, the kelvin was redefined in terms of the Boltzmann constant $k_B = 1.380649 \times 10^{-23} \text{ J/K}$.

But what *is* temperature, operationally? Two systems are at the same temperature if, when brought into thermal contact, no net heat flows between them. This is the **zeroth law of thermodynamics** — sometimes called the law that gives temperature its meaning. Temperature is what tells you which way heat will flow when two systems touch.

Three temperature scales:

- **Celsius** (°C): water freezes at 0°, boils at 100° (at 1 atm). Used in most of the world for everyday temperature.
- **Fahrenheit** (°F): water freezes at 32°, boils at 212°. Used in the U.S.
- **Kelvin** (K): zero is *absolute zero* — the temperature at which molecular motion would cease (theoretically; quantum mechanics keeps a residual zero-point motion). Same size of degree as Celsius, just shifted: $T_K = T_C + 273.15$.

Conversion: $T_C = (T_F - 32) \times 5/9$. $T_K = T_C + 273.15$.

Why kelvin is the right scale for physics: many laws (gas law, kinetic theory, blackbody radiation) involve temperature in a multiplicative way. With Celsius or Fahrenheit, you'd be multiplying by an arbitrarily-shifted number. With kelvin, $T = 0$ corresponds to the absence of thermal motion — a physically meaningful zero.

### Thermal expansion: solids, liquids, gases

When most materials are heated, they expand. For solids, the linear expansion is approximately:

$$\Delta L = \alpha L_0 \Delta T,$$

where $\alpha$ is the **coefficient of linear expansion** (units: $1/K$ or $1/°C$ — same since the size of the kelvin and celsius degree are the same). Some typical values:

- Aluminum: $\alpha = 25 \times 10^{-6} / K$.
- Steel: $\alpha = 12 \times 10^{-6} / K$.
- Glass (Pyrex): $\alpha = 3 \times 10^{-6} / K$.
- Water (volumetric, $\beta$): $\beta = 210 \times 10^{-6} / K$ (much larger than solid linear expansion).

For volume expansion of a solid, $\beta \approx 3\alpha$. For liquids, $\beta$ is the relevant quantity directly.

Water has a famous anomaly: between $0°\text{C}$ and $4°\text{C}$, water *contracts* on heating (becomes denser as it warms). This is why ice floats — solid ice is less dense than liquid water at $4°\text{C}$. It's also why ponds and lakes freeze top-down rather than bottom-up: the densest water (at $4°\text{C}$) sinks to the bottom, leaving cooler water above to freeze first.

### The mechanism — why materials expand

At the atomic level, atoms in a solid vibrate around equilibrium positions in a roughly parabolic potential well. When you heat the material, the atoms vibrate with greater amplitude. Because the potential well is slightly *asymmetric* (rising more steeply for compression than for expansion), the average position shifts outward. The macroscopic effect is expansion.

This is also why thermal expansion coefficients are typically small ($10^{-6}$ to $10^{-5}$ per kelvin): the asymmetry is mild, so the expansion per degree is small. But over large temperature ranges and long structures (Maryland railroad track), the small per-degree expansion adds up to meters.

### The trade-off

The linear-expansion formula trades **detailed atomic-scale potential** for **a single empirical coefficient $\alpha$.** It works well for moderate temperature ranges and most engineering materials. At very high or very low temperatures, $\alpha$ itself becomes temperature-dependent, and the linear formula needs corrections.

### Worked example — thermal stress in railroad track

A $200 \text{ m}$ section of welded steel rail is laid at $20°\text{C}$ (assumed neutral temperature). On a summer day, the rail temperature reaches $50°\text{C}$. (a) How much would it expand if free to expand? (b) If constrained (no expansion allowed), what compressive stress builds up in the rail? (Steel Young's modulus $Y = 200 \times 10^9 \text{ Pa}$.)

**(a) Free expansion.** $\Delta L = \alpha L_0 \Delta T = (12 \times 10^{-6})(200)(30) = 0.072 \text{ m} = 7.2 \text{ cm}$.

**(b) Stress if constrained.** Strain that would occur if free: $\epsilon = \Delta L / L_0 = 0.072 / 200 = 3.6 \times 10^{-4}$. Stress: $\sigma = Y \epsilon = (200 \times 10^9)(3.6 \times 10^{-4}) = 7.2 \times 10^7 \text{ Pa} = 72 \text{ MPa}$.

About $72 \text{ MPa}$ of compressive stress builds up. This is below structural steel's yield stress (~$250 \text{ MPa}$), so the rail won't yield, but it's enough to push the rail laterally if there's any side play — which is what causes sun-kinks.

**Sanity check.** Real railroad-rail thermal stresses can reach $\sim 100 \text{ MPa}$ or more in extreme heat, exactly the regime where lateral buckling becomes the failure mode. The numbers match published engineering experience.

### Common misconceptions

- *"Cold is the absence of heat; heat is a substance."* Heat (Chapter 14) is energy in transit due to a temperature difference. There's no "cold" substance. Cold is just less heat.
- *"All materials expand on heating."* Most do. Water between 0° and 4°C is the famous exception. Some specially-engineered materials (Invar) have nearly zero thermal expansion.

↳ **Dig Deeper — Why is the kelvin defined by Boltzmann's constant?**

*Until 2019, the kelvin was defined as a fraction (1/273.16) of the temperature at which water has a triple point — the unique temperature at which solid, liquid, and gas all coexist. In 2019, the kelvin was redefined in terms of $k_B = 1.380649 \times 10^{-23} \text{ J/K}$ exactly. The redefinition tied temperature to a fundamental constant rather than a property of water.*

**Prompt:**
> Explain the 2019 redefinition of the kelvin in terms of the Boltzmann constant. Walk through (a) the previous definition based on the triple point of water (273.16 K), (b) why an artifact-free definition using a fundamental constant is preferred, (c) the Boltzmann constant itself and its physical role (it converts temperature to energy, $k_B T$ being the characteristic thermal energy scale at temperature $T$). End with one sentence on what other SI units were redefined in the same 2019 reform (the kilogram, ampere, and mole — all tied to fundamental constants).

**What to do with the output:** Save it. The 2019 SI redefinition is one of the most consequential developments in modern metrology and continues the trend started in Chapter 1.

---

## Concept 2 — The ideal gas law: $PV = nRT$

### A fixed-mass balloon in a freezer

Take a balloon, blow it up at room temperature, tie it off. Place it in a freezer for an hour. Take it out. The balloon has shrunk — visibly, sometimes dramatically. The amount of gas inside hasn't changed (the balloon is sealed). What happened?

Pressure inside the balloon adjusts to roughly equal the outside atmospheric pressure (the rubber's tension adds a small extra). With fixed pressure, fixed amount of gas, and reduced temperature, the volume must shrink. This is the **ideal gas law** in action.

The law combines several earlier empirical laws:

- **Boyle's law:** at constant $T$ and $n$, $PV = $ constant.
- **Charles's law:** at constant $P$ and $n$, $V/T = $ constant.
- **Avogadro's law:** at constant $P$ and $T$, $V/n = $ constant.

All three combine into:

$$PV = nRT,$$

where $P$ is pressure (Pa), $V$ is volume (m³), $n$ is moles of gas, $R = 8.314 \text{ J/(mol·K)}$ is the universal gas constant, and $T$ is temperature in kelvin.

Equivalently, using number of molecules $N$ instead of moles:

$$PV = N k_B T,$$

where $k_B = R/N_A = 1.381 \times 10^{-23} \text{ J/K}$ is Boltzmann's constant and $N_A = 6.022 \times 10^{23}$ is Avogadro's number.

### The mechanism — what the law says and where it's exact

The ideal gas law treats a gas as a collection of point particles that don't interact except through brief elastic collisions. It's exact in the limit of high temperature and low density (where molecules are far apart, and intermolecular forces can be neglected). Real gases deviate at high pressure and low temperature, where intermolecular forces and finite molecular volumes matter — corrections are handled by the Van der Waals equation and more sophisticated equations of state.

For most engineering and atmospheric-science applications, the ideal gas law is excellent. Nitrogen, oxygen, hydrogen, helium, and most other common gases at room temperature and pressures from vacuum to a few atmospheres are well-approximated as ideal.

A useful rearrangement: at standard conditions ($T = 273.15 \text{ K}$, $P = 1 \text{ atm} = 101{,}325 \text{ Pa}$), one mole of ideal gas occupies:

$$V_{\text{molar}} = \frac{nRT}{P} = \frac{(1)(8.314)(273.15)}{101{,}325} \approx 0.0224 \text{ m}^3 = 22.4 \text{ L}.$$

This $22.4 \text{ L/mol}$ at STP is the most-quoted result in introductory chemistry.

### The trade-off

The ideal gas law trades **microscopic accuracy at extreme conditions** for **a single equation that captures gas behavior to within a few percent across most everyday situations.** Real gases need corrections at high pressure or low temperature; the ideal version is the entry point and works for almost all introductory physics situations.

### Worked example — pressure in a tire as it warms

A car tire is filled to gauge pressure $230 \text{ kPa}$ (about $33 \text{ psi}$, roughly atmospheric + tire) at $15°\text{C}$. After driving, the tire warms to $40°\text{C}$. The volume of the tire changes negligibly. What is the new gauge pressure?

**Setup.** Absolute initial pressure: $P_1 = 230 + 101 = 331 \text{ kPa}$. Initial temperature: $T_1 = 15 + 273 = 288 \text{ K}$. Final temperature: $T_2 = 40 + 273 = 313 \text{ K}$.

**Apply ideal gas law at constant volume and amount.** $P_1/T_1 = P_2/T_2 \implies P_2 = P_1 \times T_2/T_1$:

$$P_2 = 331 \times \frac{313}{288} \approx 360 \text{ kPa}.$$

New gauge pressure: $P_{2,\text{gauge}} = 360 - 101 = 259 \text{ kPa}$ (about $37 \text{ psi}$).

**Sanity check.** Tire pressure rises by ~$10\%$ when the tire heats from cold to driven-warm — consistent with everyday experience and with manufacturer recommendations (always check tire pressure cold). The increase isn't enough to blow a tire, but it does affect handling.

### Common misconceptions

- *"Gas law works in Celsius."* No — must use kelvin. The law $PV = nRT$ assumes absolute temperature; using Celsius in $T_2/T_1$ gives wildly wrong answers, especially at low temperatures.
- *"Pressure is the same as gauge pressure."* In the ideal gas law, $P$ is *absolute* pressure. Subtract atmospheric to get gauge if that's what you're given.

↳ **Dig Deeper — Why does breathing work? (Boyle's law in the lungs)**

*Inhalation: your diaphragm contracts, expanding the chest cavity. By Boyle's law (at constant amount and temperature, $P V = $ const), expanding the volume reduces the pressure inside the lungs below atmospheric — and air rushes in to equalize. Exhalation reverses: chest cavity contracts, lung pressure rises above atmospheric, air is pushed out. The whole system runs on Boyle's law.*

**Prompt:**
> Apply Boyle's law to the mechanics of human breathing. (a) Estimate the lung volume change during a typical breath (~0.5 L tidal volume on an ~5 L total lung capacity). (b) Compute the pressure change inside the lungs during inhalation, assuming temperature stays constant and no air enters yet (this is the driving pressure differential). (c) Discuss how this pressure differential drives airflow into the lungs, with the air entering until pressures equalize. End with one sentence on how this physiological process is one of the most direct everyday demonstrations of the gas laws.

**What to do with the output:** Save it. Breathing as gas-law application is a beautiful pedagogical bridge between physics and physiology.

---

## Concept 3 — Kinetic theory: temperature as molecular kinetic energy

### A puff of perfume diffusing across a room

Spray a small amount of perfume in one corner of a still room. Within minutes, the smell has spread across the room. There's no air current; the molecules diffused — moved on their own — from high concentration to low concentration. The molecules are in constant, random thermal motion, and that motion is what diffuses them.

How fast are they moving? It depends on temperature. The kinetic theory of gases gives an exact relationship.

### The mechanism — kinetic theory

For an ideal gas at temperature $T$ (kelvin), the average kinetic energy of a molecule is:

$$\bar{KE} = \tfrac{1}{2} m \bar{v^2} = \tfrac{3}{2} k_B T.$$

The factor of $3$ accounts for three degrees of freedom (motion in $x$, $y$, $z$). Each degree of freedom contributes $\tfrac{1}{2} k_B T$ — this is the **equipartition theorem**.

Solving for the **root-mean-square speed**:

$$v_{\text{rms}} = \sqrt{\overline{v^2}} = \sqrt{\frac{3 k_B T}{m}}.$$

For nitrogen molecules at room temperature ($T = 293 \text{ K}$, $m = 28 \times 1.66 \times 10^{-27} \text{ kg} = 4.65 \times 10^{-26} \text{ kg}$):

$$v_{\text{rms}} = \sqrt{\frac{3(1.38 \times 10^{-23})(293)}{4.65 \times 10^{-26}}} = \sqrt{\frac{1.21 \times 10^{-20}}{4.65 \times 10^{-26}}} = \sqrt{2.6 \times 10^5} \approx 510 \text{ m/s}.$$

That's *faster than the speed of sound*. Air molecules are zipping around at hundreds of meters per second, even at room temperature. The reason perfume doesn't fill the room instantly: the molecules undergo countless collisions with each other (mean free path of $\sim 70 \text{ nm}$ at standard conditions). So even though they're moving at $510 \text{ m/s}$, they're random-walking — net diffusion across a meter takes minutes.

### Pressure from kinetic theory

The ideal gas law follows from kinetic theory. Imagine a cubic box of side $L$ containing $N$ molecules, each of mass $m$. Each molecule colliding with a wall transfers momentum. Computing the time-averaged force per unit area (the pressure) and using equipartition gives:

$$PV = \tfrac{2}{3} N \cdot \tfrac{1}{2} m \overline{v^2} = \tfrac{2}{3} N \cdot \tfrac{3}{2} k_B T = N k_B T.$$

Which is the ideal gas law. The macroscopic concept of "pressure" emerges from the microscopic concept of "lots of molecular collisions." Temperature emerges from "average kinetic energy of those molecules."

### The trade-off

Kinetic theory trades **conceptual simplicity (a gas as billiard balls bouncing around)** for **statistical analysis (averages over Avogadro-scale numbers of molecules)**. The cost: you can't track individual molecules. The benefit: you derive the macroscopic gas law from microscopic mechanics, unifying statistical mechanics with classical mechanics. This is one of the deepest results in physics.

### Worked example — speeds of common gas molecules

At room temperature ($T = 300 \text{ K}$), compute $v_{\text{rms}}$ for: (a) hydrogen ($m = 2 \times 1.66 \times 10^{-27} \text{ kg}$), (b) nitrogen ($28 \times 1.66 \times 10^{-27}$), (c) carbon dioxide ($44 \times 1.66 \times 10^{-27}$).

**(a) Hydrogen.** $v = \sqrt{3(1.38 \times 10^{-23})(300)/(3.32 \times 10^{-27})} = \sqrt{3.74 \times 10^6} \approx 1{,}930 \text{ m/s}$.

**(b) Nitrogen.** $v = \sqrt{3(1.38 \times 10^{-23})(300)/(4.65 \times 10^{-26})} = \sqrt{2.67 \times 10^5} \approx 517 \text{ m/s}$.

**(c) CO₂.** $v = \sqrt{3(1.38 \times 10^{-23})(300)/(7.31 \times 10^{-26})} = \sqrt{1.70 \times 10^5} \approx 412 \text{ m/s}$.

**Sanity check.** At the same temperature, lighter molecules move faster (so all particles have the same average KE). Hydrogen (lightest) moves nearly $4\times$ faster than CO₂ (heavier). This is why hydrogen escapes from Earth's atmosphere over geological time: $v_{\text{rms}} = 1{,}900 \text{ m/s}$ is a substantial fraction of escape velocity ($11{,}200 \text{ m/s}$), and the high-velocity tail of the Maxwell-Boltzmann distribution constantly leaks hydrogen molecules to space.

### Common misconceptions

- *"All molecules at temperature T have the same speed."* No — they have a distribution of speeds (the Maxwell-Boltzmann distribution). $v_{\text{rms}}$ is just one statistical measure of that distribution.
- *"At absolute zero, molecules stop moving entirely."* In classical kinetic theory, yes ($v = 0$ at $T = 0$). In quantum mechanics, no — there's a residual zero-point motion. We won't see this until Chapter 30.

↳ **Dig Deeper — Maxwell-Boltzmann distribution and why hydrogen escaped Earth**

*Maxwell, in the 1860s, derived the probability distribution of molecular speeds in a gas at thermal equilibrium. The distribution has a long tail: a significant fraction of molecules move much faster than the average. For light gases like hydrogen, this fast tail can exceed Earth's escape velocity, meaning the atmosphere slowly leaks hydrogen to space.*

**Prompt:**
> Sketch (in description) the Maxwell-Boltzmann speed distribution for a gas at fixed temperature. Note (a) the most probable speed (peak), (b) the mean speed, (c) the rms speed (which is slightly higher than the mean due to the high-speed tail). Then explain why Earth's atmosphere has retained nitrogen and oxygen but lost almost all hydrogen and helium: compute the fraction of hydrogen at room temperature exceeding Earth's escape velocity ($11{,}200 \text{ m/s}$) using the Maxwell-Boltzmann distribution. End with one sentence on why the Moon, with much lower escape velocity, has essentially no atmosphere.

**What to do with the output:** Save it. The escape-of-hydrogen story is a beautiful application of statistical mechanics to planetary science.

---

## Synthesis — temperature as the bridge from mechanics to thermodynamics

Step back. Three concepts:

**Temperature** is what a thermometer measures. Three scales (Celsius, Fahrenheit, Kelvin), with kelvin tied to absolute zero and now defined via Boltzmann's constant. Solids expand thermally; the linear coefficient $\alpha$ is small but adds up.

**Ideal gas law** ($PV = nRT$ or $PV = N k_B T$) relates pressure, volume, temperature, and amount of gas. Excellent approximation for most gases at non-extreme conditions.

**Kinetic theory** bridges macro and micro: temperature is the average kinetic energy of randomly-moving molecules ($\tfrac{1}{2} m \overline{v^2} = \tfrac{3}{2} k_B T$). Pressure is the time-averaged momentum transfer to walls. The ideal gas law derives from kinetic theory.

The **scale shift**: temperature ranges from absolute zero ($0 \text{ K}$, no thermal motion) to the cores of stars ($10^7 \text{ K}$, plasma) to the early universe ($10^{32} \text{ K}$, beyond the Planck temperature where quantum gravity dominates). The same kinetic-theory relationship $\bar{KE} \sim k_B T$ applies across this range — only the regimes differ (classical at low T, relativistic at very high T, quantum-degenerate at very low T).

### A worked example using all three concepts — air in a hot car

A car's interior has volume $3.0 \text{ m}^3$, and at $20°\text{C}$ contains air at $1 \text{ atm}$. The car is parked in the sun and the interior temperature reaches $60°\text{C}$. The car is sealed (no air enters or leaves). (a) What is the new pressure inside? (b) What is the rms speed of N₂ molecules at the new temperature? (c) Has the volume changed measurably (assume the cabin is rigid)?

**(a) Ideal gas law (constant V, n).** $P_1/T_1 = P_2/T_2$. $T_1 = 293 \text{ K}$, $T_2 = 333 \text{ K}$.

$$P_2 = P_1 \times T_2/T_1 = 101{,}000 \times 333/293 \approx 114{,}800 \text{ Pa}.$$

About $1.13 \text{ atm}$ — a $13\%$ increase. (In practice, car windows are not perfectly sealed, so excess pressure leaks out, but the principle is the same.)

**(b) RMS speed.** $v_{\text{rms}} = \sqrt{3 k_B T/m}$ for N₂:

$$v_{\text{rms}} = \sqrt{\frac{3(1.38 \times 10^{-23})(333)}{4.65 \times 10^{-26}}} \approx 543 \text{ m/s}.$$

About $543 \text{ m/s}$ — slightly faster than at room temperature.

**(c) Volume change.** Linear thermal expansion of steel from car body: $\alpha \sim 12 \times 10^{-6}$, $\Delta T = 40$, so $\Delta L/L = 4.8 \times 10^{-4}$. Volume expands by $3 \times \Delta L/L = 1.4 \times 10^{-3}$, or about $0.14\%$. Negligible compared to the gas's pressure response.

**The synthesis** exercises all three concepts: thermal expansion (steel body, negligibly small effect on volume); ideal gas law (significant pressure rise); kinetic theory (faster-moving molecules at higher T). The dominant effect is the ideal-gas pressure rise — which is why car interiors get hot but rarely explode (small leaks through seals release the excess pressure).

---

## Exercises

### Warm-up

**13.1** *(LO 1)* Convert: (a) 25°C to Fahrenheit and Kelvin; (b) 100°F to Celsius and Kelvin; (c) 0 K to Celsius and Fahrenheit.

**13.2** *(LO 2)* A steel bridge $1{,}000 \text{ m}$ long is built at $15°\text{C}$. By how much does it expand when the temperature reaches $40°\text{C}$? ($\alpha_{\text{steel}} = 12 \times 10^{-6}/K$.)

**13.3** *(LO 3)* A balloon contains $0.10 \text{ mol}$ of helium at $300 \text{ K}$ and $1 \text{ atm}$. What is its volume?

**13.4** *(LO 4)* Compute the rms speed of helium atoms at $300 \text{ K}$. ($m_{\text{He}} = 6.65 \times 10^{-27} \text{ kg}$.)

### Application

**13.5** *(LO 2)* A glass beaker ($V_0 = 500 \text{ mL}$) is filled with water at $20°\text{C}$. The water and beaker are heated to $80°\text{C}$. (a) Volume increase of the water? ($\beta_{\text{water}} = 210 \times 10^{-6}/K$.) (b) Volume increase of the beaker (Pyrex, $\alpha = 3 \times 10^{-6}/K$)? (c) What spills over?

**13.6** *(LO 3)* A scuba diver's tank contains $11.0 \text{ L}$ of air at $200 \text{ atm}$ and $20°\text{C}$. (a) How many moles of gas? (b) If the diver descends to $30 \text{ m}$ depth (ambient pressure $\sim 4 \text{ atm}$) and uses a regulator that maintains the air at ambient pressure, how many liters of air does the tank effectively contain (at depth pressure)?

**13.7** *(LO 3)* A car tire is inflated to gauge pressure $200 \text{ kPa}$ at $15°\text{C}$. After driving, tire temperature reaches $50°\text{C}$. New gauge pressure?

**13.8** *(LO 4)* At what temperature would the rms speed of nitrogen molecules ($m = 4.65 \times 10^{-26} \text{ kg}$) equal the escape velocity from Earth's surface ($11{,}200 \text{ m/s}$)?

### Synthesis

**13.9** *(LO 1, 2)* The Eiffel Tower is $324 \text{ m}$ tall, made of iron ($\alpha = 12 \times 10^{-6}/K$). On a winter day at $-10°\text{C}$, it's at one height; on a summer day at $40°\text{C}$, it's at another. By how much does its height change?

**13.10** *(LO 3, 4)* A weather balloon at sea level has volume $5.0 \text{ m}^3$ at $20°\text{C}$ and $1 \text{ atm}$. It rises to $10 \text{ km}$ altitude where pressure is $0.26 \text{ atm}$ and temperature is $-50°\text{C}$. (a) What is its new volume? (b) Compute the rms speed of molecules in both conditions and compare.

**13.11** *(LO 3)* Air contains about $78\%$ nitrogen by mole and $21\%$ oxygen. At $20°\text{C}$ and $1 \text{ atm}$, what is the partial pressure of each? What is the molar density (mol/L)?

### Challenge

**13.12** *(LO 4, beyond chapter)* The escape velocity from the Moon is $2{,}380 \text{ m/s}$. (a) Compute the rms speed of N₂ molecules at the Moon's surface temperature ($T \sim 250 \text{ K}$). (b) Compute the rms speed of H₂. (c) Discuss why the Moon retains essentially no atmosphere.

**13.13** *(beyond chapter)* The ideal gas law fails for real gases at high pressure or low temperature. The Van der Waals equation $\left(P + \frac{an^2}{V^2}\right)(V - nb) = nRT$ corrects for intermolecular attraction (the $a$ term) and finite molecular volume (the $b$ term). For nitrogen at $25°\text{C}$, $a = 0.137 \text{ J·m}^3/\text{mol}^2$, $b = 3.87 \times 10^{-5} \text{ m}^3/\text{mol}$. (a) Compute the pressure of $1 \text{ mol}$ in $1 \text{ L}$ using both ideal gas law and Van der Waals. (b) At what density does the difference become significant (~$10\%$)?

---

## LLM Exercise — Chapter 13: Temperature and Gas Laws in Your Anchor Phenomenon

**Project:** Physics Reality Check Logbook
**What you're building this chapter:** A temperature, thermal-expansion, or gas-law analysis of one element of your anchor phenomenon.
**Tool:** Claude Project.

### The Prompt

```
I'm continuing my Physics Reality Check Logbook for College Physics with LLMs. My anchor phenomenon is [paste 1-sentence description].

For Chapter 13, I want to apply temperature, thermal expansion, and/or the ideal gas law to one element of my phenomenon. Please:

1. Identify ONE temperature- or gas-related effect in my phenomenon. Examples:
   - Bike commute: tire pressure changes with temperature; metal frame thermal expansion in summer.
   - Coffee maker: water heating from 20°C to brewing temperature (~95°C); steam volume.
   - Basketball: ball pressure and temperature variations indoor vs. outdoor.
   - Marathon: body temperature regulation (sweating, evaporative cooling).
   - Espresso: water temperature, steam dynamics, temperature drop during extraction.

2. Identify the relevant equation: thermal expansion ($\Delta L = \alpha L_0 \Delta T$), ideal gas law ($PV = nRT$), or kinetic theory ($\bar{KE} = \tfrac{3}{2}k_B T$).

3. Compute the relevant quantity. Report with units, sig figs, uncertainty.

4. Sanity check with one Fermi estimate.

5. Estimate the molecular rms speed of the relevant gas if applicable.

6. Identify which simplification (ideal gas, constant α, no phase change) is most likely to bite.

7. One sentence on how this connects to Chapter 14 (heat) — temperature change requires heat transfer, and heat capacity tells you how much.

Save the output as logbook/chapter-13-temperature-gases.md.
```

### What this produces

A thirteenth Logbook entry: a thermal/gas analysis applied to your phenomenon, often surprising in the magnitude of pressure changes or molecular speeds.

### How to adapt this prompt

- *For phenomena with no obvious gas* (a marathon, a basketball shot): focus on body-temperature regulation or atmospheric conditions.
- *For ChatGPT or Gemini:* identical with substitutions.
- *For Claude Code:* if you have temperature-time data, paste it.

### Connection to previous chapters

Builds on Chapter 7 (kinetic energy — temperature is average KE). Builds on Chapter 11 (pressure). Builds on Chapter 12 (gases as fluids — but compressible).

### Preview of next chapter

Chapter 14 introduces heat itself — energy in transit due to temperature difference. Heat capacity, specific heat, latent heat (phase changes), and the modes of heat transfer (conduction, convection, radiation). Together with this chapter, these establish the foundations of thermodynamics.

---

## Chapter summary

Three pillars. **Temperature**: what thermometers measure, with three scales (Celsius, Fahrenheit, Kelvin); kelvin is the absolute scale tied to molecular kinetic energy via $k_B$. Solids expand thermally with coefficient $\alpha$. **Ideal gas law** $PV = nRT$ (or $N k_B T$): empirical relation among pressure, volume, temperature, and amount. **Kinetic theory**: $\bar{KE} = \tfrac{3}{2} k_B T$. Pressure derives from molecular collisions with walls; temperature is just the average KE.

The one idea that matters most: **temperature is microscopic kinetic energy.** "Hot" means the molecules are moving fast on average. This unification — macroscopic temperature ↔ microscopic motion — is one of the deepest in physics, and it's the entry to all of thermodynamics and statistical mechanics.

The common mistake to watch for: **using Celsius (or Fahrenheit) where the gas law or kinetic theory requires kelvin.** The formulas $PV = nRT$ and $\bar{KE} = \tfrac{3}{2}k_B T$ require absolute temperature. Forgetting to convert produces wildly wrong answers.

What you should now be able to teach someone else: how to convert temperatures between scales, how to compute thermal expansion, how to apply the ideal gas law to predict pressure/volume/temperature changes, how to compute molecular speeds from temperature, and why temperature is fundamentally just a measure of average molecular kinetic energy. Five skills, three organizing principles.

---

## What would change my mind

The chapter argues that the ideal gas law and kinetic theory are sufficient for most introductory and engineering applications, with corrections (Van der Waals, quantum statistics) handling extremes. The argument would need revision if a class of common gas behaviors required more than mild corrections — they generally don't, until you reach the very low-temperature regime where quantum statistics dominate (Bose-Einstein and Fermi-Dirac, beyond the chapter scope).

## Still puzzling

The deepest puzzle this chapter raises and does not resolve: **why is there an absolute zero?** Classical kinetic theory says all motion ceases at $T = 0$ — but quantum mechanics says zero-point motion remains even there. The third law of thermodynamics (Nernst's theorem) says you can approach absolute zero arbitrarily closely but never actually reach it. The deeper reason — whether it has to do with information, entropy, or the structure of quantum states — is still being explored.

---

## Connections forward

Chapter 14 introduces heat — energy transfer driven by temperature difference. Heat capacity, specific heat, latent heat for phase changes. Modes of transfer: conduction, convection, radiation. Chapter 15 introduces the laws of thermodynamics — energy conservation including heat (first law), entropy and irreversibility (second law), absolute zero (third law). Chapter 14–15 together build the framework that explains why heat engines have maximum efficiencies, why some processes are irreversible, and why the universe heads toward thermal equilibrium. Statistical mechanics (beyond intro) extends kinetic theory to all states of matter and provides the deeper foundation. The kelvin you defined in this chapter and the average KE per molecule remain the key quantities throughout.

---

**Tags:** temperature, ideal-gas-law, kinetic-theory, thermal-expansion, kelvin

---

## AI Wayback Machine

**Ludwig Boltzmann** founded statistical mechanics in the 1870s — showing that thermodynamic quantities like temperature emerge from the statistical behavior of molecules. He carved his entropy formula onto his own tombstone: S = k log W.

**Run this:**

```
Who was Ludwig Boltzmann, and how does his statistical mechanics connect to the kinetic theory and gas laws we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about his career or ideas.
```

→ Search **"Ludwig Boltzmann"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to walk through how the Boltzmann distribution emerges from molecular collisions.
- Ask it about Boltzmann's contested intellectual fights with Ernst Mach and Wilhelm Ostwald over whether atoms existed.

What changes? What gets better? What gets worse?
