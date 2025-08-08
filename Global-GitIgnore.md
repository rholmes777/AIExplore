# Global .gitignore Reference and Documentation

## Overview
This document explains the recommended global .gitignore configuration for a macOS development environment with comprehensive coverage of AI tools, multiple programming languages, and common IDEs. The configuration is designed to ignore temporary files, build artifacts, and AI tool scratch files while being permissive enough for actual development work.

## Organized .gitignore Categories

### Development Tooling
- `.bundle` - Ruby bundler local configuration
- `.direnv`, `.envrc` - direnv environment management files
- `.mise.toml` - Mise (formerly rtx) development environment manager
- `vendor/` - Vendor dependencies (Ruby, Go, etc.)

### Xcode/iOS Development
- `*.pbxuser`, `*.mode1v3`, `*.mode2v3`, `*.perspectivev3` - Xcode user-specific settings
- `*.xcuserstate` - Xcode UI state
- `xcuserdata/` - Xcode user data directory

### AI Tools
- `.aider*` - Aider CLI tool files and configurations (covers .aider directory and .aider.conf.yml)
- `.claude/` - Claude-related temporary files
- `.codex/` - GitHub Codex files
- `CLAUDE.md` - Claude Code configuration (uppercase - the standard naming)
- `aider.md` - Aider documentation/configuration
- `codex.md` - Codex documentation
- `ai-scratch.md`, `ai-instructions.md` - AI working files
- `*-scratch.md`, `*-notes.md` - Pattern for temporary scratch/notes files
- `my-notes.md` - Personal notes file

### IDE and Editor Files
- `.idea/`, `*.iml`, `*.ipr`, `*.iws` - JetBrains IDEs (IntelliJ, PyCharm, WebStorm, etc.)
- `.vscode/` - VS Code workspace settings
- `*.code-workspace` - VS Code workspace files
- `.obsidian/` - Obsidian note-taking app metadata

### Programming Languages

#### Python
- `*.pyc` - Python compiled bytecode
- `__pycache__/` - Python 3 bytecode cache directories
- `*.egg-info/` - Python package metadata
- `MANIFEST` - Python manifest file
- `dist/`, `build/` - Python packaging directories
- `venv/`, `env/`, `ENV/`, `.venv/` - Virtual environment directories
- `.coverage` - Coverage.py data file
- `htmlcov/` - HTML coverage reports
- `.pytest_cache/` - Pytest cache
- `.tox/` - Tox testing environments

#### Node.js/JavaScript
- `node_modules/` - NPM/Yarn dependencies
- `npm-debug.log*` - NPM debug logs
- `yarn-debug.log*` - Yarn debug logs
- `yarn-error.log*` - Yarn error logs
- `.pnp.*` - Yarn Plug'n'Play files

#### C/C++/Objective-C
- `*.o` - Object files

### Environment and Configuration
- `.env` - Environment variables
- `.env.local` - Local environment overrides
- `.env.*.local` - Environment-specific local overrides

### Logs and Testing
- `*.log` - Log files
- `logs/` - Log directories
- `coverage/` - Generic coverage reports

### Backup and Temporary Files
- `*~.nib` - Interface Builder backup files
- `\#*#`, `.#*` - Emacs auto-save and lock files
- `*~` - General backup files (vim, emacs, etc.)

### Operating System Files

#### macOS
- `.DS_Store`, `.DS_Store?` - macOS folder metadata
- `._*` - macOS resource forks
- `.Spotlight-V100` - Spotlight index
- `.Trashes` - Trash metadata

#### Windows
- `ehthumbs.db`, `Thumbs.db` - Windows thumbnail cache

## Design Rationale

### Why These Patterns?

1. **AI Tool Files**: CLAUDE.md and similar files are ignored globally to allow local AI tool configuration without committing to repositories by default. This enables using Claude Code on any repository for experimentation without affecting the codebase.

2. **Duplication Removed**: Removed `.aider/` since `.aider*` already covers all aider-related files and directories.

3. **Case Sensitivity**: Using `CLAUDE.md` (uppercase) as this is the standard naming convention. On macOS with case-insensitive filesystem (default), this will match both cases.

4. **Comprehensive Language Support**: Added Python virtual environments, Node.js modules, and testing artifacts that are commonly left uncommitted.

5. **IDE Coverage**: Expanded to include VS Code alongside JetBrains and Xcode.

6. **Flexible Patterns**: Kept `*-scratch.md` and `*-notes.md` patterns for temporary documentation that shouldn't be committed.

### Trade-offs

- **Overly Specific Files**: Keeping `my-notes.md` and `ai-instructions.md` as they're common personal file names that rarely need committing.
- **Log Files**: Ignoring all `*.log` files globally - specific logs that need committing can use `git add -f`.
- **Environment Files**: Ignoring all `.env*` patterns for security - environment files should never be committed.

## macOS Case Sensitivity Note

macOS uses a case-insensitive filesystem by default (HFS+ or APFS), which means:
- `CLAUDE.md` will match `claude.md`, `Claude.md`, etc.
- This behavior is filesystem-dependent, not git-dependent
- On case-sensitive filesystems (Linux, case-sensitive APFS), exact case matching is required

## Usage Instructions

1. Save the configuration below to `~/.gitignore_global`
2. Configure git to use it: `git config --global core.excludesfile ~/.gitignore_global`
3. For files you want to track despite being ignored, use `git add -f <filename>`
4. To check if a file is ignored: `git check-ignore -v <filename>`

## Ready-to-Use Global .gitignore

```gitignore
# Development Tooling
.bundle
.direnv
.envrc
.mise.toml
vendor/

# Xcode/iOS Development
*.pbxuser
*.mode1v3
*.mode2v3
*.perspectivev3
*.xcuserstate
xcuserdata/

# AI Tools
.aider*
.claude/
.codex/
.obsidian/
CLAUDE.md
aider.md
codex.md
ai-scratch.md
ai-instructions.md
*-scratch.md
*-notes.md
my-notes.md

# IDE and Editor Files
.idea/
*.iml
*.ipr
*.iws
.vscode/
*.code-workspace

# Python
*.pyc
__pycache__/
*.egg-info/
MANIFEST
dist/
build/
venv/
env/
ENV/
.venv/
.coverage
htmlcov/
.pytest_cache/
.tox/

# Node.js/JavaScript
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnp.*

# C/C++/Objective-C
*.o

# Environment and Configuration
.env
.env.local
.env.*.local

# Logs and Testing
*.log
logs/
coverage/

# Backup and Temporary Files
*~.nib
\#*#
.#*
*~

# macOS
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes

# Windows
ehthumbs.db
Thumbs.db
```