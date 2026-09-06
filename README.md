# Auto Paper Figure Skill / 科研论文插图自动绘制 Skill

A reusable GitHub-ready skill for **automatically generating paper overview / method / system figures** from a real codebase and local paper references.

这是一个可直接放到 GitHub 的 skill 项目，目标是：**先理解真实项目实现，再自动生成 ACL / EMNLP 风格的科研论文图片**，尤其适用于 overview figure、method figure、system figure，以及包含 **LLM harness、training pipeline、核心模块与关键公式** 的论文图。

---

## What this repo contains / 仓库内容

- **An optimized general prompt** distilled from a real successful workflow, with project-specific details removed.
- **Chinese and English skill versions** that can be used as reusable instruction files.
- **A README template and usage guide** for turning the skill into a portable GitHub project.
- **A reference image** showing the desired visual direction.

---

## Target capability / 目标能力

This skill is designed for the following workflow:

1. **Read the implementation first** rather than hallucinating a pipeline.
2. **Identify the true method narrative**, especially the harness and training flow.
3. **Inspect local reference papers** and imitate their *design language* rather than copying their content.
4. **Draw figures in an ACL/EMNLP-style scientific illustration aesthetic**:
   - fewer words
   - clear hierarchy
   - less like a generic flowchart
   - light comic / hand-drawn module styling
   - preserve key technical details when necessary
5. **Export editable and publication-friendly outputs**, ideally SVG + PDF, plus PNG previews.

---

## Reference figure / 参考风格图

Below is the reference image included in this repo:

![Reference overview figure](assets/reference_overview_example.png)

---

## Repository structure / 目录结构

```text
paper-overview-figures-skill/
├── README.md
├── .gitignore
├── LICENSE
├── assets/
│   └── reference_overview_example.png
├── prompts/
│   ├── optimized_general_prompt_zh.md
│   └── optimized_general_prompt_en.md
├── skills/
│   ├── paper_overview_figures_skill_zh.md
│   └── paper_overview_figures_skill_en.md
├── examples/
│   ├── example_usage_zh.md
│   └── example_usage_en.md
└── docs/
    └── repo_notes.md
```

---

## Recommended usage / 推荐使用方式

### Option A: use the optimized prompt directly / 直接使用优化后的 prompt

Use the prompt under `prompts/` when you want an agent to inspect a project and generate a paper overview figure.

适合你已经有自己的 agent / coding assistant / skill runtime，只需要一份高质量通用 prompt 的情况。

### Option B: use the skill files / 使用 skill 文件

Use the `skills/` files when your environment supports skill-style reusable instruction documents.

适合你希望把这个能力封装成长期复用的“画科研图 skill”的情况。

---

## Design principles / 设计原则

### 1) Accuracy first / 科学准确性优先

The figure should reflect the **actual implementation**, not a guessed workflow.

### 2) Narrative over call graph / 方法叙事优先于代码调用链

The goal is not to dump boxes and arrows, but to tell the paper story.

### 3) Minimal text, not minimal meaning / 少文字，不少信息

Remove redundant explanation, but keep the details that define the method.

### 4) Scientific illustration, not business flowchart / 做科研图，不做业务流程图

Prefer structured scientific illustration with visual metaphors, grouped modules, and focused emphasis.

### 5) Controlled hand-drawn aesthetics / 克制的手绘感

Use light comic / hand-drawn styling to make the figure more natural, without reducing readability.

---

## Files you will likely edit / 你最可能修改的文件

- `prompts/optimized_general_prompt_zh.md`
  General Chinese prompt distilled from the original real usage.
- `prompts/optimized_general_prompt_en.md`
  English counterpart.
- `skills/paper_overview_figures_skill_zh.md`
  Chinese reusable skill.
- `skills/paper_overview_figures_skill_en.md`
  English reusable skill.

---

## Suggested downstream outputs / 建议下游输出

When this skill is used on a project, a good default deliverable set is:

- `figure/overview_en.pdf`
- `figure/overview_zh.pdf`
- `figure/overview_en.svg`
- `figure/overview_zh.svg`
- `figure/overview_en.png`
- `figure/overview_zh.png`
- `figure/src/` for editable sources or generation scripts
- `figure/README.md` documenting evidence, design choices, and export steps

---

## Example request summary / 示例请求概括

A typical request looks like this:

- Read my project implementation.
- Focus on the LLM harness and training pipeline.
- Draw an ACL/EMNLP-style overview figure.
- Reduce flowchart feel, reduce text density.
- Use light comic-style modules.
- Restore necessary technical details and formulas in key modules.
- Add a natural hand-drawn touch.
- Export PDF/SVG/PNG and keep editable sources.

---

## License / 许可

This repository is packaged with an MIT license for convenient reuse.

---

## Notes / 说明

This repo contains **prompts and skill files**, not a fixed rendering engine. It is intended to be plugged into an agentic workflow that can read project files, inspect local paper PDFs, and generate figures.

这个仓库主要提供的是 **prompt / skill 资产**，并不绑定某一个固定绘图引擎；它更适合接入一个能够读取项目代码、查看本地论文并生成图片的 agent 工作流。
