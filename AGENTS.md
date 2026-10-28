# Repository Guidelines

## Project Structure & Module Organization

- `radar/` contains the CLI (`__main__.py`), signal collectors, keyword analysis, reports, SQLite storage, and MCP server. Installed packages expose it as `new_term_radar`.
- `tests/test_radar.py` holds pytest checks; `tests/conftest.py` isolates network calls, and `tests/fixtures/` stores sample responses.
- `docs/` contains diagrams and branding; `skills/` contains agent workflows. `.github/workflows/` defines testing, scheduled runs, and publishing.
- Keep `config.example.json` and `radar/config.example.json` identical. `config.json` is tracked local configuration; preserve its customizations.

## Build, Test, and Development Commands

Use Python 3.10+. The core uses the standard library.

- `python3 -m venv .venv` followed by `source .venv/bin/activate`: create an isolated environment.
- `python -m pip install -r requirements.txt pytest mcp build`: install development, optional MCP, and packaging dependencies.
- `python -m radar --help`: inspect CLI commands without collecting data.
- `python -m pytest -q tests`: run the offline suite.
- `python -m build`: create wheel and source distributions in `dist/`.
- `python -m radar daily --out report.md`: collect signals and write Markdown/JSON reports; requires explicit authorization because it contacts external services and may incur charges.

## Coding Style & Naming Conventions

Use four-space indentation, `snake_case` functions/modules, `UPPER_SNAKE_CASE` constants, and type annotations consistent with adjacent code. Prefer existing helpers and the standard library. Keep changes focused; avoid speculative abstractions, redundant validation, and unrelated cleanup. No formatter or linter is configured.

## Testing Guidelines

Pytest checks extraction, scoring, storage, reporting, and mocked integrations. Existing functions use descriptive `test_<behavior>` names, `tmp_path`, and `monkeypatch`. Keep checks offline. CI runs Python 3.10 and 3.12; no coverage threshold is configured. Run relevant existing checks; do not add unit tests under the workspace rules. Documentation-only changes need content and whitespace checks.

## Commit & Pull Request Guidelines

History uses short, descriptive subjects, often scoped (`docs:`, `new sites:`); the latest local commit uses Chinese. Write new commit messages in Chinese, for example `docs: 补充贡献指南`. Keep commits scoped. PRs should explain the change, link relevant issues, and list checks and verification limits. Include before/after output when reports change. Update both READMEs when documented behavior changes.

## Security & Agent Instructions

Keep credentials in environment variables; never commit keys, OAuth files, state, or generated reports. Preserve uncommitted changes. Without explicit authorization, do not start services, access real databases or external systems, send messages, publish, or perform destructive operations. Report only verified outcomes. Reply in Simplified Chinese, address the user as “曦”, and avoid emoji.
