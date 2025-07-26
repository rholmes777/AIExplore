Here’s a **quick Claude Sonnet vs Opus cheat sheet**, tailored for your coding/configuration/dev workflow needs:

---

## 🧠 Claude Cheat Sheet for Technical Work

|**Task Type**|**Best Model**|**Why**|
|---|---|---|
|🔧 **Simple scripts** (Bash, Python, CLI)|**Sonnet 3.7**|Fast, responsive, low hallucination risk|
|🛠 **Env setup** (`mise`, `pyenv`, `direnv`)|**Opus 4**|Handles multi-step CLI+config context better|
|🧩 **LangChain agent logic**|**Opus 4**|Needs tool reasoning, memory of chain steps|
|📖 **Markdown/doc parsing & summarizing**|**Sonnet 3.7**|Efficient unless document spans >20k tokens|
|⚙️ **Multi-repo analysis (Aider-style)**|**Opus 4**|Stronger cohesion, handles multi-file reasoning|
|🧪 **Troubleshooting/debugging config issues**|**Opus 4**|Lower hallucination risk, better pattern tracking|
|🗃 **Refactoring >2 files across tools**|**Opus 4**|Maintains intent across large, linked contexts|
|🔄 **Prompt chain design/testing**|**Sonnet 3.7**|Quicker feedback loop for minor changes|
|📊 **Interpreting benchmarks or logs**|**Opus 4**|More precise in parsing and correlating log lines or perf metrics|
|📦 **Install issues (e.g. `brew`, pip, nvm)**|**Sonnet 3.7**|Quick and sufficient, unless the setup is multi-layered (then use Opus)|

---

## 🧭 Guidance

- Use **Sonnet 3.7** for:
    
    - High-speed iterative testing
        
    - Syntax or formatting fixes
        
    - Anything where you know what you're doing but want a helper
        
- Use **Opus 4** when:
    
    - You’re unsure how pieces fit together (multi-step config)
        
    - You're building agents, abstractions, or toolchains
        
    - A hallucination would waste real time
        

---

Let me know if you want to generate a `.md` snippet of this or tailor it to a specific stack (e.g., Python-based CLI tools, Node/TS monorepos, etc).