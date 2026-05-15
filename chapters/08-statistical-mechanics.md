# Chapter 8 — Statistical Mechanics

*The bridge between microscopic mechanics and macroscopic thermodynamics. The Boltzmann distribution, the partition function, and the path to quantum statistics.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Understand)** State the fundamental postulate of statistical mechanics and use it to derive the Boltzmann distribution.
2. **(Apply)** Compute the partition function $Z$ for simple systems and use it to find average energy, free energy, and entropy.
3. **(Apply)** Apply the two-level-system formulas to find the Schottky anomaly in heat capacity.
4. **(Analyze)** Recognize when Boltzmann statistics apply and when quantum statistics (Fermi-Dirac or Bose-Einstein) are needed.
5. **(Apply)** Compute the classical-limit of quantum statistics and recover Maxwell-Boltzmann.
6. **(Apply)** Build a Boltzmann-distribution and partition-function explorer.

---

## Opening case: spins in a magnetic field

Imagine a system of $N$ magnetic atoms, each carrying a spin-1/2 magnetic moment $\mu$. Place them in an external magnetic field $B$. Each atom can be in one of two states: spin "up" (aligned with the field, energy $-\mu B$) or spin "down" (anti-aligned, energy $+\mu B$).

At very low temperature ($k_BT \ll \mu B$): nearly all atoms in the lower-energy "up" state. Strongly magnetized.

At very high temperature ($k_BT \gg \mu B$): equal occupation of both states. No net magnetization.

At intermediate temperature ($k_BT \sim \mu B$): partial polarization. The system's *heat capacity* peaks here — a small temperature change produces a large population change, requiring lots of energy input. This is the **Schottky anomaly**.

This single example contains the full apparatus of statistical mechanics: the Boltzmann distribution, the partition function, average energy, and heat capacity — all derivable from one postulate and a few lines of algebra. The chapter ahead lays out the framework.

---

## Core concept

### The fundamental postulate

In thermodynamic equilibrium, **all microstates of equal energy are equally probable**.

A *microstate* is the complete specification of the system at the microscopic level — every particle's position and momentum, every spin's orientation, every quantum state's occupation. A *macrostate* is specified by macroscopic variables (energy, temperature, pressure, etc.). Many microstates correspond to one macrostate.

Equilibrium = the system samples all accessible microstates (ergodically). Statistical mechanics is the math of "sample uniformly over accessible microstates."

### The Boltzmann distribution

For a small system $S$ in thermal contact with a large reservoir at temperature $T$, the probability of system state $i$ (with energy $E_i$) is

$$P_i = \frac{e^{-E_i/k_BT}}{Z}$$

where the **partition function** is

$$Z = \sum_i e^{-E_i/k_BT}$$

(For degenerate energy levels with degeneracy $g_i$: $Z = \sum_i g_i e^{-E_i/k_BT}$.)

**Derivation sketch.** From the fundamental postulate applied to the combined system + reservoir: $P_i \propto \Omega_{\text{res}}(E_{\text{total}} - E_i)$. Expand $\ln\Omega_{\text{res}}$ around $E_{\text{total}}$, identify the reservoir temperature as $1/k_BT = (\partial \ln\Omega_{\text{res}}/\partial E)$. The result is the Boltzmann form.

**Alternative derivation:** maximize entropy $S = -k_B \sum_i p_i \ln p_i$ subject to constraints $\sum p_i = 1$ and $\sum p_i E_i = \langle E\rangle$. Lagrange multipliers give the same answer.

**Source:** Boltzmann (1877) for the kinetic-theory case; Gibbs (1902) for the general formulation.

### The partition function: master object

Once you have $Z(T)$ for your system, you have everything:

**Average energy:** $\langle E\rangle = -\partial \ln Z/\partial \beta = k_BT^2 \partial \ln Z/\partial T$, where $\beta = 1/k_BT$.

**Helmholtz free energy:** $F = -k_BT \ln Z$.

**Entropy:** $S = -\partial F/\partial T = k_B(\ln Z + \beta\langle E\rangle)$.

**Heat capacity (from energy fluctuations):** $C_v = \partial\langle E\rangle/\partial T = (\langle E^2\rangle - \langle E\rangle^2)/(k_BT^2)$.

This last identity is the fluctuation-dissipation theorem: heat capacity (a response) equals energy fluctuations (a property of the equilibrium ensemble). At the heart of linear response theory in statistical mechanics.

### The two-level system

Energy levels: $E_0 = 0$ and $E_1 = \varepsilon > 0$. Partition function:
$$Z = 1 + e^{-\beta\varepsilon}$$

Probabilities:
$$P_0 = \frac{1}{1 + e^{-\beta\varepsilon}}, \quad P_1 = \frac{e^{-\beta\varepsilon}}{1 + e^{-\beta\varepsilon}}$$

Average energy:
$$\langle E\rangle = \varepsilon P_1 = \frac{\varepsilon}{e^{\beta\varepsilon} + 1}$$

Heat capacity (per atom):
$$C_v = \frac{d\langle E\rangle}{dT} = k_B \left(\frac{\varepsilon/k_BT}{1 + e^{-\varepsilon/k_BT}}\right)^2 \cdot e^{-\varepsilon/k_BT} \cdot \frac{e^{-\varepsilon/k_BT}}{...}$$

Skip the algebra: the result is a curve peaking at $k_BT \sim \varepsilon/2.4$. The **Schottky anomaly** — heat capacity rises from 0 at low $T$, reaches a maximum, then decreases at high $T$.

**Physical interpretation:**
- Low $T$ ($k_BT \ll \varepsilon$): nearly all atoms in ground state; adding heat doesn't change population (states are inaccessible); low heat capacity.
- High $T$ ($k_BT \gg \varepsilon$): populations are nearly equal (50-50); adding heat barely changes them; low heat capacity.
- Intermediate $T$ ($k_BT \sim \varepsilon$): small temperature changes produce large population shifts; high heat capacity.

The Schottky anomaly is observable in real systems — spin glasses, defect states, magnetic transitions — confirming the statistical-mechanics prediction.

### The classical limit and Maxwell-Boltzmann recovery

For an ideal gas, the energy spectrum is essentially continuous (each particle has $\sim 10^{20}$ accessible momentum states at room temperature). The partition function for one particle:
$$Z_1 = \frac{V}{h^3} \int d^3p \, e^{-p^2/(2mk_BT)} = V \left(\frac{m k_BT}{2\pi\hbar^2}\right)^{3/2}$$

The Maxwell-Boltzmann speed distribution falls out by computing the probability of various speeds. The factor of $4\pi v^2$ comes from the volume element in spherical coordinates in momentum space.

For $N$ identical (classical, distinguishable) particles: $Z = Z_1^N/N!$ (divide by $N!$ because particles are indistinguishable in the macroscopic limit).

Average energy: $\langle E\rangle = (3/2)Nk_BT$ — equipartition recovered.

The classical-Boltzmann picture *is* the high-temperature, low-density limit of the more general quantum statistics.

### Quantum statistics (preview)

Identical quantum particles obey different statistics depending on whether they're fermions or bosons.

**Fermions** (electrons, protons, neutrons — half-integer spin): obey the Pauli exclusion principle. Each single-particle state can hold *at most one* particle. The **Fermi-Dirac distribution**:

$$f_{\text{FD}}(E) = \frac{1}{e^{(E-\mu)/k_BT} + 1}$$

where $\mu$ is the chemical potential. At low temperatures, $f \approx 1$ for $E < \mu$ (filled states) and $f \approx 0$ for $E > \mu$ (empty). $\mu(T = 0)$ is the **Fermi energy**.

Used for:
- Electrons in metals (predicts heat capacity $\propto T$, much smaller than equipartition $\propto T$ predicts classically).
- Electrons in semiconductors.
- White dwarf stars (electron degeneracy pressure).
- Neutron stars (neutron degeneracy pressure).

**Bosons** (photons, He-4 atoms, mesons — integer spin): no exclusion. Arbitrarily many bosons can occupy one state. The **Bose-Einstein distribution**:

$$f_{\text{BE}}(E) = \frac{1}{e^{(E-\mu)/k_BT} - 1}$$

Used for:
- Photons (Planck's blackbody radiation).
- He-4 atoms (superfluidity below 2.2 K).
- Bose-Einstein condensates of cold atoms (Cornell, Wieman, Ketterle Nobel 2001).

**Classical limit:** when $e^{-(E-\mu)/k_BT} \ll 1$ (high $T$, low density), both quantum distributions reduce to the Boltzmann form $\propto e^{-E/k_BT}$. This is the regime of ordinary gases at room temperature.

---

## Worked example: ideal gas partition function and equipartition

Compute $\langle E\rangle$ for a single particle in 3D, with energy $E = p^2/(2m)$.

**Setup.** Particle has continuous momentum states. Partition function:
$$Z_1 = \int \frac{d^3p}{h^3} V e^{-p^2/(2mk_BT)} = \frac{V}{h^3} \left[\int_{-\infty}^{\infty} e^{-p_x^2/(2mk_BT)} dp_x\right]^3 = \frac{V}{h^3}(2\pi m k_BT)^{3/2}$$

**Average energy.** Using $\langle E\rangle = -\partial \ln Z_1/\partial \beta$ with $\beta = 1/k_BT$:
$$\ln Z_1 = \ln V - 3\ln h + (3/2)\ln(2\pi m/\beta)$$
$$\frac{\partial \ln Z_1}{\partial \beta} = -\frac{3}{2\beta}$$
$$\langle E\rangle = \frac{3}{2}k_BT$$

Equipartition recovered: each of the three translational degrees of freedom contributes $(1/2)k_BT$.

**For $N$ particles:** $\langle E\rangle = (3/2)Nk_BT$, total internal energy $U = (3/2)Nk_BT$.

**Heat capacity:** $C_V = \partial U/\partial T = (3/2)Nk_B$.

**The lesson.** The partition function is a unifying object. From it, you derive thermodynamic quantities by differentiation. The ideal-gas result is the simplest case; the same machinery handles much more complex systems.

**The limit.** The $1/h^3$ factor in $Z_1$ is the classical *phase-space cell size* — equivalent to dividing by quantum-mechanical state count. The $1/N!$ factor for $N$ particles handles indistinguishability (Gibbs paradox). For *truly* quantum particles (cold, dense, or fermions/bosons), the corrections matter and the classical result fails.

---

## Common misconceptions

**"The Boltzmann distribution says only low-energy states are occupied."** They're occupied with *higher probability*. Higher-energy states are occupied with probability $e^{-(E - E_0)/k_BT}$ — not zero, but exponentially suppressed.

**"Statistical mechanics is an approximation to thermodynamics."** For systems with $N \to \infty$, statistical mechanics gives *exact* thermodynamic results. Fluctuations are $\propto 1/\sqrt{N}$, so they're negligible for thermodynamic-scale systems. Statistical mechanics generates thermodynamics; it doesn't approximate it.

**"$\mu$ in Fermi-Dirac and Bose-Einstein is temperature."** It's the *chemical potential*, defined by $\mu = \partial F/\partial N$. At $T = 0$, $\mu_{FD} =$ Fermi energy. For photons, $\mu = 0$ always (photon number isn't conserved). Distinct from temperature.

**"Quantum statistics only matter at very low temperatures."** They matter whenever the de Broglie wavelength of particles is comparable to or larger than the interparticle spacing. For atoms at room temperature: $\lambda_{dB} \sim$ angstroms; interparticle spacing $\sim$ tens of angstroms; quantum effects small. For electrons in a metal at room temperature: $\lambda_{dB} \sim$ ångströms; spacing $\sim$ ångströms; quantum effects *huge*. The criterion is comparison of $\lambda_{dB}$ to $n^{-1/3}$, not absolute temperature.

---

## Exercises

**Warm-up (Apply).** Two-level system: $E_0 = 0$, $E_1 = 0.01$ eV. Find occupation probabilities at $T = 100$ K, 300 K, 1000 K.

**Apply.** Find the temperature at which the Schottky anomaly heat capacity peaks for a two-level system with $\varepsilon = 0.005$ eV. (Hint: the peak is at $k_BT \approx 0.4\varepsilon$.)

**Apply.** A harmonic oscillator has energy levels $E_n = (n + 1/2)\hbar\omega$, $n = 0, 1, 2, ...$. Compute $Z$ as a geometric series. Find $\langle E\rangle$. Show that for $k_BT \gg \hbar\omega$, $\langle E\rangle \to k_BT$ (equipartition).

**Apply + Analyze.** Compute $C_V$ for the harmonic oscillator. Show that $C_V \to k_B$ at high $T$ but $C_V \to 0$ at low $T$. (This is why vibrational modes "freeze out" at low temperatures — Einstein's 1907 result.)

**Apply (Fermi-Dirac).** Electron in a metal at $T = 300$ K, Fermi energy $E_F = 5$ eV. (a) What's the probability of an electron state at $E = E_F - 0.1$ eV being occupied? (b) At $E = E_F + 0.1$ eV?

**Challenge.** Derive $\langle E\rangle = -\partial \ln Z/\partial\beta$ starting from the definition $\langle E\rangle = \sum_i p_i E_i$ and the Boltzmann distribution $p_i = e^{-\beta E_i}/Z$.

---

## LLM Exercises

### Build the Boltzmann-distribution explorer (`08-boltzmann-distribution.html`)

> **Show.** Boltzmann distribution: $P_i = e^{-E_i/k_BT}/Z$, $Z = \sum e^{-E_i/k_BT}$. Average energy $\langle E\rangle$, heat capacity $C_v = (\langle E^2\rangle - \langle E\rangle^2)/(k_BT^2)$.
>
> **Say.** Build a Boltzmann-distribution and partition-function explorer.
>
> **Constrain.** D3 v7. Controls: number of energy levels $N_{\text{levels}}$ (slider 2–10), energy spacing $\Delta E$ (in units of $k_B$ — so $\Delta E = 1$ means $\varepsilon = k_B$ which corresponds to $T_{\text{anomaly}} \sim 1$ K), temperature $T$ (slider 0.1 to 100). Display: energy level diagram with occupation probability shown as bar width at each level; $Z$ computed; $\langle E\rangle$ vs. $T$ curve; $C_v$ vs. $T$ curve showing Schottky peak. Filename: `08-boltzmann-distribution.html`.
>
> **Verify.** (a) Two-level system: $C_v$ peaks at $k_BT \approx 0.4\varepsilon$. (b) As $T \to 0$, all probability concentrates in the ground state. (c) As $T \to \infty$, occupation is nearly uniform.

### Exploration

- Watch the Schottky peak emerge as you vary $\Delta E$ for a two-level system. The peak's location in $T$ is proportional to $\Delta E$.
- For an N-level system (e.g., 10 levels), look at how $\langle E\rangle$ grows: nearly linear in $T$ for $k_BT > \Delta E$ (classical equipartition), but with quantum corrections at low $T$.
- Compare a two-level system (single Schottky peak) to a 5-level system. The 5-level system's heat capacity is broader and has no single sharp peak.

### Extension prompt (chapter bridge)

> **Show.** Statistical mechanics gives me the partition function. I can now compute equilibrium thermodynamic quantities. But real engines operate out of equilibrium — irreversibly. Where do these losses come from?
>
> **Say.** Build a heat-engine simulator showing how real-engine irreversibility costs efficiency.
>
> **Constrain.** Display a thermodynamic cycle (Rankine, Brayton, etc.) with adjustable irreversibility parameters: finite $\Delta T$ at heat exchangers, isentropic efficiency of turbines and compressors. Compute the actual cycle efficiency and entropy generation rate.
>
> **Verify.** As irreversibilities increase, efficiency drops below Carnot bound; entropy generation rises.

Save as `08b-real-engine-preview.html`. Bridge to Chapter 9.

---

## What would change my mind

The Boltzmann distribution and partition function framework are exact in thermodynamic equilibrium. They've been confirmed in every measurement of thermal systems for over a century. Quantum statistics (FD, BE) are likewise verified for systems where they apply (metals, semiconductors, superfluids, BEC). A confirmed deviation in a system clearly in equilibrium would force the deepest possible revision of physics — none has occurred.

What's contested: extensions to *non-equilibrium* systems (especially small ones with large fluctuations). Stochastic thermodynamics (Jarzynski equality, Crooks theorem, fluctuation theorems) is the modern frontier — they extend equilibrium statistical mechanics with specific care.

## Still puzzling

- *Why does $S = k_B \ln \Omega$?* Boltzmann's derivation is consistent with thermodynamics, but the factor of $k_B$ is somewhat arbitrary — it converts between "natural" units of entropy (log of microstates, dimensionless) and joules/kelvin. The choice of $k_B$ makes Boltzmann entropy agree with Clausius entropy.
- *What's the right entropy for a quantum system?* For systems in pure quantum states, $S = -k_B \text{Tr}(\rho \ln \rho)$ (von Neumann). For mixed states, this generalizes Boltzmann. For entangled states, $S$ is *non-additive* — the entropy of two entangled subsystems isn't the sum of subsystem entropies. Chapter 10 develops this.
- *The ergodic hypothesis.* The fundamental postulate says all microstates are equally probable. This requires the system to *sample* all of them, which is what the ergodic hypothesis asserts. Non-ergodic systems (glasses, gravitational systems) violate this; they're an active research area.

---

**Tags:** statistical mechanics, fundamental postulate, Boltzmann distribution, partition function, Helmholtz free energy, Schottky anomaly, classical limit, Fermi-Dirac distribution, Bose-Einstein distribution, equipartition

