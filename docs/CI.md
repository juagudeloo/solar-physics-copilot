# Continuous integration

GitHub Actions runs `.github/workflows/ci.yml` on every push and pull request. A `changes` job
detects which folders were touched and calls the reusable `folder-check.yml` once per affected
folder (`contracts`, `pipeline`, `vlm`, `agent`). A change to `contracts/`, `pyproject.toml` or the
workflows runs every dependent job.

Each folder job runs three steps, cheapest first:

| Step | Command | What it catches |
|---|---|---|
| Lint | `ruff check <folder>` (rules E, F, I, RUF, see `pyproject.toml`) | unused or unsorted imports, undefined names, style slips |
| Compile | `python -m compileall -q <folder>` | syntax errors in files no test imports |
| Tests | `pytest --doctest-modules <folder>` | logic regressions, and docstring examples going stale |

A folder may add `requirements-ci.txt` for its own dependencies; the job installs it when present.

## Temporary: empty folders pass

`pytest` exits with code 5 when it finds no tests. While folders are placeholders the job treats
that as a pass. Delete the `|| [ $? -eq 5 ]` in `folder-check.yml` when the first real test lands.

## Run the same checks locally

```bash
pip install ruff pytest pydantic
ruff check contracts pipeline vlm agent
pytest --doctest-modules contracts
```

## What does NOT run in CI

Nothing needs a GPU, network access to NASA/VSO, model weights or secrets. The Qwen models, VSO
queries and FITS downloads are never run in CI; tests build tiny in-memory inputs instead. Stage
quality (are the figures and metadata correct?) is what the agent audits, not CI.

## Origin

Adapted from the `ci/github-actions` branches of `sdo-paper-to-observation`,
`vision-language-model-surya` and `suvi-sdo-generalization` (local, never pushed). Their tests
cover code that is not in this repo yet and are ported together with that code.
