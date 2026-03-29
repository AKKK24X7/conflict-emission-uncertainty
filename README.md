# Conflict Emission Uncertainty
## Probabilistic GHG Accounting for Conflict Zones

A Monte Carlo analysis of greenhouse gas and air quality emissions from armed conflict,
quantifying the uncertainty that makes single-point estimates unreliable.

**Author:** Anoopkrishna Krishnakumar  
**Contact:** anoopkrishnak1998@gmail.com  
**LinkedIn:** [linkedin.com/in/akkk98](https://linkedin.com/in/akkk98/)

---

## The Question

News coverage of armed conflict frequently mentions environmental damage — burning
infrastructure, destroyed oil facilities, landscape fires. But how large are these
emissions really, and how confident can we be in any estimate?

The answer turns out to be: significant, and not very confident at all.
The uncertainty itself is the most important finding.

---

## Repository Structure

```
conflict-emission-uncertainty/
│
├── conflict_emission_uncertainty.ipynb    ← Start here
├── figures/
│   ├── 01_conflict_distribution_uncertainty.png
│   ├── 02_conflict_contributions.png
│   ├── 03_conflict_sensitivity.png
│   └── 04_conflict_convergence.png
└── README.md
```

---

## Notebook: The Hidden Climate Cost of Conflict
**`conflict_emission_uncertainty.ipynb`**

**Case study:** Ukraine conflict emissions (2022–2024)  
**Methodology:** Monte Carlo uncertainty propagation across six source categories

### The problem

Unlike industrial emissions, conflict emissions are inherently uncertain:
- Infrastructure is destroyed, disrupting data collection
- Military activity is deliberately obscured
- Satellite detection has known limitations in active conflict zones
- Expert estimates disagree by factors of 2–13 on the same source category

This makes conflict emissions a textbook Monte Carlo problem — we know approximate
magnitudes from published peer-reviewed studies, but uncertainty is large, structured,
and source-dependent.

### Emission sources modelled

| Source | Mean (MtCO₂e/yr) | CV | Basis for uncertainty |
|--------|-----------------|-----|----------------------|
| Military fuel combustion | 27.4 | 0.40 | Fuel consumption classified; vehicle ratios estimated |
| Infrastructure fires | 3.1 | 0.60 | Satellite detection ±60% in smoke-obscured zones |
| Landscape fires | 16.2 | 0.50 | Biomass estimates vary by factor of 13 (CEOBS 2024) |
| Reconstruction embodied carbon | 20.7 | 0.35 | Damage assessment 60–80% complete |
| Aviation rerouting | 4.8 | 0.15 | Flight data publicly tracked; well modelled |
| Black carbon / particulates | 0.5 | 0.80 | Almost no conflict-zone PM measurements exist |

### Key results

| Metric | Value |
|--------|-------|
| Mean annual conflict emissions | ~73 MtCO₂e/year |
| P5–P95 range | ~51–101 MtCO₂e/year |
| P95/P5 ratio | ~2x |
| Comparable to | Annual emissions of Belgium (114 MtCO₂e) |
| Dominant contributor to mean | Military fuel combustion (~38%) |
| Most uncertain source | Black carbon/PM (P95/P5 = 10x) |
| Dominant variance driver | Military fuel (highest Pearson sensitivity index) |

### The accounting gap

Current GHG reporting frameworks under the Paris Agreement do not require or enable
transparent conflict emission accounting. The same structural problem exists for
rocket launches, aviation at altitude, and other activities that cross conventional
monitoring boundaries — real environmental impacts that fall outside existing
measurement and characterisation frameworks.

---

## Why Lognormal Distributions?

Emissions are strictly positive and their uncertainties are multiplicative.
When scientists report conflict emission uncertainty, they say "could be 2× higher
or 0.5× lower" — not "±5 MtCO₂e." A lognormal distribution captures this correctly.

Additionally, conflict estimates are right-skewed — more likely to underestimate
(missing data, classified activity, destroyed monitoring infrastructure) than
to overestimate. Lognormal distributions naturally reflect this asymmetry.

---

## Getting Started

```bash
pip install numpy scipy matplotlib pandas jupyter
jupyter notebook conflict_emission_uncertainty.ipynb
```

---

## References

Bun et al. (2024). Tracking unaccounted greenhouse gas emissions due to the war
in Ukraine. *Science of the Total Environment*.

Initiative on GHG Accounting of War (2025). Three-year assessment: climate damage
caused by Russia's war in Ukraine.

CEOBS (2024). Ukraine conflict environmental briefing: the climate crisis.
Conflict and Environment Observatory.

---

## Planned Additions

| Notebook | Description | Status |
|----------|-------------|--------|
| `conflict_emission_uncertainty.ipynb` | Monte Carlo GHG accounting — Ukraine case study | ✅ Complete |
| `historical_conflict_comparison.ipynb` | Gulf War 1991 and Iraq War 2003 — historical emission benchmarks | 🔄 Next |
| `air_quality_health_impact.ipynb` | PM2.5 concentration modelling and DALY health impact from conflict emissions | 📋 Planned |
| `reconstruction_carbon_cost.ipynb` | Embodied carbon of post-conflict reconstruction under different material scenarios | 📋 Planned |
| `conflict_emissions_generalised.ipynb` | Generalised framework applicable to any conflict zone once peer-reviewed data becomes available | 📋 Planned |
