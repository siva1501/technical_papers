# Python Virtual Environment (`venv`) Cheatsheet

A virtual environment is an isolated Python environment so each project has its own packages and versions.

## Why Use It
- Avoids package version conflicts between projects.
- Keeps the global Python installation clean.
- Makes projects reproducible and shareable.

## Create

```bash
python -m venv venv          # creates a folder named "venv"
python3 -m venv .venv        # common alternative (macOS/Linux)
```

## Activate

| OS / Shell | Command |
|-----------|---------|
| Windows (CMD) | `venv\Scripts\activate.bat` |
| Windows (PowerShell) | `venv\Scripts\Activate.ps1` |
| macOS / Linux (bash/zsh) | `source venv/bin/activate` |
| Fish | `source venv/bin/activate.fish` |

When active, your prompt shows `(venv)`.

> **PowerShell error?** Run once: `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`

## Deactivate

```bash
deactivate
```

## Typical Workflow

```bash
mkdir myproject && cd myproject
python -m venv venv
source venv/bin/activate         # Windows: venv\Scripts\activate
pip install requests
pip freeze > requirements.txt
deactivate
```

## Recreate from `requirements.txt`

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Useful Options

```bash
python -m venv venv --system-site-packages   # access global packages
python -m venv venv --clear                  # wipe and recreate
python -m venv venv --upgrade-deps           # upgrade pip on creation
```

## Check Which Python Is Active

```bash
which python        # macOS/Linux
where python        # Windows
python -c "import sys; print(sys.prefix)"
```

## Delete an Environment
Deactivate first, then delete the folder:

```bash
rm -rf venv              # macOS/Linux
rmdir /s /q venv         # Windows CMD
```

## Best Practices
- Add the folder to `.gitignore` (`venv/`, `.venv/`); never commit it.
- Commit `requirements.txt` instead.
- Use one environment per project.
- Don't move or rename a venv folder; recreate it instead.

## Alternatives
| Tool | Notes |
|------|-------|
| `virtualenv` | Older, more features |
| `pipenv` | venv + pip + Pipfile |
| `poetry` | Dependency management and packaging |
| `conda` | Also manages non-Python packages |
| `uv` | Very fast modern tool |
