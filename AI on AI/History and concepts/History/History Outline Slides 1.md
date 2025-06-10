# AI’s 50-Year Whiplash (TL;DR)

- From logic provers to AlphaGo: each era scored an “impossible” win, then hit a wall 
    
- Symbolic, expert-rule, and search-heavy phases all stalled on scale/data
    
- Every “AlphaGo moment” reset expectations—then winter followed
    
- Today’s bet: fuse deep learning with search to finally escape the cycle 
    

---

##### Notes

- Pattern: breakthrough → hype → limits exposed → funding crash → new paradigm.
    
- Useful framing for audience before diving into periods.
    

---

# Logic & Theorem Proving (1950s – 1970s)

- 1956 **Logic Theorist** solved 38/52 _Principia_ proofs—shorter than humans 
- 1965 **Resolution** became the Swiss-army knife for chip-verification proof 
- _Hook_: RAND memos dubbed it “a mathematician in a shoebox”
- Reality check: outside toy theorems, search blew up exponentially
---
##### Notes
- Logic Theorist: Newell, Shaw & Simon; first FOL reasoning demo.
- Resolution still underpins SAT/SMT solvers, but needs heavy hand-holding.
---
# Lisp & Symbolic Manipulation (1958+)
- **Lisp** introduced lists, recursion, GC—the AI lingua franca 
- Demos like SHRDLU & MACSYMA felt magical to 1970s audiences
- Lisp machines sold as “workstations of the mind”
- 1987 crash: pricey slow hardware → AI winter, C-based rigs won 
- Lesson: expressive code ≠ scalable performance
---
##### Notes
- Lisp’s meta-circular hacker culture vs. real-time needs of industry.
- Good segue into rule-based boom that followed.
---
# Expert-System Era (1965 – late 1980s)
- **DENDRAL** beat chemists at molecule ID 
- **MYCIN** diagnosed infections at 65–70 % vs juniors’ 42 % 
- **XCON** saved DEC ≈ $40 M/yr configuring VAXes 
- Media hailed “electronic wizards,” VC money poured in
- Bust: rule bases ballooned >10 k; “knowledge bottleneck” killed ROI
---
##### Notes
- Liability fears kept MYCIN in the lab despite accuracy.
- Maintenance costs rose super-linearly as product lines changed.
---

# Game-Playing Machines (1959 – 2017)

- 1959 **Samuel’s Checkers** learned via self-play, beat state champ 
    
- 1997 **Deep Blue** (480 CPUs) toppled Kasparov—global TV event 
    
- 2016 **AlphaGo** stunned Go world with Move 37, 4-1 over Sedol 
    
- 2017 **AlphaZero** mastered three games from scratch
    
- _Hook_: after each win pundits shouted “AGI next!”—then silence
    

---

##### Notes

- Emphasize specialized compute: ASICs, TPUs, massive datasets.
    
- Each system unbeatable at one game, clueless outside it.
    

---

# Lessons on Scale & Accuracy

- Symbolic logic elegant but NP-hard; world is noisy 
    
- Expert rules shine narrow, shatter wide
    
- Search + compute can crush humans yet stay point solutions
    
- Deep learning adds generalization, but data/energy hungry
    
- Future likely in hybrid systems that marry symbols, search & self-learners
    

---

##### Notes

- Invite audience to watch for next paradigm shift—multi-modal, agentic hybrids.

---
https://chatgpt.com/share/68478430-4710-8002-8dd5-e296e5a4b0e5

# Interactive & SMT Provers (1980s → today)

- **Coq** (1984) & **Isabelle/HOL** (1986) debut _interactive_ assistants—users script tactics, kernel checks
    
- 1990s **PVS**, **Otter → Vampire/Prover9** certify avionics & chips, keeping first-order logic alive 
    
- 2000s **Z3** & **CVC** ignite the **SMT** era—DPLL(T) slashes combinatorial blow-ups
    
- 2010s **Lean** crowdsources math; the once-800-page Feit–Thompson proof now lives as machine-checked lemmas
    
- _Hook_: Microsoft won’t ship a Hyper-V kernel patch until Z3 signs off on every invariant
    

---

##### Notes

- **Interactive vs. automatic** Early assistants separate “strategy” (human) from “tactics” (machine), boosting trust.
    
- **Industrial uptake** PVS verified NASA fault-tolerance; SMT now sits in compilers (Rust, Boogie) and formal CI pipelines.
    
- **Lean popularity** Git-based mathlib shows open-source culture invading formal methods.
    
- **Key takeaway** Provers evolved from academic curiosities to invisible gatekeepers in safety-critical software.

