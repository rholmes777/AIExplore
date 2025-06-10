# A Half-Century of AI: Triumphs and Reality Checks
### From Dazzling "AlphaGo Moments" to Painful Scaling Walls
- **1950s-70s**: Logic theorems proved... but couldn't scale
- **1965-80s**: Expert systems beat doctors... then died of rule bloat  
- **1958-87**: Lisp unleashed expressive power... but not speed
- **1959-2017**: Game machines kept resetting the bar... while staying narrow

---
##### Notes
- AI history shows recurring pattern: breakthrough → excitement → scaling failure → new approach
- Each era had its "AlphaGo moment" - a stunning achievement that captured public imagination
- But each also hit fundamental limitations that required paradigm shifts
- Modern AI (deep learning + search) may finally be breaking this cycle
---

# Logic & Theorem Proving: The Dream of Automated Reasoning
### 1956: Logic Theorist Proves Math Theorems
- Newell, Shaw & Simon create first symbolic reasoning program
- **Triumph**: Proved 38/52 theorems from *Principia Mathematica*
- **Plot Twist**: Found shorter proof for theorem #2.85 than Russell & Whitehead!
- **Reality Check**: Search exploded combinatorially outside toy problems

---
##### Notes
- Logic Theorist was the first program to perform a task thought to require human intelligence
- Used heuristic search to navigate proof space
- Resolution theorem provers (Robinson 1965) later automated hardware verification
- Proofs became unintelligible to humans; real-world domains needed heavy human guidance
- Key lesson: Formal logic elegant but NP-hard; reality is uncertain and context-heavy
---

# McCarthy's Revolution: AI Gets Its Own Language
### 1958: Lisp Changes Everything
- First language built specifically for AI research
- **Powers**: Lists, recursion, garbage collection, symbolic manipulation
- **Legacy**: Enabled SHRDLU, MACSYMA, and decades of AI research
- **The Crash**: Lisp machines die in 1987, triggering AI winter

---
##### Notes
- John McCarthy coined "Artificial Intelligence" and created Lisp at MIT
- Lisp pioneered features now standard: dynamic typing, tree data structures, automatic memory management
- McCarthy's "Advice Taker" and Situation Calculus set agenda for knowledge representation
- Performance gap with C/Fortran became insurmountable as hardware evolved
- Formal models struggled with noisy, probabilistic reality
---

# The Expert System Gold Rush
### 1965-1980s: AI Enters the Real World
- **DENDRAL (1965)**: Matches expert chemists at molecular analysis
- **MYCIN (1972)**: 70% diagnostic accuracy vs 42% for junior doctors
- **XCON/R1 (1978)**: Saves DEC $40M/year configuring VAX systems
- **The Collapse**: 10,000+ rules = maintenance nightmare

---
##### Notes
- DENDRAL analyzed mass spectrometry data to suggest molecular structures
- MYCIN never deployed due to liability concerns and lack of common-sense reasoning
- XCON configured 95-98% of VAX orders correctly by 1986
- Knowledge acquisition bottleneck: extracting rules from experts was slow and expensive
- Rule bases became brittle when facts changed; couldn't transfer knowledge between domains
- Failure pattern: High accuracy in narrow domains, but crumble when rules collide or world changes
---

# Game Machines: Beating Humans One Board at a Time
### 1959: Samuel's Checkers Player Introduces Machine Learning
- Self-play training decades before "deep RL" was coined
- Beats Connecticut state champion using minimax search
- Introduced temporal difference learning concepts
- Limited by handcrafted features and checkers' small state space

---
##### Notes
- Arthur Samuel at IBM created one of the first self-learning programs
- Used alpha-beta pruning to search game tree efficiently
- Pioneered ideas later formalized in reinforcement learning
- Checkers has ~10^20 positions vs chess ~10^47 and Go ~10^170
- Success in checkers didn't translate to more complex games
---

# Deep Blue: The Brute Force Triumph
### 1997: Machine Defeats World Chess Champion
- IBM's 480-processor supercomputer evaluates 200M positions/second
- Defeats Garry Kasparov 3½–2½ in historic match
- **Secret Sauce**: Brute force + grandmaster heuristics + massive opening book
- **The Catch**: Purpose-built ASICs, zero generalization beyond chess

---
##### Notes
- First time a computer defeated a reigning world champion under tournament conditions
- Used specialized chess chips designed by Feng-hsiung Hsu
- Evaluated positions 8-12 moves deep (up to 40 in forcing lines)
- Kasparov accused IBM of cheating after mysterious move in Game 2
- System dismantled after victory; knowledge couldn't transfer to other domains
- Showed that sufficient compute + domain expertise could overcome human intuition
---

# AlphaGo: When AI Made Professionals Gasp
### 2016: The Move That Stunned the Go World
- DeepMind's neural nets + Monte Carlo Tree Search beat Lee Sedol 4-1
- **Move 37**: So alien that commentators thought it was a mistake
- Trained on millions of positions + thousands of TPU hours
- **Plot Twist**: Post-match analysis found self-atari bugs

---
##### Notes
- Go was considered AI-hard due to massive branching factor (~250 vs chess ~35)
- Move 37 in Game 2 had 1-in-10,000 probability according to human pros
- Combined deep learning (value/policy networks) with traditional tree search
- Required 1,920 CPUs and 280 GPUs for match play
- AlphaGo Zero (2017) reached superhuman level through pure self-play
- Still brittle in edge cases; adversarial positions could cause basic mistakes
---

# AlphaZero: One Algorithm to Rule Them All
### 2017: Tabula Rasa Learning Conquers Three Games
- Same architecture masters chess, shogi, and Go via self-play
- No human games, no opening books, no domain-specific tweaks
- Chess: Defeats Stockfish 28-0 (72 draws) after 4 hours training
- **Reality Check**: Requires extreme compute; only works in perfect-info games

---
##### Notes
- Learned chess from scratch in 9 hours, reaching superhuman level
- Discovered novel strategies: piece mobility over material in chess
- Used 5,000 TPUs (Tensor Processing Units, specially created by Google) for self-play, 64 TPUs for training
- Each game required ~300k self-play games at 800 simulations per move
- Still can't handle imperfect information (poker), continuous action spaces, or real-world messiness
- Showed that general learning algorithms could match specialized systems
---

# The Pattern: Every Breakthrough Hits a Wall
### What Half a Century Taught Us
- **Symbolic Logic**: Elegant proofs, but reality is messy and uncertain
- **Expert Systems**: High accuracy in silos, but knowledge doesn't compose
- **Game Engines**: Superhuman at board games, useless at everything else
- **Modern Fusion**: Deep learning + search hints at breaking the cycle

---
##### Notes
- Each generation's breakthrough eventually met a scaling wall:
  - Computational (logic theorem provers)
  - Knowledge-engineering (expert systems)
  - Data-hungry (early neural networks)
- Specialized compute + search (Deep Blue) or learnable heuristics (AlphaGo) can beat humans
- But each victory is a point solution, not general intelligence
- Current trend: Combine statistical learning with symbolic reasoning
- Maybe this time we'll avoid the next AI winter?
---
# EXTRA INFO
---
# Why Expert Systems Shattered: The Technical Post-Mortem
### Prolog's Promise Meets Reality's Complexity
- **Prolog**: Logic as computation—facts + rules = automatic reasoning
- **The Catch**: No variables, just pattern matching; closed-world assumption
- **Rule Explosion**: XCON grew from 750 → 10,000+ rules in 9 years
- **Zero Learning**: Every exception hand-coded by knowledge engineers
- **Brittleness**: One new product feature could break 100+ rules

---
##### Notes
- Prolog fundamentally different from imperative languages:
  - Declarative: "what" not "how"
  - Unification and backtracking built-in
  - Example: `diagnosis(Patient, strep) :- blood_culture(Patient, gram_positive), chains(Patient, yes).`
- Closed-world assumption: If something isn't explicitly stated as true, it's assumed false
  - Real world: "Unknown" is often the right answer
  - Led to incorrect conclusions from missing data
- Rule interactions created nightmares:
  - Rule A triggers Rule B which contradicts Rule C
  - Priority systems and certainty factors were band-aids
- Knowledge engineers became bottlenecks:
  - Months extracting rules from domain experts
  - Experts couldn't articulate their intuition in IF-THEN format
  - "I just know it when I see it" doesn't translate to Prolog
- No learning meant no adaptation:
  - Couldn't improve from experience
  - Couldn't transfer knowledge between domains
  - Each new system built from scratch
---
https://claude.ai/share/d36d50f8-5fd1-49b2-80a8-0094b9055ca1
