# Sestavení a kontrola každého Challenge

Po každém úkolu vytvoř PDF přes **LaTeX Workshop** a Word přímým příkazem **Pandocu**. Oba výstupy otevři a zkontroluj. Používáme dosavadní nástroje a standardní příkazy.

## PDF: LaTeX Workshop

1. Ve VS Code otevři složku `project/` a soubor `main.tex`.
2. Ulož všechny změny a spusť **LaTeX Workshop: Build LaTeX project**.
3. Od Challenge 04 použij recept zahrnující Biber, například přes `latexmk` nebo pdfLaTeX → Biber → pdfLaTeX → pdfLaTeX.
4. Otevři PDF přes **LaTeX Workshop: View LaTeX PDF** a zkontroluj log.

Cesta k PDF závisí na nastavení editoru: může být vedle `main.tex` nebo v `build/`. Pro export Wordu v `project/` vytvoř složku `build/`.

## Word: přímý export Pandocem

V terminálu otevřeném v `project/`, kde je `main.tex`, spusť pro Challenge 01–03:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx
```

Od Challenge 04 zkopíruj `apa.csl` a `ieee.csl` z `latex-hack/styles/` do vlastní složky `project/styles/`. Používej:

```bash
pandoc main.tex --from=latex --number-sections --citeproc --bibliography=references.bib --csl=styles/apa.csl -o build/main.docx
```

Při experimentu s IEEE změň v PDF `style=apa` na `style=ieee` a v příkazu Pandocu `apa.csl` na `ieee.csl`. Potom obojí vrať na APA a znovu vytvoř oba výstupy. Pandoc styl z preambule automaticky nepřebírá.

Od Challenge 09 přidej do stejného příkazu `--toc --toc-depth=1` pro obsah. `tocdepth` v LaTeXu řídí pouze PDF. Po otevření DOCX v MS Wordu aktualizuj celý obsah přes **Aktualizovat pole / Aktualizovat celou tabulku**.

Pandoc načítá kapitoly a tabulky přes `\input`. Příkaz spouštěj vždy z kořene pracovního článku, aby našel všechny relativní cesty a obrázky. [Význam přepínačů popisuje dokumentace Pandocu](https://pandoc.org/MANUAL.html).

## Co se převádí a co kontrolovat

Běžné odstavce, nadpisy, seznamy, PNG/JPEG, jednoduché tabulky, citace, poznámky pod čarou a matematické výrazy z těchto zadání se převádějí přímo. Neznamená to shodné stránkování ani podporu libovolného balíčku LaTeXu.

- Pro finální tabulky používej standardní sloupce `l`, `c`, `r`. Sloupec `S` z `siunitx` je jen experiment v Challenge 06; před závěrečným exportem jej vrať na `r`. Jednotky `\qty` ponech a v obou souborech zkontroluj jejich hodnoty a sazbu.
- Pro výsledný vícerádkový výpočet používej `equation` s vnitřním `aligned` podle Challenge 07.
- Čísla rovnic, číslované popisky a křížové odkazy z LaTeXu nejsou automaticky hotovými poli Wordu. Od Challenge 08 je po exportu ručně dokonči v MS Wordu přes **Vložit titulek** a **Křížový odkaz**, jak popisuje zadání. Odstraň všechny nevyřešené značky, například `[eq:schwarzschild-radius]`.
- Pracovní `\todo` po experimentu odstraň ze zdroje. Skrytí balíčkem v PDF není obecný pokyn pro Pandoc.
- Citace z `citeproc` nejsou aktivními poli doplňku Zotero. Metadata opravuj v Zoteru, vyčkej na export `.bib` a pak Word znovu exportuj.

Každý další export přepíše `build/main.docx`, včetně ručních oprav jeho číslování a odkazů. Hotový zkontrolovaný Word ulož jako samostatnou finální kopii. LaTeX zůstává zdrojovým dokumentem; Word má závěrečnou vlastní kontrolu.

## Volitelný vzhled Wordu

Ve složce `project/` vytvoř `styles/`, pokud ještě neexistuje, a spusť:

```bash
pandoc --print-default-data-file reference.docx > styles/reference.docx
```

Otevři šablonu ve Wordu, uprav styly a ulož. K exportnímu příkazu pak přidej `--reference-doc=styles/reference.docx`. Pokud šablonu nevytvoříš, tento přepínač vynech. Písmo, A4 a okraje nastav ve Wordové šabloně; LaTeXová preambule sama vzhled Wordu neurčuje.

## Osobní kontrola po každém úkolu

Otevři právě vytvořené PDF a DOCX a porovnej změny z aktuálního úkolu. Zkontroluj úplnost odstavců, nadpisy, seznamy a speciální znaky; od 04 citace a bibliografii, od 05 oba obrázky, od 06 dvě skutečné tabulky a jednotky, od 07 matematiku, od 08 doplněné popisky a odkazy a od 09 poznámku pod čarou, uvozovky, makra a jeden obsah. V obou formátech ověř čitelnost a okraje. Při chybě sestavení nepovažuj starý výstup za nový výsledek.
