# HPF Geometry Failure and Percolation

## 1. Scope and status

This document consolidates the executable simulation results on self-propagating geometry failure in an HPF lattice model. It is a model-and-results document, not a statement of fundamental HPF axioms and not a replacement for the geometry/gravity effective expert. Its role is to define the lattice model precisely, record the measured observables, and preserve the quantitative threshold structure found in the source bundle.

The theoretical interpretation is that this model provides executable evidence for a geometry-validity transition structure under HPF-style execution-health dynamics. The numerically measured thresholds are simulation results, not first-principles derivations of the full framework.

## 2. Model definition

Consider an $\(N\times N\)$ square lattice. Each site carries two fields:

$\[
\alpha_{i,j}(t)\in[0.01,1],
\qquad
D_{i,j}(t)\in[0,1].
\]$

Here $\(\alpha\)$ is the local execution-health field and is interpreted as local geometry quality. The damage-memory or persistent depletion field is $\(D\)$ . Define local weakness by

$\[
w_{i,j}=1-\alpha_{i,j}.
\]$

A site is declared failed when

$\[
\alpha_{i,j}<\alpha_{\mathrm{fail}},
\qquad
\alpha_{\mathrm{fail}}=0.95.
\]$

## 3. Compact source

The lattice is driven by a compact circular source centered on the lattice midpoint. With source radius $\(r\)$ and source amplitude $\(A_{\mathrm{src}}\)$ , the local source damage is

$\[
\mathrm{damage}_{\mathrm{local}}(i,j) =
\begin{cases}$
$A_{\mathrm{src}}$ , & $\sqrt{(i-N/2)^2+(j-N/2)^2}\le r$ , $\\[4pt]$
0, & \text{otherwise}.
\end{cases}
\]

The default reference seed used in the matched and finite-size studies is

\[
r=5,
\qquad
A_{\mathrm{src}}=1.2\times10^{-3}.
\]

Additional seed studies varied

\[
r\in\{3,5,7,10\},
\qquad
A_{\mathrm{src}}\in\{0.8,1.2,1.6\}\times10^{-3}.
\]

## 4. Neighbor-failed density

Propagation depends on the nearest-neighbor failed density

\[
f_{\mathrm{neigh}}(i,j)=\frac14\sum_{\text{4 nn}}\Theta\big(\alpha_{\mathrm{fail}}-\alpha_{\mathrm{nn}}\big),
\]

where the sum runs over the four nearest neighbors.

## 5. Spread laws

Two spread kernels were studied.

### 5.1 Smooth proportional law

The baseline spread law is proportional both to failed-neighbor density and local weakness:

\[
\mathrm{damage}_{\mathrm{spread}}\propto \eta\,f_{\mathrm{neigh}}\,(1-\alpha).
\]

This is the baseline infection rule.

### 5.2 Gated frontier law

The comparison law imposes simultaneous local weakness and failed-neighbor gating:

\[
\mathrm{damage}_{\mathrm{spread}}\propto
\eta\,
\max(1-\alpha-0.015,0)
\,\max(f_{\mathrm{neigh}}-0.25,0).
\]

This law makes frontier transmission more selective and therefore less efficient at long-range propagation.

## 6. Depletion and healing dynamics

The depletion field evolves by

\[
D\leftarrow (1-\delta_{\mathrm{decay}})D
+g_{\mathrm{dep}}\big(\mathrm{damage}_{\mathrm{local}}+\mathrm{damage}_{\mathrm{spread}}\big),
\]

with parameters

\[
\delta_{\mathrm{decay}}=0.003,
\qquad
g_{\mathrm{dep}}=0.35.
\]

Healing scales with weakness rather than already healthy cells:

\[
\mathrm{heal}=\eta_{\mathrm{heal}}(1-\alpha)^p(1-D),
\]

with

\[
\eta_{\mathrm{heal}}=0.060,
\qquad
p=1.2.
\]

This specific form matters because earlier healing forms that scaled with healthy-cell abundance artificially pinned the system too close to \(\alpha=1\), obscuring the transition.

## 7. Frontier renormalization

The second-axis mechanism weakens healing near failed neighbors:

\[
\mathrm{heal}\leftarrow \mathrm{heal}\,(1-0.25\,f_{\mathrm{neigh}}).
\]

This is the frontier-renormalization term. It is the dominant control mechanism identified by the numerical program. It suppresses healing precisely where the damage front must decide whether to stall or remain transmissive.

## 8. Health update

The total damage is

\[
\mathrm{damage}_{\mathrm{total}}=
\mathrm{damage}_{\mathrm{local}}+
\mathrm{damage}_{\mathrm{spread}}.
\]

The health field update is

\[
\alpha\leftarrow \alpha-
\mathrm{damage}_{\mathrm{total}}-
\delta_{\mathrm{drag}}D+
\mathrm{heal},
\]

with

\[
\delta_{\mathrm{drag}}=0.004.
\]

## 9. Observables

Because the transition is geometric and topological, several observables are needed.

### 9.1 Failure fraction

\[
F=\left\langle \Theta(\alpha_{\mathrm{fail}}-\alpha)\right\rangle.
\]

### 9.2 Geometric susceptibility proxy

The susceptibility proxy used in the numerical program is

\[
\chi_{\mathrm{geom}}=F\cdot\lambda,
\qquad
\lambda=1-\langle\alpha\rangle.
\]

Equivalent notation used during the study is

\[
\chi_{\mathrm{geom}}=\overline F\,\overline w.
\]

### 9.3 Largest failed cluster and growth rate

Let \(S_{\max}(t)\) be the size of the largest connected failed cluster under four-neighbor connectivity. Its discrete growth rate is

\[
\Gamma(t)=S_{\max}(t)-S_{\max}(t-1).
\]

After nucleation, \(\Gamma=0\) indicates a stalled front, whereas sustained positive \(\Gamma\) indicates active frontier propagation.

### 9.4 Spanning indicator

A run is classified as spanning when a connected failed cluster satisfies the implemented lattice-scale spanning criterion. This is the operational percolation marker.

### 9.5 Coarse-grained front velocity

To convert cluster growth into a propagation observable, define

\[
R_{\mathrm{eff}}(t)=\sqrt{\frac{S_{\max}(t)}{\pi}},
\qquad
v_f=\left\langle \frac{dR_{\mathrm{eff}}}{dt}\right\rangle.
\]

The average is taken in the steady-growth regime after core formation and before finite-size saturation.

### 9.6 Sampling horizon

Observables were sampled every 20 steps. Near-threshold runs were extended up to 50,000 steps where necessary. This is important because shorter horizons produced at least one false impression of a higher threshold that was later identified as a finite-time artifact.

## 10. Baseline smooth-law phase structure

With the smooth proportional infection law and without second-axis frontier renormalization, the model supports spanning only above a relatively high threshold. The consolidated result is

\[
\eta_c^{\mathrm{baseline}}\approx 0.50.
\]

Operationally,

- below about \(0.45\), failed seeds may form but do not robustly span within the tested horizon,
- near \(0.50\), spanning appears after long times,
- above \(0.50\), the system is clearly supercritical.

This establishes that HPF-style geometry degradation can become self-propagating even without frontier renormalization, but only behind a comparatively high barrier.

## 11. Second-axis frontier renormalization and threshold collapse

When healing is weakened locally near failed neighbors, the phase structure changes substantially. Early low-\(\eta\) tests at

\[
0.30,\;0.35,\;0.40,\;0.45,\;0.50
\]

all produced robust failed-cluster growth, immediately implying that the growth threshold had already moved below \(0.30\).

A refined 30,000-step low-\(\eta\) scan gave:

- \(\eta=0.38\): spans at approximately \(13{,}800\) steps,
- \(\eta=0.36\): spans at approximately \(15{,}600\) steps,
- \(\eta=0.34\): spans at approximately \(18{,}200\) steps,
- \(\eta=0.32\): spans at approximately \(24{,}500\) steps,
- \(\eta=0.30\): does not span and stalls asymptotically with large \(S_{\max}\).

This locks the second-axis thresholds at

\[
\eta_{\mathrm{growth}}^{\mathrm{second-axis}}<0.30,
\qquad
\eta_{\mathrm{span}}^{\mathrm{second-axis}}\approx 0.31.
\]

On the reference \(N=128\) lattice, the effective spanning threshold is therefore

\[
\eta_c^{\mathrm{second-axis}}\approx 0.31.
\]

This is the central numerical result of the model: frontier renormalization does not merely accelerate an existing mechanism; it opens a substantially broader supercritical phase.

## 12. Source dependence

The source bundle tested whether this threshold reduction was mainly a seed artifact by varying source radius and source amplitude under the locked second-axis law. At fixed

\[
N=128,
\qquad
\eta=0.35,
\qquad
\text{30,000-step horizon},
\]

mini-sweeps near threshold gave:

- weakest tested seed: \(\eta_c\approx 0.37\),
- strongest tested seed: \(\eta_c\approx 0.27\),
- default reference seed: \(\eta_c\approx 0.31\).

Thus the total seed-induced threshold shift is only

\[
\Delta\eta_c\approx \pm 0.06.
\]

Source strength matters, but only secondarily. The dominant control is frontier renormalization rather than seed size or amplitude.

## 13. Finite-size scaling

To test thermodynamic persistence of the lowered threshold, the locked second-axis model with the reference seed was simulated at

\[
N=64,\;128,\;256,\;512.
\]

The effective spanning thresholds were

\[
\eta_c(N)=0.34,\;0.31,\;0.305,\;0.302,
\]

respectively.

Fitting

\[
\eta_c(N)=\eta_c(\infty)+A N^{-1/\nu}
\]

gives

\[
\eta_c(\infty)\approx 0.300,
\qquad
\nu\approx 1.36\pm0.04.
\]

The source bundle interprets this as consistent with 2D percolation-like scaling within numerical uncertainty, while explicitly avoiding an overclaimed universality-class result. The conservative statement is that the lowered threshold survives thermodynamic extrapolation:

\[
\eta_c^{(\infty;\,\mathrm{second\ axis})}\approx 0.30.
\]

## 14. Matched smooth-versus-gated comparison

Under identical second-axis conditions,

\[
N=128,
\qquad \text{seed}=42,
\qquad r=5,
\qquad A_{\mathrm{src}}=1.2\times10^{-3},
\qquad \text{30,000-step horizon},
\]

a matched comparison was performed between the smooth and gated spread laws.

The results are:

| Spread law | effective \(\eta_c\) | first \(\chi_{\mathrm{geom}}>0.001\) at \(\eta=0.35\) | first span at \(\eta=0.35\) |
|---|---:|---:|---:|
| Smooth | 0.31 | \(\sim 1100\) | \(\sim 13{,}800\) |
| Gated frontier | 0.47 | \(\sim 1150\) | \(\sim 26{,}400\) |

The threshold shift is

\[
\Delta\eta_c\approx +0.16.
\]

The structural meaning is that ignition timing is nearly unchanged, but long-range propagation is much slower for the gated rule. Spread-law shape therefore acts primarily on transmission efficiency across an already prepared frontier rather than on initial failed-seed formation.

## 15. Front velocity as the propagation order parameter

The matched comparison is captured cleanly by the coarse-grained front velocity. Under the same second-axis conditions at \(\eta=0.35\),

\[
v_f^{\mathrm{smooth}}\approx 0.0047\ \text{cells/step},
\qquad
v_f^{\mathrm{gated}}\approx 0.0020\ \text{cells/step}.
\]

Thus the smooth rule propagates about

\[
\frac{0.0047}{0.0020}\approx 2.3
\]

times faster.

At the respective critical points for each kernel, \(v_f\to 0\). This motivates the macroscopic phase interpretation:

- \(v_f>0\): propagating phase,
- \(v_f\to 0\): critical boundary,
- stalled front: subcritical regime.

This yields the chain

\[
\text{microscopic spread rule}
\to
\text{front transmission efficiency}
\to
\text{macroscopic spanning threshold}.
\]

## 16. Phase hierarchy and control hierarchy

The simulations support a structured phase hierarchy:

\[
\text{localized weakening}
\to
\text{failed-seed nucleation}
\to
\text{sustained front growth}
\to
\text{spanning percolation}.
\]

They also support a clean control hierarchy:

1. frontier-renormalization physics,
2. infection-kernel form and the resulting \(v_f\),
3. seed and source variation.

This separation matters because it shows that the phase boundary is not accidental. The same model contains all regimes, but different mechanisms dominate at different stages.

## 17. Relation to geometry-validity loss

Within the broader HPF interpretation, this lattice model operationalizes geometry-validity loss rather than literal substrate illegality. The health field \(\alpha\) is an execution-quality variable, and the susceptibility proxy \(\chi_{\mathrm{geom}}\) tracks whether failed regions remain sparse and healable or become persistent and transmissive.

The conservative interpretation is therefore:

- the model provides evidence for a finite-threshold transition from local geometric damage to self-propagating geometry failure,
- the observed percolation threshold is a simulation-level realization of geometry-validity loss,
- the threshold values are not yet a first-principles derivation of the full framework quantity \(\Lambda_c^{(\mathrm{geom})}\),
- the model supports but does not itself complete the broader bridge from HPF legality to full geometric validity theory.

## 18. Final results statement

The consolidated quantitative findings are:

\[
\eta_c^{\mathrm{baseline}}\approx 0.50,
\]

\[
\eta_c^{\mathrm{second-axis}}\approx 0.31 \quad (N=128),
\]

\[
\eta_c(\infty)\approx 0.300,
\qquad
\nu\approx 1.36\pm0.04,
\]

\[
\Delta\eta_c^{\mathrm{seed}}\approx \pm0.06,
\]

\[
\eta_c^{\mathrm{smooth}}\approx0.31,
\qquad
\eta_c^{\mathrm{gated}}\approx0.47,
\qquad
\Delta\eta_c\approx+0.16,
\]

\[
v_f^{\mathrm{smooth}}\approx0.0047\ \text{cells/step},
\qquad
v_f^{\mathrm{gated}}\approx0.0020\ \text{cells/step}.
\]

These results support the claim that, in this HPF lattice realization, geometry failure is not merely local or metastable. It can become self-propagating and percolative once neighbor-coupled spread exceeds a finite threshold, and the dominant mechanism controlling that threshold is healing suppression at the failed frontier.
