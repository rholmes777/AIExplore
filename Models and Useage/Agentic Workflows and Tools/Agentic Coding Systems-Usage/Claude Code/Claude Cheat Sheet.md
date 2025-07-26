- **IDE Integrations**: Claude Code offers direct integrations with popular IDEs 
- **MCP Integration**: Claude Code supports the MCP protocol
- **`claude.md` File for Instructions**: Similar to Cursor rules, the `claude.md` file contains persistent instructions for how the agent should handle tasks.    
- **Auto-Accept Edits**: Users can enable "auto-accept edits" mode (using Shift+Tab).    
- **Custom Slash Commands**: Custom slash commands as markdown files in the `.claude` folder. 
	- Project commands in project directory `.claude/commands`
	- Global commands in `~/.claude/commands`
- **GitHub Actions Integration**: Mention Claude within GitHub to review pull requests or assign tasks that are then executed remotely.
- **Plan Mode and "Think Hard" Keyword**: Claude Code now includes a core "plan mode" accessible via Shift+Tab [[17:41](http://www.youtube.com/watch?v=aHTXccrfXC8&t=1061)]. Users can also use keywords like "think hard," "think harder," or "ultrathink" in prompts to encourage Claude Code to spend more time analyzing and generating a more reasoned plan before executing a task [[20:09](http://www.youtube.com/watch?v=aHTXccrfXC8&t=1209)].

## Synopsis
1. To enter multi-line editing on macOS, press Option+Enter; for other systems, a quick escape is available with \ + Enter.
2. You can enable auto-accept by launching Claude with the `--dangerously-skip-permissions` flag.
3. The thinking levels, in order, are: "think", "think hard", "think harder", and "UltraThink".

https://gemini.google.com/app/11e02c427dc0565d

---

Claude’s slash-command system is **scope-based**: it decides where to load a command from (and therefore who can see it) by the folder you save the Markdown file in and the prefix you type in the prompt. Below is a concise primer on the two scopes you asked about—**project-specific** and **global (a.k.a. personal)**—followed by an end-to-end overview of how custom commands work today.

---

## Key take-aways (one-paragraph summary)

Project commands live inside the repository at `.claude/commands/` and are invoked with `/project:`; they travel with the codebase, making them perfect for workflows that only make sense in that repo (e.g. “generate migrations” or “build the firmware”). Personal commands live in `~/.claude/commands/` (or `%USERPROFILE%\.claude\commands\` on Windows) and are invoked with `/user:`; they load in **every** project you open, so they’re ideal for cross-repo utilities such as note-taking, session logging (your `claude-sessions` commands), or favourite lint-then-commit templates. You can freely copy or symlink a project command into your global folder (or vice-versa) to change its scope—no other edits required.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"), [github.com](https://github.com/iannuttall/claude-sessions?utm_source=chatgpt.com "iannuttall/claude-sessions: Custom slash commands for ... - GitHub"))

---

## 1 / Scopes compared

|Scope|Folder|Prefix|Who sees it|Typical use|
|---|---|---|---|---|
|**Project**|`.claude/commands/`inside repo|`/project:`|Everyone who checks out the repo|Repo-specific workflows, shared team tools|
|**Personal (global)**|`~/.claude/commands/`|`/user:`|Only you, in every repo you open|Reusable utilities, personal productivity helpers|

Anthropic’s docs emphasise that scope is **directory-driven**; the CLI simply scans both locations when you hit `/` and merges the results.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))

---

## 2 / How Claude resolves & prioritises commands

1. **Slash menu**: When you type `/`, Claude lists built-ins first, then _project_, then _personal_. Namespacing (see below) keeps the list tidy.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))
    
2. **Settings precedence**: If command files reference `settings.json` options (permissions, env vars, etc.), those settings follow the normal hierarchy—local project overrides shared project overrides user.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/settings "Claude Code settings - Anthropic"))
    
3. **Shadowing**: A project command named `fix` will **override** a personal command of the same name in the slash menu, so choose names carefully or rely on namespaces.
    

---

## 3 / Anatomy of a command file

```markdown
---
description: "Start or resume a focused coding session."
allowed-tools: Bash(git status:*), Bash(git diff:*)
---

## Context
- Current branch: !`git rev-parse --abbrev-ref HEAD`
- Git status: !`git status --short`
- Recent commits: !`git log -5 --oneline`

## Task
Write a short plan for the next 30 minutes addressing $ARGUMENTS.
```

- **Front-matter** (`allowed-tools`, `description`) controls security prompts.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))
    
- **Back-ticks with `!`** execute Bash and inject the output.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))
    
- `@path/to/file.js` embeds file contents; `$ARGUMENTS` injects what comes after the command in the prompt.
    
- **One file = one command**—community discussions confirm that splitting a single logical command across multiple files confuses the parser.([reddit.com](https://www.reddit.com/r/ClaudeAI/comments/1lhws2e/best_practices_for_creating_custom_commands_slash/ "Best practices for creating custom commands (slash commands) : r/ClaudeAI"))
    

---

## 4 / Namespacing & prefixes

Placing files in sub-folders creates additional colons in the command name:

```
.claude/commands/frontend/build.md   ➜  /project:frontend:build
~/.claude/commands/git/commit.md     ➜  /user:git:commit
```

Anthropic’s reference calls this _namespacing_ and recommends it for large command collections.([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))

---

## 5 / Moving a command between scopes

Because scope is purely path-based you can:

```bash
# promote a project command to global scope
mkdir -p ~/.claude/commands/session
cp .claude/commands/session-start.md ~/.claude/commands/session/
```

Restart Claude Code and it now appears as `/user:session-start` in **every** repo. The `claude-sessions` README explicitly suggests this for users who want the logging workflow everywhere.([github.com](https://github.com/iannuttall/claude-sessions?utm_source=chatgpt.com "iannuttall/claude-sessions: Custom slash commands for ... - GitHub"))

Tip: use a **symlink** instead of a copy to keep a single source of truth:

```bash
ln -s "$(pwd)/.claude/commands/session-start.md" ~/.claude/commands/session-start.md
```

---

## 6 / Best-practice checklist

|Recommendation|Why|
|---|---|
|**Keep global commands generic** (no repo-specific paths).|Prevents breakage when invoked in unrelated projects.|
|**Use namespaces for large sets** (`/user:git:*`, `/project:db:*`).|Keeps auto-complete readable.|
|**Document required tools** in `allowed-tools`; otherwise Claude floods you with permission prompts.|Security + smoother UX.|
|**Add project commands to repo** so teammates get them automatically; add personal commands to dot-files repo or symlink.|Share vs. personal.|
|**Watch for prefix quirks**: a recent bug occasionally drops “/user:” if the command lives under `~/.config/claude/commands`. Track the GitHub issue for fixes.([github.com](https://github.com/anthropics/claude-code/issues/2348?utm_source=chatgpt.com "Incorrect Custom Slash Command Prefix for User-Defined ... - GitHub"))||
|**Explore curated sets** like “awesome-claude-code” for inspiration.([github.com](https://github.com/hesreallyhim/awesome-claude-code "GitHub - hesreallyhim/awesome-claude-code: A curated list of awesome commands, files, and workflows for Claude Code"))||

---

## 7 / Why your _session_ commands belong in `~/.claude/commands/`

`/project:session-*` templates work anywhere, and you probably don’t want dozens of identical copies across repos. Copying or symlinking them into `~/.claude/commands/` turns them into `/user:session-*`, giving you:

- **Zero setup** in new projects—just `claude` and go.
    
- **Single history folder** if you tweak the commands to log outside the repo (e.g. `~/claude-sessions/`).
    
- **No accidental commit** of private logs.
    

If a particular repo needs _extra_ session metadata, keep a tiny project wrapper that calls the global command and adds repo-specific context—e.g. `.claude/commands/session/start.md` with `Include @docs/CONTRIBUTING.md then /user:session-start $ARGUMENTS`.

---

### Copy-paste cheat-sheet

```markdown
# Create folders
mkdir -p ~/.claude/commands
mkdir -p .claude/commands

# Move a project command to global
mv .claude/commands/mytool.md ~/.claude/commands/

# Invoke
/user:mytool   # global
/project:build-assets   # project

# Namespace example
~/.claude/commands/git/commit.md  ➜  /user:git:commit
```

---

### Further reading

- Anthropic Slash-command reference ([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/slash-commands "Slash commands - Anthropic"))
    
- Settings hierarchy for user vs. project configs ([docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/settings "Claude Code settings - Anthropic"))
    
- Agentic-coding best practices blog ([anthropic.com](https://www.anthropic.com/engineering/claude-code-best-practices "Claude Code Best Practices \ Anthropic"))
    
- Community cheat sheet & `.claude/commands` patterns ([htdocs.dev](https://htdocs.dev/posts/claude-code-best-practices-and-pro-tips/ "Claude Code: Best Practices and Pro Tips"))
    
- `claude-sessions` repo README ([github.com](https://github.com/iannuttall/claude-sessions?utm_source=chatgpt.com "iannuttall/claude-sessions: Custom slash commands for ... - GitHub"))
    
- Prefix bug discussion ([github.com](https://github.com/anthropics/claude-code/issues/2348?utm_source=chatgpt.com "Incorrect Custom Slash Command Prefix for User-Defined ... - GitHub"))
    
- “One command per file” Reddit thread ([reddit.com](https://www.reddit.com/r/ClaudeAI/comments/1lhws2e/best_practices_for_creating_custom_commands_slash/ "Best practices for creating custom commands (slash commands) : r/ClaudeAI"))
    
- Awesome command collection ([github.com](https://github.com/hesreallyhim/awesome-claude-code "GitHub - hesreallyhim/awesome-claude-code: A curated list of awesome commands, files, and workflows for Claude Code"))
    

You’re now set to sculpt a command toolkit that loads seamlessly wherever you code—project IDs stay local, personal power-ups follow you everywhere. Happy automating!

https://chatgpt.com/share/686054b7-5234-8002-8dde-a7cdf48bf282

---
# Claude Code: Best practices for agentic coding
https://www.anthropic.com/engineering/claude-code-best-practices

---
## Claude Sessions (GitHub)
https://github.com/iannuttall/claude-sessions

---
