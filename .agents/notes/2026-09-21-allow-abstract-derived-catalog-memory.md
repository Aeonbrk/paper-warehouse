# Allow abstract-derived semantic memory in catalog records

## Context / Trigger

The complete KDD 2022–2026 catalog existed, but title-only bodies provided little
semantic retrieval value. Full-text reading of every paper is neither required
nor justified for catalog ingestion.

## Decision

Catalog records may contain a short neutral synopsis derived only from a
verified abstract or equivalent authoritative abstract metadata.

The evidence basis must be explicit.

Full-text-only claims remain reserved for deep-read records.

## Rejected Alternatives

- Keep catalog records bibliographic-only:
  rejected because the warehouse would remain a directory rather than useful
  searchable paper memory.

- Deep-read all papers during ingestion:
  rejected because it materially expands scope and encourages unsupported or
  low-quality mass summaries.

- Infer summaries from titles / search snippets:
  rejected because the evidence is insufficient.

## Consequences / Invariants

- abstract-derived claims cannot be presented as full-text findings;
- absent abstract information remains absent;
- semantic enrichment does not change scholarly identity;
- deep-read remains a distinct stronger evidence level;
- summaries must remain neutral and source-grounded.
