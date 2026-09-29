# CS-DDD-audit

Supplementary material for the paper **"CS-DDD Revisited: A Self-Audit of Forecasting and Granger-Precedence Claims on U.S. Breakeven Inflation and the Federal Funds Rate"** (S. Al-Qublawi, Al-Jafara University).

The paper is a self-audit by the developer of the CS-DDD framework. It is not an independent replication.

## Files

| File | Content |
|---|---|
| `S1_Extended_Analysis.docx` | Full-length analysis: all sections, tables and procedures omitted from the six-page IEEE paper |
| `S2_Code_and_Raw_Output.docx` | Appendix D (source code of the Section 9 scripts) and Appendix E (raw JSON/CSV output) |
| `data/T10YIE.csv`, `data/T10YIEM.csv`, `data/FEDFUNDS.csv` | FRED series used in the analysis (add these files) |
| `scripts/step1_data_baselines.py` ... `scripts/step10_hln_baiperron.py` | Analysis scripts (add these files; step7 is not reproduced in S2) |
| `requirements.txt` | Exact package versions (add this file) |

## Data

All data are public FRED series (https://fred.stlouisfed.org): T10YIE, T10YIEM and FEDFUNDS.

- Short sample: n = 60 (July 2021 to June 2026).
- Extended sample: n = 284 (January 2003 to August 2026).
- The original symbolic-search comparison used an earlier pull (n = 282).

## Environment

Python 3.12, statsmodels 0.15.0, scikit-learn 1.8.0, plus numpy, scipy and pandas (list the exact versions in `requirements.txt`).

## Reproducing the results

1. Place the three FRED CSV files in `data/`.
2. Run `scripts/step1_data_baselines.py` through `scripts/step10_hln_baiperron.py` in numerical order.
3. Note that `step10_hln_baiperron.py` loads helper functions from a file named `cw.py`. Save `step9_clark_west.py` under that name, or change the import path.
4. Random seeds are fixed in each script. Compare the JSON outputs with Appendix E in S2.

## Known limitations

See Section V of the paper. The symbolic-search engine was not re-run on the refreshed data, the Granger lag search was capped at six lags, and residual diagnostics were not computed.

