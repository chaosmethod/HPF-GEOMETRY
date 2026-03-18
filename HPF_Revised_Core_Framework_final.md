# HPF Revised Core Framework

## 1. Scope and status

This document is the canonical framework statement for the Holographic Projection Framework (HPF). HPF is not an object-level gravity model and not a phenomenological stability fit. HPF is the regulatory execution framework that defines legality conditions for physical evolution, constrains expert validity, and governs routing between effective and substrate-level theories. Geometry and gravity appear only as one valid expert regime inside HPF. QPRCA appears as a deeper substrate-level expert that must be used when geometry ceases to be legal or ceases to be valid.

The consolidated source set supports five classes of statements, which are kept distinct throughout:

- **Fundamental:** finite-capacity, finite-resolution, local, reversible execution laws and the substrate load tensor.
- **Effective:** geometry/gravity as an emergent expert regime and coarse-grained bridge laws.
- **Derived:** routing law, legality functionals, weak-field bridge relations, and coarse-grained stability functionals.
- **Empirical / simulation-based:** percolation thresholds, finite-size scaling, front velocities, and related geometry-failure observables.
- **Open / programmatic:** first-principles construction of the geometry-validity threshold, full microscopic construction of the legality functional from QPRCA dynamics, and complete elimination of residual phenomenological parameters by substrate derivation.

HPF therefore provides a layered execution architecture rather than a single object-level theory.

## 2. Ontology and motivation

HPF starts from the claim that physical structure should be treated as execution on a bounded substrate rather than as unconstrained continuum ontology. The primitive question is not “what continuum field exists everywhere?” but “what local updates are legal, what effective descriptions remain valid, and when must execution route to a deeper substrate expert?”

The role of HPF is to regulate this execution. It enforces hard constraints, tracks load, distinguishes legality from validity, and selects the expert whose domain assumptions remain satisfied. In this sense HPF functions as a physics operating system. The expert layers do object-level work; HPF governs when those layers may or may not be trusted.

## 3. Core axioms

The framework is defined by the following axioms.

### 3.1 Finite capacity

All regions possess bounded update bandwidth. The local load variable is bounded:

$\[
0 \le \Lambda \le 1
\]$

The load variable represents fractional consumption of local update capacity. Saturation is therefore physically meaningful rather than a coordinate artifact.

### 3.2 Finite resolution

No legal state requires infinite precision. Singular states are not fundamental legal states.

### 3.3 Locality

All fundamental updates are local.

### 3.4 Reversibility

Microscopic evolution is bijective.

### 3.5 Conservation

At the effective level the load tensor satisfies

$\[
\nabla_\mu \Lambda^{\mu\nu}=0
\]$

These axioms are sovereign over all expert layers. Any object-level theory used inside HPF must be interpreted subject to them.

## 4. Primitive substrate object: the load tensor

The microscopic primitive is the substrate load tensor

$\[
\Lambda^{(\mathrm{sub})}_{\mu\nu}(x)
\]$

Its defining properties are:

- dimensionless,
- local,
- bounded,
- conserved in the effective description,
- interpretable as directional depletion of update capacity.

The canonical component meanings are

$\[
\Lambda_{00}=\Lambda_0 \quad \text{temporal capacity depletion},
\]$

$\[
\Lambda_{0i} \quad \text{directional load flow},
\]$

$\[
\Lambda_{ij} \quad \text{anisotropic transport load}.
\]$

This tensor is fundamental to the framework. Geometry, stress-energy analogs, validity margins, and routing conditions are downstream constructions from it.

## 5. Execution-health variables

The canonical geometry-viability quantity is

$\[
G_{\mathrm{health}} = 1-\Lambda_0
\]$

This is not the whole regulator. It is a key local viability observable extracted from substrate load. It measures the remaining margin before temporal execution capacity is exhausted.

A reduction in $\(G_{\mathrm{health}}\)$ indicates that geometry is becoming a less reliable effective description. A value near zero indicates that the substrate is approaching full local saturation.

## 6. Legality versus validity

HPF requires an explicit distinction between legality and validity.

### 6.1 Legality

A state or evolution is **legal** if it satisfies substrate constraints. At minimum, legality requires bounded load, finite resolution, locality, reversibility, and closure of the relevant update structure. Legality is therefore framework-level and substrate-sensitive.

The source bundle gives the local substrate legality functional in schematic form as

$\[
L_{\mathrm{QPRCA}}(x)=1 \iff F(x)<1,
\]$

where \(F(x)\) aggregates channel occupancy, blocked transport fraction, reservoir or relaxation burden, directional anisotropy, and reversible update closure. Failure occurs when

$\[
F(x)\ge 1
\]$

### 6.1.1 Candidate Microscopic Legality Functional $\(F(x)\)$  
**[DERIVED / PROPOSED]**

This section explores candidate realizations of the microscopic legality functional $\(F(x)\)$ whose five-component schematic checklist is given above. $\(F(x)\)$ belongs strictly to the substrate-expert level and is used by the MDEA routing kernel to enforce the HPF hard wall $\(L_{\mathrm{QPRCA}}(x)=1\) iff \(F(x)<1\)$ . No full derivation from QPRCA dynamics is claimed.

**A. Conservative candidate constitutive form (additive)**  

$$
\[
F(x) = w_1 \cdot (	ext{channel occupancy}) + w_2 \cdot (	ext{blocked transport fraction}) + w_3 \cdot (	ext{reservoir / relaxation burden}) + w_4 \cdot (	ext{directional anisotropy}) + w_5 \cdot (	ext{reversible-update closure deficit}),
\]
$$

with weights $\(w_i \ge 0\)$ and $\(\sum w_i = 1\)$ . This is the direct linear realization of the five named channels.

**B. Alternative non-additive form (dominant-channel max)**  


$$
F(x) = \max \left( 
  \text{channel occupancy}, \quad 
  \text{blocked transport fraction}, \quad 
  \text{reservoir burden}, \quad 
  \text{directional anisotropy}, \quad 
  \text{reversible-update closure deficit} 
\right)
$$



This selects the single worst local burden at each site.

**C. Properties any legal $\(F(x)\)$ must satisfy**  

Any admissible $\(F(x)\)$ must:  
- be non-negative and bounded above by a finite value,  
- increase monotonically with each of the five channels,  
- be compatible with the coarse-grained conservation structure $\(
abla_\mu \Lambda^{\mu
u}=0\)$ ,  
- remain local (depend only on quantities at $\(x\)$ or its immediate neighborhood),  
- preserve the finite-capacity axiom (saturation at any single channel must be able to reach the legality boundary).

**D. Conditions under which $\(F(x) < 1\)$ remains a sensible hard wall**  

\(F(x) < 1\) is a sensible hard wall if:  
- each individual channel is normalized to lie in \([0,1]\),  
- the aggregation rule never allows one channel to exceed 1 without forcing \(F \ge 1\),  
- the boundary is approached continuously from below as any channel saturates,  
- the condition is compatible with reversibility and locality (no instantaneous global dependence).

**E. What remains open**  

The exact functional form, the values of any weights or saturation parameters, and the microscopic update rules that generate each of the five channels from QPRCA dynamics remain open/programmatic. No candidate above is claimed to be canonical or derived from first principles.


This is a hard-wall criterion. The associated microscopic saturation boundary is exact:

\[
\Lambda_c^{(\mathrm{sub})}=1.
\]

That result follows directly from finite capacity. When local capacity is fully consumed, no further legal transport or redistribution is available.

### 6.2 Validity

A theory or expert can be legal yet not valid as an effective description. Geometry is the main example. Even while the substrate remains legal, geometry may already have lost the margin required for a coarse-grained metric description to remain reliable.

Hence:

- **Legality** asks whether the substrate-level evolution is admissible.
- **Validity** asks whether a chosen expert remains trustworthy in that legal region.

This distinction is central. HPF does not wait for literal substrate saturation before routing away from geometry.

## 7. Hard walls and thresholds

Two thresholds must be kept separate.

### 7.1 Substrate hard wall

The microscopic saturation wall is

\[
\Lambda_c^{(\mathrm{sub})}=1.
\]

This is fixed by axiom and is not phenomenological.

### 7.2 Geometry-validity threshold

The geometry-validity threshold is lower:

\[
\Lambda_c^{(\mathrm{geom})}<1.
\]

Geometry remains valid only while the coarse-grained execution burden remains below this threshold. The exact numerical value of \(\Lambda_c^{(\mathrm{geom})}\) is not yet derived from first principles in the source set. Determining it is an open closure problem.

## 8. MDEA routing law

The expert-routing kernel is the Mixture-of-Domain-Experts Architecture (MDEA). It governs which expert evolves the state at the next step:

\[
X_{t+1}=F_{E^*}(X_t),
\]

with

\[
E^*=\operatorname*{argmax}_E \big[ V_{\mathrm{HPF}}(E,X)\,L_{\mathrm{HPF}}(E,X) \big].
\]

Here \(V_{\mathrm{HPF}}\) encodes expert validity and \(L_{\mathrm{HPF}}\) encodes legality compatibility under HPF constraints.

This law is regulatory, not object-level. MDEA is therefore not “one more theory.” It is the routing kernel that selects among theories or expert regimes.

## 9. Hard routing gates

The consolidated source set specifies explicit hard gates:

\[
G_{\mathrm{health}}<0.3 \;\Longrightarrow\; \text{route to QPRCA},
\]

\[
\sigma_{\max}>1 \;\Longrightarrow\; \text{route to saturation regime}.
\]

The first gate states that when geometry viability drops below the specified margin, the geometry expert is no longer trusted and execution must hand off to the deeper substrate-level expert. The second gate captures a saturation-driven routing boundary.

The key rule from the source bundle is:

> the geometry expert is used unless it fails legality.

Combined with the legality-validity distinction developed above, the canonical interpretation is:

1. geometry is preferred when its regime assumptions hold,
2. geometry may be rejected either because it violates legality compatibility or because it loses validity margin,
3. QPRCA is the deeper destination when geometry can no longer be safely used.

## 10. Soft routing weights and the stability functional

The source bundle also includes a soft routing weight based on load statistics. This is not the regulator itself and must not be mistaken for HPF. It is a coarse-grained weighting factor that modulates routing confidence near regime boundaries.

Define a flux ratio or throughput ratio \(S_f\). The stability functional is

\[
\xi(S_f)=P\big(\Lambda^{(b)}<\Lambda_c\big).
\]

Assuming coarse-grained load statistics

\[
\Lambda^{(b)}\sim \mathcal N(\mu(S_f),\sigma^2),
\qquad
\mu(S_f)\approx \alpha S_f,
\]

one obtains

\[
\xi(S_f)=\Phi\!\left(\frac{\Lambda_c-\alpha S_f}{\sigma}\right)
\approx \frac{1}{1+e^{k(S_f-\lambda)}}.
\]

Parameter identification gives

\[
\lambda = \frac{\Lambda_c}{\alpha},
\qquad
k=\frac{\alpha}{\sigma},
\]

or, more generally when \(\mu(S_f)\approx \alpha S_f+\beta\),

\[
\lambda = \frac{\Lambda_c^{(\mathrm{geom})}-\beta}{\alpha}.
\]

This logistic form is therefore an emergent coarse-grained survival probability for geometry validity. It is not fundamental, not the regulator itself, and not a substitute for hard legality gates.

## 11. Coarse-graining and renormalization structure

For block size \(b\), define block-averaged load

\[
\Lambda^{(b)}_{\mu\nu}(X)=\frac{1}{b^3}\sum_{x\in B_X}\Lambda^{(\mathrm{sub})}_{\mu\nu}(x).
\]

The geometry-level effective load is

\[
\Lambda^{(\mathrm{geom})}_{\mu\nu}=Z_\Lambda(b)\,\Lambda^{(b)}_{\mu\nu},
\]

with leading-order renormalization factor

\[
Z_\Lambda(b)\approx 1.
\]

Fluctuations are suppressed under coarse-graining as

\[
\delta\Lambda^{(b)}\sim b^{-3/2}\,\delta\Lambda.
\]

This supplies the basic route by which noisy microscopic load becomes a smooth geometry-compatible effective source.

## 12. Relation to QPRCA

QPRCA is the deeper substrate-level expert invoked when geometry fails. It is not identical to HPF. HPF governs legality and routing; QPRCA is one substrate expert that can realize microscopic legality conditions and carry execution when geometry is no longer valid.

The source bundle states the key completion program explicitly:

1. construct \(F(x)\) from QPRCA dynamics,
2. define \(\chi_{\mathrm{geom}}\) explicitly,
3. measure \(\Lambda_c^{(\mathrm{geom})}\),
4. derive \(\mu(S_f)\),
5. eliminate residual phenomenological parameters such as \(\lambda\).

This means the HPF–QPRCA relation is already conceptually fixed but not fully closed in first-principles executable detail.

## 13. Geometry as an emergent expert regime

Geometry is not fundamental in HPF. It is an emergent, coarse-grained execution regime that becomes valid only when:

- load remains sufficiently below the substrate hard wall,
- anisotropy remains controlled,
- blockage relaxes rather than persists,
- depletion heals rather than accumulates,
- coarse-grained fluctuations remain small enough for metric closure.

The geometry expert is therefore subordinate to the regulator and must hand off when its domain fails. No geometry-based argument can override HPF legality.

## 14. Failure order parameters and validity diagnostics

The source set introduces both substrate-level and geometry-level order parameters.

At the substrate level, a failure order parameter \(\chi_{\mathrm{fail}}\) is defined schematically by

\[
\chi_{\mathrm{fail}}=0 \text{ below threshold},
\qquad
\chi_{\mathrm{fail}}>0 \text{ above threshold},
\]

with candidate observables including persistent blocked transport fraction, non-decaying backlog, and reservoir debt accumulation. The exact microscopic critical point satisfies

\[
\Lambda_c^{(\mathrm{sub})}=\inf\{\Lambda: \chi_{\mathrm{fail}}>0\}=1.
\]

At the geometry level, an executable coarse-grained validity burden is introduced:

\[
\chi_{\mathrm{geom}}(X)=w_B\,\overline B(X)+w_A\,\overline A(X)+w_D\,\overline D(X),
\qquad w_B,w_A,w_D>0,
\]
with typically
\[
w_B+w_A+w_D=1.
\]

Here

\[
\overline B(X)=\frac{1}{|X|}\sum_{x\in X}\limsup_{T\to\infty}\frac{1}{T}\sum_{t=1}^T b(x,t)
\]

measures persistent blocked-transport fraction,

\[
\overline A(X)=\frac{1}{|X|}\sum_{x\in X}\frac{\sum_i |\Lambda_{0i}(x)|}{\Lambda_0(x)+\varepsilon},\qquad \varepsilon>0
\]

measures anisotropy burden, and

\[
\overline D(X)=\frac{1}{|X|}\sum_{x\in X}\limsup_{T\to\infty}\frac{1}{T}\sum_{t=1}^T \max\big(0,\Delta\Lambda_0(x,t)\big)
\]

measures depletion or debt persistence.

Geometry is stable when

\[
\chi_{\mathrm{geom}}(X)\to 0,
\]

and invalid when the coarse-grained burden remains persistently nonzero:

\[
\limsup_{T\to\infty}\chi_{\mathrm{geom}}(X)>0.
\]

This gives the operational threshold definition

\[
\Lambda_c^{(\mathrm{geom})}=\inf\Big\{\Lambda_0^{(\mathrm{geom})}: \limsup_{T\to\infty}\chi_{\mathrm{geom}}>0\Big\}.
\]

This construction is stronger than a purely verbal notion of breakdown, but the source set still treats full closure as incomplete.

## 15. Symbol normalization

The canonical notation fixed by the source bundle is:

\[
\Lambda_{\mu\nu} \text{ load tensor},\qquad
\Lambda_0 \text{ temporal load component},
\]
\[
\Xi \text{ load-to-energy-density bridge},\qquad
T_{\mu\nu} \text{ effective stress-energy},
\]
\[
a \text{ lattice spacing},\qquad
\Delta t \text{ update interval},\qquad
c=a/\Delta t,
\]
\[
G_{\mathrm{health}}=1-\Lambda_0,
\]
\[
\rho_{\mathrm{HPF}} \text{ effective load density},\qquad
j_i^{\mathrm{HPF}} \text{ load current},\qquad
\Pi_{ij}^{\mathrm{HPF}} \text{ stress tensor},
\]
\[
\Phi_g,\; A_i^{(g)},\; E_g,\; B_g \text{ gravitational analog potentials and fields},
\]
\[
\kappa \text{ Einstein normalization},\qquad
b \text{ coarse-graining scale},\qquad
Z_\Lambda(b) \text{ RG factor}.
\]

## 16. Solved, derived, and open components

### 16.1 Solved / fixed at framework level

The following are fixed by the consolidated source set:

- HPF core axioms.
- The existence and interpretation of the substrate load tensor.
- The exact microscopic saturation wall \(\Lambda_c^{(\mathrm{sub})}=1\).
- The distinction between legality and validity.
- The role of MDEA as routing kernel.
- The hard routing gates \(G_{\mathrm{health}}<0.3\to \mathrm{QPRCA}\) and \(\sigma_{\max}>1\to\) saturation regime.
- The non-fundamental status of the soft stability functional \(\xi(S_f)\).
- The status of geometry as an emergent expert regime rather than the regulator.

### 16.2 Derived but still regime-limited

The following are already derived in useful form but are effective rather than fundamental:

- coarse-grained load averaging,
- fluctuation suppression under coarse-graining,
- geometry-level burden diagnostic \(\chi_{\mathrm{geom}}\),
- probabilistic stability functional \(\xi(S_f)\),
- load-to-stress-energy bridge relations used by the geometry/gravity expert.

### 16.3 Open / programmatic

The following remain open or only partially closed:

- first-principles construction of \(F(x)\) directly from detailed QPRCA dynamics,
- first-principles derivation or measurement program for \(\Lambda_c^{(\mathrm{geom})}\),
- full derivation of \(\mu(S_f)\) from substrate statistics,
- complete elimination of phenomenological remnants in soft routing weights,
- broader closure of all expert handoff boundaries from microscopic legality alone.

## 17. Final framework statement

HPF is the regulatory legality framework for bounded physical execution. MDEA is the routing kernel that selects among expert regimes under HPF constraints. Geometry and gravity are effective experts valid only in a restricted coarse-grained domain. QPRCA is the deeper substrate-level expert to which execution must hand off when geometry no longer remains legal or valid. The soft stability functional is a secondary coarse-grained routing weight and is not the regulator itself.

That layered separation is canonical and must not be collapsed.
