**In one sentence:** _Even when the identical “GPT-4.1” weights are running on the GPU, ChatGPT.com, GitHub Copilot, and JetBrains AI feel different because each wraps the raw model in its own stack of system-prompts, context builders, tools, and guardrails—and those layers strongly steer what the model can “see,” what it’s asked to do, and therefore how well it performs._

---

## 1 Where the Same Model Shows Up

|Surface|Typical top-tier model today|Max context window|Built-in tools|Primary pre-prompt focus|
|---|---|---|---|---|
|**ChatGPT.com**|GPT-4.1 / GPT-4o / o4-mini|up to 128 k tokens|Browsing, Python (code-interpreter), file-analysis, vision, DALL·E|“Helpful, honest, harmless” general assistant + your _Custom Instructions_|
|**GitHub Copilot (IDE/CLI)**|GPT-4.1 (plus Claude, Gemini, o3/4-mini etc.)|64 k tokens in Copilot Chat|Codebase retriever, repo graph, agent-mode (runs tests via Actions)|“You are a senior software engineer” + inline code context & AST snippets|
|**JetBrains AI Assistant**|GPT-4o, GPT-4.1, o3-mini, Gemini, local LLMs|up to 128 k tokens (inherits model limit)|IDE PSI/AST, refactor engine, commit generator, tests, local search|Prompt templates tied to IDE actions; users can create custom prompts|

_Key takeaway:_ The “above-the-model” stack—system prompt + context builder + tools—varies far more than the underlying weights.

---

## 2 System Prompts & Alignment Layers

### 2.1 ChatGPT

- A huge hidden system prompt encodes policy, tool-usage guidelines, and user _Custom Instructions_ fields.
    
- RLHF/RLAIF training optimizes for polite, exhaustive answers across any domain.
    

### 2.2 GitHub Copilot

- Pre-prompt injects the active file, relevant neighboring files, diagnostics, and repo metadata, then says _“respond with valid code only”_ for completions.
    
- Copilot Chat adds a repository-aware “coprocessor” that decides when to search or stage changes, enabled by agent-mode tools.
    

### 2.3 JetBrains AI

- Each IDE action ships its own template (e.g., _“Explain this Kotlin stack-trace”_); users may override or chain prompts.
    
- When you choose a different backend (Gemini vs GPT-4o), JetBrains swaps the system prompt to match provider quirks.
    

---

## 3 Context-Building & Memory

|Feature|ChatGPT|Copilot|JetBrains|
|---|---|---|---|
|**Automatic retrieval**|Tool call to browsing/RAG when the model “decides” it needs fresh facts|Embedding search over current repo + Code Search API|PSI tree + usage search over project scope|
|**Session memory**|Optional account-level memory across chats|Per-repo embeddings; no cross-project memory|Project-bound caches; no cloud memory|
|**Window mgmt**|128 k summarization heuristics|64 k sliding window & heuristics for large files|Up to model limit; IDE decides which slices of code/AST to send|

---

## 4 Tooling Layer

- **ChatGPT** can run Python, read uploaded files, call DALL·E, or hit the live web; these tools are behind function calls auto-selected by the model.
    
- **Copilot** tools live outside the model: GitHub Actions spin up sandboxes to execute, test, and iterate on code changes.
    
- **JetBrains AI** proxies IDE services (refactor engine, compiler) so the model can suggest edits but the IDE does the heavy lifting.
    

---

## 5 Why Output Quality Differs (Even with the Same Weights)

1. **Prompt steering** – A code-only Copilot prompt suppresses long natural-language digressions, while ChatGPT encourages fuller prose.
    
2. **Context fidelity** – Copilot’s curated code slice preserves symbol definitions; ChatGPT may truncate large code blobs; JetBrains adds rich type info.
    
3. **Tool availability** – ChatGPT can fetch web docs or compute; Copilot can run linters/tests; JetBrains can invoke refactor engines.
    
4. **Safety filters** – ChatGPT’s public policy is stricter (e.g., no license-violating code) than Copilot’s enterprise policy knobs.
    
5. **Latency & cost tuning** – Copilot may fall back to a smaller model for completions to keep typing latency <100 ms; ChatGPT keeps you on GPT-4.1 unless you pick a cheaper tier; JetBrains lets you switch models manually.
    

---

## 6 Performance Patterns You’ll Notice

|Task|ChatGPT Web|Copilot|JetBrains AI|
|---|---|---|---|
|**Explaining an algorithm**|Best general exposition; rich analogies|Adequate; may shortcut details|Similar to Copilot but injects language-specific hints|
|**Live refactor across 50 files**|Manual; you copy/paste|Agent-mode can stage PR autonomously|IDE intentions automate structural refactors|
|**Quick inline completion**|None (editor-agnostic)|30–70 ms avg latency on small model fallback|Slightly slower but offers AST-aware suggestions|
|**Researching external API usage**|Uses browsing tool to cite docs|Leverages repo code search; can’t hit live web|No external web, but can inspect local SDK sources|

---

## 7 Bottom Line for Developers

- **ChatGPT** is a _generalist_: broad knowledge, powerful tools, but no deep repo context.
    
- **GitHub Copilot** is a _repo-specialist_: tailored system prompt + code graph + agent workflows give it an edge on large-scale code editing, at the cost of narrower domain knowledge.
    
- **JetBrains AI Assistant** is a _language-aware IDE sidekick_: same top-tier models, plus rich PSI/type info and customizable prompts, but limited to what’s inside your editor.
    

Choose the surface that matches your bottleneck: idea exploration (ChatGPT), automated code change (Copilot), or in-IDE context-aware guidance (JetBrains).

---

### Further reading

- [wired.com](https://www.wired.com/story/openai-announces-4-1-ai-model-coding?utm_source=chatgpt.com)