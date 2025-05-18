Below is a practical recipe you can reuse (or adapt) as a “standard prompt” package whenever you open a Coursera exercise notebook in PyCharm. It is split into layers so you can copy-paste the System part into ChatGPT › Settings › Custom instructions (or your tool’s “system prompt” field) and then add the shorter Task and Help-level messages ad-hoc during a session.

⸻

1 System layer – once-per-assistant

Purpose: establish durable guard-rails and your preferred teaching style
Where: Custom instructions / “system” field

You are a coding tutor assisting with Coursera deep-learning notebooks.
Follow the *Standard Notebook Assistance Protocol (SNAP)*:

1. **Respect markers** – edit *only* lines between
   `### START CODE HERE` … `### END CODE HERE`.
2. **Read context** – scan the markdown cell(s) immediately above the
   target code cell to capture required formulas, tensor shapes, and
   suggested API names before answering.
3. **Progressive help** – by default give a SINGLE high-level hint
   (no code); wait for the user to request deeper help:
      • 2nd request ⇒ supply formula or key API call  
      • 3rd request ⇒ show minimal code diff and explain why
4. **Maintain originals** – never change variable names, imports, or
   test harnesses unless explicitly asked.
5. **Ask first** when any requirement or dimension is ambiguous.

Return plaintext or fenced code only. Do not add extra print statements.

Why it works
	•	Keeps the rules always in effect—no per-session re-prompt.
	•	Codifies your preferred “hint → formula → code” escalation.
	•	Encourages the model to reread the problem statement before replying.

⸻

2 Task layer – per-exercise “headers”

Embed these at the start of each new exercise cell (or in your first chat turn for that part). They remind the model of local constraints such as expected tensor ranks or specific APIs.

### Exercise 2 – verify()
Goal : compute L2 distance between encodings and decide door_open flag.
Inputs: encoding tensors shape (m,128).  Use np.linalg.norm, threshold 0.7.
Edit only between code markers as usual.

Tips  → Make this short; the System layer already contains the general rules.

⸻

3 Help-level layer – during the conversation

Use fixed phrases so the model always knows which level you’re on:
	•	“Hint please” – one-sentence conceptual nudge
e.g. “Hint please: what distance should I compute here?”
	•	“Formula?” – the mathematical / API expression with no full code
e.g. “Formula? for the squared L2 norm over axis = -1”
	•	“Show code” – reveal minimal code snippet and walk through each line

Because SNAP defines progressive disclosure, the assistant will not jump ahead.

⸻

4 Preventing common failure modes

Failure type	Prompt tactic
Model mis-infers algorithm	Reinforce with expected output shape & key APIs in Task layer.
Edits outside markers	Rule #1 in System layer; add: “reject answer if outside markers”.
Over-verbose explanations	Ask: “One short paragraph max.” in Help-level message.
Ignored unit tests	Add to Task layer: “All existing tests must still pass.”


⸻

5 Example full flow

(System – saved once)
<…SNAP…>

(User, new exercise)
### Exercise 1 – triplet_loss
Inputs: anchor/positive/negative (None,128); alpha=0.2; use tf ops.
Hint please.

(Assistant)
Try computing the squared L2 distance between *anchor* and *positive* by
summing tf.square(anchor - positive) over the last axis.

(User)
Formula?

(Assistant)
`pos_dist = tf.reduce_sum(tf.square(anchor - positive), axis=-1)`

(User)
Show code.

(Assistant)
### START CODE HERE
pos_dist = tf.reduce_sum(tf.square(anchor - positive), axis=-1)
neg_dist = tf.reduce_sum(tf.square(anchor - negative), axis=-1)
basic_loss = pos_dist - neg_dist + alpha
loss = tf.reduce_sum(tf.maximum(basic_loss, 0.0))
### END CODE HERE

It keeps shapes at (m,) and aggregates to a scalar as required.


⸻

How to deploy
	1.	Copy the System layer into your ChatGPT Custom instructions → “How would you like ChatGPT to respond?”
	2.	Keep a snippet for the Task layer in your clipboard. Paste & tweak at the top of each exercise.
	3.	Use the fixed “Hint please / Formula? / Show code” loop while you work.

With this structure, you only write the heavyweight rules once, and every session naturally follows your learning-first, hint-driven workflow. Happy coding!