Here’s a polished, concise **Cheat Sheet / Guide Sheet** for providing scaffolding to Claude 3.7 Sonnet (or similar models) during your software engineering and development work. I’ve refined the earlier advice—clarifying where needed, expanding key points, collapsing redundancies, and generalizing for broader use—while folding in the practical tips. This should serve as a handy reference to maximize Claude’s performance for your coding tasks.

---

# Cheat Sheet: Scaffolding Claude 3.7 Sonnet for Software Development

**Purpose**: Claude 3.7 Sonnet doesn’t have built-in scaffolding or internet access, but you can boost its software engineering performance (e.g., toward that 70.3% SWE-bench level) by providing external structure and context. Use this guide to turn Claude into a powerhouse for coding, debugging, and development.

**Current Date**: March 08, 2025  
**Model Context**: Works for Claude 3.7 Sonnet, 3.5 Sonnet, or similar reasoning-focused AIs without native scaffolding.

---

## Core Scaffolding Techniques

### 1. Craft Rich, Structured Prompts
- **How**: Give Claude the full picture—code, error messages, expected outcomes, and specific guidance.
- **Example**:  
  ```
  Here’s my Python code: [insert code]. It throws “TypeError: unsupported operand” on line 8. I want it to add two numbers safely. Analyze and fix it.
  ```
- **Why**: Mimics SWE-bench’s contextual scaffolding, improving reasoning accuracy by 20-30% (per X user reports).
- **Tip**: Be explicit—vague prompts like “fix this” waste Claude’s potential.

### 2. Break Tasks into Steps
- **How**: Split complex problems into bite-sized prompts, fed sequentially.
- **Example**:  
  1. “Explain this function: [code].”  
  2. “Now optimize it for memory usage.”  
  3. “Rewrite it with your suggestions.”
- **Why**: Guides Claude through multi-step reasoning, reducing errors on big tasks.
- **Tip**: Treat it like pair programming—lead Claude one step at a time.

### 3. Supply Examples or Templates
- **How**: Provide a sample solution or pattern for Claude to adapt.
- **Example**:  
  ```
  Here’s a fixed version of a similar bug: [example code]. Use this approach to fix: [new code].
  ```
- **Why**: Claude excels at pattern-matching; examples act as a blueprint, cutting guesswork.
- **Tip**: Pull from your own codebase or open-source repos for relevance.

### 4. Feed in External Context
- **How**: Since Claude’s offline, manually add fresh data (docs, threads, etc.).
- **Example**:  
  ```
  Here’s the latest NumPy docs on array slicing: [text]. Rewrite my script using this: [code].
  ```
- **Why**: Bridges Claude’s lack of internet, giving it up-to-date info to work with.
- **Tip**: Use GitHub issues, Stack Overflow, or library docs—scrape them yourself.

### 5. Activate Thinking Mode (Pro Plan)
- **How**: Prompt Claude to reason step-by-step explicitly.
- **Example**:  
  ```
  Debug this code step-by-step: [code]. Show your thought process.
  ```
- **Why**: Forces Claude to self-scaffold, leveraging its top-tier reasoning (e.g., 70.3% SWE-bench caliber).
- **Tip**: Pair with structured prompts for best results.

---

## Practical Tips for Software Development

### Test and Iterate
- **How**: Start with a small task (e.g., a bug fix), scaffold heavily, and refine your approach based on output.
- **Why**: Fine-tunes your scaffolding style to Claude’s strengths.
- **Example**: Try fixing a loop error with a rich prompt, then adjust if Claude misses edge cases.

### Combine with Dev Tools
- **How**: Use Claude for high-level reasoning alongside tools like linters (pylint), IDEs (VS Code), or Copilot for syntax.
- **Why**: Claude shines at logic and planning; let other tools handle grunt work.
- **Example**: Claude designs an algorithm, Copilot fills in boilerplate.

### Benchmark Performance
- **How**: Test Claude on a real-world task (e.g., a GitHub issue) and compare to a human fix.
- **Why**: Gauges how close you’re getting to SWE-bench-level success (aim for 50-70%).
- **Example**: Pick a bug from your project, scaffold Claude, and score its solution.

### Generalize Across Tasks
- **How**: Adapt these techniques for coding, debugging, optimization, or even non-dev tasks (e.g., writing docs).
- **Why**: Scaffolding’s universal—Claude thrives with structure, whatever the job.
- **Example**: Use “Break Tasks into Steps” for a code review or a design spec.

---

## Quick Notes
- **Scaffolding Isn’t Built-In**: Claude’s high SWE-bench scores (e.g., 70.3%) come from external help in tests—you replicate that here.
- **Time Investment**: Scaffolding takes effort but pays off in precision. Expect 5-10 minutes upfront per task.
- **Scaling Up**: For big projects, batch small tasks with consistent scaffolding to maintain quality.
