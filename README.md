# Cyber risk analytics — vulnerability scoring & remediation

Portfolio project: quantitative **risk scoring** over assets and vulnerabilities (CVSS-based), statistical critique of a legacy capped score, a **smooth bounded alternative** to reduce saturation, **remediation simulation** (IT vs. medical device rules), and an **LLM-assisted enrichment** workflow for CPS device types and OS metadata (batched JSON prompts, validation, consolidation).

## What’s inside

| Path | Description |
|------|-------------|
| `data/` | Synthetic-style CSVs: assets, vulnerabilities, mappings, devices, CPS model list |
| `notebooks/risk_analyst_analysis.ipynb` | Full analysis: EDA, scoring, distributions, normality tests, new formula, top-risk devices, before/after remediation, LLM sections |
| `outputs/` | Placeholder for exported CSVs / plots when you re-run the notebook |

## Run locally

```bash
cd claroty-cyber-risk-analytics
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/risk_analyst_analysis.ipynb
```

**Important:** Start Jupyter from the **repository root** (`claroty-cyber-risk-analytics`) so `os.getcwd()/data` resolves correctly. Alternatively, open the notebook and `cd` to the repo root in the first cell.

## Methods (short)

- **Legacy risk:** sum of CVSS base scores per asset, hard cap at 100 (induces saturation / ties at the top).
- **Proposed score:** smooth mapping of total CVSS into `[0, 100]` with calibration on high percentiles to preserve separation in the tail.
- **Remediation:** rule-based removal of vulnerabilities by category (e.g. IT vs. medical), then residual risk and distribution shift.
- **LLM task:** cleaned device model strings → batched prompts → strict JSON outputs → merged tables (with manual/API paste workflow as in the original assignment).

## Note

This repository is for **demonstration and job search** only. If any material is subject to an NDA, remove or replace files before publishing.
