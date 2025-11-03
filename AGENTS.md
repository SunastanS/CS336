# Repository Guidelines

## Project Structure & Module Organization
Use `assignment1-basics/` as the working root for code changes. Python sources live under `assignment1-basics/cs336_basics/`, with utility scripts such as `pretokenization_example.py` available for quick experiments. Tests and fixtures are located in `assignment1-basics/tests/`; start by wiring your implementation through `tests/adapters.py` so the harness can discover your code. Supporting assets (handout, lockfiles, submission script) stay in the same directory; add new datasets under a local `data/` folder that is ignored from version control.

## Build, Test, and Development Commands
Initialize the managed environment with `uv run <command>`; `uv` resolves dependencies defined in `pyproject.toml`. Run the full suite via `uv run pytest`, and target a single test file with commands such as `uv run pytest tests/test_tokenizer.py -k basic`. Use `uv run python cs336_basics/pretokenization_example.py` for quick smoke checks while developing tokenization features. Generate a turn-in archive with `./assignment1-basics/make_submission.sh`.

## Coding Style & Naming Conventions
Match the project’s Ruff configuration (120 character lines, 4-space indents, import sorting). Favor explicit, lower_snake_case names for functions and modules, and UpperCamelCase for classes. Type hints are encouraged where interfaces touch adapters or tests. Before submitting, optionally run `uv run ruff check .` to catch lint findings early.

## Testing Guidelines
Pytest drives the assignment, with snapshot expectations in `tests/_snapshots/`. Keep new tests alongside existing files and mirror the fixture patterns in `tests/fixtures/`. Name tests with `test_<feature>` and prefer parametrization over loops. When adding features, update adapters so tests import the implementation. Aim to keep all upstream tests passing and add regression coverage for any bug fixes.

## Commit & Pull Request Guidelines
This repository is self-maintained, so keep commits concise and imperative (e.g., `Add BPE training loop`) to preserve a readable history. Group related changes together and reference local issue IDs if you track work items. If you use pull requests within this repo, document scope, attach validation commands (at minimum `uv run pytest`), and note any new data requirements or artifacts; there is no need to open PRs against the official course repository.
