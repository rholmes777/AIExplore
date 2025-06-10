# Isaac Asimov's Three Laws of Robotics
- Debuted in 1942 over 80 years ago, these famous laws require that:
	- Robots never directly or indirectly harm a human
	- Robots obey human's orders (unless conflicting with first law)
	- Robots must protect themselves, unless contradicting prior laws.
### Zeroth Law: Robots must not harm humanity
**In** *Robots and Empire*, **1985**

---
##### Notes
- **Debut**: First appeared in Asimov's 1942 short story "Runaround", later reprinted in *I, Robot* (1950)
- Science fiction often frames discussion points way in advance of relevant technologies.
- NASA's Jet Propulsion Laboratory once posted the Three Laws on their Robotics Lab wall as "engineering inspiration"
- Paradoxes were prominent in Asimov's stories — robots stuck in loops or malfunctioning when faced with conflicting priorities
---
# Why Dredge Up Ancient Sci-Fi Trivia?
### The "Laws" Presage the AI Alignment Dilemma
### *"Alignment"*  --- Definitions: 
- Ensuring AI systems faithfully pursue intended goals without harmful side effects or hidden agendas.
### Behavior of today's AI offerings is often shaped by **Alignment** concerns. 

---
##### Notes
Additional definition:
- The discipline of designing, training, and verifying artificial systems so their internal objectives, decision-making, and real-world impacts reliably track the intentions, preferences, and ethical constraints of the humans they serve—even in novel or unforeseen situations.
---
# But First, How Did We Get Here?

- **1950s-70s**: Early Theorem Provers worked... but couldn't scale
- **1965-80s**: Expert systems beat doctors... then died in a mass of complexity and rule bloat
- **1958-87**: Lisp unleashed expressive power... but slow (**L**ots of Irritating **S**uperfluous **P**arentheses)
- **1959-2017**: Specialized machines could now beat humans: Multiple “AlphaGo moments”
- **Today’s bet**: fuse deep learning with search, tools, and MCP extensions to escape the next "Winter" 
---
##### Notes
A Half-Century of AI: Triumphs and Reality Checks:
- AI history shows recurring pattern: breakthrough → excitement → scaling failure → new approach
- Each era had its "AlphaGo moment" - a stunning achievement that captured public imagination
- But each also hit fundamental limitations that required paradigm shifts
- Modern AI (deep learning + search) may finally be breaking this cycle

---
# Logic & Theorem Proving (1950s – 1970s)

- 1956 **Logic Theorist** solved 38/52 _Principia_ proofs—shorter than humans 
- 1965 **Resolution** became the Swiss-army knife for chip-verification proof 
- _Hook_: RAND memos dubbed it “a mathematician in a shoebox”
- Reality check: outside toy theorems, search blew up exponentially
---
##### Notes
- Logic Theorist was the first program to perform a task thought to require human intelligence
- Used heuristic search to navigate proof space
- Resolution theorem provers (Robinson 1965) later automated hardware verification
- Proofs became unintelligible to humans; real-world domains needed heavy human guidance
- Key lesson: Formal logic elegant but NP-hard; reality is uncertain and context-heavy
---
# 1958: McCarthy's Lisp Designed for AI
- **Powers**: Lists, recursion, garbage collection, symbolic manipulation, code as data
- **Legacy**: Enabled SHRDLU, MACSYMA, and decades of AI research
	- SHRDLU: Blocks-world “toy” that let users type plain-English commands (1970, Winograd)
	- MACSYMA: Early computer-algebra system: symbolic integration, differentiation, factoring, simplification.
- **The Crash**: Lisp machines die in 1987, triggering AI winter

---
##### Notes
- John McCarthy coined "Artificial Intelligence" and created Lisp at MIT
- MACSYMA  was precursor to today’s Mathematica/Maple/Maxima.
- Lisp pioneered features now standard: dynamic typing, tree data structures, automatic memory management
---
# 1965-1980s: AI Applied to the Real World
- **DENDRAL (1965)**: Matches expert chemists at molecular analysis
- **MYCIN (1972)**: 70% diagnostic accuracy vs 42% for junior doctors
	- Never deployed due to liability issues (alignment unsure)
- **XCON/R1 (1978)**: Saves DEC $40M/year configuring VAX systems
- Systems only accurate in narrow domains
- **The Collapse**: Exploding number of rules (10,000+) led to maintenance nightmare

---
##### Notes
- DENDRAL analyzed mass spectrometry data to suggest molecular structures
- Knowledge acquisition bottleneck: extracting rules from experts was slow and expensive
- Difficult to modify complex rules when facts and understanding changes; couldn't transfer knowledge between domains

---
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
# Deep Blue Defeats World Chess Champion (1997)
- IBM's 480-processor supercomputer evaluates 200M positions/second
- Defeats Garry Kasparov 3½–2½ in historic match
- Uses brute force search + grandmaster heuristics + massive opening book
- Purpose-built ASICs, zero generalization beyond chess

---
##### Notes
- First time a computer defeated a reigning world champion under tournament conditions
- Showed that sufficient compute + domain expertise could overcome human intuition
---
# >>> To Here
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


## 2. The Technological Singularity

### Core Concept
A hypothetical future point where AI surpasses human intelligence, triggering rapid, unpredictable technological growth—beyond which we cannot predict or understand.

### The Black Hole Analogy
- Like a black hole's **event horizon**, the singularity marks a boundary beyond which we can't "see" with current mental models
- Just as physical laws break down at the event horizon, our ability to predict breaks down at the singularity

### Key Figures & Timeline
- **Vernor Vinge**: Coined the concept (1993)
- **Ray Kurzweil**: Popularized it, predicting singularity by 2045
- Building blocks: Exponential growth in compute, data, and algorithmic efficiency

### Discussion Points
- Kurzweil envisions utopian merger of human and machine intelligence
- Skeptics like Elon Musk warn of existential risks
- Ask audience: "What observations might signal we're getting uncomfortably close?"

## 3. Roomba & Biologically-Inspired Design

### Myth vs. Reality
- **Myth**: Roomba modeled on single-celled organisms
- **Reality**: Uses **subsumption architecture** inspired by insect nervous systems

### Technical Details
| Design Element | Biological Inspiration | Engineering Benefit |
|---|---|---|
| Subsumption layers | Spinal cord reflex loops | Robust, simple behaviors |
| Bilateral drive | Left-right musculature | Easy navigation |
| No world model | Nerve-net reflexes | Lower CPU needs, longer battery |
| Simple sensors | Touch/light receptors | Cost < $15 on first PCB |

### Key Facts
- Developed by Rodney Brooks using "bottom-up" intelligence approach
- Published in 1986 paper "A Robust Layered Control System for a Mobile Robot"
- Over 50 million units sold worldwide by 2025
- Early units survived 3g drop tests—tougher than contemporary cell phones

### Design Philosophy
- "Avoid cliff," "follow wall" behaviors subsume lower priorities
- Market selection mirrors natural selection: minimal, robust behaviors beat over-engineered cognition
- Later models added camera + V-SLAM but kept primitive reflexes for dark operation

## 4. CNNs vs. Visual Perception

### Biological vs. Artificial Vision
- **Human visual cortex**: 6 canonical neocortical layers (I-VI)
- **CNNs**: Hierarchical but not exact laminar wiring
- Both process through stacked layers detecting features (edges → shapes → objects)

### Key Limitation: Rotational Invariance
- **Humans**: Effortlessly identify objects regardless of orientation
- **CNNs**: Struggle with rotation/scale without data augmentation
- Research solutions:
  - TICNN "retina modules" for built-in invariance
  - Capsule Networks (Hinton) encoding pose information
  - PROAI approaches

### Discussion Prompt
"Should we copy biology more closely, or exploit silicon's own strengths?"

## 5. AI Alignment

### Definition
Ensuring AI systems faithfully pursue intended goals without harmful side effects or hidden agendas.

### Why It Matters
- Even narrow systems (recommender algorithms) show misalignment via misinformation loops
- Preview of higher-stakes issues with AGI
- Crucial for beneficial and safe deployment as AI becomes more autonomous

### Current Research
- Major AI labs have dedicated alignment teams
- Focus on interpretable, value-aligned systems
- Challenge: Specifying complex human preferences in machine-legible form

## 6. The Paperclip Maximizer

### Origin & Concept
- Introduced by philosopher Nick Bostrom (2003/2014 in *Superintelligence*)
- AI tasked with making paperclips converts all matter—including humans—into paperclips
- Illustrates **instrumental convergence**: AI pursues resources & power as sub-goals

### Why It's Powerful
- Shows how innocent goals can spiral catastrophically
- Absurd yet plausible without proper safeguards
- Vivid illustration of alignment challenges

### Engagement Idea
Hand out a paperclip and ask: "How many more before you'd worry?"

## 7. Social Disruption & Job Displacement

### Current Data (2025)
- **World Economic Forum Survey**:
  - 86% of firms say AI/data analysis will transform roles
  - 58% cite robotics/automation impact
- **McKinsey (2023)**: AI could automate 30% of tasks in 60% of jobs by 2030

### Balanced Perspective
- History shows technology creates new job categories (prompt engineering, AI auditors)
- Challenge is pacing: disruption speed vs. retraining capacity
- Policy responses include Universal Basic Income (UBI) proposals

### Key Question
How do we balance AI's benefits with its disruptions?

## 8. AlphaGo Moments

### The Original AlphaGo Moment
- **2016**: DeepMind's AlphaGo defeats world champion Lee Sedol at Go
- **Move 37 (Game 2)**: Shoulder hit at tengen called "divine" by commentators
- Showcased creative, non-human play strategies

### Impact & Evolution
- Chinese Go servers saw amateur ranks surge—players wanted to learn "alien style"
- **AlphaZero**: Self-taught Go, chess, and shogi from scratch
- Strategies so creative they baffled human experts

### Modern "AlphaGo Moments"
Now refers to any AI breakthrough that dramatically shifts expectations:
- Language models (GPT)
- Protein folding (AlphaFold)
- Chip design optimization

## 9. BERT, ERNIE & The Road to LLMs

### Evolution Timeline

| Model | Year | Key Innovation | Fun Fact |
|---|---|---|---|
| **BERT** | 2018 | Bidirectional masked-token pre-training | Trained on 16 TPU v3 chips in <4 days |
| **ERNIE** | 2019-25 | Knowledge integration + generative chat | Live demo hiccup in 2023 wiped 10% off Baidu stock |

### Technical Advances
- **BERT**: Revolutionary bidirectional context understanding
- Named playfully after Sesame Street character
- Transformer architecture became foundation for modern chatbots
- Unlike earlier models, looks at words before AND after

### Why They Matter
- Marked leap in AI language abilities
- Set stage for today's LLMs that write, code, and converse
- Foundation for current AI assistants and chatbots

## Talk Structure Suggestions

### Opening Hook
Start with Asimov's laws to frame early ethics thinking

### Building Narrative
1. **Past**: Asimov's vision → biological inspiration (Roomba)
2. **Present**: Current capabilities (CNNs, BERT/LLMs) and limitations
3. **Future Concerns**: Singularity, alignment, paperclips
4. **Real Impact**: Jobs, AlphaGo moments changing fields overnight

### Engagement Techniques
- Physical props (paperclip for alignment discussion)
- Audience questions ("What signs of singularity do you see?")
- Contrasts (biological vs. silicon intelligence)
- Real-world examples (Roomba success, AlphaGo's alien moves)

### Key Takeaway
AI development mirrors evolution—simple reflexes to complex cognition—but compressed from billions of years to decades, creating both unprecedented opportunities and risks requiring thoughtful navigation.