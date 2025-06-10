## Quick primers

**SHRDLU (1970, Winograd)**

- Blocks-world “toy” that let users type plain-English commands: _“Pick up the red block and put it on the green one.”_
    
- Parsed language, planned the action, updated an internal 3-D model, and answered follow-up questions (“Why can’t I stack that there?”).
    
- Landmark demo of natural-language understanding + reasoning in a constrained micro-universe.
    

**MACSYMA (1968, MIT)**

- Early computer-algebra system: symbolic integration, differentiation, factoring, simplification.
    
- Handled expressions too large or messy for hand math—precursor to today’s Mathematica/Maple/Maxima.
    
- Adopted by DOE & NASA for plasma physics and orbital mechanics in the 1970s.
    

---

### Why LISP became _the_ symbolic-computing language

1. **Homoiconic lists** – Code _is_ data (S-expressions), making it trivial to build and transform abstract syntax trees—the core of symbolic manipulation.
    
2. **Automatic memory management** – Garbage‐collected cons cells free researchers from manual bookkeeping while juggling large expression graphs.
    
3. **Macros & runtime eval** – Programs can generate and run new code on the fly, ideal for AI systems that extend their own rule sets.
    
4. **Dynamic types & recursion** – Suits heterogeneous symbolic structures (atoms, lists, trees) and pattern-matching algorithms.
    
5. **Ecosystem effect** – Most AI labs (MIT, SAIL, CMU) standardized on LISP, so landmark systems—SHRDLU, MACSYMA, MYCIN—shared libraries, IDEs, and hardware (Lisp machines).
    

_Net takeaway:_ LISP’s list-processing DNA matched the needs of “symbolic AI,” where manipulating symbols, terms, and rules trumped raw number-crunching.