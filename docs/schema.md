# Canonical paper record schema

Canonical records use Markdown with a YAML front matter block. A record is stored as `library/papers/<paper-id>.md`. The local `paper_id` is stable within this warehouse and should be reused when an existing scholarly identity is found.

The front matter is warehouse metadata and discovery information. The Markdown body is reserved for neutral, paper-reported description. A statement about a paper should be attributed to the paper or tied to an evidence pointer when it is substantive; warehouse metadata must not be presented as a paper-reported claim.

## Level 1: catalog record

Level 1 records contain the minimum identity and discovery fields:

```yaml
---
schema_version: 1
record_level: catalog
paper_id: "stable-local-id"
title: "Paper title"
authors:
  - "Author One"
publication_year: 2025
venue_id: "configured-venue-id"
venue_name: "Venue name"
publication_type: conference
track: null
doi: null
arxiv_id: null
official_paper_url: null
publication_status: published
source_provenance:
  - source: official-proceedings
    locator: "URL or bibliographic locator"
    accessed: "2026-09-21"
---

# Paper title
```

`track`, `doi`, `arxiv_id`, `official_paper_url`, and any other unavailable value remain `null` or are omitted; they are never guessed. `publication_type` and `publication_status` are descriptive metadata, not quality judgments.

The stable front matter keys are `schema_version`, `record_level`, `paper_id`, `title`, `authors`, `publication_year`, `venue_id`, `venue_name`, `publication_type`, `publication_status`, and `source_provenance`. `track`, `doi`, `arxiv_id`, and `official_paper_url` are optional. `record_level` is `catalog` or `deep-read`; `schema_version` is `1` for this format.

## Level 2: deep-read record

Level 2 keeps all Level 1 fields and adds factual sections in the Markdown body:

- Problem
- Method
- Information / computation flow
- Training
- Data
- Evaluation
- Main results
- Ablations
- Limitations / evidence boundaries
- Reproducibility assets
- Evidence pointers

Sections may state that information is not reported. The warehouse does not infer missing details. Evidence pointers may identify a section, table, figure, or appendix, and should be specific enough to relocate the supporting passage. Author novelty claims are recorded as claims by the authors rather than as warehouse verdicts.

There are no relevance, recommendation, importance, novelty, quality, ranking, or project-fit fields in canonical records.
