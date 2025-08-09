# VSCode Agent Mode: Quick Reference

## Essential Setup (2 minutes)

### 1. Enable Agent Mode
- **Requirement:** VS Code 1.99+ (June 2025 stable)  
- **Access:** Copilot Chat panel → Toggle to "Agent" mode
- **No preview flags needed** (now GA)

### 2. Create Project Instructions
**File:** `.github/copilot-instructions.md` (commit to repo)

```markdown
**Project:** [Brief description]
**Tech Stack:** [Languages, frameworks, versions]  
**Constraints:** [Don't use X, always use Y pattern]
**Style:** [Key conventions: snake_case, PEP8, etc.]
```

## The 4-Step Workflow

| Step | Action | Example |
|------|--------|---------|
| **1. Define Goal** | Be specific, start fresh chat | "Optimize parseData() from O(n²) to O(n)" |
| **2. Add Context** | Use `#file:path` syntax | "Error in `#file:logs/crash.txt`, fix `#file:src/parser.cpp`" |
| **3. Review Plan** | Agent shows what it will do | Approve or correct before coding starts |
| **4. Supervise** | Monitor edits, approve commands | Watch real-time diffs, provide feedback |

## Prompt Templates

### Bug Fix Template
```markdown
**Bug:** [Clear description]
**Context:** #file:src/problematic.cpp, suspected [cause]
**Task:** 
1. Investigate root cause
2. Fix the issue  
3. Verify with tests
```

### Feature Template  
```markdown
**Feature:** [Name]
**Requirements:**
- Frontend: [UI needs]
- Backend: [API needs] 
- Tests: [Validation needs]
**Context:** #file:existing/similar.cpp
**Task:** Plan and implement complete feature
```

### Design Doc Template
```markdown
**Design Spec:** [Feature name]
**Structure:** Overview, Solution, Impact, Testing
**Context:** #file:docs/existing-design.md
**Task:** Generate technical specification with diagrams
```

## Context Management

### What to Attach
| File Type | When | Best Practice |
|-----------|------|---------------|
| **Source** | Code changes | Include .h + .cpp for C++ |
| **Logs** | Bug fixes | Actual error messages |
| **Tests** | Features | Show expected patterns |
| **Specs** | Design work | API docs, requirements |

### Context Limits
- **Theoretical:** 200k tokens (modern models)
- **Practical:** ~80k tokens in VS Code  
- **Solution:** Quality over quantity—attach 3-5 relevant files max

## Command Approval Quick Guide

| Command | Risk | Decision |
|---------|------|----------|
| `ls`, `git status` | Low | ✅ Usually approve |
| `npm test`, `pytest` | Medium | ✅ Good for verification |
| `make`, `npm build` | Medium | ✅ If build system trusted |
| `rm`, `mv` files | High | ⚠️ Review paths carefully |
| Network calls | High | ⚠️ Understand what it downloads |

## Troubleshooting

| Problem | Quick Fix |
|---------|-----------|
| **Agent "forgets" context** | Start new chat, attach key files only |
| **Stuck repeating failed fix** | Interrupt: "Stop, try [different approach]" |
| **Wrong coding style** | Check `.copilot-instructions.md` has examples |
| **Build commands fail** | Verify VS Code tasks configured for project |
| **Slow responses** | Too many files attached—simplify context |

## When NOT to Use Agent Mode

Use **simpler tools** for:
- Single file edits → Copilot Edits mode
- Quick questions → Standard Copilot Chat
- Variable renaming → Search & replace  
- Simple refactoring → VS Code refactoring tools

## Best Practices Checklist

### Before Starting
- [ ] Fresh chat for each major task
- [ ] Repository instructions file created
- [ ] Relevant files identified for context
- [ ] Clear, specific goal defined

### During Execution  
- [ ] Review agent's plan before approval
- [ ] Monitor real-time edits as they happen
- [ ] Approve shell commands thoughtfully
- [ ] Provide feedback if agent gets stuck

### After Completion
- [ ] Review all generated code
- [ ] Run additional tests manually  
- [ ] Check code follows team standards
- [ ] Verify feature works end-to-end

## Advanced Patterns

### Iterative Refinement
```
You: [Initial request]
Agent: [Makes changes]
You: "Good, but add thread safety"
Agent: [Adjusts with mutex/locks]
You: "Perfect, now add unit tests"
```

### Multi-Step Features
```
You: "Add user authentication system"
Agent: "I'll create: 1) User model 2) Login API 3) JWT handling 4) Frontend forms 5) Tests"
You: "Looks good, proceed"
[Agent implements systematically]
```

### Design-First Approach
```
You: "Design a caching system architecture"
Agent: [Creates design doc with diagrams]
You: [Review and approve design]
You: "Now implement this design"
Agent: [Codes according to approved spec]
```

## Useful Phrases

### Steering the Agent
- "Stop, let's try a different approach"
- "Explain your reasoning for this change"  
- "Follow the pattern in `#file:examples/similar.cpp`"
- "Add error handling for [specific case]"
- "Make it thread-safe using our ThreadPool utility"

### Quality Control
- "Review this for security vulnerabilities"
- "Optimize for performance, target O(n log n)"
- "Add comprehensive unit tests"
- "Follow our coding standards in the instructions file"
- "Document the public API with examples"

---

**Remember:** You're the pilot, Copilot Agent is your co-pilot. Set clear direction, provide oversight, and validate results. Agent Mode excels at multi-step implementation within your guidance.