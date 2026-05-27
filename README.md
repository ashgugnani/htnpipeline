# Hypertension Pipeline Dashboard

A static HTML dashboard summarising hypertension pipeline performance across PCN practices, built from monthly Pipeline_Export extracts.

## What it shows

Four headline metrics, totalled across all practices in the network, with click-through to per-practice breakdowns:

- **No BP in 5Y** — patients aged 18+ without a BP reading in the last 5 years
- **Raised BP · no ABPM** — raised BP in last 3 months without ABPM follow-up
- **Raised ABPM · diagnosis > 1M** — raised ABPM not progressed to diagnosis within one month
- **Latest BP controlled** — patients diagnosed in last 12 months with latest BP controlled

Each tile is clickable. The drill-down sorts practices worst-first relative to the network average, with reference lines showing where each practice sits against the mean.

## Running it

It's a single self-contained HTML file with no dependencies. To view:

- **Locally**: double-click `index.html` — opens in your default browser
- **Hosted**: served via GitHub Pages at the URL configured in repo Settings → Pages
- **Embedded**: iframe the Pages URL into a SharePoint Embed web part

No server, no build step, no package install.

## Data scope

- 8 GP practices 
- Run date shown in the dashboard header
- No patient-identifiable data — all figures are aggregate counts

## Updating the data

When a fresh `Pipeline_Export.xls` arrives:

1. Open `index.html` in any text editor (Notepad, VS Code, whatever)
2. Find the `const DATA = { … }` block near the bottom of the file
3. Update the `num` and `denom` arrays for each metric (one number per practice, in the same order as the `practices` array)
4. Update the `run_date` field
5. Save and commit

The arrays are ordered alphabetically by practice name. Keep the order consistent across all metrics or the per-practice values will misalign.

## Information governance



## Structure

```
.
├── index.html        # the dashboard (self-contained: HTML + CSS + JS + data)
└── README.md         # this file
```

## Roadmap / nice-to-haves

- Monthly conversion script: take a raw `Pipeline_Export.xls` and produce an updated `DATA` block automatically
- Historical trend lines per metric
- Frailty / CKD / Diabetes sub-pathway views
- Export to PDF for inclusion in PCN board papers

## Source

Pipeline extract: practice-level hypertension pipeline export, run 11 May 2026.
Built with assistance from Claude.
