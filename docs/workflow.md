# Current workflow contract

No venue sweep or paper ingestion is performed during initialization.

When a future sweep is authorized, process each configured venue and year through this contract:

`configured in-scope venue → authoritative venue/year interface → enumerate the venue/year surface → normalize scholarly identity → deduplicate → create or update catalog records → record coverage state → optionally deep-read papers later`

Prefer the official conference or journal interface or proceedings. If that is unavailable, use the source hierarchy below in order: official publisher proceedings; an authoritative community archive; DOI/Crossref/DBLP metadata; arXiv or an author page; Semantic Scholar/OpenAlex; and general web search. Secondary services support discovery and metadata completion; they do not silently replace the primary paper as evidence for scientific claims.

For substantive deep-read claims, use the paper full text or official proceedings first, then an official supplement, the official code or repository when code behavior is the subject, other primary author material, and secondary metadata sources only when appropriate.

Future venue/year coverage must distinguish processing state from reading depth. A coverage record identifies a `venue_id` and `year`, uses one of `not_started`, `partial`, `enumerated`, or `catalogued` for `state`, and separately records `deep_read_count`. Deep-read count is only processing depth; it does not mean that a paper is important.

The filesystem and Git history are sufficient for this initialized repository. Search catalogs, crawlers, indexes, and dashboards are outside the current workflow contract.
