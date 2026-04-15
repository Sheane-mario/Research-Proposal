# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a LaTeX research proposal document for SCS 3216 (Research Methods) at the University of Colombo School of Computing. The paper is titled **"Towards a Multidimensional Composite Quality Index for AI-Generated Codebases"** by S.M. Silva, Praneesh S., and R.M.I.M. de Silva.

## Build Commands

The project uses **VS Code LaTeX Workshop** with a custom build pipeline configured in [.vscode/settings.json](.vscode/settings.json). The build sequence is:

```
pdflatex → biber → pdflatex → pdflatex
```

All output files go to the `Build/` directory. The PDF auto-builds on save when using VS Code with the LaTeX Workshop extension.

To build manually from the command line:
```bash
pdflatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=Build main.tex
biber --output-directory=Build main
pdflatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=Build main.tex
pdflatex -synctex=1 -interaction=nonstopmode -file-line-error -output-directory=Build main.tex
```

## Document Structure

[main.tex](main.tex) is the root file. It sets up formatting (12pt, A4, 1.5 line spacing, 1.5in left / 1in right margins) and inputs section files in order:

| Chapter | File |
|---------|------|
| Front matter (title page) | [sections/frontmatter.tex](sections/frontmatter.tex) |
| List of Acronyms | inline in `main.tex` |
| 1. Introduction | [sections/intro.tex](sections/intro.tex) |
| 2. Problem Statement and Justification | [sections/problem_statement.tex](sections/problem_statement.tex) |
| 3. Research Aims, Questions, and Objectives | [sections/research_aims_questions_objectives.tex](sections/research_aims_questions_objectives.tex) |
| 4. Evaluation Methods and Data Requirements | [sections/evaluation_data_requirements.tex](sections/evaluation_data_requirements.tex) |
| 5. Conclusion | [sections/conclusion.tex](sections/conclusion.tex) |

Bibliography is stored in [references.bib](references.bib) and compiled with **biblatex + biber** using Harvard (authoryear) style. Citations use `\parencite{}`, `\textcite{}`, or `\autocite{}`.

The document uses a graceful fallback for environments missing `biblatex` or `acronym` packages, so it can compile on minimal TeX installations.

## Key Formatting Constraints

- Margins: 1.5in left, 1in right, 1.5in top, 1in bottom (enforce these — do not change)
- Line spacing: 1.5 (`\baselinestretch`)
- Font size: 12pt
- Document class: `report` (uses `\chapter` not `\section` at top level)
- The university logo `ucsc.png` must remain in the project root alongside `main.tex`
