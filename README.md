# 🧠 Hypothesis Generation for ARC Tasks - CCM Project (Fall 2024)

## Overview

This project addresses the **HARC Challenge** for **December 2024**:  
**Solving abstract reasoning tasks from the ARC dataset** using **human cognitive insights** and **hypothesis generation** techniques.

Inspired by cognitive science, our approach builds a scalable system that:
- Leverages human-annotated explanations from the **H-ARC dataset**,
- Synthesizes natural language hypotheses,
- Converts hypotheses into Python code,
- Iteratively refines through feedback loops,
- Executes and validates solutions asynchronously for efficiency.

Our goal is to bridge the gap between AI and human abstract reasoning, by demonstrating how structured hypothesis generation improves ARC task-solving capabilities.

---

## Challenge Background: HARC December 2024

The **Abstraction and Reasoning Corpus (ARC)**, introduced by François Chollet, is considered one of the toughest benchmarks for machine intelligence.  
Despite advances like GPT-4, solving ARC tasks remains a major unsolved problem.

Our project tackles this gap using:
- The **H-ARC Dataset** (Human-Annotated ARC),
- **Prompt-engineered** hypothesis generation,
- **Code synthesis** through a large open-source model (Qwen 2.5 Coder 32B),
- **Feedback-driven iterative refinement**.

By combining human reasoning patterns with LLMs, we push towards achieving **true abstraction capabilities** in AI systems.

---

## Project Pipeline

1. **Hypothesis Synthesis**  
   - Generate a natural language hypothesis describing grid transformations.
   - Use structured prompts with human annotations from H-ARC.

2. **Code Generation**  
   - Translate hypotheses into executable Python functions (`transform_grid`).

3. **Iterative Feedback Loop**  
   - Evaluate generated code.
   - Refine hypotheses and code based on errors.
   - Repeat up to `MAX_FEEDBACK_ATTEMPTS` times.

4. **Validation**  
   - Test on unseen examples.
   - Measure accuracy and task-solving performance.

5. **Asynchronous Execution**  
   - Use parallel processing to scale across tasks efficiently.

---

## Results Summary

| Method                        | Correct (out of 100 tasks) |
|:-------------------------------|:---------------------------|
| Direct Prompting (no context)  | 0                          |
| H-ARC Hypothesis (longest only) | 9                         |
| Synthesized Hypothesis (ours)   | 11                         |

✅ Even though accuracy remains low compared to humans, our method shows **notable improvement** over direct prompting baselines, highlighting the effectiveness of **human-guided abstraction**.

---

## Setup Instructions

1. **Clone the repositories**
   ```bash
   git clone https://github.com/fchollet/ARC-AGI.git
   git clone https://github.com/Le-Gris/h-arc.git
   ```

2. **Install required packages**
   ```bash
   pip install langchain-openai dotenv tqdm numpy pandas
   ```

3. **Setup API Keys**
   - Create a `.env` file in the project root.
   - Add your OpenRouter API key:
     ```
     OPENROUTER_API_KEY="your_api_key_here"
     ```

4. **Run Evaluation**
   ```bash
   python main.py
   ```

---

## Project Structure

| File | Purpose |
|:-----|:--------|
| `main.py` | Orchestrates the evaluation pipeline across tasks. |
| `solution_base.py` | Baseline simple solution using human explanations directly. |
| `solution_code_gen.py` | Full pipeline: hypothesis synthesis ➔ code generation ➔ feedback refinement. |
| `eval_code.py` | Evaluates and tests the generated code. |
| `prompts.py` | Stores and formats prompts for hypothesis and code generation. |
| `H_arc_paper.pdf` | Project report detailing methodology, experiments, and results. |

---

## Key Innovations

- **Hypothesis-Driven Code Generation:** Inspired by human reasoning, not just direct code synthesis.
- **Iterative Feedback Loop:** Error-driven refinement mimicking human trial-and-error.
- **Asynchronous Execution:** Parallel evaluation to optimize performance.
- **Human Cognitive Integration:** Leveraging the H-ARC dataset to inject human-like reasoning capabilities.

---

## Future Directions

- Fine-tuning LLMs specifically on H-ARC data to improve hypothesis clarity.
- Integrating richer multi-modal inputs (e.g., state graphs).
- Exploring hierarchical reasoning strategies.
- Scaling up to larger evaluation sets with increased MAX_PROGRAMS.

---

## Acknowledgements

This work was completed as part of the **CCM Project - NYU Fall 2024**, by  
**Abhinay Krishna Bodi**, **Peter Skovorodnikov**, **Nikolas Prasinos**, and **Xinrui Hu**.

We are grateful to the developers of the ARC and H-ARC datasets, and to the broader research community pushing the boundaries of cognitive AI.

---
