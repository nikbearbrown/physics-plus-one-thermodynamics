# Chapter 6 — Heat and Heat Transfer Methods

**Suggested titles**

1. Heat and Heat Transfer Methods
2. Energy in Transit: Conduction, Convection, Radiation
3. Why Your Kitchen Tile Feels Colder Than Your Carpet

**TL;DR.** Heat is energy in transit between objects at different temperatures — not a substance an object holds, but a flow that exists only while temperatures differ. This chapter pins down the three numbers that govern that flow ($Q = mc\Delta T$ for warming, $Q = mL$ for phase change, and the rate equations for conduction, convection, and radiation), and walks through worked examples that turn each equation into a defensible prediction.

---

## A barefoot step at 6 a.m., kitchen tile

It is winter, just before sunrise. You walk from your bedroom across a thick wool carpet, then through a doorway and onto a ceramic kitchen tile. The carpet felt fine. The tile feels like a slap.

Stick a thermometer to each surface and you find, to within the resolution of the instrument, the same number. Both surfaces are sitting at room temperature, around 18 °C. The tile is not colder than the carpet. The tile *removes heat from your foot faster than the carpet does*. Your skin is the thermometer, and what your skin reports is not temperature — it is the *rate* at which energy is leaving you.

This is the central trick of the entire chapter. Heat is not a thing inside an object. Heat is what moves between two objects when their temperatures differ. The pile of wool fibers in the carpet traps still air, and air is a poor conductor — energy seeps out of your foot slowly enough that your skin barely notices. The ceramic tile is a continuous solid lattice of atoms in close contact, with thousands of times the conductivity of trapped air, and it sucks energy out of your foot fast enough to register as cold even though the tile and the carpet are at the same temperature.

The molecular biologist Julius Comroe had a phrase: *the body is a thermometer that lies*. What it actually measures is heat flux. Once you know the difference, the rest of this chapter follows.

**Learning objectives.** By the end of this chapter you should be able to:

1. Distinguish heat from temperature, and state the calorie and joule equivalence ($1 \text{ kcal} = 4186 \text{ J}$).
2. Compute the heat required to change the temperature of an object using $Q = mc\Delta T$, looking up specific heats from a table and propagating uncertainty.
3. Compute the heat absorbed or released during a phase change using $Q = mL$, and combine temperature-change and phase-change steps in one calorimetry problem.
4. Calculate conductive heat transfer rates through a slab using $Q/t = kA(T_2 - T_1)/d$ and reason about R-value.
5. Calculate radiative heat transfer using the Stefan-Boltzmann law $Q/t = \sigma e A T^4$ and the net radiation expression $Q_\text{net}/t = \sigma e A (T_2^4 - T_1^4)$.
6. Identify when conduction, convection, or radiation dominates a given heat-transfer problem.

**Prerequisites.** Chapters 1–2 (units, uncertainty, dimensional analysis), Chapter 7 (energy as a conserved quantity), Chapter 13 (temperature, thermal equilibrium, ideal gas).

**Why this chapter matters.** Almost every engineered system you touch was designed around heat transfer — furnaces, refrigerators, engines, insulation, clothing, computer chips, climate. Earth's energy budget, the design of a coffee cup, and the reason an iceberg takes years to melt at sea all live inside the equations on the next ten pages.

---

## Concept 1 — Heat is energy in transit

### Joule's paddle wheel, Salford, 1845

In 1845, James Prescott Joule — son of a Manchester brewer, working in the laboratory next to his father's brewery — set up a heavy weight on a rope, looped the rope over a pulley, and let the weight fall, slowly, while turning a paddle wheel inside an insulated tank of water. He measured the temperature of the water before. The weight fell. He measured the temperature of the water after.

The water was warmer. Not by much — Joule needed thermometers calibrated to a hundredth of a degree, and his own family's brewing tradition for the patience to do it right. But warmer, repeatably, in proportion to how far the weight had fallen.

What Joule had shown, and what the entire calorie-versus-joule conversion of modern thermodynamics rests on, is that *mechanical work and heat are interchangeable forms of energy*. The gravitational potential energy of the weight became kinetic energy of the wheel became kinetic energy of the water became, eventually, increased random kinetic energy of the water molecules — which is what we call temperature. The conversion factor:

$$1.000 \text{ kcal} = 4186 \text{ J}.$$

That is to say: it takes 4,186 joules of mechanical work, applied through a paddle wheel or by any other means, to warm one kilogram of water by 1 °C — exactly the same energy that flows in if you put the same kilogram on a stove and add 1 kilocalorie of heat. The two paths are indistinguishable from the inside. This equivalence is why the SI unit of energy is named the joule, and why the discipline that studies it — thermodynamics — is the only one in physics where two earlier traditions (mechanics and heat) had to be welded into one.

### The mechanism — what heat actually is

We define **heat** as *the spontaneous transfer of energy due to a temperature difference*. The word matters. Heat is not stored in a thing. A coffee cup at 80 °C does not "contain heat." It contains internal energy — the sum of the kinetic and potential energies of every molecule inside it. *Heat* is the name for the flow of that energy across a boundary, and the flow happens only when there is a temperature difference to drive it.

This is the language Joule's paddle-wheel experiment forced into existence. You can change the internal energy of a system in two ways: do work on it (the paddle wheel), or transfer heat to it (the stove). After the change, you cannot tell which path was used. The system has more internal energy; that is all. So we say a system has well-defined internal energy, but does not have "heat content" or "work content." Heat and work are *processes*, not properties.

The SI unit for heat, like for any energy, is the joule. The kilocalorie persists for historical reasons and because food labels still use it (one Food Calorie equals one kilocalorie equals 1,000 small calories — the upper-case C does the work of three orders of magnitude, which is part of why nutrition labels confuse people).

### The trade-off

Defining heat as a *transfer* trades **intuitive language for analytical clarity.** Everyday speech says "the heat in the room is unbearable," as if heat were a substance accumulating in a space. The technical definition rules that sentence out — what is unbearable is the *temperature*, and what your body notices is the *rate* of heat transfer to or from your skin. Adopting the technical definition costs you a colloquialism. It buys you the ability to write down energy balance equations that work.

### Worked example — paddle wheel into a beaker

Suppose you drop a 1.50 kg weight through a height of 2.00 m, and all of its lost gravitational potential energy goes into stirring 0.200 kg of water in an insulated container. By how much does the water's temperature rise?

**Reasoning.** The energy delivered to the water is $E = mgh = (1.50)(9.80)(2.00) = 29.4 \text{ J}$. Setting this equal to $Q = m_w c_w \Delta T$ with $c_w = 4186 \text{ J/(kg} \cdot \text{°C)}$:

$$\Delta T = \frac{E}{m_w c_w} = \frac{29.4}{(0.200)(4186)} \approx 0.0351 \text{ °C}.$$

Three hundredths of a degree. That is why Joule needed thermometers good to a hundredth — and why he had to repeat the experiment many times to be sure the warming was real and not drift.

**Sanity check.** Water has the largest specific heat of any common substance. A 30 J jolt to 200 g of water producing a tiny temperature change is exactly what you should expect. If the answer had been a degree or two, something would have been wrong.

### Common misconceptions

- *"Heat is a kind of substance."* No — this is the eighteenth-century *caloric* theory, killed by Joule's experiments. Heat is a flow of energy, not stuff.
- *"A hot object contains a lot of heat."* It contains a lot of *internal energy*. The word *heat* is reserved for the transfer. Use it as a verb-disguised-as-noun.

↳ **Dig Deeper — Why caloric theory survived for a century**

*The caloric theory of heat — that heat is an invisible weightless fluid that flows from hot bodies to cold ones — was the dominant physics from Lavoisier in the 1780s through the 1840s. It made many correct predictions before Joule's work overturned it. Understanding why scientists held the wrong theory for so long is a useful case study in how physics actually progresses.*

**Prompt:**
> Walk me through the rise and fall of the caloric theory of heat. What predictions did the theory get right that made it durable? Which experiments first put it under stress (Count Rumford's cannon-boring observations, then Joule's paddle wheel)? Why did caloric theory survive Rumford for forty years before Joule finally killed it? End with one sentence on what historians of science take from the case about how scientific consensus shifts.

**What to do with the output:** Save it. The same pattern — a theory that explains a lot but eventually fails one decisive test — recurs in Chapter 28 (the ether) and Chapter 29 (classical orbital atoms).

---

## Concept 2 — Specific heat and phase change

### A copper saucepan on a January morning

Pour 250 mL of water from the tap into a clean copper-bottomed saucepan, set it on a 1500-watt electric burner, and time how long it takes to come to a rolling boil. About three and a half minutes, give or take, on a good stove. Now do the same experiment with the same volume of cooking oil. Faster — about a minute and a half. Same volume, same burner, same starting temperature, very different times. The water resists heating in a way the oil does not.

The number that captures the resistance is called **specific heat**. It is the energy required to raise one kilogram of a substance by one degree Celsius. Water's specific heat is about $4186 \text{ J/(kg} \cdot \text{°C)}$ — five times that of glass, ten times that of iron, and roughly twice that of cooking oil. Among common substances, water is an outlier, and its outlier status is most of why life on Earth is possible. A planet covered in water has a thermostat built into its oceans.

### The mechanism — $Q = mc\Delta T$

The relationship between heat transfer, temperature change, and substance is captured in a single equation:

$$Q = m c \Delta T,$$

where $Q$ is the heat transferred (joules), $m$ is the mass (kg), $c$ is the specific heat (J/(kg·°C)), and $\Delta T$ is the temperature change (°C or K — the units are identical for a *difference*, only the zero point differs). This equation is exact when no phase change occurs and the specific heat is roughly constant over the temperature range. Both assumptions hold for most introductory problems. Both fail near phase boundaries and at very low or very high temperatures, but those are problems for a graduate course.

A short table of specific heats, from the OpenStax data:

| Substance | $c$ (J/(kg·°C)) |
|---|---|
| Water (15 °C) | 4186 |
| Ice (avg, −50 to 0 °C) | 2090 |
| Ethanol | 2450 |
| Aluminum | 900 |
| Glass | 840 |
| Iron, steel | 452 |
| Copper | 387 |
| Silver | 235 |
| Lead | 128 |
| Human body (avg at 37 °C) | 3500 |

Notice that the human body sits near water — about 60% of you, by mass, *is* water — which is part of why your body temperature is so stable. It takes 3,500 joules to warm a kilogram of you by one degree. A 70 kg person warming by a single degree Celsius absorbs about 245 kJ — roughly the energy in a slice of bread.

### Phase change — the latent heats

Heat $Q = mc\Delta T$ describes warming and cooling *between* phase changes. Inside a phase change — ice melting at 0 °C, water boiling at 100 °C — temperature does not change while heat is being added. The energy goes into breaking molecular bonds, not into faster molecular motion. The amount of heat required:

$$Q = m L_f \quad \text{(melting / freezing)},$$
$$Q = m L_v \quad \text{(vaporization / condensation)},$$

where $L_f$ is the **latent heat of fusion** and $L_v$ is the **latent heat of vaporization**. *Latent* means *hidden* — the energy is going somewhere, but the thermometer shows no change.

Water again is exceptional. To melt one kilogram of ice at 0 °C into one kilogram of water at 0 °C requires $L_f = 334 \text{ kJ/kg}$. To vaporize one kilogram of water at 100 °C into steam at 100 °C requires $L_v = 2256 \text{ kJ/kg}$ — six and a half times the energy of melting, and equivalent to the energy required to raise a kilogram of liquid water from 0 °C all the way to 540 °C if no boiling occurred. This is enormous. It is the reason a pot of water at a steady boil takes a long time to evaporate dry, the reason humid air feels oppressive at 35 °C, and the reason that orange growers in Florida spray their trees with water before a frost: the freezing water releases 334 kJ per kilogram, just enough to keep the fruit a little above 0 °C while the spray turns to ice.

### The trade-off

The $Q = mc\Delta T$ formula trades **temperature dependence for arithmetic simplicity.** Real specific heats vary, sometimes substantially, over wide temperature ranges. Treating $c$ as constant is fine for a 60 °C window; it would mislead badly for a 600 °C window. The honest physicist looks at the temperature range first, then decides whether the constant-$c$ shortcut is acceptable.

### Worked example — pouring cold water into a hot aluminum pan

You pour 0.250 kg of 20.0 °C water into a 0.500 kg aluminum pan that was sitting at 150 °C. The pan is on an insulated pad. What is the final equilibrium temperature?

**Reasoning.** No heat escapes; heat lost by the pan equals heat gained by the water:

$$m_w c_w (T_f - 20.0) = - m_{Al} c_{Al} (T_f - 150).$$

Solve for $T_f$:

$$T_f = \frac{m_{Al} c_{Al} (150) + m_w c_w (20.0)}{m_{Al} c_{Al} + m_w c_w}.$$

With $c_{Al} = 900$ and $c_w = 4186$:

$$T_f = \frac{(0.500)(900)(150) + (0.250)(4186)(20.0)}{(0.500)(900) + (0.250)(4186)} = \frac{67{,}500 + 20{,}930}{450 + 1046.5} = \frac{88{,}430}{1{,}496.5} \approx 59.1 \text{ °C}.$$

**Sanity check.** Why is the final temperature so much closer to the water's starting temperature (20 °C) than to the pan's (150 °C)? Because water's specific heat is more than four times that of aluminum, and the masses partly compensate but not enough. Water dominates the heat capacity of the system. Lakes and oceans dominate the heat capacity of the planet for the same reason.

**The general lesson.** A calorimetry problem is a bookkeeping exercise. Set heat-in equal to negative heat-out, write each side using $Q = mc\Delta T$ (or $Q = mL$ if a phase change is involved), and solve for the unknown.

### Common misconceptions

- *"Adding heat always raises temperature."* Not during a phase change. Pour 1 kJ into a slush of ice and water at 0 °C and the mixture stays at 0 °C — some ice melts, but nothing warms.
- *"Specific heat is the same for all phases of one substance."* No — ice, liquid water, and steam each have their own specific heat (2090, 4186, and ~2010 J/(kg·°C) respectively). The substance is the same; the molecular environment is not.

↳ **Dig Deeper — Why is water's specific heat so high?**

*Water's specific heat is anomalously high among common substances. Methanol, ethanol, and most other small molecules sit between 1500 and 2500 J/(kg·°C); water sits at 4186. The explanation lies in hydrogen bonding — and that explanation in turn predicts a lot of water's other anomalies (high boiling point, high surface tension, ice floating).*

**Prompt:**
> Explain why liquid water has an anomalously high specific heat compared to other small molecules. Walk me through the molecular mechanism (hydrogen bonding between H₂O molecules) and how it absorbs energy without raising kinetic energy as efficiently. Then connect this to two other water anomalies — its high boiling point relative to H₂S, and the fact that ice floats on liquid water. End with one sentence on why these anomalies matter for life on Earth.

**What to do with the output:** Save it. The hydrogen-bond story shows up again in Chapter 26 (vision, biological optics) and in any biology course that touches osmosis or membrane physics.

---

## Concept 3 — The three modes of heat transfer

### A coffee cup, a fan, and a sun

Hold a paper coffee cup full of hot coffee. The paper warms in your hand — that is conduction, energy hopping atom-by-atom from the hot inside surface of the cup, through the paper, to your skin. Above the cup, steam rises and curls — that is convection, hot, low-density air carrying its energy upward by bulk motion. And if you set the cup down by a sunny window, the side facing the sun warms even though no air or contact connects them — that is radiation, electromagnetic waves carrying energy across the gap.

Three mechanisms. Every heat transfer in the universe is some combination of these three, and learning to spot which one dominates a given problem is the work of this concept.

### Conduction

**Conduction** is heat transfer through stationary matter by physical contact, by atom-to-atom collisions and electron motion. The rate equation:

$$\frac{Q}{t} = \frac{k A (T_2 - T_1)}{d},$$

where $k$ is the **thermal conductivity** of the material (units J/(s·m·°C) or W/(m·°C)), $A$ is the cross-sectional area, $d$ is the thickness, and $T_2 - T_1$ is the temperature difference across the slab.

A short table:

| Substance | $k$ (W/(m·°C)) |
|---|---|
| Silver | 420 |
| Copper | 390 |
| Aluminum | 220 |
| Steel (stainless) | 14 |
| Ice | 2.2 |
| Glass | 0.84 |
| Water | 0.6 |
| Wood | 0.08–0.16 |
| Air | 0.023 |
| Styrofoam | 0.010 |

The four-orders-of-magnitude spread between silver and Styrofoam is what makes thermal engineering possible. A copper saucepan delivers stovetop heat efficiently to the food. A Styrofoam cooler keeps that same heat *out* of your beer at the beach. The same physics, different choice of $k$.

The R-factor often quoted for building insulation is just $d/k$ in awkward customary units — bigger R, bigger ratio of thickness to conductivity, slower heat flow.

**Worked example — heat through a Styrofoam cooler.** A Styrofoam ice box has area $A = 0.950 \text{ m}^2$, walls 2.50 cm thick, holding ice at 0 °C in a car trunk at 35 °C. Conductive rate:

$$\frac{Q}{t} = \frac{(0.010)(0.950)(35 - 0)}{0.0250} \approx 13.3 \text{ W}.$$

In one day ($86{,}400 \text{ s}$), $Q \approx 1.15 \times 10^6 \text{ J}$. With $L_f = 334 \times 10^3 \text{ J/kg}$ for water, the mass of ice melted is $m = Q/L_f \approx 3.44 \text{ kg}$ — about a 7-pound bag, which matches grocery-store experience.

### Convection

**Convection** is heat transfer by the bulk motion of a fluid (a liquid or a gas). Hot fluid rises because it is less dense; cool fluid sinks; a circulation cell forms and carries energy from one region to another. Atmospheric circulation, ocean currents, the heating of a room by a radiator, and the steam off a coffee — all convection.

We do not typically write down a single rate equation for convection because the rate depends on too many things at once (geometry, viscosity, fluid properties, gravity). What we do is *track the moving mass*. If you can compute how much fluid moves and by how much its temperature changes, you can use $Q = mc\Delta T$ on the moving fluid.

**Worked example — air leakage in a leaky house.** A house with interior dimensions $12.0 \times 18.0 \times 3.00$ m (volume 648 m³) has all its air replaced every 30 minutes (a leaky old house). The cold air entering must be warmed by 10.0 °C. Mass of air per replacement: $m = \rho V = (1.29 \text{ kg/m}^3)(648 \text{ m}^3) \approx 836 \text{ kg}$. Energy per replacement: $Q = mc\Delta T = (836)(1000)(10.0) \approx 8.36 \times 10^6 \text{ J}$. Rate: divide by 1800 s, get about 4.64 kW.

That is 46 hundred-watt light bulbs of heat just keeping up with air leakage. A modern weatherized house turns over its air roughly every two hours instead of every thirty minutes, cutting that loss by a factor of four.

### Radiation

**Radiation** is heat transfer by electromagnetic waves. No medium required — radiation is how the Sun's energy reaches Earth across 150 million kilometers of vacuum. The rate equation, called the Stefan-Boltzmann law:

$$\frac{Q}{t} = \sigma e A T^4,$$

where $\sigma = 5.67 \times 10^{-8} \text{ W/(m}^2 \cdot \text{K}^4)$ is the Stefan-Boltzmann constant, $A$ is the radiating surface area, $T$ is the absolute temperature in *kelvin* (not Celsius — this matters), and $e$ is the **emissivity**, a dimensionless number between 0 and 1 that captures how good the surface is at radiating. A perfect black-body has $e = 1$; a perfect mirror has $e = 0$. Skin in the infrared has $e \approx 0.97$ — almost a perfect radiator, which is why night-vision cameras pick up humans so easily.

The fourth-power dependence is dramatic. A surface at 600 K radiates not twice as much but $2^4 = 16$ times as much as a surface at 300 K.

For a body at temperature $T_1$ surrounded by an environment at $T_2$, the *net* rate of radiative transfer is

$$\frac{Q_\text{net}}{t} = \sigma e A (T_2^4 - T_1^4),$$

which is positive when the surroundings are hotter than the body (net heat in) and negative when the body is hotter (net heat out).

**Worked example — a person in a cool room.** A person with skin temperature 33.0 °C (306 K), surface area 1.50 m², emissivity 0.97, in a room at 22.0 °C (295 K):

$$\frac{Q_\text{net}}{t} = (5.67 \times 10^{-8})(0.97)(1.50)\left[(295)^4 - (306)^4\right] \approx -99 \text{ W}.$$

Almost a hundred watts of radiation leaving the body to the room, just from the temperature difference. A resting person produces about 125 W of metabolic heat. Without clothes, just from radiation, the person is losing nearly all of it to the walls — and conduction and convection add to the loss. This is why an unclothed person in a 22 °C room feels cold despite "room temperature" being above body temperature for the *interior* of the body. The skin is cooler than the core, and the room is colder than the skin.

### The trade-off — pick the right mode

Each mode trades **range of applicability for accuracy.** Conduction equations require a steady temperature gradient through a stationary slab. Convection rate calculations require knowing the bulk flow, which usually requires fluid mechanics. Radiation requires the Stefan-Boltzmann law and absolute temperatures. In any real problem, all three are happening at once — your coffee cup loses heat by conduction through the cup wall, convection of warm air rising off the cup, and infrared radiation in every direction. The skill is identifying which mode dominates so you can reason about it cleanly.

### Common misconceptions

- *"Cold flows from cold objects to hot ones."* No. Heat flows from hot to cold. "Cold" is just *less hot*; there is no separate substance flowing the other way.
- *"Radiation requires a hot, glowing object."* No — every object above absolute zero radiates. You are radiating right now, mostly in the infrared at wavelengths around 10 μm. We see "glow" only when the object is hot enough to radiate visibly (red-hot starts around 800 K).
- *"Black objects always heat up faster."* They absorb radiation faster *and* emit it faster. On a sunny day, a black asphalt parking lot is hotter than gray sidewalk. On a clear night, the same asphalt is cooler than the sidewalk. Same emissivity, opposite signs of net flux.

↳ **Dig Deeper — The greenhouse effect, quantitatively**

*The chapter mentions that Earth's atmosphere keeps the planet about 33 °C warmer than it would be without one. That number comes from a calculation you can do yourself — comparing the radiative equilibrium temperature of a bare rock at Earth's distance from the Sun with the actual temperature of Earth's surface. The mismatch is the greenhouse effect, and the climate debate is fundamentally an argument about how big the mismatch is and how it changes when we add CO₂.*

**Prompt:**
> Walk me through the calculation of Earth's "no-atmosphere" radiative equilibrium temperature. Start with the solar constant (~1361 W/m²), apply Earth's geometric cross-section vs. surface area (factor of 4), apply Earth's albedo (~0.30), and use the Stefan-Boltzmann law to solve for the equilibrium temperature. Compare the result to Earth's actual average surface temperature (~288 K). Explain how greenhouse gases (CO₂, water vapor, methane) close that gap by absorbing outgoing infrared and re-radiating it back. End with one sentence on what changes when CO₂ concentration doubles.

**What to do with the output:** Save it. This is the load-bearing physics under every climate model. Re-read it after Chapter 24 (electromagnetic spectrum) — the absorption bands of CO₂ in the infrared are the actual mechanism, and seeing the spectrum makes the story concrete.

---

## Synthesis — heat transfer as a single bookkeeping discipline

Step back. You have three rate equations and two state equations. Together they let you write an energy balance for any thermal system you encounter:

- $Q = mc\Delta T$ for bulk warming or cooling.
- $Q = mL$ for phase changes at fixed temperature.
- $Q/t = kA(T_2 - T_1)/d$ for steady-state conduction.
- $Q/t = (\text{flow rate}) \cdot c \cdot \Delta T$ for convection of a bulk fluid.
- $Q/t = \sigma e A (T_2^4 - T_1^4)$ for net radiation.

The trick in any real problem is recognizing which of these terms appear and at what rate, then writing $\sum Q_\text{in} = \sum Q_\text{out}$ for steady state, or $\sum Q = mc\Delta T_\text{system}$ for transient warming.

### A worked example using all three modes — the iceberg in warm water

A 1986 iceberg from the Ross Ice Shelf — roughly 160 km × 40 km × 250 m, density 917 kg/m³ — drifted into warm Atlantic water. About how long would the ice take to melt under sustained 100 W/m² of solar absorption (a generous half-day average)?

**Mass of ice.** Volume: $V = 160{,}000 \times 40{,}000 \times 250 \approx 1.6 \times 10^{12} \text{ m}^3$. Mass: $m = \rho V = (917)(1.6 \times 10^{12}) \approx 1.5 \times 10^{15} \text{ kg}$.

**Energy required to melt it.** $Q = m L_f = (1.5 \times 10^{15})(334 \times 10^3) \approx 5.0 \times 10^{20} \text{ J}$.

**Top surface area** (sun absorbs from above only): $A = 160{,}000 \times 40{,}000 = 6.4 \times 10^9 \text{ m}^2$. At 100 W/m² for 12 h/day = 43,200 s/day, daily energy in: $E_\text{day} = 100 \times 6.4 \times 10^9 \times 43{,}200 \approx 2.8 \times 10^{16} \text{ J/day}$.

**Days to melt by sun alone:** $5.0 \times 10^{20} / 2.8 \times 10^{16} \approx 1.8 \times 10^4 \text{ days}$ — about 49 years.

The iceberg is so massive, and the latent heat of fusion of water so large, that even a continuous radiative input plus contact with warm water takes years to melt it. This is why the long-tail visual signature of climate change in the Arctic — actual ice melt — lags so far behind the temperature trend driving it. The ice is a gigantic heat sink with a 50-year time constant.

**Scale shift.** That same calculation, scaled down by 15 orders of magnitude, governs how long it takes the cube of ice in your gin and tonic to melt — about 10 minutes, with the warm tonic playing the role of the warm Atlantic, and convection in the glass dominating the heat input. The physics is identical. Only the size of $m$ and $A$ change.

---

## Exercises

### Warm-up

**14.1** *(LO 1)* Convert 250 Calories (Cal, dietary) into joules. Then estimate how long you would have to lift a 50 kg barbell through 0.5 m, once per second, to burn that energy. Ignore inefficiency.

**14.2** *(LO 2)* A 0.500 kg block of copper is heated from 20.0 °C to 80.0 °C. How much heat was added? ($c_{Cu} = 387 \text{ J/(kg·°C)}$.)

**14.3** *(LO 3)* How much heat is required to convert 0.100 kg of ice at 0 °C to liquid water at 0 °C? To convert that liquid water to steam at 100 °C? Compare the two.

**14.4** *(LO 4)* A glass window 1.0 m² in area and 5.0 mm thick separates a room at 20 °C from outside air at 0 °C. At what rate (in watts) does heat conduct through it? ($k_\text{glass} = 0.84 \text{ W/(m·°C)}$.)

### Application

**14.5** *(LO 2)* On a hot day, a swimming pool with 80,000 L of water warms by 1.50 °C from sun alone. How much energy was absorbed? Convert to kWh and estimate the energy bill if this had to be supplied by an electric heater at $0.15 / kWh.

**14.6** *(LO 3)* You drop three ice cubes (6.0 g each, at 0 °C) into 0.250 kg of soda at 20 °C in a foam cup. What is the final temperature once all the ice has melted, assuming no heat loss to the cup? (Treat the soda as water.) Show that two of the cubes would have given a different answer.

**14.7** *(LO 5)* An unclothed person stands in a 5 °C walk-in cooler. Skin temperature 33 °C, surface area 1.7 m², emissivity 0.97. Compute the net radiative heat loss in watts. Compare to a sedentary metabolic rate of 100 W. Does this person warm or cool?

**14.8** *(LO 4)* A house attic has 15 cm of fiberglass insulation (k ≈ 0.040 W/(m·°C)) over a 150 m² ceiling. Inside is 20 °C, attic is 5 °C. How much power leaks through the ceiling? If the heating system runs at $0.15/kWh of electricity, what is the daily cost just for ceiling losses?

### Synthesis

**14.9** *(LO 2, 3, 5)* You boil water in an aluminum pan to make pasta. The pan is 0.500 kg, contains 1.50 L of water initially at 18 °C, on a 1500 W burner. (a) How long until the water reaches boiling? (b) Once at 100 °C, at what rate (in g/s) is water boiling away if all the burner's power goes into vaporization?

**14.10** *(LO 6)* A campfire warms you when you stand 1 m away. Identify the dominant mode of heat transfer. Now you crouch and put your hands directly above the flames — does the dominant mode change? Why?

**14.11** *(LO 5, beyond chapter)* The Sun radiates as a near-perfect black body at about 5800 K. Using the Stefan-Boltzmann law, compute the total power output of the Sun (radius $7.0 \times 10^8$ m). Then compute the intensity (W/m²) at Earth's distance ($1.5 \times 10^{11}$ m). Compare your answer to the published solar constant of about 1361 W/m².

### Challenge

**14.12** *(LO 2, 3, beyond chapter)* You want to cool a 350 g cup of 95 °C coffee to 45 °C. You can either (a) wait for evaporation alone, or (b) drop in ice cubes. For each path, compute either how much coffee (in g) must evaporate, or how much 0 °C ice (in g) must melt. Use $L_v = 2340 \text{ kJ/kg}$ at this temperature.

**14.13** *(LO 5, 6, beyond chapter)* A double-paned window has two 0.80 cm panes of glass separated by a 1.00 cm air gap. Total area 1.50 m². Inside 15 °C, outside −10 °C. Treat each interface as a series resistor for conduction. Compute the heat-loss rate. Now compare to a single-pane window of the same total thickness ($2 \times 0.80 + 1.0 = 2.60$ cm) of pure glass. Why is the air gap such a powerful insulator despite air's tiny thickness?

---

## LLM Exercise — Chapter 14: Heat Transfer in Your Anchor Phenomenon

**Project:** Physics Reality Check Logbook
**What you're building this chapter:** A heat-transfer balance for one moment of your anchor phenomenon — at least one mode (conduction, convection, or radiation) computed honestly with units and uncertainty.
**Tool:** Claude Project.

### The Prompt

```
I'm continuing my Physics Reality Check Logbook for College Physics with LLMs. My anchor phenomenon is [paste the 1-sentence description from Chapter 1].

For Chapter 14 (Heat and Heat Transfer), I want to apply heat-transfer physics to ONE moment of my phenomenon where temperature change or thermal flow matters.

Please:

1. Identify ONE specific thermal moment in my phenomenon. Examples:
   - Coffee maker: the rate of heat loss from the carafe when full of hot coffee.
   - Bike commute: the rate at which I lose heat to the wind by forced convection.
   - Marathon: the metabolic heat I generate per minute and how my body sheds it.
   - Espresso machine: the energy required to bring the boiler from 20°C to 95°C.

2. Identify which mode of heat transfer dominates (conduction, convection, radiation, or a phase change). Justify.

3. Write the relevant equation. List inputs I need: surface areas, temperatures, masses, conductivities, emissivities. For each, tell me where to source the number and what uncertainty to expect.

4. Plug in and solve. Report Q (or Q/t) with proper units and uncertainty.

5. Sanity check against a published number for a comparable system if possible.

6. Identify ONE assumption that might fail in my actual situation and flag it.

7. Connect to Chapter 15 (Thermodynamics) — what efficiency or work-vs-heat question is now lurking?

Save the output as logbook/chapter-14-heat-transfer.md.
```

### What this produces

Your fourteenth Logbook entry — a quantified heat balance that turns the chapter's equations into a defensible number for your anchor phenomenon.

### How to adapt this prompt

- *For phenomena dominated by phase change* (boiling, sweating, freezing): emphasize $Q = mL$ over $Q = mc\Delta T$.
- *For phenomena dominated by radiation* (anything with the sun, anything with infrared imaging): use the net Stefan-Boltzmann formula and remember to convert temperature to kelvin.
- *For Claude Code:* If you have time-series temperature data (from a thermometer or smart device), use Code instead — fit an exponential decay and extract the time constant, which will give you an effective $h \cdot A$ product for the system.

### Connection to previous chapters

Builds on Chapter 13's temperature/equilibrium definitions. Uses Chapter 7's energy bookkeeping. The uncertainty propagation rules from Chapter 1 still apply.

### Preview of next chapter

Chapter 15 introduces the laws of thermodynamics — energy conservation including heat, the impossibility of perfect engines, and entropy. The Chapter 15 LLM Exercise will ask you to compute an efficiency for whatever heat-conversion process is lurking in your phenomenon.

---

## Chapter summary

Heat is energy in transit between objects at different temperatures — not a property of an object, but a flow defined by what crosses a boundary. Three commitments:

1. **Heat and work are interchangeable forms of energy.** Joule's $1 \text{ kcal} = 4186 \text{ J}$ is the conversion. The internal energy of a system can be raised by either heat transfer or work done on it; afterwards the two paths are indistinguishable.

2. **The amount of heat to change a state has a clean formula.** $Q = mc\Delta T$ for warming or cooling without phase change. $Q = mL$ for phase change at constant temperature. Specific heats and latent heats are tabulated; you look them up and plug them in.

3. **Three modes of transfer: conduction, convection, radiation.** Each has its own rate equation. Real systems involve all three. The skill is identifying the dominant mode and bounding the others.

The one idea that matters most: **temperature differences drive heat flow, and the rate of flow depends on the path's properties (conductivity, geometry, emissivity), not just the difference.** The kitchen tile and the wool carpet are at the same temperature; they feel different because they remove heat from your foot at different rates.

The common mistake to watch for: **forgetting absolute temperature in the radiation law.** The Stefan-Boltzmann law uses kelvin, not Celsius, and the fourth power amplifies any error catastrophically.

---

## What would change my mind

The chapter argues that the three rate equations (conduction, convection, radiation) suffice to describe nearly any heat-transfer scenario in introductory physics. The argument would need revision if a routine engineering problem in this regime — say, the design of a CPU heat sink or a single-glazed window — were poorly approximated by these tools alone. They aren't; computational fluid dynamics refines convection in detail, but the orders of magnitude come from the simple equations above.

## Still puzzling

The deepest puzzle this chapter raises: *why does heat flow only from hot to cold and never the other way, when the underlying molecular collisions are all microscopically reversible?* The asymmetry is the second law of thermodynamics, and we will meet it head-on in Chapter 15. Until then, hold the puzzle: every individual molecular collision could run backwards in time, but the bulk transfer of heat always picks one direction. Why?

---

## Connections forward

Chapter 15 introduces **thermodynamics** — the laws governing energy flow, the impossibility of perfectly efficient engines, and entropy. The rate equations of Chapter 14 tell you *how fast* heat moves; thermodynamics tells you *what fraction of that heat can be turned into useful work*. Chapter 16 begins oscillations, where the energy bookkeeping habits installed here will reappear in mechanical and thermal damping. The Stefan-Boltzmann law you used here is the foundation of Chapter 29 (quantum mechanics) — historically, the failure of classical physics to predict the *spectral* shape of black-body radiation is what forced Planck to invent the quantum.

---

**Tags:** heat-transfer, specific-heat, latent-heat, conduction, radiation

---

## AI Wayback Machine

**Joseph Fourier** developed the mathematical theory of heat conduction in 1822 — including the partial differential equation that bears his name. Modern heat transfer engineering still uses Fourier's framework directly.

**Run this:**

```
Who was Joseph Fourier, and how does the Fourier heat equation connect to heat transfer we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about his career or ideas.
```

→ Search **"Joseph Fourier"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to walk through the Fourier heat equation and what each term represents physically.
- Ask it about Fourier's parallel role as governor of Egypt under Napoleon — and how that work shaped his physics.

What changes? What gets better? What gets worse?
