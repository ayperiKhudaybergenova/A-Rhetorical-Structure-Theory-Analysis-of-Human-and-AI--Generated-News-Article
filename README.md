# A-Rhetorical-Structure-Theory-Analysis-of-Human-and-AI--Generated-News-Article

https://www.bbc.com/news/articles/cqlxvvw06pqo

This repository contains a Rhetorical Structure Theory (RST) discourse analysis comparing an original news article from the BBC with an AI-generated version. The project examines how AI text generators alter discourse hierarchy, sentence length, and rhetorical relations compared to human journalism.

---

## 🛠 Generation Metadata

* **AI Model & Version:** Anthropic Claude (Latest Version: `Claude 3.5 Sonnet` / `Claude 3 Opus` — *specify exact model used*)
* **Generation Purpose:** To evaluate rhetorical structure shifts, sentence expansion, and discourse tree variations between human-authored and LLM-generated text.

---

## 📝 Prompting Strategy & Methodology

For details on the exact prompts used to produce the target text, please refer to the [Prompts Section](#-prompts-used) below.

### Generation Techniques Applied
* **Zero-Shot / Few-Shot Contextual Prompting:** Providing source themes and stylistic constraints to test discourse cohesion.
* **Structural Framing:** Explicitly asking the model to expand upon scientific background, anecdotal herder accounts, and physiological mechanisms.

---

## 🔍 Prompts Used

> **Generation Prompt**
> *"Rewrite/expand the article regarding extreme heat impacts on camels in Africa, incorporating background explanations, scientific data, and pastoralist testimonies."*

*(For the complete step-by-step prompt chain, see the `prompts/` directory in this repository.)*

---

## 💡 Why RST Analysis Matters (Original vs. Generated Text)

Rhetorical Structure Theory (RST) breaks text down into Elementary Discourse Units (EDUs) and categorizes their relationships (e.g., *Nucleus* vs. *Satellite*, *Elaboration*, *Evidence*, *Cause*). Analyzing generated text with RST is important because:

1. **Discourse Hierarchy Inspection:** It reveals whether LLMs maintain logical macro-structures or simply append verbose, redundant clauses.
2. **Cohesion & Coherence Evaluation:** It highlights how AI transitions between main thesis points (Nuclei) and supporting details (Satellites).
3. **Stylistic Shift Identification:** It proves how AI text expansion impacts readability and information density.

---

## 📊 Results & Early Findings

> **Note:** The full experimental evaluation and data tables are currently under development. Detailed RST trees and metrics can be found in the accompanying term paper uploaded to this repository.

### Key Observations So Far

1. **Sentence Expansion & Verbosity:**
   * **Observation:** The AI-generated version consistently produces longer, more complex sentence structures.
   * **Meaning:** Concise facts that are stated simply in the original human text are often expanded into multi-clause sentences by the AI, even when adding minimal new information.

2. **RST Structural Comparison Example:**

   * **Original BBC Article (Concise Structure):**
     > *"Within the past one month I have lost eight camel calves because of the extreme heat, it has become much more intense and difficult."*
     * **RST Structure:** Direct `EVIDENCE` / `CAUSE` relation embedded directly within a single quote unit.

   * **AI-Generated Article (Expanded Structure):**
     > *"Nur said he lost four camels during the drought that struck the region between 2020 and 2023, one of the worst in the Horn of Africa in four decades. Two died of dehydration after a longer trek to a water point that had itself begun to dry up."*
     * **RST Structure:** Split into a multi-tiered `ELABORATION` chain with subordinate `BACKGROUND` and `RESULT` satellites attached to a central narrative nucleus.

---

## 📖 Methodology & Full Term Paper

The complete RST discourse parsing methodology, annotation guidelines, and full tree diagrams are detailed in the term paper uploaded to this repository:

* 📄 **Term Paper:** `docs/RST_Analysis_Term_Paper.pdf` *(or see repository root)*

### How to Reproduce or Locate This Analysis Method
If you wish to apply this RST framework to your own comparative text analyses:
1. Refer to the **Mann & Thompson (1988)** Rhetorical Structure Theory framework.
2. Use the **Macro-EDU Segmentation Technique** outlined in `docs/RST_Analysis_Term_Paper.pdf` to group text into functional discourse blocks (Preparation, Evidence, Causality, Consequence, Synthesis).
3. Compare `Nucleus-Satellite` ratios between human news writing and LLM outputs.

---

## 📜 Copyright & Usage Rights

**© [Your Name / Your Organization], 2026. All Rights Reserved.**

* **Original Text Attribution:** The original article excerpt is property of the BBC / Navin Singh Khadka.
* **Analysis & Code License:** The RST annotations, methodology, and comparative framework created in this repository are open for academic research and educational purposes. If you extend or build upon this research, please attribute this repository.
