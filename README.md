# Modular CV

A modular LaTeX-based CV system with flexible configuration and customizable sections.

## 📁 Structure

```
CV/
├── Master CV.tex           # Main file - orchestrates everything
├── config.tex              # LaTeX configuration (packages, settings, environments)
├── user-config.tex         # Control center (modes, section order, visibility)
├── sections/               # Individual section files
│   ├── header.tex
│   ├── summary.tex
│   ├── education.tex
│   ├── domain-expertise.tex
│   ├── skills.tex
│   ├── publications.tex
│   ├── projects.tex
│   ├── teaching.tex
│   ├── achievements.tex
│   └── personal.tex
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

Edit `user-config.tex` to control how sections appear:

```latex
\renewcommand{\summarymode}{hybrid}     % none, academic, academicshort, 
                                        % industry, industryshort, 
                                        % hybrid, hybridshort

\renewcommand{\skillsmode}{compact}     % compact, expanded
\renewcommand{\projectmode}{bullet}     % text, bullet
\renewcommand{\teachingmode}{expanded}  % supercompact, compact, expanded
```

### Section Visibility

Toggle sections on/off:

```latex
\showheadertrue        % Show header
\showsummaryfalse      % Hide summary
\showeducationtrue     % Show education
```

### Section Order

Reorder sections by rearranging the `\input{sections/...}` commands in the `\rendersections` command within `user-config.tex`.

## 📝 Examples

**Academic CV:**
```latex
\renewcommand{\summarymode}{academic}
\renewcommand{\skillsmode}{expanded}
\renewcommand{\projectmode}{text}
\renewcommand{\teachingmode}{expanded}
```

**Industry-focused CV:**
```latex
\renewcommand{\summarymode}{industry}
\renewcommand{\skillsmode}{compact}
\renewcommand{\projectmode}{bullet}
\showpublicationsfalse
```

**Short CV:**
```latex
\renewcommand{\summarymode}{hybridshort}
\renewcommand{\skillsmode}{compact}
\renewcommand{\teachingmode}{supercompact}
\showprojectsfalse
\showpersonalfalse
```

## 🧩 Adding New Sections

1. Create a new file in `sections/` (e.g., `sections/new-section.tex`)
2. In `user-config.tex`:
   - Add a toggle: `\newif\ifshownewsection`
   - Enable it: `\shownewsectiontrue`
   - Add to `\rendersections`:
     ```latex
     \ifshownewsection
         \input{sections/new-section.tex}
     \fi
     ```

## 📄 License

Personal CV project.
