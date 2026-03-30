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

# `LaTeX` Note

LaTeX is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. LaTeX is the de facto standard for the communication and publication of scientific documents.

For more advanced usage, see [[LaTeX_advanced]].

## Basic Document Structure

A minimal LaTeX document has the following structure:

```latex
\documentclass{article}

\title{My First LaTeX Document}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle

Hello, world!

\end{document}
```

- **`\documentclass{article}`**: Specifies the type of document.
- **`\title`, `\author`, `\date`**: Define the title, author, and date.
- **`\begin{document}` ... `\end{document}`**: The main content of the document.
- **`\maketitle`**: Displays the title, author, and date.

## Compiling a Document

To create a PDF from a `.tex` file, you use a LaTeX compiler like `pdflatex`.

```bash
# Compile my_document.tex into my_document.pdf
pdflatex my_document.tex
```

## Basic Formatting

- **Sections**: `\section{}`, `\subsection{}`, `\subsubsection{}`
- **Text Styles**: `\textbf{bold}`, `\textit{italic}`, `\underline{underline}`
- **Lists**:
  - **Unordered**: `\begin{itemize} ... \end{itemize}` with `\item` for each entry.
  - **Ordered**: `\begin{enumerate} ... \end{enumerate}` with `\item` for each entry.

### Example

```latex
\documentclass{article}

\begin{document}

\section{Introduction}
This is the first section.

\subsection{A Subsection}
This is a subsection with a list.

\begin{itemize}
  \item An item.
  \item Another item.
\end{itemize}

\end{document}
```