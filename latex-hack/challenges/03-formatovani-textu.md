# Challenge 03: Struktura a formátování odborného textu


## Scénář

V předchozím Challenge jsi vytvořil první funkční verzi vědeckého článku *Exploring the Universe: From Stars to Black Holes*. Dokument zatím obsahuje titulní část a krátký úvod.

Nyní je čas připravit článek pro rozsáhlejší odborný text. Postupně přidáš abstrakt, několik tematických sekcí a podsekcí a vyzkoušíš si základní formátování textu.

Současně se naučíš rozdělit dokument do samostatných souborů. Díky tomu bude hlavní soubor `main.tex` přehledný, i když bude článek obsahovat větší množství textu, obrázků, tabulek a citací.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Organizovat obsah článku do samostatných `.tex` souborů.
- Propojovat soubory pomocí příkazů `\input` a `\include`.
- Vysvětlit rozdíly mezi těmito příkazy a vybrat vhodný způsob použití.
- Vytvořit abstrakt vědeckého článku.
- Používat sekce a podsekce.
- Formátovat text pomocí tučného písma a kurzívy.
- Vytvářet číslované a nečíslované seznamy.
- Správně zapisovat speciální znaky.

## Zadání

### Úkol 1: Rozděl dokument do samostatných souborů

V předchozím Challenge jsi vytvořil sekci `Introduction` přímo v souboru `main.tex`.

Nyní její obsah přesuň do souboru:

`chapters/introduction.tex`

V hlavním souboru původní sekci nahraď následujícím příkazem:

```latex
\input{chapters/introduction}
```

Příkaz `\input` načte obsah externího souboru a vloží jej na místo, kde je uveden.

V souboru `chapters/introduction.tex` ponech pouze samotnou sekci a její text. Nepřidávej do něj deklaraci dokumentu ani příkazy `\begin{document}` a `\end{document}`.

**Ověření:** Zkompiluj dokument pomocí LaTeX Workshop. Výsledné PDF by mělo vypadat stejně jako před přesunutím textu.

### Úkol 2: Vyzkoušej rozdíl mezi `\input` a `\include`

LaTeX nabízí dva základní příkazy pro načítání obsahu z externích souborů.

| Vlastnost                                  | `\input`               | `\include`                                  |
| ------------------------------------------ | ---------------------- | ------------------------------------------- |
| Načtení externího souboru                  | Ano                    | Ano                                         |
| Automatické zalomení stránky               | Ne                     | Ano, před i za vloženým obsahem             |
| Typické použití                            | Články, sekce, tabulky | Knihy, diplomové práce a rozsáhlé dokumenty |

**Praktický experiment:**

1. V souboru `main.tex` dočasně nahraď `\input{chapters/introduction}` příkazem `\include{chapters/introduction}`.
2. Zkompiluj dokument a sleduj, zda se změní rozložení stránek.
3. Pro experiment vytvoř `chapters/test.tex` s `\section{Temporary test}` a větou `Temporary content.` hned pod ní. V `main.tex` jej dočasně načti za úvodem a před `\end{document}`, nejprve pomocí `\input{chapters/test}`, potom `\include{chapters/test}`.
4. Porovnej výsledná PDF.
5. Vrať se k používání příkazu `\input` a odstraň dočasnou sekci i její načítání. Experiment nemění výsledný obsah článku.

Příkaz `\include` využívá `\clearpage`, který nejen zalomí stránku, ale také zajistí vysázení čekajících plovoucích objektů, například obrázků a tabulek.

U rozsáhlých dokumentů lze navíc pomocí `\includeonly` vybrat, které části se mají během kompilace zpracovat. Tento mechanismus je užitečný například při práci s dlouhou knihou.

**Doporučení:** Pro náš vědecký článek budeme používat `\input`, protože chceme, aby jednotlivé sekce plynule navazovaly bez zbytečných stránkových zlomů.

### Úkol 3: Přidej abstrakt

Vědecký článek obvykle začíná abstraktem, který stručně shrnuje jeho téma, zaměření a obsah.

V souboru `main.tex` vytvoř za příkazem `\maketitle` prostředí `abstract`:

```latex
\begin{abstract}
...
\end{abstract}
```

Do abstraktu vlož následující text:

> This paper provides an introductory overview of the universe, focusing on stars, galaxies, and black holes. It discusses fundamental astronomical concepts, observational methods, and selected physical principles that help explain the structure and evolution of the cosmos.

**Ověření:** Abstrakt se musí zobrazit mezi titulní částí dokumentu a sekcí `Introduction`.

### Úkol 4: Vytvoř strukturu článku

Připrav následující sekce v odpovídajících souborech:

| Soubor                            | Název sekce            |
| --------------------------------- | ---------------------- |
| `chapters/introduction.tex`       | Introduction           |
| `chapters/stars-and-galaxies.tex` | Stars and Galaxies     |
| `chapters/black-holes.tex`        | Black Holes            |
| `chapters/observations.tex`       | Observing the Universe |
| `chapters/conclusion.tex`         | Conclusion             |

V dosud prázdných souborech patří `\section{...}` na první řádek. V `introduction.tex` už nadpis máš; znovu jej nevkládej.

V `main.tex` za `\end{abstract}` a před `\end{document}` ponech právě tento blok (nahraď jím dosavadní samostatné načtení úvodu):

```latex
\input{chapters/introduction}
\input{chapters/stars-and-galaxies}
\input{chapters/black-holes}
\input{chapters/observations}
\input{chapters/conclusion}
```

Všimni si, že číslování sekcí nemusíš nastavovat ručně. LaTeX je automaticky očísluje podle jejich pořadí v dokumentu.

### Úkol 5: Přidej podsekce

V `chapters/stars-and-galaxies.tex` bezprostředně za `\section{Stars and Galaxies}` vytvoř v tomto pořadí dvě podsekce:

- The Life Cycle of Stars
- Types of Galaxies

V `chapters/black-holes.tex` bezprostředně za `\section{Black Holes}` vytvoř v tomto pořadí dvě podsekce:

- Formation of Black Holes
- Event Horizons

Použij příkaz:

```latex
\subsection{Název podsekce}
```

**Ověření:** Ve výsledném PDF by měly být podsekce automaticky očíslované například jako `2.1`, `2.2`, `3.1` a `3.2`.

### Úkol 6: Naformátuj odborný text

V `chapters/stars-and-galaxies.tex` za `\subsection{The Life Cycle of Stars}` a před `\subsection{Types of Galaxies}` vlož jako první odstavec:

> Stars are massive celestial objects primarily composed of hydrogen and helium. They generate energy through nuclear fusion. The evolution of a star depends largely on its initial mass.

Uprav text tak, aby:

- Výraz **nuclear fusion** byl tučný.
- Výraz *initial mass* byl kurzívou.

Použij příkazy `\textbf{}` a `\textit{}`.

Zkus oddělit poslední větu prázdným řádkem; po experimentu ponech celý text jako jeden odstavec.

### Úkol 7: Vytvoř nečíslovaný seznam

V `chapters/stars-and-galaxies.tex` hned za `\subsection{Types of Galaxies}` vlož větu:

> Galaxies can be classified into several major categories:

Pod ni vytvoř nečíslovaný seznam pomocí prostředí `itemize`:

- Spiral galaxies
- Elliptical galaxies
- Irregular galaxies

Každá položka musí být uvedena pomocí příkazu `\item`.

### Úkol 8: Vytvoř číslovaný seznam

V `chapters/observations.tex` použij už vytvořenou sekci `Observing the Universe`; druhý nadpis nepřidávej.

Bezprostředně za nadpis `\section{Observing the Universe}` vlož větu:

> A typical scientific observation process includes:

Následně vytvoř číslovaný seznam pomocí prostředí `enumerate`:

1. Collect observational data.
2. Process and calibrate measurements.
3. Analyze the results.
4. Interpret the astronomical findings.

**Ověření:** Čísla položek musí být generována automaticky.

### Úkol 9: Pracuj se speciálními znaky

Některé znaky mají v LaTeXu speciální význam a nelze je do textu zapisovat přímo.

V `chapters/observations.tex` za `\end{enumerate}` přidej jako nový odstavec následující dvě věty:

> Modern astronomy combines observations, data analysis & computational models.

> Observational data require careful calibration to achieve uncertainties below 1% in suitable measurements.

Zajisti správné zobrazení znaků `&` a `%` pomocí příslušných LaTeX příkazů.

Další znaky z tabulky můžeš dočasně zkusit v tomtéž odstavci; po experimentu je odstraň:

| Znak | Zápis v LaTeXu |
| ---- | -------------- |
| `&`  | `\&`           |
| `%`  | `\%`           |
| `$`  | `\$`           |
| `#`  | `\#`           |
| `_`  | `\_`           |
| `{`  | `\{`           |
| `}`  | `\}`           |

**Pozor:** Znak `%` v LaTeXu běžně označuje začátek komentáře. Pokud jej nezapíšeš jako `\%`, zbytek řádku nebude zpracován jako obsah dokumentu.

### Úkol 10: Doplň zbývající obsah

V `chapters/black-holes.tex` bezprostředně za `\subsection{Formation of Black Holes}` vlož jako první odstavec:

> Black holes can form when massive stars collapse under their own gravity at the end of their life cycles.

V témže souboru bezprostředně za `\subsection{Event Horizons}` vlož jako první odstavec:

> The event horizon is the boundary beyond which light and other signals cannot escape to distant observers.

V `chapters/conclusion.tex` bezprostředně za `\section{Conclusion}` vlož jako první odstavec:

> The study of the universe connects observations with fundamental physical principles. Understanding stars, galaxies, and black holes helps scientists investigate the history and evolution of the cosmos.

Tím bude mít článek základní obsah, který v následujících Challenges rozšíříš o citace, obrázky, tabulky a matematické rovnice.

## Nápověda

| Příkaz nebo prostředí | Význam                                                               |
| --------------------- | -------------------------------------------------------------------- |
| `\input{soubor}`      | Načte obsah externího souboru bez automatického stránkového zlomu.   |
| `\include{soubor}`    | Načte externí soubor a oddělí jej stránkovými zlomy.                 |
| `\includeonly{...}`   | Umožňuje zpracovat pouze vybrané soubory načítané pomocí `\include`. |
| `abstract`            | Prostředí pro abstrakt vědeckého článku.                             |
| `\section{}`          | Vytvoří číslovanou sekci.                                            |
| `\subsection{}`       | Vytvoří číslovanou podsekci.                                         |
| `\textbf{}`           | Tučné písmo.                                                         |
| `\textit{}`           | Kurzíva.                                                             |
| `itemize`             | Nečíslovaný seznam.                                                  |
| `enumerate`           | Číslovaný seznam.                                                    |
| `\item`               | Položka seznamu.                                                     |
| `\&`                  | Znak `&`.                                                            |
| `\%`                  | Znak `%`.                                                            |

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

- [ ] Hlavní soubor `main.tex` načítá jednotlivé sekce pomocí `\input`.
- [ ] Úvodní text je přesunut do `chapters/introduction.tex`.
- [ ] Dokážeš vysvětlit rozdíl mezi `\input` a `\include`.
- [ ] Dokument obsahuje abstrakt.
- [ ] Dokument obsahuje všech pět požadovaných sekcí.
- [ ] Podsekce jsou správně automaticky očíslované.
- [ ] V textu je použité tučné písmo a kurzíva.
- [ ] Dokument obsahuje nečíslovaný i číslovaný seznam.
- [ ] Speciální znaky se zobrazují správně.
- [ ] Dokument se bez chyb kompiluje pomocí LaTeX Workshop.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)
