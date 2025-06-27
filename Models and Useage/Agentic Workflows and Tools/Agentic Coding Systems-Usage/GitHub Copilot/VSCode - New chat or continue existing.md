**Short answer up‑front:**  
_Continue in the same chat while you’re still working on the _same_ tightly‑scoped objective and the thread is short; open a **fresh chat** whenever the objective changes, the thread grows large (≈ 50 %–70 % of the model’s token window), or you notice “context drift.”_ Doing so keeps the model focused, avoids hitting hard token limits, and prevents the subtle degradation in answer quality that emerges in long multi‑turn conversations.

---

## Understanding the Context Window

Large‑language models don’t have true long‑term memory; every request must fit—prompt + chat history + tool calls—inside a **context window**. Modern coding models are generous (≈ 200 k tokens for OpenAI o3/o4‑mini and Claude 4 Sonnet/Opus), yet practical capacity is lower because IDE scaffolding, system prompts, and your code snippets all consume tokens. Community reports show truncation or failure when real payloads reach even ~80 k tokens despite the theoretical 200 k limit. Once older messages are trimmed, the model “forgets” them, so decisions made early in a marathon chat may silently disappear.

---

## Advantages of **Staying** in the Same Chat

|Benefit|Why it helps|Sources|
|---|---|---|
|**Continuity of reasoning**|The model can refer back to decisions, examples, or code you already pasted without you re‑typing them.|Anthropic notes that Claude “only retains context within a single conversation” and you can reference earlier info without repeating it.|
|**Lower prompting overhead**|You don’t need to re‑attach large specs or code blocks for every follow‑up, saving both tokens and time.|OpenAI prompt‑engineering guide encourages building on earlier turns when they remain relevant.|
|**Faster momentum**|Copilot Agent already knows which files it touched, which tests failed, etc.; it can continue iterating immediately.|GitHub Copilot agent best‑practice page: break tasks down but let the agent iterate until done.|

Use this when you are still on _one_ logical task—e.g., refactor A → small follow‑up fix → polish comments.

---

## Why Long Threads Go Off‑Track

|Risk|How it shows up|Evidence|
|---|---|---|
|**Context degradation/drift**|Answers start missing earlier constraints, hallucinate file names, or give generic advice.|“Context Degradation Syndrome” write‑up (Medium) describes coherence breakdown over long chats. Hacker News discussion echoes the same phenomenon.|
|**Token overflow & truncation**|Model silently forgets early messages or code; later steps contradict earlier choices.|Reddit threads on model change mid‑conversation explain full history is re‑sent each turn until trimmed.|
|**Cognitive overload**|Both user and AI lose the “north star” of the task as corrections and side threads accumulate.|GitHub community post on keeping game context from drifting; Dev.to article on “context drift” in AI pair programming.|

If you see these symptoms—especially after many back‑and‑forth fixes—stop, harvest the useful outcome (committed code, a design snippet, a one‑paragraph summary), and spawn a new chat.

---

## Practical Decision Matrix

|Ask yourself|If **Yes**|If **No**|
|---|---|---|
|**Is the next action still part of the same epic/bug?**|Stay|New chat|
|**Has the conversation exceeded ~50 %–70 % of window (≈ 100 k tokens for 200 k‑token models)?**|New chat|Stay|
|**Are answers drifting or contradicting earlier instructions?**|New chat|Stay|
|**Will I need different code areas, languages, or tools?**|New chat|Stay|
|**Did a long time (hours/days) pass since last turn?**|New chat (session context may have been forgotten, per Anthropic session limits)|Stay|

---

## How to “Reset Cleanly”

1. **Summarise before you switch** – Ask the model to produce a concise bullet recap of decisions and open items (_“Summarise key points from this thread in 10 bullets”_).  
    _This distilled summary is small, copy‑pasteable, and can seed the next chat._
    
2. **Pin durable guidance elsewhere** – Put project‑wide rules in `.github/copilot‑instructions.md`; they auto‑load in every new Copilot chat.
    
3. **Attach only what’s needed** – In the fresh thread, re‑attach the summary, relevant code, or prompt file template; avoid dumping the entire old conversation.
    
4. **Name your chats** (VS Code & GitHub let you rename threads) so teammates know which chat corresponds to which ticket.
    
5. **Archive the old chat** – keep it for audit/reference but don’t let it keep growing.
    

---

## Special Notes for GitHub Copilot Agent Mode

- **Agent plans & edits are _per chat_**; a new chat means a brand‑new scratchpad plan. That’s good when you want a clean sheet; bad if you break mid‑iteration.
    
- **Running commands/tests**: the GA version of Agent Mode still asks for approval before the first shell or test task in each chat; starting a new chat resets that approval flow.
    
- **Cost & latency**: each new chat requires re‑embedding any attached context. Avoid churn by batching logically related micro‑tasks in one session.
    
- **GitHub’s own suggestion:** “Break complex work into smaller tasks” and “start with a fresh chat if the topic changes” (Best Practices guide).
    

---

## Conclusion

Think of a chat thread as a scratchpad with finite pages. Keep writing on the same page while you’re still solving **one**problem and the page isn’t full; open a fresh page the moment the project or the conversation gets messy, bloated, or heads in a new direction. A quick summary‑and‑restart habit gives you the best of both worlds: continuity when you need it, clarity when you don’t.

---

### Key References

1. GitHub Docs – _Best practices for Copilot_
    
2. GitHub Docs – _Best practices for using Copilot agent_
    
3. Anthropic Help – _Usage‑limit best practices_
    
4. OpenAI API – _o3 model context window 200 k_
    
5. OpenAI API – _o3‑mini context window_
    
6. Community report on practical 80 k limit despite 200 k spec
    
7. Hacker News thread “Keeping your context clean matters”
    
8. GitHub discussion on models drifting in long chats
    
9. Medium article on Context Degradation Syndrome
    
10. Dev.to post on minimizing context drift for AI pair programmers