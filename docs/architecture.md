# Current architecture

The repository keeps each responsibility in one place.

- `AGENTS.md` contains small, stable rules that every future agent must
  follow.
- `config/venues.toml` is the one canonical machine-readable venue scope and
  CCF-rank configuration.
- `docs/` describes the current structure, record schema, source hierarchy, and
  workflow contract.
- `library/papers/` is reserved for canonical neutral paper records.
- `coverage/` contains factual venue/year processing-state and reconciliation
  records.
- `docs/cookbook/` contains current operational procedures that apply across
  catalog sweeps.
- `.agents/notes/` holds append-only rationale for non-trivial repository-level
  decisions; routine work does not create notes.

The supplied official 2026 CCF directory PDF remains at the repository root as
the initialization authority for the configured ranks. It is source material,
not a paper record or a second venue configuration.
