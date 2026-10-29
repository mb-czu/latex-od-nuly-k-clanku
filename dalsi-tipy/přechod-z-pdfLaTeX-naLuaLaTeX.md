# Volitelný přechod z pdfLaTeXu na LuaLaTeX

**V main.tex vyměň řádky pro písmo**

Místo:
```
\usepackage[T1]{fontenc}
\usepackage{lmodern}
```
Použij
```
\usepackage{fontspec}
\setmainfont{Times New Roman} % volitelné, jakékoli písmo z Macu
```
Pokud řádek `\setmainfont` vynecháš, zůstane výchozí LaTeXové písmo.


**Změň způsob spuštění ve VS Code**

V levém panelu klikni na ikonu TeX → Build LaTeX project → Recipe: latexmk (lualatex).

**Na co si dát pozor**

- První běh trvá déle, i minutu. LuaLaTeX si vytváří mezipaměť písem. Další běhy jsou rychlejší.
- Nejde to kombinovat. Dokument s fontspec už pdfLaTeXem nepřeložíš. Kdo dokument přebírá (časopis, spoluautor v
  Overleafu), musí vědět, že je pro LuaLaTeX.
- Šablony časopisů: Pokud časopis vyžaduje pdfLaTeX, drž se ho.

