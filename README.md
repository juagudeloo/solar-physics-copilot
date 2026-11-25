# solar-physics-copilot

Data pipeline, vision-language model and audit agent for solar physics, built on the Surya
foundation model. The data pipeline is a central part of the project, not just infrastructure:
better data comes first, and a small VLM prototype is tested early on whatever verified data exists.

| Folder | Purpose | Status |
|---|---|---|
| `pipeline/` | Finds papers, extracts solar figures, reads observation metadata, re-queries SDO | Placeholder; reviewed stage by stage before any code lands |
| `vlm/` | Frozen Surya encoder + trainable projector + frozen LLM | Empty until the first small verified batch exists |
| `agent/` | Audits the pipeline's output through its CLI and a versioned schema | Placeholder; no imports from other folders |
| `contracts/` | Versioned JSON schemas shared by all folders (sample, provenance, validation report) | Placeholder |
| `docs/` | Context, decisions, CI notes | Active |

Each code folder has its own `tests/`. Tests are designed together with the owner before the code
they check (see `docs/decisions.md`).

Everything at runtime uses open-source models only. See `docs/CONTEXT.md` for the full context and
`docs/CI.md` for what the CI checks.
