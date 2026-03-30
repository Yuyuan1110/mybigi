---
tags: 
  - Utils
  - LaTeX
  - typesetting
  - document
alias: []
created: 2025-08-01
updated: 2025-09-25
source:
---

# `LaTeX` Advanced Usage

This note covers more advanced LaTeX features. For a basic introduction, see [[LaTeX]].

## Packages

LaTeX packages add new features and commands. You load them in the preamble (before `\begin{document}`) with `\usepackage{}`.

- **`graphicx`**: For including images.
- **`amsmath`**: For advanced mathematical formulas.
- **`geometry`**: For changing page margins.
- **`hyperref`**: For creating hyperlinks within the document.

### Example with Packages

```latex
\documentclass{article}

\usepackage{graphicx}
\usepackage{amsmath}
\usepackage[margin=1in]{geometry}

\begin{document}

\section{Including an Image}

\includegraphics[width=0.5\textwidth]{my_image.png}

\section{A Complex Equation}

The quadratic formula is given by:
\[ x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} \]

\end{document}
```

## Tables

Tables are created with the `tabular` environment.

```latex
\begin{tabular}{|l|c|r|}
\hline
Left & Center & Right \\
\hline
1 & 2 & 3 \\
4 & 5 & 6 \\
\hline
\end{tabular}
```

- **`{|l|c|r|}`**: Defines the columns (left-aligned, center-aligned, right-aligned) with vertical lines.
- **`\hline`**: Adds a horizontal line.
- **`&`**: Separates columns.
- **`\\`**: Starts a new row.

## Cross-Referencing

LaTeX can automatically number and reference sections, figures, and equations.

- **`\label{marker}`**: Creates a marker.
- **`\ref{marker}`**: References the marker.

### Example

```latex
\section{Introduction} \label{sec:intro}

As we will see in Section~\ref{sec:conclusion}, LaTeX is great.

\section{Conclusion} \label{sec:conclusion}

As mentioned in Section~\ref{sec:intro}, LaTeX is indeed great.
```

**Note:** You may need to compile the document twice for the references to appear correctly.
