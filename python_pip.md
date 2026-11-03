# Python pip Cheatsheet

`pip` is Python's package installer. It installs packages from PyPI (Python Package Index).

> Tip: use `python -m pip ...` to be sure you're using the pip that belongs to the right Python.

## Check Version / Upgrade pip

```bash
pip --version
python -m pip install --upgrade pip
```

## Install

```bash
pip install requests                  # latest version
pip install requests==2.31.0          # exact version
pip install "requests>=2.0,<3.0"      # version range
pip install requests numpy pandas     # multiple packages
pip install -r requirements.txt       # from a file
pip install -e .                      # editable/development install
pip install git+https://github.com/user/repo.git
```

## Upgrade

```bash
pip install --upgrade requests
pip install -U requests               # short form
```

## Uninstall

```bash
pip uninstall requests
pip uninstall -r requirements.txt -y  # no confirmation
```

## List & Inspect

```bash
pip list                  # installed packages
pip list --outdated       # packages with updates
pip show requests         # details about a package
pip freeze                # installed packages in requirements format
pip check                 # check for broken dependencies
```

## Requirements File

```bash
pip freeze > requirements.txt          # save
pip install -r requirements.txt        # restore
```

Example `requirements.txt`:

```
requests==2.31.0
numpy>=1.24
pandas~=2.1.0
```

| Specifier | Meaning |
|-----------|---------|
| `==1.2.3` | Exactly this version |
| `>=1.2` | This version or newer |
| `<2.0` | Older than 2.0 |
| `~=1.2.3` | Compatible release (`>=1.2.3, <1.3`) |

## Search & Download

```bash
pip download requests                  # download without installing
pip install --no-cache-dir requests    # skip cache
pip cache purge                        # clear cache
```

> `pip search` is disabled on PyPI; search at https://pypi.org instead.

## Useful Flags

| Flag | Purpose |
|------|---------|
| `--user` | Install for current user only |
| `-q` / `-v` | Quiet / verbose output |
| `--no-deps` | Don't install dependencies |
| `--pre` | Include pre-release versions |
| `-i URL` | Use a custom package index |
| `--break-system-packages` | Override system-managed Python protection |

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `pip: command not found` | Use `python -m pip` |
| Permission denied | Use a virtual environment or `--user` |
| `externally-managed-environment` | Use a `venv` (recommended) |
| Version conflicts | Use a fresh venv; check `pip check` |
| SSL / network errors | Check proxy; upgrade pip |

## Best Practices
- Always install inside a **virtual environment**.
- Pin versions in `requirements.txt` for reproducible builds.
- Regularly review `pip list --outdated`.
- Don't use `sudo pip install`.
