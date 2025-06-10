     ## TL;DR — Same brains, different “bodies”
ChatGPT.com, GitHub Copilot Chat, GitHub Copilot **Agent Mode**, and Microsoft Copilot all expose GPT-4.1 (or o-series siblings) but surround it with **different system prompts, context builders, tool sets, and guardrails**.  
These wrapper layers decide **what the model can see, how long it can think, which tools it may call, and when it must refuse**—so depth of reasoning, latency, and even creativity vary noticeably across the four surfaces.

---

## 1 Stack-at-a-Glance

| Layer | ChatGPT.com | Copilot Chat (IDE/Web) | Copilot Agent Mode (Workspace / PR) | Microsoft Copilot Chat |
|-------|-------------|------------------------|-------------------------------------|------------------------|
| **Default model** | GPT-4.1 / GPT-4o / o-series | GPT-4.1 (default, switchable) :contentReference[oaicite:0]{index=0} | GPT-4.1 behind the scenes :contentReference[oaicite:1]{index=1} | GPT-4o for paid tenants :contentReference[oaicite:2]{index=2} |
| **System prompt focus** | “Helpful, honest, harmless” + your *Custom Instructions* | *“You are an AI programming assistant”*, scope limited to SW dev :contentReference[oaicite:3]{index=3} | Adds tasks like *analyze repo, run tests* | *Grounded* with Microsoft Graph data + corporate policy :contentReference[oaicite:4]{index=4} |
| **Context builder** | 128 k sliding window + file upload | Up to 64 k; embeds open files & nearby code :contentReference[oaicite:5]{index=5} | Full-repo graph, AST, PR diff | Combines prompt with Graph grounding & Bing search :contentReference[oaicite:6]{index=6} |
| **Built-in tools** | Browsing, Python, file analysis, vision, DALL·E :contentReference[oaicite:7]{index=7} | None; IDE handles code execution | GitHub Actions sandbox executes, tests, stages edits :contentReference[oaicite:8]{index=8} | Office file context, Teams messages, image gen; enterprise controls :contentReference[oaicite:9]{index=9} |
| **Memory** | Optional account-level memory | Per-repo embeddings only | Workspace persists across PR session | Tenant-scoped Graph history |
| **Typical refusal pattern** | Strict OpenAI policy; may ask clarifying qs | Refuses non-coding queries; short answers by design | Limited only by repo scope & policy | Extra corporate and compliance filters :contentReference[oaicite:10]{index=10} |

---

## 2 Why Depth Differs

### 2.1 Prompt Steering  
* Copilot Chat’s hard-coded prompt keeps answers short, impersonal, and code-centric, so attempts to “think aloud” or philosophize are truncated—hence the *“won’t dig deep”* feel. :contentReference[oaicite:11]{index=11}  
* Microsoft Copilot must ground every answer in Microsoft Graph or web results, adding safety layers that prefer concise business summaries. :contentReference[oaicite:12]{index=12}  

### 2.2 Context Fidelity  
* ChatGPT can “see” arbitrary text you paste plus uploads (huge essays, CSVs) but **not** your private repo.  
* Copilot Chat only sees the active file/selection and maybe a few nearby files, so long-range architectural questions stall. :contentReference[oaicite:13]{index=13}  
* Copilot Agent Mode builds a full dependency graph and can iterate for hours inside a PR workspace, enabling deeper reasoning over the whole codebase. :contentReference[oaicite:14]{index=14}  
* Microsoft Copilot’s grounding pipeline injects your calendar, e-mails, and docs, but strips raw internet noise—helpful for business context, limiting for open-ended research. :contentReference[oaicite:15]{index=15}  

### 2.3 Tool Availability  
* ChatGPT runs Python or live web search; it can chain tools mid-thought. :contentReference[oaicite:16]{index=16}  
* Copilot surfaces **no runtime tools**—the IDE compiles/runs code; the model only suggests text.  
* Agent Mode spins up GitHub Actions to run tests or linters automatically. :contentReference[oaicite:17]{index=17}  
* Microsoft Copilot invokes Microsoft 365 APIs for document creation or email drafts but cannot execute arbitrary code. :contentReference[oaicite:18]{index=18}  

### 2.4 Latency & Cost Tuning  
* Copilot completer may downshift to a smaller o-series model for <100 ms inline latency, while Copilot Chat keeps GPT-4.1 unless you switch. :contentReference[oaicite:19]{index=19}  
* Microsoft Copilot batches requests through the Graph grounding layer, adding 300-600 ms.  
* ChatGPT targets ~1 s for full answers and never swaps models mid-session unless you pick a different tier. :contentReference[oaicite:20]{index=20}  

---

## 3 Practical Advice

| Need | Best Surface | Why |
|------|--------------|-----|
| **Explain repo-local bug** | **Copilot Chat** | Quick inline context from current file; fine-tune answer manually if needed. |
| **Automate sweeping refactor / fix tests** | **Copilot Agent Mode** | Access to entire repo + ability to run CI tasks automatically. |
| **Ideation, research, writing docs** | **ChatGPT** | Long context window, web browsing, rich tool suite. |
| **Summarize Teams threads, draft PPT** | **Microsoft Copilot** | Deep integration with Graph data and Office formats. |
| **Ask “why does Copilot refuse?”** | ChatGPT (paste Copilot prompt) | No repo constraints; can reason about policy and suggest prompt tweaks. |

---

## 4 Troubleshooting “Shallow” Copilot Answers

1. **Scope check** – Make sure the file with the relevant code is open and selected; Copilot Chat can’t see hidden files. :contentReference[oaicite:21]{index=21}  
2. **Switch models** – In Copilot Chat’s “Models” dropdown pick GPT-4.1 or o4-mini-high for more reasoning tokens. :contentReference[oaicite:22]{index=22}  
3. **Chain prompts** – Break the request into *Clarify → Generate → Refine* steps; the short system prompt allows multi-turn depth even if single answers are terse.  
4. **Agent Mode for repo tasks** – Open a Copilot Workspace, give it an explicit goal (“refactor to DI pattern”), and let it iterate. :contentReference[oaicite:23]{index=23}  
5. **Fallback to ChatGPT** – Paste code snippets or design docs when you need cross-domain reasoning, mathematical proofs, or policy critique that Copilot filters out.

---

## 5 Key Takeaways

* The **raw GPT-4.1 weights are identical** across products; the *wrapping* layers drive the difference.  
* GitHub’s two Copilot modes trade **speed & scope**: *Chat* is a smart autocomplete, *Agent* is a repo-scale assistant.  
* Microsoft Copilot optimizes for **enterprise data safety** and document workflows, not deep coding dives.  
* When an answer feels shallow, it’s usually a **prompt-or-context bottleneck**, not the model’s capability.

---

### Sources
1. Copilot model selection docs :contentReference[oaicite:24]{index=24}  
2. Copilot Workspace for PRs :contentReference[oaicite:25]{index=25}  
3. Copilot system prompt leak (scope restrictions) :contentReference[oaicite:26]{index=26}  
4. Copilot context builder discussion :contentReference[oaicite:27]{index=27}  
5. Copilot Agent Mode blog post :contentReference[oaicite:28]{index=28}  
6. Microsoft 365 Copilot overview :contentReference[oaicite:29]{index=29}  
7. Microsoft 365 Copilot architecture & grounding :contentReference[oaicite:30]{index=30}  
8. Copilot Chat uses GPT-4o with enterprise controls :contentReference[oaicite:31]{index=31}  
9. Microsoft Copilot feature breakdown & policy layers :contentReference[oaicite:32]{index=32}  
10. ChatGPT o-series tool list (browsing, Python, vision) :contentReference[oaicite:33]{index=33}  
11. GPT-4o & o-series context info :contentReference[oaicite:34]{index=34}
