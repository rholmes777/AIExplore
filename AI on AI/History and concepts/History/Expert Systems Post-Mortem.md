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