# Challenge 01: Vytvoření struktury LaTeX projektu

## Scénář

Představ si, že připravuješ vědecký článek s názvem **Exploring the Universe: From Stars to Black Holes**.

Článek bude obsahovat několik tematických kapitol, odborné citace, obrázky, tabulky a matematické rovnice.

Při práci s rozsáhlejšími dokumenty není vhodné zapisovat veškerý obsah do jediného souboru. Dokument by se postupně stával nepřehledným a jeho úpravy by byly komplikovanější.

Tvým prvním úkolem proto bude **vytvořit přehlednou adresářovou strukturu projektu**, která ti umožní jednotlivé části článku spravovat samostatně.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Vytvořit základní adresářovou strukturu LaTeX projektu.
- Rozlišovat hlavní soubor dokumentu od souborů s jeho obsahem.
- Pochopit účel souborů `.tex` a `.bib`.
- Připravit samostatné adresáře pro kapitoly, obrázky a tabulky.
- Otevřít projekt ve Visual Studio Code.

## Zadání

### Úkol 1: Otevři pracovní projekt

V adresáři `latex-hack/` najdi složku `project/` (pokud neexistuje, vytvoř ji).

Tato složka bude obsahovat všechny pracovní soubory tvého vědeckého článku.

Otevři ji ve Visual Studio Code pomocí nabídky **File → Open Folder**.

### Úkol 2: Vytvoř adresářovou strukturu

Uvnitř složky `project/` vytvoř následující adresáře:

- `chapters/` – jednotlivé kapitoly článku.
- `figures/` – obrázky a jejich zdrojové soubory.
- `figures/images/` – obrázky připravené k vložení do dokumentu.
- `figures/definitions/` – zdrojové definice diagramů a ilustrací.
- `tables/` – samostatné soubory s tabulkami.

### Úkol 3: Připrav základní soubory

V kořenovém adresáři `project/` vytvoř:

- `main.tex` – hlavní soubor dokumentu.
- `references.bib` – soubor pro správu bibliografických záznamů.

V adresáři `chapters/` vytvoř:

- `introduction.tex`
- `stars-and-galaxies.tex`
- `black-holes.tex`
- `observations.tex`
- `conclusion.tex`

Kapitoly a `references.bib` zatím ponech prázdné. Jejich obsah budeme postupně doplňovat. Soubor `main.tex` však musí jít sestavit už v tomto úkolu: vlož do něj celý následující minimální dokument. Balíček `csquotes` přidáváme rovnou za `lmodern`, aby od zavedení bibliografie nevznikalo upozornění na jeho chybějící načtení.

```latex
\documentclass[11pt,a4paper]{article}
\usepackage[english]{babel}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{csquotes}

\title{Exploring the Universe: From Stars to Black Holes}
\author{Your Name}
\date{\today}

\begin{document}
\maketitle
Project initialized.
\end{document}
```

Do preambule patří nastavení před `\begin{document}`; obsah dokumentu patří mezi `\begin{document}` a `\end{document}`. `Your Name` nahraď vlastním jménem. `Project initialized.` je jediný provizorní odstavec, který v Challenge 02 nahradíš úvodem. Prázdné kapitoly zatím nenačítej pomocí `\input`.

Postup pro oba formáty popisuje [sestavení](/latex-hack/přílohy/BUILD.md). V `project/` vytvoř také prázdnou složku `build/` pro export Wordu. PDF sestavuj dosavadním postupem přes LaTeX Workshop.

### Úkol 4: Zkontroluj výslednou strukturu

Výsledný projekt by měl vypadat následovně:

```text
project/
├── main.tex
├── references.bib
├── build/                 # výstup Wordu, případně PDF dle nastavení editoru
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

## Nápověda

| Soubor nebo adresář    | K čemu slouží                                             |
| ---------------------- | --------------------------------------------------------- |
| `main.tex`             | Hlavní soubor, ze kterého se sestavuje výsledný dokument. |
| `references.bib`       | Databáze bibliografických záznamů.                        |
| `chapters/`            | Obsah jednotlivých kapitol článku.                        |
| `figures/images/`      | Obrázky používané v dokumentu.                            |
| `figures/definitions/` | Zdrojové soubory diagramů a dalších ilustrací.            |
| `tables/`              | Tabulky uložené v samostatných souborech.                 |

V dalších Challenges se naučíš jednotlivé soubory propojit pomocí příkazu `\input`, takže výsledný článek bude možné sestavit z více samostatných částí.

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../přílohy/BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

Challenge je dokončený, pokud:

- [ ] Máš vytvořený adresář `project/`.
- [ ] Projekt obsahuje hlavní soubor `main.tex`.
- [ ] Projekt obsahuje soubor `references.bib`.
- [ ] Máš připravené všechny požadované soubory v `chapters/`.
- [ ] Existují adresáře pro obrázky a tabulky.
- [ ] Celý projekt můžeš otevřít ve Visual Studio Code.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Dílčí řešení úkolů 01–09 najdeš v [checkpointech](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)
