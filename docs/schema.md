# Canonical paper record schema

Canonical records use Markdown with a YAML front matter block. A record is stored as `library/papers/<paper-id>.md`. The local `paper_id` is stable within this warehouse and should be reused when an existing scholarly identity is found.

The front matter is warehouse metadata and discovery information. The Markdown body is reserved for neutral, paper-reported description. A statement about a paper should be attributed to the paper or tied to an evidence pointer when it is substantive; warehouse metadata must not be presented as a paper-reported claim.

## Level 1: catalog record

Level 1 records contain bibliographic identity and discovery fields. They may
also contain a short synopsis derived from a verified abstract and optional
source-provided keywords or concepts. Semantic content declares its evidence
basis in front matter and preserves the abstract source in
`source_provenance`.

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
semantic_basis: official_abstract
source_provenance:
  - source: official-proceedings
    locator: "URL or bibliographic locator"
    accessed: "2026-09-21"
---

# Paper title
```

`track`, `doi`, `arxiv_id`, `official_paper_url`, and any other unavailable value remain `null` or are omitted; they are never guessed. `publication_type` and `publication_status` are descriptive metadata, not quality judgments.

`semantic_basis` is `official_abstract`, `authoritative_abstract_metadata`, or
`null`. When it is non-null, the body may include an `Abstract-derived
synopsis` section with a short neutral paraphrase supported only by that
abstract. The synopsis is not a full-text finding. Source-provided keywords or
concepts may be included when directly available from the same authoritative
metadata. If no reliable abstract is available, omit the synopsis and leave
`semantic_basis` null.

The stable front matter keys are `schema_version`, `record_level`, `paper_id`, `title`, `authors`, `publication_year`, `venue_id`, `venue_name`, `publication_type`, `publication_status`, `semantic_basis`, and `source_provenance`. `track`, `doi`, `arxiv_id`, and `official_paper_url` are optional. `record_level` is `catalog` or `deep-read`; `schema_version` is `1` for this format.

## Level 2: deep-read record

Level 2 keeps all catalog fields and adds factual sections derived from paper
full text in the Markdown body:

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
