## TL;DR (one‑screen gist)

```bash
# 1‑line bootstrap on Ubuntu 20.04
curl -sSf https://mise.run | sh            # installs mise :contentReference[oaicite:0]{index=0}
curl -LsSf https://astral.sh/uv/install.sh | sh   # installs uv :contentReference[oaicite:1]{index=1}

# reload shell (or run the eval line printed by mise)

# project‑level setup
echo "python 3.12" > .tool-versions         # pick a version your team supports
mise install                                # downloads CPython 3.12.x
uv pip install --system -r requirements.txt # fast, deterministic install
```

---

## 1. Install **mise** (tool‑version manager)

| Step                     | Command                                          | Notes                                             |
| ------------------------ | ------------------------------------------------ | ------------------------------------------------- |
| Download & run installer | `curl -sSf [https://mise.run](https://mise.run/) | sh`                                               |
| Reload shell             | `exec $SHELL` or open a new terminal             | Shims now precede system tools on `$PATH`         |
| Verify                   | `mise --version`                                 | Should print a semantic version (e.g. `2025.6.1`) |

**Shell activation (manual)**  
If the installer didn’t patch your RC file, add:

```bash
# ~/.bashrc or ~/.zshrc
eval "$(~/.local/bin/mise activate bash)"   # zsh → ...activate zsh
```

---

## 2. Install **uv** (fast resolver / installer)

|Option|One‑liner|
|---|---|
|Stand‑alone script (recommended)|`curl -LsSf [https://astral.sh/uv/install.sh](https://astral.sh/uv/install.sh)|
|Via `pipx`|`pipx install uv`|
|Via `cargo`|`cargo install uv`|

> **Tip:** In CI, keep your home clean:  
> `UV_UNMANAGED_INSTALL="/usr/local/bin" bash -c "$(curl -LsSf https://astral.sh/uv/install.sh)"` ([Astral Docs](https://docs.astral.sh/uv/reference/installer/?utm_source=chatgpt.com "The uv installer - Astral Docs"))

---

## 3. Convert the project

### 3.1 Add a tool‑versions file

```bash
echo "python 3.12" > .tool-versions   # commit this
```

- For teammates without mise the file is harmless.
    
- Anyone with mise automatically gets Python 3.12.x shims inside the project.
    

### 3.2 Install the runtime

```bash
mise install         # downloads/compiles only once per version
mise exec python -V  # shows 3.12.x
```

### 3.3 Replace `pip` with `uv pip`

```bash
# fast, lock‑compatible install into the ACTIVE interpreter
uv pip install --system -r requirements.txt     # avoids venv
# OR reproducible install:
uv pip sync requirements.txt                    # respects hashes
```

_`--system` tells uv/pip to use the interpreter on `$PATH` (here, mise’s shim),  
so you **don’t disturb** users who still do `sudo pip install …` on the distro Python._

### 3.4 Optional lockfile

```bash
uv pip compile -r requirements.txt -o requirements.lock
git add requirements.lock
```

Now colleagues can choose:

- **Fast path** (mise + uv): `mise install && uv pip sync requirements.lock`
    
- **Classic path**: `python3 -m pip install -r requirements.txt`
    

---

## 4. Helpful commands cheat‑sheet

|Task|Command|
|---|---|
|List all runtimes|`mise list`|
|Upgrade Python 3.12 to latest patch|`mise install python@3.12 --latest`|
|Global default Python|`mise use -g python@3.12`|
|Create quick venv (if desired)|`uv venv .venv`|
|Add a new dep & lock|`uv pip install -r requirements.txt pandas && uv pip compile -o requirements.lock`|
|Self‑update tools|`mise self-update` • `uv self update`|

---

## 5. Non‑intrusive project script (optional)

`./dev‑install.sh`

```bash
#!/usr/bin/env bash
set -e
command -v mise >/dev/null && eval "$(mise activate bash)"
if command -v uv >/dev/null; then
  uv pip install --system -r requirements.txt
else
  python3 -m pip install --upgrade pip
  python3 -m pip install -r requirements.txt
fi
```

- Detects mise/uv automatically—team‑friendly and CI‑friendly.*
    

---

### Common pitfalls

- **`sudo` installs:** discourage them; prefer `--user` or venv.
    
- **Conflicting shims:** ensure `~/.local/bin` is ahead of `/usr/bin` in `$PATH`.
    
- **M1/ARM builds on CI:** add `MZ_FORCE_BUILD=1` for mise to compile from source if no pre‑built binary exists.
    
