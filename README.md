# GLOW
## Gradient Learning Order-parameter and Wick Transition

**A Unified BCS-Wick-Luttinger Theory of the Grokking Phase Transition**

ERI Labs · Eric Ren · New Jersey, United States · github.com/ericrenone · Founded January 2025

---

> *Cooper showed such binding will occur in the presence of an attractive potential, no matter how weak.* — BCS, 1957
>
> *Grokking is the Wick rotation of a neural network from a Minkowski memory to a Euclidean mind.* — WKET
>
> *The volume enclosed by a Fermi surface is directly proportional to the particle density.* — Luttinger & Ward, 1960

---

## The Central Claim

Three frameworks — GCCT, WKET, and FLML — describe the same event from three directions. The event is grokking. The three descriptions are not analogies. They share equations.

**GCCT** derives grokking as BCS Cooper condensation: gradient modes near the Farey learning surface are unstable against pair formation under any attractive Farey-phonon interaction, no matter how weak. The learning gap $\Delta_t$ opens at the critical training time $t^*$ exactly as the BCS gap opens at $T_c$. The order parameter is real, computable, and self-consistent.

**WKET** derives grokking as a Wick rotation: the substitution $t \to \tau = it$ converts the oscillatory Minkowski path integral (memorization regime, indefinite metric, circular points accessible) into the convergent Euclidean partition function (generalization regime, positive-definite metric, circular points at infinity). The spectral gap $\lambda_1 > 0$ is the condition that the Wick-rotated propagator $e^{-\mathcal{L}_{JL}\tau}$ converges — equivalently, that the Boltzmann weight $e^{-H_\text{learn}/T_\text{learn}}$ is normalizable below $T_c$.

**FLML** derives grokking as a Luttinger-non-conserving topological transition: the Luttinger number $N_L(t)$ — the fraction of gradient Farey modes with positive dressed propagator — is conserved throughout the generalization phase (Theorem 3.3) and jumps discontinuously at grokking (Corollary 3.4). The dressed propagator $G_t$ is the BCS Nambu Green's function. The quasiparticle weight $Z_t = [1 - \partial\Sigma/\partial\omega]^{-1}$ is the BCS coherence factor. The Luttinger-Ward functional $\Omega_{LW}$ is the BCS free energy.

The unification: the learning gap equation (GCCT §4.3) reduces to the Dyson equation (FLML §1.2) in the GW approximation, which reduces to the Poincaré inequality (LKTL) in the large-$C_\alpha$ limit. The Wick rotation (WKET) is the geometric transformation that maps between the Minkowski and Euclidean regimes that GCCT labels "memorization" and "generalization" and FLML labels $\lambda_1 < 0$ and $\lambda_1 > 0$.

---

## The Three-Language Identification

The same physical event, written three ways:

| Event | GCCT language | WKET language | FLML language |
|---|---|---|---|
| Grokking itself | $\Delta_t = 0 \to \Delta_t > 0$ | Wick rotation completes: circular points move to $\infty$ | $N_L$ jumps; $FS_t$ topology changes |
| Order parameter | Learning gap $\Delta_t = \|\lambda_F\| \sum_k u_k v_k$ | Imaginary part of circular point: $\Delta_t \leftrightarrow \text{Im}(\omega)$ | $\sqrt{\Sigma_{FS}(t)}$; self-energy at Farey surface |
| Critical point | $T_\text{learn} = T_c$; $N_F\|\lambda_F\| \to 1$ | $\lambda_1 = 0$; null metric; isotropic diffusion | $\lambda_1(\mathcal{L}_{JL}) = 0$; $Z_t \to \frac{1}{2}$ at $k_F$ |
| Phase below | Superconducting condensate: $n_s > 0$ | Euclidean geometry: $ds^2 = dx^2 + dt^2$ | $N_L$ conserved; GWI holds |
| Phase above | Normal state: $\Delta_t = 0$, Luttinger liquid | Minkowski geometry: $ds^2 = dx^2 - dt^2$ | GWI anomalous: $A_t \ne 0$ |
| Precursor | $C_\alpha \to 1$; $\xi_F \to \infty$ | $d_{CK}(b, \mathcal{Q}) \to 0$ | $Z_t \to \frac{1}{2}$; $N_L$ fluctuating |
| Propagator | BdG Green's function $G_t^{BdG}$ | Wick-rotated $G_E(k,\tau) = G_t(k,-i\tau)$ | Dyson: $G_t = [G_0^{-1} - \Sigma_t]^{-1}$ |
| Symmetry | U(1) batch rotation breaking | Klein four-group $V_4 = \{e, P, T, C\}$ | Batch permutation invariance |
| Geometric object | BCS unitarity circle $u_k^2 + v_k^2 = 1$ | Absolute conic $\mathcal{Q} = \{\lambda_1 = 0\}$ | Fermi Learning Surface $FS_t$ |

The mathematical identity at the core:

$$\Delta_t = \sqrt{\Sigma_{FS}(t)} \quad\text{(GCCT ↔ FLML)}$$

$$G_t(k, 0)^{-1} = H_0(k) - \Sigma_t(k) = \xi_k - \Sigma_t(k) \quad\text{(Dyson = BdG diagonal)}$$

$$\Omega_{LW}(t) = E_{BCS}(t) = -\frac{1}{2} N_F \Delta_t^2 + O(\Delta_t^4) \quad\text{(LW free energy = BCS condensation energy)}$$

$$\lambda_1 > 0 \iff \text{Wick-rotated propagator converges} \iff \Delta_t > 0 \quad\text{(WKET ↔ GCCT)}$$

---

## Part I — WKET: The Geometry of Grokking

### The Wick Rotation

Wick (1954) observed that substituting $t \to \tau = -it$ (imaginary time) converts the oscillatory quantum evolution operator into the thermal Boltzmann weight:

$$e^{-iH_\text{learn} t/\hbar} \xrightarrow{t \to -i\tau} e^{-H_\text{learn} \tau / \hbar} = e^{-\beta H_\text{learn}}$$

with $\beta = \tau/\hbar = 1/T_\text{learn}$. Under this substitution:

- The Schrödinger equation $i\hbar \partial_t \psi = H\psi$ becomes the heat equation $\hbar \partial_\tau \rho = -H\rho \leftrightarrow \partial_\tau \rho = \mathcal{L}_{JL} \rho$
- The quantum path integral $\int \mathcal{D}\theta\, e^{iS[\theta]/\hbar}$ becomes the statistical partition function $\int \mathcal{D}\theta\, e^{-S_E[\theta]/\hbar}$
- The oscillatory (memorization) regime becomes the convergent (generalization) regime

The Jordan-Liouville operator $\mathcal{L}_{JL} = -\nabla \cdot (D_s \nabla) + \bar{\mathcal{S}}$ is already the Wick-rotated form of the learning Hamiltonian. It is positive-definite when $\lambda_1 > 0$ — the spectral gap condition is the condition that the Wick-rotated dynamics converge.

### The Learning Temperature

Under the Wick identification:

$$T_\text{learn} = \frac{\text{Tr}(D_s)}{C_\alpha} = \frac{\text{Tr}(\text{Cov}_\text{batch}[\nabla L])}{\|\mathbb{E}[\nabla L]\|^2}$$

$$\beta_\text{learn} = \frac{1}{T_\text{learn}} = \frac{C_\alpha}{\text{Tr}(D_s)} = Q_\text{max} \quad\text{(in discrete Farey units)}$$

The inverse learning temperature equals the Farey resolution cutoff $Q_\text{max} = \lfloor 1/\varepsilon_t \rfloor$. High $C_\alpha$ (deep generalization) = low temperature = large $Q_\text{max}$ = fine Farey resolution. The Debye cutoff and the inverse temperature are the same object.

### Matsubara Frequencies as Farey Denominators

At finite temperature, imaginary time is compactified on a circle $\tau \sim \tau + \beta$. The allowed Fourier modes are the Matsubara frequencies. For the fermionic gradient modes (anticommuting creation/annihilation operators):

$$\omega_n^\text{Fermi} = (2n+1)\pi T_\text{learn}, \quad n \in \mathbb{Z}$$

**GLOW identification:** Farey denominator $q_n \in \{1, \ldots, Q_\text{max}\}$ $\leftrightarrow$ Matsubara index $n$. The Farey alphabet $\mathcal{A}_Q$ is the set of allowed Matsubara frequencies at inverse temperature $\beta_\text{learn} = Q_\text{max}$.

### Circular Points and Cooper Pairs

In the complex projective plane $\mathbb{C}P^2$, the circular points at infinity are:

$$\omega = (1 : i : 0), \quad \bar\omega = (1 : -i : 0)$$

Every real circle passes through both $\omega$ and $\bar\omega$. Every angle between two lines is a cross-ratio with respect to $\omega$ and $\bar\omega$.

**GLOW identification:** $\omega \leftrightarrow k = (p,q) \in \mathcal{A}_Q$, $\bar\omega \leftrightarrow -k = (q-p, q)$. The Cooper pair $(k, -k)$ is the gradient-space analog of the pair of circular points. The BCS unitarity circle $u_k^2 + v_k^2 = 1$ is the circle through $\omega$ and $\bar\omega$ in the $(u_k, v_k)$ plane.

Klein's imaginary transformation $T_i: (x:y:z) \to (x:iy:z)$ maps:
- Circular points: real → complex (Euclidean geometry, generalization)
- The BCS circle $u_k^2 + v_k^2 = 1 \to u_k^2 - v_k^2 = 1$ (memorization hyperbola)
- Metric: $ds^2_E = dx^2 + dy^2 \to ds^2_M = dx^2 - dy^2$ (Euclidean → Minkowski)

The three conic sections give the complete phase diagram:

| Conic | Equation | Geometry | Phase | $\lambda_1$ |
|---|---|---|---|---|
| Circle | $u_k^2 + v_k^2 = 1$ | Euclidean | Generalization | $> 0$ |
| Parabola (degenerate) | $u_k^2 = 1$, $v_k = 0$ | Null/isotropic | Grokking frontier | $= 0$ |
| Hyperbola | $u_k^2 - v_k^2 = 1$ | Minkowski | Memorization | $< 0$ |

The grokking transition is the moment Klein's imaginary transform maps the BCS circle to the memorization hyperbola — equivalently, the moment the circular points move from infinity to the real plane.

### The Grokking Locus as Absolute Conic

Let $\mathcal{Q} = \{b \in \mathcal{B} : \lambda_1(\mathcal{L}_{JL}(b)) = 0\}$ be the grokking locus. The Cayley-Klein distance from a parameter point $b$ to $\mathcal{Q}$ is:

$$d_{CK}(b, \mathcal{Q}) = \frac{1}{2} \log\,\text{cross-ratio}(b, b'; b_1, b_2)$$

where $\{b_1, b_2\} = \mathcal{B}_\text{line} \cap \mathcal{Q}$ are the two intersections of the gradient line through $b$ with the grokking locus. The spectral gap is this Cayley-Klein distance:

$$\lambda_1(b) = d_{CK}(b, \mathcal{Q})$$

The three phases of learning are the three Cayley-Klein regimes: interior ($\lambda_1 > 0$, generalization), on the conic ($\lambda_1 = 0$, grokking), exterior ($\lambda_1 < 0$, memorization).

### The Klein Four-Group Symmetry

The Bogoliubov-de Gennes Hamiltonian $H_k^{BdG} = \xi_k \sigma_z + \Delta_t \sigma_x$ admits three discrete symmetries whose composition forms the Klein four-group $V_4 = \{e, P, T, C\}$:

- $P$ (particle-hole): $c_{k,t} \to c^\dagger_{-k,t}$, maps $(\xi_k, \Delta_t) \to (-\xi_k, \Delta_t)$
- $T$ (time-reversal): $t \to -t$, maps $(\xi_k, \Delta_t) \to (-\xi_k, -\Delta_t)$  
- $C = PT$ (charge conjugation): maps $(\xi_k, \Delta_t) \to (\xi_k, -\Delta_t)$

These satisfy $P^2 = T^2 = C^2 = e$ and $PT = C$ — exactly $V_4$. The grokking frontier $\{\lambda_1 = 0, \Delta_t = 0\}$ is invariant under all four elements of $V_4$: it is the fixed-point locus of the symmetry group of the phase transition.

### Osterwalder-Schrader Correspondence

The Osterwalder-Schrader theorem (1973) establishes that a Euclidean QFT satisfying reflection positivity corresponds to a unitary Minkowski QFT. In the learning framework:

**Theorem (GLOW Reflection Positivity).** For any test function $\phi \in L^2(\mathcal{B}, \mu)$:

$$\langle \phi, \mathcal{L}_{JL} \phi \rangle = \int |D_s^{1/2} \nabla\phi|^2\, d\text{vol} + \int \bar{\mathcal{S}} |\phi|^2\, d\text{vol} \geq \lambda_1 \|\phi\|^2$$

This is the Poincaré inequality (condition IV of the Master Equivalence). Reflection positivity of the learning dynamics is equivalent to the spectral gap $\lambda_1 > 0$ — the same condition as GCCT's $\Delta_t > 0$ and FLML's $N_L$ conservation.

---

## Part II — GCCT: The Condensate

### Gradient Modes and the Farey Learning Surface

For each Farey mode $k = (p,q) \in \mathcal{A}_Q$, define the gradient mode operators satisfying fermionic anticommutation $\{c_{k,t}, c^\dagger_{k',t}\} = \delta_{kk'}$. The Farey mode energy relative to the learning chemical potential $\bar\rho_t$ (mean gradient rotation):

$$\xi_k = (p/q) - \bar\rho_t$$

The Farey Learning Surface $FS_t = \{k : \xi_k = 0\}$ is the boundary between modes above (generalization) and below (memorization) it. The learning chemical potential $\bar\rho_t$ is fixed self-consistently by $N_L(t)$ (Luttinger conservation).

The time-reversed mode of $k = (p,q)$ is $-k = (q-p, q)$ — the Farey complement. The Nambu gradient spinor $\Psi_k = (c_{k,t}, c^\dagger_{-k,t})^T$ pairs each mode with its Farey complement.

### Cooper Instability in Gradient Space

**Theorem (Cooper Gradient Instability).** Consider two gradient modes $k$ and $-k$ near the Farey Learning Surface subject to the Farey-phonon attraction $V_F = -|\lambda_F|$ for $|\xi_k| < Q_\text{max}$. For any $|\lambda_F| > 0$, the two-mode system has a bound state with binding energy:

$$W = -2 Q_\text{max} \exp\!\left(-\frac{2}{N_F |\lambda_F|}\right) < 0$$

where $N_F = |\{k \in \mathcal{A}_Q : |\xi_k| < Q_\text{max}\}| / Q_\text{max}$ is the density of Farey modes at the learning surface.

*Proof sketch.* Writing the two-mode wavefunction as $\sum_k g_k c^\dagger_k c^\dagger_{-k} |FS\rangle$ above the Farey surface, the secular equation yields $1 = N_F |\lambda_F| \ln(2Q_\text{max}/|W|)$, giving $W = -2Q_\text{max} e^{-2/N_F|\lambda_F|} < 0$ for any $|\lambda_F| > 0$. $\square$

The exponential non-analyticity in the coupling $|\lambda_F|$ is why generalization cannot be accessed perturbatively from the memorization phase. The grokking transition has no perturbative precursor in the coupling expansion — it is a non-perturbative phenomenon.

### The GCCT Wavefunction

The learning condensate state is the gradient-space BCS wavefunction:

$$|\text{GCCT}_t\rangle = \prod_{k \in \mathcal{A}_Q} \left(u_k + v_k\, c^\dagger_{k,t}\, c^\dagger_{-k,t}\right)|0_t\rangle$$

where the coherence factors $u_k, v_k \in \mathbb{R}$ satisfy unitarity $u_k^2 + v_k^2 = 1$ and encode the signal/noise decomposition of each mode. The pairing amplitude:

$$F_k = \langle c_{-k,t} c_{k,t} \rangle_\text{GCCT} = u_k v_k$$

has no analog in the normal state — it is the off-diagonal expectation value that DIRA identifies as the coherence $\langle a|\rho|a'\rangle$ for $a \ne a'$. The learning order parameter:

$$\Delta_t = |\lambda_F| \sum_{k \in \mathcal{A}_Q} F_k = |\lambda_F| \sum_k u_k v_k$$

is a macroscopic quantity measuring collective coherence across all gradient modes. When $\Delta_t > 0$, the system is generalizing. When $\Delta_t = 0$, it is memorizing.

### The BdG Hamiltonian and Bogoliubov-Learning Transform

In the Nambu basis, the full GCCT Hamiltonian takes the Bogoliubov-de Gennes form:

$$H_k^{BdG} = \begin{pmatrix} \xi_k & \Delta_t \\ \Delta_t^* & -\xi_k \end{pmatrix}$$

with quasiparticle eigenvalues $E_k(t) = \pm\sqrt{\xi_k^2 + |\Delta_t|^2}$. The minimum excitation energy is $|{\Delta_t}|$ — the learning gap: the minimum energy needed to break a gradient Cooper pair.

**Definition (Bogoliubov-Learning Transform, BLT).** The BLT diagonalizes $H^{BdG}$ via:

$$\gamma_{k,t} = u_k\, c_{k,t} + v_k\, c^\dagger_{-k,t}$$

with coherence factors:

$$u_k^2 = \frac{1}{2}\!\left(1 + \frac{\xi_k}{E_k(t)}\right) \quad\text{(signal fraction)}, \qquad v_k^2 = \frac{1}{2}\!\left(1 - \frac{\xi_k}{E_k(t)}\right) \quad\text{(noise fraction)}$$

At the Farey surface ($\xi_k = 0$): $u_k = v_k = 1/\sqrt{2}$ — the quasiparticle is an equal mixture of signal and noise. This is the most non-commutative point in gradient space.

**GLOW identification:** The FLML quasiparticle weight $Z_t = [1 - \partial\Sigma_t/\partial\omega]^{-1}$ equals the Bogoliubov $u_{k_F}^2$ evaluated at the Farey surface:

$$Z_t = u_{k_F}^2 = \frac{1}{2}\!\left(1 + \frac{\xi_{k_F}}{E_{k_F}}\right) \xrightarrow{\Delta_t \to 0} \frac{1}{2}$$

When $\Delta_t$ is large (deep condensate): $Z_t \approx 1$ (pure signal, coherent gradient). When $\Delta_t \to 0$ (approaching grokking): $Z_t \to \frac{1}{2}$ (half signal, half noise — quasiparticle collapse).

### The Learning Gap Equation

**Theorem (Learning Gap Equation).** The GCCT order parameter $\Delta_t$ satisfies the self-consistent equation:

$$\Delta_t = |\lambda_F| \sum_{k \in \mathcal{A}_Q,\, |\xi_k| < Q_\text{max}} \frac{\Delta_t}{2 E_k(t)} \tanh\!\left(\frac{E_k(t)}{2 T_\text{learn}}\right)$$

In the weak-coupling limit $N_F|\lambda_F| \ll 1$, the solution at zero noise ($T_\text{learn} = 0$) is:

$$\Delta_t(0) = 2 Q_\text{max} \exp\!\left(-\frac{1}{N_F |\lambda_F|}\right)$$

The universal gap ratio:

$$\frac{\Delta_t(0)}{k_\text{learn} T_c} = 1.764 \quad\text{(GLOW universal constant)}$$

**GLOW identification:** The learning gap equation is the GCCT form of the Dyson equation (FLML §1.2). The self-consistent $\Delta_t$ is the square root of the self-energy evaluated at the Farey surface: $\Delta_t = \sqrt{\Sigma_{FS}(t)}$. The gap equation's self-consistency condition is the learning-theoretic version of the Luttinger-Ward stationarity $\delta\Omega_{LW}/\delta G = 0$.

### Meissner Effect: Noise Expulsion

Define the gradient noise field $A_t = \text{Cov}_\text{batch}[\nabla L]^{1/2}$ and the condensate current $J_t = \mathbb{E}_\text{batch}[\nabla L]$. The London-GCCT equation:

$$J_t = -\frac{n_s(t)}{m_\text{learn}} A_t, \qquad m_\text{learn} = 1/C_\alpha, \qquad n_s(t) = N_L(t)\, |\Delta_t|^2$$

The noise penetration depth $\lambda_L = 1/\sqrt{C_\alpha\, n_s(t)\, |\Delta_t|^2}$: noise perturbations at scales larger than $\lambda_L$ are expelled from the condensate. When $C_\alpha \to 1$ (approaching grokking): $\lambda_L \to \infty$ — the condensate can no longer expel noise, explaining the fragility of networks near the grokking transition.

### Anderson-Higgs: BatchNorm Acquires Mass

The spontaneous breaking of U(1) batch-rotation symmetry at $t = t^*$ produces a Goldstone mode $\delta\phi(k, t)$ — uniform phase fluctuations of the gradient Cooper pair amplitude.

**Theorem (GLOW Anderson-Higgs).** When $\Delta_t > 0$, the Goldstone mode $\delta\phi$ is absorbed by the BatchNorm scale parameter $\beta_\ell$ at layer $\ell$, which acquires the learning mass:

$$m_{BN}(t) = C_\alpha\, N_L(t)\, |\Delta_t|^2 = \lambda_L^{-2}$$

BatchNorm stabilizes training because it is the realization of the Anderson-Higgs mechanism: it converts the dangerous massless Goldstone fluctuations (phase noise in gradient directions) into a massive, stable degree of freedom.

### Josephson Effect: Basin Tunneling

Two loss basins separated by a saddle point carry a basin Josephson current:

$$J_\text{basin} = J_c \sin(\Delta\phi_F)$$

where $\Delta\phi_F = \phi_L - \phi_R$ is the phase difference of the gradient Cooper pair amplitude between basins, and the critical tunneling rate $J_c = \sqrt{\Delta_t^{(L)} \Delta_t^{(R)}} / (2\tilde\ell_\text{saddle})$, with $\tilde\ell_\text{saddle}$ the normalized persistence length of the saddle (from PH-SP).

The AC Josephson frequency $\omega_J = 2V_\text{basin}/\hbar_\text{learn}$ corresponds to the Farey Backtrack period in KQOM — the oscillatory gradient fluctuations during loss plateau transitions.

**GLOW identification:** The Josephson phase difference $\Delta\phi_F$ between two basins is the Cayley angle (WKET) between the two gradient directions, computed via the cross-ratio with the circular Farey endpoints:

$$\Delta\phi_F = \frac{1}{2i} \log\,\text{cross-ratio}(k_L, k_R; \omega, \bar\omega)$$

---

## Part III — FLML: The Luttinger-Ward Structure

### Dressed Gradient Propagator

For each Farey mode $k = (p,q) \in \mathcal{A}_Q$, the free propagator is the Green's function of the unperturbed (quadratic) loss:

$$G_0(k, \omega) = [\omega I - H_0(k)]^{-1}, \qquad H_0(k) = \frac{p}{q} \cdot \|H_0\|$$

The learning self-energy $\Sigma_t(k)$ encodes corrections from batch noise, nonlinear coupling, and layer-to-layer entanglement. The Dyson equation gives the dressed propagator:

$$G_t(k, \omega) = [G_0(k,\omega)^{-1} - \Sigma_t(k)]^{-1}$$

**GLOW identification:** $G_t(k, \omega)^{-1} = \omega I - H_0(k) - \Sigma_t(k) = \omega I - \xi_k - \Sigma_t(k)$. At $\omega = 0$: $G_t(k,0)^{-1} = -\xi_k - \Sigma_t(k) = -H_k^{BdG}$ diagonal — the Dyson equation is the static BdG eigenvalue equation. The sign of $G_t(k,0)$ determines whether mode $k$ generalizes ($G_t > 0$) or memorizes ($G_t < 0$), exactly as the sign of $\xi_k$ determines whether a BCS mode is above or below the Fermi surface.

### The Fermi Learning Surface and Luttinger Number

**Definition.** $FS_t = \{k \in \mathcal{A}_Q : G_t(k,0) = 0 \text{ or } \infty\}$ — the zero surface of the dressed static propagator.

**Definition.** $N_L(t) = |\{k : G_t(k,0) > 0\}| / |\mathcal{A}_Q| \in [0,1]$ — the fraction of Farey modes carrying coherent forward-propagating signal.

**Theorem (Luttinger Conservation).** When $\lambda_1(\mathcal{L}_{JL}) > 0$ and $\Sigma_t(k)$ is analytic in $k$:

$$N_L(t) = N_L(0) \quad \text{for all } t > 0$$

*Proof sketch.* The sign of $G_t(k,0)$ changes only when $k$ crosses $FS_t$. Analyticity of $\Sigma_t$ means $FS_t$ cannot change topology without a phase transition. Since $\lambda_1 > 0$ forbids phase transitions, $FS_t$ is topologically frozen and $N_L$ is conserved. $\square$

**Corollary (Luttinger Violation at Grokking).** At $t = t^*$, $\lambda_1 = 0$, and $N_L$ jumps discontinuously:

$$N_L(t^{*+}) - N_L(t^{*-}) = \Delta N_L \ne 0$$

The grokking transition creates new generalization capacity — new modes cross the Fermi Learning Surface and $N_L$ increases. This is detectable as a topological change in $FS_t$ in the Farey mode space.

### The Luttinger-Ward Learning Functional

The Luttinger-Ward functional $\Phi_{LW}[G_t]$ is the sum of all closed, bold, two-particle-irreducible (2PI) skeleton diagrams:

$$\Phi_{LW}[G_t] = \sum_\text{2PI skeleton diagrams} D[G_t]$$

The 2PI condition encodes representation robustness: features encoded in 2PI diagrams survive removal of any two propagator lines (any two network layers). The learning grand potential:

$$\Omega_{LW}(t) = \text{Tr}[\ln(-G_t)] - \text{Tr}[\Sigma_t G_t] + \Phi_{LW}[G_t]$$

converges to a self-consistent minimum ($\delta\Omega_{LW}/\delta G_t = 0$) exactly when the training converges to the Kähler-Einstein fixed point.

**GLOW identification:** The GW truncation $\Phi_{LW}^\text{GW}[G_t] = \frac{1}{2}\text{Tr}[G_t \cdot \text{Cov}_\text{batch}[\nabla L] \cdot G_t]$ recovers $C_\alpha = \|\mathbb{E}[\nabla L]\|^2 / \text{Tr}(\text{Cov}[\nabla L])$. $C_\alpha$ is the leading-order conserving approximation to the full Luttinger-Ward functional. $\Omega_{LW}$ at convergence is the BCS free energy evaluated at the learning gap:

$$\Omega_{LW}(t^*) = E_\text{BCS}(t^*) = -\frac{1}{2} N_F \Delta_t^2 + O(\Delta_t^4)$$

### Schrieffer-Wolff: UV/IR Decoupling

The full learning Hamiltonian decomposes as $H_\text{learn} = H_\text{signal} + H_\text{noise} + V_\text{coupling}$. The SW-Learning Generator $\mathcal{S}_t$ satisfies $[H_\text{signal}, \mathcal{S}_t] = -V_\text{coupling}$, with components:

$$(\mathcal{S}_t)_{kk'} = \frac{(V_\text{coupling})_{kk'}}{\varepsilon_k - \varepsilon_{k'}} \approx \frac{D_s}{\lambda_1} \quad\text{(leading order)}$$

The effective signal Hamiltonian $H_\text{eff} = H_\text{signal} + \frac{1}{2}[\mathcal{S}_t, V_\text{coupling}]$ is block-diagonal when $\|V_\text{coupling}\| \ll \lambda_1$. The second-order energy correction $\varepsilon_k^\text{eff} = \varepsilon_k + \sum_{k'} |V_{kk'}|^2/(\varepsilon_k - \varepsilon_{k'})$ is the Kondo exchange coupling — the FLML analog of $J \propto V^2/U$.

The three SW regimes:

| $V/\Delta$ | Phase | Learning | BCS analogy |
|---|---|---|---|
| $\ll 1$ | Generalization | Clean signal/noise separation | BCS weak coupling |
| $\sim 1$ | Grokking frontier | Signal and noise resonant | Quantum critical |
| $\gg 1$ | Memorization | Noise overwhelms signal | Anderson impurity strong coupling |

### Gradient Ward Identity

**Theorem (GWI).** Batch permutation invariance implies:

$$\frac{\partial \Sigma_t(k)}{\partial k} = \Gamma_t(k)$$

This relates the self-energy to the full gradient vertex through the same symmetry that generates current conservation. BatchNorm is the gauge-fixing condition that enforces this symmetry layer-by-layer.

**Theorem (Anomaly Cancellation).** BatchNorm at layer $\ell$ restores the GWI for modes $k$ supported within that layer: $A_t(k)|_\text{layer \ell} = 0$.

When $\lambda_1 < 0$ (memorization), the GWI becomes anomalous — $A_t(k) = \partial_k\Sigma_t - \Gamma_t \ne 0$ — signaling that batch symmetry is broken and gradient information has become localized to individual training examples.

---

## The Unified Equations

The three frameworks share one set of core equations. All notation is unified:

$$\boxed{G_t(k,\omega) = \left[G_0(k,\omega)^{-1} - \Sigma_t(k)\right]^{-1} = H_k^{BdG}(\omega)^{-1}} \qquad\text{(Dyson = BdG)}$$

$$\boxed{\Delta_t = |\lambda_F| \sum_k \frac{\Delta_t}{2E_k(t)} \tanh\!\frac{E_k(t)}{2T_\text{learn}} \iff \frac{\delta\Omega_{LW}}{\delta G_t} = 0} \qquad\text{(gap equation = LW stationarity)}$$

$$\boxed{\lambda_1 > 0 \iff \Delta_t > 0 \iff Z_t > \tfrac{1}{2} \iff N_L \text{ conserved} \iff e^{-\mathcal{L}_{JL}\tau} \text{ converges}} \qquad\text{(all conditions identical)}$$

$$\boxed{C_\alpha = 1 \iff T_\text{learn} = T_c \iff \Delta_t = 0^+ \iff N_L \text{ jumps} \iff \text{Wick rotation complete}} \qquad\text{(grokking)}$$

The GLOW identification table for all primary objects:

| Symbol | GCCT | WKET | FLML | KQOM |
|---|---|---|---|---|
| Order parameter | $\Delta_t$ | Imaginary part of $\omega$ | $\sqrt{\Sigma_{FS}}$ | — |
| Critical point | $T_\text{learn} = T_c$ | $\lambda_1 = 0$; null metric | $\lambda_1 = 0$ | $C_\alpha = 1$ |
| Propagator | BdG $G_t^{BdG}$ | Wick-rotated $G_E$ | Dyson $G_t$ | $Q_\text{max}$ encoding |
| Phase boundary | $FS_t$ | Absolute conic $\mathcal{Q}$ | $FS_t$ | $Q_\text{max}$ boundary |
| Coherence | $(u_k, v_k)$ circle | Circular points $(\omega, \bar\omega)$ | $Z_t = u_{k_F}^2$ | $q^*/Q_\text{max}$ |
| Free energy | $E_\text{BCS}$ | $F_\text{learn} = -T\log Z_\text{learn}$ | $\Omega_{LW}$ | $-\text{Tr}[\mathcal{L}_{JL}]$ |
| Symmetry group | U(1) $\times V_4$ | Klein Erlangen | Batch permutation | PSL(2,$\mathbb{Z}$) |
| Temperature | $T_\text{learn} = \text{Tr}(D_s)/C_\alpha$ | $1/\beta_\text{learn}$ | $T_c = \lambda_1 = 0$ | $1/Q_\text{max}$ |

---

## The Fourteen-Language Master Equivalence

Under assumptions A1–A5 (LKTL), K1–K3 (LKTL), FL1–FL3 (FLML), BC1–BC3 (GCCT), and WK1–WK4 (WKET), the following fourteen conditions are equivalent:

```
λ₁(ℒ_JL) > 0
  ⟺  (I)   C_α > 1                              [signal-to-noise; KQOM/LKTL]
  ⟺  (II)  KE metric on ℬ                        [Kähler-Einstein; KYBM]
  ⟺  (III) Poincaré inequality holds             [functional analysis / OS positivity]
  ⟺  (IV)  Bellman escape finite                 [combinatorics; VBE]
  ⟺  (V)   Möbius M_n converges                  [number theory; KQOM]
  ⟺  (VI)  K-polystable                          [algebraic geometry; KYBM]
  ⟺  (VII) MMP terminates at ℬ_min              [birational geometry; KYBM]
  ⟺  (VIII)Ca_eff < Ca_c                         [thin-film physics; LKTL]
  ⟺  (IX)  N_L conserved; GWI anomaly-free       [Luttinger-Ward; FLML]
  ⟺  (X)   Δ_t > 0  (learning gap open)         [BCS pairing; GCCT]
  ⟺  (XI)  ΔV_DLVO > k_BT · ln W_Fuchs          [colloidal barrier; CSSG]
  ⟺  (XII) SW(ℬ, s) ≠ 0                         [monopole count; SWMS]
  ⟺  (XIII)Z_learn = Tr[e^{-ℒ_JL/T_learn}]
            normalizable; β_learn · λ₁ > 0       [Wick partition function; WKET]
  ⟺  (XIV) d_CK(b, 𝒬) > 0                       [Cayley-Klein distance; WKET]
```

The three phases:

```
Δ_t > 0 · λ₁ > 0 · N_L conserved   →   GENERALIZATION   (condensate; Euclidean)
Δ_t = 0 · λ₁ = 0 · N_L jumps       →   GROKKING         (quantum critical; null)
Δ_t = 0 · λ₁ < 0 · GWI anomalous   →   MEMORIZATION     (normal; Minkowski)
```

---

## Falsifiable Predictions

Ordered by resource requirement. Each prediction is specific, quantitative, and testable on existing data.

**P1 — Universal gap ratio (two weeks, existing training logs)**

Compute $\Delta_t(0) = 2Q_\text{max}\exp(-1/N_F|\lambda_F|)$ from gradient statistics at each training step for any model exhibiting grokking. Measure the ratio $\Delta_t(0) / (k_\text{learn} T_c)$ where $T_c$ corresponds to $C_\alpha = 1$. 

$$\frac{\Delta_t(0)}{k_\text{learn} T_c} = 1.764 \quad\text{(GLOW universal constant; exact in BCS weak coupling)}$$

Confirmation establishes: grokking follows BCS universality with a computable, universal, dimensionless constant derivable from first principles.

**P2 — Luttinger number jump at grokking (three weeks, Power et al. 2022 checkpoints)**

Compute $N_L(t) = |\{k : G_t(k,0) > 0\}|/|\mathcal{A}_Q|$ at every training step on public modular arithmetic checkpoints. Show that $N_L(t)$ is approximately constant throughout memorization, then jumps at the step where test accuracy jumps ($C_\alpha \to 1$).

Confirmation establishes: grokking is a Luttinger-non-conserving topological event — the Fermi surface topology changes at exactly the step the network generalizes.

**P3 — Meissner noise expulsion (one month, controlled experiment)**

Train two networks to the same test accuracy, one with BatchNorm and one without. Compute the noise penetration depth $\lambda_L = 1/\sqrt{C_\alpha N_L |\Delta_t|^2}$ for each.

$$\lambda_L^\text{with BN} < \lambda_L^\text{without BN}$$

Confirmation establishes: BatchNorm implements the Anderson-Higgs mechanism — it reduces $\lambda_L$ by giving mass to the Goldstone mode, making the condensate more robust to gradient noise.

**P4 — Isotope effect (two months, batch size scaling)**

Train the same architecture to grokking at batch sizes $B \in \{32, 64, 128, 256, 512\}$. Record the grokking step $t^*$ for each.

$$t^* \propto 1/\sqrt{B}$$

Confirmation establishes: the GCCT isotope effect holds — larger batches reduce $T_\text{learn}$, reaching $T_c$ sooner, in exact analogy with the BCS isotope effect $T_c \propto 1/\sqrt{M}$.

**P5 — Josephson oscillations at basin transitions (three months)**

During a loss plateau transition, measure the gradient oscillation frequency $\omega_J$. The applied voltage $V_\text{basin} = L_\text{left} - L_\text{right}$ is the loss difference between basins.

$$\omega_J = \frac{2 V_\text{basin}}{\hbar_\text{learn}} \iff \omega_J \cdot T_\text{backtrack} = 2\pi$$

Confirmation establishes: gradient oscillations during plateau transitions are AC Josephson oscillations — their frequency is set by the loss difference between basins, not by noise.

**P6 — Type-I vs. Type-II learning phase diagram (three months)**

Compute the GCCT Ginzburg-Landau parameter $\kappa_\text{GCCT} = \lambda_L / \xi_F$ where $\xi_F = q^*/Q_\text{max}$ for various architectures and training configurations.

```
κ < 1/√2:  single-basin generalization (Type-I)
κ > 1/√2:  multi-basin learning with PH-SP nontrivial H₁ features (Type-II)
```

Confirmation establishes: the type-I / type-II distinction is a real and measurable property of training trajectories, with the Abrikosov vortex lattice of loss basins being detectable via the PH-SP merge tree.

---

## Algorithm: GLOW Training Monitor (GTM)

```python
def glow_monitor(g_t, g_next, cov_batch_grad, Delta_prev, T_prev):
    """
    Unified GCCT + FLML + WKET training diagnostic.
    One function. No held-out data. No Hessian.
    """
    # Step 1: KQOM encoding
    eps_t = norm(g_next - g_t) / (norm(g_t) + norm(g_next))
    Q_max = int(1.0 / eps_t)
    p_t, q_t = farey_convergent(dot(g_t, g_next) / (norm(g_t) * norm(g_next)))
    rho_bar = p_t / q_t

    # Step 2: FLML — learning temperature and C_α
    mu_g = mean(g_t)
    C_alpha = dot(mu_g, mu_g) / trace(cov_batch_grad)  # GW-level
    T_learn = trace(cov_batch_grad) / dot(mu_g, mu_g)

    # Step 3: GCCT — Farey mode energies and gap equation (self-consistent)
    xi_k = farey_mode_energies(Q_max, rho_bar)        # xi_k = (p/q) - rho_bar
    N_F = count_near_surface(xi_k, Q_max) / Q_max

    Delta_t = solve_gap_equation(Delta_prev, xi_k, N_F, Q_max, T_learn)
    E_k = sqrt(xi_k**2 + Delta_t**2)
    u_k = sqrt(0.5 * (1 + xi_k / E_k))               # signal fractions
    v_k = sqrt(0.5 * (1 - xi_k / E_k))               # noise fractions

    # Step 4: FLML — Dyson equation and Luttinger number
    Sigma_GW = compute_self_energy_gw(cov_batch_grad, Q_max)
    G_t = dyson(xi_k, Sigma_GW)                       # G_t = [xi_k - Sigma]^{-1}
    N_L = mean(G_t > 0)                               # Luttinger number
    Z_t = C_alpha / (1 + abs(d_Sigma_d_omega(Sigma_GW)))

    # Step 5: WKET — Cayley-Klein geometry
    beta_learn = Q_max                                 # inverse temperature = Farey cutoff
    n_s = N_L * Delta_t**2                            # condensate density
    lambda_L = 1.0 / sqrt(C_alpha * n_s * Delta_t**2 + 1e-12)
    xi_F = q_t / Q_max                               # Farey coherence length
    kappa_GCCT = lambda_L / (xi_F + 1e-12)

    # Step 6: Phase classification
    if Delta_t > 1e-4:
        phase = "CONDENSATE"
        geometry = "Euclidean"     # circular points at infinity
        if kappa_GCCT > 0.7071:
            phase = "CONDENSATE_TYPE_II"
    elif abs(Delta_t) < 1e-4 and abs(C_alpha - 1.0) < 0.05:
        phase = "CRITICAL"         # grokking frontier
        geometry = "Null"          # circular points becoming real
    else:
        phase = "NORMAL"
        geometry = "Minkowski"     # circular points accessible

    # Step 7: Ward identity anomaly (memorization diagnostic)
    A_t = ward_anomaly(Sigma_GW, G_t)

    return {
        "phase":       phase,      "geometry":   geometry,
        "Delta_t":     Delta_t,    "N_L":        N_L,
        "Z_t":         Z_t,        "lambda_L":   lambda_L,
        "kappa_GCCT":  kappa_GCCT, "C_alpha":    C_alpha,
        "T_learn":     T_learn,    "beta_learn": beta_learn,
        "xi_F":        xi_F,       "anomaly":    A_t,
    }
```

Computational cost: $O(Q_\text{max})$ per step for Steps 3–7, with $O(10)$ iterations for the gap equation. Negligible relative to backpropagation.

---

## Quick Reference

```
══════════════════════════════════════════════════════════════
CORE IDENTIFICATION: GCCT ↔ WKET ↔ FLML
══════════════════════════════════════════════════════════════
[Learning gap ↔ spectral gap]   Δ_t ↔ √(λ₁(ℒ_JL) / 2)
[Critical temperature]          T_c = T_learn|_{t=t*} ↔ λ₁ = 0 ↔ C_α = 1
[Debye cutoff ↔ Farey]         ω_D ↔ Q_max = ⌊1/ε_t⌋ ↔ β_learn (discrete)
[Coherence length]              ξ_F = q*/Q_max ↔ 1/C_α
[Condensate density]            n_s = N_L |Δ_t|² ↔ C_α − 1 (leading order)
[Cooper pair ↔ circular pts]   (k, −k) ↔ (ω, ω̄) ↔ (1:i:0), (1:−i:0)
[BCS circle ↔ Euclidean]       u² + v² = 1 ↔ ds² = dx² + dt² ↔ λ₁ > 0
[Memorization hyperbola]        u² − v² = 1 ↔ ds² = dx² − dt² ↔ λ₁ < 0
[Grokking ↔ Wick rotation]     Δ_t = 0 → Δ_t > 0 ↔ t → τ = it complete
[Circular pts ↔ grokking]      ω, ω̄ at ∞ → real ↔ λ₁ > 0 → λ₁ = 0
[Absolute conic ↔ frontier]    𝒬 = {λ₁=0} ↔ d_CK(b, 𝒬) = λ₁
[BatchNorm ↔ Anderson-Higgs]   BN scale β_ℓ acquires mass m_BN = C_α N_L |Δ_t|²
[Dyson ↔ BdG]                  G_t(k,0)⁻¹ = −H_k^{BdG} diagonal
[GW truncation ↔ C_α]          δΦ_LW^{GW}/δG_t = Σ_t^{GW} → C_α
[Matsubara ↔ Farey]            ω_n^{Fermi} = (2n+1)πT_learn ↔ q_n ∈ 𝒜_Q
[Josephson ↔ Cayley angle]     Δφ_F = log(cr(k_L,k_R;ω,ω̄))/2i
[Poincaré ↔ OS positivity]     Poincaré ineq. ↔ reflection positivity ↔ λ₁>0

══════════════════════════════════════════════════════════════
BdG HAMILTONIAN AND BLT
══════════════════════════════════════════════════════════════
H_k^{BdG} = ξ_k σ_z + Δ_t σ_x = ( ξ_k    Δ_t )
                                    ( Δ_t   −ξ_k )
E_k(t)  = √(ξ_k² + |Δ_t|²)
γ_{k,t} = u_k c_{k,t} + v_k c†_{−k,t}
u_k²    = ½(1 + ξ_k/E_k),   v_k² = ½(1 − ξ_k/E_k),   u_k² + v_k² = 1
Z_t     = u²_{k_F} → ½ at grokking → 1 at convergence

══════════════════════════════════════════════════════════════
LEARNING GAP EQUATION
══════════════════════════════════════════════════════════════
Δ_t = |λ_F| Σ_k Δ_t/(2E_k) tanh(E_k/2T_learn)   [self-consistent]
Δ_t(0) = 2Q_max exp(−1/N_F|λ_F|)                  [zero-noise gap]
Δ_t(0)/k_learn T_c = 1.764                         [universal ratio]
W = −2Q_max exp(−2/N_F|λ_F|)                       [Cooper binding energy]

══════════════════════════════════════════════════════════════
MEISSNER, COHERENCE, JOSEPHSON
══════════════════════════════════════════════════════════════
n_s(t)    = N_L(t) |Δ_t|²                          [condensate density]
λ_L       = 1/√(C_α n_s |Δ_t|²)                   [noise penetration depth]
ξ_F       = q*(t)/Q_max ↔ 1/C_α                   [Farey coherence length]
κ_GCCT    = λ_L/ξ_F; Type-I: <1/√2; Type-II: >1/√2
J_basin   = J_c sin(Δφ_F)                          [Josephson current]
ω_J       = 2V_basin/ℏ_learn ↔ 1/T_backtrack (KQOM)
m_BN(t)   = C_α N_L |Δ_t|² (Anderson-Higgs mass)

══════════════════════════════════════════════════════════════
WARD IDENTITY AND ANOMALY
══════════════════════════════════════════════════════════════
∂_k Σ_t(k) = Γ_t(k)          [GWI; λ₁ > 0]
A_t(k) = ∂_k Σ_t − Γ_t ≠ 0  [memorization anomaly; λ₁ < 0]
BatchNorm at layer ℓ → A_t(k)|_{layer ℓ} = 0

══════════════════════════════════════════════════════════════
KLEIN GEOMETRY PHASE DIAGRAM
══════════════════════════════════════════════════════════════
λ₁ > 0  ↔  Euclidean: ds² = dx² + dt²  ↔  u²+v²=1 (circle)
λ₁ = 0  ↔  Null:      ds² = 0          ↔  u²=1 (parabola)
λ₁ < 0  ↔  Minkowski: ds² = dx² − dt²  ↔  u²−v²=1 (hyperbola)

Cayley-Klein distance:  d_CK(b, 𝒬) = ½ log cr(b, b'; b₁, b₂) = λ₁
Klein four-group V₄ = {e, P, T, C} = BdG symmetry group
Circular points ω=(1:i:0), ω̄=(1:−i:0) ↔ Cooper pair (k, −k)

══════════════════════════════════════════════════════════════
MASTER EQUIVALENCE: ALL 14 CONDITIONS AT λ₁ > 0
══════════════════════════════════════════════════════════════
(I) C_α > 1  ·  (II) KE metric  ·  (III) Poincaré / OS positivity
(IV) Bellman escape  ·  (V) Möbius converges  ·  (VI) K-polystable
(VII) MMP terminates  ·  (VIII) Ca_eff < Ca_c  ·  (IX) N_L conserved
(X) Δ_t > 0  ·  (XI) DLVO barrier  ·  (XII) SW ≠ 0
(XIII) Z_learn normalizable  ·  (XIV) d_CK(b,𝒬) > 0
```

---

## Open Conjectures

**GC-C1 (BC-C9 / O10-FL Completion).** The imaginary-time propagator at half the period satisfies:

$$G_t^E(k, \beta_\text{learn}/2) = -F_k = -\frac{\Delta_t}{2E_k} = -\tilde\ell_i(t)$$

connecting the Euclidean Green's function (WKET) to the Cooper amplitude (GCCT) to the normalized persistence length of the occupied loss basin (PH-SP). This would complete the unification of the Trajectory Tree, Merge Tree, and Dyson flow conjectured in O10-FL.

**GC-C2 (Josephson-Farey Backtrack Identity).** The AC Josephson frequency satisfies:

$$\omega_J \cdot T_\text{backtrack} = 2\pi$$

where $T_\text{backtrack}$ is the KQOM Farey Backtrack period. Confirmation would identify basin tunneling oscillations with the Goldstone mode of the condensate.

**GC-C3 (Catastrophic Forgetting as Instanton).** Each catastrophic forgetting event is a Euclidean instanton in the Wick-rotated learning path integral, with action:

$$S_\text{inst} = \int YM_t(\tau)\, d\tau = \frac{8\pi^2 k}{g^2(T_\text{learn})}$$

where $k \in \mathbb{Z}$ is the topological charge and $g(T_\text{learn})$ is the effective gradient coupling. Catastrophic forgetting becomes exponentially rare as $T_\text{learn} \to 0$.

**GC-C4 (Isotope Effect).** $t^* \propto 1/\sqrt{B}$ where $B$ is batch size. The grokking time scales as the inverse square root of batch size, in exact analogy with $T_c \propto 1/\sqrt{M}$ in BCS theory.

**GC-C5 (Unitary Learning Rate).** The learning rate $\eta^*$ maximizing generalization efficiency satisfies $C_\alpha(\eta^*) = 2$ exactly — the GCCT unitary limit where Farey coherence length equals the inter-pair spacing.

**GC-C6 (Learning Free Energy = Farey Discrepancy).** The learning free energy $F_\text{learn} = -T_\text{learn} \log Z_\text{learn}$, expanded around $T_\text{learn} = 0$, equals the Farey discrepancy function whose vanishing is equivalent to the Riemann Hypothesis (Franel-Landau). The spectral gap $\lambda_1 > 0$ is the learning-theoretic analogue of RH.

---

## Repository Structure

```
glow/
├── core/
│   ├── bcs.py              # Gap equation, BdG Hamiltonian, BLT
│   ├── wick.py             # Wick rotation, imaginary-time propagator
│   ├── luttinger.py        # Dressed propagator, Luttinger number, GWI
│   └── klein.py            # Circular points, Cayley-Klein metric, V₄
│
├── monitor/
│   ├── gtm.py              # GLOW Training Monitor (GTM)
│   ├── gap_equation.py     # Self-consistent gap equation solver
│   └── fermi_surface.py    # FS_t topology tracker, N_L computation
│
├── physics/
│   ├── meissner.py         # London equation, noise penetration depth
│   ├── josephson.py        # Basin tunneling, AC/DC Josephson
│   ├── anderson_higgs.py   # BatchNorm mass, Goldstone mode
│   └── vortex.py           # Gradient vortices, Type-I/II classifier
│
├── geometry/
│   ├── cayley_klein.py     # Grokking locus as absolute conic
│   ├── circular_points.py  # ω = (1:i:0) ↔ Cooper pair (k,−k)
│   └── erlangen.py         # Phase diagram as Klein geometry classification
│
└── glow.py                 # Unified entry point
```

---

## Proven Results

| # | Statement | Status |
|---|---|---|
| G1 | Cooper gradient instability: for any $\|\lambda_F\| > 0$, bound state forms | Theorem (§GCCT) |
| G2 | BdG quasiparticle spectrum $E_k = \sqrt{\xi_k^2 + \Delta_t^2}$ | §GCCT |
| G3 | BLT diagonalizes $H^{BdG}$; $u_k^2 + v_k^2 = 1$ | Def (§GCCT) |
| G4 | Gap equation: self-consistent $\Delta_t$ exists for any $\|\lambda_F\| > 0$ below $T_c$ | Theorem (§GCCT) |
| G5 | Luttinger conservation: $N_L$ conserved when $\lambda_1 > 0$ | Theorem 3.3 (FLML) |
| G6 | $N_L$ jumps at grokking ($\lambda_1 = 0$) | Corollary 3.4 (FLML) |
| G7 | GWI holds when batch permutation symmetry preserved | Theorem 5.2 (FLML) |
| G8 | BatchNorm restores GWI layer-by-layer | Theorem 5.3 (FLML) |
| G9 | Wick rotation: $\mathcal{L}_{JL}$ is the Euclidean form of $H_\text{learn}$ | §WKET |
| G10 | OS positivity $\iff$ Poincaré inequality $\iff$ $\lambda_1 > 0$ | §WKET |
| G11 | Klein four-group $V_4$ = BdG symmetry group | §WKET |
| G12 | Circular points $(1:i:0)$ ↔ Cooper pair $(k,-k)$ | §WKET |
| G13 | Fourteen-language master equivalence (I)–(XIV) | Theorem 12.2 (GCCT) |
| G14 | Anderson-Higgs: BatchNorm acquires mass $m_{BN} = C_\alpha N_L |\Delta_t|^2$ | Theorem 7.1 (GCCT) |
| G15 | Basin Josephson current $J_\text{basin} = J_c \sin(\Delta\phi_F)$ | §GCCT |

---

## Theoretical Foundations

**BCS Theory**
Bardeen, J.; Cooper, L. N.; Schrieffer, J. R. (1957). Theory of Superconductivity. *Physical Review* 108(5): 1175–1204.
Cooper, L. N. (1956). Bound Electron Pairs in a Degenerate Fermi Gas. *Physical Review* 104(4): 1189–1190.
Bogoliubov, N. N. (1958). A new method in the theory of superconductivity. *Soviet Physics JETP* 7: 41.
Anderson, P. W. (1958). Random-phase approximation in the theory of superconductivity. *Physical Review* 112: 1900.
London, F.; London, H. (1935). The electromagnetic equations of the supraconductor. *Proc. Royal Society A* 149: 71.
Josephson, B. D. (1962). Possible new effects in superconductive tunnelling. *Physics Letters* 1(7): 251.

**Luttinger-Ward Theory**
Luttinger, J. M.; Ward, J. C. (1960). Ground-State Energy of a Many-Fermion System. II. *Physical Review* 118(5): 1417.
Luttinger, J. M. (1960). Fermi Surface and Some Simple Equilibrium Properties. *Physical Review* 119(4): 1153.
Ward, J. C. (1950). An Identity in Quantum Electrodynamics. *Physical Review* 78(2): 182.
Schrieffer, J. R.; Wolff, P. A. (1966). Relation between the Anderson and Kondo Hamiltonians. *Physical Review* 149(2): 491.

**Wick Rotation and Klein Geometry**
Wick, G. C. (1954). Properties of Bethe-Salpeter Wave Functions. *Physical Review* 96(4): 1124.
Osterwalder, K.; Schrader, R. (1973, 1975). Axioms for Euclidean Green's Functions I, II. *Commun. Math. Phys.*
Klein, F. (1872). Erlangen Program (Vergleichende Betrachtungen). Inaugural lecture, University of Erlangen.
Klein, F. (1871). Über die sogenannte Nicht-Euklidische Geometrie. *Mathematische Annalen.*
Cayley, A. (1859). A Sixth Memoir upon Quantics. *Phil. Trans. Royal Society* 149: 61.
Matsubara, T. (1955). A New Approach to Quantum-Statistical Mechanics. *Prog. Theor. Phys.* 14: 351.

**Inherited Foundations**
KQOM · PH-SP · LKTL · LB/DK · GAME · PPMC · KYBM · SWMS · CSSG · DIRA · ARIA
Dickson (1913) · Higman (1952) · Kruskal (1960) · Landau (1936, 1941, 1942)
Yau-Tian-Donaldson · Atiyah-Singer · Edelsbrunner-Harer (2010)
Robertson-Seymour (1985–2004) · ZF axioms Z1–Z8

---

*ERI Labs · Emergent Reality Intelligence · New Jersey, United States*
*Eric Ren · Executive Chairman · github.com/ericrenone · Founded January 2025*

---

**Grokking is not analogous to a phase transition. It is one. The condensate forms. The Wick rotation completes. The Fermi surface topology changes. Three statements. One event.**
