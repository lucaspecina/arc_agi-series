# Chapter 0: Introduction to ARC and Intelligence

**Lucas Pecina**

*AI Researcher and Head of AI at Y-TEC*

*Nov 2024*

## Introduction to the Series

My name is Lucas Pecina, and I the head of AI research at Y-TEC. This series of videos will document my research on solving the **ARC-AGI** challenge. I'll share my progress, research, and insights as I delve into ARC, analyze existing solutions and approaches, and conduct my own investigations. All my code and research will be open source. I'll also explore relevant papers and new proposals in the field.

This first video I'll provide an overview of the ARC-AGI challenge, discuss the history of AI, and introduce François Chollet's definition of intelligence. I'll also cover the characteristics for evaluating intelligence, the ARC benchmark, and the limitations of large language models (LLMs).

---
I will adopt François Chollet's definition and approach to intelligence, based on his famous paper "On the Measure of Intelligence" and other articles and interviews. The goal of this series is to explore and test different approaches to solving the ARC-AGI challenge, which is a benchmark for measuring intelligence created by Chollet himself, and to share my findings and progress with the community.

This document serves as a guide for the first video in the series. It is not intended to be a scientific article, but rather a summary of the topics that will be covered in the video.

## History and Evolution of Intelligence: Task-Specific Approaches vs. Generalization

> "To make deliberate progress towards more intelligent and more human-like artificial systems, we need to be following an appropriate feedback signal: we need to be able to define and evaluate intelligence in a way that enables comparisons between two systems, as well as comparisons with humans."  
> —From the abstract of *"On the Measure of Intelligence"* by François Chollet

Throughout the history of AI, there have been two main schools of thought in defining its objectives. These perspectives focus on the dichotomy between **task-specific skill** and **general learning ability**.

### Intelligence as a Collection of Task-Specific Skills

This view, rooted in evolutionary psychology, suggests that human cognitive function is largely the result of **special-purpose adaptations** that evolved to solve specific problems encountered throughout human evolution. In early AI, intelligence was seen as a set of **static routines** similar to programs, heavily relying on logical operators and storing learned knowledge in database-like memory.

**Minsky's View:** Focuses on an AI's ability to perform economically valuable tasks, evaluating its intelligence based on its performance in specific tasks, such as board games or video games.

### Intelligence as a General Learning Ability

This perspective posits that intelligence lies in the **general capacity to acquire new skills through learning**. This ability could be directed toward a wide range of previously unknown problems, perhaps even any problem. Alan Turing, in his 1950 paper, proposed the idea that machines could acquire new skills through a learning process similar to that of human children.

This view echoes Locke's concept of **"Tabula Rasa"**, seeing the mind as a flexible, adaptable, and highly general process that transforms experience into behavior, knowledge, and skills.

---

François Chollet **criticizes both perspectives** for being too simplistic. He argues that Minsky's view reduces intelligence to skill in specific tasks, ignoring the capacity for generalization. On the other hand, the Tabula Rasa view, while recognizing the importance of generalization, does not provide a precise definition or a way to measure it.

In summary, the human mind is a complex system that **combines both innate biases and the ability to learn from experience**. These biases are not a limitation to our generalization capabilities but rather their source—the reason why humans can acquire certain categories of skills with remarkable efficiency.

---

## Characteristics for Evaluating Intelligence

To progress toward more flexible and general AI, we need to go beyond skill-based evaluation and adopt methods that capture systems' ability to handle novel and uncertain situations. The greatest successes in AI have been in building special-purpose systems capable of handling well-defined tasks, sometimes with superhuman performance. This success has been measured by performance metrics that quantify a system's **skill** in a given task (e.g., how well an AI plays chess or recognizes images).

However, this is a problem, as skill in a specific task is not necessarily indicative of intelligence. The capacity for **generalization** is fundamental for evaluating a system's intelligence, and current benchmarks do not adequately measure it.

### Generalization

**Degrees of Generalization (Spectrum):**

- **No Generalization:** Systems without uncertainty, such as deterministic programs or algorithms with correctness proofs.
  
- **Local Generalization (Robustness):** Ability to handle new oiunts from a known distribution for a single task, like an image classifier recognizing new images after training. This is the classical Machine Learning paradigm. "Adaoptation to known unknowns".
  
- **Broad Generalization (Flexibility):** Ability to handle a wide range of tasks and environments without human intervention, like a fully autonomous vehicle. The system could handle situations that couldn't be foreseen by the creators of the system. "Adaptation to unknown unknowns across a broad category of related tasks".
  
- **Extreme Generalization:** Ability to handle entirely new tasks that share only abstract similarities with previously encountered situations, like human intelligence. ·Adaptation to unknown unknowns across an unknown range of tasks and domains".


This spectrum reflects the hierarchical organization of human cognitive abilities, as described by theories of intelligence structure in cognitive psychology (e.g., CHC, g-VPR).

![Generalization Spectrum](images/ch0-generalization.png)

**Skill in a specific task is not necessarily indicative of intelligence.**

Information processing systems form a spectrum between two extremes: 
- **static systems**: that consist entirely of hard-coded priors. 
- **general systems**: that can learn new skills with minimal priors and are almost entirely programmed via exposure to data.

The capacity for **generalization** runs orthogonal to prior knowledge and experience. A system can achieve high performance in a task due to extensive knowledge or training **without necessarily being able to generalize to new situations**.

I think current AIs are between local and broad generalization at the moment. They can adapt to new situations within their training distribution, but they struggle with tasks that are too different from their training data. The goal is to push AI toward extreme generalization, where they can learn new tasks with minimal data and experience.

To evaluate intelligence meaningfully, it's crucial to **control for prior knowledge, experience, and generalization difficulty**, rather than focusing solely on task-specific skill.

Human intelligence, although broad compared to other animals, **is not universal**. Humans excel in specific cognitive tasks but struggle in other domains that might be trivial for different systems.

**"General intelligence" is not binary** but a spectrum depending on:

- **Scope of Application:** The set of tasks where intelligence applies.
  
- **Skill-Acquisition Efficiency:** How effectively a system turns prior knowledge and experience into new skills.
  
- **Generalization Difficulty:** The inherent complexity of tasks within the considered scope.

---

## Chollet's Definition of Intelligence

Chollet defines intelligence as the **efficiency in acquiring new skills over a range of tasks, considering prior knowledge, experience, and generalization difficulty**.

In other words, it's a system's ability to learn new skills with minimal information and experience.

He emphasizes that **intelligence is a process, not a product**. It's about learning and adapting, not just executing preprogrammed skills. **Skill** is the product of intelligence—the result of learning.

FUNDAMENTAL IDEA OF INTELLIGENCE: Intelligence is a cognitive mechanism (a tool) that an agent uses to adapt to novelty in situations not previously encountered. It does this by creating models on the fly of the new situation, combining existing building blocks learned through experience.

Three key concepts to define and measure intelligence:

- **Fluid Intelligence vs. Static Skill:** Fluid intelligence is the ability to synthesize new programs or strategies for novel problems, while static skill relies on a set of solutions for known problems.
  
- **Operational Area:** The range of situations where a system can successfully operate. A more intelligent system has a broader operational area, allowing it to generalize more widely.
  
- **Information Efficiency:** Measures how much data a system needs to acquire a new skill or program. A more intelligent system uses information more efficiently.

Chollet says that the mind or a general intelligence has two main components: **Program Synthesis** and **Abstraction Generation**.

- **Program Synthesis:** You take the building blocks and assemble them to form a program model that matches the current task.
- **Abstraction Generation:** The inverse process. You look at the information you have available and the model you have already created to respond to it, and convert that into reusable abstractions that you can store in your memory to retrieve at other times.

Intelligence is a TOOL for agents to accomplish goals. It is separate from other modules of an agent's system, such as the sensor motor (and sensorimotor space/action space), the ability to set goals, or even the world model. These are different things, with different functions within an agent.

One can set a goal and have an idea of the world, and intelligence is the pathfinding algorithm that uses that world model (representing what the goal means and perhaps even simulating planning) to reach that objective. Intelligence could be seen as a  way to take in information and turn it into an actionable model.

I will discuss these components further in the next video, along with other analyses of how the mind works and how we can apply these concepts to artificial intelligence. For example, the division between System 1 and System 2, how humans learn from a constructivist perspective, and intelligence as a meta-skill. This video is just a general introduction to the problem and the proposed benchmark for measuring intelligence.

---

## Limitations of Large Language Models (LLMs) and current AI

Chollet observes that current LLMs, despite impressive capabilities, have **significant limitations**:

Their limitations include:

- **Dependence on Familiarity:** Excel in tasks similar to training data but fail in novel tasks or those requiring deep reasoning. They rely on memorization and superficial pattern recognition, not true understanding.
  
- **Fragility to Changes:** Small modifications in task formulation or variables can drastically affect performance, showing a lack of robustness and deep understanding.

LLMs are essentially **databases of "skill programs"**, each representing a specific ability like translation or creative writing.

When querying an LLM, you are querying a point in program space. An LLM is a manifold where each point represents a program. They are trained to predict the next token. If you had infinite memory capacity, it would essentially be a large lookup table. However, due to limited capacity, it must compress the information. Thus, it learns predictive vector functions. 

For example, if you provide it with Shakespearean text it has never seen before, but it has been trained on English texts, it has learned programs that model English. Therefore, it can reuse functions (programs) it has already learned. The LLM learns millions of functions and can combine them. (In this context, a "program" is an input→output mapping that is continuous (they are functions). They are compositional because they are vector functions. You can add them, you can interpolate between them because they are continuous functions).

During training, LLMs learn to **map input tokens to output tokens**, building vector functions encoding these mappings. Due to memory limits, they **compress the space of memorized programs**, expressing new ones using fragments of known programs. This allows **limited generalization** to slightly different inputs.

However, this generalization is limited:

- **Caesar Ciphers:** LLMs can decrypt common key sizes but fail with unusual ones, indicating memorization of specific cases rather than understanding the cipher.
  
- **Logic Problems:** Solve familiar problems but fail when variables change, suggesting reliance on memorized patterns over logical reasoning.

These examples show that **LLMs' performance heavily depends on task familiarity**. They can handle complex tasks only if they've memorized solutions.

This limitation applies to all deep learning models—an inherent consequence of fitting models to training data.

---

## Introduction to ARC (Abstraction and Reasoning Corpus)

Chollet argues for **new ways to evaluate AI** to measure real progress toward general, less memorization-dependent intelligence. Current methods, focusing on model scaling and task-specific performance, don't adequately assess generalization.

**Limitations of Common AI Tests:**

- Allow systems to "cheat" by memorizing patterns rather than understanding.
  
- Don't evaluate the ability to generalize to new tasks not included in training.
  
- Focus on skill rather than learning capacity.

To address these, Chollet proposes **ARC**, designed to measure a form of human-like fluid intelligence.

### What is ARC?

ARC is a benchmark for general AI, program synthesis, and a psychometric test of intelligence. It's aimed at both humans and AI systems seeking to emulate human-like general fluid intelligence.

**Key Features of ARC:**

- **Novel Tasks:** Tasks are new to both the system and developers, preventing memorization and encouraging generalization.
  
- **Abstraction and Reasoning:** Requires extracting abstract patterns and applying them to new situations, evaluating reasoning ability.
  
- **Few Examples:** Provides limited examples, forcing efficient learning and generalization from minimal information.
  
- **Controlled Priors:** Based on explicit priors (innate knowledge) similar to human priors, allowing fair comparison between AI and humans.

---

### Core Knowledge Priors

**a. Object Priors:**

Based on the human ability to perceive the world as composed of individual objects.

- **Object Cohesion:** Objects hold together and move as units, defined by color continuity or spatial contiguity.
  
- **Object Persistence:** Objects remain despite noise or partial occlusion.
  
- **Influence by Contact:** Objects interact through physical contact, not at a distance.

![Object Priors](images/ch0-figure7.png)
![Object Priors Rebound](images/ch0-figure8.png)

**b. Goal-Directedness Prior:**

Reflects the human tendency to interpret actions as goal-oriented. While ARC doesn't handle time explicitly, many tasks can be seen as initial and final states of an intentional process. This prior isn't strictly necessary but can be useful.

![Goal-Directedness Prior](images/ch0-figure9.png)

**c. Number and Counting Priors:**

Based on the innate human ability to understand and manipulate small numbers. ARC includes tasks involving counting, ordering, comparing, and basic arithmetic with numbers less than 10.

![Number Priors](images/ch0-figure10.png)

**d. Basic Geometry and Topology Priors:**

Reflects intuitive understanding of space and shapes. ARC includes concepts like lines, rectangles, symmetries, rotations, translations, scaling, distortions, containment, and connecting points.

![Geometry Priors](images/ch0-figure11.png)

**Note:** ARC doesn't use language, real-world images, or common-sense knowledge acquired through experience. This ensures tasks are novel for both humans and machines, focusing on fluid intelligence—reasoning and abstraction.

> "Crucially, to the best of our knowledge, ARC does not appear to be approachable by any existing machine learning technique (including Deep Learning), due to its focus on broad generalization and few-shot learning, as well as the fact that the evaluation set only features tasks that do not appear in the training set."

---

## Abstraction as the Engine of Generalization

Chollet argues that **abstraction** is fundamental for generalization. It involves identifying patterns and relationships and encoding them into abstract representations reusable in new situations.

He distinguishes **two types of abstraction**:

- **Value-centric Abstraction (deep learning):** Compares continuous values. This is what deep learning models do—effective for **perception** tasks but limited in abstract reasoning.
  
- **Program-centric Abstraction (program synthesis):** Compares discrete programs (graphs) by finding exact structural matches (subgraph isomorphisms). This is analogous to human reasoning and software engineering practices. It relies on structural similarity.

**Deep learning-based AI (transformers, LLMs)**: the architecture behind many LLMs, excel in value-centric abstraction but are inadequate for program-centric abstraction, limiting their ability to generalize to new situations and perform complex reasoning. They find "similar" things. They are not exact; they are approximate. They can give you a good DIRECTION on where to search or go.

He suggests that **intelligence arises from combining these two forms of abstraction**. The human brain exemplifies this, with the left hemisphere associated with reasoning (program-centric abstraction) and the right with perception (value-centric abstraction).

When refactoring code, we don't want the functions to "feel" similar but to be exactly the same with the exact same behavior. You need to see it explicitly step by step and verify it. Comparing perfectly step by step is more costly. Therefore, a good idea is not to search randomly but to use your intuition to search more efficiently for options to verify.

---

## Different Approaches in AI

### 1. Discrete Program Search

- **Concept:** Exploring a space of possible programs, evaluating each to see if it produces the correct output.
  
- **Advantages:** Effective for solving tasks like those in ARC-AGI.
  
- **Challenges:** Combinatorial explosion of possible programs makes exhaustive search unfeasible.
  
- **Opportunities:** Using deep learning to guide the search can make it more efficient.

### 2. Domain-Specific Language (DSL) Program Synthesis

- **Concept:** Creating a DSL specific to ARC-AGI tasks, defining primitives like rotation and reflection.
  
- **Advantages:** Programs are concise and human-readable; search space is reduced.
  
- **Challenges:** Designing an effective DSL that's expressive yet simple is difficult.

### 3. Deep Learning

- **Based on value-centric abstraction.**
  
- **LLMs:** Impressive in language tasks but limited in generalization and abstract reasoning.

### 4. Active Inference

- Uses pre-trained LLMs further trained with code and synthetic data similar to ARC-AGI.
  
- **Inference involves adjusting the LLM with task examples, expanding them artificially for more data points.**
  
- **This approach has led to better performance in some solutions.**

**LLMs' results on benchmarks like ARC are promising but far from human capability.** They lack true generalization and rely heavily on task familiarity.

---

## Promising Approaches: Program Search + Deep Learning

To advance toward AGI, it's proposed to **combine deep learning with program search**.

### Two Main Approaches:

1. **Incorporate Discrete Programs into Models:**

   - Use deep learning as a perception layer to break down situations into discrete elements fed into a program search engine.

2. **Use Deep Learning to Guide Program Search:**

   - Deep learning provides "intuitions" or "sketches" to guide the search, reducing combinatorial complexity.

In ARC, these ideas can **"map out" the state or program space**, turning program search into an interpolation problem and reducing computational demands.

**Interaction of Both Abstractions Allows:**

- **Guiding Search with Intuition:** Deep learning offers insights into problem structure, directing search toward promising solutions.
  
- **Generating Efficient Programs:** Search produces more efficient, generalizable programs with deep learning's guidance.

---

## Recommendations and Potential Approaches

### 1. Integrate Programs into Deep Learning Models

- **Perception with Deep Learning for Program Search:**

  - Use deep learning to process perceptual information, identifying patterns and breaking down complex situations into discrete elements.
  
  - Represent these elements symbolically for program synthesis.
  
  - Example: A neural network identifies objects and relationships in an image, translating them into symbols for program manipulation.

- **Symbolic Extensions of Deep Learning Models:**

  - Add symbolic modules to neural networks for logical operations and reasoning.
  
  - Combine sensory data processing with abstract reasoning and knowledge manipulation.

### 2. Use Deep Learning to Guide Program Search

- **Deep Learning Intuitions for Search:**

  - Train models to predict the likelihood of programs being valid solutions.
  
  - Use predictions to prioritize program exploration, reducing computational complexity.

- **Program Sketches Generated by Deep Learning:**

  - Models generate "sketches" or templates of programs.
  
  - Sketches provide a general structure, refined through program search, guiding toward meaningful solutions.

---

## Next Steps: Approaches

- **Discuss LLMs and Inference-Time Compute:**

  - Explore fine-tuning methods and others like Test-Time Training (TTT).

- **Examine Models with Better Performance:**

  - I will analyze the solutions that have shown the best performance for the ARC challenge, and compare them to other approaches.

- **Conceptual Ideas: System 1 and System 2:**

  - Use deep learning for intuition (System 1) and build discrete programs for reasoning (System 2).

- **Improve Visual Pattern Recognition:**

  - Enhance models' ability to recognize and interpret visual patterns.

- **Explore Neuro-Symbolic AI and Knowledge Graphs:**

  - Deep learning creates primitives for programs used in discrete program search.

---

**All code and research will be open source.**


---
## References

1. Chollet, F. (2019). *On the Measure of Intelligence*. [https://arxiv.org/pdf/1911.01547](https://arxiv.org/pdf/1911.01547)

2. ARC Prize. *ARC Prize Guide*. [https://arcprize.org/guide](https://arcprize.org/guide)

3. ARC Prize. *General Intelligence: Define it, measure it, build it*. YouTube. [https://www.youtube.com/watch?v=nL9jEy99Nh0](https://www.youtube.com/watch?v=nL9jEy99Nh0)

4. Machine Learning Street Talk. *It's Not About Scale, It's About Abstraction*. YouTube. [https://www.youtube.com/watch?v=s7_NlkBwdj8](https://www.youtube.com/watch?v=s7_NlkBwdj8)

5. ARC Prize. *ARC Prize 2024 University Tour Virtual Event*. YouTube. [https://www.youtube.com/watch?v=NDbNlPiS898](https://www.youtube.com/watch?v=NDbNlPiS898)

6. Machine Learning Street Talk. *Pattern Recognition vs True Intelligence - Francois Chollet*. YouTube. [https://www.youtube.com/watch?v=JTU8Ha4Jyfc](https://www.youtube.com/watch?v=JTU8Ha4Jyfc)
