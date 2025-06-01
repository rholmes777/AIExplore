# Common Artifacts Across Agentic Coding Workflows: Context, Memory, and Instruction Files

AI agents are becoming increasingly sophisticated tools for developers, with platforms like GitHub Copilot, JetBrains Junie, Cursor, and OpenAI Codex offering autonomous coding assistance. These systems rely on specialized files to maintain context, set parameters, and preserve memory. Understanding how these artifacts function across different platforms provides insights into effective agentic workflow management.

## Context and Instruction Files

### AGENTS.md: The Codex Standard

The AGENTS.md file serves as a standardized knowledge base for OpenAI Codex and compatible AI agents. According to the specification details:

- **Scope and Location**: AGENTS.md files define rules for "the entire directory tree rooted at the folder that contains it" with more deeply-nested files taking precedence in case of conflicts[9][10]
- **Function**: These files provide "context-specific information about your project's structure, conventions, and requirements"[3]
- **Content Structure**: Typically includes coding standards, project organization, testing procedures, and PR message formatting requirements[3][10]

AGENTS.md files help OpenAI Codex "understand your codebase architecture and start contributing effectively, dramatically reducing the time needed for AI to become productive"[3]. The specification states that "for every file you touch in the final patch, you must obey instructions in any AGENTS.md file whose scope includes that file"[10], establishing clear hierarchical rules.

### Platform-Specific Context Files

Different platforms implement their own variations of context files:

1. **GitHub Copilot Custom Instructions**:
   - Stored in user settings rather than project repositories
   - Contains sections for code standards, development flow, repository structure, and key guidelines[7]
   - Enables consistent behavior across sessions: "Custom instructions...is where you can really start shaping how Copilot behaves across a session"[7]

2. **JetBrains Junie Guidelines**:
   - Stored in ".junie/guidelines.md" in the root project directory
   - Provides "persistent, reusable context to the agent"[8]
   - Can be version-controlled and is applied to every task Junie works on[8]

3. **Cursor and Windsurf Rules Files**:
   - Cursor uses "cursor.rules" in the project root
   - Windsurf uses ".windsurf.rules" (supporting YAML or JSON formats)[12]
   - These files address the problem that "AI coding tools can't read your mind. They don't understand the context behind your project's goal or quirks"[12]

4. **Netlify Context Files**:
   - Official context files in .mdc or .txt format
   - Can be added via CLI commands like "netlify recipes ai-context"
   - Ensure AI tools have "accurate, up-to-date information about platform capabilities and best practices"[6]

## Memory Systems

Memory systems allow AI agents to maintain continuity across sessions and conversations:

### Types of Memory Implementation

1. **PraisonAI's Configurable Memory**:
   - Offers multiple provider options including "rag", "mem0", and "none"
   - Supports both short-term and long-term memory storage
   - Uses embedding-based semantic search capabilities[14]

2. **Cline's Memory Bank**:
   - Community-created custom instruction set
   - Uses a folder structure approach: "Before you do any work, check the memory-bank/ folder in the project"
   - Combines markdown files with Mermaid diagrams to maintain documentation structure[16]

3. **Basic Memory Concepts**:
   - AI agent memory enables "storing and recalling past experiences to improve decision-making"
   - Unlike simple reflex agents, memory-enabled agents can "retain context, recognize patterns over time and adapt based on past interactions"[11]
   - Memory addressing the limitation that "large language models (LLMs) cannot, by themselves, remember things"[11]

## Cross-Platform Comparisons and Workflows

### Common Patterns

Despite platform differences, several common patterns emerge across agentic artifacts:

1. **Project Structure Documentation**:
   All platforms encourage documenting file organization, directory structures, and component relationships[3][7][12]

2. **Coding Standards and Conventions**:
   Consistent focus on providing style guides, naming conventions, and formatting rules[7][8][12]

3. **Development Workflow Information**:
   Instructions for common tasks like building, testing, and deployment processes[3][7]

4. **Hierarchy of Instructions**:
   Most systems implement some form of precedence rules, with more specific or direct instructions overriding general ones[10]

### Key Differentiators

1. **Integration Approach**:
   - GitHub Copilot integrates with existing development environments as a plugin
   - Cursor and Windsurf require adopting entirely new development environments[7]

2. **Location and Versioning**:
   - Some artifacts (AGENTS.md, Junie guidelines) are version-controlled with the project
   - Others (Copilot custom instructions) are tied to user profiles[7][8]

3. **Memory Persistence Strategies**:
   - Ranges from file-based approaches (Memory Bank) to sophisticated database systems (PraisonAI)[14][16]

## Conclusion

The emergence of standardized artifacts like AGENTS.md, context files, and memory systems reflects the industry's recognition that "just as developers need clear documentation and well-structured codebases, AI agents need the right context to be helpful"[6]. These artifacts serve as critical interfaces between human developers and AI assistants, establishing conventions, maintaining context, and enabling more efficient collaborative workflows.

While implementation details vary across platforms, the fundamental purpose remains consistent: providing AI agents with the necessary context to generate higher-quality code that aligns with project standards and requirements. As the field evolves, we may see further standardization of these artifacts, particularly as developers seek to leverage multiple AI agents across different stages of the development lifecycle.

Sources
[1] image.jpg https://pplx-res.cloudinary.com/image/upload/v1748705472/user_uploads/58300541/3a0a59fa-eb5e-4183-8907-0fe0b0c82a62/image.jpg
[2] Meet 4 developers leading the way with AI agents - Source https://news.microsoft.com/source/features/ai/meet-4-developers-leading-the-way-with-ai-agents/
[3] Agents.md Guide for OpenAI Codex - Enhance AI Coding https://agentsmd.net
[4] GitHub Copilot’s New Agent Mode Enables Autonomous Code Completion https://gbhackers.com/github-copilots-new-agent-mode/
[5] GitHub - letta-ai/agent-file https://github.com/letta-ai/agent-file
[6] AI pair programming: enhancing Developer Experience through Agent Experience (AX) | Netlify https://www.netlify.com/blog/ai-better-pair-programmer-with-agent-experience/
[7] Copilot ask, edit, and agent modes: What they do and when to use them https://github.blog/ai-and-ml/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/
[8] Guidelines | Junie Documentation - JetBrains https://www.jetbrains.com/help/junie/customize-guidelines.html
[9] Introducing Codex - OpenAI https://openai.com/index/introducing-codex/
[10] System Prompt of Codex https://baoyu.io/blog/codex-system-prompt
[11] What Is AI Agent Memory? | IBM https://www.ibm.com/think/topics/ai-agent-memory
[12] Code Smarter, Not Harder: How Contextual Rules Supercharge AI Coding Assistants https://dev.to/govindvyas/code-smarter-not-harder-how-contextual-rules-supercharge-ai-coding-assistants-2dj6
[13] Oracle Health's Clinical AI Agent Helps Doctors Spend More Time ... https://www.oracle.com/news/announcement/oracle-clinical-ai-agent-2024-10-29/
[14] AI Agents with Memory - PraisonAI Documentation https://docs.praison.ai/concepts/memory
[15] What are AI agents? - GitHub https://github.com/resources/articles/ai/what-are-ai-agents
[16] Memory Bank: How to Make Cline an AI Agent That Never Forgets https://cline.bot/blog/memory-bank-how-to-make-cline-an-ai-agent-that-never-forgets
[17] AI Agents: An Advanced Version of Medical AI Scribes - OmniMD https://omnimd.com/blog/ai-medical-scribe-vs-ai-agent-upgrade/
[18] AI Agents in Healthcare: Transforming Diagnosis and Treatment https://smythos.com/ai-industry-solutions/healthcare/ai-agents-in-healthcare/
[19] GitHub Copilot Agent Mode: Enhancing Developer Workflows https://dev.to/brylie/github-copilot-agent-mode-enhancing-developer-workflows-2ae0
[20] GitHub - mem0ai/mem0: Memory for AI Agents https://github.com/mem0ai/mem0
[21] Zep - AI Agent Memory https://www.getzep.com
