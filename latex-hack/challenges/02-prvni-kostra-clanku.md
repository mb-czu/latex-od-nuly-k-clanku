# Challenge 02: První vědecký článek

## Scénář

V předchozím Challenge jsi připravil adresářovou strukturu svého LaTeX projektu. Nyní je čas vytvořit první funkční verzi vědeckého článku.

Připravuješ odborný článek s názvem **Exploring the Universe: From Stars to Black Holes**, který se zabývá vesmírem, hvězdami, galaxiemi a černými dírami.

Než začneš psát jednotlivé kapitoly, musíš nastavit základní vlastnosti dokumentu, připravit jeho titulní část a ověřit, že se správně kompiluje.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Vytvořit základní strukturu LaTeX dokumentu.
- Použít třídu dokumentu `article`.
- Nastavit velikost papíru, písma a jazyk dokumentu.
- Načíst potřebné balíčky pomocí `\usepackage`.
- Definovat název článku, autora a datum.
- Vygenerovat titulní část pomocí `\maketitle`.
- Vytvořit první číslovanou kapitolu.
- Zkompilovat dokument pomocí rozšíření LaTeX Workshop.

## Zadání

### Úkol 1: Připrav hlavní soubor

Otevři svůj projekt ve Visual Studio Code a najdi soubor `main.tex`.

Tento soubor bude hlavním vstupním bodem celého článku.

Zachovej základ z Challenge 01. Následující úkoly jej upravují; nevytvářej druhou preambuli ani další prostředí `document`. Zkontroluj, že obsahuje:

- deklaraci třídy dokumentu,
- preambuli pro nastavení balíčků,
- začátek dokumentu,
- prostor pro obsah článku,
- konec dokumentu.

### Úkol 2: Nastav vlastnosti dokumentu

Dokument musí splňovat následující požadavky:

| Vlastnost | Požadovaná hodnota |
|---|---|
| Třída dokumentu | `article` |
| Velikost písma | 11 pt |
| Formát papíru | A4 |
| Jazyk dokumentu | Angličtina |
| Kódování fontů | T1 |
| Písmo | Latin Modern |

Tyto parametry a balíčky už máš z Challenge 01. Zachovej také `\usepackage{csquotes}` bez další kopie.

### Úkol 3: Přidej informace o článku

V `main.tex` v preambuli nahraď stávající `\title`, `\author` a `\date` (za `\usepackage{csquotes}`) těmito hodnotami:

- **Název:** Exploring the Universe: From Stars to Black Holes
- **Autor:** Tvoje jméno
- **Datum:** Aktuální datum

Dosavadní jediný `\maketitle` bezprostředně za `\begin{document}` ponech; zobrazí upravené údaje. Druhou kopii nepřidávej.

### Úkol 4: Vytvoř úvodní kapitolu

V `main.tex` v těle dokumentu za `\maketitle` a před `\end{document}` přidej `\section{Introduction}`. Provizorní větu `Project initialized.` z Challenge 01 odstraň.

Bezprostředně za `\section{Introduction}` vlož jako první odstavec následující text:

> The universe is a vast and fascinating place. In this paper, we explore the mysteries of stars, galaxies, and black holes. Modern astronomy provides powerful tools to investigate the origins, structure, and evolution of the cosmos.

Sekce i text zatím patří přímo do `main.tex`. V dalších Challenges jej přesuneme do samostatného souboru `chapters/introduction.tex`.

### Úkol 5: Sestav oba výstupy

Nejprve můžeš použít náhled PDF přes **LaTeX Workshop**. Potom sestav PDF a exportuj Word podle bloku níže.

1. Otevři `main.tex`.
2. Ulož soubor.
3. Spusť **LaTeX Workshop: Build LaTeX project**.
4. Otevři výsledné PDF.
5. Zkontroluj titulní část a úvodní kapitolu.

## Nápověda

| Příkaz | Význam |
|---|---|
| `\documentclass` | Definuje typ dokumentu a jeho základní vlastnosti. |
| `\usepackage` | Načítá rozšiřující balíčky. |
| `\title` | Nastavuje název článku. |
| `\author` | Nastavuje autora článku. |
| `\date` | Nastavuje datum. |
| `\today` | Automaticky vloží aktuální datum. |
| `\begin{document}` | Označuje začátek obsahu dokumentu. |
| `\maketitle` | Vygeneruje titulní část dokumentu. |
| `\section` | Vytváří číslovanou sekci. |
| `\end{document}` | Označuje konec dokumentu. |

**Poznámka:** Třída `article` používá pro hlavní části článku příkaz `\section`. Příkaz `\chapter` není v této třídě dostupný.

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

Challenge je dokončený, pokud:

- [ ] Dokument používá třídu `article`.
- [ ] Dokument má formát A4 a velikost písma 11 pt.
- [ ] Jsou správně načtené požadované balíčky.
- [ ] PDF obsahuje název článku, autora a datum.
- [ ] Úvodní sekce je správně očíslovaná.
- [ ] Úvodní odstavec se správně zobrazuje.
- [ ] Kompilace přes LaTeX Workshop proběhne bez chyb.

## Další Challenge

V **Challenge 03: Formátování a struktura odborného textu** začneš článek rozšiřovat o další sekce, podsekce a různé možnosti formátování.

[Zpět na přehled Hacku](../README.MD)
