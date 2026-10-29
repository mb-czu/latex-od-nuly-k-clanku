# Challenge 04: Citace a bibliografie

## Scénář

V předchozích Challenges jsi připravil strukturu článku *Exploring the Universe: From Stars to Black Holes*, vytvořil abstrakt a rozdělil text do samostatných souborů. Odborný článek však musí také jasně uvádět, z jakých publikací vychází.

Tvým úkolem je vytvořit databázi literatury v souboru `references.bib`, propojit ji s článkem a doplnit průběžné citace. Vyzkoušíš si také, jak se změní vzhled citací při přepnutí citačního stylu.

V tomto Challenge budeme používat **BibLaTeX** pro správu citací a bibliografie a **Biber** pro zpracování bibliografických dat. Kompilaci spouštíme ve **Visual Studio Code prostřednictvím LaTeX Workshop**.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Vysvětlit rozdíl mezi bibliografickou databází a seznamem literatury ve výsledném PDF.
- Přidat skutečné publikace do Zotera a automaticky exportovat Better BibLaTeX.
- Načíst balíček `biblatex` a připojit bibliografický soubor.
- Používat `\textcite`, `\parencite` a citace více zdrojů.
- Vygenerovat seznam použité literatury pomocí `\printbibliography`.
- Porovnat styly `apa` a `ieee`.
- Zkontrolovat, že LaTeX Workshop správně spouští Biber.

## Výchozí stav

Navazuješ na **Challenge 03**. Projekt už obsahuje soubor `main.tex` a jednotlivé sekce v adresáři `chapters/`.

Pokračuj ve vlastním `project/` po Challenge 03; dílčí checkpointy zatím nejsou publikované.

> **Pozor:** Bibliografické záznamy uvedené níže jsou výukové příklady vycházející ze skutečných publikací. Při psaní vlastního článku vždy ověř přesnost metadat a cituj jen zdroje, které jsi skutečně použil.

## Zadání

### Úkol 1: Přidej původní zdroje do Zotera

Vytvoř v Zoteru kolekci `Exploring the Universe`. Podle [seznamu původních zdrojů](../ZDROJE.md) přidej Hawkingovu knihu (1988), druhé vydání Carrolla a Ostlieho (2007) a článek EHT (2019). Použij uvedené ISBN/DOI přes **Přidat položku podle identifikátoru**, případně Zotero Connector na stránce publikace. Zkontroluj autory, vydání, rok a typ položky.

V poli **Extra** každé položky nastav pevný klíč samostatným řádkem:

```text
Citation Key: hawking1988
```

U dalších dvou položek použij `Citation Key: carroll2007` a `Citation Key: eventhorizon2019`. Každý řádek patří k odpovídající položce, nikoliv všechny k jedné. Neměň kvůli ukázkovému klíči rok skutečného vydání.

### Úkol 2: Vytvoř references.bib automatickým exportem

Na kolekci klikni pravým tlačítkem → **Exportovat kolekci** → formát **Better BibLaTeX** → **Keep updated**. Ulož ji jako `project/references.bib` a nahraď dosud prázdný soubor. Podrobnosti jsou v [návodu Zotero](../../docs/02-zotero-better-bibtex.md).

Otevři export a ověř právě tři záznamy s klíči `hawking1988`, `carroll2007`, `eventhorizon2019`. Metadata upravuj v Zoteru, nikoliv v automaticky generovaném `.bib`, který další export přepíše. Referenční `.bib` v `solution/` slouží ke kontrole a k sestavení vzorového článku; nenahrazuje tento úkol.

V `project/` vytvoř složku `styles/`. Z `latex-hack/styles/` do ní zkopíruj `apa.csl` a `ieee.csl`; nepřidávají se do preambule, používá je přímo příkaz Pandocu.

### Úkol 3: Nastav BibLaTeX v hlavním dokumentu

Otevři `main.tex`. Do **preambule**, bezprostředně za stávající `\usepackage{csquotes}` a před `\title`, vlož:

```latex
\usepackage[backend=biber,style=apa]{biblatex}
\addbibresource{references.bib}
```

Parametr `backend=biber` určuje, že bibliografická data bude zpracovávat Biber. Parametr `style=apa` nastavuje citační styl APA.

Příkaz `\addbibresource` propojí článek se souborem bibliografických záznamů.

> Pro tento Challenge používej balíček `biblatex`. Nekombinuj jej s balíčkem `natbib` ani s příkazem `\bibliography{...}` ze staršího postupu BibTeX.

### Úkol 4: Přidej první citaci do textu

Otevři `chapters/introduction.tex` a za původní úvodní odstavec přidej novou větu, která odkazuje na Hawkingovu knihu:

> Hawking provides an accessible introduction to the evolution of the universe and the physical principles behind black holes.

Za větu vlož **citaci v závorce** pomocí `\parencite` a klíče `hawking1988`.

Ukázka syntaxe:

```latex
A scientific statement supported by a source \parencite{hawking1988}.
```

**Ověření:** Po správné kompilaci se místo citačního klíče zobrazí citace podle zvoleného stylu.

### Úkol 5: Vyzkoušej textovou citaci

V souboru `chapters/stars-and-galaxies.tex` přidej do podsekce *The Life Cycle of Stars*, za první odstavec končící *initial mass* a před `\subsection{Types of Galaxies}`, nový odstavec:

> Carroll and Ostlie describe stellar structure and evolution in detail.

Přepiš ji tak, aby jména autorů byla vložena automaticky pomocí `\textcite{carroll2007}`. Nepiš jména autorů ručně před citační příkaz.

Nápověda:

```latex
\textcite{carroll2007} describe stellar structure and evolution in detail.
```

**Porovnej:**

- `\parencite{...}` – citace tvoří samostatný odkaz v závorce.
- `\textcite{...}` – jméno autora je přirozenou součástí věty.

### Úkol 6: Cituj odborný článek

V `chapters/black-holes.tex`, v podsekci *Event Horizons*, za první odstavec končící *distant observers* přidej nový odstavec:

> The Event Horizon Telescope collaboration published an image of the black hole shadow in the galaxy M87.

Na konec věty přidej citaci `\parencite{eventhorizon2019}`.

Zkontroluj, že se v bibliografii správně zobrazí název článku, časopisu a DOI.

### Úkol 7: Cituj více zdrojů současně

V `chapters/conclusion.tex`, v sekci *Conclusion*, za stávající závěrečný odstavec končící *evolution of the cosmos* vlož nový odstavec:

> Understanding the universe requires combining theoretical models with astronomical observations.

Doplň k ní **jednu společnou citaci** odkazující na zdroje `hawking1988` a `carroll2007`.

Nápověda:

```latex
\parencite{hawking1988,carroll2007}
```

### Úkol 8: Vygeneruj seznam použité literatury

Na konec souboru `main.tex`, **za poslední `\input` a před `\end{document}`**, přidej:

```latex
\printbibliography
```

LaTeX automaticky vytvoří seznam použitých zdrojů. Ve výchozím nastavení se v něm zobrazují především publikace, které jsi v dokumentu citoval.

Pokud chceš dočasně vypsat i necitované záznamy, můžeš experimentovat s příkazem `\nocite{*}`. Po vyzkoušení jej odstraň.

### Úkol 9: Zkompiluj dokument přes LaTeX Workshop

1. Otevři `main.tex` ve Visual Studio Code.
2. Ulož všechny upravené `.tex` a `.bib` soubory.
3. Spusť **LaTeX Workshop: Build LaTeX project**.
4. Ujisti se, že vybraný kompilační recept obsahuje zpracování bibliografie pomocí **Biberu** (například prostřednictvím `latexmk` s odpovídající konfigurací nebo receptu `pdfLaTeX → Biber → pdfLaTeX → pdfLaTeX`).
5. Otevři PDF a zkontroluj průběžné citace i seznam literatury.

Pokud místo citací vidíš otazníky nebo hlášení o nedefinovaných citacích, zkontroluj zejména:

- zda jsou citační klíče v `.tex` a `.bib` naprosto shodné,
- zda je správně uveden `\addbibresource{references.bib}`,
- zda je nainstalovaný Biber a skutečně se spouští,
- zda nebyla kompilace přerušena chybou.

**Důležité:** Pro průběžný náhled PDF používej LaTeX Workshop. Na konci úkolu vždy spusť také sestavení PDF přes LaTeX Workshop a export Wordu přes Pandoc.

### Úkol 10: Porovnej styly APA a IEEE

V souboru `main.tex` změň:

```latex
\usepackage[backend=biber,style=apa]{biblatex}
```

na:

```latex
\usepackage[backend=biber,style=ieee]{biblatex}
```

Spusť sestavení PDF přes LaTeX Workshop a export Wordu přes Pandoc. V příkazu Pandocu dočasně změň `--csl=styles/apa.csl` na `--csl=styles/ieee.csl`. Otevři oba výstupy a porovnej:

- podobu průběžných citací,
- pořadí a formát bibliografických údajů,
- způsob označování jednotlivých zdrojů.

| Styl | Typické průběžné citace | Charakteristika |
|---|---|---|
| APA | Autor a rok | Častý v sociálních a behaviorálních vědách. |
| IEEE | Číselné odkazy, např. `[1]` | Častý v technických a informatických oborech. |

**Pozor:** Styl IEEE je číselný; příkaz `\textcite` v něm nebude vypadat stejně jako v APA. Porovnej také, zda věta zůstává přirozeně čitelná.

Po experimentu **vrať styl na `apa`, přepínač Pandocu na `--csl=styles/apa.csl` a znovu sestav PDF i Word**, abychom měli jednotný výchozí stav pro další Challenges.

## Nápověda: Přehled příkazů

| Příkaz | Význam |
|---|---|
| `\usepackage[backend=biber,style=apa]{biblatex}` | Načte BibLaTeX s Biberem a stylem APA. |
| `\addbibresource{references.bib}` | Připojí bibliografickou databázi. |
| `\parencite{klíč}` | Vloží citaci v závorce. |
| `\textcite{klíč}` | Vloží textovou citaci jako součást věty. |
| `\parencite{klíč1,klíč2}` | Vloží společnou citaci více zdrojů. |
| `\printbibliography` | Vytvoří seznam použité literatury. |
| `\nocite{*}` | Zahrne do bibliografie všechny záznamy z databáze. |

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx --citeproc --bibliography=references.bib --csl=styles/apa.csl
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

Challenge je dokončený, pokud:

- [ ] Tři skutečné publikace mám v Zoteru a `references.bib` vzniká automatickým exportem Better BibLaTeX.
- [ ] Každý záznam má jedinečný citační klíč.
- [ ] V `main.tex` je správně nastaven BibLaTeX s Biberem.
- [ ] Úvod obsahuje citaci pomocí `\parencite`.
- [ ] Sekce o hvězdách obsahuje textovou citaci pomocí `\textcite`.
- [ ] Sekce o černých dírách cituje odborný článek.
- [ ] Závěr obsahuje společnou citaci dvou zdrojů.
- [ ] Na konci dokumentu se zobrazuje seznam použité literatury.
- [ ] Vyzkoušel jsi rozdíl mezi citačními styly APA a IEEE.
- [ ] Po experimentu je znovu nastaven styl APA.
- [ ] Kompilace přes LaTeX Workshop probíhá bez chyb a bez nedefinovaných citací.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](../DILCI-RESENI.md).

## Další Challenge

V **Challenge 05: Obrázky a ilustrace** se naučíš vkládat obrázky pomocí `\includegraphics`, nastavovat jejich velikost a umístění a přidávat popisky.

[Zpět na přehled Hacku](../README.MD)
