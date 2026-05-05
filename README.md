<p align="center"><img src="assets/logo.jpg" height="80" alt="Williams &amp; Williams PTY (LTD)"/></p>
# Neutrino Absolute Mass Derivation

**Persistence; The Theorem of Everything — Tier 1 Reviewer Repository**

**Author:** Camron Williams · Williams & Williams PTY (LTD)
**License:** [Tier 1 Reviewer License] — USD 25 / month, max 3 months
**Lean version:** see [`lean-toolchain`](lean-toolchain)
**Scope:** 10 files — the complete derivation chain for the neutrino mass predictions
**Build:** 0 `sorry` · 0 custom axioms · kernel base: `{propext, Classical.choice, Quot.sound}`
**Zenodo DOI:** [10.5281/zenodo.20027419](https://doi.org/10.5281/zenodo.20027419)
**Bitcoin notarisation:** blocks 947159–947160 (OpenTimestamps)

---

## What This Proves

Three absolute neutrino mass predictions derived from first-principles geometry.
D = 4 is forced as a theorem — not a postulate.

| Prediction | Exact value | Falsified by |
|---|---|---|
| m₁ | 0 exactly | Any measurement m₁ > 1 meV |
| m₃ | 1/20 eV = 50 meV exactly | KATRIN / PTOLEMY at ~10% precision |
| Σmν | ≈ 58.66 meV | CMB-S4 / Planck (current bound: < 120 meV) |

The primary falsification target is the dimensionless splitting ratio:

> Δm²₃₁ / Δm²₂₁ = 100/3 ≈ 33.333...

This ratio is unit-free and independent of any Dirac/Majorana assumption or cosmological prior.
Zero free parameters. Every prediction is an unconditional Lean 4 theorem.

---

## Derivation Chain

```
D = 4   (theorem: D4_unique_rank_all_N, D4_unique_for_SM)
  |
  +-- Lattice  L = Z/6Z x Z/7Z,  |L| = 42
  |    `-- Z/7Z has exactly one self-conjugate mode: k = 0
  |         (proved by `decide`: 2k = 0 mod 7 iff k = 0, since gcd(2,7) = 1)
  |
  +-- m1  = 0 exactly            (m1^2 = k^2 * dm21^2  at  k = 0)
  +-- m3  = 1/20 eV = 50 meV    (m3^2 = 1/(4(D+1))^(D-2) at D = 4)
  `-- Smv ~ 58.66 meV            (normal hierarchy; inverted hierarchy excluded)
```

---

## File Scope (Tier 1)

This package contains exactly the 10 files in the neutrino derivation chain. The Lean module
namespace is `TheTheorem`, matching the canonical *Persistence; The Theorem of Everything*
formal-verification project:

```
TheTheorem/
  Chapter1_Foundations/
    Constants.lean                  -- R, delta, tau derived from D=4
    Geometry.lean                   -- D=4 torus T^4 structure
    D4Uniqueness.lean               -- D=4 is the unique solution (D4_unique_rank_all_N)
  Chapter2_Geometry/
    Universal_Wave_Function.lean    -- psi on T^4
  Chapter3_WaveFunction/
    Quantum_Postulates.lean         -- quantum structure on L = Z/42Z
  Chapter6_Physics/
    StandardModel.lean              -- SU(3) x SU(2) x U(1) from 42 = 2 x 3 x 7
    Neutrinos.lean                  -- mixing angles, mass-squared splittings, ratio = 100/3
    NeutrinoAbsoluteMasses.lean     -- m1 = 0, m3 = 50 meV, Smv ~ 58.66 meV
  Chapter13_UniversalLaws/
    AllUniversalLaws.lean           -- 185 universal-law theorems used by the chain
  Chapter14_Audit/
    HeadlineAxioms.lean             -- #print axioms for every cited theorem
```

No consciousness modules. No Clay Prize bridges. No AI or biology extensions.

---

## Verify in 3 Steps

```bash
# 1. Install Lean 4 + Lake
#    https://leanprover.github.io/lean4/doc/setup.html

# 2. Clone and build
git clone https://github.com/Williams-and-Williams-PTY-LTD/Neutrino-Absolute-Mass-Derivation
cd Neutrino-Absolute-Mass-Derivation
lake build

# 3. Check axioms
#    Open TheTheorem/Chapter14_Audit/HeadlineAxioms.lean in VS Code
#    with the Lean 4 extension. Every #print axioms line should list only:
#      [propext, Classical.choice, Quot.sound]
```

The CI workflow (`.github/workflows/verify.yml`) runs `lake build` and asserts
`sorryAx` is absent from the axiom chain on every dispatch.

---

## Falsification Targets

| Experiment | Observable | Falsifies if |
|---|---|---|
| **JUNO** (primary) | Δm²₃₁/Δm²₂₁ | Outside [32, 34] at > 5σ |
| JUNO | Δm²₂₁ | Outside [7.4, 7.6] × 10⁻⁵ eV² |
| KATRIN (direct β) | m(νe) | > 0.45 eV |
| PTOLEMY | tritium end-point | m₁ > 1 meV |
| CMB-S4 / Planck | Σmν | > 120 meV or < 50 meV |
| T2K / NOvA / IceCube | mass ordering | Inverted hierarchy confirmed |

No rescue condition exists for the splitting ratio. The theorem either holds or is refuted.

---

## Bitcoin Notarisation

- **Block 947159** — `d459f11db97ab6c78b0f0d02e29b513ecd1fd2ac24d0882b39e8cc988280a31b`
- **Block 947160** — `548fcf273927f16948039827c53b479078fc77e7f93a727a3576a2773c68cab2`

---

## Access

This repository (Tier 1) is the **10-file reviewer slice** of a much larger
formally verified corpus. The table below shows what each tier unlocks. Every
tier above Tier 0 is enquiry-first and personally approved by the author.

| Tier | Scope | Commercial use | How to obtain |
|---|---|:---:|---|
| **Tier 0 — Reader** (free) | Whitepaper, abstracts, audit reports, this README, all press-kit docs. No source. | ❌ | Public — cite per the BibTeX block below. |
| **Tier 1 — Reviewer** (this repo, USD 25 / mo, max 3 months) | Read-only access to the 10 `.lean` files in the neutrino-derivation chain. Build, `#print axioms`, publish a written review citing ≤ 50 lines per published review. | ❌ | Email `camron.d.williams@gmail.com`, subject `[ACCESS POLICY] Tier 1 — <intent>`. PayPal link issued on written approval. |
| **Tier 2 — Researcher** (by application; non-commercial; pricing private) | Read-only access to the **full 291-file Lean 4 corpus** across all 14 chapters — every theorem, every audit file. Build, verify, cite any theorem in academic publications. | ❌ | Email subject `[ACCESS POLICY] Tier 2 — <institution and intent>`. Intent review required. |
| **Tier 3 — Commercial** (by application; pricing private) | Full Tier 2 access **plus** the right to use the corpus in commercial products, internal tooling, and revenue-generating research within a single named legal entity. No sub-licensing; no AI training on the verbatim corpus. | ✅ (internal) | Email subject `[ACCESS POLICY] Tier 3 — <entity and intent>`. |
| **Tier 4 — Acquisition** (singular instrument; pricing private) | Full IP transfer of the entire derivation corpus **and the application base built on it** — Lean 4 corpus, C runtime (`n3o`), all proof artefacts, derivation extensions, downstream application layers. Includes sub-licensing, AI-training, right-of-first-refusal on future theorems. One buyer, one transfer permitted. | ✅ (full) | Email subject `[ACCESS POLICY] Tier 4 — <entity>`. |

**Right-to-buy is not right-to-receive.** No payment is accepted before the author's written approval. Any payment tendered before approval is refunded in full and confers no rights of any kind.

**Contact:** camron.d.williams@gmail.com
**ORCID:** [0009-0007-1228-2462](https://orcid.org/0009-0007-1228-2462)


---

## Corpus Overview (what Tier 2+ unlocks)

The Tier 1 slice in this repository (10 files) is the experimentally-falsifiable
neutrino chain. The full machine-verified corpus is **291 Lean 4 source files
across 14 chapters** — 545 headline-audited theorems, 0 `sorry`, 0 custom axioms.
The table below shows the structure (no theorem statements disclosed at this
tier; available at Tier 2+ on approval).

| Chapter | Files | Domain |
|---|---:|---|
| `Chapter1_Foundations` | 13 | Uniqueness of `D = 4`; lattice trajectories; physical-process axiomatisation |
| `Chapter2_Geometry` | 37 | Torus & lattice geometry; CRT isomorphism `Z/42Z ≅ Z/6Z × Z/7Z` |
| `Chapter3_WaveFunction` | 16 | Wave-function propagation, Born rule, superposition on `T⁴` |
| `Chapter4_Symmetry` | 20 | Gauge theory: `G_SM = SU(3) × SU(2) × U(1)` from `42 = 2·3·7`; `α_s = 15/128` |
| `Chapter5_Arithmetic` | 19 | Zero-free-parameter bundle; `κ·R = 1`; `ε + δ = 39/80` |
| `Chapter6_Physics` | 30 | Particle physics & cosmology; complete neutrino sector; ΛCDM |
| `Chapter7_Biology` | 8 | Beyond the scope of this paper (companion materials) |
| `Chapter8_Consciousness` | 25 | Beyond the scope of this paper (companion materials) |
| `Chapter9_Observer` | 5 | Beyond the scope of this paper (companion materials) |
| `Chapter10_Mind` | 6 | Beyond the scope of this paper (companion materials) |
| `Chapter11_Unity` | 18 | Unification; unity law `R − 2δ = 1`; cross-sector coupling |
| `Chapter12_ClayPrizes` | 23 | Lattice instantiations; Yang–Mills mass gap `m_gap = log(8/5)` on `L` |
| `Chapter13_UniversalLaws` | 17 | Conservation laws, time-reversal symmetry, Poincaré recurrence |
| `Chapter14_Audit` | 21 | Proof hygiene; 545 headline theorems; axiom-budget enforcement |

The four chapters previously held back from this paper (Biology, Consciousness, Observer, Mind) extend
the formalism beyond the experimental falsification scope of the neutrino prediction. They
are not premises of any neutrino prediction.

A reviewer at Tier 1 sees the 10 files of the neutrino chain and can verify the
headline experimental claim end-to-end. Tier 2 unlocks every other file and
every other theorem in the table above for non-commercial academic use.

---

## Citation

```bibtex
@software{williams2026persistence,
  author    = {Williams, Camron},
  title     = {{Persistence; The Theorem of Everything}:
               Neutrino Absolute Mass Derivation (Tier 1 Reviewer Package)},
  year      = {2026},
  publisher = {Williams \& Williams PTY (LTD)},
  doi       = {10.5281/zenodo.20027419},
  note      = {Lean 4, 0 sorry, 0 custom axioms.
               Bitcoin notarisation blocks 947159--947160.
               Preprint: Zenodo v1.0 (May 2026).},
  url       = {https://doi.org/10.5281/zenodo.20027419}
}
```

<!-- Copyright (c) 2024-2026 Williams & Williams PTY (LTD). All rights reserved. -->
