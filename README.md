# SAPM Monte Carlo — Alcohol / Prohibition Paradox

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Alcohol (Prohibition Paradox).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **24.96** |
| β_W mean | 25.15 |
| β_W std | 3.58 |
| **90% CI** | **[19.6, 31.4]** |
| 99% CI | [17.7, 34.4] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$2,121.4B/yr** |
| Π (revenue) | $85.0B/yr |

**β_W = 24.96** means the alcohol industry destroys **$24.96 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-alcohol.git
cd sapm-mc-alcohol
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 24.96` and `ΔW median : $2,121.4B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_mortality_morbidity | $1,098.8B | [$804.9B, $1,498.3B] | Lognormal |
| C2_organ_damage_cancer | $149.9B | [$114.9B, $185.3B] | Normal |
| C3_violence_traffic | $180.0B | [$140.9B, $229.9B] | Lognormal |
| C4_addiction_family | $65.0B | [$44.4B, $94.9B] | Lognormal |
| C5_productivity | $594.2B | [$395.7B, $793.5B] | Normal |
| C6_governance | $25.0B | [$15.6B, $40.0B] | Lognormal |
| **Total ΔW** | **$2,121.4B** | **[$1,668.3B, $2,664.8B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.0 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Alcohol (Prohibition Paradox)*.
> GitHub: epostnieks/sapm-mc-alcohol.
> https://github.com/epostnieks/sapm-mc-alcohol
