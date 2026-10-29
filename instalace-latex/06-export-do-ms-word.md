# Krok 6: Export do MS Word přes Pandoc

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

Pandoc převádí zdroj `main.tex` do `.docx`. Pro citace používá `citeproc` a styl CSL; nepoužívá Biber ani sazbu LaTeXem. Výsledek proto vždy otevři v MS Word a porovnej s PDF. [Podporované formáty a přepínače popisuje Pandoc](https://pandoc.org/MANUAL.html).

## Instalace Pandocu

Nainstaluj Pandoc podle [oficiálního návodu pro macOS a Windows](https://pandoc.org/installing.html). Na macOS s Homebrew stačí `brew install pandoc`; na Windows použij instalační balíček z návodu. Poté znovu otevři terminál a ověř `pandoc --version`.

## Jednoduchý úvodní dokument

V terminálu otevřeném ve složce `instalace-latex/prvni-dokument/` vytvoř složku `build/`. Vzor už obsahuje `styles/ieee.csl`. U vlastního projektu vytvoř `styles/` a zkopíruj do ní tento soubor nebo styl z [oficiálního repozitáře CSL](https://github.com/citation-style-language/styles). Potom spusť:

```bash
pandoc main.tex --from=latex --citeproc --bibliography=references.bib --csl=styles/ieee.csl -o build/main.docx
```

CSL musí odpovídat stylu v `biblatex`: APA používá `apa.csl`, IEEE `ieee.csl`. Stejný styl nemusí mít v obou procesorech zcela totožnou sazbu. Výsledné citace nejsou aktivními poli doplňku Zotero.

Volitelnou šablonu Wordu vytvoříš ve stejné pracovní složce takto:

```bash
pandoc --print-default-data-file reference.docx > styles/reference.docx
```

Otevři ji ve Wordu, uprav styly a ulož. Pak k exportu přidej `--reference-doc=styles/reference.docx`. Pokud šablonu nevytvoříš, tento přepínač vynech.