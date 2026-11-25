# contracts

Versioned JSON schemas shared by `pipeline/`, `vlm/` and `agent/`. Folders talk to each other only
through these schemas and the pipeline's CLI, never through cross-folder imports.

Planned (not designed yet; each needs the owner's approval first):

- **sample**: one training sample, with a `source` field (`paper` | `noaa`), a verification status
  and, for paper samples, bibcode, DOI and licence.
- **provenance**: where each sample came from and how it was produced.
- **validation report**: the pipeline's deterministic quality report that the agent parses.

Tests for the schemas go in `tests/`: a valid example passes and each missing or malformed required
field fails with a clear error.
