# Modular CV Structure

This CV has been restructured for better maintainability and flexibility. Each section is now in its own file, making it easy to update content and customize the CV for different purposes.

## 📁 File Structure

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
└── sent/                   # Previously sent CVs
    ├── Fontas/
    └── Siavash Bigdeli/
```

## 🎯 Quick Start Guide

### To customize your CV:

1. **Edit `user-config.tex`** - This is your control center:
   - Change display modes for sections
   - Show/hide entire sections
   - Reorder sections

2. **Edit section content** - Modify files in `sections/` directory

3. **Edit LaTeX settings** - Modify `config.tex` (rarely needed)

## 🔧 User Configuration Options

### Display Modes

Control how each section appears by editing `user-config.tex`:

```latex
\renewcommand{\summarymode}{hybrid}    % Options: none, academic, academicshort, 
                                       %          industry, industryshort, 
                                       %          hybrid, hybridshort

\renewcommand{\skillsmode}{compact}    % Options: compact, expanded

\renewcommand{\projectmode}{bullet}    % Options: text, bullet

\renewcommand{\teachingmode}{expanded} % Options: supercompact, compact, expanded
```

### Show/Hide Sections

Toggle sections on or off:

```latex
\showheadertrue        % Show header
\showsummaryfalse      % Hide summary
\showeducationtrue     % Show education
% ... etc.
```

### Change Section Order

Reorder sections by modifying the `\rendersections` command in `user-config.tex`. Simply rearrange the `\input{sections/...}` commands to change the order.

Example:
```latex
\newcommand{\rendersections}{
    \ifshowheader
        \input{sections/header.tex}
    \fi
    
    \ifshowsummary
        \input{sections/summary.tex}
    \fi
    
    \ifshoweducation
        \input{sections/education.tex}
    \fi
    
    % ... continue with other sections in your desired order
}
```

## 📝 Editing Content

### To update a section:

1. Navigate to `sections/` directory
2. Open the relevant `.tex` file
3. Make your changes
4. Save and recompile `Master CV.tex`

### To add a new section:

1. Create a new file in `sections/` directory (e.g., `sections/new-section.tex`)
2. Add the section content using appropriate LaTeX commands
3. In `user-config.tex`:
   - Add a toggle: `\newif\ifshownewsection`
   - Enable it: `\shownewsectiontrue`
   - Add to `\rendersections`: 
     ```latex
     \ifshownewsection
         \input{sections/new-section.tex}
     \fi
     ```

## 🎨 Examples

### Example 1: Academic CV
```latex
\renewcommand{\summarymode}{academic}
\renewcommand{\skillsmode}{expanded}
\renewcommand{\projectmode}{text}
\renewcommand{\teachingmode}{expanded}
\showpersonalfalse  % Hide personal highlights for formal CV
```

### Example 2: Industry-focused CV
```latex
\renewcommand{\summarymode}{industry}
\renewcommand{\skillsmode}{compact}
\renewcommand{\projectmode}{bullet}
\renewcommand{\teachingmode}{compact}
\showdomainexpertisetrue
\showpublicationsfalse  % Hide publications for industry focus
```

### Example 3: Short CV for quick applications
```latex
\renewcommand{\summarymode}{hybridshort}
\renewcommand{\skillsmode}{compact}
\renewcommand{\projectmode}{text}
\renewcommand{\teachingmode}{supercompact}
\showprojectsfalse  % Hide some sections to keep it short
\showpersonalfalse
```

## 🔨 Compiling the CV

Compile `Master CV.tex` using your preferred LaTeX compiler:

```bash
pdflatex "Master CV.tex"
```

Or use your LaTeX editor's compile button.

## 📦 Benefits of This Structure

✅ **Maintainable**: Each section is in its own file - easy to find and edit
✅ **Flexible**: Quickly create different versions for different purposes
✅ **Organized**: Clear separation of configuration, content, and structure
✅ **Reusable**: Easy to reuse sections across different CV versions
✅ **Version Control Friendly**: Git diffs are cleaner with separate files

## 🆘 Troubleshooting

**Issue**: CV doesn't compile
- Check that all paths in `\input{}` commands are correct
- Ensure all section files exist in the `sections/` directory

**Issue**: Section not appearing
- Verify the section toggle is set to `true` in `user-config.tex`
- Check that the section is included in `\rendersections`

**Issue**: Mode changes not taking effect
- Make sure you're using `\renewcommand` not `\newcommand` to change modes
- Check spelling of mode values (they're case-sensitive)

## 📚 Additional Notes

- The original `Master CV.tex` has been restructured but maintains all original content
- All formatting and styling is preserved in `config.tex`
- Personal information can be updated in `sections/header.tex`
