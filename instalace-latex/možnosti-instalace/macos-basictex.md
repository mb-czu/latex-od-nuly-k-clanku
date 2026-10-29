# Krok 1: Instalace LaTeXu (BasicTeX)

> [!NOTE]
> [Zpět na přehled](../02-instalace.md)


🎯 Cíl etapy: Mít na Macu kompletní LaTeX včetně češtiny, citací (biblatex, biber) a nástroje latexmk, aby šlo vyrobit PDF. Biblatex určuje, jak citace a seznam literatury v dokumentu vypadají, a biber je program, který načte zdroje ze Zotera (soubor .bib), seřadí je a předá biblatexu k vysázení.

## 1a) Instalace

Příkaz níže předpokládá nainstalovaný [Homebrew](https://brew.sh/); alternativou je [oficiální instalátor BasicTeXu](https://www.tug.org/mactex/morepackages.html).

`brew install --cask basictex`

## 1b) Načtení cest
Zavři Terminál a otevři nový, nebo spusť (očekávaným výstupem je že výstup nic nevypíše):
`eval "$(/usr/libexec/path_helper)"`

## 1c) Ověření instalace
```
pdflatex --version
tlmgr --version
```

## 1d) Aktualizace správce balíčků
`sudo tlmgr update --self`

## 1e) Instalace balíčků - varianta 1
Je třeba nainstalovat balíčky, které následně budeme v rámci LaTeX souboru využávat v rámci `\usepackage{}`

| Balíček         | Popis a využití                                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| latexmk         | Automatizuje kompilaci dokumentu. Podle potřeby opakuje překlad a spouští Biber. Využívá ho LaTeX Workshop ve VS Code. |
| biber           | Zpracovává bibliografické záznamy ze souboru .bib a připravuje citace a seznam literatury.                             |
| biblatex        | Spravuje citace a bibliografii v dokumentu. Umožňuje nastavit citační styl, například IEEE.                            |
| csquotes        | Zajišťuje správné typografické uvozovky podle jazyka dokumentu. Spolupracuje s biblatex.                               |
| babel           | Nastavuje jazyk dokumentu, překlady automatických popisků a pravidla dělení slov.                                      |
| hyphen-english  | Obsahuje pravidla pro správné dělení anglických slov na koncích řádků.                                                 |
| lm              | Poskytuje písmo Latin Modern, modernizovanou variantu výchozího LaTeXového písma.                                      |
| graphics        | Umožňuje vkládat a upravovat obrázky prostřednictvím graphicx.                                                         |
| hyperref        | Vytváří klikací odkazy, odkazy na kapitoly, obrázky, tabulky a bibliografické záznamy v PDF.                           |
| microtype       | Zlepšuje typografii, zarovnání a rozložení textu. Pomáhá omezit nevzhledné mezery mezi slovy.                          |
| cleveref        | Automaticky vytváří inteligentní odkazy na obrázky, tabulky a kapitoly, například „Figure 1“ místo samotného čísla.    |
| booktabs        | Poskytuje příkazy pro profesionální tabulky s kvalitními vodorovnými linkami.                                          |
| geometry        | Umožňuje jednoduše nastavit okraje stránky a rozměry textové oblasti.                                                  |
| biblatex-ieee   | Citační balíček IEEE.                                                                                                  |
| biblatex-iso690 | Citační balíček ISO-690.                                                                                               |

Příkaz níže zahrnuje také balíčky pro navazující LaTeX Hack (`biblatex-apa`, `siunitx`, `amsmath`, `todonotes`, `float`). Další balíčky doplň podle vlastního dokumentu.

Instalace všech balíčků jedním příkazem `sudo tlmgr install latexmk biber biblatex csquotes babel hyphen-english lm graphics hyperref microtype cleveref booktabs geometry biblatex-ieee biblatex-iso690 biblatex-apa siunitx amsmath todonotes float`

## 1f) Instalace kolekcí balíčků - varianta 2 (doporučeno)
| Kolekce / balíček           | Co přinese                                                                                                    |
| --------------------------- | ------------------------------------------------------------------------------------------------------------- |
| collection-latexrecommended | základ pro články: geometry, microtype, booktabs, caption, xcolor, float, fontspec, setspace                  |
| collection-latexextra       | velká sbírka běžných doplňků: enumitem, cleveref, tcolorbox, lipsum, pdfpages … (největší položka, stovky MB) |
| collection-bibtexextra      | citační styly: biblatex-ieee, biblatex-iso690 (česká norma), biblatex-apa …                                   |
| collection-fontsrecommended | běžná písma (Latin Modern, TeX Gyre, tedy obdoby Times a Helvetiky)                                           |
| collection-langczechslovak  | česká a slovenská dělení slov a babel-czech                                                                   |
| latexmk, biber              | překlad a zpracování citací                                                                                   |
| latexindent, chktex         | formátování a kontrola kódu, které používá LaTeX Workshop ve VS Code                                          |

Instalace všech kolekcí `sudo tlmgr install collection-latexrecommended collection-latexextra collection-bibtexextra collection-fontsrecommended collection-langczechslovak latexmk biber latexindent chktex`