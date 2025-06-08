## TL;DR

A half-century of AI has swung between dazzling “AlphaGo moments” and painful reality checks.  
Symbolic logic proved theorems but stalled on real-world scale; expert systems beat doctors yet died of rule bloat; Lisp unleashed expressive power but not speed; game machines—from Samuel’s checkers to Deep Blue and AlphaGo—kept resetting the bar while reminding us how narrow “super-human” can be. 

---

## 1 Logic & Theorem Proving (1950 s – 1970 s)

|Milestone|Why it mattered|“AlphaGo”-like highlight|Scaling / accuracy failure|
|---|---|---|---|
|**Logic Theorist**(Newell, Shaw & Simon, 1956)|First program to do symbolic reasoning in first-order predicate calculus|Proved 38/52 theorems from _Principia Mathematica_—even finding a shorter proof for #2.85. ([en.wikipedia.org](https://en.wikipedia.org/wiki/Logic_Theorist?utm_source=chatgpt.com "Logic Theorist - Wikipedia"))|Could only handle tiny proofs; search exploded combinatorially outside toy problems.|
|**Resolution theorem provers** (Robinson 1965 → Prover9 et al.)|Unified proof strategy for FOL; backbone of hardware‐verification proofs|Automated pieces of the Four-Colour Theorem and later chip-verification proofs|Proofs unintelligible to humans; real-world domains still needed heavy guidance.|

---

## 2 McCarthy, Lisp & Symbolic Manipulation

|Milestone|Upside|Downside|
|---|---|---|
|**Lisp** (McCarthy 1958)|First language built _for_ AI—lists, recursion, garbage collection; powered projects from SHRDLU to MACSYMA. ([en.wikipedia.org](https://en.wikipedia.org/wiki/Lisp_%28programming_language%29?utm_source=chatgpt.com "Lisp (programming language) - Wikipedia"))|Slower than C/Fortran; Lisp-machine hardware crash (1987) helped trigger an AI winter.|
|**Advice Taker idea & Situation Calculus**|Set the agenda for knowledge representation and planning|Formal models struggled with noisy, probabilistic reality.|

---

## 3 Expert-System Era (1965 – late 1980 s)

|System|Domain success (“AlphaGo moment”)|What broke down|
|---|---|---|
|**DENDRAL**(1965)|Suggested molecular structures from mass spectra; matched expert chemists. ([en.wikipedia.org](https://en.wikipedia.org/wiki/Dendral?utm_source=chatgpt.com "Dendral - Wikipedia"))|Rules handcrafted for a narrow chemistry niche; couldn’t transfer knowledge.|
|**MYCIN**(1972)|65–70 % diagnostic accuracy vs ~42 % for junior physicians. ([en.wikipedia.org](https://en.wikipedia.org/wiki/Mycin?utm_source=chatgpt.com "Mycin - Wikipedia"))|Never deployed—liability worries, no common-sense reasoning, hard to explain certainty factors.|
|**XCON/R1**(DEC 1978)|Configured VAX systems; saved ≈ $40 M / yr—a commercial triumph. ([ojs.aaai.org](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/download/460/396?utm_source=chatgpt.com "[PDF] AI Technology Transfer at Digital Equipment Corporation"))|Rule base ballooned (>10 000 rules); maintenance costs rose as product line changed.|

**Failure pattern:** brittle if facts change; “knowledge acquisition bottleneck” slowed new systems.

---

## 4 Game-Playing Machines

|Era|System & Tech|Highlight|Limitation|
|---|---|---|---|
|1959|**Samuel’s Checkers Player**—minimax, α-β pruning, self-play learning|Beat Connecticut state champion; introduced TD learning decades before deep RL. ([ibm.com](https://www.ibm.com/history/early-games?utm_source=chatgpt.com "The games that helped AI evolve - IBM"))|Needed handcrafted features; checkers’ small state space hides scaling issues.|
|1997|**IBM Deep Blue**—brute-force + expert heuristics on 480-way parallel HW|First machine to defeat reigning world chess champ Garry Kasparov 3½ – 2½. ([en.wikipedia.org](https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov?utm_source=chatgpt.com "Deep Blue versus Garry Kasparov - Wikipedia"), [wired.com](https://www.wired.com/2011/05/0511ibm-deep-blue-beats-chess-champ-kasparov?utm_source=chatgpt.com "May 11, 1997: Machine Bests Man in Tournament-Level Chess Match"))|Purpose-built ASICs & massive opening book; no generalization beyond chess.|
|2016|**Alphabet/DeepMind AlphaGo**—deep neural nets + Monte Carlo Tree Search|Beat Go legend Lee Sedol 4 – 1; Move 37 stunned pros. ([en.wikipedia.org](https://en.wikipedia.org/wiki/AlphaGo_versus_Lee_Sedol?utm_source=chatgpt.com "AlphaGo versus Lee Sedol - Wikipedia"), [wired.com](https://www.wired.com/2016/03/two-moves-alphago-lee-sedol-redefined-future?utm_source=chatgpt.com "In Two Moves, AlphaGo and Lee Sedol Redefined the Future"))|Trained on millions of positions & TPUs; still brittle in edge cases (e.g., self-atari bugs found post-2016).|
|2017|**AlphaZero**—tabula rasa RL conquered chess, shogi, Go|Same architecture mastered three games via self-play|Requires extreme compute; still operates only in perfect-information games.|

---

## 5 What We Learned about Accuracy & Scale

- **Symbolic logic**: Elegant but NP-hard; reality is uncertain, continuous, and context-heavy.
    
- **Expert systems**: High accuracy in _narrow_ domains; crumble when rules collide or world changes.
    
- **Lisp & symbolic manipulation**: Unlocked rapid prototyping but couldn’t match the speed/scale of later statistical methods.
    
- **Game engines**: Repeatedly show that specialized compute + search (Deep Blue) or learnable heuristics (AlphaGo) can smash human ceilings—yet each victory is a point solution, not general intelligence.
    

> **Big picture:** Every generation’s breakthrough eventually met a scaling wall—computational, knowledge-engineering, or data-hungry. The modern trend couples learning (deep nets, RL) with search, hinting that fusing statistical and symbolic approaches may finally break the cycle.