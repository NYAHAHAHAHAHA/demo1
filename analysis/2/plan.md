# Plan: CLEAR: an auditable foundation model for radiology grounded in clinical concepts

- Issue: https://github.com/NYAHAHAHAHAHA/demo1/issues/2
- Paper path: `recommended/2026-08-20/clear-auditable-foundation-model-radiology/paper.json`
- DOI: https://doi.org/10.1038/s41551-026-01741-4
- Physician focus: none specified beyond "please analyze thoroughly" (잘 분석해주세요). No named subgroup, so the plan defaults to the paper's own recommended axes — cross-institution generalization and multi-label pathology co-occurrence — as documented in the paper's `axes`/`check` fields.

## Proposed presentation

- **Institution × finding-status bar chart** (stacked bar, x = institution INST01–05, y = record count, stacked by No Finding vs. any abnormal finding). This directly operationalizes the paper's "cross-institution generalization" axis and the `check` field's suggestion to see whether abnormal-rate differs by institution — a bar/stacked-bar suits categorical-institution vs. count comparison better than a line or scatter.
- **Pathology co-occurrence table/chart** (horizontal bar or pie of single vs. multi-label vs. No Finding proportions, plus a top-N bar of individual label frequency including compound labels like `Effusion|Infiltration`). This targets the paper's "multi-pathology labels and co-occurrence" axis; a pie is appropriate only for the 3-way single/multi/no-finding split, while a ranked bar is needed for the long-tailed label frequency (a pie would be unreadable with 19+ categories).
- **Demographics summary panel** (small text/table: sex count, mean age by sex, age range, view position split) — supporting context, not a primary chart, since the paper's external validation cohorts are not broken down by these variables in the abstract; this section exists mainly to support the "Differences" comparison in the report, not as a headline visual.
- **Text sections, in order**: (1) one-paragraph paper summary with link, (2) the two proposed charts with captions explaining what institutional/label pattern to look for, (3) explicit caveat block reproducing the paper.json `caveat` field (cohort size vs. CLEAR's 230k+ external validation), (4) a "what a deep dive would need" list (e.g., per-institution AUROC if a model were run, concept-level audit trail — none of which exists yet).
- **Layout order**: Abstract/summary → institution generalization chart → pathology co-occurrence chart → demographics panel → caveats. This mirrors the paper's own emphasis (generalization first, concept-level pathology detail second) and defers demographics since they are not a focus axis of the paper.

## Open questions

- The physician gave no specific sub-question or subgroup — should the deep dive prioritize the institution-generalization angle, the multi-label co-occurrence angle, or both equally?
- Is there any real (non-synthetic) validation subset planned, since the entire 272-record cohort is `is_synthetic = true` and CLEAR's claims rest on external real-world validation?
- Should "abnormal" be defined simply as "not No Finding" for this dashboard, or should specific pathology groupings (e.g., only Infiltration/Atelectasis/Nodule per the README's top findings) be tracked separately per institution?
- Is per-institution sample size (48–62 records) considered sufficient by the physician to draw even preliminary generalization conclusions, or should this be flagged as underpowered from the start?
