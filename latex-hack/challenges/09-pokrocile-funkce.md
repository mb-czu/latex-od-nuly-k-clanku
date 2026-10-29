# Challenge 09: Pokročilé funkce LaTeXu

## Scénář

V předchozích Challenges jsi vytvořil vědecký článek *Exploring the Universe: From Stars to Black Holes*, doplnil citace, obrázky, tabulky, rovnice a křížové odkazy. Dokument je nyní funkční, ale při skutečném psaní odborného textu narazíš i na další situace: potřebuješ vysvětlit pojem mimo hlavní text, správně zapsat citovaný výrok, opakovaně používat stejný odborný výraz nebo si označit část článku, kterou musíš ještě dopracovat.

V tomto Challenge si vyzkoušíš několik praktických funkcí, které ti pomohou psát přehledněji a udržovat rozsáhlejší dokument.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Vkládat poznámky pod čarou pomocí `\footnote`.
- Rozlišit poznámku pod čarou od bibliografické citace.
- Používat balíček `csquotes` a příkaz `\enquote`.
- Vytvářet vlastní příkazy pomocí `\newcommand`.
- Definovat příkazy s argumenty.
- Pracovat s průběžnými poznámkami pomocí balíčku `todonotes`.
- Generovat automatický obsah pomocí `\tableofcontents`.
- Udržet hlavní soubor `main.tex` přehledný.

## Zadání

### Úkol 1: Přidej poznámku pod čarou

Poznámky pod čarou slouží k doplňujícímu vysvětlení, které by v hlavním textu narušovalo plynulost čtení.

Otevři soubor `chapters/black-holes.tex` a najdi část o horizontu událostí. V prvním odstavci pod `\subsection{Event Horizons}` přidej vysvětlující poznámku bezprostředně za slova `The event horizon`, před `is the boundary`. Nenahrazuj odstavec ukázkovou větou níže.

Použij příkaz:

```latex
\footnote{Text poznámky pod čarou.}
```

Například:

```latex
The event horizon\footnote{The event horizon is a boundary in
spacetime beyond which signals cannot reach a distant observer.}
is a fundamental concept in black hole physics.
```

**Ověření:** Ve výsledném PDF se u textu objeví značka poznámky a její obsah bude uveden ve spodní části stránky.

> **Pozor:** Poznámka pod čarou není náhradou za bibliografickou citaci. Pokud přebíráš odborné tvrzení z publikace, použij citaci pomocí BibLaTeXu, jak ses naučil v Challenge 04.

### Úkol 2: Vyzkoušej automatické uvozovky

Při psaní odborných textů se často setkáš s citovanými výroky nebo pojmy uvedenými v uvozovkách. Jejich podoba se může lišit podle jazyka dokumentu.

Pro správnou sazbu uvozovek využij balíček `csquotes`.

Balíček už je v preambuli `main.tex` od Challenge 01 za `lmodern`. Pouze ověř jeho existenci; znovu jej nepřidávej:

```latex
\usepackage{csquotes}
```

V `chapters/introduction.tex`, v sekci *Introduction*, za odstavec *Black holes are discussed…* vlož nový odstavec s pojmem *observable universe* v uvozovkách:

```latex
The term \enquote{observable universe} refers to the region
from which light has had time to reach an observer.
```

**Ověření:** Zkontroluj, že se ve výsledném PDF zobrazují správně typograficky vysázené uvozovky.

**Důležité:** Příkaz `\enquote` pouze formátuje uvozovky. Pokud jde o doslovně převzatý výrok z publikace, je stále nutné uvést odpovídající bibliografickou citaci.

### Úkol 3: Vytvoř vlastní příkaz bez argumentů

Pokud se v článku často opakuje stejný výraz, můžeš si pro něj vytvořit vlastní příkaz. Výhodou je, že případnou změnu provedeš pouze na jednom místě.

Do preambule `main.tex`, za `\usepackage[capitalise,noabbrev]{cleveref}` a před `\title`, přidej:

```latex
\newcommand{\blackhole}{black hole}
```

V `chapters/black-holes.tex` v podsekci *Formation of Black Holes* **nahraď celý dosavadní první odstavec** následujícím; druhou obdobnou větu nepřidávej:

```latex
A \blackhole{} can form after the gravitational collapse
of a sufficiently massive stellar core.
```

Prázdné složené závorky `{}` zajistí, aby se za příkazem správně zachovala mezera.

**Ověření:** Ve výsledném PDF se místo názvu příkazu zobrazí text *black hole*.

### Úkol 4: Vytvoř vlastní příkaz s argumentem

Vlastní příkazy mohou přijímat i vstupní hodnoty. To je užitečné například při opakovaném formátování odborných termínů.

V preambuli `main.tex`, bezprostředně za definici `\blackhole`, přidej:

```latex
\newcommand{\term}[1]{\textit{#1}}
```

V `chapters/black-holes.tex`, v podsekci *Event Horizons*, za odstavec s citací `eventhorizon2019` a před obrázek `fig:black-hole` vlož:

```latex
The \term{event horizon} is an important concept
in general relativity.
```

Všimni si, že:

- `[1]` znamená, že příkaz přijímá jeden argument.
- `#1` představuje hodnotu tohoto argumentu.
- `\textit{#1}` určuje, jak bude argument naformátován.

**Ověření:** Výraz *event horizon* se zobrazí kurzívou.

**Doporučení:** Vlastní příkazy pojmenovávej jednoznačně a nepřepisuj jimi existující příkazy LaTeXu. U rozsáhlejších projektů je vhodné jejich definice přesunout do samostatného souboru, například `commands.tex`, a načíst jej pomocí `\input{commands}` v preambuli.

### Úkol 5: Přidej pracovní poznámku pomocí `todonotes`

Při psaní vědeckého článku nemusíš mít všechny části dokončené. Pro označení míst, která vyžadují další práci, lze využít balíček `todonotes`.

V preambuli `main.tex`, za definici `\term` a před `\title`, přidej:

```latex
\setlength{\marginparwidth}{2cm}
\usepackage{todonotes}
```

V `chapters/observations.tex` bezprostředně za větu *A typical scientific observation process includes:* a před `\begin{enumerate}` dočasně vlož pracovní poznámku:

```latex
\todo{Add a recent reference about astronomical observations.}
```

Za odstavec se speciálními znaky, před odstavec *The wavelength…*, dočasně vlož také:

```latex
\todo[inline]{Expand this section with a short example
of telescope observations.}
```

**Ověření:** V PDF se zobrazí pracovní poznámka. Standardní `\todo` se obvykle umísťuje na okraj stránky, zatímco `\todo[inline]` se zobrazí přímo mezi odstavci.

> **Pozor:** `todonotes` může ovlivnit rozložení stránky a potřebuje dostatek místa pro okrajové poznámky. V konečné verzi článku by pracovní poznámky neměly zůstat viditelné.

### Úkol 6: Přepni pracovní poznámky do režimu `disable`

Balíček `todonotes` umožňuje poznámky skrýt, aniž bys je musel odstranit ze zdrojového kódu.

V preambuli `main.tex` nahraď pouze řádek `\usepackage{todonotes}` následujícím; nastavení `marginparwidth` před ním ponech:

```latex
\usepackage[disable]{todonotes}
```

Znovu dokument zkompiluj.

**Ověření:** Poznámky vytvořené pomocí `\todo` se již ve výsledném PDF nezobrazují.

Skrytí se týká sazby PDF; není obecně přenosným pokynem Pandocu. Po experimentu obě ukázková `\todo` odstraň ze zdroje. Pro další kroky ponech `\usepackage[disable]{todonotes}`; ukázkové poznámky nejsou skutečným požadavkem doplnit článek.

### Úkol 7: Vygeneruj automatický obsah

LaTeX dokáže sestavit obsah dokumentu z existujících sekcí a podsekcí.

Do souboru `main.tex` vlož za abstrakt a před první `\input{chapters/...}`:

```latex
\tableofcontents
```

Pro náš krátký vědecký článek není obsah nutný, ale vyzkoušíme si jej jako funkci využitelnou zejména v delších dokumentech.

**Ověření:** V PDF se zobrazí obsah s názvy sekcí a čísly stránek. Pokud se při prvním sestavení nezobrazí správně, spusť sestavení v LaTeX Workshop znovu; LaTeX aktualizuje obsah z pomocných souborů.

### Úkol 8: Uprav hloubku obsahu

Někdy chceš v obsahu zobrazit pouze hlavní sekce, jindy i podsekce.

Dosavadní jediný `\tableofcontents` z úkolu 7 **nahraď** tímto blokem (nevkládej další obsah):

```latex
\setcounter{tocdepth}{1}
\tableofcontents
```

Hodnota `1` v třídě `article` zahrnuje sekce, ale ne podsekce. Vyzkoušej také hodnotu `2`, která zobrazí i podsekce.

**Ověření:** Porovnej hodnoty `tocdepth` v PDF; pro Word nastav odpovídající `--toc-depth=1` nebo `--toc-depth=2` přímo v příkazu Pandocu s `--toc`. Nakonec vrať v obou případech `1`. V MS Word klikni do obsahu a zvol **Aktualizovat pole / Aktualizovat celou tabulku**, aby Word doplnil čísla stránek.

### Úkol 9: Udržuj preambuli přehlednou

V průběhu Hacku jsi do preambule přidával další a další balíčky. Nyní si jejich použití zkontroluj.

Preambule může obsahovat například následující balíčky (nepřidávej zbytečně duplicity):

```latex
\usepackage[english]{babel}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{siunitx}
\usepackage{amsmath}
\usepackage{csquotes}
\usepackage{float}
\usepackage[disable]{todonotes}
\usepackage[backend=biber,style=apa]{biblatex}
\addbibresource{references.bib}
\usepackage[hidelinks]{hyperref}
\usepackage{cleveref}
```

Tento seznam je **orientační** a předpokládá, že uvedené balíčky využíváš v předchozích Challenges. Balíček `cleveref` načítej až po `hyperref`.

Volitelný experiment: přesuň obě definice z preambule do nového `commands.tex` v kořeni projektu. V `main.tex` pak na původním místě definic ponech právě `\input{commands}`; definice nesmí existovat dvakrát:

```latex
\newcommand{\blackhole}{black hole}
\newcommand{\term}[1]{\textit{#1}}
```

Na původním místě definic pak zůstane:

```latex
\input{commands}
```

**Ověření:** Dokument se bez chyb sestaví pomocí LaTeX Workshop a všechny dosavadní obrázky, tabulky, rovnice, citace i odkazy nadále fungují.

## Nápověda

| Příkaz nebo balíček | Význam |
|---|---|
| `\footnote{...}` | Vloží poznámku pod čarou. |
| `csquotes` | Zajišťuje jazykově vhodné uvozovky. |
| `\enquote{...}` | Vysází text v uvozovkách. |
| `\newcommand{\nazev}{...}` | Definuje vlastní příkaz. |
| `\newcommand{\nazev}[1]{...#1...}` | Definuje příkaz s jedním argumentem. |
| `todonotes` | Přidává pracovní poznámky do dokumentu. |
| `\todo{...}` | Vloží pracovní poznámku. |
| `\todo[inline]{...}` | Vloží pracovní poznámku přímo do textu. |
| `\usepackage[disable]{todonotes}` | Skryje pracovní poznámky ve výsledném PDF. |
| `\tableofcontents` | Vygeneruje obsah dokumentu. |
| `\setcounter{tocdepth}{2}` | Nastaví hloubku automatického obsahu. |

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

- [ ] Do článku jsi přidal alespoň jednu poznámku pod čarou.
- [ ] Rozumíš rozdílu mezi poznámkou pod čarou a bibliografickou citací.
- [ ] Umíš použít `\enquote` z balíčku `csquotes`.
- [ ] Vytvořil jsi vlastní příkaz bez argumentu.
- [ ] Vytvořil jsi vlastní příkaz s jedním argumentem.
- [ ] Vyzkoušel jsi pracovní poznámky pomocí `todonotes`.
- [ ] Umíš pracovní poznámky skrýt pomocí volby `disable`.
- [ ] Vygeneroval jsi automatický obsah.
- [ ] Porovnal jsi obsah při různých hodnotách `tocdepth`.
- [ ] Dokument se bez chyb sestaví pomocí LaTeX Workshop.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)
