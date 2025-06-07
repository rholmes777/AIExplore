## Virtual Environments with Direnv + Mise — Cheat Sheet

### 1 — Activate a repo-local **`.venv`**
```bash
# .envrc
export VIRTUAL_ENV="$PWD/.venv"
export PATH="$VIRTUAL_ENV/bin:$PATH"
# optional helpers
# PATH_add "scripts"
```

---

### 2 — Activate a **pyenv-virtualenv**
```bash
# .envrc
pyenv activate myenv          # or: pyenv shell myenv
PATH_add "$VIRTUAL_ENV/bin"   # direnv stdlib helper (pyenv sets VIRTUAL_ENV)
```

---

### 3 — Use **Mise-managed Python**
```bash
# ~/.bashrc  (after: eval "$(direnv hook bash)")
eval "$(mise activate bash)"

# .envrc
use_mise                      # ask Mise for shims
# fallback if Mise missing:
# source_up .venv/bin/activate || true
```

---

### 4 — Example **`.mise.toml`**
```toml
[tools]           # language runtimes
python  = "3.12.2"
ruby    = "3.2.2"
node    = "20.14.0"
go      = "1.22.2"
rust    = "1.78.0"
erlang  = "26.2.4"
clojure = "1.11.3"
lisp    = "sbcl-2.4.3"   # Common Lisp via SBCL

[env]              # (optional) dir-scoped env-vars
BUNDLE_PATH = "vendor/bundle"
```

---

### 5 — Handy **Mise** commands
```bash
mise install                    # install everything in .mise.toml
mise use node 21.1.0 --save     # change & save version
mise list                       # list installed versions
mise doctor                     # health check
```
