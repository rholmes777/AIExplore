# VSCode Agent Mode: Complete Guide

## Quick Start / TL;DR

GitHub Copilot's **Agent Mode** is an autonomous AI pair programmer in VS Code that handles multi-step coding tasks—from bug fixes to feature development. Unlike basic code completion, Agent Mode can analyze your entire codebase, make coordinated edits across multiple files, run builds and tests, and iterate until completion.

### Essential Setup (30 seconds)
1. **Enable Agent Mode:** VS Code 1.99+ has Agent Mode in stable release
2. **Create project instructions:** Add `.github/copilot-instructions.md` with your tech stack and conventions
3. **Start a focused chat:** One task per session, be specific about your goal

### The 4-Step Workflow
1. **Define Clear Goal:** "Fix segfault in BackgroundWorker::stop()" not "improve this"
2. **Provide Context:** Use `#file:src/Parser.cpp` syntax to attach relevant files
3. **Review Plan:** Agent shows what it will do—correct before it starts coding
4. **Supervise & Approve:** Monitor edits, approve shell commands, provide feedback

## Setup & Prerequisites

### Version Requirements (June 2025 Status)
- **VS Code:** 1.99+ (stable release with Agent Mode GA)
- **Context Window:** Modern models support up to 200,000 tokens (OpenAI o3/o4-mini, Claude 4 Sonnet/Opus)
- **Practical Limit:** ~80k tokens due to IDE overhead before truncation errors
- **No Preview Flag Required:** Agent Mode is now generally available

### Repository-Level Configuration

#### Persistent Instructions (`.github/copilot-instructions.md`)
Create this file at your repository root. Copilot automatically includes it in every chat session for consistent guidance across your team.

**What to Include:**
```markdown
# Project Context for Copilot

**Project:** CLI tool for processing genomic data
**Tech Stack:** C++17 with Python 3.10 scripts, Qt5 GUI, Boost 1.75

**Constraints:**
- Do NOT use C++20 features  
- Use snake_case for C++ variables, PEP8 for Python
- Database access via our in-house ORM, not raw SQL
- Multi-threading: Use ThreadPool utility, NOT std::thread directly
- Do not modify files in /build/ or @generated files

**Performance Requirements:** 
- Functions must handle 10M+ records efficiently
- Prefer O(n log n) algorithms when possible
```

#### Reusable Prompt Templates (`.github/prompts/*.prompt.md`)
For recurring tasks, create templates that team members can attach:

**Example: `security-review.prompt.md`**
```markdown
Review this code for security vulnerabilities:
- Input validation and sanitization
- Authentication and authorization checks
- SQL injection prevention
- Buffer overflow protection
- Rate limiting considerations
```

### Verification Setup
Check that instructions are active by looking for `.github/copilot-instructions.md` in the "References" section after agent responses.

## Core 4-Step Workflow

### Step 1: Define a Clear and Focused Goal
**Start fresh chat for each distinct task.** Vague prompts lead to poor results.

❌ **Bad:** "Improve this function's performance"
✅ **Good:** "Optimize the `parseData()` function for speed—reduce runtime from O(n²) to O(n) without changing external behavior"

**For Features, Include Requirements:**
```markdown
**Feature:** Add 'forgot password' functionality
**Requirements:**
- Frontend: Email input form accessible from login page  
- Backend: Generate secure reset token (1-hour expiry)
- Email: Send reset link via existing EmailService
- Database: Add password_reset_token field to User model
- Tests: Unit tests for token generation and expiration
```

### Step 2: Provide Essential Context
While Agent Mode can search your workspace, direct context is more effective.

**Use `#file` Syntax:**
```markdown
The error in #file:logs/crash.txt indicates null pointer dereference in #file:src/Parser.cpp. Fix the crash when processing empty input.
```

**Attach Multiple Context Types:**
- **Source files:** Both `.cpp` and `.h` for C++ tasks
- **Error logs:** Actual stack traces or exception messages  
- **Specifications:** Design docs or API specs
- **Related code:** Similar implementations for reference
- **Test files:** Existing tests that show expected behavior

### Step 3: Review the Agent's Plan
For non-trivial tasks, Agent Mode first proposes a plan. **Always review before approving.**

**Example Agent Plan Output:**
> "To implement password reset, I will:
> 1. Add password_reset_token field to User model
> 2. Create /api/password-reset endpoint in auth.py  
> 3. Implement token generation with 30-minute expiry
> 4. Add frontend ResetPassword component
> 5. Integrate with EmailService for sending reset links
> 6. Write unit tests for token lifecycle"

**Your Review Options:**
- ✅ Approve: "Looks good, proceed"
- ❌ Correct: "Use existing PasswordResetToken model, don't create new field"
- 🔄 Refine: "Also add input validation on the frontend form"

### Step 4: Supervise, Approve, and Iterate
Once the plan is approved, monitor execution:

**Editing Phase:**
- Real-time diffs appear in your editor
- Agent works through files systematically
- You can interrupt with corrections mid-process

**Testing Phase:**
- Agent proposes commands: `npm test`, `pytest`, `./build.sh`
- **You must approve each command** before execution
- Agent analyzes output and self-corrects failures

**Iteration Loop:**
- Failed tests → Agent reads error → Attempts fix → Retests
- Build errors → Agent reads compiler output → Adjusts code
- **Your role:** Provide guidance if agent gets stuck

## Workflow Examples

### Bug Fixing Workflow

**Template Structure:**
```markdown
**Bug:** [Clear description with impact]
**Error/Log:** [Actual error messages or attach log file] 
**Context:** [Where to look, suspected cause]
**Task:**
1. Investigate root cause
2. Explain proposed fix briefly  
3. Implement code changes
4. Verify fix with tests/build
```

**Complete C++ Example:**
```markdown
**Bug:** Application crashes with SIGSEGV in `BackgroundWorker::stop()` when main window closes during active background task.

**Context:**
- Crash is intermittent, likely threading race condition
- Relevant code: #file:src/BackgroundWorker.cpp and #file:src/MainWindow.cpp  
- Suspect worker thread accessed after deletion

**Task:**
1. Investigate race condition in thread shutdown
2. Propose safe thread termination approach  
3. Implement fix (add mutex/join as needed)
4. Verify app closes cleanly without crashes

Run unit tests with `./run_tests.sh` to confirm fix.
```

### Feature Implementation Workflow

**User Story Approach:**
```markdown
**Feature:** Password Reset via Email

**User Story:** As a user, I want to reset my password via email so I can regain access if I forget it.

**Acceptance Criteria:**
- Frontend: "Forgot Password?" link → email input form
- Backend: `/api/password-reset` endpoint generates secure token (30min expiry)
- Email: Send reset link using existing EmailService  
- Security: Single-use tokens, securely random generation
- Tests: Unit tests for token generation, integration test for full flow

**Context:**
- Email templates in `email_templates/reset.html`
- User model: #file:models/user.py
- Existing auth: #file:src/auth.py

**Task:** Plan and implement complete password reset feature.
```

### Design Documentation Workflow

**Specification Generation:**
```markdown
**Design Spec Needed:** Advanced Search Filtering Feature

**Structure Required:**
- Overview (problem statement and goals)
- Proposed Solution (high-level approach + architecture diagram)  
- Detailed Design (classes/modules to modify, data flow)
- Alternatives Considered (other approaches evaluated)
- Impact Analysis (performance, security considerations)
- Testing Strategy (validation approach)

**Context:** Current search in #file:docs/SearchArchitecture.md
Use existing design doc format from #file:docs/FeatureTemplate.md

Generate first draft with technical details and Mermaid diagrams where helpful.
```

## Best Practices & Agent Coordination

### Effective Agent Guidance

**Set Clear Goals and Constraints, Then Let It Work:**
```markdown
**Goal:** Implement caching system
**Constraints:** 
- Must work on Windows + Linux
- Use only standard C++ libraries (no third-party)
- Thread-safe design required
- Cache size limit: 100MB max

[Let agent plan the implementation approach]
```

**Avoid Micromanaging:**
❌ Don't: "Open fileA.cpp, change line 45 to call foo(), then in fileB.cpp add new class..."
✅ Do: "Update logging system to use asynchronous writes for better performance"

**Stay Actively Engaged:**
- Monitor proposed changes in real-time
- Intervene at key decision points: "That approach might be too slow, consider lazy-loading instead"
- Ask for explanations: "Why did you choose recursive implementation here?"

### Iterative Refinement Patterns

**Feedback Loop:**
1. Agent makes changes
2. You review critically
3. Provide specific feedback: "Function works but isn't thread-safe—add mutex around critical section"
4. Agent adjusts and continues

**Course Correction:**
- Stop bad approaches early: "Actually, this approach won't work because [reason]. Try [alternative] instead"
- Use undo controls if agent goes wrong direction
- Start fresh chat if discussion becomes too tangled

### Context Management

**Quality over Quantity:**
- Attach 3-5 highly relevant files rather than 20 loosely related ones
- Close unrelated files in editor before starting
- Use fresh chats for new tasks to avoid context pollution

**When to Break Into New Chat:**
- Switching from bug fix to feature work
- Context window getting full (conversation very long)
- Agent seems confused or "forgot" earlier instructions
- Starting completely different area of codebase

## Capabilities & Limitations

### Current Capabilities (June 2025)

| Feature | Status | Details |
|---------|---------|---------|
| **Multi-file Edits** | ✅ GA | Coordinates changes across entire codebase |
| **Build/Test Integration** | ✅ GA | Runs commands with approval, self-corrects on failures |
| **Autonomous Planning** | ✅ GA | Creates and executes multi-step task plans |
| **Real-time Streaming** | ✅ GA | Shows code changes as they happen |
| **Context Window** | ✅ 200k tokens | Modern models support very large context |
| **MCP Tool Integration** | ⚠️ Limited | GitHub-owned tools available, third-party coming |

### Limitations & Workarounds

**Context Window Reality:**
- **Theoretical:** 200,000 tokens for modern models
- **Practical:** ~80k tokens before truncation issues in VS Code
- **Workaround:** Focus conversations, attach only essential files

**Planning Reliability:**
- **Issue:** Agent may occasionally misinterpret requirements or get stuck
- **Mitigation:** Review plans before approval, provide feedback early

**Code Quality Variance:**
- **Issue:** Generated code may not match team standards
- **Solution:** Use detailed `.copilot-instructions.md` with examples

**Performance Considerations:**
- **Agent Mode Overhead:** Slower than basic completions due to multi-step process
- **Usage Limits:** Each iteration counts toward quotas
- **Best Practice:** Reserve agent mode for multi-step tasks, use simple chat for quick questions

### When NOT to Use Agent Mode

**Use Simpler Tools Instead:**
- **Single file edits:** Use Copilot Edits mode
- **Quick questions:** Use standard Copilot Chat  
- **Simple refactoring:** Use built-in VS Code refactoring
- **Variable renaming:** Use search-and-replace

**Environment Prerequisites:**
- Ensure build/test commands work before letting agent run them
- Configure VS Code tasks for your project's build system
- Have permissions set up for file operations

## Future Outlook

### Near-Term Improvements (6-12 months)

**Expanded Context Windows:**
- Models moving toward 1M+ token windows
- Will enable full repository context in single session
- Reduced need for manual context curation

**Enhanced Tool Integration:**
- Broader MCP (Model-Context Protocol) support
- Integration with CI/CD pipelines, issue trackers
- Custom tool development for team-specific workflows

**Improved Planning Algorithms:**
- More reliable multi-step reasoning
- Better error recovery and iteration
- Fine-grained undo/redo capabilities

**Performance Optimizations:**
- Faster model inference times
- More generous usage quotas
- Model selection based on task complexity

### Conservative Expectations

**What Won't Change Soon:**
- Agent Mode won't become fully independent (you remain the pilot)
- Code review and validation still essential
- Human judgment required for architecture decisions
- Security and performance considerations need human oversight

**Evolution of Developer Role:**
- More time reviewing AI-generated code, less writing boilerplate
- Focus shifts to high-level design and quality assurance
- Agent handles implementation details within your guidance
- Partnership model: human strategy + AI execution

## Quick Reference Tables/Cheatsheets

### Prompt Templates Quick Reference

| Task Type | Template Structure | Key Elements |
|-----------|-------------------|--------------|
| **Bug Fix** | Bug → Context → Task → Verification | Error details, suspected cause, relevant files |
| **Feature** | Story → Requirements → Context → Task | User value, acceptance criteria, existing patterns |
| **Design Doc** | Topic → Structure → Context → Output Format | Problem scope, required sections, reference docs |
| **Refactor** | Current State → Goal → Constraints → Approach | What to change, why, limitations, success criteria |

### Context Attachment Strategies

| File Type | When to Attach | Best Practice |
|-----------|----------------|---------------|
| **Source files** | Always for code changes | Include both .h and .cpp for C++ |
| **Error logs** | Bug fixes, debugging | Actual stack traces, not summaries |
| **Test files** | Feature work, refactoring | Show expected behavior patterns |
| **Config files** | Environment-related tasks | Database configs, build settings |
| **Documentation** | Design work, specifications | API specs, architecture docs |

### Command Approval Guidelines

| Command Type | Risk Level | Approval Strategy |
|--------------|------------|------------------|
| **Read-only** (`ls`, `cat`, `git status`) | Low | Generally safe to approve |
| **Build commands** (`make`, `npm build`) | Medium | Approve if you trust the build system |
| **Test commands** (`pytest`, `npm test`) | Medium | Good for verification, usually safe |
| **File operations** (`rm`, `mv`) | High | Review carefully, check paths |
| **Network calls** (`curl`, `wget`) | High | Understand what it's downloading |

### Troubleshooting Common Issues

| Problem | Symptoms | Solution |
|---------|----------|----------|
| **Context Overflow** | Agent "forgets" earlier instructions | Start new chat, attach key files only |
| **Stuck in Loop** | Repeatedly trying same failed approach | Interrupt and provide corrective guidance |
| **Wrong Architecture** | Suggests unfamiliar patterns | Reference repository instructions, provide examples |
| **Slow Performance** | Long delays between responses | Check if too many files attached, simplify context |
| **Build Failures** | Can't run project commands | Verify VS Code tasks configured, check permissions |

### Model Selection Guide

| Task Complexity | Recommended Approach | Rationale |
|------------------|---------------------|-----------|
| **Simple edits** | Standard Copilot completions | Faster, lower resource usage |
| **Single-file changes** | Copilot Edits mode | Quick iteration without agent overhead |
| **Multi-file features** | Agent Mode with GPT-4/Claude | Complex reasoning and coordination needed |
| **Architecture planning** | Agent Mode with largest context model | Needs broad codebase understanding |
| **Quick questions** | Standard Copilot Chat | Immediate responses without planning overhead |

---

*This guide reflects VSCode Agent Mode capabilities as of June 2025. As the technology evolves rapidly, check the latest GitHub Copilot documentation for the most current features and best practices.*