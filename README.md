# Cyber asset & vulnerability risk analytics

End-to-end portfolio work: quantitative **risk scoring** over assets and vulnerabilities (**CVSS**), statistical analysis of a **legacy capped score**, a **smooth bounded alternative** to reduce saturation at the top of the scale, **remediation simulation** (e.g. IT vs. clinical device policies), and an **LLM-assisted enrichment** workflow for connected-device metadata (batched JSON prompts, validation, merged outputs).

This repository presents the methodology and code for **job search**; it is not affiliated with any employer’s branding.

## Interactive report (HTML)

A **read-only HTML export** of the analysis is in `docs/index.html`. View it in the browser (charts and narrative; no execution):

**[Open interactive report →](https://edenmalka123.github.io/cyber-asset-risk-analytics/)**

If the link returns 404, enable **GitHub Pages** once: **Settings → Pages → Branch `main` / folder `/docs` → Save**, then wait a minute and refresh.

## What’s inside

| Path | Description |
|------|-------------|
| `data/` | CSVs: assets, vulnerabilities, mappings, devices, CPS-style model list |
| `notebooks/risk_analyst_analysis.ipynb` | Full analysis: EDA, scoring, distributions, normality tests, proposed formula, top-risk assets, before/after remediation, LLM sections |
| `outputs/` | For CSV/plot exports when you re-run the notebook |

## Run locally

```bash
cd cyber-asset-risk-analytics
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/risk_analyst_analysis.ipynb
```

**Important:** Start Jupyter from the **repository root** (`cyber-asset-risk-analytics`) so `os.getcwd()/data` resolves correctly, or `cd` to the repo root in the first cell.

## Methods (short)

- **Legacy risk:** sum of CVSS base scores per asset with a hard cap (saturation / ties among highest-risk items).
- **Proposed score:** smooth mapping into `[0, 100]` with calibration on high percentiles to preserve separation in the tail.
- **Remediation:** rule-based vulnerability removal by asset category, then residual risk and distribution shift.
- **LLM workflow:** normalized device labels → structured prompts → JSON outputs → consolidated tables (interactive / API-style workflow as in the original exercise).

## Note

For **demonstration and recruiting** only. If any dataset or deliverable is subject to confidentiality, do not publish those files publicly.
