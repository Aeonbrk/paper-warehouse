# Paper acquisition cookbook

## Enumerate a venue

Start with the official conference proceedings for the exact year. Record
every proceedings part or volume that belongs to the conference. Use the
official conference program only to recover track labels or to distinguish
paper entries from non-paper program material. Do not use DBLP, OpenAlex,
arXiv, or search results as the complete corpus.

## Verify identity

Use the ACM DOI and publisher metadata as the primary identity. Query Crossref
for missing title or author fields with the DOI, for example:

```sh
curl -fsSL 'https://api.crossref.org/works/10.1145/DOI-SUFFIX'
```

Use a strong title, author, venue, or DOI query for a targeted fallback. The
OpenAlex and arXiv OpenCLI adapters were verified on this machine:

```sh
opencli openalex search 'paper title' --format json
opencli arxiv search 'paper title' --format json
```

For bounded abstract enrichment, query Semantic Scholar by DOI in batches and
use its abstract only when the returned title and DOI match the catalog record.
The batch endpoint is:

```text
https://api.semanticscholar.org/graph/v1/paper/batch?fields=title,abstract,externalIds
```

If that record has no abstract, query arXiv by the exact title and verify the
title before using its abstract. OpenAlex abstract metadata is another
fallback when its DOI record matches. Record the selected abstract source and
locator in `source_provenance`.

DBLP and OpenAlex records can confirm a bibliographic match. Semantic Scholar
and arXiv can supply abstract metadata for an existing DOI identity. An arXiv
record can document a preprint relationship. Neither source creates a second
KDD catalog record.

## Acquire full text lawfully

Use an openly accessible ACM HTML or PDF first. If it is not open, check arXiv,
an author or institutional repository, or another legitimate public
repository. User-authorized institutional subscription access is allowed. A
subscription route is not open access.

Do not bypass a paywall, login, CAPTCHA, cookie or token check. Do not guess
credentials or redistribute subscription-only material. Do not download a
full venue corpus for a catalog sweep.

## Evidence boundary

Metadata, abstracts, search snippets, and repository landing pages establish
identity or discovery. They do not substitute for paper full text when a future
task makes a scientific claim.

## Failure handling

If a broad search fails, switch to the DOI, an exact title-author query, or the
official publisher page. Stop retrying a broad interface that does not return
a usable record. Leave unavailable fields unknown.
