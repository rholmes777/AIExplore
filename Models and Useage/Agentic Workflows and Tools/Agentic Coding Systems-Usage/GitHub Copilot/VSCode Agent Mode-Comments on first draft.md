@Copilot: this is information that can be integrated into the first draft, including updated context window limits, verification that the VS preview is no longer required, a bit more neutral benefits statements, etc. 

GitHub Copilot’s **repository‑level custom instructions** and **prompt files** are designed to live _in_ the repository so that every contributor (and their local VS Code instance) receives identical guidance. Below is a neutral confirmation of those mechanics, of the current Agent‑mode capabilities available in the June 2025 stable release of VS Code, and of the typical context‑window sizes now offered by leading large‑context models.

---

## 1  |  Location and Version‑Control Expectations

|File / Folder|Purpose|Must be committed?|Rationale & Docs|
|---|---|---|---|
|`.github/copilot‑instructions.md`|Persistent, repo‑wide guidance automatically appended to every Copilot Chat / Agent prompt opened **inside that repository**|**Yes** – it is intended to be stored under version control alongside the code so that the whole team sees the same rules|GitHub Docs explicitly direct you to place it in the repo root under `.github`and note that all collaborators benefit automatically.|
|`.github/prompts/*.prompt.md`|Re‑usable _prompt templates_(public preview in VS Code) that a user can attach to a chat session via _Attach context → Prompt..._|**Yes** – created in the workspace under `.github/prompts`, committed like any other Markdown asset|The folder is created by the _Chat: Create Prompt_command; templates are then shared with anyone who checks out the repo.|

_Why it is **not** a local‑only setting:_ Both mechanisms rely on the file path being present for Copilot to read and to add as a reference in responses. Local settings (the VS Code `settings.json`) _enable/disable_ their use, but the files themselves are stored in the project, not the user profile. This lets teams update guidance via normal pull‑request workflows.

---

## 2  |  Agent‑Mode Feature Check (Stable VS Code 1.99+)

|Capability|Present in  June 2025 stable?|Evidence|
|---|---|---|
|**Plan → multi‑file edits → iterate**|✅|Agent mode GA announcement (Visual Studio / VS Code) states it “handles multi‑step tasks… loops until completion”.|
|**Running build / test commands**(with user approval)|✅|Doc page shows agent _“might run unit tests… If the tests fail, it re‑edits”_ and mentions the `chat.agent.maxRequests` iteration limit. GitHub issue #8106 discusses the approval dialog for shell commands.|
|**Streaming diffs directly into the editor**|✅|Same doc notes code edits are streamed in real time during execution.|
|**MCP tool integration (pulling external data)**|⚠️ Early GA — only GitHub‑owned tools today; wider third‑party hooks announced but not yet broadly released.||
|**Prompt‑file UI inside VS Code**|✅ (still labelled “preview”)|Enabled via `"chat.promptFiles": true`; creation and use workflow documented in GitHub Docs.|

> **What was removed in this revision?**  
> – All marketing language (“next evolution”, “super‑productive”) and preview caveats that no longer apply were dropped.  
> – Only capabilities verifiably in the June 2025 release are listed; anything still experimental is flagged as such.

---

## 3  |  Typical Context‑Window Sizes (mid‑2025)

|Model (publicly available)|Documented context window|
|---|---|
|**OpenAI o3 / o3‑pro**|200 000 tokens input + 100 000 output tokens|
|**OpenAI o4‑mini**|Same 200 k input window (lighter model)|
|**Anthropic Claude 4 Sonnet**|200 000 tokens|
|**Anthropic Claude 4 Opus**|200 000 tokens|

> _Note_: real‑world usable length can be lower because IDE plug‑ins must allocate space for Copilot’s own scaffolding + your prompt + the model’s answer. Copilot does not expose the raw number, but large‑file chats > 100 k tokens generally require manual trimming or summarisation; community threads confirm practical limits often ~80 k before truncation errors appear.

---

## 4  |  Short, Neutral Benefit Statement

> **Why bother with these files and Agent Mode at all?**  
> Putting shared rules in `.github/copilot‑instructions.md` and reusable templates in `.github/prompts`ensures that every Copilot interaction—bug fix, feature work, or documentation draft—starts with the same project context and standards. Agent Mode can then apply those rules autonomously across multiple files, run the project’s actual test suite, and refine its work until tests pass or you stop it, while still requiring explicit approval before executing shell commands. The result is faster iteration without forfeiting code‑review control.

---

### Citations used

1. GitHub Docs – repository instruction file creation
    
2. GitHub Docs – prompt files workflow & storage
    
3. GitHub Docs – definition & applicability of custom instructions
    
4. VS Code documentation – Agent Mode workflow & test‑running loop
    
5. DevBlogs (Microsoft) – GA announcement and capabilities
    
6. GitHub issue track – user approval for shell commands
    
7. VS Code blog – introduction of Agent Mode features (multi‑file, run tests)
    
8. Anthropic model overview – 200 k context for Claude 4 Sonnet/Opus
    
9. OpenAI help article – o3/o4‑mini 200 k context window
    
10. OpenAI API docs – o3‑mini model specification (200 k context)
    
11. Community thread confirming practical limits of large‑context calls
    

_(All links retrieved 24 Jun 2025 and reference the current, non‑preview product manuals.)_