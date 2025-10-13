# Modular CV

A modular LaTeX-based CV system with flexible configuration and customizable sections.

## 📁 Structure

```
CV/
├── Master CV.tex           # Main file - orchestrates everything
├── config.tex              # LaTeX configuration (packages, settings, environments)
├── user-config.tex         # Control center (modes, section order, visibility)
├── sections/               # Individual section files
└── sent/                   # Archive of previously sent CVs
```

## 🚀 Quick Start

1. **Edit content**: Modify files in the `sections/` directory
2. **Configure display**: Adjust settings in `user-config.tex`
3. **Compile**: Run LaTeX on `Master CV.tex`

```bash
pdflatex "Master CV.tex"
```

## ⚙️ Configuration

### Display Modes

Edit `user-config.tex` to control how sections appear.

### Section Selection

Define which sections to include and their order in `user-config.tex`:

```latex
\newcommand{\rendersections}{
    \input{sections/header.tex}
    \input{sections/projects.tex}
    \input{sections/education.tex}
}
```

### Project Selection

Control which projects appear in the "Selected Projects" section and their order through `user-config.tex`:

```latex
\newcommand{\selectedprojects}{
    edgemark,
    cavitation,
    dlcoding
}
```

## 🌱 Adding New Sections

1. Create a new file in `sections/` (e.g., `sections/new-section.tex`)
2. In `user-config.tex`, add a new `\input` line to `\rendersections`

## 🧩 Adding New Projects

1. In `sections/projects.tex`:
    - Add the project content inside `\newcommand{\projectnewproject}{...}` following the existing format.
    - Register it in `\renderproject` inside a `\ifstrequal` line.
2. In `user-config.tex`, add the project name to the `\selectedprojects` list.

## 📄 License

Personal CV project.
