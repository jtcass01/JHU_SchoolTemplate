<!--
*** REFERENCE: https://github.com/othneildrew/Best-README-Template
***
*** After copying this template into a new class repository, search and
*** replace the following placeholders:
***
***   github_username, repo_name, class_name, class_code, project_description
-->

<!-- PROJECT HEADER -->
<br />
<p align="center">
  <a href="https://github.com/github_username/repo_name">
    <img src="Figures/JHU_WHITING_LOGO.png" alt="Johns Hopkins Whiting School of Engineering" width="620">
  </a>
</p>

<p align="center">
  <img src="Figures/Johns_Hopkins_Blue_Jays.svg" alt="Johns Hopkins Blue Jays" height="120">
</p>

<h1 align="center">class_name</h1>

<p align="center">
  <strong>class_code</strong>
  <br />
  Johns Hopkins University &middot; Engineering for Professionals
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Documents-LaTeX-68ACE5?style=for-the-badge&labelColor=002D72" alt="LaTeX">
  <img src="https://img.shields.io/badge/Build-pdflatex%20%2B%20bibtex-68ACE5?style=for-the-badge&labelColor=002D72" alt="Build">
  <img src="https://img.shields.io/badge/Lint-pre--commit-68ACE5?style=for-the-badge&labelColor=002D72" alt="Lint">
  <img src="https://img.shields.io/badge/License-GPL--3.0-68ACE5?style=for-the-badge&labelColor=002D72" alt="License">
</p>

<p align="center">
  <a href="https://github.com/github_username/repo_name"><strong>Explore the Repository »</strong></a>
  &middot;
  <a href="https://github.com/github_username/repo_name/issues">Report Bug</a>
</p>

---

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li><a href="#class-description">Class Description</a></li>
    <li><a href="#whats-inside">What's Inside</a></li>
    <li><a href="#writing-an-assignment">Writing an Assignment</a></li>
    <li><a href="#code-quality-tooling">Code Quality Tooling</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

---

## Class Description

project_description

---

## What's Inside

```
HW/Template/          starting point for a homework assignment
Exams/Template/       starting point for an exam
Figures/              JHU marks shared across the repository
```

Each template directory is **self-contained** — copy the whole folder and it
builds on its own:

| File | Purpose |
|------|---------|
| `jhu.sty` | The document style: JHU brand palette, branded title page, running header naming the current section, and a footer with the page count. |
| `*.tex` | The root document. Sets the title, author, and course, then pulls in each answer. |
| `sections/` | One file per problem, pulled in with `\input`. Keeps a long assignment navigable. |
| `build.ps1` | Builds the PDF and reports warnings. |
| `ref.bib` | Bibliography entries (homework template only). |
| `Figures/` | Logos used by the title page and footer. |

`jhu.sty` is duplicated in both template directories rather than shared from
the repository root. That is deliberate: copying one folder into a new class
repository is all it takes to get started.

---

## Writing an Assignment

**1. Copy a template** into your class repository and rename the `.tex` for
the assignment.

**2. Fill in the fields** at the top of the `.tex`:

```latex
\renewcommand{\jhuTitle}{Gesture Recognition System}
\renewcommand{\jhuDocType}{Final Exam}
\renewcommand{\jhuAuthor}{YOUR-NAME}
\renewcommand{\jhuCourse}{CLASS-NUMBER: YOUR-CLASS}
\renewcommand{\jhuRunningHead}{CLASS-NUMBER Exam}
```

**3. Write each answer** in its own file under `sections/`, adding a matching
`\section` and `\input` to the root document.

**4. Build:**

```powershell
.\build.ps1            # build, then report warnings
.\build.ps1 -Clean     # delete aux files first
.\build.ps1 -Quiet     # suppress the warning report
```

The script runs the `pdflatex` → `bibtex` → `pdflatex` → `pdflatex` sequence
directly rather than through `latexmk`, which needs Perl. It finds the root
`.tex` by looking for `\documentclass`, so renaming the file does not mean
editing the script.

> **Requires MiKTeX** at `%LOCALAPPDATA%\Programs\MiKTeX`. The script checks
> for `pdflatex.exe` there and stops with a clear message if it is missing.

---

## Code Quality Tooling

| Tool | Config | Applies to |
|------|--------|------------|
| [pre-commit](https://pre-commit.com/) | `.pre-commit-config.yaml` | Trailing whitespace, end-of-file fixes, YAML validation, and stray debug statements |
| [prospector](https://prospector.landscape.io/) | `.prospector.yaml` | Python linting, run as a pre-commit hook |
| [clang-format](https://clang.llvm.org/docs/ClangFormat.html) | `.clang-format` | C and C++ sources |

Install the hooks once per clone:

```bash
pre-commit install
```

Format C and C++ sources in place:

```bash
./run_clang.sh
```

---

## License

Distributed under the GNU General Public License v3.0. See [`LICENSE`](LICENSE)
for details.
