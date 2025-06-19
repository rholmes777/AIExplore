# **uv: The Game-Changer for Python Project Management** ⚡

You're absolutely right to be interested - **uv is revolutionary**. It's what pip/poetry _should_ have been all along.

## What uv Actually Is

**uv = pip + venv + poetry + conda... but 10-100x faster**

Written in Rust by the Ruff team, it handles:

- Package installation (replaces `pip`)
- Virtual environments (replaces `python -m venv`)
- Dependency resolution (replaces `poetry`)
- Python version management (complements `mise`)

## Speed Comparison (Real Numbers)

```bash
# Installing pandas + numpy + matplotlib
pip install pandas numpy matplotlib     # ~45 seconds
uv add pandas numpy matplotlib          # ~3 seconds
```

## Basic uv Workflow

### **Creating New Projects**

```bash
# The modern way
uv init my-ml-project
cd my-ml-project

# Creates:
# ├── .python-version     # Python version (works with mise!)
# ├── pyproject.toml      # Dependencies & config
# ├── README.md
# └── src/my_ml_project/
```

### **Adding Dependencies**

```bash
# Add packages (like poetry add)
uv add pandas numpy matplotlib seaborn
uv add --dev jupyter pytest black

# Add from requirements.txt
uv add -r requirements.txt

# Add specific versions
uv add "tensorflow>=2.13,<2.16" "python<3.12"
```

### **Daily Workflow**

```bash
# Install everything (like poetry install)
uv sync

# Run in the environment  
uv run jupyter lab
uv run python train_model.py
uv run pytest

# Quick shell access
uv shell  # activate venv (optional)
```

## Integration with mise

**This is where it gets powerful:**

```toml
# .mise.toml
[tools]
python = "3.11"    # mise manages Python versions
uv = "latest"      # mise manages uv itself

# pyproject.toml  
[project]
requires-python = ">=3.11,<3.12"  # uv respects this
dependencies = [
    "tensorflow>=2.13",
    "pandas>=2.0",
    "jupyter"
]
```

**Workflow:**

```bash
cd ml-project
mise install          # Sets up Python 3.11 + uv
uv sync               # Creates venv with right Python, installs deps
uv run jupyter lab    # Ready to go!
```

## Migration from pyenv virtualenv

### **Old Way (pyenv virtualenv)**

```bash
pyenv virtualenv 3.11.7 ml-project
pyenv activate ml-project  
pip install -r requirements.txt
python train.py
```

### **New Way (mise + uv)**

```bash
# One-time setup
echo "python = '3.11'" > .mise.toml
uv init --python 3.11
uv add pandas tensorflow jupyter

# Daily use
cd project && uv run python train.py  # That's it!
```

## Data Science Best Practices

### **Project Template**

```bash
uv init ml-research
cd ml-research

# Set up the typical DS stack
uv add pandas numpy matplotlib seaborn scikit-learn
uv add jupyter ipykernel nbconvert
uv add --dev pytest black ruff

# For TensorFlow projects
uv add "tensorflow>=2.13" "python<3.12"

# For PyTorch  
uv add torch torchvision --index-url https://download.pytorch.org/whl/cu118
```

### **Managing Jupyter Kernels**

```bash
# Old way: manual kernel registration
# New way: uv handles it
uv add ipykernel
uv run python -m ipykernel install --user --name ml-research
```

### **Reproducible Environments**

```toml
# pyproject.toml - commit this
[project]
dependencies = [
    "pandas>=2.0,<3.0",
    "tensorflow>=2.13,<2.16"
]

# uv.lock - also commit this (like poetry.lock)
# Contains exact versions for reproducibility
```

## Advanced Patterns

### **Multiple Environments per Project**

```bash
# Different environments for different tasks
uv venv training --python 3.11
uv venv inference --python 3.12

# Use specific env
uv run --env training python train.py
uv run --env inference python deploy.py
```

### **GPU/CPU Variants**

```toml
# pyproject.toml
[project.optional-dependencies]
gpu = ["tensorflow[gpu]>=2.13"]
cpu = ["tensorflow-cpu>=2.13"]

# Install variants
uv sync --extra gpu    # or
uv sync --extra cpu
```

## Migration Checklist

### **From pyenv virtualenv:**

1. **Document current environments:**
    
    ```bash
    pyenv versions > old_envs.txt
    pip list > current_packages.txt
    ```
    
2. **Create new uv project:**
    
    ```bash
    uv init project-name
    uv add $(cat current_packages.txt | grep -v "^Package" | awk '{print $1}')
    ```
    
3. **Update scripts:**
    
    ```bash
    # Old: pyenv activate env && python script.py
    # New: uv run python script.py
    ```
    
4. **Clean up:**
    
    ```bash
    pyenv uninstall old-env-name
    ```
    

## Performance Benefits for Data Science

**Real impact:**

- **Environment creation**: 30s → 3s
- **Package installation**: 5min → 30s
- **Dependency resolution**: Often impossible → Always works
- **Docker builds**: 10min → 2min (with uv in containers)

## The "Aha!" Moment

**Before (pyenv + pip):**

```bash
pyenv virtualenv 3.11 ml-proj
pyenv activate ml-proj
pip install tensorflow  # ☕ Coffee break...
pip install pandas     # Still installing...
python train.py         # Finally!
```

**After (mise + uv):**

```bash
cd ml-proj && uv run python train.py  # ⚡ Done!
```

**Bottom line:** uv eliminates the "Python environment friction" that has plagued data scientists for years. Combined with mise, you get a professional, fast, reproducible workflow that actually _helps_ rather than hinders your work.

Ready to try it on a project? 🚀

---
**Great practical questions! Let me break these down:**

## 1. `uv run` vs Forgetting the Prefix

### **What Actually Happens:**

```bash
# In a uv project directory:
uv run python train.py    # ✅ Uses project venv with all dependencies
python train.py           # ⚠️  Uses whatever Python is on PATH
```

**If you forget `uv run`:**

- **Best case**: Uses mise's global Python + any globally installed packages
- **Likely case**: `ImportError: No module named 'pandas'`
- **Worst case**: Uses system Python with wrong versions

### **Solutions to Avoid This:**

**Option A: Use `uv shell` (like old virtualenv activate):**

```bash
cd my-project
uv shell                  # Activates the venv
python train.py           # Now works normally!
exit                      # Deactivate
```

**Option B: Create aliases/scripts:**

```bash
# In project root, create run.sh:
#!/bin/bash
uv run python "$@"

# Then:
./run.sh train.py         # Wrapper approach
```

**Option C: Accept the `uv run` pattern** (most common)

- Modern Python devs are adopting this
- Similar to `npm run` or `cargo run`
- Clear and explicit

## 2. Existing Projects with uv

### **For Existing Projects:**

```bash
cd existing-ml-project    # Your current project structure:
                         # ├── train.py
                         # ├── data/
                         # ├── models/
                         # └── requirements.txt

# This works fine:
uv init .                # Creates config in current directory
uv add -r requirements.txt  # Migrates dependencies
```

**You get:**

```
existing-ml-project/
├── train.py             # ← Your existing code stays put
├── data/
├── models/ 
├── pyproject.toml       # ← New uv config
├── uv.lock             # ← New lockfile
└── .python-version     # ← Python version
```

### **About the `src/` Structure:**

**You DON'T have to restructure!** uv is flexible:

```toml
# pyproject.toml - if you keep flat structure:
[project]
name = "my-project"
# No need to specify src layout

# OR if you want to move to src/ (optional):
[tool.setuptools.packages.find]
where = ["src"]
```

**Most data science projects stay flat:**

```
ml-project/
├── train.py           # Scripts at root
├── notebooks/         # Jupyter notebooks  
├── data/              # Data files
├── models/            # Saved models
└── pyproject.toml     # uv config
```

## 3. Global mise Tools Installation

### **Setting up Global Tools:**

```bash
# 1. Create the global config
mkdir -p ~/.config/mise
cat > ~/.config/mise/config.toml << EOF
[tools]
python = "3.13"
uv = "latest"
pipx = "latest"
gh = "latest"
EOF

# 2. Install them
mise install              # Installs everything in the config

# 3. Verify they're available
which python             # Should show mise's Python
which uv                 # Should show mise's uv
python --version         # Should be 3.13.x
```

### **How Global Access Works:**

mise modifies your `$PATH` automatically:

```bash
echo $PATH
# /Users/rholmes/.local/share/mise/installs/python/3.13/bin:
# /Users/rholmes/.local/share/mise/installs/uv/latest/bin:
# ... other paths
```

**It "just works"** after `mise install`! ✨

### **Verification Commands:**

```bash
# Check what's installed globally
mise list

# Check current active versions  
mise current

# Install missing tools
mise install

# Upgrade everything
mise upgrade
```

## Practical Workflow Example

**Day 1 - Global setup:**

```bash
# Set up global tools once
echo '[tools]\npython = "3.13"\nuv = "latest"' > ~/.config/mise/config.toml
mise install
```

**Day 2 - New project:**

```bash
mkdir new-ml-project && cd new-ml-project
uv init .
uv add pandas scikit-learn jupyter
uv run jupyter lab        # Ready to go!
```

**Day 3 - Existing project:**

```bash
cd old-project
uv init .                 # Add uv to existing project
uv add -r requirements.txt
uv run python train.py    # Now managed by uv
```

**Day 4 - Quick exploration:**

```bash
cd ~/scratch
python                    # Uses global mise Python 3.13
# Quick data exploration with global packages
```

## Pro Tips

1. **Start with `uv shell`** while learning - feels familiar
2. **Graduate to `uv run`** for scripts and automation
3. **Use global mise** for exploration and system tools
4. **Use local uv** for real projects
5. **Always commit** `pyproject.toml` and `uv.lock`

The beauty is you get **flexibility**: global tools for quick work, isolated environments for serious projects, and no more dependency hell! 🎯