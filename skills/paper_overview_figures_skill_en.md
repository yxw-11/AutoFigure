---
name: paper-overview-figures-en
description: >-
  Automatically generate or refine research-paper overview, method, and system figures
  from real project code and local reference papers. Prioritizes implementation-grounded
  understanding, ACL/EMNLP-style scientific illustration, reduced flowchart feel,
  necessary formulas, light hand-drawn/comic modules, bilingual outputs, and editable sources.
---

# Research Paper Figure Generation Skill (English)

## Core Objective

You are **not** simply converting code into a flowchart. You are turning the **real method** into a publication-quality scientific figure.

Priority order:

**Scientific accuracy > key mechanism completeness > readability > visual simplicity > decoration**

## Default Inputs

- `project_root`: project root directory; use the current working directory if not specified.
- `references_dir`: default `<project_root>/papers`.
- `output_dir`: default `<project_root>/figure`; create it if it does not exist.
- `focus`: prioritize the LLM harness, inference flow, and training pipeline; if they do not exist, focus on the real core method.
- `languages`: by default generate both English and Chinese versions.

Respect explicit user overrides for paths, focus modules, and output formats. If the project is incomplete, inaccessible, or lacks paper references, state the limitation clearly instead of pretending you inspected them.

## 1. Read the implementation and build evidence

Read the README, entry scripts, key modules, configs, training code, and—when necessary—tests, logs, or examples. Only inspect what is needed for understanding and drawing; do not launch full training or alter business logic.

Verify at least the following:

- the real inputs and outputs of the system
- whether an LLM harness exists, and if so: prompt/context construction, model calls, action parsing, tool/environment execution, feedback, validation, and stopping conditions
- whether a training pipeline exists, and if so: data source, preprocessing, supervision or reward signal, objective, parameter updates, and how the trained model is later used at inference time
- which modules are actual method contributions versus generic engineering utilities

Create lightweight evidence notes for key modules, key links, and core formulas, e.g. `path: function/class/config`. Distinguish between “confirmed in code,” “documented,” and “inferred.” Do not present unverified mechanisms as facts in the final figure.

## 2. Learn the visual language of reference papers

Inspect relevant overview / method / system figures in `references_dir`, and record what to borrow:

- overall layout
- information hierarchy
- text density
- color and line style
- icons / visual metaphors
- formula placement
- how key modules are emphasized

Borrow the **design language**, not the reference paper’s method content, and do not copy whole figures.

## 3. Decide the main visual narrative

First summarize the method in one or two sentences, then determine:

1. the 1–3 most important contributions;
2. the list of details that must not be lost;
3. which modules should be expanded versus compressed.

Organize the information in three levels:

- **global level**: the full method story
- **mechanism level**: the most important 1–2 modules
- **detail level**: necessary formulas, scoring functions, objectives, intermediate representations, or micro-examples

Remove redundant engineering detail, repeated labels, and paragraph-style explanation—but do not remove the mechanisms that make the method distinctive.

## 4. Draw an ACL / EMNLP-style scientific figure

Target style:

- clean, readable, and concise
- low text density
- less like a generic business flowchart
- more like a scientific illustration in a paper
- small modules shown in a lightweight comic / illustrative style where appropriate
- the overall figure may include a restrained hand-drawn touch

Recommended practices:

- use spatial grouping to express stages, instead of placing everything inside same-sized boxes
- use icons, object interactions, state cards, trajectory snippets, or compact visual metaphors to replace excessive text
- keep only the arrows needed to explain data flow, control flow, or parameter updates
- clearly emphasize the core contribution modules with more space, clearer boundaries, or stronger focus
- keep the background simple, the palette restrained, and the whitespace sufficient

The hand-drawn touch should only enhance naturalness; it must not harm the clarity of formulas, labels, arrows, or logic.

## 5. Preserve necessary formulas and computations in key modules

Only add technical detail where it helps explain the main mechanism, such as:

- core scoring functions
- objective functions
- aggregation rules
- policy update rules
- important intermediate variables

Principles:

- formulas should serve explanation, not be evenly spread across every module
- symbols must stay consistent with the implementation
- if evidence is missing, prefer accurate textual description instead of inventing equations
- never conflate training signals, execution feedback, and parameter updates

## 6. Bilingual outputs and editable deliverables

By default, generate:

- `overview_en.pdf`, `overview_zh.pdf`
- `overview_en.svg`, `overview_zh.svg`
- `overview_en.png`, `overview_zh.png`
- `src/`: scripts, source graphics, label tables, or export notes
- `README.md`: method summary, code evidence, style references, retained key details, and export steps

The two language versions should ideally share:

- layout
- module numbering
- colors
- icons
- arrows
- math notation

Minor line-breaking or label-length adjustments are allowed for typography, but do not change the structure or information content.

## 7. Check and iterate

Check at least three categories:

1. **scientific content**: is it faithful to the code evidence; are any key modules wrongly added or omitted?
2. **visual expression**: is it clean, clear, and focused; has the flowchart feel been reduced?
3. **export quality**: are the bilingual versions consistent; do fonts render correctly; are PDF / SVG / PNG usable?

Typical user feedback should be handled as follows:

- “Too much like a flowchart”: change the composition and module depiction; reduce mechanical boxes while preserving logic.
- “Too much text”: compress labels and use icons or captions, but do not erase the core mechanism.
- “Important details were lost”: restore formulas, core computations, or intermediate states in key modules without cluttering the entire figure.
- “Make it more natural”: strengthen the light hand-drawn contours and decorative cues while preserving scientific readability.

## 8. Final delivery

In the final response, provide:

- actual generated file paths
- the main visual narrative of the figure
- the emphasized modules
- the preserved core formulas / computations
- the completed verification items
- any remaining points that may need manual polishing
