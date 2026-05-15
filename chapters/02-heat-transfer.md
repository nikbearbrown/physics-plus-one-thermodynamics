# Chapter 2 — Heat Transfer

*Three mechanisms — conduction, convection, radiation — that move heat from hot to cold.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Use Fourier's law $P = kA \Delta T/L$ to compute heat flow rates through materials, and combine layers using thermal resistance.
2. **(Apply)** Use Newton's law of cooling $P = hA \Delta T$ to compute convective heat losses.
3. **(Apply)** Use the Stefan-Boltzmann law $P = \varepsilon \sigma A T^4$ to compute radiative heat transfer.
4. **(Apply)** Use Wien's displacement law $\lambda_{\max} T = 2.898 \times 10^{-3}$ m·K to predict peak wavelength of thermal emission.
5. **(Analyze)** For a given engineering scenario, identify which heat transfer mechanism dominates and apply the appropriate formula.
6. **(Apply)** Build a steady-state composite-wall conduction simulator.

---

## Opening case: why your coffee gets cold

You set down a fresh cup of coffee — say 90°C, in a room at 20°C. Within an hour it's lukewarm. The thermal energy doesn't disappear; it's transferred to the surroundings through three pathways operating simultaneously:

1. **Conduction** through the cup walls and the table beneath: a slow, steady drain.
2. **Convection** from the hot coffee surface to the air above (warm air rises, cool air sinks): the dominant loss mechanism for hot liquids.
3. **Radiation** as infrared photons from the coffee surface: about 100 mW for a typical cup, comparable to convection.

If you put a lid on the coffee, you reduce convection (no warm air can escape) and partially block radiation (some IR is absorbed in the lid). Heat loss drops; the coffee stays warm longer.

The chapter ahead is the quantitative law for each mechanism. Engineers use these to design insulation, refrigeration, and every device that creates or manages temperature differences.

---

## Core concept

### Conduction: Fourier's law

In a solid (or in a fluid at rest), heat conducts through molecular collisions. The rate of heat transfer through a slab of cross-sectional area $A$ and thickness $L$, with temperatures $T_H$ on one face and $T_C$ on the other:

$$P = k A \frac{T_H - T_C}{L}$$

where $P$ is the rate of heat transfer (watts) and $k$ is the **thermal conductivity** of the material (W/(m·K)).

Common values:
- Silver: $k \approx 430$ W/(m·K). Best conductor.
- Copper: 390. Used widely in heat sinks and electrical wires.
- Aluminum: 240.
- Glass: 0.8.
- Brick: 0.8.
- Wood: 0.13.
- Air: 0.026. Why insulation works: trap air.
- Fiberglass: ~0.04.
- Aerogel: 0.013. Modern wonder-material insulator.
- Water: 0.6. Better than air; why wet clothes are worse than dry for insulating.

**Thermal resistance.** Define $R = L/(kA)$ as the thermal resistance of a slab. Then $P = \Delta T / R$ — the analogue of Ohm's law for thermal circuits. Resistances in *series* add: $R_{\text{total}} = R_1 + R_2 + ...$. Composite walls (drywall + insulation + brick) have additive resistances.

**Steady-state temperature profile** in a composite wall: piecewise linear, with slope inversely proportional to $k$ in each layer. The temperature drops most steeply across the highest-resistance layer (i.e., the best insulator).

**R-value in construction.** In the US, R-value is typically reported in $\text{ft}^2 \cdot °F \cdot \text{h}/\text{BTU}$. R-13 fiberglass batting in a 2×4 wall is standard residential insulation. R-30 attic insulation is upgraded. R-50+ is passive-house grade.

### Convection: Newton's law of cooling

In a fluid (gas or liquid) where bulk motion is possible, heat moves with the moving fluid. For a surface at temperature $T_s$ in a fluid at $T_f$:

$$P = h A (T_s - T_f)$$

where $h$ is the **convection coefficient** (W/(m²·K)). $h$ depends strongly on geometry, fluid properties, and whether flow is *natural* (driven by buoyancy from temperature-induced density differences) or *forced* (driven by an external pump or wind).

Typical values:
- Natural convection in air: $h \approx 5$–25 W/(m²·K).
- Forced convection in air (typical wind): 25–250.
- Natural convection in water: 100–1000.
- Forced convection in water: 500–10,000.
- Boiling water: 10,000–100,000.

**Newton's law of cooling** as a differential equation: $dT/dt = -h A (T - T_f)/(m c)$. Solution: $T(t) = T_f + (T_0 - T_f) e^{-t/\tau}$ where $\tau = mc/(hA)$.

**Why wind feels cold.** Wind increases $h$ dramatically (forced vs. natural convection). Your body's surface temperature ~33°C. In still air (20°C, $h = 5$): heat loss rate ~$50 \cdot 13$ = 65 W/m². In 5 m/s wind ($h \sim 30$): ~$300 \cdot 13$ = 4 kW/m². Six times the heat loss. Wind chill is real.

### Radiation: Stefan-Boltzmann law

Every object at temperature $T > 0$ emits electromagnetic radiation. Total power radiated:

$$P_{\text{emit}} = \varepsilon \sigma A T^4$$

where $\sigma = 5.67 \times 10^{-8}$ W/(m²·K⁴) is the **Stefan-Boltzmann constant** and $\varepsilon$ is the **emissivity** (0 to 1; 0 for perfect reflector, 1 for blackbody, ~0.97 for human skin, ~0.04 for polished aluminum).

Net radiation between an object at $T_s$ and surroundings at $T_{\text{surr}}$:

$$P_{\text{net}} = \varepsilon \sigma A (T_s^4 - T_{\text{surr}}^4)$$

The $T^4$ dependence is dramatic: doubling $T$ increases emission by $16\times$. A red-hot object at 1000 K emits ~$10^4\times$ what it emits at 300 K.

**Wien's displacement law.** The wavelength at which blackbody emission peaks:

$$\lambda_{\max} T = 2.898 \times 10^{-3} \text{ m·K}$$

- Sun ($T \approx 5800$ K): $\lambda_{\max} \approx 500$ nm (green-yellow visible).
- Earth ($T \approx 288$ K): $\lambda_{\max} \approx 10$ μm (mid-infrared).
- CMB ($T \approx 2.7$ K): $\lambda_{\max} \approx 1$ mm (microwave).

**Source:** $\sigma$ is exact (CODATA 2018, defined in terms of $h$, $c$, $k_B$). Wien's constant: 2898 μm·K to four digits.

### The greenhouse effect

Earth's atmosphere is mostly transparent to incoming visible light from the Sun (5800 K spectrum, peak at 500 nm), but absorbs much of the outgoing infrared (288 K spectrum, peak at 10 μm). H₂O, CO₂, CH₄, and other greenhouse gases are particularly effective IR absorbers.

This *asymmetric transmission* warms the Earth's surface. Without it, Earth's surface would average ~255 K (about −18°C). With it, ~288 K. The 33 K difference is the natural greenhouse effect.

Anthropogenic addition of CO₂ (and methane, and other GHGs) increases IR absorption, pushing the equilibrium temperature higher. The chapter doesn't go into the quantitative climate model; the *mechanism* is straightforward Stefan-Boltzmann with selective absorption.

---

## Worked example: heat loss through a composite wall

A wall in a passive house: outside brick 10 cm + insulation foam 15 cm + interior drywall 1.5 cm. Wall area 25 m². Outside −5°C, inside 20°C. Find the heat loss rate and the temperature at each interface.

**Thermal conductivities:** brick $k_1 = 0.7$ W/(m·K); foam $k_2 = 0.04$; drywall $k_3 = 0.17$. (Approximate.)

**Resistances (per unit area):**
- $r_1 = L_1/k_1 = 0.10/0.7 = 0.143$ m²·K/W
- $r_2 = L_2/k_2 = 0.15/0.04 = 3.75$ m²·K/W
- $r_3 = L_3/k_3 = 0.015/0.17 = 0.088$ m²·K/W
- $r_{\text{total}} = 0.143 + 3.75 + 0.088 = 3.98$ m²·K/W

**Heat flux** (per unit area): $P/A = \Delta T / r_{\text{total}} = (20 - (-5))/3.98 = 6.28$ W/m².

**Total heat loss** through the 25 m² wall: $P = 25 \cdot 6.28 = 157$ W. About 4 kWh per day; modest.

**Interface temperatures.** The temperature drop across each layer is $\Delta T_i = (P/A) \cdot r_i$:
- Across brick: $6.28 \cdot 0.143 = 0.9$ K. From −5°C to −4.1°C.
- Across foam: $6.28 \cdot 3.75 = 23.6$ K. From −4.1°C to 19.5°C. Almost all the temperature drop is across the foam — exactly what good insulation does.
- Across drywall: $6.28 \cdot 0.088 = 0.55$ K. From 19.5°C to 20.0°C.

**The lesson.** In a series thermal circuit, the temperature drop concentrates across the highest-resistance layer. Adding more insulation is the most effective way to reduce heat loss; adding more brick or drywall barely helps.

**The limit.** This calculation assumes one-dimensional steady-state conduction with perfect contact at interfaces. In real walls, thermal bridges (where studs short-circuit the insulation) and air gaps with convection complicate the picture. For typical residential analysis, the simple R-value series gets the order of magnitude right but underestimates real heat loss by 20–50%.

---

## Common misconceptions

**"Warm clothes generate heat."** They don't. Clothes are *thermal insulators* — they reduce the rate of heat loss from your warm body to the cold surroundings. Body heat is the source; the clothes just slow its escape.

**"Dark objects are always hotter in sunlight."** They absorb more visible light *and* radiate more IR (since emissivity is high in both bands for typical "dark" surfaces). At equilibrium, the temperature is determined by the *ratio* of absorbed to emitted power, which depends on the specific spectrum of incident and emitted radiation. Most "dark in visible, light in IR" surfaces (selective absorbers) are engineered specifically for solar thermal collectors.

**"Radiation requires a medium."** Radiation is the only heat transfer mechanism that works in vacuum. The Sun heats the Earth through 150 million km of empty space.

**"Convection requires gravity."** Mostly. Natural convection (buoyancy-driven) requires gravity. But forced convection (pumps, fans) works in zero-g. Astronauts on the ISS still rely on forced convection for cabin heat distribution.

**"Higher temperature means hotter feel."** Approximately, but conductivity matters too. A 200°C aluminum block feels hotter than a 200°C wooden block because aluminum conducts heat to your skin much faster. Same temperature, very different thermal sensation.

---

## Exercises

**Warm-up (Apply).** A 1 m² window with 4 mm glass ($k = 0.8$ W/(m·K)) separates a 22°C room from a 0°C outdoor. Find the heat loss rate.

**Apply.** A composite wall: 12 cm brick ($k = 0.8$) + 10 cm foam ($k = 0.035$) + 1.3 cm drywall ($k = 0.17$). 30 m² area. Outside 5°C, inside 22°C. Find total heat loss rate; find interface temperatures.

**Apply.** A hot coffee (90°C) in a room (20°C) cools by Newton's law of cooling. Convection coefficient $h = 10$ W/(m²·K); cup surface area $A = 0.025$ m²; mass $m = 0.3$ kg; specific heat $c = 4186$ J/(kg·K). (a) Find initial cooling rate. (b) Find $\tau$ (time constant). (c) After how long is the coffee at 60°C?

**Apply.** A human body at 33°C (skin temperature), surface area 1.8 m², emissivity 0.97. (a) Total radiated power in a 20°C room. (b) Net radiation loss. Compare to your typical metabolic rate of about 100 W resting.

**Analyze.** Stefan-Boltzmann: doubling absolute temperature increases emission by what factor? At $T = 6000$ K (Sun surface) vs $T = 300$ K (room temperature), what's the ratio of emitted power per unit area?

**Challenge.** Wien's law application. A star's color tells you its temperature. A blue-white star like Rigel emits peak around 200 nm (UV). What's its surface temperature?

---

## LLM Exercises

### Build the composite wall simulator (`02-heat-conduction.html`)

> **Show.** Fourier's law: $P = kA(T_H - T_C)/L$. Resistance $R = L/(kA)$. Series resistances add.
>
> **Say.** Build an interactive composite-wall thermal conduction simulator.
>
> **Constrain.** D3 v7. Wall cross-section displayed horizontally. Toggle for number of layers (1–4). For each layer: dropdown for material (sets $k$: copper 390, glass 0.8, brick 0.7, wood 0.13, fiberglass 0.04, foam 0.04, aerogel 0.013, air 0.026), slider for thickness $L$. Slider for total wall area $A$. Sliders for $T_H$ (hot side) and $T_C$ (cold side). Display: temperature profile $T(x)$ across the wall as a piecewise-linear curve; heat flux $P$ in watts; thermal resistance per layer and total. Filename: `02-heat-conduction.html`.
>
> **Verify.** (a) A wall of pure copper transmits much more heat than a wall of foam at the same dimensions. (b) Adding foam thickness reduces heat loss. (c) Temperature gradient is steepest across the highest-resistance layer.

### Exploration

- Build a passive-house-grade wall and a typical-residential wall. Compare heat losses.
- Insert a copper layer in series with a foam layer. The copper barely contributes to the total resistance; foam dominates.
- Vary wall area $A$. Heat loss is proportional to area at fixed $\Delta T$.

### Extension prompt (chapter bridge)

> **Show.** I've handled conduction. Now I want to see how radiation works — Stefan-Boltzmann's $T^4$ law and Wien's $\lambda_{\max}T$ relationship.
>
> **Say.** Build a thermal radiation visualizer.
>
> **Constrain.** Slider for temperature (50–10000 K). Display the blackbody spectrum (power per unit wavelength) as a curve, with peak wavelength $\lambda_{\max}$ marked. Display total radiated power and where in the EM spectrum (radio, IR, visible, UV, X-ray) the peak falls.
>
> **Verify.** Sun temperature ~5800 K → peak in visible. Earth ~288 K → peak in mid-IR. Doubling T → 16× total power.

Save as `02b-radiation-preview.html`. Bridge to applications in Chapter 3 and 6.

---

## What would change my mind

The three heat transfer mechanisms — conduction, convection, radiation — have been confirmed empirically at every scale where measurements are possible. The Stefan-Boltzmann law has been verified to extraordinary precision; the value of $\sigma$ is now derived from $h, c, k_B$ in the 2019 SI. A confirmed deviation in any of the three laws at scales where the chapter's assumptions hold (small-temperature-gradients for Newton's law of cooling; non-extreme materials) would force revision. None exists.

## Still puzzling

- *Non-Fourier heat transfer.* At very short time scales (picoseconds) or in nanoscale systems, the Fourier's-law diffusion picture breaks down. Heat propagates more like a wave than a diffusion. Phonon transport in carbon nanotubes and graphene shows this. Not in intro scope but worth knowing exists.
- *Convection at the boundary layer.* The convection coefficient $h$ depends on the flow regime (laminar vs. turbulent). Predicting $h$ from first principles requires fluid mechanics; here we treat it as an empirical input.
- *Wavelength-dependent emissivity.* The chapter treats $\varepsilon$ as a single number, but it varies strongly with wavelength. Selective absorbers (high $\varepsilon$ in visible, low in IR — solar collectors) and selective emitters (low $\varepsilon$ in visible, high in IR — radiative coolers that emit thermal IR to space at night) are engineering frontiers.

---

**Tags:** conduction, Fourier's law, convection, Newton's law of cooling, radiation, Stefan-Boltzmann, Wien's law, R-value, greenhouse effect

