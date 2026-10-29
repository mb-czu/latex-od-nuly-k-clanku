# Krok 5: První dokument

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

🎯 Cíl etapy: Vytvořit první LaTeX článek s jednou sekcí a citacemi dle vyexportovaného souboru. Zkus sestavit článek z této [složky](/instalace-latex/prvni-dokument/) a ověř, že výsledné PDF odpovídá, případně si vytvoř svůj dle návodu níže.

## 5a) Struktura složky
Vytvoření složky, ve které se bude nacházet zdrojový soubor main.tex a ve stejné složce bude umístěn soubor (exportovaný ze Zotera podle [kroku 3](03-zotero-better-bibtex.md)) references.bib.

## 5b) Rozbor souboru `main.tex`

### 1. Preambule (vše před `\begin{document}`)

| Řádek                                              | Co dělá                                                                                                                   |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `\documentclass[11pt]{article}`                    | Typ dokumentu `article` (článek), základní písmo 11 bodů. Další možnosti: `report`, `book`, `beamer` (prezentace).        |
| `\usepackage[english]{babel}`                      | Jazyk dokumentu: dělení slov a texty jako „Abstract“ nebo „References“. Pro češtinu použij `[czech]`.                     |
| `\usepackage{csquotes}`                            | Správné uvozovky podle jazyka; biblatex ho doporučuje.                                                                    |
| `\usepackage[T1]{fontenc}`                         | Kódování písma, aby se správně zobrazovala a kopírovala písmena s diakritikou (ě, š, č…).                                 |
| `\usepackage{lmodern}`                             | Písmo Latin Modern, ostřejší verze výchozího LaTeX písma.                                                                 |
| `\usepackage{graphicx}`                            | Vkládání obrázků příkazem `\includegraphics`.                                                                             |
| `\usepackage[backend=biber, style=ieee]{biblatex}` | Správa citací. `backend=biber` určuje program, který zpracuje `.bib`; `style=ieee` dává číslované citace [1], [2]…        |
| `\usepackage[hidelinks]{hyperref}`                 | Klikací odkazy v PDF (citace, obsah, URL). `hidelinks` skryje barevné rámečky. Načítá se jako jeden z posledních balíčků. |
| `\addbibresource{references.bib}`                  | Připojí soubor s literaturou (s příponou `.bib`).                                                                         |
| `\title{...}`, `\author{...}`                      | Údaje pro titulek; zatím se nic nevypíše.                                                                                 |

### 2. Tělo dokumentu

| Příkaz                                | Co dělá                                                                                                 |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `\begin{document}` … `\end{document}` | Začátek a konec obsahu. Co je za `\end{document}`, LaTeX ignoruje.                                      |
| `\maketitle`                          | Vypíše nadpis, autora a datum. Datum změníš přes `\date{...}` v preambuli, prázdné `\date{}` ho skryje. |
| `\begin{abstract}` … `\end{abstract}` | Abstrakt, odsazený a s nadpisem.                                                                        |
| `\noindent\textbf{Keywords:} ...`     | Klíčová slova: řádek bez odsazení a tučný popisek.                                                      |
| `% \tableofcontents`                  | Obsah, zakomentovaný. Pro použití smaž `%`.                                                             |
| `\section{Introduction}`              | Číslovaná kapitola. Dále: `\subsection{}`, `\subsubsection{}`, bez čísla `\section*{}`.                 |
| Prázdný řádek v textu                 | Nový odstavec. Obyčejné zalomení řádku nic nedělá.                                                      |
| `\parencite{eventhorizon2019}`        | Citace v závorce podle klíče z `.bib`. Ve stylu IEEE vypíše `[1]`.                                      |
| `\printbibliography`                  | Vypíše seznam použité (citované) literatury.                                                            |

### 3. Komentáře
Vše za `%` až do konce řádku je komentář a do PDF se nedostane.
Samotný znak procenta napíšeš jako `\%`.

## 5c) Rozbor souboru `references.bib`

Ukázkový záznam pro citaci v článku:

```bibtex
@article{eventhorizon2019,
  author  = {{Event Horizon Telescope Collaboration}},
  title   = {First M87 Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole},
  journal = {The Astrophysical Journal Letters},
  volume  = {875},
  number  = {1},
  pages   = {L1},
  year    = {2019},
  doi     = {10.3847/2041-8213/ab0ec7}
}
```

- `eventhorizon2019` je **klíč**, kterým se zdroj cituje (`\parencite{eventhorizon2019}`).
- Dvojité závorky `{{...}}` zajistí, že se jméno instituce nerozdělí na jméno a příjmení.
- Necitovaný zdroj se v seznamu neobjeví. Pro vypsání všech zdrojů přidej `\nocite{*}`.

## Překlad do PDF

### Doporučeno: latexmk (vše jedním příkazem)
```bash
latexmk -pdf main.tex
```
latexmk sám pozná, kolikrát spustit `pdflatex` a kdy `biber`.


### Ručně (pochopení, co se děje)
```bash
pdflatex main.tex   # 1. průchod – zjistí, co se cituje
biber main          # zpracuje references.bib (bez přípony!)
pdflatex main.tex   # 2. průchod – vloží literaturu
pdflatex main.tex   # 3. průchod – doplní čísla odkazů
```

### Úklid pomocných souborů
```bash
latexmk -c    # smaže .aux, .log, .bbl, .bcf, .run.xml… (PDF nechá)
latexmk -C    # smaže i PDF
```

