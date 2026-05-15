# Chapter 1 — Temperature and Thermal Energy

*Temperature is not heat. Thermal energy is not temperature. Heat is energy in transit.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Understand)** Distinguish temperature (state variable, intensive), thermal energy (state variable, extensive), and heat (process quantity, path-dependent) in plain language.
2. **(Apply)** Use the molecular definition $T = \langle KE\rangle / k_B \times $ (factor depending on degrees of freedom) to predict molecular speeds from temperature.
3. **(Apply)** Apply thermal expansion formulas (linear $\Delta L = \alpha L_0 \Delta T$; volume $\Delta V = \beta V_0 \Delta T$) to engineering problems.
4. **(Apply)** Solve calorimetry problems with multiple substances reaching thermal equilibrium.
5. **(Understand)** State the Zeroth Law of Thermodynamics and explain why it underlies all thermometry.
6. **(Apply)** Build a molecular speed-distribution visualizer at adjustable temperature.

---

## Opening case: a cold ocean and a warm bathtub

You step into the ocean off Maine in summer: water at 12°C. Painfully cold. You step into a bathtub at home: water at 38°C. Comfortable.

A small fact: the ocean contains *vastly more* thermal energy than the bathtub. The ocean's total internal kinetic energy of water molecules — the thermal energy $U$ — exceeds the bathtub's by many orders of magnitude. Same molecules; the ocean just has more of them. The ocean is "thermally rich"; the bathtub is "thermally poor."

But you feel cold in the ocean and warm in the bath. Why? Because *heat flow* is driven by *temperature differences*, not by thermal energy differences. Your skin is at ~33°C. The ocean (12°C) is colder than you, so heat flows *out* of your skin. The bath (38°C) is hotter than you, so heat flows *in*. Direction of flow follows temperature, not thermal energy.

This is the single most common confusion in thermodynamics: *temperature vs. thermal energy vs. heat*. The chapter ahead sorts them out, defines them precisely, and uses them throughout the rest of the book.

---

## Core concept

### Temperature: a state variable, measured from $\langle KE\rangle$

**Temperature** $T$ is an intensive state variable — it characterizes the system but doesn't depend on the system's size. At the molecular level:

$$T = \frac{2 \langle KE \rangle_{\text{translational}}}{f \cdot k_B}$$

where $\langle KE \rangle_{\text{translational}}$ is the average translational kinetic energy per molecule, $f$ is the number of translational degrees of freedom (3 for 3D), and $k_B = 1.38 \times 10^{-23}$ J/K is the Boltzmann constant.

For a monatomic ideal gas in 3D:
$$T = \frac{2}{3 k_B} \langle KE \rangle = \frac{m \langle v^2 \rangle}{3 k_B}$$

**The Kelvin scale.** Absolute temperature scale, used in all thermodynamic equations. $T(K) = T(°C) + 273.15$. Absolute zero ($T = 0$ K) corresponds to no thermal motion (classical limit; quantum zero-point energy remains, but the chapter treats that as a footnote).

**Source:** $k_B$ is exact since 2019: $k_B = 1.380649 \times 10^{-23}$ J/K (BIPM SI Brochure, 2019 redefinition).

### Thermal energy: the system's internal kinetic + potential energy

**Thermal energy** $U_{\text{thermal}}$ is the total internal energy of all molecules — sum of all translational kinetic energies, plus rotational and vibrational modes (in molecules), plus intermolecular potential energy (in non-ideal systems).

Extensive (proportional to system size). For a monatomic ideal gas: $U = (3/2) N k_B T$. For a diatomic gas at moderate temperature (where rotation is excited but vibration is not): $U = (5/2) N k_B T$.

Note: temperature is a *per-molecule* quantity (intensive), while thermal energy is a *total* quantity (extensive). A bathtub at 38°C and an ocean at 12°C have very different thermal energies but only differ by ~26 K in temperature.

### Heat: energy in transit, due to a temperature difference

**Heat** $Q$ is energy that flows from one system to another *because of a temperature difference*. It is not a property of either system — it's a process quantity, like "force" applied during a motion.

Units: joules (SI). Sometimes calories: 1 cal = 4.184 J.

Heat flows from hot to cold. Spontaneously, never the reverse (that's the Second Law, Chapter 6).

The three mechanisms by which heat moves (Chapter 2) are conduction (through materials), convection (with moving fluid), and radiation (electromagnetic).

### The Zeroth Law: the basis of thermometry

If system A is in thermal equilibrium with system C, and system B is in thermal equilibrium with C, then A is in thermal equilibrium with B.

This *trivial-sounding* claim is the foundation of all thermometry. Without it, "temperature" wouldn't be a well-defined property — we could put a thermometer (system C) in contact with two objects (A and B) that read the same temperature, and yet the objects might not be in equilibrium with each other. The Zeroth Law says they are.

The law was named "zeroth" because it was recognized as logically prior to the first three laws but was identified after they were named — by Ralph Fowler in the 1930s.

### Thermal expansion

Most materials expand when heated. Linear expansion (1D):
$$\Delta L = \alpha L_0 \Delta T$$

where $\alpha$ is the linear thermal expansion coefficient. For steel: $\alpha \approx 12 \times 10^{-6}$ /K. For aluminum: $\sim 23 \times 10^{-6}$ /K.

Volume expansion (3D):
$$\Delta V = \beta V_0 \Delta T$$

For isotropic solids, $\beta \approx 3\alpha$.

**Thermal stress.** When a material is heated but constrained from expanding (e.g., a steel beam fixed at both ends), thermal stress builds up: $\sigma = E \alpha \Delta T$, where $E$ is Young's modulus. For a steel beam constrained over a 30°C rise: $\sigma = (200 \times 10^9) \cdot (12 \times 10^{-6}) \cdot 30 = 7.2 \times 10^7$ Pa = 72 MPa. Substantial — engineers leave expansion joints in bridges and railroad rails to avoid this.

**Anomalous expansion of water.** Water has a *negative* thermal expansion coefficient between 0°C and 4°C — it *contracts* when heated in this range, reaching maximum density at 4°C. This is why ice floats and why aquatic ecosystems survive freezing winters: ice forms at the surface, insulating the water below.

### Specific heat capacity

The energy needed to raise one unit mass by one degree:
$$Q = m c \Delta T$$

Common values:
- Water: $c = 4186$ J/(kg·K). Anomalously high.
- Ice: $c = 2090$ J/(kg·K).
- Aluminum: $c = 900$ J/(kg·K).
- Iron: $c = 449$ J/(kg·K).
- Copper: $c = 385$ J/(kg·K).
- Air (constant pressure): $c_p = 1005$ J/(kg·K).

Water's high specific heat is *physically consequential*: oceans moderate Earth's climate (slow temperature changes); coastal areas have milder weather than inland; cooking requires more energy when you have a lot of water in the pan.

### Calorimetry

When two systems at different temperatures come into thermal contact and reach equilibrium, the heat lost by the hotter equals the heat gained by the colder:
$$Q_{\text{lost by hot}} = Q_{\text{gained by cold}}$$
$$m_1 c_1 (T_1 - T_f) = m_2 c_2 (T_f - T_2)$$

Solve for the final equilibrium temperature $T_f$.

---

## Worked example: copper in water

A 200 g copper block at 80°C is placed in 500 g of water at 20°C. Find the final equilibrium temperature.

**Setup.** Let $T_f$ = final temperature. Copper cools from 80°C to $T_f$; water warms from 20°C to $T_f$.

**Apply conservation of energy:**
$$m_{\text{Cu}} c_{\text{Cu}} (80 - T_f) = m_{\text{H₂O}} c_{\text{H₂O}} (T_f - 20)$$

Plug in numbers ($c_{\text{Cu}} = 385$, $c_{\text{H₂O}} = 4186$ J/(kg·K)):
$$(0.200)(385)(80 - T_f) = (0.500)(4186)(T_f - 20)$$
$$77(80 - T_f) = 2093(T_f - 20)$$
$$6160 - 77T_f = 2093 T_f - 41860$$
$$48020 = 2170 T_f$$
$$T_f \approx 22.1°C$$

The copper cools dramatically (from 80°C to 22°C), and the water barely warms (from 20°C to 22°C). Why? Because water has *11× the specific heat* of copper. The thermal energy lost by the small amount of copper is gained by the much larger thermal heat capacity of the water.

**The lesson.** Temperature changes inversely with heat capacity. A high-heat-capacity reservoir barely changes temperature in response to small heat inputs — the principle behind every thermal buffer (thermostat, thermal mass in buildings, the ocean's role in climate).

**The limit.** This calculation assumes no heat loss to the surroundings. In practice, calorimetry experiments use insulated containers; the chapter's idealization breaks down for non-insulated systems.

---

## Common misconceptions

**"Temperature and heat are the same thing."** Temperature is a state variable. Heat is energy in transit. A bathtub and an ocean at the same temperature have different thermal energies; both can transfer heat, but heat flows from the hotter object to the colder, regardless of which has more thermal energy.

**"Heat flows from objects with more energy to objects with less energy."** No. Heat flows from hot to cold, regardless of energy content. An ocean at 12°C has vastly more thermal energy than a bathtub at 38°C, but heat flows from the bathtub (hot) to the ocean (cold) if they're in contact.

**"Absolute zero means no energy."** It means no *thermal* (translational kinetic) energy. Quantum mechanically, zero-point energy remains — every harmonic mode has a $(1/2)\hbar\omega$ ground-state energy even at $T = 0$. This is a real effect (helium remains liquid at atmospheric pressure even at 0 K), but the chapter treats it as a footnote.

**"Specific heats are temperature-independent."** Most are nearly so for narrow temperature ranges, but $c$ does depend on $T$, especially near phase transitions. Water's $c$ jumps from 2090 J/(kg·K) (ice) to 4186 J/(kg·K) (liquid), with a huge latent heat of melting (334 kJ/kg) in between.

**"Cold has its own substance."** No. "Cold" is the absence of thermal energy. The 18th-century "caloric" theory said cold was a separate fluid; Joule (1840s) and others demolished this. Heat is just energy.

---

## Exercises

**Warm-up (Apply).** Compute $T$ in Kelvin for room temperature (20°C), body temperature (37°C), and a comfortable shower (40°C).

**Apply.** Find the rms speed of nitrogen molecules (N₂, $m = 4.65 \times 10^{-26}$ kg) at $T = 300$ K. Use $T = m\langle v^2\rangle/(3k_B)$.

**Apply.** A steel rail 10 m long at 20°C. Find its length on a 50°C summer day. Then find the thermal stress if the rail is fixed at both ends and cannot expand. ($\alpha = 12 \times 10^{-6}$ /K; $E = 200$ GPa.)

**Apply + Analyze.** A 200 g aluminum cup at 25°C holds 300 g of water at 95°C. (a) Find the equilibrium temperature, assuming negligible heat loss to surroundings. (b) Does it matter what order you compute the heat losses/gains? Justify. ($c_{\text{Al}} = 900$, $c_{\text{water}} = 4186$ J/(kg·K).)

**Apply.** Two equal-volume containers, one with water (1 kg) and one with iron (7.87 kg same volume), both at 30°C. Each receives 5000 J of heat. Compute the temperature rise of each.

**Challenge.** Anomalous expansion of water. Look up or compute the volume of 1 kg of water at $T = 1°C$, 4°C, and 10°C. Show that water at 4°C is densest. Why does this matter for ice formation in lakes?

---

## LLM Exercises

### Build the temperature-distribution visualizer (`01-temperature-kinetic.html`)

> **Show.** Maxwell-Boltzmann speed distribution: $f(v) = 4\pi (m/(2\pi k_B T))^{3/2} v^2 \exp(-mv^2/(2k_B T))$. Three characteristic speeds: most probable $v_{mp} = \sqrt{2k_BT/m}$, average $v_{avg} = \sqrt{8k_BT/(\pi m)}$, rms $v_{rms} = \sqrt{3k_BT/m}$.
>
> **Say.** Build a temperature + speed distribution visualizer with animated particles.
>
> **Constrain.** D3 v7. 2D box with N=100 particles colored by speed. Slider for T (50–2000 K) and molecular mass (selector for H₂=2, N₂=28, O₂=32, Ar=40). When T is changed, rescale all particle velocities accordingly. Below the box: a histogram of particle speeds updating in real time, with the analytical Maxwell-Boltzmann curve overlaid as a smooth line. Vertical markers at $v_{mp}, v_{avg}, v_{rms}$ with labels. Filename: `01-temperature-kinetic.html`.
>
> **Verify.** (a) Lower T: distribution narrows and shifts left. (b) Heavier molecule at same T: distribution narrows and shifts left. (c) $v_{mp} < v_{avg} < v_{rms}$ always (the distribution is asymmetric).

### Exploration

- Compare H₂ and N₂ at the same temperature. H₂ is 14× lighter; its $v_{rms}$ is $\sqrt{14} \approx 3.7$× faster.
- Raise T from 300 K to 1200 K. The distribution should broaden by a factor of 2 ($\sqrt{4}$).
- What fraction of N₂ molecules at 300 K have $v > 1000$ m/s? (Very small — the tail decays exponentially.)

### Extension prompt (chapter bridge)

> **Show.** Different materials have different specific heats. Calorimetry: $Q_{\text{lost}} = Q_{\text{gained}}$ when systems reach equilibrium.
>
> **Say.** Build a calorimetry simulator: two substances in thermal contact, equilibrating over time.
>
> **Constrain.** Two boxes side by side, particles in each. Each box has its own initial $T_i$ and total energy. When the wall between them is "thermally conducting," energy flows: the hotter side's particles transfer energy to the cooler side via the boundary. Display each side's $T$ over time. They should converge to a common equilibrium $T_f$.
>
> **Verify.** $T_f$ matches the calorimetry calculation: $m_1 c_1 (T_1 - T_f) = m_2 c_2 (T_f - T_2)$.

Save as `01b-calorimetry-preview.html`. Bridge to Chapter 2.

---

## What would change my mind

The molecular definition of temperature ($T \propto \langle KE \rangle$) has been confirmed at every scale where measurement is possible — from ultracold gases at nanokelvin temperatures up through plasma physics at millions of degrees. The Boltzmann constant is now exact by definition (2019 SI). A confirmed measurement showing $T$ proportional to a different molecular property would force a fundamental rethink — none exists. Calorimetry calculations have been verified countless times.

## Still puzzling

- *What does temperature mean for a single particle?* Strictly, temperature is a property of an *ensemble*. A single particle has a kinetic energy, not a temperature. The thermodynamic limit ($N \to \infty$) is where temperature becomes a sharp variable. For small systems (microscopic devices, single biomolecules), temperature fluctuations are large and the concept gets subtle. *Stochastic thermodynamics* (the modern subfield) addresses this.
- *Negative temperatures.* In some unusual systems (laser-cooled atoms with restricted state spaces, nuclear spin systems), the population distribution can be inverted, with more high-energy than low-energy states. The formula $T = (\partial U/\partial S)^{-1}$ then gives negative $T$. Negative-temperature systems are *hotter than infinity* (they spontaneously transfer heat to any positive-$T$ object). Exotic but real; not in this book's scope.
- *Why does water have anomalously high specific heat?* Hydrogen bonding. Each water molecule can form up to four hydrogen bonds with neighbors; energy goes into breaking these bonds, not just into translational motion. Detailed chemistry beyond intro scope; the *consequence* (water as climate moderator) is in scope.

---

**Tags:** temperature, thermal energy, heat, Zeroth Law, Kelvin scale, thermal expansion, specific heat, calorimetry, Boltzmann constant

