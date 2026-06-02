# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies
pip install pytest python-dotenv

# Run all tests
pytest tests/

# Run a single test
pytest tests/test_main.py::test_main_runs

# Run the app
python -m src.main
```

## Architecture

This is an early-stage AI automation project built in Python. The intended pattern is:

- `src/` — application logic; entry point is `src/main.py`. Uses `python-dotenv` to load environment variables (API keys go in `.env`).
- `prompts/` — reusable prompt templates written in Markdown. Templates use `{placeholder}` syntax for variable substitution before being sent to an LLM API.
- `tests/` — pytest tests that import directly from `src/`.
- `.github/workflows/ci.yml` — runs `pytest tests/` on Python 3.11 for every push/PR to `main`.

Environment variables are loaded via `load_dotenv()` in `src/main.py`. Add secrets to a local `.env` file (already gitignored).
