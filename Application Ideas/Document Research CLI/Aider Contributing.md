## Adding Ruby + Bundler for the docs site

### What Ruby version?
* **Latest stable:** Ruby **3.4.4** (released 2025-05-14) :contentReference[oaicite:0]{index=0}  
* Bundler ships with Ruby 3.4 by default :contentReference[oaicite:1]{index=1}.

### Where to activate Ruby?
| Scope | Pros | Cons | How |
|-------|------|------|-----|
| **`aider/website/` only** | *Isolates* gems & PATH; Python-only tasks in repo stay lighter | One extra `.envrc` / `.mise.toml` to maintain | Put Ruby lines in `aider/website/.mise.toml` + `aider/website/.envrc` |
| **Repo root (`aider/`)** | Single config; less duplication | Ruby shims always on PATH even when not building docs | Add Ruby to the existing root-level `.mise.toml` |

**Practically:** most projects keep Ruby isolated under `website/` to avoid surprise gem warnings in unrelated tooling. If no one else on your team minds, root-level is simpler.

---

### Quick setup (using Mise)

1. **Add Ruby to whichever `.mise.toml` you choose**

   ```toml
   [tools]
   ruby = "3.4.4"
```

2. **Install & expose Ruby**
    
    ```bash
    mise install        # downloads 3.4.4
    direnv allow        # reloads if inside the dir
    ```
    
3. **Install site gems**
    
    ```bash
    cd aider/website
    gem update --system            # optional, keeps RubyGems fresh
    bundle config set path vendor/bundle   # keeps gems under repo
    bundle install
    ```
    
4. **Build / serve docs**
    
    ```bash
    bundle exec jekyll build       # one-off build
    bundle exec jekyll serve       # live preview at http://127.0.0.1:4000
    ```
    

---

### Minimal `.envrc` example for `aider/website/`

```bash
use_mise                 # Ruby shims come from Mise
# optional: keep Python venv active too
source_up ../.venv/bin/activate || true
```

> _Heads-up:_ early reports show Jekyll 4.x needs the `webrick` gem on Ruby ≥ 3.4. If `jekyll serve` errors, run  
> `bundle add webrick` (it’s tiny). ([batsov.com](https://batsov.com/articles/2025/01/12/running-jekyll-on-ruby-3-4/?utm_source=chatgpt.com "Running Jekyll on Ruby 3.4 - Bozhidar Batsov"))
