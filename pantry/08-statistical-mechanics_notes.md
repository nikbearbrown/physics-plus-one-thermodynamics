# Research Notes: Chapter 08 — Statistical Mechanics

**Source:** TIKTOC.md chapter entry (Chapter 08)
**Notes file:** 08-statistical-mechanics_notes.md
**Corresponding chapter:** chapters/08-statistical-mechanics.md (not yet written)
**Generated:** 2026-05-14

---

## Chapter summary (from TIKTOC.md)

Statistical mechanics is the bridge between microscopic physics and macroscopic thermodynamics. The chapter derives the Boltzmann distribution from maximum entropy. The partition function $Z = \sum e^{-E_i/k_B T}$ encodes all thermodynamic information. Average energy, heat capacity, and entropy are computed from $Z$. Quantum statistics (Fermi-Dirac, Bose-Einstein) appear as the bridge to the QM volume.

---

## A. Conceptual foundations

### The fundamental postulate

In thermodynamic equilibrium, **all microstates of equal energy are equally probable**. This is the bedrock assumption from which everything else follows.

A *microstate* is the complete specification of every particle's position and momentum (or every spin's orientation, every quantum state's occupation, etc.). A *macrostate* is specified by macroscopic variables like temperature, pressure, volume, energy. Many microstates correspond to one macrostate.

The fundamental postulate says: given fixed total energy, all microstates with that energy are sampled equally over time (ergodic hypothesis), or equivalently, sampling at one instant equally.

### Deriving the Boltzmann distribution

Consider a small system $S$ in thermal contact with a much larger reservoir $R$. Total energy is fixed; the system's energy $E_i$ can vary. Number of microstates of the reservoir at energy $E_{\text{tot}} - E_i$: $\Omega_R(E_{\text{tot}} - E_i)$.

By the fundamental postulate, the probability of system state $i$ is proportional to the number of reservoir microstates that allow it:
$$P_i \propto \Omega_R(E_{\text{tot}} - E_i)$$

For a large reservoir, expand the log of $\Omega_R$:
$$\ln \Omega_R(E_{\text{tot}} - E_i) \approx \ln \Omega_R(E_{\text{tot}}) - \frac{\partial \ln \Omega_R}{\partial E} \cdot E_i$$

The reservoir's temperature is defined as $1/T = k_B (\partial \ln \Omega_R / \partial E)$. So:
$$P_i \propto e^{-E_i/(k_B T)}$$

Normalizing: $P_i = e^{-E_i/(k_B T)} / Z$, where the **partition function** is
$$Z = \sum_i e^{-E_i/(k_B T)}$$

Alternatively, derive Boltzmann by maximizing entropy $S = -k_B \sum p_i \ln p_i$ subject to $\sum p_i = 1$ and $\sum p_i E_i = \langle E \rangle$. Lagrange multipliers give exactly the Boltzmann form.

**Common misconception:** that "Boltzmann distribution" only applies to ideal gases. It applies to *any* system in thermal contact with a reservoir — atoms in a magnetic field, molecules in a chemical equilibrium, photons in a cavity, vibrational modes of a solid.

### The partition function: master object of statistical mechanics

Once you know $Z(T, V, N)$, you know all macroscopic thermodynamic quantities:

**Average energy:**
$$\langle E \rangle = -\frac{\partial \ln Z}{\partial \beta} \quad \text{where } \beta = 1/k_B T$$

**Helmholtz free energy:**
$$F = -k_B T \ln Z$$

**Entropy:**
$$S = -\frac{\partial F}{\partial T} = k_B(\ln Z + \beta \langle E \rangle)$$

Heat capacity follows from the energy fluctuation formula:
$$C_v = \frac{\partial \langle E \rangle}{\partial T} = \frac{\langle E^2 \rangle - \langle E \rangle^2}{k_B T^2}$$

This is the central result of statistical mechanics: the *fluctuations* of energy are connected to the *response* (heat capacity). Linear response theory generalizes this — it's the basis of the fluctuation-dissipation theorem.

### Worked: two-level system

A system has just two energy levels: $E_0 = 0$ and $E_1 = \varepsilon$. Boltzmann probabilities:
$$P_0 = \frac{1}{1 + e^{-\beta\varepsilon}}, \quad P_1 = \frac{e^{-\beta\varepsilon}}{1 + e^{-\beta\varepsilon}}$$

Partition function: $Z = 1 + e^{-\beta\varepsilon}$.

Average energy: $\langle E \rangle = \varepsilon P_1 = \varepsilon/(e^{\beta\varepsilon} + 1)$.

Heat capacity: derivative of $\langle E \rangle$ with respect to $T$ gives a curve that *peaks* at a temperature where $k_B T \sim \varepsilon$. This **Schottky anomaly** is observable in real systems: spin glasses, defect states, magnetic salts.

The peak occurs because:
- At $k_B T \ll \varepsilon$: almost all atoms in ground state; adding energy doesn't change populations.
- At $k_B T \gg \varepsilon$: populations saturate at 50/50; adding energy doesn't change them either.
- At $k_B T \sim \varepsilon$: small changes in $T$ produce large changes in population; high heat capacity.

### Quantum statistics (preview)

For *distinguishable* particles, Boltzmann statistics apply directly. For *identical* quantum particles:

- **Fermions** (electrons, protons, neutrons — half-integer spin): obey the Pauli exclusion principle. Each state can hold at most one particle. **Fermi-Dirac distribution:**
$$f_{\text{FD}}(E) = \frac{1}{e^{(E-\mu)/k_B T} + 1}$$
Used for electrons in metals, semiconductors, white dwarfs, neutron stars.

- **Bosons** (photons, He-4 atoms, mesons — integer spin): no exclusion; arbitrarily many bosons can occupy one state. **Bose-Einstein distribution:**
$$f_{\text{BE}}(E) = \frac{1}{e^{(E-\mu)/k_B T} - 1}$$
Used for photons (blackbody radiation), He-4 (superfluidity), Bose-Einstein condensates.

In the *classical limit* — when occupation numbers are much less than 1 — both quantum distributions reduce to the Boltzmann form. The classical limit applies at low density / high temperature.

**Common misconception:** that quantum statistics "are a correction to classical statistics." They are the *fundamental* distributions for identical particles; the classical Boltzmann distribution is the *high-temperature/low-density limit*.

---

## B. Domain examples and cases

### Case 1: Bose-Einstein condensation
At sufficiently low temperatures, bosons "condense" into the ground state in macroscopic numbers. First experimental realization: Cornell, Wieman (rubidium-87 at 170 nK), and Ketterle (sodium) in 1995. Nobel Prize 2001.

The chemical potential $\mu$ approaches zero from below; at $\mu = 0$, the ground state acquires macroscopic occupation. Below the condensation temperature, the system has two components: the condensate (a single macroscopic quantum state) and thermal excitations.

### Case 2: Specific heat of metals
The electronic contribution to heat capacity in a metal is $C_v^{el} = (\pi^2/2)(k_B T/T_F) N k_B$ — much smaller than the classical equipartition prediction $C_v^{cl} = (3/2)Nk_B$ at room temperature, because $T \ll T_F$ (Fermi temperature, typically $\sim 10^4$ K for typical metals).

Sommerfeld 1928 derived this from Fermi-Dirac statistics, finally explaining why the equipartition theorem fails for metals' electron gas.

### Case 3: Einstein and Debye models of solid heat capacity
The Einstein model (1907) treats each atom in a solid as a quantum harmonic oscillator. The heat capacity drops below the classical Dulong-Petit value of $3Nk_B$ at low temperatures, in agreement with experiment. Debye (1912) refined this with a distribution of vibrational frequencies, giving the famous $T^3$ low-temperature behavior of crystalline solids.

### Failure case: classical equipartition for blackbody
Apply classical statistical mechanics to electromagnetic radiation in a cavity: each mode of frequency $\nu$ should have energy $k_B T$ (equipartition). Sum over all modes: the energy density diverges as $\nu \to \infty$ (the "ultraviolet catastrophe"). Real blackbodies don't show this divergence; their spectrum is finite.

Planck's 1900 resolution: quantize the energy of each mode in units of $h\nu$. The partition function for a single mode becomes a geometric series; the average energy is $h\nu/(e^{h\nu/k_BT} - 1)$ — small for high $\nu$. This is the Planck distribution; the ultraviolet catastrophe disappears.

The classical-physics failure forced quantization. Statistical mechanics is the natural bridge between the classical and quantum descriptions.

---

## C. Connections and dependencies

**Prerequisites:** Probability and counting (combinatorics), calculus (derivatives, exponentials), Ch 7 (entropy as $k_B \ln \Omega$).

**Unlocks:** Ch 10 (information-theoretic and quantum extensions); the QM volume (partition function in quantum form).

**Adjacent chapter connections:**
- Ch 7: Boltzmann entropy is the starting point.
- Ch 9: real-device applications.

---

## D. Current state of the field

**Settled:**
- Boltzmann distribution from maximum entropy.
- Partition function as the master object.
- Classical limit of quantum statistics.
- Fluctuation-dissipation relations at the linear-response level.

**Contested or emerging:**
- Quantum thermodynamics frontier: how do thermodynamic laws extend to coherent quantum systems?
- Generalized statistical mechanics (Tsallis, Renyi entropies) — extensions to non-extensive systems. Some controversy; mainstream physics still uses Boltzmann-Gibbs.
- Stochastic thermodynamics: the thermodynamics of small systems where fluctuations are large. Jarzynski equality, Crooks theorem.

**Key references:**
1. Kittel & Kroemer, *Thermal Physics* — the standard undergraduate text.
2. Reif, *Fundamentals of Statistical and Thermal Physics* — somewhat older but excellent.
3. Mandl, *Statistical Physics* — accessible.
4. Landau & Lifshitz, *Statistical Physics* Vol. 5 — graduate-level definitive treatment.

**Recent developments:**
- Quantum simulators (cold-atom systems, trapped ions) directly test statistical mechanics predictions.
- Stochastic thermodynamics has become a mature subfield (Seifert 2012 review).

---

## E. Teaching considerations

**Where students get stuck:**
- The transition from microscopic to macroscopic feels abstract. Worked examples with small systems (2-level, 3-level, harmonic oscillator) help.
- Partition function — students often see it as a definition rather than a *useful computational object*. Emphasizing "$Z$ encodes everything" helps.
- Quantum statistics — students need to see why the classical Boltzmann form is the high-T limit of both quantum distributions.

**Analogies and framings that work:**
- *"Boltzmann distribution: the universe's probability function."* Anchors the central role.
- *"$Z$ is a transform of the energy spectrum; the spectrum and $Z$ contain the same information."*
- *"At high T, all states look equally probable; at low T, only the ground state matters."*

**Exercises that build the target skill:**
- *Two-level Schottky peak* (Bloom: Apply) — compute $\langle E\rangle$, $C_v$ vs. $T$; identify peak.
- *Diatomic gas heat capacity vs. T* (Bloom: Analyze) — rotational modes activate at $T \gtrsim 10$ K; vibrational at $T \gtrsim 3000$ K. Quantum effects visible.
- *Derive Maxwell-Boltzmann from Boltzmann distribution applied to translational energy* (Bloom: Synthesize) — recovers Ch 3 result.

---

## F. Library files relevant to this chapter
None.

---

## G. Gaps and flags

- FLAG: Notational conventions vary. Some texts use $\beta = 1/k_B T$ throughout; others $1/T$ (with $k_B$ absorbed). Pick one and stick with it.
- FLAG: Quantum statistics preview should *not* derive Fermi-Dirac and Bose-Einstein from scratch; just state the formulas and explain their physical content. Full derivation belongs to the QM volume.
- GAP: The chapter should mention the canonical, microcanonical, and grand canonical ensembles briefly but not develop them all — the canonical (fixed $T, V, N$) is the standard intro framework.
