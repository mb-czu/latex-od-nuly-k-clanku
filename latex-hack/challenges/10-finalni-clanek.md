# Challenge 10: Finální vědecký článek

## Scénář

V předchozích devíti Challenges jsi postupně vytvořil vědecký článek: od základní struktury projektu přes odborný text, citace, obrázky, tabulky a rovnice až po křížové odkazy a pokročilé funkce LaTeXu.

V posledním Challenge se zaměříš na dokončení dokumentu. Tvým úkolem není přidávat další obsah za každou cenu, ale ověřit, že všechny části spolu fungují, výsledek je přehledný a zdrojový projekt lze bez problémů znovu sestavit.

> **Důležité:** Náš článek je výukový příklad, nikoliv původní astronomický výzkum. Neprezentuj ukázkové formulace, tabulky ani ilustrace jako vlastní vědecká zjištění. U převzatých informací a obrázků ověř zdroje.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Zkontrolovat úplnost a konzistenci vícesouborového LaTeX projektu.
- Provést závěrečnou kontrolu odborného textu, abstraktu a struktury.
- Ověřit citace, bibliografii a správné přiřazení zdrojů.
- Zkontrolovat popisky a odkazy na obrázky, tabulky a rovnice.
- Odstranit pracovní poznámky a vyřešit varování kompilátoru.
- Vytvořit finální PDF přes LaTeX Workshop a DOCX přímým příkazem Pandocu.
- Ověřit export Pandocem včetně číslování, odkazů a APA CSL.
- Připravit zdrojové soubory k odevzdání tak, aby šel projekt znovu sestavit.

## Zadání

### Úkol 1: Zkontroluj strukturu projektu

Otevři svůj projekt ve VS Code a zkontroluj, že obsahuje všechny potřebné soubory. Orientační struktura může vypadat takto:

```text
project/
├── main.tex
├── references.bib
├── chapters/
│   ├── introduction.tex
│   ├── stars-and-galaxies.tex
│   ├── black-holes.tex
│   ├── observations.tex
│   └── conclusion.tex
├── figures/
│   ├── images/
│   └── definitions/
└── tables/
```

Pokud jsi v Challenge 09 vytvořil soubor `commands.tex`, ponech jej na místě, ze kterého jej `main.tex` načítá. V projektu mohou být i další soubory vzniklé v předchozích úkolech.

**Ověř:**

1. Všechny cesty v příkazech `\input` odpovídají existujícím souborům.
2. Všechny soubory s obrázky jsou dostupné na uvedených cestách.
3. V dokumentu je právě jedna dvojice `\begin{document}` a `\end{document}` — v `main.tex`.
4. Jednotlivé kapitoly neobsahují vlastní preambuli ani samostatné prostředí `document`.

### Úkol 2: Proveď kontrolu hlavního souboru

Zkontroluj preambuli `main.tex`. Měla by obsahovat balíčky, které skutečně používáš, například:

```latex
\documentclass[11pt,a4paper]{article}

\usepackage[english]{babel}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{csquotes}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{siunitx}
\usepackage{amsmath}
\usepackage[backend=biber,style=apa]{biblatex}
\addbibresource{references.bib}

% hyperref načítej před cleveref.
\usepackage[hidelinks]{hyperref}
\usepackage{cleveref}
```

Tento blok je **orientační kontrolní příklad**, nikoli pokyn bezmyšlenkovitě přepsat fungující preambuli. Zachovej další potřebné balíčky z předchozích úkolů, například `float` nebo `todonotes`, pokud je používáš.

Pokud máš vlastní příkazy v `commands.tex`, zkontroluj jejich načtení v preambuli pomocí `\input{commands}`.

**Ověř:** Bibliografický styl odpovídá zadání a `cleveref` je načten až po `hyperref`.

### Úkol 3: Zkontroluj strukturu a odborný text

Pročti celý článek od titulní části až po závěr.

- Titulek odpovídá tématu článku.
- Autor je uveden správně; nahraď výukový text `Your Name`.
- Abstrakt stručně shrnuje skutečný obsah dokumentu.
- Sekce a podsekce mají logické pořadí.
- Závěr navazuje na témata probíraná v článku.
- V textu nezůstaly výukové zástupné texty, například `TODO`, `...` nebo `Lorem ipsum`.
- Číselná tvrzení jsou ověřena a tam, kde je to potřeba, podložena zdrojem.

V případě potřeby uprav formulace. Zachovej angličtinu jako jazyk samotného článku.

### Úkol 4: Ověř citace a bibliografii

Otevři `references.bib` a porovnej jej s citacemi použitými v textu.

**Zkontroluj:**

1. Každý použitý citační klíč existuje v `references.bib`.
2. Bibliografické záznamy obsahují správné autory, názvy, roky a dostupné identifikátory, například DOI.
3. Odborná tvrzení převzatá z literatury jsou řádně citována.
4. Bibliografie se ve výsledném PDF skutečně zobrazuje.
5. Neobjevují se v ní nevyřešené citační klíče ani zástupné znaky místo citací.

Pokud používáš BibLaTeX, musí být v závěru dokumentu před `\end{document}` uvedeno:

```latex
\printbibliography
```

Při práci s citacemi můžeš využít například:

```latex
According to \textcite{citation-key}, ...

This phenomenon has been studied extensively
\parencite{citation-key}.
```

`citation-key` je pouze zástupný název: nahraď jej existujícím klíčem ze svého souboru `references.bib`.

### Úkol 5: Zkontroluj obrázky a tabulky

Prohlédni si všechny obrázky a tabulky ve výsledném PDF.

- Jsou dostatečně velké a čitelné?
- Mají výstižné anglické popisky (`\caption`)?
- Jsou správně číslované?
- Jsou převzaté obrázky a data opatřeny odpovídajícím uvedením zdroje?
- Nezasahují do okrajů stránky?
- Odpovídají odkazy v textu skutečným obrázkům a tabulkám?

**Příklad obrázku:**

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/images/galaxy-types.png}
    \caption{Classification of galaxies}
    \label{fig:galaxy-types}
\end{figure}
```

**Příklad odkazu v textu:**

```latex
The main galaxy categories are shown in
\cref{fig:galaxy-types}.
```

Zkontroluj také tabulky vytvořené pomocí `booktabs` a případné číselné sloupce z `siunitx`.

### Úkol 6: Zkontroluj matematické rovnice

Najdi všechny matematické výrazy a rovnice vytvořené v Challenge 07.

**Ověř:**

- Matematické symboly a indexy jsou správně zapsané.
- Číslované rovnice mají unikátní `\label`.
- Odkazy na rovnice ukazují na správná čísla.
- Rovnice nepřetékají mimo sazební oblast.
- Jednotky a označení veličin jsou v dokumentu konzistentní.

Například:

```latex
\begin{equation}
    E = mc^2
    \label{eq:mass-energy}
\end{equation}
```

A odkaz:

```latex
The mass--energy relationship is given by
\cref{eq:mass-energy}.
```

Pokud stejný příklad v dokumentu už máš, nevkládej jej znovu; pouze zkontroluj jeho sazbu a odkaz.

### Úkol 7: Odstraň pracovní poznámky

V Challenge 09 sis vyzkoušel poznámky pod čarou, vlastní příkazy a pracovní komentáře.

Nyní vyhledej a vyřeš všechny rozpracované poznámky:

- Poznámky typu `\todo{...}` vyřeš a odstraň ze zdroje před finálním exportem.
- Odstraň dočasné testovací odstavce a duplicitní příklady.
- Zkontroluj, zda v textu nezůstaly poznámky určené pouze autorovi.
- Ponech smysluplné poznámky pod čarou `\footnote{...}`, které mají být součástí článku.

Pokud používáš balíček `todonotes`, můžeš jej ve finální verzi načíst takto:

```latex
\usepackage[disable]{todonotes}
```

Tato volba skryje poznámky při sazbě PDF. Pro finální společný export odstraň zbývající `\todo` ze zdroje; účinek balíčku není zárukou chování Pandocu. Pokud balíček nepoužíváš, není nutné jej přidávat.

### Úkol 8: Proveď závěrečnou kompilaci

Ve VS Code otevři `main.tex` a použij LaTeX Workshop:

1. Ulož všechny změněné soubory.
2. Spusť **LaTeX Workshop: Build LaTeX project**.
3. Ujisti se, že používaný build recipe zpracuje také bibliografii pomocí **Biber** (například přes správně nastavený `latexmk` nebo posloupnost LaTeX → Biber → LaTeX → LaTeX).
4. Otevři výsledek přes **LaTeX Workshop: View LaTeX PDF**.
5. Projdi celý dokument stránku po stránce.
6. Zkontroluj výstupní log a případná varování.

**Rozlišuj chyby a varování:**

| Zpráva | Co prověřit |
|---|---|
| `Undefined control sequence` | Překlep v příkazu nebo chybějící balíček. |
| `Citation ... undefined` | Citační klíč, `references.bib` a běh Biberu. |
| `Reference ... undefined` | Chybějící nebo chybný `\label`, případně nutnost opakované kompilace. |
| `Overfull \\hbox` | Text, tabulka nebo rovnice přesahující dostupnou šířku. |
| `File ... not found` | Nesprávná cesta k obrázku nebo vloženému souboru. |

Ne každé varování znamená nefunkční dokument. U finálního článku ale musíš rozumět všem zbývajícím relevantním upozorněním a ověřit, že nemají negativní dopad na výstup.

### Úkol 9: Exportuj a dokonči finální Word

PDF sestav přes LaTeX Workshop jako dosud. Pro Word otevři terminál v `project/` a spusť:

```bash
pandoc main.tex --from=latex --number-sections --citeproc --bibliography=references.bib --csl=styles/apa.csl --toc --toc-depth=1 -o build/main.docx
```

Pokud používáš vlastní šablonu Wordu, přidej `--reference-doc=styles/reference.docx`. Složky `build/` a `styles/` a soubor `apa.csl` už máš z předchozích úkolů. Podrobnosti jsou ve [společném návodu](../BUILD.md).

Otevři PDF i DOCX a projdi je stránku po stránce. Ve Wordu aktualizuj obsah a podle Challenge 08 dokonči číslované popisky, čísla rovnic a křížové odkazy. Odstraň nevyřešené značky typu `[eq:schwarzschild-radius]`. Zkontroluj sekce, odstavce, citace, bibliografii, oba obrázky, obě tabulky, jednotky, rovnice, poznámku pod čarou, uvozovky a vlastní makra.

Přímý export nepřebírá automaticky veškeré LaTeXové číslování ani formátování. Citace nejsou živá pole doplňku Zotero. Rozdílné stránkování samo o sobě není chyba; chybějící obsah nebo nevyřešené odkazy chybou jsou. Po ručním dokončení ulož Word jako samostatnou finální kopii, aby jej další export nepřepsal.

### Úkol 10: Připrav projekt k odevzdání

Připrav tři části výsledku:

1. **Finální PDF** – čitelný dokument se všemi sekcemi, citacemi, obrázky, tabulkami a rovnicemi.
2. **Finální Word (.docx)** – exportovaný článek s citacemi a bibliografií.
3. **Zdrojový projekt** – `main.tex`, jednotlivé kapitoly, `references.bib`, všechny používané obrázky a další potřebné zdrojové soubory.

Před odevzdáním můžeš odstranit dočasné soubory vzniklé při kompilaci (například `.aux`, `.log`, `.bcf`, `.bbl`, `.run.xml` nebo `.synctex.gz`). **Nemaž** soubory `.tex`, `.bib`, obrázky ani další podklady, které jsou potřeba k opětovnému sestavení.

Výstupní PDF můžeš pojmenovat například `exploring-the-universe.pdf`. Soubor Wordu můžeš pojmenovat `exploring-the-universe.docx`. Ke zdrojovému projektu přilož i použité CSL a případnou Wordovou šablonu:

```text
odevzdani/
├── main.tex
├── references.bib
├── chapters/
├── tables/
├── figures/
├── styles/
│   ├── apa.csl
│   ├── ieee.csl
│   └── reference.docx    # pouze pokud používáš vlastní šablonu
└── README.MD
```

Do `README.MD` napiš potřebné nástroje, sestavení PDF přes LaTeX Workshop, výše uvedený příkaz Pandocu a postup ručního dokončení Wordu. Automatický export Zotera při další práci přesměruj do nové pracovní kopie, nebo přiložený `.bib` používej jako neměnný export pro reprodukci.

**Ověření reprodukovatelnosti:** Otevři připravený zdrojový projekt jako samostatnou složku ve VS Code a ověř sestavení PDF přes LaTeX Workshop a přímý export DOCX přes Pandoc. Oba výstupy znovu otevři a porovnej obsah. Pokud používáš lokální obrázky, fonty nebo vlastní balíčky, ujisti se, že jsou dostupné také při tomto opakovaném sestavení.

## Nápověda

| Příkaz / nástroj | K čemu slouží |
|---|---|
| `\input{...}` | Vkládá obsah samostatných souborů. |
| `\printbibliography` | Vypíše bibliografii spravovanou BibLaTeXem. |
| `\label{...}` | Vytváří identifikátor sekce, obrázku, tabulky nebo rovnice. |
| `\ref{...}` | Vypíše číslo odkazovaného objektu. |
| `\cref{...}` | Vytvoří kontextový odkaz, například *Figure 1*. |
| `\eqref{...}` | Vypíše číslo rovnice v závorkách. |
| `\caption{...}` | Přidává popisek obrázku nebo tabulky. |
| `\todo{...}` | Pracovní poznámka, pokud je načten `todonotes`. |
| LaTeX Workshop | Sestavení a zobrazení výsledného PDF ve VS Code. |
| Biber | Zpracování bibliografických dat pro BibLaTeX. |
| Pandoc | Export LaTeXového dokumentu do Wordu. |
| CSL | Definice citačního stylu pro Pandoc. |
| `--citeproc` | Zpracování citací při exportu přes Pandoc. |

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx --citeproc --bibliography=references.bib --csl=styles/apa.csl --toc --toc-depth=1
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

Challenge je dokončený, pokud:

- [ ] Projekt obsahuje všechny potřebné zdrojové soubory.
- [ ] `main.tex` načítá všechny kapitoly ve správném pořadí.
- [ ] Titulní část, abstrakt, sekce a závěr odpovídají obsahu článku.
- [ ] Všechny citace se správně zobrazují a bibliografie je úplná.
- [ ] Obrázky a tabulky mají čitelné popisky a správné odkazy.
- [ ] Rovnice jsou správně vysázené a jejich odkazy fungují.
- [ ] V dokumentu nezůstaly nevyřešené pracovní poznámky.
- [ ] V PDF nejsou chybějící odkazy ani viditelné problémy se sazbou.
- [ ] Projekt lze úspěšně zkompilovat přes LaTeX Workshop včetně Biberu.
- [ ] Úspěšně jsi exportoval článek do Wordu pomocí Pandocu.
- [ ] Ověřil jsi citace, bibliografii, obrázky, tabulky a rovnice ve Wordu.
- [ ] Máš připravené finální PDF, DOCX i kompletní zdrojový projekt.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](/latex-hack/checkpoints/README.MD).

## Dokončení LaTeX Hacku

**Gratulujeme!** Dokončil jsi všech deset Challenges a prošel sis kompletním postupem tvorby jednoduchého vědeckého článku v LaTeXu: od založení projektu až po výsledné PDF a export do Wordu.

Získané postupy můžeš dále využít při psaní seminárních prací, odborných článků, diplomových prací i rozsáhlejších výzkumných dokumentů.

[Zpět na přehled Hacku](../README.MD)
