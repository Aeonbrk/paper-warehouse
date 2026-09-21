# AGENTS.md — Paper Warehouse

This repository maintains a neutral scholarly literature corpus for a curated set of research venues.

- Use the supplied official 2026 CCF directory PDF as the sole venue-rank authority.
- Prefer primary scholarly sources for scientific facts.
- Never invent missing bibliographic, methodological, or experimental details.
- Canonical paper records describe papers; they do not rank relevance, usefulness, novelty, importance, or quality.
- Downstream research projects must not alter canonical paper semantics.
- Keep repository rules, current documentation, scholarly evidence, and historical decision rationale in their proper homes.
- Before a non-trivial change, read the nearest applicable `AGENTS.md`, only the needed current docs, relevant `.agents/notes/`, and then the live implementation/config/data; keep this proportional to the task.
- Keep `docs/` current-only; keep `.agents/notes/` append-only and causal for non-trivial decisions, not work logs or indexes.
- Preserve evidence locators for substantive deep-read claims when practical.
- Prefer updating an existing scholarly identity over creating duplicates.
- Do not manually maintain a global paper index; derived catalogs are not canonical evidence.
- Write an Agent Note only for a non-trivial repository architecture, schema, methodology, or workflow decision.
- Do not add infrastructure without a concrete current need.
