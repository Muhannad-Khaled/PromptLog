# PromptLog

**Git-like version control for AI prompts.**

Prompts drift. You tweak a system prompt, the output gets better, and three edits later nobody can say which change did it — or how to get back. PromptLog is meant to give prompts the same treatment code gets: versions, diffs, and a record of what each revision actually scored.

> **Status: early scaffold.** The package layout, CLI entry point, and dependencies are set up; the commands are not implemented yet. Nothing below is usable today — it describes where this is heading.

## Planned design

| Area | Intent |
|---|---|
| Versioning | Commit a prompt revision with a message, list history, check out an earlier version |
| Diffing | Show what changed between two revisions of the same prompt |
| Evaluation | Attach scores or test results to a revision so revisions can be compared on evidence, not memory |
| Storage | Local SQLite via SQLAlchemy — no server, no account |
| Interface | A `promptlog` command-line tool |

## Stack

Python 3.10+ · [Click](https://click.palletsprojects.com) for the CLI · [Rich](https://rich.readthedocs.io) for terminal output · [Pydantic](https://docs.pydantic.dev) for models · [SQLAlchemy](https://www.sqlalchemy.org) for storage · [httpx](https://www.python-httpx.org) for provider calls

## Development setup

```bash
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # macOS / Linux

pip install -e ".[dev]"
```

That installs the package in editable mode and registers the `promptlog` command, so the entry point can be exercised as the commands land.

```bash
pytest           # tests
ruff check .     # lint
```

## Layout

```
promptlog/
├── src/promptlog/
│   ├── __init__.py
│   └── cli.py          # Click entry point — promptlog.cli:cli
└── pyproject.toml
```

## License

MIT
