# Repository Guidelines

## Project Structure & Module Organization
Course content is notebook-first:
- `notebooks/`: lab exercises (primary teaching artifacts).
- `src/`: helper Python package used by notebooks (for reusable plotting/data code).
- `data/`: course datasets and downloaded inputs (for example `data/PXD006832/...`).
- `docs/`: MkDocs source (`docs/index.md` is the lab links page).
- `site/`: generated static site output.
- `envs/`: local Conda environment path created by project commands.

Keep notebook-specific helpers in `src/` when reuse improves readability; keep large binaries out of Git when possible.

## Build, Test, and Development Commands
Use `make` targets as the default interface:
- `make env`: create/update the Conda env from `environment.yml`.
- `make jupyter`: activate env and launch Jupyter Lab in `notebooks/`.
- `make data`: download required training data via `ppx`.
- `make serve`: run MkDocs locally for docs preview.
- `make help`: list available targets.

Recommended quality checks before opening a PR:
- `pre-commit run --all-files`
- `uv run ruff check .`
- `uv run ruff format .`

## Coding Style & Naming Conventions
Python style is enforced with Ruff (`pyproject.toml`):
- Max line length: 79.
- Target: Python 3.10+.
- Use snake_case for functions/variables and descriptive notebook filenames (for example `2.1_logistic-regression-svms.ipynb`).
- Prefer small, importable helpers in `src/` instead of repeating notebook cells.

## Testing Guidelines
There is no dedicated `tests/` suite yet. Validate changes with:
- Lint/format checks (`ruff`, `pre-commit`).
- Notebook execution checks for edited notebooks (run cells top-to-bottom in a clean kernel).
- Quick import smoke test for `src/` modules used by notebooks.

If you add non-trivial Python logic, include a minimal automated test module and document how to run it.

## Commit & Pull Request Guidelines
Recent history favors short, imperative commit messages (for example `fix link`, `update notebook`, `add session 2 and 3 notebooks`). Keep commits scoped and descriptive.

For pull requests:
- Summarize teaching impact and files changed.
- Link related issue/discussion when applicable.
- Include screenshots for docs/site visual changes.
- Confirm local checks passed and note any required data/environment steps for reviewers.
