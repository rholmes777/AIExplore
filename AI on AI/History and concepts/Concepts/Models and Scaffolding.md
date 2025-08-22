# Models and Scaffolding: Understanding Infrastructure Layers in AI Systems

**In one sentence:** _Modern AI systems like ChatGPT, GitHub Copilot, and Microsoft Copilot use identical foundation models but deliver vastly different experiences through their unique scaffolding layers—system prompts, context builders, tool integrations, and coordination protocols that determine what the model can see, how it responds, and how well it performs._

---

## 1 Foundation Models vs. Scaffolding Infrastructure

### 1.1 The Common Foundation
Most enterprise AI systems in 2025 share similar foundation models:
- **GPT-N, GPT-N pro** - OpenAI's flagship models (currently GPT-5, GPT-5 thinking, GPT-5 pro as of August 2025)
- **GPT reasoning models** - Optimized for complex reasoning tasks  
- **Claude Sonnet, Claude Haiku** - Anthropic's models (currently Claude 4 Sonnet)
- **Gemini N** - Google's offerings (currently Gemini 2.5)

### 1.2 Where Differentiation Happens
The scaffolding layer creates the actual user experience through:

|Component|Function|Impact on Performance|
|---|---|---|
|**System Prompts**|Define personality, scope, and behavior constraints|Determines response style, depth, and domain focus|
|**Context Builders**|Manage information flow and memory systems|Controls what information the model can access|
|**Tool Integration**|Enable external capabilities and actions|Extends model functionality beyond text generation|
|**Coordination Protocols**|Orchestrate multi-agent workflows and handoffs|Enables complex, multi-step task execution|

---

## 2 Current AI System Architectures

### 2.1 Surface Comparison

| Platform                | Foundation Model                  | Context Management           | Built-in Tools                  | Coordination Layer                   |
| ----------------------- | --------------------------------- | ---------------------------- | ------------------------------- | ------------------------------------ |
| **ChatGPT**             | GPT-N/GPT reasoning               | Sliding window + memory      | Browsing, Python, vision, Sora  | Single-agent with tool chaining      |
| **GitHub Copilot Chat** | Multiple                          | Repository-scoped embeddings | IDE integration only            | Code-focused single agent            |
| **Copilot Agent Mode**  | Multiple                          | Full repository graph        | GitHub Actions sandbox          | Multi-step autonomous workflows      |
| **JetBrains AI**        | Multiple (GPT-N, Gemini N, local) | IDE PSI/AST context          | Refactor engine, compiler tools | IDE-integrated agent                 |
| **Microsoft Copilot**   | Multiple                          | Microsoft Graph grounding    | Office apps, Teams integration  | Enterprise multi-agent orchestration |

### 2.2 System Prompt Differentiation

**ChatGPT Web**: "Helpful, honest, harmless" with custom instructions support
- Optimized for general-purpose conversation and problem-solving
- Encourages detailed explanations and step-by-step reasoning

**GitHub Copilot**: "You are an AI programming assistant"
- Hard-coded to keep responses concise and code-focused
- Refuses non-programming queries to maintain scope

**Microsoft Copilot**: Enterprise-first with Graph data grounding
- Must validate responses against corporate data sources
- Includes compliance and security filters

---

## 3 Advanced Context Management (2025)

### 3.1 Memory Architecture Evolution
Modern AI systems employ sophisticated context management strategies:

**Dynamic Context Windows**: Systems now intelligently expand and contract context based on task complexity, with some implementations achieving over 1 million token context windows for complex reasoning tasks.

**Semantic Chunking**: Rather than simple sliding windows, 2025 systems use semantic understanding to retain the most relevant context while summarizing or discarding less critical information.

**Cross-Session Memory**: Advanced systems maintain persistent memory across sessions, with ChatGPT's optional memory and Copilot's repository-scoped embeddings leading the way.

### 3.2 Context Retrieval Patterns

|System|Retrieval Strategy|Performance Impact|
|---|---|---|
|**Vector Search**|Semantic similarity matching|High relevance, moderate latency|
|**Graph Traversal**|Relationship-based context building|High accuracy for connected information|
|**Hybrid RAG**|Combined vector + keyword + semantic|Best overall performance for complex queries|

---

## 4 Coordination and Orchestration (2025 Developments)

### 4.1 Model Context Protocol (MCP)
The Model Context Protocol emerged as the standardization framework for AI agent coordination in 2025:

**Unified Context Sharing**: MCP enables seamless context persistence across different tools and agents, reducing information loss during handoffs by 67%.

**Cross-Tool Coordination**: Agents can now maintain contextual continuity when switching between different applications or services.

**Enterprise Adoption**: Fortune 500 companies are rapidly adopting MCP-based systems, with 65% projected implementation by 2027.

### 4.2 Multi-Agent Orchestration Frameworks

**LangGraph**: Explicit multi-agent coordination through directed graphs with conditional logic and hierarchical control.

**CrewAI**: Team-based agent coordination with role-based specialization and collaborative workflows.

**Google ADK**: Agent Development Kit for production-ready agentic applications with end-to-end development support.

---
## 5 Tool Integration and Capability Extension

### 5.1 Current Tool Ecosystems

**ChatGPT Web**
- Python code interpreter with persistent sessions
- Real-time web browsing and search
- File analysis and document processing
- Sora image generation
- Vision capabilities for image analysis

**GitHub Copilot Ecosystem**
- **Chat Mode**: IDE-integrated code assistance
- **Agent Mode**: Autonomous GitHub Actions workflows
- Repository analysis and code graph traversal
- Automated testing and validation

**Microsoft Copilot Suite**
- Microsoft Graph data integration
- Office application automation
- Teams and email context
- Enterprise security and compliance tools

**Note**
All models are converging on common extensions such as image analysis, tool calls for coding, etc.

### 5.2 Emerging Tool Patterns
**Sandbox Execution**: Secure code execution environments for testing and validation
**API Orchestration**: Intelligent routing between different service endpoints
**Document Intelligence**: Advanced parsing and analysis of complex document formats
**Workflow Automation**: Multi-step process automation with human oversight points

---

## 6 Performance Characteristics by Use Case

### 6.1 Task-Specific Performance

| Task Type                          | Best Platform        | Why                                 | Performance Advantage              |
| ---------------------------------- | -------------------- | ----------------------------------- | ---------------------------------- |
| **Algorithm Explanation**          | ChatGPT Web          | Rich exposition with analogies      | Deep conceptual understanding      |
| **Large-Scale Refactoring**        | Copilot Agent Mode   | Full repository access + automation | Can process 50+ files autonomously |
| **Inline Code Completion**         | IDE-integrated tools | Low latency specialized models      | 30-70ms response times             |
| **API Documentation Research**     | ChatGPT Web          | Live web access                     | Real-time information retrieval    |
| **Enterprise Document Processing** | Microsoft Copilot    | Graph data integration              | Contextual business intelligence   |

### 6.2 Latency and Model Switching
**Intelligent Model Selection**: Systems now automatically switch between models based on task requirements:
- Small, fast models for simple completions (<100ms)
- Large reasoning models for complex analysis (1-3s)
- Specialized models for domain-specific tasks

**Context Optimization**: Advanced caching and preprocessing reduce context preparation time by up to 60%.

---

## 7 Future Architecture Trends

### 7.1 Emerging Patterns
**Hybrid Human-AI Orchestration**: Regulated industries implementing systems with explicit human oversight points
**Event-Driven Coordination**: Real-time response systems with millisecond coordination latencies
**Hierarchical Agent Networks**: Complex workflows with supervisor agents managing specialized sub-agents

### 7.2 Infrastructure Scaling
**Zero-Shot Coordination**: Agents can coordinate effectively without prior training on specific collaboration patterns
**Distributed Processing**: Agent workloads distributed across cloud regions for optimal performance
**Adaptive Resource Allocation**: Dynamic scaling based on coordination complexity and user demand

---

## 8 Practical Implementation Guidance

### 8.1 Choosing the Right Platform

**For Individual Developers**:
- **Exploration and Research**: ChatGPT Web for broad knowledge access
- **Code-Focused Work**: GitHub Copilot for repository-aware assistance
- **IDE Integration**: JetBrains AI for language-specific tooling

**For Enterprise Teams**:
- **Business Process Automation**: Microsoft Copilot for Graph integration
- **Large-Scale Development**: Copilot Agent Mode for autonomous workflows
- **Custom Solutions**: Consider MCP-based frameworks for specialized needs

### 8.2 Optimization Strategies

**Context Preparation**: Structure prompts and context to match the target system's strengths
**Tool Chain Integration**: Leverage native tool ecosystems rather than forcing cross-platform workflows
**Memory Management**: Implement session persistence strategies appropriate to your use case
**Performance Monitoring**: Track coordination efficiency and adjust agent allocation accordingly

---

## 9 Key Takeaways

1. **Foundation models are commoditizing**; differentiation happens at the scaffolding layer
2. **Context management** is becoming the primary performance bottleneck and optimization target
3. **Multi-agent coordination** is maturing into enterprise-ready infrastructure with measurable ROI
4. **Model Context Protocol** is emerging as the key standardization framework for 2025-2027
5. **Intelligent model switching** and resource allocation are becoming core competencies
6. **Enterprise adoption** is accelerating, with Fortune 500 companies leading MCP implementation

The AI infrastructure landscape is rapidly consolidating around these scaffolding patterns, with successful implementations focusing on context optimization, coordination efficiency, and tool integration rather than foundation model selection.

---

## Further Reading

- [IBM AI Agent Orchestration Overview](https://www.ibm.com/think/topics/ai-agent-orchestration)
- [Google Agent Development Kit Documentation](https://developers.googleblog.com/en/agent-development-kit-easy-to-build-multi-agent-applications/)
- [Model Context Protocol Specification](https://github.com/modelcontextprotocol/spec)
- [Enterprise Multi-Agent Systems Analysis](https://medium.com/@josefsosa/ai-agent-orchestration-enterprise-framework-evolution-and-technical-performance-analysis-4463b2c3477d)

# Extended Section on Context Management Schemes

## Overview

- **Dynamic context windows** today are a mix of (a) _bigger native windows_ (e.g., 1M tokens) and (b) _smart plumbing_that decides what to include: paging KV caches, faster attention kernels, streaming/“infinite” attention, and budget‑aware prompt assembly. Native 1M windows exist (Gemini 2.5 Pro; Claude Sonnet 4 in beta), while most widely deployed assistants still default to 128k–200k. ([Google DeepMind](https://deepmind.google/models/gemini/pro/?utm_source=chatgpt.com "Gemini 2.5 Pro"), [Anthropic](https://docs.anthropic.com/en/docs/build-with-claude/context-windows?utm_source=chatgpt.com "Context windows"), [OpenAI](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/?utm_source=chatgpt.com "GPT-4o mini: advancing cost-efficient intelligence"))
    
- **Semantic chunking** is standard in RAG: split by meaning (not fixed sizes), then _re‑rank_ and _compress_ the survivors before they hit the prompt. Tools: LangChain/LlamaIndex semantic splitters, GraphRAG, contextual compression, rerankers. ([LangChain](https://python.langchain.com/docs/how_to/semantic-chunker/?utm_source=chatgpt.com "How to split text based on semantic similarity"), [LlamaIndex](https://docs.llamaindex.ai/en/stable/examples/node_parsers/semantic_chunking/?utm_source=chatgpt.com "Semantic Chunker"), [Microsoft](https://www.microsoft.com/en-us/research/project/graphrag/?utm_source=chatgpt.com "Project GraphRAG - Microsoft Research"))
    
- **Cross‑session memory**: ChatGPT offers optional, controllable memory across chats; Copilot builds _repository‑scoped indices/embeddings_ so chat answers can reference your code. Both ship with clear controls and limits. ([OpenAI](https://openai.com/index/memory-and-new-controls-for-chatgpt/ "Memory and new controls for ChatGPT | OpenAI"), [GitHub Docs](https://docs.github.com/copilot/concepts/indexing-repositories-for-copilot-chat "Indexing repositories for Copilot Chat - GitHub Docs"), [Visual Studio Code](https://code.visualstudio.com/docs/copilot/reference/workspace-context "Making chat an expert in your workspace"), [The GitHub Blog](https://github.blog/ai-and-ml/generative-ai/what-is-retrieval-augmented-generation-and-what-does-it-do-for-generative-ai/?utm_source=chatgpt.com "What is retrieval-augmented generation, and what does it do for ..."))
    

---

## 3.1 Memory Architecture Evolution

### Dynamic Context Windows

**What this means in practice**  
“Dynamic” doesn’t usually mean the model’s _architecture_ grows and shrinks at runtime. Instead, systems dynamically _assemble_ the prompt (what goes into the fixed window) and _route_ to models/windows that fit the task and latency budget.

**1) Bigger native windows (when you really need them)**

- **1M‑token models**: Google’s Gemini 1.5/2.5 Pro supports a 1M context for long‑form multimodal tasks; Anthropic’s **Claude Sonnet 4** now offers a 1M context (beta/limited tiers). These are the current top end used in production ecosystems. ([blog.google](https://blog.google/technology/ai/google-gemini-next-generation-model-february-2024/?utm_source=chatgpt.com "Introducing Gemini 1.5, Google's next-generation AI model"), [Google DeepMind](https://deepmind.google/models/gemini/pro/?utm_source=chatgpt.com "Gemini 2.5 Pro"), [Anthropic](https://docs.anthropic.com/en/docs/build-with-claude/context-windows?utm_source=chatgpt.com "Context windows"))
    
- **Common defaults**: A lot of day‑to‑day assistants still run at **128k** (e.g., GPT‑4o and 4o‑mini), while some OpenAI releases (e.g., GPT‑4.1) advertise strong performance even up to 1M tokens—availability may depend on product tier/rollout. ([OpenAI](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/?utm_source=chatgpt.com "GPT-4o mini: advancing cost-efficient intelligence"))
    

**2) Systems plumbing that makes long windows feasible**

- **Paged KV caches** (vLLM’s _PagedAttention_): stores attention keys/values in fixed‑size blocks so the server can “page” memory like an OS → much higher throughput with long sequences and multi‑user batching. ([arXiv](https://arxiv.org/abs/2309.06180?utm_source=chatgpt.com "Efficient Memory Management for Large Language Model Serving with PagedAttention"), [VLLM Documentation](https://docs.vllm.ai/en/latest/design/paged_attention.html?utm_source=chatgpt.com "Paged Attention - vLLM"), [Red Hat](https://www.redhat.com/en/blog/meet-vllm-faster-more-efficient-llm-inference-and-serving?utm_source=chatgpt.com "Meet vLLM: For faster, more efficient LLM inference and ..."))
    
- **Fast attention kernels** (_FlashAttention‑2_): IO‑aware tiling keeps intermediate tensors in fast memory, cutting memory from quadratic to effectively linear in sequence length and making long contexts train/infer faster. ([Stanford CRFM](https://crfm.stanford.edu/2023/07/17/flash2.html?utm_source=chatgpt.com "FlashAttention-2: Faster Attention with Better Parallelism ..."))
    

**3) Streaming / “infinite” style attention (when history keeps growing)**

- **StreamingLLM** uses “attention sinks” so models trained on short windows can _generalize_ to very long streams without fine‑tuning, keeping a rolling working set. ([arXiv](https://arxiv.org/abs/2309.17453?utm_source=chatgpt.com "Efficient Streaming Language Models with Attention Sinks"), [OpenReview](https://openreview.net/forum?id=NG7sS51zVF&utm_source=chatgpt.com "Efficient Streaming Language Models with Attention Sinks"))
    
- **Ring Attention** distributes blocks of very long sequences across devices with overlapping compute/communication, enabling near‑infinite contexts at training/inference time. ([ICLR Proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/file/1119587863e78451f080da2a768c4935-Paper-Conference.pdf?utm_source=chatgpt.com "RingAttention with Blockwise Transformers for Near-Infinite ..."))  
    _(These aren’t magic—you trade exact global attention for engineering that keeps the _useful_ bits hot.)_
    

**4) Budget‑aware prompt assembly (what most apps rely on daily)**

- Retrieve candidates with vector search, _re‑rank_ for intent match, then _compress/summarize_ to fit the window. Methods like **LLMLingua/LongLLMLingua** can preserve salient tokens while cutting 4–20×. ([Cohere Documentation](https://docs.cohere.com/docs/rerank?utm_source=chatgpt.com "Cohere's Rerank Model (Details and Application)"), [arXiv](https://arxiv.org/abs/2310.05736?utm_source=chatgpt.com "LLMLingua: Compressing Prompts for Accelerated Inference of Large Language Models"), [Microsoft](https://www.microsoft.com/en-us/research/blog/llmlingua-innovating-llm-efficiency-with-prompt-compression/?utm_source=chatgpt.com "Innovating LLM efficiency with prompt compression"))
    
- A simple budgeting rule of thumb: choose $k=\left\lfloor \dfrac{B-H}{s} \right\rfloor$, where $B$ is available tokens (model max minus safety margin), $H$ is header/system/history tokens, and $s$ is average tokens per chunk.
    

**Reality check**

- Long context ≠ guaranteed fidelity. The _“lost in the middle”_ effect is real—models often favor the beginning/end of long inputs, so strategic ordering, re‑ranking, and compression matter. ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    

---

### Semantic Chunking

**Idea**: Instead of splitting text every N tokens, _split on meaning_ and keep semantically coherent spans together so retrieval returns self‑contained, on‑topic chunks.

**How it’s implemented today**

- **Semantic splitters** group sentences by embedding similarity, adapt chunk boundaries, and optionally add small overlaps to preserve coreference. (LangChain _SemanticChunker_, LlamaIndex _Semantic Chunker_.) ([LangChain](https://python.langchain.com/docs/how_to/semantic-chunker/?utm_source=chatgpt.com "How to split text based on semantic similarity"), [LlamaIndex](https://docs.llamaindex.ai/en/stable/examples/node_parsers/semantic_chunking/?utm_source=chatgpt.com "Semantic Chunker"))
    
- **Re‑ranking** (cross‑encoder rerankers like Cohere Rerank 3/3.5; BAAI BGE; Jina rerankers) score query–passage pairs to keep only high‑value chunks. ([Cohere Documentation](https://docs.cohere.com/docs/rerank?utm_source=chatgpt.com "Cohere's Rerank Model (Details and Application)"), [Pinecone Docs](https://docs.pinecone.io/models/cohere-rerank-3.5?utm_source=chatgpt.com "cohere-rerank-3.5"), [Hugging Face](https://huggingface.co/BAAI/bge-reranker-v2-m3?utm_source=chatgpt.com "BAAI/bge-reranker-v2-m3"))
    
- **Contextual compression** runs a “compressor” over preliminary results to drop the off‑topic parts before they ever hit the prompt. (LangChain _ContextualCompressionRetriever_.) ([LangChain](https://python.langchain.com/docs/how_to/contextual_compression/?utm_source=chatgpt.com "How to do retrieval with contextual compression"))
    
- **GraphRAG** builds a knowledge graph + hierarchy from your corpus, then retrieves communities/summaries instead of raw spans—useful for broad or cross‑document questions. ([Microsoft](https://www.microsoft.com/en-us/research/project/graphrag/?utm_source=chatgpt.com "Project GraphRAG - Microsoft Research"))
    

**Why it matters**

- Better grounding → shorter prompts, fewer holes for hallucinations, and less sensitivity to chunk boundaries.
    
- Plays well with long contexts: you _still_ want the most relevant, compressed bits up front because of positional biases. ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    

---

### Cross‑Session Memory

**What “memory” means operationally**

- _Short‑term_: the live conversation and working set (history, tools results).
    
- _Long‑term_: facts about the user/project stored outside the model window, fetched when relevant (profiles, preferences, doc/code embeddings, prior decisions).
    

**Current implementations**

- **ChatGPT memory** (opt‑in, controllable): remembers user preferences and key facts _across chats_; you can view/delete memories; Team/Enterprise memory is excluded from training; recent updates expanded referencing to past chats with clear on/off controls. ([OpenAI](https://openai.com/index/memory-and-new-controls-for-chatgpt/ "Memory and new controls for ChatGPT | OpenAI"))
    
- **GitHub Copilot**:
    
    - Builds **repository indexes** to answer questions about your code; indexing runs in the background and stays up to date; _“will not use your indexed repository for model training.”_ ([GitHub Docs](https://docs.github.com/copilot/concepts/indexing-repositories-for-copilot-chat "Indexing repositories for Copilot Chat - GitHub Docs"))
        
    - In VS Code, Copilot uses **workspace indices**—remote (GitHub‑maintained) or local—to search quickly and select relevant snippets/symbols for chat. ([Visual Studio Code](https://code.visualstudio.com/docs/copilot/reference/workspace-context "Making chat an expert in your workspace"))
        
    - GitHub confirms Copilot Chat uses **embedding similarity** to find relevant code/doc snippets for answers. ([The GitHub Blog](https://github.blog/ai-and-ml/generative-ai/what-is-retrieval-augmented-generation-and-what-does-it-do-for-generative-ai/?utm_source=chatgpt.com "What is retrieval-augmented generation, and what does it do for ..."))
        
- **Agent frameworks** (open‑source):
    
    - **LangGraph** persists agent state (“threads”) so memory spans sessions; supports long‑term memory add‑ons. ([LangChain AI](https://langchain-ai.github.io/langgraph/concepts/persistence/?utm_source=chatgpt.com "LangGraph persistence - GitHub Pages"), [LangChain Blog](https://blog.langchain.dev/launching-long-term-memory-support-in-langgraph/?utm_source=chatgpt.com "Launching Long-Term Memory Support in LangGraph"))
        
    - **LlamaIndex** offers chat stores and summary buffers that _roll up_ history once token limits are hit, optionally flushing to long‑term memory (DB) for recall. ([LlamaIndex](https://docs.llamaindex.ai/en/stable/module_guides/storing/chat_stores/?utm_source=chatgpt.com "Chat Stores"))
        
    - Research systems like **MemGPT** implement OS‑style _virtual memory_ for LLMs, moving info between “fast” (prompt) and “slow” (persistent) tiers. ([arXiv](https://arxiv.org/abs/2310.08560?utm_source=chatgpt.com "MemGPT: Towards LLMs as Operating Systems"))
        

---

## Comparative snapshot (Aug 2025)

|Model / System|Max native window (tokens)|Notes|
|---|--:|---|
|Gemini 1.5/2.5 Pro|1,000,000|Multimodal, long‑context flagship. ([Google DeepMind](https://deepmind.google/models/gemini/pro/?utm_source=chatgpt.com "Gemini 2.5 Pro"))|
|Claude Sonnet 4|1,000,000|Rolling out (beta/tiers). ([Anthropic](https://docs.anthropic.com/en/docs/build-with-claude/context-windows?utm_source=chatgpt.com "Context windows"))|
|GPT‑4o / 4o‑mini|128,000|Common default in apps today. ([OpenAI](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/?utm_source=chatgpt.com "GPT-4o mini: advancing cost-efficient intelligence"))|
|GPT‑4.1 (select access)|up to 1,000,000 (reported perf)|“Maintains strong performance even up to 1M” per OpenAI; availability varies. ([OpenAI](https://openai.com/index/gpt-4-1/?utm_source=chatgpt.com "Introducing GPT-4.1 in the API"))|

_(Regardless of window size, most production stacks still retrieve, rerank, and compress before prompting.)_

---

## How these pieces fit together (an implementation mental model)

**At request time**

1. **Detect task type & budget** (latency/cost limits, model choice).
    
2. **Assemble candidates**
    
    - Vector search over _project memory_ (docs/code) and _user memory_ (preferences).
        
    - Diversify with MMR to avoid redundancy. ([LangChain](https://python.langchain.com/docs/how_to/example_selectors_mmr/?utm_source=chatgpt.com "How to select examples by maximal marginal relevance ..."))
        
3. **Re‑rank** with a cross‑encoder reranker (e.g., Cohere Rerank or BGE). ([Cohere Documentation](https://docs.cohere.com/docs/rerank?utm_source=chatgpt.com "Cohere's Rerank Model (Details and Application)"), [Hugging Face](https://huggingface.co/BAAI/bge-reranker-v2-m3?utm_source=chatgpt.com "BAAI/bge-reranker-v2-m3"))
    
4. **Compress** with contextual compression or prompt‑compression (LLMLingua/LongLLMLingua). ([LangChain](https://python.langchain.com/docs/how_to/contextual_compression/?utm_source=chatgpt.com "How to do retrieval with contextual compression"), [arXiv](https://arxiv.org/abs/2310.05736?utm_source=chatgpt.com "LLMLingua: Compressing Prompts for Accelerated Inference of Large Language Models"))
    
5. **Budget the prompt** using a token calculator, then place the most critical snippets early to mitigate “lost in the middle.” ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    
6. **Infer** on a model whose window matches the assembled prompt; servers use **PagedAttention** + **FlashAttention‑2**under the hood for throughput. ([arXiv](https://arxiv.org/abs/2309.06180?utm_source=chatgpt.com "Efficient Memory Management for Large Language Model Serving with PagedAttention"), [Stanford CRFM](https://crfm.stanford.edu/2023/07/17/flash2.html?utm_source=chatgpt.com "FlashAttention-2: Faster Attention with Better Parallelism ..."))
    

**Across sessions**

- Persist _facts_ (profile/preferences) and _artifacts_ (intermediate summaries, decisions) to a store keyed by user/project; automatically retrieve when the query pattern matches. ChatGPT and Copilot do this at product level; LangGraph/LlamaIndex give you OSS primitives. ([OpenAI](https://openai.com/index/memory-and-new-controls-for-chatgpt/ "Memory and new controls for ChatGPT | OpenAI"), [GitHub Docs](https://docs.github.com/copilot/concepts/indexing-repositories-for-copilot-chat "Indexing repositories for Copilot Chat - GitHub Docs"), [LangChain AI](https://langchain-ai.github.io/langgraph/concepts/persistence/?utm_source=chatgpt.com "LangGraph persistence - GitHub Pages"), [LlamaIndex](https://docs.llamaindex.ai/en/stable/module_guides/storing/chat_stores/?utm_source=chatgpt.com "Chat Stores"))
    

---

## Design tips (what works in 2025)

- **Prefer quality over raw length.** Even with 1M windows, _relevance ordering_ and _compression_ often beat dumping everything in. (Lost‑in‑the‑middle.) ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    
- **Front‑load evidence**: put citations/snippets the model must use near the top of the prompt. (Helps with positional bias.) ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    
- **Use rerankers** for final selection—cheap embeddings first, then cross‑encoders on the shortlist. ([Cohere Documentation](https://docs.cohere.com/docs/rerank?utm_source=chatgpt.com "Cohere's Rerank Model (Details and Application)"))
    
- **Cache & page**: on the serving layer, use engines with **PagedAttention** and modern attention kernels to keep latency predictable as history grows. ([arXiv](https://arxiv.org/abs/2309.06180?utm_source=chatgpt.com "Efficient Memory Management for Large Language Model Serving with PagedAttention"), [Stanford CRFM](https://crfm.stanford.edu/2023/07/17/flash2.html?utm_source=chatgpt.com "FlashAttention-2: Faster Attention with Better Parallelism ..."))
    
- **Memory governance**: make memory _visible and editable_ to users (like ChatGPT’s controls); avoid storing sensitive data unless explicitly asked; document retention. ([OpenAI](https://openai.com/index/memory-and-new-controls-for-chatgpt/ "Memory and new controls for ChatGPT | OpenAI"))
    

---

## Where the field is heading

- **Near‑infinite streaming** will become more practical (Ring/StreamingLLM‑style methods), but most product wins will still come from better _selection and compression_ rather than sheer window size. ([ICLR Proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/file/1119587863e78451f080da2a768c4935-Paper-Conference.pdf?utm_source=chatgpt.com "RingAttention with Blockwise Transformers for Near-Infinite ..."), [arXiv](https://arxiv.org/abs/2309.17453?utm_source=chatgpt.com "Efficient Streaming Language Models with Attention Sinks"))
    
- **RAG‑plus‑graphs** (GraphRAG) and **multimodal rerankers** (e.g., Jina for visually rich docs) are spreading beyond PoC into production stacks. ([Microsoft](https://www.microsoft.com/en-us/research/project/graphrag/?utm_source=chatgpt.com "Project GraphRAG - Microsoft Research"), [Jina AI](https://jina.ai/models/jina-reranker-m0/?utm_source=chatgpt.com "jina-reranker-m0 - Search Foundation Models"))
    

---

## Sources (selected)

- Long windows & model specs: Gemini 2.5 Pro (1M), Claude Sonnet 4 (1M beta), GPT‑4o (128k), GPT‑4.1 (notes on 1M). ([Google DeepMind](https://deepmind.google/models/gemini/pro/?utm_source=chatgpt.com "Gemini 2.5 Pro"), [Anthropic](https://docs.anthropic.com/en/docs/build-with-claude/context-windows?utm_source=chatgpt.com "Context windows"), [OpenAI](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/?utm_source=chatgpt.com "GPT-4o mini: advancing cost-efficient intelligence"))
    
- Systems plumbing: PagedAttention/vLLM; FlashAttention‑2. ([arXiv](https://arxiv.org/abs/2309.06180?utm_source=chatgpt.com "Efficient Memory Management for Large Language Model Serving with PagedAttention"), [VLLM Documentation](https://docs.vllm.ai/en/latest/design/paged_attention.html?utm_source=chatgpt.com "Paged Attention - vLLM"), [Stanford CRFM](https://crfm.stanford.edu/2023/07/17/flash2.html?utm_source=chatgpt.com "FlashAttention-2: Faster Attention with Better Parallelism ..."))
    
- Streaming/infinite attention: StreamingLLM; Ring Attention (ICLR 2024). ([arXiv](https://arxiv.org/abs/2309.17453?utm_source=chatgpt.com "Efficient Streaming Language Models with Attention Sinks"), [ICLR Proceedings](https://proceedings.iclr.cc/paper_files/paper/2024/file/1119587863e78451f080da2a768c4935-Paper-Conference.pdf?utm_source=chatgpt.com "RingAttention with Blockwise Transformers for Near-Infinite ..."))
    
- “Lost in the middle”: original paper (Stanford). ([arXiv](https://arxiv.org/abs/2307.03172?utm_source=chatgpt.com "Lost in the Middle: How Language Models Use Long Contexts"))
    
- Semantic chunking & compression: LangChain/LlamaIndex semantic splitters; ContextualCompression; GraphRAG; LLMLingua/LongLLMLingua. ([LangChain](https://python.langchain.com/docs/how_to/semantic-chunker/?utm_source=chatgpt.com "How to split text based on semantic similarity"), [LlamaIndex](https://docs.llamaindex.ai/en/stable/examples/node_parsers/semantic_chunking/?utm_source=chatgpt.com "Semantic Chunker"), [Microsoft](https://www.microsoft.com/en-us/research/project/graphrag/?utm_source=chatgpt.com "Project GraphRAG - Microsoft Research"), [arXiv](https://arxiv.org/abs/2310.05736?utm_source=chatgpt.com "LLMLingua: Compressing Prompts for Accelerated Inference of Large Language Models"))
    
- Cross‑session memory in products: ChatGPT memory controls; Copilot repository/workspace indexing & embedding search. ([OpenAI](https://openai.com/index/memory-and-new-controls-for-chatgpt/ "Memory and new controls for ChatGPT | OpenAI"), [GitHub Docs](https://docs.github.com/copilot/concepts/indexing-repositories-for-copilot-chat "Indexing repositories for Copilot Chat - GitHub Docs"), [Visual Studio Code](https://code.visualstudio.com/docs/copilot/reference/workspace-context "Making chat an expert in your workspace"), [The GitHub Blog](https://github.blog/ai-and-ml/generative-ai/what-is-retrieval-augmented-generation-and-what-does-it-do-for-generative-ai/?utm_source=chatgpt.com "What is retrieval-augmented generation, and what does it do for ..."))
    

---

### If you want, I can sketch a minimal reference pipeline (LangChain/LlamaIndex + reranker + LLMLingua) and a prompt‑budgeting function you can drop into your agent.