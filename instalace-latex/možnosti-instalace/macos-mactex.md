### Krok 1: Instalace LaTeXu (MacTeX)

> [!NOTE]
> [Zpět na přehled](../02-instalace.md)

🎯 Cíl etapy: Mít na Macu kompletní LaTeX včetně češtiny, citací (biblatex, biber) a nástroje latexmk, aby šlo vyrobit PDF. Biblatex určuje, jak citace a seznam literatury v dokumentu vypadají, a biber je program, který načte zdroje ze Zotera (soubor .bib), seřadí je a předá biblatexu k vysázení.

#### 1a) Instalace

Příkaz níže předpokládá nainstalovaný [Homebrew](https://brew.sh/); alternativou je [oficiální instalátor MacTeXu nebo BasicTeXu](https://www.tug.org/mactex/).


`brew install --cask mactex-no-gui`

#### 1b) Načtení cest

Zavři Terminál a otevři nový, nebo spusť (očekávaným výstupem je že výstup nic nevypíše):
`eval "$(/usr/libexec/path_helper)"`

#### 1c) Ověření

```
pdflatex --version
latexmk --version
biber --version
```

#### 1d) Aktualizace

`sudo tlmgr update --self --all`

> [!IMPORTANT]
> Aktualizaci vždy nech doběhnout do konce, jinak se LaTeX rozbije.