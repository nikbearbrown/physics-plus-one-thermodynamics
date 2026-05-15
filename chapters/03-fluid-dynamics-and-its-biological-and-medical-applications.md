# Chapter 3 — Fluid Dynamics and Its Biological and Medical Applications

**Suggested titles**

1. Fluid Dynamics and Its Biological and Medical Applications
2. Why Faster Flow Has Lower Pressure
3. From Kitchen Tap to Aorta: How Fluids Get From Here to There

**TL;DR.** Once a fluid moves, two new principles take over. The **continuity equation** ($A_1 v_1 = A_2 v_2$) is mass conservation: a fluid speeds up when it enters a narrower channel. **Bernoulli's equation** ($P + \tfrac{1}{2}\rho v^2 + \rho g h = $ const) is energy conservation along a streamline: faster flow means lower pressure. Real fluids also have **viscosity** (internal friction) and can flow either smoothly (**laminar**) or chaotically (**turbulent**), with the **Reynolds number** deciding which. Together, this machinery describes blood flow through arteries, water through pipes, air over a wing, and almost every flowing-fluid problem in engineering and biology.

---

## A blood pressure cuff inflating, every primary care visit

You sit down at the doctor's office. The medical assistant wraps a cuff around your upper arm. The cuff inflates — squeezing your brachial artery shut. She places a stethoscope just below the cuff and slowly releases the pressure. At a certain pressure, she hears the first thumping sound — your **systolic** blood pressure, the peak pressure your heart generates with each beat. As the cuff continues to deflate, the sounds change in character; at the moment they disappear entirely, she records the **diastolic** pressure, the resting pressure between beats. The reading: $120/80 \text{ mmHg}$, or in pascals: $16{,}000 / 10{,}700 \text{ Pa}$.

What's happening physically? Your heart pumps blood through arteries; the arteries narrow and widen; the blood flows in pulses, not continuously. The cuff exploits a fluid-dynamics phenomenon: when the cuff pressure exceeds the artery's interior pressure, the artery is squeezed shut and no blood flows. As cuff pressure drops below the systolic peak, blood starts squirting through during peak heart pressure — and the flow is *turbulent*, producing the audible sound (the "Korotkoff sounds"). When cuff pressure drops below the diastolic minimum, blood flows smoothly all the time, and the turbulent sounds vanish.

Almost every step in this routine is fluid dynamics: the heart's pulsatile pressure, the artery's pressure-volume relationship, the transition from no-flow to turbulent-flow to laminar-flow as cuff pressure changes. The doctor's reading translates to medical decisions about cardiovascular health — but the physics underneath is what makes the measurement work.

This chapter is about fluids in motion: continuity, Bernoulli's equation, viscosity, turbulence, and the way these ideas apply to engineering pipelines and biological circulations alike. By the end, you should be able to compute flow rates, predict pressure drops in pipes and arteries, distinguish laminar from turbulent flow, and recognize where fluid dynamics underlies the medical and biological systems you take for granted.

**Learning objectives.** By the end of this chapter you should be able to:

1. Apply the continuity equation $A_1 v_1 = A_2 v_2$ for incompressible fluid in a tube of varying cross-section.
2. Apply Bernoulli's equation $P + \tfrac{1}{2}\rho v^2 + \rho g h = $ const along a streamline to relate pressure, speed, and height.
3. Compute viscous flow in pipes using Poiseuille's law and identify when it applies (laminar regime).
4. Compute the Reynolds number $\text{Re} = \rho v L / \eta$ and predict whether flow is laminar or turbulent.
5. Apply fluid dynamics to biomedical situations: blood flow, cardiac output, breathing, fluid loss / replacement.

**Prerequisites.** Chapter 7 (energy conservation — Bernoulli is energy conservation for fluids). Chapter 11 (pressure, density, fluid statics).

**Why this chapter matters.** Every flowing fluid system in nature and engineering uses this physics: the human cardiovascular system, the lungs, plant transpiration, water and gas pipelines, hydraulic turbines, airfoils, ship hulls, weather, ocean currents, glaciers. Many medical interventions (IV drips, catheters, dialysis, nebulizers, blood-pressure measurement) are direct applications. Many medical pathologies (heart attacks, aneurysms, atherosclerosis) are fluid-dynamic events.

---

## Concept 1 — Flow rate and continuity

### Pinching the end of a garden hose

You're watering the garden. The hose is open and water flows out at a leisurely speed. You pinch the end of the hose, narrowing the opening. The water shoots out faster — fast enough to spray several meters further. Same hose, same source, same total flow rate per second. What changed?

The cross-sectional area where the water exits got smaller. By **mass conservation**, the same amount of water has to come through a smaller opening per second — so it moves faster. This is the **continuity equation**:

$$A_1 v_1 = A_2 v_2,$$

where $A$ is the cross-sectional area and $v$ is the speed. The product $Av$ is constant along a flow tube.

### The mechanism — flow rate, continuity, and incompressibility

**Flow rate** $Q$ is defined as the volume of fluid passing a given cross-section per unit time:

$$Q = \frac{V}{t} = A v.$$

Units: $\text{m}^3/\text{s}$.

For an incompressible fluid (good approximation for liquids; sometimes for slow-moving gases) flowing through a tube whose cross-section varies, mass conservation requires:

$$Q = A_1 v_1 = A_2 v_2 = \text{constant}.$$

So if a pipe narrows by a factor of 4 in cross-sectional area, the flow speeds up by a factor of 4. If it widens by a factor of 9, the flow slows by a factor of 9.

This is why a river runs faster through a narrow gorge than over a wide plain. It's why blood flows fastest through narrowed (constricted) arteries and capillaries — the cross-section is smaller, even though arteries are individually narrower. It's why water sprays farther when you pinch the hose.

For the circulatory system: aorta cross-section is $\sim 4 \text{ cm}^2$; total cross-section of all capillaries combined is $\sim 4{,}500 \text{ cm}^2$. So blood flow speed in the aorta is $\sim 1{,}000 \times$ faster than in capillaries — about $30 \text{ cm/s}$ in the aorta, $0.03 \text{ cm/s}$ in capillaries. The slower flow in capillaries is exactly what's needed for gas and nutrient exchange.

### The trade-off

The continuity equation trades **a true 3D flow analysis** for **a 1D area-vs-speed picture along a streamline**. It assumes incompressible fluid, steady flow (not changing in time), and a single flow tube (no branching for the simple form). The cost: it doesn't capture turbulence or compressibility. The benefit: a single equation gives you the speed-area relationship for any pipe-like geometry.

### Worked example — water through a Venturi meter

A Venturi meter (a tube that narrows in the middle for measuring flow) has cross-section $A_1 = 4.0 \text{ cm}^2$ in the wide section and $A_2 = 1.0 \text{ cm}^2$ in the narrow section. Water flows through at $0.50 \text{ m/s}$ in the wide section. (a) What is the speed in the narrow section? (b) What is the volume flow rate?

**(a) Continuity.**

$$A_1 v_1 = A_2 v_2 \implies v_2 = v_1 \frac{A_1}{A_2} = 0.50 \times \frac{4.0}{1.0} = 2.0 \text{ m/s}.$$

The water moves $4\times$ faster in the narrow section.

**(b) Volume flow rate.**

$$Q = A_1 v_1 = (4.0 \times 10^{-4} \text{ m}^2)(0.50 \text{ m/s}) = 2.0 \times 10^{-4} \text{ m}^3/\text{s} = 0.20 \text{ L/s}.$$

About 200 mL per second — comparable to a kitchen faucet.

**Sanity check.** The flow rate should be the same in both sections (mass conservation). Compute also in the narrow section: $Q = A_2 v_2 = (1.0 \times 10^{-4})(2.0) = 2.0 \times 10^{-4} \text{ m}^3/\text{s}$ ✓.

### Common misconceptions

- *"Mass flow rate and volume flow rate are the same."* Only for incompressible fluids. For gases (compressible), mass flow rate $\dot{m} = \rho A v$ is what's conserved, while $Q = Av$ varies.
- *"Faster flow means more flow."* Not necessarily. If the area shrinks by a factor of 4 while speed quadruples, total flow rate (volume per second) is the same.

↳ **Dig Deeper — The continuity equation in branching networks (cardiovascular system)**

*The simple continuity equation $Av =$ const works for a single tube. The cardiovascular system branches: the aorta splits into many arteries, then arterioles, then capillaries. The total cross-sectional area increases as you go to smaller vessels, but each individual vessel is smaller. The right form of continuity sums over all parallel branches.*

**Prompt:**
> Walk through how continuity applies to a branching network like the human cardiovascular system. Compute (a) blood velocity in the aorta given a cardiac output of $5 \text{ L/min}$ and aortic cross-section $4 \text{ cm}^2$, (b) average blood velocity in the capillary bed given total capillary cross-section $\sim 4{,}500 \text{ cm}^2$, (c) the ratio. End with one sentence on why the slow capillary velocity is biologically essential (gas and nutrient exchange takes time).

**What to do with the output:** Save it. The branching-continuity insight clarifies why slow capillary flow isn't a design flaw but an essential feature.

---

## Concept 2 — Bernoulli's equation: energy conservation for fluids

### A bath drain creating a vortex

Pull the plug from a bathtub full of water. As the water drains, you see a vortex form above the drain — a swirling depression where the water level dips. The dipping happens because in the vortex, water is moving fast, and Bernoulli's principle says fast-moving fluid has *lower pressure*. The lower pressure in the vortex is what pulls water upward (or, equivalently, lets the surface dip below the surrounding level).

This is one of the two big consequences of fluid energy conservation. Fast flow → low pressure. Slow flow → high pressure. And the connection isn't qualitative — it's quantitative.

### The mechanism — Bernoulli's equation

For an incompressible, steady, frictionless flow along a streamline:

$$P + \tfrac{1}{2}\rho v^2 + \rho g h = \text{constant}.$$

This is **Bernoulli's equation**. Three terms:

- $P$: pressure (the static pressure at the point in the flow).
- $\tfrac{1}{2}\rho v^2$: kinetic energy per unit volume (dynamic pressure).
- $\rho g h$: gravitational potential energy per unit volume.

Their sum is constant along a streamline. The equation is essentially energy conservation per unit volume of fluid: the work done by pressure plus the kinetic energy plus the gravitational potential energy equals a constant.

Several immediate consequences:

**Bernoulli's principle:** if $h$ is constant, $P$ and $v$ trade off — faster flow has lower pressure. This is the lift on an airplane wing (faster flow over the curved top creates lower pressure, net upward force), the spin of a baseball (Magnus effect — different speeds on opposite sides create pressure differences), the function of a Venturi meter (measuring flow rate from a pressure drop).

**Torricelli's theorem:** for water flowing out of a hole at depth $h$ below an open reservoir surface, the speed is $v = \sqrt{2gh}$ — the same as a free-falling object that fell a height $h$. (Apply Bernoulli with $P_{\text{surface}} = P_{\text{outlet}} = $ atmospheric, $v_{\text{surface}} \approx 0$.)

### The trade-off

Bernoulli's equation trades **a fully detailed velocity field** for **a single along-streamline relationship**. It assumes incompressible, steady, frictionless (no viscosity), and along a single streamline. Real flows often violate these (compressibility for fast gas, unsteadiness for pulsating flow, friction for any real fluid). When the assumptions hold, Bernoulli is exact. When they fail, it's a useful approximation.

### Worked example — water shooting from a fire hose

Water flows from a fire-hose nozzle at $20 \text{ m/s}$ horizontally. The hose's interior pressure (just upstream of the nozzle) is $2.0 \times 10^5 \text{ Pa}$ above atmospheric. (a) If the hose has cross-section $20 \text{ cm}^2$ and the nozzle has cross-section $5.0 \text{ cm}^2$, what is the water speed inside the hose? (b) Verify Bernoulli's equation between the hose and the nozzle outlet (where pressure equals atmospheric).

**(a) Continuity.** $A_h v_h = A_n v_n \implies v_h = (5.0/20)(20) = 5.0 \text{ m/s}$.

**(b) Bernoulli.** Take both points at the same height. Inside hose: $P_h = 2.0 \times 10^5 + P_{\text{atm}}$, $v_h = 5.0 \text{ m/s}$. Nozzle outlet: $P_n = P_{\text{atm}}$, $v_n = 20 \text{ m/s}$.

LHS (hose): $P_h + \tfrac{1}{2}\rho v_h^2 = (P_{\text{atm}} + 2.0 \times 10^5) + \tfrac{1}{2}(1000)(5.0)^2 = (P_{\text{atm}} + 2.0 \times 10^5) + 12{,}500$.

RHS (nozzle): $P_{\text{atm}} + \tfrac{1}{2}(1000)(20)^2 = P_{\text{atm}} + 200{,}000$.

So Bernoulli requires: $P_{\text{atm}} + 2.0 \times 10^5 + 12{,}500 = P_{\text{atm}} + 200{,}000 \implies 212{,}500 = 200{,}000$. Close but not exact — the discrepancy ($12{,}500 \text{ Pa}$, about $6\%$) reflects friction in the hose, which Bernoulli's idealization ignores.

**Sanity check.** A high-pressure water source (the hose interior pressure of $\sim 2 \text{ atm}$ above atmospheric) accelerating water through a nozzle from $5$ to $20 \text{ m/s}$ is exactly the principle of fire hoses, sprinkler systems, and many other high-velocity water applications. Bernoulli explains why narrow nozzles produce fast jets.

### Common misconceptions

- *"Bernoulli applies everywhere in a fluid."* Only along a streamline (a single path of fluid flow). Different streamlines can have different constants.
- *"Bernoulli proves airplanes fly."* Only partly. Bernoulli explains pressure-speed correlation, but airplane lift involves additional effects (downwash from wing, momentum change of air mass). The full story requires fluid dynamics beyond Bernoulli alone.

↳ **Dig Deeper — Bernoulli, momentum, and how airplane wings actually generate lift**

*The popular textbook explanation of airplane lift via Bernoulli's principle (faster flow over curved upper surface → lower pressure → lift) is technically true but misleading — the equal-transit-time argument it usually relies on is wrong. The complete picture combines Bernoulli with Newton's third law (the wing redirects air downward; air pushes wing upward).*

**Prompt:**
> Critically examine the textbook "Bernoulli explanation" of airplane lift. (a) State the equal-transit-time argument and explain why it's empirically wrong. (b) Give the more complete picture combining Bernoulli's principle with momentum-flux arguments (Newton's third law: wing pushes air down, air pushes wing up). (c) End with the modern view that lift = pressure difference (true) AND lift = downward momentum imparted to air per second (also true) — they're complementary descriptions of the same physics.

**What to do with the output:** Save it. The lift-explanation question is one of the most-discussed examples of how popular physics oversimplifies; the correct picture is more interesting than the textbook story.

---

## Concept 3 — Viscosity, laminar vs. turbulent, Reynolds number

### Honey vs. water from a pitcher

Pour water from a pitcher. The water falls in a smooth column, splashes into the cup, and you're done in a second. Pour honey from a pitcher. The honey falls slowly, in a thick column that may break into elongated globs, takes seconds to even begin filling the cup.

The difference is **viscosity** — internal friction within a fluid. Water has low viscosity; honey has high viscosity. Both are fluids; both flow under gravity. But the rate of flow differs by orders of magnitude because of how easily the molecules slide past one another.

Real fluids have viscosity. The frictionless idealization in Bernoulli's equation is convenient but rarely exactly true. For pipe flow, syrup vs. water, blood vs. air, viscosity matters.

### The mechanism — viscosity, Poiseuille's law, Reynolds number

**Viscosity** $\eta$ has units of $\text{Pa} \cdot \text{s}$. Some values:

- Water at $20°\text{C}$: $\eta \approx 10^{-3} \text{ Pa}\cdot\text{s}$.
- Air at $20°\text{C}$: $\eta \approx 1.8 \times 10^{-5} \text{ Pa}\cdot\text{s}$.
- Blood: $\eta \approx 3 \times 10^{-3} \text{ to } 4 \times 10^{-3} \text{ Pa}\cdot\text{s}$ (about 3–4× water).
- Honey: $\eta \approx 10 \text{ Pa}\cdot\text{s}$ (about $10{,}000$× water).

**Poiseuille's law:** for incompressible, steady, *laminar* flow through a pipe of radius $r$ and length $L$, with pressure drop $\Delta P$ across the length:

$$Q = \frac{\pi r^4 \Delta P}{8 \eta L}.$$

Flow rate scales as $r^4$. Doubling pipe radius increases flow rate $16\times$ for the same pressure drop. Halving radius (e.g., partial atherosclerotic blockage of an artery) reduces flow rate $16\times$, requiring much greater pressure to maintain the same volume per second. This explains why even modest atherosclerotic narrowing leads to disproportionate cardiovascular strain.

**Laminar vs. turbulent flow.** Laminar flow is smooth, with fluid layers sliding past one another. Turbulent flow is chaotic, with eddies and vortices. The transition between them is governed by the **Reynolds number**:

$$\text{Re} = \frac{\rho v L}{\eta},$$

where $\rho$ is fluid density, $v$ is characteristic flow speed, $L$ is a characteristic length (e.g., pipe diameter), and $\eta$ is viscosity.

For pipe flow:
- Re $< 2{,}000$: laminar (smooth).
- Re $\sim 2{,}000$–$3{,}000$: transitional (oscillates).
- Re $> 3{,}000$: turbulent (chaotic).

A swimming-pool-sized turbulent flow and a teacup-sized laminar flow can be the same Reynolds number — it's the dimensionless ratio that matters.

### The trade-off

Viscous flow analysis trades **simple Bernoulli** for **more complex equations involving the fluid's viscosity**. Real-flow problems (blood through a stenosed artery, oil in a pipeline, air around a car) typically need viscosity. The cost is added complexity; the benefit is realistic predictions.

### Worked example — blood flow through a healthy artery

A healthy artery has radius $r = 2.0 \text{ mm} = 2.0 \times 10^{-3} \text{ m}$ and length $L = 0.10 \text{ m}$. Blood flows through it with pressure drop $\Delta P = 100 \text{ Pa}$. Blood viscosity $\eta = 4 \times 10^{-3} \text{ Pa}\cdot\text{s}$. (a) What is the flow rate? (b) What is the average flow speed? (c) What is the Reynolds number?

**(a) Poiseuille.**

$$Q = \frac{\pi (2.0 \times 10^{-3})^4 (100)}{8 (4 \times 10^{-3})(0.10)} = \frac{\pi (1.6 \times 10^{-11})(100)}{3.2 \times 10^{-3}} = \frac{5.03 \times 10^{-9}}{3.2 \times 10^{-3}} \approx 1.57 \times 10^{-6} \text{ m}^3/\text{s}.$$

About $1.6 \text{ mL/s}$, or $94 \text{ mL/min}$. For one segment of one artery — total cardiac output ($\sim 5 \text{ L/min}$) is the sum across many such segments.

**(b) Average speed.** $Q = \pi r^2 v_{\text{avg}}$:

$$v_{\text{avg}} = \frac{Q}{\pi r^2} = \frac{1.57 \times 10^{-6}}{\pi (2.0 \times 10^{-3})^2} \approx 0.125 \text{ m/s}.$$

About $13 \text{ cm/s}$ — typical mid-artery flow speed.

**(c) Reynolds number.** Density of blood $\rho \approx 1{,}060 \text{ kg/m}^3$. Diameter $L = 4.0 \times 10^{-3} \text{ m}$.

$$\text{Re} = \frac{\rho v L}{\eta} = \frac{(1060)(0.125)(4.0 \times 10^{-3})}{4 \times 10^{-3}} \approx 132.$$

Re $\sim 130$, well below the laminar/turbulent transition. Flow is laminar — Poiseuille's law applies. (At an arterial constriction, Re can rise into the turbulent regime, producing the bruit sounds that physicians listen for with a stethoscope.)

**Sanity check.** Healthy peripheral artery flow is indeed laminar in most circumstances. At narrowed sites or at junctions, Re increases and turbulence can occur — exactly what produces audible sounds in the blood-pressure measurement (Korotkoff sounds at certain cuff pressures).

### Common misconceptions

- *"Reynolds number tells you the velocity."* No — it's a dimensionless ratio of inertial to viscous forces. Two systems with very different velocities can have the same Re if their other parameters compensate.
- *"Turbulent always means worse."* Sometimes turbulent flow is desirable (better mixing, heat transfer); sometimes it's a problem (drag, energy loss, cavitation). Whether you want laminar or turbulent depends on the application.

↳ **Dig Deeper — Why Poiseuille's flow scales as $r^4$ (the implications for medicine)**

*The fact that flow scales as the fourth power of pipe radius has dramatic consequences in cardiovascular medicine. A modest narrowing of an artery (say, 30% reduction in radius) reduces flow by a factor of $\sim (0.7)^4 \approx 0.24$ — a 76% reduction in flow for the same pressure drop. Maintaining flow requires either more pressure (work for the heart) or compensatory dilation elsewhere.*

**Prompt:**
> Explain why Poiseuille's law gives flow rate proportional to $r^4$ rather than $r^2$ (which is what cross-sectional area scaling would suggest). Walk through the physics: (a) cross-section grows as $r^2$; (b) the velocity profile in laminar flow is parabolic, with maximum at the center; (c) integrating the parabolic velocity over the cross-section gives an additional $r^2$. Then explain the medical implication: a 30% radius reduction in a coronary artery (atherosclerosis) reduces flow capacity by what factor? End with one sentence on why this is why even mild atherosclerosis is medically significant.

**What to do with the output:** Save it. The $r^4$ scaling is one of the most consequential results in cardiovascular physiology and explains the asymmetric severity of arterial narrowing.

---

## Synthesis — fluid dynamics from kitchen tap to bloodstream

Step back. Three concepts:

**Continuity** ($A_1 v_1 = A_2 v_2$): mass conservation. Smaller cross-section → faster flow.

**Bernoulli** ($P + \tfrac{1}{2}\rho v^2 + \rho g h = $ const along a streamline): energy conservation. Faster flow → lower pressure (at constant height).

**Viscosity, Poiseuille, Reynolds** ($Q = \pi r^4 \Delta P / (8\eta L)$, Re $= \rho v L / \eta$): real fluids have internal friction; flow is laminar or turbulent depending on Re.

The **scale shift**: from a kitchen faucet ($r \sim 1 \text{ cm}$, $v \sim 1 \text{ m/s}$, Re $\sim 10^4$ — turbulent) to blood through capillaries ($r \sim 5 \text{ μm}$, $v \sim 0.001 \text{ m/s}$, Re $\sim 10^{-3}$ — laminar) to a 747 jet engine intake (Re $\sim 10^7$ — fully turbulent). The same equations apply. Re tells you the regime.

### A worked example using all three concepts — water through a kitchen sink to drain

Water flows from a kitchen tap at $0.5 \text{ L/s}$ ($5 \times 10^{-4} \text{ m}^3/\text{s}$). The tap outlet has radius $r_t = 1.0 \text{ cm}$. The drain pipe is $r_d = 2.5 \text{ cm}$ and runs $1.5 \text{ m}$ down to the trap. (a) Speed at tap outlet? (b) Speed in drain pipe? (c) Pressure in drain pipe vs. in air, ignoring viscosity? (d) Reynolds number in drain pipe.

**(a) Continuity at tap outlet.** $Q = \pi r_t^2 v_t \implies v_t = Q/(\pi r_t^2) = 5 \times 10^{-4}/(\pi \times 10^{-4}) \approx 1.6 \text{ m/s}$.

**(b) Continuity in drain.** $v_d = Q/(\pi r_d^2) = 5 \times 10^{-4}/(\pi \times 6.25 \times 10^{-4}) \approx 0.25 \text{ m/s}$.

**(c) Bernoulli, tap outlet to drain pipe entry, taking both at same height** (~kitchen counter level): $P_t + \tfrac{1}{2}\rho v_t^2 = P_d + \tfrac{1}{2}\rho v_d^2$. Tap outlet at atmospheric: $P_t = P_{\text{atm}}$. So:

$$P_d = P_{\text{atm}} + \tfrac{1}{2}(1000)(1.6^2 - 0.25^2) = P_{\text{atm}} + \tfrac{1}{2}(1000)(2.56 - 0.0625) = P_{\text{atm}} + 1{,}249 \text{ Pa}.$$

The drain pipe (just past the entry) is at slightly higher pressure than atmospheric — about $1.2 \text{ kPa}$ above. This is small (about $1\%$ of atmospheric).

**(d) Reynolds number in drain.** Pipe diameter $L = 5 \text{ cm} = 0.05 \text{ m}$, water $\rho = 10^3 \text{ kg/m}^3$, $\eta = 10^{-3} \text{ Pa}\cdot\text{s}$.

$$\text{Re} = \frac{(1000)(0.25)(0.05)}{10^{-3}} = 12{,}500.$$

Re $\sim 10^4$, well above $3{,}000$. The flow in the drain is **turbulent**. (Pipe drains are typically turbulent; that's why you hear gurgling.)

The synthesis exercises all three concepts: continuity to find speeds in the variable-cross-section system; Bernoulli to relate pressure to speed; Reynolds to identify the flow regime. Everyday plumbing is fluid dynamics in action.

---

## Exercises

### Warm-up

**12.1** *(LO 1)* Water flows through a $5.0 \text{ cm}$ diameter pipe at $2.0 \text{ m/s}$. (a) Cross-sectional area? (b) Volume flow rate in $\text{m}^3/\text{s}$ and L/min?

**12.2** *(LO 1)* A river $50 \text{ m}$ wide and $2.0 \text{ m}$ deep on average flows at $0.50 \text{ m/s}$. What is its volume flow rate?

**12.3** *(LO 2)* Water flows horizontally through a pipe at $3.0 \text{ m/s}$ at gauge pressure $50 \text{ kPa}$. The pipe narrows so that the speed becomes $9.0 \text{ m/s}$. What is the new gauge pressure?

**12.4** *(LO 4)* Water at $20°\text{C}$ flows through a $1.0 \text{ cm}$ diameter pipe at $0.50 \text{ m/s}$. Compute Re. Is flow laminar or turbulent?

### Application

**12.5** *(LO 1, 2)* Water emerges from a hole at depth $3.0 \text{ m}$ below the surface of a large reservoir. (a) Use Torricelli's theorem ($v = \sqrt{2gh}$) to find the exit speed. (b) If the hole has area $5.0 \text{ cm}^2$, what is the volume flow rate?

**12.6** *(LO 3)* Compute the volume flow rate through a horizontal cylindrical pipe with radius $1.0 \text{ cm}$, length $5.0 \text{ m}$, viscosity $\eta = 10^{-3} \text{ Pa}\cdot\text{s}$, with pressure drop $200 \text{ Pa}$ across the length.

**12.7** *(LO 5)* Cardiac output is about $5 \text{ L/min}$. Aortic radius is about $1.0 \text{ cm}$. (a) Compute average blood velocity in the aorta. (b) Reynolds number ($\rho_{\text{blood}} = 1{,}060$, $\eta = 4 \times 10^{-3}$). Laminar or turbulent under healthy conditions?

**12.8** *(LO 2)* An airplane wing produces lift in part because of pressure difference between top and bottom surfaces. If the speed of air over the top is $100 \text{ m/s}$ and underneath is $80 \text{ m/s}$ (air density $1.21 \text{ kg/m}^3$), what is the pressure difference?

### Synthesis

**12.9** *(LO 1, 2, 3)* A garden hose has $1.5 \text{ cm}$ inner diameter and water flows through at $5 \text{ L/min}$. The hose is $20 \text{ m}$ long and the supply pressure is $250 \text{ kPa}$ above atmospheric. (a) Speed in hose? (b) Bernoulli pressure drop from speed alone? (c) Poiseuille pressure drop from viscosity? (d) Comment on which dominates.

**12.10** *(LO 3, 5)* An atherosclerotic narrowing reduces an artery's radius by $25\%$ ($r_{\text{new}} = 0.75 r_{\text{old}}$). (a) By what factor does flow rate decrease (at the same pressure)? (b) By what factor must pressure increase to maintain the same flow rate?

**12.11** *(LO 4)* A swim at $1 \text{ m/s}$ involves a body of characteristic length $1.5 \text{ m}$ moving through water. Compute Re. Is flow around the swimmer laminar or turbulent?

### Challenge

**12.12** *(LO 5, beyond chapter)* A patient has an aortic stenosis (narrowing) reducing the aortic valve cross-section to $1/4$ of normal. Cardiac output remains $5 \text{ L/min}$. (a) Velocity through the stenosed valve? (b) Reynolds number? Is flow turbulent? (c) Pressure drop across the stenosis (use Bernoulli, ignoring viscosity)? Express in mmHg.

**12.13** *(beyond chapter)* For a bacterium of radius $1 \text{ μm}$ swimming through water at $30 \text{ μm/s}$, compute the Reynolds number. Comment: the bacterium lives in a regime where viscous forces dominate inertial forces. What does this mean for how it must swim (hint: it can't coast)?

---

## LLM Exercise — Chapter 12: Fluid Dynamics in Your Anchor Phenomenon

**Project:** Physics Reality Check Logbook
**What you're building this chapter:** A flow-rate, pressure, or Reynolds-number analysis of one moving fluid in your anchor phenomenon.
**Tool:** Claude Project.

### The Prompt

```
I'm continuing my Physics Reality Check Logbook for College Physics with LLMs. My anchor phenomenon is [paste 1-sentence description].

For Chapter 12, I want to apply fluid dynamics — continuity, Bernoulli, viscosity — to one flowing fluid in my phenomenon. Please:

1. Identify ONE moving fluid in my phenomenon. Examples:
   - Bike commute: air flowing around the body at riding speed (drag); blood flow in the rider during exertion.
   - Coffee maker: water flowing through coffee grounds during brewing; steam through wand.
   - Basketball: airflow around the spinning ball (Magnus effect).
   - Marathon: airflow around the runner; sweat evaporation.
   - Espresso: water at 9 bar through the coffee puck during extraction (this is the central flow event).

2. Identify the relevant equation: continuity ($Av = $const), Bernoulli ($P + \tfrac{1}{2}\rho v^2 + \rho g h$), or Poiseuille ($Q = \pi r^4 \Delta P / 8\eta L$).

3. Compute the relevant quantities. Report with units, sig figs, uncertainty.

4. Compute the Reynolds number to determine flow regime (laminar, turbulent, transitional).

5. Sanity check with one Fermi estimate.

6. Identify which assumption (incompressible, frictionless, steady-state, ignored viscosity) is most likely to bite.

7. One sentence on how this connects to Chapter 13 (gas laws) — flowing gases involve compressibility that liquids don't.

Save the output as logbook/chapter-12-fluid-dynamics.md.
```

### What this produces

A twelfth Logbook entry: a fluid-flow analysis of one moving fluid in your phenomenon, often revealing the regime (laminar vs. turbulent) governs which equations apply.

### How to adapt this prompt

- *For phenomena with mostly slow flow* (a coffee drip): use Stokes / low-Re analysis.
- *For phenomena with high-speed flow* (a basketball through air): apply turbulent drag from Ch. 5.
- *For ChatGPT or Gemini:* identical with substitutions.
- *For Claude Code:* if you have flow data (water-meter readings, blood-pressure log), paste it.

### Connection to previous chapters

Builds directly on Chapter 11 (pressure, density, fluid statics). Builds on Chapter 7 (Bernoulli is energy conservation for fluids). Builds on Chapter 5 (drag in fluids — Reynolds number connects).

### Preview of next chapter

Chapter 13 introduces temperature and the kinetic theory of gases. Gases differ from liquids in that they are compressible, and their behavior is described by the ideal gas law $PV = nRT$. Many fluid-dynamic phenomena in gases (lift, sound, weather) involve both fluid dynamics and gas-law thermodynamics together.

---

## Chapter summary

Three big results. **Continuity** ($A_1 v_1 = A_2 v_2$) is mass conservation: incompressible fluids speed up in narrower channels. **Bernoulli** ($P + \tfrac{1}{2}\rho v^2 + \rho g h = $ const) is energy conservation along a streamline: faster flow has lower pressure. **Viscosity, Poiseuille, Reynolds**: real fluids have internal friction; whether flow is laminar or turbulent depends on the dimensionless Re.

The one idea that matters most: **Bernoulli is just energy conservation per unit volume.** Once you internalize that the three terms are pressure-energy, kinetic-energy, and gravitational-energy densities, the equation isn't surprising — it's the energy ledger for a fluid parcel along its path.

The common mistake to watch for: **applying Bernoulli where viscosity matters.** For long pipes, narrow capillaries, or any high-Re turbulent flow, the frictionless idealization fails. Use Poiseuille for laminar pipe flow; use empirical methods for turbulent flow in pipes; use computational fluid dynamics for complex geometries.

What you should now be able to teach someone else: how to apply continuity to find speed in a pipe of varying cross-section, how to apply Bernoulli to relate pressure and velocity along a streamline, how to compute Reynolds number to predict flow regime, and how Poiseuille's $r^4$ scaling explains the medical significance of arterial narrowing. Four skills, three underlying conservation laws.

---

## What would change my mind

The chapter argues that Bernoulli's equation is a clean and sufficient idealization for many fluid-flow situations, with corrections (Poiseuille, Reynolds-based turbulence models) handling viscous and turbulent regimes. The argument would need revision if a class of common fluid-flow problems systematically required corrections beyond viscosity (e.g., for non-Newtonian fluids like blood at very low shear rates, or for compressible flows near the speed of sound). Both are well-handled by extended fluid dynamics, beyond the scope here.

## Still puzzling

The deepest puzzle this chapter raises and does not resolve: **what causes the laminar-to-turbulent transition?** The Reynolds-number criterion is empirical — Re $\sim 2{,}300$ is the rough threshold for pipe flow. The deeper question of why and how flows transition (and what triggers the chaotic instability) is one of the hardest open problems in classical physics. Turbulence is, in some senses, the last great unsolved problem of classical mechanics.

---

## Connections forward

Chapter 13 introduces the kinetic theory of gases and the ideal gas law. Gases are compressible and their behavior couples directly to temperature. Chapters 14–15 (heat, thermodynamics) treat the energy and entropy aspects of fluid systems. Chapter 16 (oscillations and waves) treats sound — pressure waves in fluids — using fluid-dynamic principles. The cardiovascular system continues to make appearances: Chapter 21 (electricity) connects to nerve signals controlling the heart. Chapter 31 (medical physics applications) builds on the fluid foundation.

---

**Tags:** fluid-dynamics, Bernoulli, continuity, Poiseuille, Reynolds-number

---

## AI Wayback Machine

**Daniel Bernoulli** published *Hydrodynamica* in 1738 — establishing the relationship between fluid velocity and pressure that bears his name. The principle now explains airplane lift, carburetors, and arterial blood flow.

**Run this:**

```
Who was Daniel Bernoulli, and how does Bernoulli's equation connect to fluid dynamics we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about his career or ideas.
```

→ Search **"Daniel Bernoulli"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to walk through how Bernoulli's principle accounts for lift on an airfoil — and what the common popular explanation gets wrong.
- Ask it about the famous Bernoulli family of mathematicians and the bitter rivalries among them.

What changes? What gets better? What gets worse?
