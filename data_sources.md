# Data Sources — Alcohol Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Alcohol: Prohibition Paradox) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_mortality_morbidity`

3M deaths/yr, VSL-adjusted plus morbidity burden

*Full citations: paper §4 (available SSRN).*

### `C2_organ_damage_cancer`

Liver disease, cancer treatment, chronic conditions

*Full citations: paper §4 (available SSRN).*

### `C3_violence_traffic`

DUI fatalities, domestic violence, assault

*Full citations: paper §4 (available SSRN).*

### `C4_addiction_family`

AUD treatment, family destruction, child welfare

*Full citations: paper §4 (available SSRN).*

### `C5_productivity`

Absenteeism, presenteeism, lost human capital

*Full citations: paper §4 (available SSRN).*

### `C6_governance`

Industry lobbying, regulatory capture, marketing to youth

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $85.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Alcohol (Prohibition Paradox)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
