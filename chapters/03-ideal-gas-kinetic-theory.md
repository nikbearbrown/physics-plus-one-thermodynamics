# Chapter 3 — The Ideal Gas and Kinetic Theory

*Deriving $PV = NkT$ from molecular collisions, and the Maxwell-Boltzmann distribution.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Derive the ideal gas law $PV = NkT = nRT$ from the molecular pressure calculation.
2. **(Apply)** Use the Maxwell-Boltzmann distribution to compute $v_{mp}$, $v_{avg}$, $v_{rms}$ and predict the shape of the speed distribution.
3. **(Apply)** Apply the equipartition theorem to predict molar heat capacities of monatomic and diatomic ideal gases.
4. **(Analyze)** Identify when the ideal gas approximation breaks down and use the van der Waals equation as the next-order correction.
5. **(Understand)** Connect the molecular picture (kinetic theory) to macroscopic gas laws.
6. **(Apply)** Build a Maxwell-Boltzmann distribution explorer with adjustable temperature and molecular mass.

---

## Opening case: why Mars lost its atmosphere

Mars is about half the diameter of Earth. Its gravitational escape velocity at the surface is $v_{\text{esc}} \approx 5.0$ km/s (vs. Earth's 11.2 km/s).

For hydrogen molecules in the Martian upper atmosphere at $T \approx 200$ K: $v_{rms} = \sqrt{3 k_B T / m_{H_2}} = \sqrt{3 \cdot 1.38 \times 10^{-23} \cdot 200 / (2 \cdot 1.66 \times 10^{-27})} \approx 1.6$ km/s. Much less than escape velocity. *But* — the Maxwell-Boltzmann distribution has a *tail*. Some molecules move much faster than average. The fraction with $v > 5$ km/s is small but non-zero.

Over billions of years, those tail molecules slowly escape Mars's gravity. Hydrogen leaks fastest (lightest); helium next; nitrogen and oxygen barely at all (too heavy at Mars's temperatures). The result: Mars lost essentially all its hydrogen long ago, and most of its lighter atmospheric components. Today, Mars's atmosphere is 95% CO₂ at 6 mbar — about 0.6% of Earth's atmospheric pressure.

The chapter ahead is the kinetic theory that explains this. It also derives the ideal gas law, predicts the Maxwell-Boltzmann distribution, and sets up the equipartition theorem that governs heat capacities. The big picture: macroscopic gas behavior comes from molecular mechanics.

---

## Core concept

### The ideal gas model

A gas is treated as a collection of point particles (no internal structure) that:
1. Move randomly with the Maxwell-Boltzmann distribution.
2. Collide elastically with each other and the container walls.
3. Have negligible volume compared to the container.
4. Don't interact except during collisions (no intermolecular forces).

This is an idealization. Real gases at low density and moderate temperature behave close to ideal; deviations matter near phase transitions and at high density.

### Deriving the ideal gas law

Consider $N$ molecules of mass $m$ in a cubic box of side $L$ (volume $V = L^3$). Pick one molecule moving in the $+x$ direction with speed $v_x$. When it hits the right wall and bounces back, momentum transfer to wall: $\Delta p = 2 m v_x$. Time between collisions with the same wall: $2L/v_x$.

Average force on the right wall from this one molecule: $F = \Delta p / \Delta t = (2 m v_x)/(2L/v_x) = m v_x^2 / L$.

Total force on the right wall from all $N$ molecules: $F_{\text{total}} = (N/3) m \langle v^2\rangle / L$ (factor of 1/3 because only one component of $v$ matters at any wall, and $\langle v_x^2\rangle = \langle v^2\rangle/3$).

Pressure: $P = F/A = F/L^2 = (N/3) m \langle v^2\rangle / L^3 = (N/3V) m \langle v^2\rangle$.

But $T = m\langle v^2\rangle / (3k_B)$, so $m\langle v^2\rangle = 3k_BT$. Substituting:

$$PV = N k_B T$$

In terms of moles ($N = nN_A$):

$$PV = nRT$$

where $R = N_A k_B = 8.314$ J/(mol·K) is the universal gas constant.

The ideal gas law isn't postulated — it's a *derived consequence* of molecular mechanics plus the definition of temperature.

### The Maxwell-Boltzmann speed distribution

For an ideal gas at temperature $T$, the fraction of molecules with speed between $v$ and $v + dv$ is

$$f(v) \, dv = 4\pi \left(\frac{m}{2\pi k_B T}\right)^{3/2} v^2 e^{-mv^2/(2k_B T)} \, dv$$

This distribution has three characteristic speeds:

- **Most probable speed** (peak of $f(v)$): $v_{mp} = \sqrt{2k_BT/m}$
- **Average speed**: $v_{avg} = \sqrt{8k_BT/(\pi m)}$
- **Root-mean-square speed**: $v_{rms} = \sqrt{3k_BT/m}$

Always $v_{mp} < v_{avg} < v_{rms}$ — the distribution is asymmetric, with a tail extending to high speeds.

**Source:** Maxwell derived this in 1860; Boltzmann later generalized it. The derivation uses statistical mechanics; Chapter 8 redoes it from the Boltzmann distribution.

**Effects of $T$:** higher $T$ broadens the distribution and shifts the peak right.

**Effects of $m$:** heavier molecules at the same $T$ have *slower* distributions. At room temperature, hydrogen molecules average $\sim 1900$ m/s, nitrogen molecules $\sim 510$ m/s.

### The equipartition theorem

At thermal equilibrium, each *quadratic degree of freedom* of a system has average energy $\frac{1}{2} k_B T$.

A monatomic atom has 3 translational degrees of freedom: 3 quadratic terms in the kinetic energy ($(1/2)mv_x^2 + (1/2)mv_y^2 + (1/2)mv_z^2$). Internal energy per atom: $U_1 = (3/2)k_BT$. Total internal energy: $U = (3/2)Nk_BT$. Heat capacity: $C_V = (3/2)Nk_B = (3/2)nR$.

A diatomic molecule (N₂, O₂) at moderate temperature has 3 translational + 2 rotational degrees of freedom (only 2 rotational because rotation about the molecular axis carries no energy for a symmetric molecule). 5 quadratic terms. $U = (5/2)Nk_BT$. $C_V = (5/2)nR$.

At very high temperatures, vibrational modes also activate — adding 2 more quadratic terms per mode (one for KE, one for PE in the harmonic oscillator). For N₂, vibrational mode activates at $T \gtrsim 3000$ K. $C_V$ jumps to $(7/2)nR$.

**The quantum twist:** the equipartition theorem assumes *classical* harmonic oscillator. At low $T$ where $k_B T < \hbar\omega$ for the mode, quantum effects "freeze out" the mode and equipartition fails. Chapter 8 explains why.

### Real gases and van der Waals

The ideal gas law fails when (a) molecules are close together (high density), (b) temperatures are low, or (c) the gas is near a phase transition. The simplest correction is the **van der Waals equation**:

$$\left(P + \frac{a n^2}{V^2}\right)(V - nb) = nRT$$

The $a$ term accounts for **attractive intermolecular forces** (reducing effective pressure). The $b$ term accounts for **finite molecular volume** (reducing effective container volume).

For CO₂: $a = 3.64$ L²·atm/mol², $b = 0.0427$ L/mol.

At low density / high temperature, van der Waals reduces to the ideal gas law. Near the critical point, van der Waals predicts a first-order phase transition (liquid ↔ vapor) — qualitatively correct, quantitatively approximate.

### Dalton's law of partial pressures

In a mixture of $N$ non-reacting ideal gases at the same temperature, the total pressure is the sum of partial pressures:

$$P_{\text{total}} = P_1 + P_2 + \cdots + P_N$$

where $P_i = n_i RT/V$ for each gas as if it were alone. This is a direct consequence of the molecular picture: each species contributes its share of momentum-transfer-per-area to the walls.

---

## Worked example: O₂ at room temperature

$N$ moles of oxygen (O₂, molar mass $M = 32$ g/mol) at $T = 300$ K. Find $v_{mp}$, $v_{avg}$, $v_{rms}$ and verify ordering.

**Molecular mass:** $m = M/N_A = (0.032 \text{ kg/mol})/(6.022 \times 10^{23}/\text{mol}) = 5.31 \times 10^{-26}$ kg.

**Compute each:**
- $v_{mp} = \sqrt{2 k_B T / m} = \sqrt{2 \cdot 1.38 \times 10^{-23} \cdot 300 / 5.31 \times 10^{-26}} = \sqrt{156,000} \approx 395$ m/s.
- $v_{avg} = \sqrt{8 k_B T / (\pi m)} = \sqrt{(8/\pi) \cdot 156,000 / 2} \approx 446$ m/s.

Actually let me redo: $\sqrt{8 k_B T/(\pi m)} = \sqrt{(8/\pi)} \cdot \sqrt{k_BT/m}$. We have $\sqrt{k_BT/m} = \sqrt{156,000/2} = \sqrt{78,000} \approx 279$ m/s, so $v_{avg} = \sqrt{8/\pi} \cdot 279 \approx 1.596 \cdot 279 \approx 446$ m/s.

- $v_{rms} = \sqrt{3 k_B T / m} = \sqrt{1.5 \cdot 156,000} = \sqrt{234,000} \approx 484$ m/s.

**Verify ordering:** $395 < 446 < 484$. ✓

**The lesson.** At room temperature, oxygen molecules average about 400–500 m/s — comparable to the speed of sound in air. The exact value depends on which "average" you mean.

**The limit.** This is the *ideal-gas, classical, single-species* calculation. At very low temperatures (cryogenic), quantum effects appear — Bose-Einstein condensation of a gas of bosonic atoms requires the molecules to slow to $\sim$ μm/s. At extremely high temperatures, ionization and dissociation dominate, and the gas becomes a plasma.

---

## Common misconceptions

**"All molecules in a gas at temperature T have the same speed."** False — they have a distribution. $T$ controls the *average* (specifically the second moment of the distribution); individual molecules range from near-zero to many times $v_{rms}$.

**"Heavier gases at the same T are hotter."** Temperature depends on $\langle KE\rangle$, not $\langle v\rangle$. Heavier molecules at the same $T$ are *slower*. Hydrogen at 300 K: $v_{rms} \approx 1930$ m/s. Carbon dioxide at 300 K: $v_{rms} \approx 411$ m/s.

**"The ideal gas law is always accurate."** It works well for low-density gases. At high pressure, low temperature, or near a phase transition, intermolecular forces and finite molecular volume become important — van der Waals or more sophisticated equations of state are needed.

**"The Maxwell-Boltzmann distribution is symmetric."** It's *not*. It's a skewed distribution with a tail extending to high speeds. That tail is what allows hydrogen to escape Mars's atmosphere.

**"Equipartition is a fundamental law."** It's a classical result. Quantum mechanics (Chapter 8) explains *why it breaks down* at low temperatures — vibrational modes "freeze out" when $k_BT$ falls below their quantum energy spacing.

---

## Exercises

**Warm-up (Apply).** Find $v_{rms}$ for nitrogen (N₂, $M = 28$) at $T = 300$ K.

**Apply.** Compute $v_{mp}, v_{avg}, v_{rms}$ for argon (Ar, $M = 40$) at $T = 500$ K. Verify ordering.

**Apply.** A 1 mol sample of helium at $T = 300$ K, $V = 10$ L. (a) Pressure from ideal gas law. (b) Pressure from van der Waals ($a = 0.0341$ L²·atm/mol², $b = 0.0237$ L/mol). Are they close?

**Apply + Analyze.** For diatomic gas like O₂: predict $C_V$ at $T = 100$ K (rotation excited, vibration frozen), $T = 1000$ K (rotation + most of vibration), $T = 5000$ K (rotation + vibration fully classical).

**Apply (atmospheric escape).** Find the fraction of N₂ molecules in Earth's exosphere ($T = 1000$ K) with $v > 11.2$ km/s (escape velocity). Hint: integrate the Maxwell-Boltzmann distribution from $v_{\text{esc}}$ to infinity, or use a software estimate. (Answer: ~$10^{-50}$ — essentially zero. Earth keeps its nitrogen.)

**Challenge.** Mars: $T = 200$ K, escape velocity $v_{\text{esc}} = 5.0$ km/s. Find the fraction of hydrogen molecules (H₂, $M = 2$) above escape velocity. (Answer: ~$10^{-3}$ — small but non-zero. Hydrogen escapes Mars over geological time.)

---

## LLM Exercises

### Build the Maxwell-Boltzmann explorer (`03-maxwell-boltzmann.html`)

> **Show.** Maxwell-Boltzmann speed distribution: $f(v) = 4\pi(m/(2\pi k_BT))^{3/2} v^2 e^{-mv^2/(2k_BT)}$. Three speeds: $v_{mp} = \sqrt{2k_BT/m}$, $v_{avg} = \sqrt{8k_BT/(\pi m)}$, $v_{rms} = \sqrt{3k_BT/m}$.
>
> **Say.** Build a Maxwell-Boltzmann distribution explorer.
>
> **Constrain.** D3 v7. Slider for $T$ (100–2000 K). Dropdown for molecular species: H₂ (M=2), He (4), N₂ (28), O₂ (32), Ar (40), CO₂ (44). Compute and display $f(v)$ as an area chart, with $v_{mp}, v_{avg}, v_{rms}$ marked as vertical lines (color-coded). Numerical readouts of all three speeds. Display the "escape fraction" — fraction of molecules above 11.2 km/s (Earth escape) and above 5.0 km/s (Mars escape). Two-curve overlay mode: compare two temperatures or two species. Filename: `03-maxwell-boltzmann.html`.
>
> **Verify.** (a) At higher $T$, distribution broadens and shifts right. (b) At higher $m$, distribution narrows and shifts left. (c) Always $v_{mp} < v_{avg} < v_{rms}$. (d) Escape fraction for H₂ on Mars at 200 K: about $10^{-3}$.

### Exploration

- Compare H₂ at 300 K and N₂ at 300 K. Verify that the lighter molecule has a much faster distribution.
- Look at the escape fractions for various atmospheres: H₂ at Mars (200 K) vs N₂ at Earth (288 K). Mars has lost its hydrogen; Earth keeps its nitrogen.
- At what temperature does the average speed of nitrogen equal the speed of sound in air (343 m/s)? (Answer: around 300 K — coincidence, but instructive.)

### Extension prompt (chapter bridge)

> **Show.** I've modeled the gas in equilibrium. Now I want to apply the *first law of thermodynamics* — energy conservation — to processes that change a gas's state.
>
> **Say.** Build a first-law energy-balance visualizer.
>
> **Constrain.** A box with gas at $T_0$, $P_0$, $V_0$. Slider for process type (isothermal, adiabatic, isochoric, isobaric). Slider for final state. Compute $Q$, $W$, $\Delta U$ from the appropriate formulas. Display the energy bar chart showing energy moving in/out.
>
> **Verify.** Isothermal: $\Delta U = 0$ so $Q = W$. Adiabatic: $Q = 0$ so $\Delta U = -W$. Isochoric: $W = 0$ so $Q = \Delta U$. Isobaric: $W = P\Delta V$, $Q = \Delta U + W$.

Save as `03b-first-law-preview.html`. Bridge to Chapter 4.

---

## What would change my mind

The ideal gas law has been verified empirically over centuries of measurements; the molecular derivation is a textbook calculation that requires only Newton's laws and the definition of temperature. The Maxwell-Boltzmann distribution has been confirmed in countless experiments — molecular beam apparatuses, atomic clocks, plasma physics, and (subtly) in spectroscopic line shapes. A confirmed deviation from these predictions for a *low-density gas of non-interacting molecules* would shake the foundations. None exists.

Real gases deviate from ideal behavior in known, quantitative ways. The van der Waals equation captures the first-order correction; more sophisticated equations of state (Redlich-Kwong, Peng-Robinson, etc.) capture higher-order effects. None challenges the underlying molecular picture.

## Still puzzling

- *Why does equipartition fail at low T?* Because energy levels are quantized; modes whose energy spacing exceeds $k_B T$ can't be excited. The "freezing out" of vibrational modes is the simplest case. Chapter 8 explains this in detail.
- *What about quantum gases at low T?* Bose-Einstein condensation and degenerate Fermi gases (cold neutron stars, white dwarfs) — none of these obey classical kinetic theory. Required: quantum statistics (Ch 8).
- *What about plasma?* At high enough $T$, electrons get knocked off atoms. The gas becomes a plasma — neutral overall but with mobile charged particles. Plasma physics is its own field; the chapter is for *neutral* gases.

---

**Tags:** ideal gas law, kinetic theory, Maxwell-Boltzmann distribution, $v_{mp}$, $v_{avg}$, $v_{rms}$, equipartition theorem, degrees of freedom, van der Waals equation, atmospheric escape

