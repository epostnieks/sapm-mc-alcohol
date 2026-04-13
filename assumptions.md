# Monte Carlo Assumptions — Alcohol / Prohibition Paradox

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $85.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 24.96 | Confirmed by N=100,000 draws |
| ΔW median (result) | $2,121.4B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_mortality_morbidity` | lognormal | $800B | $1,100B | $1,500B | 3M deaths/yr, VSL-adjusted plus morbidity burden |
| `C2_organ_damage_cancer` | normal | $120B | $150B | $190B | Liver disease, cancer treatment, chronic conditions |
| `C3_violence_traffic` | lognormal | $140B | $180B | $230B | DUI fatalities, domestic violence, assault |
| `C4_addiction_family` | lognormal | $45B | $65B | $95B | AUD treatment, family destruction, child welfare |
| `C5_productivity` | normal | $400B | $595B | $800B | Absenteeism, presenteeism, lost human capital |
| `C6_governance` | lognormal | $15B | $25B | $40B | Industry lobbying, regulatory capture, marketing to youth |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.0 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.0) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 24.88 | 20% DC adj = 19.91 | 40% DC adj = 14.93

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $2,121B = 2.0% of world GDP ($106T) ✓
- **β_W range**: 24.96 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
