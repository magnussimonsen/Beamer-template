# Beamer $\LaTeX$ Teaching Template

## Preview

[Abstract Linear Algebra PDF](Abstract-Linear-Algebra.pdf)

[Special Relativity Norwegian High School PDF](Special-Relativity-Norwegian-High-School.pdf)

[Italian Pronunciation PDF](Italian-Pronunciation.pdf)

[French Pronunciation PDF](French-Pronunciation.pdf)

This repository contains a Beamer template for teaching mathematics, physics, and languages. It uses a minimalist theme-less Beamer layout with:

- **Custom color palette**: `myblue`, `myred`, `mygreen`, `mycyan`, `mygray`  
- **Header macros**: `\blueheader`, `\redheader`, `\greenheader`, `\cyanheader`, `\grayheader`  
- **tcolorbox theorem environments**: `bluebox` (Definition), `redbox` (Theorem), `greenbox` (Example), `cyanbox` (Exercise), `graybox` (Explore)  
- **tcolorbox focus environments**: frameless highlight boxes — `bluefocus`, `redfocus`, `greenfocus`, `cyanfocus`, `grayfocus`  
- **Clean layout**: frame numbers visible, navigation symbols hidden, custom `\faAngleRight` bullets  
- **Default font**: Comic Neue (`comicneue`), with several alternatives commented out  
- **Handout mode**: `handout` option in `\documentclass` enabled by default; optional 2-up / 4-up layout via `pgfpages`  
- **Utility macros**: `\warn`, `\warnCustomMsg[color]{msg}`, `\info`, `\infoCustomMsg[color]{msg}`  
- **Math macros**: `\norm{}`, `\abs{}` for vectors and absolute values  
- **IPA support**: via `tipa` (pdfLaTeX) or Unicode IPA (XeLaTeX/LuaLaTeX)

---

## Features

### 1) Colored headers per frame
```latex
\blueheader
\begin{frame}{Topic title}
Bullet 1
\end{frame}
```

### 2) Theorem-like boxes with matching colors

Environments: `bluebox` (Definition), `redbox` (Theorem), `greenbox` (Example), `cyanbox` (Exercise), `graybox` (Explore).  
Syntax: `\begin{<env>}{Title}{label}`

```latex
\begin{redbox}{Rule}{lbl:rule}
State a key rule or takeaway here.
\end{redbox}

\begin{bluebox}{Definition}{lbl:def}
A formal definition here.
\end{bluebox}
```

### 3) Focus (highlight) boxes — no title, no frame

Use for soft highlights inside a frame.

```latex
\begin{bluefocus}
Highlighted fact in a soft blue background.
\end{bluefocus}

\begin{redfocus}
Highlighted warning in a soft red background.
\end{redfocus}
```

### 4) Info and warning callouts

`\warn` and `\info` use fixed default messages.  
`\warnCustomMsg` and `\infoCustomMsg` accept an optional color and a required message:

```latex
\warn                                          % "Not part of the syllabus" in red
\info                                          % "For your information" in blue
\warnCustomMsg[orange]{Not part of curriculum}
\infoCustomMsg[blue]{This helps but is not examinable.}
```

### 4) IPA in slides
With **pdfLaTeX** + `tipa`:
```latex
\textipa{[bO~]}   % e.g., French "bon"
\textipa{[tSe]}   % Italian "ce" as [t͡ʃe]
```
With **XeLaTeX/LuaLaTeX** + `fontspec`:
```latex
% In preamble:
\usepackage{fontspec}
\setmainfont{Doulos SIL} % or Charis SIL, Noto Serif

% In frames:
[ bɔ̃ ]   % type Unicode IPA directly
```

## Requirements

Core packages:
- `beamer` (Copenhagen theme), `tcolorbox`, `tikz`, `pgfplots`
- Math: `amsmath`, `amssymb`, `amsthm`
- Utilities: `hyperref`, `xcolor`, `siunitx`, `graphicx`, `minted` (optional), `tipa` (for IPA with pdfLaTeX)
- Icons: `fontawesome5` (for `\warn` and `\info` icons)

Optional:
- `minted` for code highlighting (requires `--shell-escape`)

---

## Build instructions

Choose one of these setups.

### Option A: pdfLaTeX + `tipa` (safe for IPA with `\textipa{}`)

Use when you want to stay on pdfLaTeX.

```bash
pdflatex -shell-escape main.tex   # needed if you use minted
pdflatex -shell-escape main.tex
```

Notes:
- `tipa` is already loaded in the template. Wrap IPA in `\textipa{...}`.
- If you do not use `minted`, you can omit `-shell-escape`.  

### Option B: XeLaTeX or LuaLaTeX + Unicode IPA

Use when you prefer to type real IPA characters.

Add to preamble:
```latex
\usepackage{fontspec}
\setmainfont{Doulos SIL} % or Charis SIL, Noto Serif
```

Build:
```bash
xelatex -shell-escape main.tex     # or lualatex
xelatex -shell-escape main.tex
```

Notes:
- Keep `-shell-escape` only if `minted` is enabled.
- Comment out `\usepackage[utf8]{inputenc}` when using XeLaTeX/LuaLaTeX.

---

## Quick start

```bash
git clone https://github.com/USERNAME/beamer-template.git
cd beamer-template
```

Open `main.tex`, toggle which modules to include:
```latex
% \include{Abstract-Linear-Algebra}
% \include{Italian-Pronunciation}
\include{French-Pronunciation}
```

Build using one of the options above.

---

## Repository structure (suggested)

```
.
├── preamble.tex             # theme, packages, colors, layout macros
├── main.tex                 # root file (loads preamble and includes chapters)
├── Abstract-Linear-Algebra.tex
├── Italian-Pronunciation.tex
├── French-Pronunciation.tex
├── focusbox-example.tex     # demo of focus and theorem boxes
├── latex-crash-course.tex   # optional LaTeX reference slides
├── figures/                 # images if needed
└── README.md
```

---

## Troubleshooting

- **Unicode or IPA errors with pdfLaTeX**  
  Use `\textipa{...}` and keep `\usepackage{tipa}`. Remove raw IPA symbols like `ɔ ɛ ʁ`.

- **minted errors or build fails**  
  Add `-shell-escape` to the LaTeX command. If that is not possible, replace `minted` with `verbatim` or `listings`.

- **Font issues with Unicode IPA**  
  Use XeLaTeX or LuaLaTeX and load a font with IPA coverage, for example Doulos SIL or Charis SIL.

- **Overfull boxes**  
  Shorten line text, add `\small` on dense frames, or split content across two frames.

---

## License

Released under the **MIT License**.  
Copyright © 2025 Magnus Simonsen.

---

### Credits and notes

- Theme: Minimal theme-less Beamer layout with custom frametitle, footline, and bullets.
- Icons: `fontawesome5` for info and warning callouts.
- IPA: `tipa` for pdfLaTeX or Unicode IPA via XeLaTeX/LuaLaTeX.
