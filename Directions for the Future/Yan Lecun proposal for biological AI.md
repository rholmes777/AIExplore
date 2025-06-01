Yann LeCun's lecture, "Mathematical Obstacles on the Way to Human-Level AI," delivered as the Josiah Willard Gibbs Lecture at the 2025 Joint Mathematics Meetings, offers a critical perspective on the current trajectory of AI development, particularly large language models (LLMs), and proposes a fundamentally different path toward achieving human-level artificial intelligence (AI).

-----

## Core Arguments and Key Takeaways

LeCun, a pioneer in deep learning and Chief AI Scientist at Meta, argues that current AI, heavily reliant on **supervised learning** and **reinforcement learning**, is highly **sample-inefficient** compared to human and animal learning. He contends that present-day LLMs are fundamentally flawed and will not lead to Artificial General Intelligence (AGI), which he prefers to call **Advanced Machine Intelligence (AMI)**. His core criticisms of LLMs include:

  * **Lack of World Models:** LLMs do not build an internal, intuitive understanding of the physical and social world, which is crucial for common sense, reasoning, and planning.
  * **Next-Token Prediction Limitations:** Their auto-regressive nature of predicting the next token in a sequence is inherently limited. It leads to **error accumulation** over long sequences and is inefficient for tasks requiring complex reasoning or variable computation. LeCun famously describes LLMs as "doomed" to remain mere "token generators."
  * **System 1 vs. System 2 Thinking:** LLMs primarily operate in what Daniel Kahneman terms "System 1" (fast, intuitive, fixed computation), lacking the "System 2" (slow, deliberate, variable computation) reasoning capabilities essential for true intelligence.
  * **Data Inefficiency:** While impressive, LLMs require astronomical amounts of text data, vastly exceeding what humans need to learn.

LeCun proposes that the path to AMI requires AI systems to learn **"world models"** from observation, similar to how infants learn about their environment through interaction. This would enable them to understand intuitive physics, predict outcomes, perform complex planning, and reason. He advocates for a shift towards **objective-driven AI** using **energy-based models (EBMs)** and **inference by optimization**.

His proposed cognitive architecture for AMI includes:

  * A **world model** learned through self-supervised learning.
  * **Objective functions** that guide behavior.
  * An **actor** that performs inference by optimization.
  * **Memory** modules.
  * A **perception module**.

Central to his vision is the **Joint Embedding Predictive Architecture (JEPA)**, a self-supervised learning method designed to learn rich, abstract representations of sensory data (like images or video) by predicting in a latent, abstract space rather than predicting every pixel or detail. This allows the model to discard irrelevant information and focus on predictable features.

-----

## Mathematical Obstacles Highlighted by LeCun

LeCun identifies several key mathematical and conceptual hurdles that, in his view, prevent current AI paradigms from reaching human-level intelligence:

  * **Sample Inefficiency:** The vast number of examples required for current supervised and reinforcement learning models is a mathematical inefficiency. Humans and animals learn complex skills from far fewer demonstrations or trials.
  * **Divergence of Auto-Regressive Prediction:** The challenge of predicting long sequences of discrete symbols leads to an "exponentially-divergent diffusion process" where errors compound, making models uncontrollable for complex tasks. This mathematical property limits the scalability of auto-regressive LLMs for true understanding and reasoning.
  * **Fixed Computational Budget:** Current LLMs perform a fixed amount of computation per token or step, which is inadequate for problems requiring variable, deeper thought processes (System 2 thinking).
  * **Learning World Models:** The mathematical challenge lies in designing architectures that can effectively learn an internal, causal, and compositional model of the world from raw, high-dimensional sensory inputs without explicit supervision. This requires overcoming the "curse of dimensionality" and learning abstract representations that capture underlying dynamics.
  * **Training Stability of Energy-Based Models:** While advocating for EBMs, LeCun acknowledges the mathematical difficulties in training them to prevent "collapse" (where the model learns to assign low energy to all possible inputs). Methods like **VicReg (Variance-Invariance-Covariance Regularization)** are proposed to stabilize training by ensuring high variance and decorrelation in the learned representations.
  * **Moravec's Paradox:** LeCun implicitly refers to this paradox, which states that what is easy for humans (e.g., sensorimotor skills, common sense) is hard for AI, and what is hard for humans (e.g., complex calculations, abstract reasoning) is relatively easier for AI. Current AI, particularly LLMs, excels at "hard" human tasks (text generation) but struggles with the "easy" common-sense understanding of the physical world.

-----

## Research and Background Information

### Yann LeCun's Key Publications and Initiatives

  * **Official Website:** [Yann LeCun's Home Page](http://yann.lecun.com/) - A comprehensive source for his publications, talks, and research philosophy.
  * **"A Path Towards Autonomous Machine Intelligence" (2022):** This influential position paper outlines LeCun's vision for AGI, emphasizing world models, self-supervised learning, and an architecture based on energy-based models.
      * [A Path Towards Autonomous Machine Intelligence](https://www.google.com/search?q=https://openreview.net/forum%3Fid%3DVfF1Y3Kx4D)
  * **Energy-Based Models (EBMs):** LeCun has extensively researched EBMs, which are foundational to his proposed AMI architecture.
      * **Tutorials and Overviews:**
          * [Energy-Based Models · Deep Learning](https://atcold.github.io/NYU-DLSP20/en/week07/07-1/)
          * [Introduction to latent variable energy-based models: a path toward autonomous machine intelligence (Dawid, LeCun, 2024)](https://arxiv.org/abs/2410.02102) - A recent comprehensive overview.
          * [Energy-Based Models: Structured Learning Beyond Likelihoods (LeCun, 2006 NIPS Tutorial)](https://www.google.com/search?q=https://cs.nyu.edu/~yann/talks/06-nips-ebm-tutorial.pdf)
  * **Joint Embedding Predictive Architecture (JEPA):** While the conceptual framework for JEPA was introduced by LeCun (e.g., in his 2022 position paper), the practical implementations are often developed by his research group.
      * **I-JEPA (Image-JEPA):**
          * [I-JEPA: The first AI model based on Yann LeCun's vision for more human-like AI (Meta AI Blog)](https://ai.meta.com/blog/yann-lecun-ai-model-i-jepa/)
          * [Self-Supervised Learning From Images With a Joint-Embedding Predictive Architecture (Assran et al., CVPR 2023)](https://openaccess.thecvf.com/content/CVPR2023/papers/Assran_Self-Supervised_Learning_From_Images_With_a_Joint-Embedding_Predictive_Architecture_CVPR_2023_paper.pdf) - This paper details the first implementation of JEPA for images.
      * **V-JEPA (Video-JEPA):**
          * [V-JEPA: The next step toward Yann LeCun's vision of advanced machine intelligence (AMI) (Meta AI Blog)](https://ai.meta.com/blog/v-jepa-yann-lecun-ai-model-video-joint-embedding-predictive-architecture/)

### Broader Discussions on Mathematical Obstacles to AGI

  * **Limitations of Scaling Laws:** While many in AI believe simply scaling up current models will lead to AGI, others, including LeCun, argue that fundamental architectural changes are necessary.
  * **Theoretical Barriers to Proving AGI Intractability:** Research explores the mathematical difficulties in proving that certain AI approaches cannot achieve AGI, or conversely, that AGI is inherently intractable with current methods.
      * [Barriers to Complexity-Theoretic Proofs that Achieving AGI Using Machine Learning is Intractable (Korb, arXiv 2023)](https://arxiv.org/pdf/2309.05779)
  * **Neural-Symbolic AI:** The debate on whether symbolic reasoning needs to be explicitly integrated with neural networks to overcome the limitations of purely statistical models.
      * [AI Reasoning in Deep Learning Era: From Symbolic AI to Neural–Symbolic AI (Liu et al., Sci Rep. 2023)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10719875/)

-----

## Technical Terms Explained

  * **Energy-Based Models (EBMs):** A class of statistical models that associate a scalar "energy" value with each configuration of variables. Learning in EBMs involves finding a function that assigns low energy to correct or compatible configurations and high energy to incorrect or incompatible ones. Inference then becomes an optimization problem of finding variables that minimize the energy function.
  * **Joint Embedding Predictive Architecture (JEPA):** A type of self-supervised learning architecture where two or more neural networks (encoders) learn to map different views or parts of an input (e.g., different patches of an image, or future frames of a video) into a shared, abstract representation space. The model is trained to predict the representation of one part from the representation of another, rather than predicting the raw pixels or data directly. This forces the model to learn meaningful, high-level features.
  * **VicReg (Variance-Invariance-Covariance Regularization):** A self-supervised learning objective used to train joint embedding architectures. It encourages the learned representations to be invariant to input augmentations, maintain high variance (to prevent collapse where all inputs map to the same representation), and have decorrelated dimensions.
  * **Auto-regressive LLMs:** Large Language Models that predict the next token (word or sub-word) in a sequence based on the preceding tokens. This process is repeated to generate longer texts. Examples include GPT series.
  * **System 1 & System 2 Thinking:** Concepts from Daniel Kahneman's "Thinking, Fast and Slow." **System 1** is fast, intuitive, automatic, and emotionally driven. **System 2** is slower, more deliberate, analytical, and logical. LeCun argues current LLMs are primarily System 1.
  * **Backpropagation:** The fundamental algorithm used to train artificial neural networks. It calculates the gradient of the loss function with respect to the weights of the network, allowing the weights to be adjusted to minimize the loss.
  * **Moravec's Paradox:** The observation in AI and robotics that reasoning requiring high-level human intellect (e.g., playing chess) often requires relatively little computation, whereas basic sensorimotor skills and perception (e.g., walking, recognizing faces) that are unconscious and effortless for humans require immense computational resources and are hard for AI.

-----

## Follow-up Discussions and Critiques

Yann LeCun's outspoken views often spark significant debate within the AI community. Critiques and discussions surrounding his "Mathematical Obstacles" lecture and broader vision include:

  * **Skepticism about Strong Predictions:** Some critics express skepticism about definitive statements regarding the "doom" of certain AI paradigms, noting that the field evolves rapidly.
  * **Meta's Dual Strategy:** LeCun's strong stance against LLMs is sometimes contrasted with Meta's significant investment in and development of its own LLMs (e.g., Llama), leading to discussions about the company's long-term AI strategy.
  * **The Nature of AGI:** The definition and path to AGI remain highly debated. LeCun's emphasis on world models and embodied intelligence is one prominent viewpoint among many.
  * **Hallucination in LLMs:** While not a direct critique of LeCun, research highlighting the inherent tendency of LLMs to "hallucinate" (generate factually incorrect or nonsensical information) provides strong independent support for LeCun's arguments about their fundamental limitations.
      * [Hallucination is Inevitable: A Taxonomy of Hallucinations in Large Language Models (arXiv 2024)](https://arxiv.org/abs/2403.01646) - This paper mathematically argues that LLMs are intrinsically prone to generating plausible but incorrect information.

LeCun's lecture serves as a powerful call to rethink the foundational mathematical and architectural approaches to AI, advocating for a shift towards systems that learn robust world models and reason through optimization, rather than relying solely on large-scale pattern matching from text data.