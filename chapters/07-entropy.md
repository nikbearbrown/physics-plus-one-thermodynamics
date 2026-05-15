# Chapter 7 — Entropy

*Clausius defined it as $dS = \delta Q/T$. Boltzmann defined it as $S = k_B \ln \Omega$. They are the same quantity.*

---

## Learning objectives

By the end of this chapter you will be able to:

1. **(Apply)** Use the Clausius definition $dS = \delta Q_{\text{rev}}/T$ to compute entropy changes for reversible processes.
2. **(Apply)** Use the Boltzmann definition $S = k_B \ln \Omega$ to compute entropy from the count of microstates.
3. **(Analyze)** Apply $\Delta S_{\text{universe}} \geq 0$ as the entropy form of the second law to predict process directions.
4. **(Apply)** Compute entropy changes for standard processes (isothermal, isochoric, isobaric, adiabatic, free expansion, heat conduction).
5. **(Understand)** State the third law and its implications for cooling toward absolute zero.
6. **(Apply)** Build a microstate-counting simulator showing the second law emerging from probability.

---

## Opening case: why the cream stays mixed

Pour cream into hot coffee. Stir. The cream mixes throughout. Wait. The cream never spontaneously *un-mixes* — separating itself back into a layer at the top — even though nothing in Newton's laws forbids it.

Newton's laws are *time-symmetric*. If you played a movie of mixing in reverse, every particle would follow valid Newtonian trajectories. The reverse motion is *physically allowed*, but you've never seen it. Why?

The answer is statistical, not mechanical. There are *vastly more microstates* corresponding to "mixed cream" than to "cream on top." For a few hundred cream molecules and coffee molecules, the ratio of mixed to separated configurations is already enormous. For a real cup, $\Omega_{\text{mixed}}/\Omega_{\text{separated}} \gg 10^{10^{20}}$. The probability of spontaneous un-mixing is so small that, on cosmological timescales, you'd never see it.

The second law is *statistical*: not "thou shalt not un-mix" but "of the $\Omega_{\text{total}}$ accessible microstates, only a vanishing fraction looks 'un-mixed,' so we never see it." Entropy is the *log of the number of microstates*. The second law is the statement that systems evolve toward states with more microstates — toward higher entropy.

This chapter develops entropy from two angles. Clausius's macroscopic definition uses heat divided by temperature. Boltzmann's microscopic definition uses microstate counting. They give the *same answer* — that they agree is the deepest result in classical thermodynamics, and the bridge to statistical mechanics (Chapter 8).

---

## Core concept

### The Clausius definition of entropy

For a reversible infinitesimal heat exchange $\delta Q_{\text{rev}}$ at temperature $T$:

$$dS = \frac{\delta Q_{\text{rev}}}{T}$$

For a finite reversible process from state A to state B:

$$\Delta S_{A \to B} = \int_A^B \frac{\delta Q_{\text{rev}}}{T}$$

**Units:** joules per kelvin (J/K).

**Crucial property:** entropy is a *state function*. $\Delta S$ depends only on the initial and final states, not on the path taken — *even if the actual process is irreversible*. You compute $\Delta S$ by finding *any reversible path* between the same endpoints and integrating $\delta Q/T$ along that path.

### Entropy changes for standard processes

**Isothermal process** (ideal gas): $Q = W = nRT \ln(V_f/V_i)$. So
$$\Delta S = Q/T = nR \ln(V_f/V_i)$$

**Isochoric heating** (ideal gas): $\Delta U = nC_V dT = \delta Q$. So $\delta Q/T = nC_V dT/T$. Integrate:
$$\Delta S = nC_V \ln(T_f/T_i)$$

**Isobaric heating** (ideal gas): $\delta Q = nC_P dT$. Integrate:
$$\Delta S = nC_P \ln(T_f/T_i)$$

**Reversible adiabatic** (isentropic): $\delta Q = 0$, so $\Delta S = 0$. The adiabatic curve is also called an *isentrope*.

**Free expansion** (irreversible): a gas expands into vacuum. No work done ($W = 0$), no heat exchanged ($Q = 0$), no temperature change for ideal gas ($\Delta U = 0$). To compute $\Delta S$, find a reversible path between the same endpoints — an isothermal expansion gives $\Delta S = nR \ln(V_f/V_i) > 0$. Free expansion has *positive* entropy change despite $Q = 0$.

The free-expansion case shows why "entropy is heat divided by temperature" is incomplete — you must specify a reversible path, not just compute $\delta Q/T$ along the actual irreversible path.

### The second law in entropy form

For any process:
$$\Delta S_{\text{universe}} = \Delta S_{\text{system}} + \Delta S_{\text{surroundings}} \geq 0$$

- Equality holds for reversible processes.
- Strict inequality for irreversible processes.

This is the most useful form of the second law. It governs all spontaneous processes: $\Delta S_{\text{universe}}$ must increase (or stay the same).

**Example: heat conduction.** Heat $Q$ flows from hot reservoir at $T_H$ to cold reservoir at $T_C$. Hot loses entropy $\Delta S_H = -Q/T_H$. Cold gains $\Delta S_C = +Q/T_C$. Net: $\Delta S_{\text{universe}} = Q(1/T_C - 1/T_H) > 0$ (since $T_H > T_C$). Spontaneous, irreversible.

What if we tried to make heat flow the other way (cold to hot)? Net $\Delta S$ would be negative. Forbidden by the second law.

### Boltzmann's entropy: $S = k_B \ln \Omega$

For an isolated system in equilibrium, the entropy is

$$S = k_B \ln \Omega$$

where $\Omega$ is the number of microstates accessible to the system at the given energy.

**Boltzmann's tombstone equation** — the inscription on his Vienna tomb reads "$S = k \ln W$" (with $W$ standing for $\Omega$).

**Why this is the same entropy as Clausius's:** for a system in thermal contact with a reservoir, the Boltzmann definition gives exactly the same $\Delta S$ as the Clausius definition for any process. Chapter 8 proves this from the Boltzmann distribution and the partition function.

### Simple microstate counting

**Example: gas in two halves of a box.** $N$ particles distributed between left and right halves. Each particle has 2 possible "states" (left or right). Total microstates: $\Omega_{\text{total}} = 2^N$.

The macrostate "$n$ particles on left" has $\Omega(n) = \binom{N}{n} = N!/(n!(N-n)!)$ microstates.

The most probable macrostate is $n = N/2$ (uniformly distributed). For $N = 100$: $\Omega(50) = \binom{100}{50} \approx 10^{29}$. The macrostate $n = 100$ (all particles on left): $\Omega(100) = 1$. Ratio: $10^{29}$. The system spends essentially all its time near $n = N/2$.

**Entropy of the most probable macrostate:** $S = k_B \ln \Omega(N/2) \approx k_B (N \ln 2 - \frac{1}{2}\ln(\pi N/2))$ (Stirling's approximation). For $N$ large: $S \approx N k_B \ln 2$, almost exactly the entropy of mixing.

### Why Ω overwhelmingly favors disorder

For a 1-mole system ($N = N_A \approx 6 \times 10^{23}$): $\Omega(N_A/2)$ is astronomical; $\Omega(\text{all on left})$ is exactly 1. The ratio is $\sim e^{N_A \ln 2}$ — beyond imagination. The system spends essentially all its time near the most probable macrostate.

The second law isn't a *fundamental prohibition* on un-mixing or backward processes. It's the *statistical observation* that, with $10^{23}$ particles, the probability of seeing anything other than maximum-entropy states is effectively zero.

For small $N$ (a few particles), entropy fluctuations are large. For thermodynamic-scale $N$ ($\sim 10^{20}$+), they're invisible.

### The third law of thermodynamics

As $T \to 0$, the entropy of a system approaches a constant (the same constant for all pure systems):

$$\lim_{T \to 0} S = 0$$

Why: at $T = 0$, only the lowest-energy state(s) are occupied. For a non-degenerate ground state, $\Omega = 1$ and $S = k_B \ln 1 = 0$. For degenerate ground states, $\Omega > 1$ and $S > 0$, but the entropy is still bounded.

**Implications:**
- Absolute entropy: $S(T) = \int_0^T \delta Q_{\text{rev}}/T'$ is well-defined (not just $\Delta S$).
- Approaching $T = 0$ requires infinitely many steps (Nernst's theorem). You can get arbitrarily close to 0 K, but you can't reach it in finite time.

**Source:** Nernst (1906). Connects classical thermodynamics to quantum mechanics (the ground state has $S = 0$ because there's only one of it).

### Entropy and the arrow of time

The second law gives time an arrow: spontaneous processes go in the direction of increasing entropy. This is the only fundamental law in classical physics that distinguishes past from future.

Mechanics (Newtonian and quantum) is time-symmetric. The thermodynamic arrow comes from *initial conditions* — the universe started in an unusual low-entropy state, and is statistically evolving toward maximum entropy.

This is profound: the *direction* of time is encoded in our universe's initial conditions, not in its dynamical laws. The cosmological reason for low initial entropy is one of the deepest open questions in physics.

---

## Worked example: free expansion

1 mol of ideal gas expands into a vacuum, doubling its volume. Find $\Delta S$.

**Direct computation impossible.** The actual process is irreversible (free expansion). $Q = 0$, $W = 0$. We *can't* directly compute $\Delta S = \int \delta Q/T$ — the path is irreversible.

**But $\Delta S$ is a state function.** Find a *reversible* path between the same initial and final states.

A reversible isothermal expansion of the gas: same initial state (1 mol at $T$, $V$), same final state (1 mol at $T$, $2V$). For isothermal expansion: $Q_{\text{rev}} = nRT \ln(V_f/V_i) = R T \ln 2$.

So $\Delta S = Q_{\text{rev}}/T = R \ln 2 \approx 8.314 \cdot 0.693 = 5.76$ J/K.

**Check via Boltzmann.** The state of the gas is specified by particle positions. Each particle now has access to twice the volume. For $N$ particles, $\Omega$ doubles for each: $\Omega_f = \Omega_i \cdot 2^N = \Omega_i \cdot 2^{N_A}$.

$\Delta S = k_B \ln(\Omega_f/\Omega_i) = N_A k_B \ln 2 = R \ln 2 \approx 5.76$ J/K. ✓

**The lesson.** The two definitions agree exactly. Clausius and Boltzmann describe the same quantity.

**The limit.** This calculation assumed ideal gas. For real gases (with intermolecular forces), $\Delta U \neq 0$ in free expansion, and the calculation requires care.

---

## Common misconceptions

**"Entropy is disorder."** "Disorder" is a useful but loose analogy. Entropy is the logarithm of the number of accessible microstates. A liquid crystal — which looks "ordered" — can have more entropy than its disordered analogue if it has more accessible vibrational modes. Don't equate entropy with how it "looks."

**"Entropy always increases everywhere."** Only the *total* entropy of the universe increases. *Local* entropy can decrease (refrigerators, organisms, crystal growth) at the cost of larger entropy increases elsewhere (work input, heat exhaust, environment).

**"Reversible processes don't change entropy."** They don't change the entropy of the *universe* (zero net change). But the system's entropy can change; the surroundings's entropy changes by an equal and opposite amount. Total: zero.

**"Entropy is heat divided by temperature."** Only for reversible processes. For irreversible processes, you must find a reversible path with the same endpoints and integrate along that path.

**"Maxwell's demon violates the second law."** Apparent paradox resolved in Chapter 10: the demon's memory is an entropy-bearing element. Erasing the memory generates entropy that more than compensates for the apparent local decrease.

---

## Exercises

**Warm-up (Apply).** 1 mol of ideal gas is heated isobarically from 300 K to 400 K. Find $\Delta S$ for a diatomic gas ($C_P = (7/2)R$).

**Apply.** 100 J of heat flows from a reservoir at 600 K to a reservoir at 300 K. Find $\Delta S_H$, $\Delta S_C$, and $\Delta S_{\text{universe}}$.

**Apply.** 0.5 mol of monatomic ideal gas expands isothermally and reversibly from $V_1 = 1$ L to $V_2 = 5$ L at $T = 300$ K. Find $\Delta S$ of the gas. Compute it both ways (Clausius and Boltzmann).

**Apply.** Free expansion: 2 mol of ideal gas in 1 L at 300 K expands into a previously evacuated 4 L chamber (total final volume 5 L). Find $\Delta S$ of the gas.

**Apply + Analyze.** Mix 1 kg of water at 0°C with 1 kg of water at 100°C. Find the equilibrium temperature and the entropy change of the combined system. Specific heat of water = 4186 J/(kg·K). (Approximate: $\Delta S \approx mc \ln(T_f^2/(T_1 T_2))$.)

**Challenge.** A perfect crystal at $T = 5$ K: estimate its entropy. Why is this much smaller than the same material's entropy at room temperature?

---

## LLM Exercises

### Build the entropy / microstate simulator (`07-entropy-microstates.html`)

> **Show.** Boltzmann's $S = k_B \ln \Omega$. For $N$ particles distributed in two halves of a box: $\Omega(n_L) = N!/(n_L!(N-n_L)!)$.
>
> **Say.** Build an entropy-from-microstates simulator.
>
> **Constrain.** D3 v7. A box divided into two halves. $N$ particles (slider, 4 to 100). Each particle, at each time step, hops to the other half with probability 0.5. Count particles in left half ($n_L$). Compute $\Omega(n_L) = \binom{N}{n_L}$ and $S = k_B \ln \Omega$. Display: histogram of $n_L$ over time as the system equilibrates; running maximum entropy; current $S/k_B$. Starting condition: all particles on one side ($n_L = N$, $S = 0$). Animation shows particles spreading; entropy rises and saturates near the maximum at $n_L = N/2$. Filename: `07-entropy-microstates.html`.
>
> **Verify.** (a) Starting with all particles on left, $S$ starts at 0 and rises. (b) Maximum $S$ is achieved when $n_L \approx N/2$. (c) For $N = 20$: max $S/k_B = \ln\binom{20}{10} \approx \ln 184756 \approx 12.13$.

### Exploration

- Watch the system evolve from $n_L = 20$ (all on left) to $n_L \approx 10$. Note: starting with all particles on one side is *not* equilibrium; the system spontaneously evolves to equilibrium.
- The second law is statistical: at $N = 20$, fluctuations are visible. At $N = 200$, fluctuations are smaller. At $N = 10^{20}$, they're invisible.
- Once the system is near equilibrium, count how often $n_L$ deviates by more than 20% from $N/2$. The fluctuation rate decreases dramatically with $N$.

### Extension prompt (chapter bridge)

> **Show.** The microstate counting gives the entropy. The Boltzmann distribution generalizes this: in thermal equilibrium with a reservoir at temperature $T$, the probability of energy $E_i$ is $\propto e^{-E_i/k_BT}$.
>
> **Say.** Build a Boltzmann distribution simulator.
>
> **Constrain.** A system with $N$ energy levels equally spaced by $\Delta E$. Sliders for $T$ and $N$. Display: occupation probability of each level as a bar chart, with $p_i = e^{-E_i/k_BT}/Z$.
>
> **Verify.** At low $T$ ($k_BT \ll \Delta E$): essentially all in ground state. At high $T$ ($k_BT \gg \Delta E$): nearly uniform distribution. Average energy $\langle E\rangle$ rises with $T$.

Save as `07b-boltzmann-preview.html`. Bridge to Chapter 8.

---

## What would change my mind

The dual nature of entropy (Clausius's macroscopic and Boltzmann's microscopic definitions) is a settled result, confirmed by every calculation in classical thermodynamics and statistical mechanics. Boltzmann's death in 1906 came just before his views were vindicated by Einstein's 1905 work on Brownian motion and Perrin's 1908 measurements; the molecular view of entropy is now bedrock.

The second law in entropy form ($\Delta S_{\text{universe}} \geq 0$) has been confirmed in every measured process. A confirmed violation would shake everything. The closest thing to "violation" is the *small-system fluctuations* covered by stochastic thermodynamics — these can momentarily decrease entropy, but only with probability that decreases exponentially with system size.

## Still puzzling

- *Why does the universe have low initial entropy?* Penrose's "Weyl curvature hypothesis" and other cosmological proposals address this, but no consensus. It's genuinely puzzling that the early universe was so highly ordered.
- *What is the "right" interpretation of entropy?* For closed systems with well-defined energies, Boltzmann's $S = k_B \ln \Omega$ is unambiguous. For open systems, systems with quantum entanglement, or non-equilibrium systems, entropy is harder to define. Generalized entropies (Renyi, Tsallis, von Neumann) appear in different contexts.
- *Heat death of the universe.* Will the universe reach a state of maximum entropy and stop changing? Modern cosmology (with dark energy) suggests the universe will keep expanding forever, with entropy increasing without bound. But the late universe doesn't fit any simple maximum-entropy picture — it's a separate puzzle.

---

**Tags:** entropy, Clausius definition, Boltzmann entropy, microstate counting, second law, irreversibility, free expansion, third law, arrow of time, Maxwell's demon

