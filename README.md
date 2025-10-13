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

### Section Order and Visibility

Reorder or hide sections by editing the `\rendersections` command in `user-config.tex`: rearrange the `\input{sections/...}` commands to change their order, or comment out a line to hide a section.

## 🧩 Adding New Sections

1. Create a new file in `sections/` (e.g., `sections/new-section.tex`)
2. In `user-config.tex`, add the following to `\rendersections`:
    ```latex
    \input{sections/new-section.tex}
    ```

## 📄 License

Personal CV project.
