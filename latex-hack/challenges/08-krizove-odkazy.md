# Challenge 08: Křížové odkazy v dokumentu

## Scénář

Tvůj vědecký článek *Exploring the Universe: From Stars to Black Holes* už obsahuje několik sekcí, obrázky, tabulky, citace a matematické rovnice. V odborném textu ale potřebujeme čtenáře také odkazovat na konkrétní části dokumentu: například „viz obrázek 1“, „podle rovnice (2)“ nebo „v sekci 3“.

Kdybys čísla psal ručně, každé přidání nové sekce nebo obrázku by mohlo odkazy rozbít. LaTeX proto nabízí **křížové odkazy**, které se aktualizují automaticky.

## Cíle

Po dokončení Challenge budeš umět:

- Označovat sekce, obrázky, tabulky a rovnice příkazem `\label`.
- Odkazovat na ně pomocí `\ref` a `\eqref`.
- Rozlišovat mezi číselným odkazem a textem, který jej obklopuje.
- Používat `hyperref` pro klikatelné odkazy v PDF.
- Používat `cleveref` pro automatické názvy odkazovaných objektů.
- Řešit běžné chyby, například `??` místo čísla odkazu.

## Zadání

### Úkol 1: Připrav balíčky pro odkazy

V `main.tex` do preambule, za `\usepackage{amsmath}` a před `\title`, přidej tyto balíčky:

```latex
\usepackage[hidelinks]{hyperref}
\usepackage[capitalise,noabbrev]{cleveref}
```

**Důležité:** `cleveref` načítej **až po** `hyperref`. `hyperref` vytváří klikatelné odkazy; `cleveref` k nim automaticky doplňuje označení typu objektu (například *Figure*, *Table* nebo *Section*). Volba `hidelinks` skryje barevné rámečky kolem odkazů. Volby `capitalise,noabbrev` zajistí například tvar *Figure 1* místo zkráceného *fig. 1*.

Balíčky přidej k již existujícím balíčkům z předchozích Challenges; nemaž konfiguraci `biblatex`, `graphicx`, `booktabs`, `siunitx` ani `amsmath`.

### Úkol 2: Označ sekce

Do souboru `chapters/black-holes.tex` přidej identifikátor hned za nadpis sekce:

```latex
\section{Black Holes}
\label{sec:black-holes}
```

V `chapters/stars-and-galaxies.tex` přidej bezprostředně za `\section{Stars and Galaxies}` druhý identifikátor:

```latex
\section{Stars and Galaxies}
\label{sec:stars-and-galaxies}
```

V `chapters/introduction.tex`, v sekci *Introduction*, za odstavec s citací `hawking1988` přidej nový odstavec:

```latex
Black holes are discussed in Section~\ref{sec:black-holes}.
```

Všimni si znaku `~`: jde o **nezalomitelnou mezeru**, která zabrání oddělení slova *Section* od jeho čísla na konci řádku.

### Úkol 3: Odkazuj na obrázek

Najdi obrázek typů galaxií z Challenge 05. Ujisti se, že obsahuje `\label` **až za** `\caption`:

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/images/galaxy-types.png}
    \caption{Major galaxy morphologies: spiral, elliptical, and irregular.}
    \label{fig:galaxy-types}
\end{figure}
```

V `chapters/stars-and-galaxies.tex`, v podsekci *Types of Galaxies*, mezi `\end{itemize}` a první `\begin{figure}` přidej odstavec:

```latex
The main galaxy categories are illustrated in
Figure~\ref{fig:galaxy-types}.
```

**Poznámka:** Pokud jsi v předchozím Challenge použil jiný název souboru nebo identifikátor, zachovej svůj skutečný název a použij jej konzistentně v odkazu.

### Úkol 4: Odkazuj na tabulku

Najdi tabulku vlastností hvězd z Challenge 06. Ujisti se, že její prostředí `table` obsahuje popisek a identifikátor:

```latex
\begin{table}[htbp]
    \centering
    \caption{Illustrative properties of selected stars}
    \label{tab:stellar-properties}
    % Zde ponech existující prostředí tabular.
\end{table}
```

Tento příklad ukazuje **umístění popisku a identifikátoru**, nikoliv úplnou tabulku. Zachovej skutečný obsah své tabulky z Challenge 06.

V `chapters/stars-and-galaxies.tex` už před `\input{tables/stellar-properties}` z Challenge 06 máš následující větu. Pouze ji zkontroluj; další kopii nevkládej:

```latex
Selected properties of stars are summarized in
Table~\ref{tab:stellar-properties}.
```

### Úkol 5: Odkazuj na matematickou rovnici

V kapitole *Black Holes* najdi Schwarzschildův poloměr z Challenge 07. Stávající nečíslovaný blok `\[...\]` pro `r_s` z Challenge 07 **nahraď** následujícím prostředím; druhou rovnici nepřidávej:

```latex
\begin{equation}
    r_s = \frac{2GM}{c^2}
    \label{eq:schwarzschild-radius}
\end{equation}
```

V `chapters/black-holes.tex`, v podsekci *Event Horizons*, mezi odstavec *The Schwarzschild radius is denoted…* a právě upravené `\begin{equation}` přidej odstavec:

```latex
The Schwarzschild radius is calculated using
Equation~\eqref{eq:schwarzschild-radius}.
```

Příkaz `\eqref` z balíčku `amsmath` vrací číslo rovnice **v kulatých závorkách**. Proto už závorky do textu ručně nepřidávej.

Porovnej:

| Příkaz | Typický výsledek |
|---|---|
| `\ref{eq:schwarzschild-radius}` | `1` |
| `\eqref{eq:schwarzschild-radius}` | `(1)` |

*Konkrétní číslo závisí na pořadí rovnic v dokumentu.*

### Úkol 6: Vyzkoušej automatické odkazy pomocí `cleveref`

Příkaz `\ref` vrací pouze číslo. V následujících dočasných experimentech nahraď v existujících větách odkazy na obrázek, tabulku a Schwarzschildovu rovnici pomocí `\cref`; nové duplicitní odstavce nepřidávej:

```latex
As shown in \cref{fig:galaxy-types}, galaxies can
have different shapes.

The values are compared in \cref{tab:stellar-properties}.

The event horizon is related to \cref{eq:schwarzschild-radius}.
```

Porovnej následující přístupy:

| Zápis | Typický výsledek |
|---|---|
| `Figure~\ref{fig:galaxy-types}` | Figure 1 |
| `\cref{fig:galaxy-types}` | Figure 1 |
| `\cref{tab:stellar-properties}` | Table 1 |
| `\cref{eq:schwarzschild-radius}` | Equation (1) |

Protože jsme nastavili `capitalise`, používá `\cref` velká počáteční písmena. Příkaz `\Cref` lze využít také, zejména pokud v budoucnu tuto volbu změníš.

**Pozor:** S `\cref` už před odkaz nepiš `Figure`, `Table` ani `Equation` — jinak by se označení zdvojilo.

### Úkol 7: Odkazuj na více objektů najednou

V `chapters/introduction.tex` za odstavec *Black holes are discussed…* dočasně vlož větu:

```latex
The main topics are introduced in
\cref{sec:stars-and-galaxies,sec:black-holes}.
```

`cleveref` dokáže více odkazů vhodně spojit. Výsledek závisí na číslování a jazykovém nastavení dokumentu.

Po experimentu tuto větu odstraň a v úkolu 6 vrať původní věty s `\ref` a `\eqref`. Zůstane společný výchozí stav pro další Challenge. Tyto příkazy se učíme pro PDF. Přímý export Pandocem nezaručuje převod jejich čísel a klikatelnosti do Wordu; postup pro Word je uveden níže.

### Úkol 8: Ověř klikatelnost odkazů

Zkompiluj dokument pomocí **LaTeX Workshop** a otevři výsledné PDF.

1. Klikni na odkaz na obrázek.
2. Klikni na odkaz na tabulku.
3. Klikni na odkaz na rovnici.
4. Ověř, že tě PDF prohlížeč přenese na odpovídající místo.

Pokud používáš vestavěný prohlížeč PDF ve VS Code, ověř odkazy přímo v něm. Chování navigace se může mírně lišit podle prohlížeče.

### Úkol 9: Otestuj automatické přečíslování

Před obrázek typů galaxií dočasně vlož jiný obrázek s vlastním popiskem (můžeš použít druhý obrázek z Challenge 05). Potom dokument znovu sestav.

Sleduj, zda se číslo původního obrázku i odkaz v textu automaticky aktualizují. Následně dočasný obrázek včetně jeho popisku a vlastního unikátního `\label{fig:temporary}` odstraň a spusť znovu sestavení PDF a export do Wordu.

**Smysl experimentu:** Odkazy jsou navázané na identifikátory, nikoliv na ručně napsaná čísla.

## Dokončení odkazů v MS Wordu

Automatické odkazy výše ověřuj v PDF. Pandoc nepoužívá LaTeXové pomocné soubory a nepřenáší spolehlivě číslování popisků a rovnic. Po přímém exportu proto v DOCX:

1. U každého ze dvou obrázků a dvou tabulek ponech věcný popis a přes **Reference → Vložit titulek** doplň odpovídající označení a automatické číslo. Pokud titulek vkládáš znovu, odstraň původní nečíslovaný popisek, aby nebyl dvakrát.
2. Pro tři číslované rovnice zvol konzistentní číslování pomocí titulků s označením *Equation*. Čísla ve Wordu nemusí být umístěna typograficky stejně jako v PDF.
3. V odstavcích *The main galaxy categories are illustrated…*, *Selected properties of stars are summarized…*, *The main morphological categories are summarized…* a *The Schwarzschild radius is calculated…* nahraď převedené číslo nebo značku typu `[eq:schwarzschild-radius]` přes **Reference → Křížový odkaz** odkazem na odpovídající titulek. Zaškrtni vložení jako hypertextový odkaz. Zachovej větu a nepřidávej další odstavec.
4. V úvodu zkontroluj odkaz *Black holes are discussed in Section…*. Pokud nefunguje, nahraď jeho číslo křížovým odkazem na nadpis *Black Holes*.
5. Aktualizuj pole a otestuj odkazy. Po dalším exportu se ruční úpravy DOCX musí provést znovu; hotový Word si ulož jako samostatnou finální kopii.

To je ruční dokončení přímo ve Wordu, bez dalších nástrojů. Ze samotného přímého exportu neslibujeme hotové číslování a odkazy.

## Nápověda

### Doporučené názvy identifikátorů

| Typ objektu | Prefix | Příklad |
|---|---|---|
| Sekce | `sec:` | `\label{sec:black-holes}` |
| Obrázek | `fig:` | `\label{fig:galaxy-types}` |
| Tabulka | `tab:` | `\label{tab:stellar-properties}` |
| Rovnice | `eq:` | `\label{eq:schwarzschild-radius}` |

Prefixy nejsou povinné, ale výrazně usnadňují orientaci ve větším projektu. **Každý identifikátor musí být v dokumentu jedinečný.**

### Kam umístit `\label`?

- U sekcí: obvykle bezprostředně za `\section` nebo `\subsection`.
- U obrázků a tabulek: za `\caption`, aby identifikátor odkazoval na správné číslo objektu.
- U rovnic: uvnitř číslovaného prostředí `equation` nebo na odpovídajícím řádku `align`.

### Proč se místo čísla zobrazuje `??`?

Nejčastější příčiny:

1. Identifikátor v `\ref` nebo `\cref` neodpovídá žádnému `\label`.
2. V identifikátoru je překlep.
3. Dokument nebyl zkompilován dostatečněkrát, aby se odkazy aktualizovaly.
4. Některý soubor nebyl načten pomocí `\input`.

LaTeX ukládá informace o odkazech do pomocných souborů. Při běžném sestavení pomocí LaTeX Workshop s `latexmk` se potřebné průchody obvykle provedou automaticky. Pokud odkaz zůstává nevyřešený, zkontroluj log sestavení a spusť build znovu.

### `\ref`, `\eqref` a `\cref` – rychlé srovnání

| Příkaz | Kdy jej použít |
|---|---|
| `\ref{...}` | Potřebuješ samotné číslo sekce, obrázku nebo tabulky. |
| `\eqref{...}` | Potřebuješ číslo rovnice v závorkách. |
| `\cref{...}` | Chceš automaticky doplnit také typ objektu. |
| `\Cref{...}` | Chceš variantu s velkým počátečním písmenem, zejména na začátku věty. |

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx --citeproc --bibliography=references.bib --csl=styles/apa.csl
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

- [ ] V preambuli mám načtené `hyperref` a následně `cleveref`.
- [ ] Sekce *Stars and Galaxies* a *Black Holes* mají vlastní identifikátory.
- [ ] Umím odkazovat na obrázek pomocí `\ref`.
- [ ] Umím odkazovat na tabulku pomocí `\ref`.
- [ ] Umím odkazovat na rovnici pomocí `\eqref`.
- [ ] Rozumím rozdílu mezi `\ref`, `\eqref` a `\cref`.
- [ ] Odkazy ve výsledném PDF jsou klikatelné.
- [ ] Po změně pořadí objektů se odkazy automaticky přečíslují.
- [ ] Dokument se úspěšně sestaví přes LaTeX Workshop bez nevyřešených odkazů.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](../DILCI-RESENI.md).

## Další Challenge

V **Challenge 09: Pokročilé funkce LaTeXu** se zaměříme na další nástroje pro přípravu odborného textu, například vlastní příkazy, poznámky pod čarou a užitečné typografické prvky.

[Zpět na přehled Hacku](../README.MD)
