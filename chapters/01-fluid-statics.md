# Chapter 1 — Fluid Statics

**Suggested titles**

1. Fluid Statics
2. Why a Steel Ship Floats and a Stone Sinks
3. Pressure as the Fluid's Way of Being a Force

**TL;DR.** A fluid (liquid or gas) doesn't push back along a single direction the way a solid does — it pushes equally in every direction at every point. That equal-in-every-direction quantity is **pressure**, $P = F/A$. This chapter installs pressure, the depth-pressure relation $P = \rho g h$, Pascal's principle (pressure applied to an enclosed fluid is transmitted everywhere), Archimedes' principle (buoyant force equals weight of displaced fluid), and the molecular forces (cohesion, adhesion, surface tension) that govern menisci and capillary action. Together: how fluids at rest behave, why ships float, and how a hydraulic jack lifts a car.

---

## A submersible at the bottom of the Mariana Trench, 2019

Victor Vescovo, in a custom-built submersible called the *Limiting Factor*, descends $10{,}928 \text{ m}$ to the bottom of the Challenger Deep — the deepest point in the Mariana Trench, the deepest place on Earth. The descent takes about four hours. The crushing depth means the pressure outside the submersible is roughly $1{,}100$ times atmospheric — about $110 \text{ MPa}$, or $16{,}000 \text{ pounds per square inch}$.

To survive that pressure, the *Limiting Factor*'s crew sphere is a $9 \text{ cm}$ thick titanium shell, machined to exquisite precision. Even at full depth, with the entire weight of the Pacific Ocean pressing in, the sphere deforms by only a few millimeters. Every square inch of the sphere's surface is being squeezed by the equivalent of ten compact cars stacked on top of it.

How do we know the pressure? We didn't measure it directly with a gauge that can tolerate $110 \text{ MPa}$. We computed it. From the depth, $h$, and the density of seawater, $\rho \approx 1{,}030 \text{ kg/m}^3$, the formula $P = \rho g h$ gives:

$$P = 1030 \times 9.80 \times 10928 \approx 1.10 \times 10^8 \text{ Pa}.$$

That's $110 \text{ MPa}$, exactly. The depth-pressure relation, derived from nothing more than weighing a column of water above a point and dividing by area, predicts the crushing force the submersible's titanium must resist — and engineering teams used that formula to design the sphere thick enough to survive.

This chapter is about how fluids at rest exert pressure, why that pressure depends on depth, why something floats or sinks (Archimedes had this, in the bath, in 250 BC), and how the molecular forces between fluid molecules give rise to phenomena like menisci, capillary rise, and surface tension. The Mariana Trench example is one extreme; an ice cube floating in a glass of water is the everyday other end. Both are governed by the same machinery.

**Learning objectives.** By the end of this chapter you should be able to:

1. Compute density $\rho = m/V$ for any substance and apply density tables to identify materials.
2. Compute pressure $P = F/A$ in any context, and convert between Pa, atm, mmHg, and psi.
3. Apply $P = \rho g h$ to find pressure at depth in a static fluid; combine atmospheric pressure for total absolute pressure.
4. Apply Pascal's principle to hydraulic systems (compute the force amplification of a hydraulic jack).
5. Apply Archimedes' principle to predict buoyant force, sinking/floating, and the apparent weight of submerged or partially submerged objects.

**Prerequisites.** Chapter 4 (force, pressure as force-per-area). Chapter 7 (energy, occasionally useful). Chapter 9 (force balance, statics).

**Why this chapter matters.** Fluid statics underlies hydraulic engineering (cranes, brakes, lifts), naval architecture (every ship), ocean and atmospheric science (pressure with depth and altitude), medicine (blood pressure, intraocular pressure, breathing), and meteorology. The same physics that explains why a $10{,}928 \text{ m}$ descent produces $110 \text{ MPa}$ explains why your ears pop in an airplane and why the surface tension of water lets some insects walk on it.

---

## Concept 1 — Density and pressure

### A ton of feathers, a ton of bricks

The riddle is so old it's a cliche, but it points at a real distinction. A ton of feathers and a ton of bricks weigh the same — but the feathers occupy a much larger volume. The bricks have higher *density*: more mass packed into less space.

**Density** is mass per unit volume:

$$\rho = \frac{m}{V}.$$

Units: $\text{kg/m}^3$. Symbol: Greek letter rho. Some standard values to know:

- Water (fresh, $4°\text{C}$): $1{,}000 \text{ kg/m}^3$.
- Seawater: $\sim 1{,}030 \text{ kg/m}^3$.
- Air (sea level, $20°\text{C}$): $1.21 \text{ kg/m}^3$.
- Aluminum: $2{,}700 \text{ kg/m}^3$.
- Iron / steel: $\sim 7{,}800 \text{ kg/m}^3$.
- Lead: $11{,}300 \text{ kg/m}^3$.
- Mercury: $13{,}600 \text{ kg/m}^3$.
- Gold: $19{,}300 \text{ kg/m}^3$.

The factor-of-a-thousand difference between water and air, and the further factor of nearly $20$ between water and gold, sets up almost everything in fluid statics: floating, sinking, buoyancy.

### Pressure: force per unit area

When a force is distributed across a surface, pressure measures how concentrated that force is:

$$P = \frac{F}{A}.$$

Units: Pa (pascal) $= 1 \text{ N/m}^2$. Other common units:
- $1 \text{ atm} = 101{,}325 \text{ Pa} \approx 10^5 \text{ Pa}$ (atmospheric pressure at sea level).
- $1 \text{ psi} \approx 6{,}895 \text{ Pa}$.
- $1 \text{ mmHg} \approx 133 \text{ Pa}$ (used for blood pressure).
- $1 \text{ bar} = 10^5 \text{ Pa}$.

The same force spread over a larger area gives lower pressure. A person walking on snow with snowshoes distributes their weight over a much larger area than walking in regular boots — same weight, much less pressure per square centimeter, no sinking through the crust.

### The mechanism — what makes pressure special in a fluid

Inside a fluid at rest, pressure has a remarkable property: at any point, it is the same in every direction. Push a tiny imaginary cube of fluid: the force per unit area on the top, bottom, sides, front, and back are all equal in magnitude. (This is why pressure is a *scalar*, not a vector — even though it produces forces in specific directions when it pushes against surfaces.)

This isotropy of pressure is what distinguishes a fluid from a solid. A solid can have different stresses in different directions (you can push down on a beam without pushing sideways). A fluid cannot — any imbalance would set the fluid in motion.

### The trade-off

Treating fluids as having scalar pressure trades **the directionally-rich vector force language** for **a single scalar quantity per point in space.** The cost is some abstraction; the benefit is enormous tractability. Once you know $P(x, y, z)$ in a fluid, you know everything about the forces it exerts on any surface — multiply by area, get force.

### Worked example — pressure under a snowshoe vs. boot

A $70 \text{ kg}$ person stands in winter snow. (a) Wearing standard boots ($A = 0.030 \text{ m}^2$ contact each, two boots), what is the pressure on the snow under each boot? (b) Wearing snowshoes ($A = 0.20 \text{ m}^2$ each), what is the pressure?

**Force.** $W = mg = 70 \times 9.80 = 686 \text{ N}$, distributed over both feet.

**Pressure (boots).** Total area $= 2 \times 0.030 = 0.060 \text{ m}^2$. $P = 686 / 0.060 \approx 11{,}400 \text{ Pa}$.

**Pressure (snowshoes).** Total area $= 2 \times 0.20 = 0.40 \text{ m}^2$. $P = 686 / 0.40 \approx 1{,}720 \text{ Pa}$.

Snowshoes reduce pressure by a factor of $\sim 6.6$ — enough to keep the person on top of the snow rather than sinking through it.

**Sanity check.** Atmospheric pressure is $\sim 10^5 \text{ Pa}$. The person's pressure on the snow is only $\sim 10\%$ (boots) or $\sim 2\%$ (snowshoes) of atmospheric. The snow's compressive strength is what determines whether the person sinks — and dry powder snow can support pressures around $10^4$–$10^5 \text{ Pa}$, while crusty snow holds more.

### Common misconceptions

- *"Pressure and force are the same."* They aren't. Pressure is force per unit area. The same force can produce very different pressures (boots vs. snowshoes). The same pressure can produce very different forces if applied to different areas (a hydraulic jack — Concept 2).
- *"Pressure has a direction."* In fluid statics, no — pressure at a point is a scalar. It produces forces in specific directions when applied to specific surfaces (always perpendicular to the surface), but the pressure itself is direction-independent.

↳ **Dig Deeper — Why is pressure a scalar in a fluid but stress is a tensor in a solid?**

*Solids can resist shear; fluids cannot. This single physical difference gives rise to the mathematical distinction: the state of stress in a solid requires a $3\times 3$ tensor (six independent components), while in a static fluid it reduces to a single scalar (pressure).*

**Prompt:**
> Explain why pressure in a static fluid can be described by a single scalar, while stress in a solid requires a tensor. Walk through the physical argument: a fluid by definition cannot sustain a static shear stress (any shear sets it in motion), so all the off-diagonal terms of the stress tensor vanish, and the diagonal terms must be equal (otherwise the fluid would shear under unequal compression). End with one sentence on what changes when the fluid is moving (then viscosity creates shear stresses, and pressure is no longer the only stress component).

**What to do with the output:** Save it. The scalar-pressure-vs-tensor-stress distinction is foundational to continuum mechanics and explains why fluid statics is conceptually simpler than solid mechanics.

---

## Concept 2 — Pressure with depth: $P = \rho g h$, Pascal's principle, hydraulic systems

### Why your ears pop on an airplane (and again at the bottom of a pool)

You're at sea level, atmospheric pressure $\sim 10^5 \text{ Pa}$. The plane climbs to $3{,}000 \text{ m}$. Atmospheric pressure drops to about $0.7 \times 10^5 \text{ Pa}$. The cabin is partially pressurized but not all the way to sea-level — typically around $0.8$ atm. Your ears equilibrate as quickly as your eustachian tubes allow, and the pop is the equilibration.

You're at sea level again, then dive into a swimming pool. Two meters down, your ears feel pressure. At that depth, in addition to the atmospheric pressure pressing on the water surface, you have $2 \text{ m}$ of water column above you adding extra pressure. Each meter of water adds $\rho g \times 1 \text{ m} = 1000 \times 9.80 \times 1 = 9{,}800 \text{ Pa}$ — about $0.1 \text{ atm}$. At $10 \text{ m}$ down, you've added a full atmosphere of pressure on top of the surface atmospheric.

### The mechanism — the depth-pressure relation

At a depth $h$ below the surface of a fluid of density $\rho$, the pressure is:

$$P = P_0 + \rho g h,$$

where $P_0$ is the pressure at the surface (atmospheric, if the fluid is exposed to air; or the pressure at whatever reference depth you choose).

The derivation is short. Consider a column of fluid of cross-section $A$ extending from the surface down to depth $h$. Its weight is $\rho V g = \rho A h g$. That weight is supported by the pressure difference across its bottom and top: $(P_{\text{bottom}} - P_{\text{top}}) A = \rho A h g$. So $P_{\text{bottom}} - P_{\text{top}} = \rho g h$, which gives the formula.

Notice what doesn't appear: the cross-sectional area, the shape of the container. The pressure at depth $h$ depends only on the density of the fluid, gravity, and depth. A narrow standpipe of water has the same pressure at its base as a wide swimming pool of the same depth.

### Pascal's principle

For an enclosed fluid (a tank with no free surface, or with the free surface at atmospheric pressure), if you increase the pressure at one point by some amount $\Delta P$, that increase is transmitted *undiminished* throughout the fluid. This is **Pascal's principle**.

The application: hydraulic systems. Push down on a small piston ($A_1$) with force $F_1$. The pressure increase $\Delta P = F_1 / A_1$ is transmitted to a larger piston ($A_2$). The force on the larger piston is $F_2 = \Delta P \times A_2 = F_1 \times (A_2 / A_1)$. If $A_2 = 100 A_1$, you get $100\times$ force amplification.

The trade-off (energy conservation, Chapter 7): the larger piston moves $1/100$ as far as the smaller. Total work in equals total work out. Pascal's principle redistributes force at the cost of distance — exactly like a lever.

### The trade-off

The depth-pressure relation $P = \rho g h$ assumes incompressible fluid and constant $g$. For water, both are excellent approximations even at depths of kilometers. For air, density itself varies with altitude (because air is compressible), so the relation needs modification — though over short altitude ranges, the linear formula is fine. This is the classic engineering trade: the simple formula works in most practical regimes; the corrections matter at extremes.

### Worked example — hydraulic jack lifting a car

A hydraulic jack has a small piston of area $A_1 = 5.0 \text{ cm}^2$ and a large piston of area $A_2 = 250 \text{ cm}^2$. (a) If you push down on the small piston with $200 \text{ N}$, what force is exerted by the large piston? (b) If the small piston moves down $10 \text{ cm}$, how far does the large piston rise?

**(a) Force amplification.**

$$F_2 = F_1 \frac{A_2}{A_1} = 200 \times \frac{250}{5.0} = 200 \times 50 = 10{,}000 \text{ N}.$$

A $200 \text{ N}$ push generates $10{,}000 \text{ N}$ of lift — enough to raise a $1{,}000 \text{ kg}$ car (weight $9{,}800 \text{ N}$).

**(b) Distance.** Volume conservation: $A_1 d_1 = A_2 d_2$.

$$d_2 = d_1 \frac{A_1}{A_2} = 10 \times \frac{5.0}{250} = 0.20 \text{ cm} = 2.0 \text{ mm}.$$

The large piston rises $2 \text{ mm}$ for every $10 \text{ cm}$ of small-piston travel. To lift a car $0.5 \text{ m}$, you'd need $250$ pump strokes — which is why hydraulic jacks have ratchets and you pump them many times.

**Sanity check.** Force amplification $\times$ distance ratio $= (250/5) \times (5/250) = 1$. Energy in equals energy out. Pascal's principle gives you force at the cost of distance. Consistent with conservation of energy from Chapter 7.

### Common misconceptions

- *"Pressure depends on the shape of the container."* It doesn't. $P = \rho g h$ depends only on depth (and $\rho$, $g$). A tall narrow column of water at the bottom has the same pressure as a shallow wide pool of the same depth.
- *"Hydraulic systems multiply energy."* They don't. They multiply *force* at the cost of distance. Total work is conserved. Energy is not free.

↳ **Dig Deeper — Atmospheric pressure as the weight of the air column above you**

*The atmosphere is a fluid (gas) under gravity. The pressure at sea level — about $1.013 \times 10^5 \text{ Pa}$ or $14.7 \text{ psi}$ — is the weight per unit area of all the air directly above you. Computing this from first principles requires integrating because air's density varies with altitude.*

**Prompt:**
> Use $P = \rho g h$ (or its integral form, since $\rho$ varies with altitude) to estimate atmospheric pressure at sea level. Take an effective scale height of about 8 km for the atmosphere (the height over which density falls by a factor of $e$). Show that the pressure works out to about $10^5 \text{ Pa}$. Then explain (a) why the formula $P = \rho g h$ is exactly right for an incompressible liquid but only approximate for the atmosphere, (b) why Mt. Everest's summit (~9 km) has roughly $1/e \approx 37\%$ of sea-level pressure, (c) what this means for hikers / climbers physiologically.

**What to do with the output:** Save it. The connection between depth-pressure relations and atmospheric structure is foundational to meteorology and high-altitude physiology.

---

## Concept 3 — Buoyancy and Archimedes' principle

### Eureka, in a bath

The story is that Archimedes, sometime around 250 BC, was asked by King Hiero II of Syracuse to determine whether a goldsmith had cheated by replacing some of a crown's gold with silver. Archimedes was stuck on the problem until he stepped into a public bath and noticed the water level rise as he submerged. He realized, the legend goes, that the volume of water displaced equals the volume of the submerged object. Since gold and silver have different densities, comparing the crown's mass to its volume (via water displacement) would reveal whether it was pure gold. He shouted "Eureka!" — Greek for "I have found it!" — and ran naked through the streets to tell the king.

Whether the bath story is literal or apocryphal, the underlying principle is real and bears Archimedes' name:

**Archimedes' principle:** the buoyant force on a submerged or partially submerged object equals the weight of the fluid the object displaces.

### The mechanism — buoyant force from pressure differences

Consider a cube of side $L$ submerged in a fluid, with its top at depth $h_1$ and bottom at depth $h_2 = h_1 + L$. The pressure on the top is $P_1 = P_0 + \rho g h_1$; on the bottom, $P_2 = P_0 + \rho g h_2$. The pressure on the bottom is greater than on the top by $\rho g L$.

Forces: on the top, $P_1 \times L^2$ pushing down. On the bottom, $P_2 \times L^2$ pushing up. Net upward force:

$$F_{\text{buoy}} = (P_2 - P_1) L^2 = \rho g L \times L^2 = \rho g V_{\text{cube}}.$$

But $\rho V_{\text{cube}}$ is the mass of fluid that would occupy the cube's volume — i.e., the mass of fluid the cube displaced. So:

$$F_{\text{buoy}} = \text{(weight of displaced fluid)}.$$

This is Archimedes' principle. The argument generalizes to any shape (not just a cube), because all shapes can be approximated as collections of small cubes.

**Sinking vs. floating.** An object sinks if its weight exceeds the buoyant force when fully submerged — i.e., if its density exceeds that of the fluid. An object floats if its density is less than the fluid's. A floating object displaces just enough fluid for the buoyant force to equal its weight; the rest sticks up above the surface.

A steel ship floats not because steel is less dense than water (it isn't) but because the ship's *average* density (steel + a lot of enclosed air) is less than water's. A solid block of the same steel would sink; the hull's volume gives it average density below water's.

### The trade-off

Archimedes' principle trades **detailed pressure-on-surface integration** for **a single rule about displaced fluid weight.** The cost: the rule doesn't tell you about pressure distribution (which can matter for designing pressure hulls). The benefit: it tells you the *net* buoyant force in one line, regardless of object shape.

### Worked example — the gold crown problem

A crown weighs $7.84 \text{ N}$ in air. Submerged in water, its apparent weight (buoyant force subtracted) is $6.84 \text{ N}$. Is the crown pure gold? (Density of gold: $19{,}300 \text{ kg/m}^3$; water: $1{,}000 \text{ kg/m}^3$.)

**Buoyant force.** $F_{\text{buoy}} = 7.84 - 6.84 = 1.00 \text{ N}$.

**Volume of crown** (volume of water displaced).

$$F_{\text{buoy}} = \rho_{\text{water}} g V \implies V = \frac{F_{\text{buoy}}}{\rho_{\text{water}} g} = \frac{1.00}{1000 \times 9.80} \approx 1.02 \times 10^{-4} \text{ m}^3.$$

**Mass of crown.**

$$m = W/g = 7.84 / 9.80 = 0.800 \text{ kg}.$$

**Density of crown.**

$$\rho_{\text{crown}} = \frac{m}{V} = \frac{0.800}{1.02 \times 10^{-4}} \approx 7{,}840 \text{ kg/m}^3.$$

This is much less than gold's $19{,}300 \text{ kg/m}^3$. The crown is not pure gold. (It's denser than aluminum, but lighter than gold — consistent with a gold-silver mix or some other diluted alloy.)

**Sanity check.** A pure gold crown of mass $0.800 \text{ kg}$ would have volume $0.800/19300 \approx 4.1 \times 10^{-5} \text{ m}^3$ — about $40 \text{ mL}$ — and would displace only $0.40 \text{ N}$ of buoyant force, giving apparent weight $7.44 \text{ N}$. Our measurement of $6.84 \text{ N}$ is far below that — the crown displaces more water than pure gold would, indicating it's less dense.

### Common misconceptions

- *"Buoyant force depends on depth."* It doesn't (much) for incompressible fluids. The buoyant force on a submerged object is the weight of the displaced fluid — which depends on the volume of the object and the fluid's density, not on how deep the object is.
- *"Wood floats because it's lighter than water."* Wood floats because it's *less dense* than water. A small block of wood and a large log both float — but the log is much heavier than the small block. Density (mass per volume), not mass, determines flotation.

↳ **Dig Deeper — Surface tension, capillary action, and how mosquitoes walk on water**

*The surface of a fluid behaves as if it has a thin elastic skin under tension. This is surface tension, arising from cohesive forces between fluid molecules. It's what lets some insects walk on water, what shapes water droplets, and what drives capillary action — the rise of fluid in a thin tube.*

**Prompt:**
> Explain surface tension as a consequence of cohesive forces between liquid molecules at a free surface. Compute (a) the surface tension of water at room temperature ($\gamma \approx 0.073 \text{ N/m}$), (b) the height water rises in a $1 \text{ mm}$ diameter glass capillary tube using Jurin's law $h = 2\gamma \cos\theta / (\rho g r)$ with $\theta \approx 0$ for water-on-glass and $r$ the radius. End with one sentence on why mercury in a glass tube *falls* below the surrounding level (the contact angle exceeds $90°$, so $\cos\theta$ is negative).

**What to do with the output:** Save it. Surface tension is the entry point to soap films, foams, contact angles, and the molecular forces in fluid biology (lung surfactant, plant transpiration).

---

## Synthesis — fluids at rest

Step back. Three concepts:

**Density and pressure** are the fundamentals. Pressure is force per unit area; in a static fluid, it's the same in every direction at a point.

**Pressure with depth** ($P = \rho g h$), Pascal's principle, hydraulic systems. Pressure increases linearly with depth in an incompressible fluid; pressure applied to an enclosed fluid is transmitted everywhere.

**Buoyancy** (Archimedes' principle): the buoyant force on a submerged object equals the weight of the displaced fluid. Floating/sinking is decided by average density compared to fluid density.

The **scale shift**: from a $9{,}800 \text{ Pa}$ pressure increase at $1 \text{ m}$ depth in a swimming pool, to $110 \text{ MPa}$ at $11 \text{ km}$ depth in the Mariana Trench, to gigapascals at the center of the Earth. The same equation $P = \rho g h$ (or its integral form for non-uniform density) applies. From $1 \text{ atm}$ at sea level to vacuum in space, to $10^5$ atm at the center of Jupiter. Pressure spans tens of orders of magnitude in nature, all governed by the same machinery.

### A worked example using all three concepts — a submarine in equilibrium

A small submarine of mass $50{,}000 \text{ kg}$ has hull volume $48 \text{ m}^3$. The hull is mostly empty space (the metal walls plus crew quarters). It floats half-submerged at the surface (with half its volume — $24 \text{ m}^3$ — under water). To dive, ballast tanks (each $5 \text{ m}^3$) are flooded with seawater. (a) What buoyant force does it experience while half-submerged? (b) How many ballast tanks must be flooded to make it neutrally buoyant (just barely sinking)?

**Concept 1 — pressure / density setup.** Density of seawater $\rho = 1{,}030 \text{ kg/m}^3$. Submarine weight $W = mg = 50{,}000 \times 9.80 = 490{,}000 \text{ N}$.

**Concept 2 — pressure at depth (not directly used here for floating, but relevant for diving):** Surface pressure $\sim 1 \text{ atm}$; at $100 \text{ m}$ depth, additional pressure $\rho g h = 1030 \times 9.80 \times 100 \approx 10^6 \text{ Pa} \approx 10 \text{ atm}$.

**Concept 3 — Archimedes.** While half-submerged, displaced water = $24 \text{ m}^3$. Mass of displaced water = $24 \times 1030 = 24{,}720 \text{ kg}$. Buoyant force = $24{,}720 \times 9.80 \approx 242{,}000 \text{ N}$.

But $W = 490{,}000 \text{ N}$ — twice the buoyant force at half-submerged. This means the submarine *wouldn't* float half-submerged with the given numbers; it would sink. Let me redo: if the sub floats at the surface, its average density (mass / total volume) must equal water's density, so:

$$\rho_{\text{sub, avg}} = m / V_{\text{total}} = 50000 / 48 \approx 1042 \text{ kg/m}^3.$$

This is greater than seawater's $1030$ — so actually the empty submarine (without flooding tanks) sinks. Let me reframe the problem: assume the submarine is designed with $V_{\text{total}} = 50 \text{ m}^3$ such that average density empty is $50000/50 = 1000 < 1030$, so it floats.

If submarine total volume (empty hull) is $V_{\text{total}} = 50 \text{ m}^3$, fully submerged buoyant force = $50 \times 1030 \times 9.80 = 504{,}700 \text{ N}$. Weight = $490{,}000 \text{ N}$. Net upward force = $14{,}700 \text{ N}$ — submarine wants to float.

To make it neutrally buoyant, flood ballast: each $5 \text{ m}^3$ tank, when filled with $5{,}150 \text{ kg}$ of seawater, adds $50{,}500 \text{ N}$ of weight and reduces effective displaced volume by $5 \text{ m}^3$ (so $51{,}500 \text{ N}$ of buoyancy is replaced by water that adds nothing to net buoyancy). Net change per tank: $-101{,}000 \text{ N}$ approximately. To overcome the $14{,}700 \text{ N}$ excess buoyancy, you need ~$0.15$ tanks worth — i.e., partially filling one tank. The exact value depends on the tank geometry; the algebra gives the answer.

This synthesis exercises all three concepts: density (water density and average submarine density), pressure (matters during the dive though not directly in equilibrium), and buoyancy (Archimedes determining the float / sink condition). Real submarine ballast control is a matter of fine-tuning the average density to be just barely above or below seawater's — and most submarines also use trim tanks to adjust pitch.

---

## Exercises

### Warm-up

**11.1** *(LO 1)* A block of aluminum has dimensions $0.10 \text{ m} \times 0.10 \text{ m} \times 0.20 \text{ m}$. Density of aluminum is $2{,}700 \text{ kg/m}^3$. (a) Volume? (b) Mass? (c) Weight on Earth?

**11.2** *(LO 2)* A force of $400 \text{ N}$ is applied perpendicular to a $0.020 \text{ m}^2$ surface. What is the pressure?

**11.3** *(LO 3)* What is the gauge pressure (above atmospheric) at $5.0 \text{ m}$ depth in fresh water?

**11.4** *(LO 5)* A $2.0 \text{ kg}$ object hung from a spring scale reads $20 \text{ N}$ in air and $15 \text{ N}$ when fully submerged in water. (a) What is the buoyant force? (b) What is the object's volume? (c) What is the object's density?

### Application

**11.5** *(LO 3)* Compute the absolute pressure at the bottom of a $3.0 \text{ m}$ deep swimming pool, including atmospheric pressure ($1.01 \times 10^5 \text{ Pa}$).

**11.6** *(LO 4)* A hydraulic lift has small piston area $20 \text{ cm}^2$ and large piston area $400 \text{ cm}^2$. (a) What input force lifts a $1{,}500 \text{ kg}$ car? (b) If the small piston moves down $20 \text{ cm}$, how high does the car rise?

**11.7** *(LO 5)* A block of wood ($\rho = 700 \text{ kg/m}^3$) is placed in fresh water. What fraction of its volume is submerged? In seawater?

**11.8** *(LO 5)* A helium balloon (volume $0.030 \text{ m}^3$, mass of balloon material $0.010 \text{ kg}$, helium density $0.18 \text{ kg/m}^3$, air density $1.21 \text{ kg/m}^3$) is released. What is the maximum mass it can lift (in addition to itself)?

### Synthesis

**11.9** *(LO 1, 5)* A solid ice cube ($\rho_{\text{ice}} = 917 \text{ kg/m}^3$) of side $4 \text{ cm}$ floats in fresh water. (a) Compute the volume submerged. (b) Compute the height of ice above the water surface.

**11.10** *(LO 3, 5)* A diver descends to $50 \text{ m}$ depth in seawater. (a) What absolute pressure does she experience? In atm? (b) If her lungs (at the surface) hold $4 \text{ L}$ of air at atmospheric pressure, and the air is compressed isothermally during descent, what volume do the lungs hold at $50 \text{ m}$? (Use $PV = $ constant for isothermal compression, from the gas laws — preview of Ch. 13.)

**11.11** *(LO 1, 5)* A boat with mass $5{,}000 \text{ kg}$ floats in fresh water with $0.40 \text{ m}^2$ of waterline (the area at the water surface). When 8 passengers totaling $640 \text{ kg}$ board, by how much does the boat sink (assume the waterline area doesn't change much)?

### Challenge

**11.12** *(beyond chapter)* A cylindrical pressure vessel ($d = 1.0 \text{ m}$, length $5.0 \text{ m}$) holds water at gauge pressure $5.0 \times 10^5 \text{ Pa}$ ($\sim 5 \text{ atm}$). (a) Compute the total force on each circular end-cap. (b) Compute the total force trying to split the cylinder along a longitudinal seam. (c) Comment on why pressure vessels typically have rounded ends.

**11.13** *(beyond chapter)* Estimate the depth at which a glass of water held by a scuba diver would burst due to internal-vs-external pressure mismatch. (Glass yield stress $\sim 50 \text{ MPa}$ in tension; assume the glass is $3 \text{ mm}$ thick and $7 \text{ cm}$ in diameter.)

---

## LLM Exercise — Chapter 11: Fluid Statics in Your Anchor Phenomenon

**Project:** Physics Reality Check Logbook
**What you're building this chapter:** A pressure or buoyancy analysis of one fluid element in your anchor phenomenon.
**Tool:** Claude Project.

### The Prompt

```
I'm continuing my Physics Reality Check Logbook for College Physics with LLMs. My anchor phenomenon is [paste 1-sentence description].

For Chapter 11, I want to apply fluid statics — pressure, depth, buoyancy — to one fluid in my phenomenon. Please:

1. Identify ONE fluid element in my phenomenon (a static fluid or a fluid at near-equilibrium). Examples:
   - Bike commute: tire pressure (gauge vs. absolute); pressure under each wheel.
   - Coffee maker: pressure of the water column above the heating element; pressure at the brewing chamber gasket.
   - Basketball: pressure inside the inflated ball.
   - Marathon: blood pressure in the runner's circulatory system at heart vs. feet (hydrostatic gradient).
   - Espresso: pressure profile in the puck during 9-bar extraction (this is dynamic but the static piece can be analyzed first).

2. Identify the relevant fluid statics quantity: pressure, depth, density, buoyancy.

3. Compute it using $P = F/A$, $P = \rho g h$, or Archimedes' principle as appropriate.

4. Express the result in multiple units (Pa, atm, mmHg, psi as appropriate).

5. Sanity check: does the magnitude match what you'd expect? (Tire pressures should be a few atm; blood pressure ~100 mmHg systolic; a basketball ~8 psi gauge.)

6. Identify which assumption (incompressible, static, no temperature gradient) is most likely to bite.

7. One sentence on how this connects to Chapter 12 (fluid dynamics) — when fluid moves, pressure becomes part of an energy budget along with kinetic energy and elevation.

Save the output as logbook/chapter-11-fluid-statics.md.
```

### What this produces

An eleventh Logbook entry: a fluid-statics analysis of one element in your phenomenon, often surprising in the magnitudes.

### How to adapt this prompt

- *For phenomena with no obvious fluid* (a basketball shot in air): the air around the ball is a fluid; air pressure changes with altitude can be relevant.
- *For ChatGPT or Gemini:* identical with substitutions.
- *For Claude Code:* if you have pressure-time data (e.g., from a smart scale or pressure sensor), paste it for analysis.

### Connection to previous chapters

Builds on Chapter 4 (force, here as pressure × area), Chapter 7 (energy in hydraulic systems), Chapter 9 (statics — fluid statics is a special case where everything is balanced).

### Preview of next chapter

Chapter 12 takes fluids into motion. Bernoulli's principle relates fluid speed to pressure (faster flow has lower pressure). The continuity equation describes how flow speed changes with pipe cross-section. Fluid dynamics has its own conservation principles — and many medical and engineering applications (blood flow, airplane lift, plumbing).

---

## Chapter summary

Three pillars of fluid statics. **Density** $\rho = m/V$ is the basic property of a substance that determines floating, sinking, and how much it weighs per unit volume. **Pressure** $P = F/A$ is force concentration; in a static fluid, it's a scalar (same in every direction at a point). **Pressure with depth** $P = P_0 + \rho g h$ (incompressible fluid) lets you compute pressure at any depth. **Pascal's principle** says pressure changes propagate undiminished throughout an enclosed fluid — the basis of hydraulic systems. **Archimedes' principle** says buoyant force equals weight of displaced fluid — the basis of why things float or sink.

The one idea that matters most: **fluid statics reduces all the geometric complexity of a fluid to a single scalar field, the pressure $P(x, y, z)$.** Once you know $P$ everywhere, you know all the forces the fluid exerts on any surface. The depth-pressure relation gives you $P$ in most everyday static situations.

The common mistake to watch for: **conflating mass and density.** A ton of feathers has the same mass as a ton of bricks, but very different density. Whether something floats depends on density (relative to the fluid), not absolute mass.

What you should now be able to teach someone else: how to compute pressure in a fluid at any depth, why a hydraulic jack amplifies force at the cost of distance, and how Archimedes' principle predicts whether an object floats. Three skills, one organizing principle: pressure, propagating through a fluid, generates all the forces.

---

## What would change my mind

The chapter argues that the static-fluid framework — incompressible, scalar pressure, $P = \rho g h$ — is sufficient for most practical engineering and biological applications. The argument would need revision if a class of static-fluid problems systematically required corrections beyond compressibility (e.g., for atmospheric pressure at large altitudes — which the chapter notes) or beyond the scalar approximation (e.g., for fluids with significant elasticity, like complex biological fluids). Both corrections are well-handled by extensions of the framework.

## Still puzzling

The deepest puzzle this chapter raises and does not resolve: **why is pressure isotropic in a static fluid, exactly?** The argument from "fluids can't sustain shear" is correct, but its molecular basis (random thermal motion of molecules, equilibrating collisions in all directions) connects fluid statics to statistical mechanics in a way that classical mechanics alone can't capture. We won't see kinetic theory until Chapter 13.

---

## Connections forward

Chapter 12 introduces fluid dynamics — fluids in motion. Bernoulli's equation is essentially energy conservation for fluids and reduces to $P + \rho g h + \tfrac{1}{2}\rho v^2 = $ constant along a streamline (when the fluid is steady, incompressible, and frictionless). Continuity equation describes mass conservation. Together, they predict everything from Venturi meters to airplane lift to blood flow through arteries. Chapter 13 (gas laws) treats compressible fluids — gases — with their own equations of state. Chapter 14 (heat) connects pressure to temperature via the ideal gas law. The static-fluid framework here is the foundation; later chapters add motion, compressibility, and thermal effects on top.

---

**Tags:** fluid-statics, pressure, buoyancy, Pascals-principle, Archimedes

---

## AI Wayback Machine

**Blaise Pascal** worked out fluid pressure in the 1640s — including the principle that any pressure applied to an enclosed fluid is transmitted undiminished throughout. Modern hydraulic systems are still applications of Pascal's principle.

**Run this:**

```
Who was Blaise Pascal, and how does Pascal's principle connect to the fluid statics we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about his career or ideas.
```

→ Search **"Blaise Pascal"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to walk through how a hydraulic press multiplies force using Pascal's principle.
- Ask it about Pascal's parallel career inventing the first calculating machine and pioneering probability theory.

What changes? What gets better? What gets worse?
