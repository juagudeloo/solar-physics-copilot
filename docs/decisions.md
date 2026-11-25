# Decision log

One entry per decision, with its reason. When a rule stops being true, edit it instead of adding a
contradicting one. The starting set is in `CONTEXT.md` section 3.

## 2026-11-18

- **Early small VLM prototype.** Build it in `vlm/` as soon as a few verified samples exist and
  keep iterating while more data is verified. *Why:* fast feedback on whether the data helps the
  model, instead of verifying thousands of samples blind.
- **Skeleton scope.** Folders, per-folder CI, minimal shared `pyproject.toml` (ruff + pytest) and
  `contracts/` placeholders. No `src/` package layout until the prototype is validated. *Why:* the
  project is still exploratory; packaging waits for validation.
- **`vlm/` starts empty.** *Why:* priority is better data; the prototype is ported when the first
  small batch exists.

## 2026-11-22

- **Tests are designed together, before the code.** For every new function or class we agree the
  test cases first, then implement. Every code folder has a `tests/` directory from day one. Also
  added to the `/ml-development` skill (rule 11, `references/testing.md`). *Why:* so what we build
  does what the owner wants, and the owner states the intended behaviour explicitly.
