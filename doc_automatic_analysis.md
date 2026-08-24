# Automatic RST Analysis — Pre-Manual Annotation Stage

Before carrying out the manual Rhetorical Structure Theory (RST) analysis, I created an initial **automatic RST analysis** to organize the texts and identify possible rhetorical relations. The purpose of this stage was not to produce a final expert RST annotation, but to generate a preliminary structure that could later be inspected and corrected manually.

## Text Cleaning and Preparation

The original text files first needed to be cleaned before automatic analysis. The raw material contained formatting elements that were not part of the actual discourse analysis, including Markdown headings such as `##`, unnecessary blank lines, inconsistent whitespace, and some places where sentences or quotations were joined together without clear separation. I removed unnecessary formatting, stripped extra whitespace, removed empty units, and divided the text into individual text units. The cleaned units were then organized into a structured dataframe with a `Unit_ID` and `Text` column.

This cleaning step was necessary because automatic RST classification operates on textual units. If headings, empty lines, or formatting artefacts are treated as normal units, they can receive incorrect rhetorical classifications and affect the resulting analysis.

## Automatic RST Approach

The automatic analysis uses a **rule-based RST approach** rather than a fully trained RST parser. Automatic RST analysis means using computational methods to identify possible discourse relations and structural roles in a text without manually annotating every relation first. In this project, the system uses linguistic keywords and phrases as indicators of possible rhetorical relations.

The method assigns two main RST roles:

- **Nucleus** — the more central information in a rhetorical relation.
- **Satellite** — supporting information that provides evidence, explanation, background, cause, or other additional information.

The system also assigns a possible rhetorical relation to each unit. The main relations used in this first-pass analysis are **Evidence, Cause, Contrast, Background, and Elaboration**.

## Rule-Based Classification

The classification was implemented using Python and the **pandas** package for dataframe processing. The text of each unit was converted to lowercase so that keyword matching was not affected by capitalization.

The system searches for linguistic signals associated with different rhetorical relations.

For **Evidence**, it searches for terms such as:

`study`, `research`, `scientists`, `veterinarians`, `experts`, `analysis`, `report`, `published`, `data`, `researcher`, and `according to`.

For **Cause**, it searches for expressions such as:

`because of`, `as a result`, `cause behind`, `due to`, `causing`, `leads to`, `affected by`, and `resulting in`.

For **Contrast**, it searches for terms such as:

`but`, `however`, `although`, `while`, and `yet`.

For **Background**, it searches for contextual and geographical terms such as:

`region`, `Africa`, `Ethiopia`, `Somalia`, `Kenya`, `North Africa`, `Sahara`, and `Sahel`.

If none of these rules are triggered, the unit is assigned **Elaboration** as a default relation.

## Rule Priority

The rules are applied in a fixed order:

**Evidence → Cause → Contrast → Background → Elaboration**

This was important because a sentence can contain signals for more than one possible relation. The first matching rule determines the automatic classification. Therefore, the result represents the strongest lexical signal identified by the system rather than a complete interpretation of the discourse structure.

## Confidence Scores

A simple confidence value was also assigned to each classification:

| Relation | Confidence |
|---|---:|
| Evidence | 0.80 |
| Cause | 0.75 |
| Contrast | 0.70 |
| Background | 0.65 |
| Elaboration | 0.50 |

These values are **rule-based confidence scores**, not statistical probabilities. They indicate how strongly the implemented rule matched the text.

## Problems Encountered

The main difficulty was that RST relations cannot always be identified reliably from individual keywords. A word such as `but` can indicate contrast, but its presence alone does not guarantee that the complete unit represents an RST Contrast relation. Similarly, the presence of `study` or `research` suggests Evidence, but the sentence may have another rhetorical function depending on the surrounding discourse.

Another problem was the distinction between **textual cleaning** and **rhetorical segmentation**. Removing formatting and empty lines is relatively straightforward, but deciding exactly where one meaningful rhetorical unit ends and another begins requires linguistic and contextual judgement.

The automatic method therefore provides a **first-pass annotation**, not a final RST tree. This is why the output will be reviewed manually afterwards. The automatic results provide a structured starting point and help identify possible Nucleus/Satellite roles and relations before the detailed manual analysis.

## Packages and Techniques

The main computational tool used for this stage was **pandas**, which was used to structure the text, create the analysis dataframe, add the RST classification columns, and export the results.

Python's built-in text-processing functionality was used for reading, cleaning, splitting, and writing the text. The final results were exported as **CSV** for structured data analysis and **Markdown** for readable inspection and documentation.

No pretrained RST parser or machine-learning RST model was used at this stage. The current system is a **custom rule-based automatic RST classifier** based on lexical and phrase-level indicators.

## Results Created So Far

The automatic analysis produced structured files containing:

- `Unit_ID`
- `Text`
- `Role`
- `Relation`
- `Confidence`

The results are available in both **CSV** and **Markdown** formats. These files should be inspected alongside the original cleaned text because the purpose of this stage is to provide an initial automatic annotation that can be checked, corrected, and refined during the subsequent manual RST analysis.

The automatic RST output should therefore be understood as a **pre-analysis layer**: it reduces the amount of initial manual work, highlights possible rhetorical relations, and provides a consistent starting point for the final human interpretation.
