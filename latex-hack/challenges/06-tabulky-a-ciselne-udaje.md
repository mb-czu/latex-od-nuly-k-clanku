# Challenge 06: Tabulky a práce s číselnými údaji

## Scénář

V předchozích Challenges jsi vytvořil odborný článek *Exploring the Universe: From Stars to Black Holes*, doplnil citace a vložil obrázky. Vědecké články ale často potřebují také přehledně porovnávat údaje. K tomu slouží tabulky.

V tomto Challenge vytvoříš jednoduchou tabulku, naučíš se rozlišovat prostředí `table` a `tabular`, vyzkoušíš profesionálnější vzhled s `booktabs` a zarovnání čísel s `siunitx`. Všechny texty samotného článku zůstávají v angličtině.

## Cíle

Po dokončení budeš umět:

- Vytvořit tabulku pomocí prostředí `tabular`.
- Rozlišit strukturu tabulky (`tabular`) od plovoucího objektu (`table`).
- Nastavit sloupce a zarovnání pomocí `l`, `c` a `r`.
- Použít `&` pro oddělení buněk a `\\` pro ukončení řádku.
- Vytvořit popisek a identifikátor tabulky pomocí `\caption` a `\label`.
- Formátovat odborné tabulky pomocí balíčku `booktabs`.
- Zarovnat číselné údaje pomocí sloupce `S` z balíčku `siunitx`.
- Správně zapisovat fyzikální jednotky a odkazovat na tabulky v textu.

## Zadání

### Úkol 1: Připrav soubor pro tabulku

Ve složce `tables/` vytvoř soubor:

`tables/stellar-properties.tex`

Tabulku budeme uchovávat v samostatném souboru, aby hlavní kapitoly zůstaly přehledné. Do souboru **nevkládej** `\documentclass` ani `\begin{document}`.

Do `chapters/stars-and-galaxies.tex` v podsekci *The Life Cycle of Stars* za odstavec s `\textcite{carroll2007}` a před `\subsection{Types of Galaxies}` přidej větu:

> Selected properties of stars are summarized in Table~\ref{tab:stellar-properties}.

Na následující řádek vlož:

```latex
\input{tables/stellar-properties}
```

Zatím se může zobrazovat varování o nevyřešeném odkazu. To odstraníme po vytvoření tabulky.

### Úkol 2: Vytvoř jednoduchou tabulku

Do souboru `tables/stellar-properties.tex` vlož:

```latex
\begin{tabular}{lcr}
Star & Type & Approx. mass (solar masses) \\
Sun & G-type & 1.0 \\
Sirius A & A-type & 2.1 \\
Betelgeuse & Red supergiant & 16.5 \\
\end{tabular}
```

**Jak zápis funguje:**

| Zápis     | Význam                                                                       |
| --------- | ---------------------------------------------------------------------------- |
| `{lcr}`   | Tři sloupce: zarovnání vlevo, na střed a vpravo.                             |
| `&`       | Odděluje jednotlivé buňky v řádku.                                           |
| `\\`      | Ukončuje řádek tabulky.                                                      |
| `tabular` | Sází samotnou mřížku buněk; automaticky nevytváří popisek ani číslo tabulky. |

**Ověření:** Zkompiluj dokument pomocí LaTeX Workshop a ověř, že jsou hodnoty ve třech sloupcích. Uvedené hmotnosti jsou pouze orientační výukové hodnoty, nikoli přesný vědecký datový soubor.

### Úkol 3: Přidej prostředí `table`, popisek a identifikátor

Obal `tabular` prostředím `table` a přidej centrování, popisek a identifikátor:

```latex
\begin{table}[htbp]
    \centering
    \caption{Illustrative properties of selected stars}
    \label{tab:stellar-properties}
    \begin{tabular}{lcr}
        Star & Type & Approx. mass (solar masses) \\
        Sun & G-type & 1.0 \\
        Sirius A & A-type & 2.1 \\
        Betelgeuse & Red supergiant & 16.5 \\
    \end{tabular}
\end{table}
```

**Rozdíl mezi prostředími:** `tabular` vytváří řádky a sloupce; `table` je plovoucí objekt, který umožňuje popisek, automatické číslování a umístění podobně jako `figure` u obrázků.

Parametry `[htbp]` vymezují povolená umístění: přibližně zde (`h`), nahoře (`t`), dole (`b`) nebo na stránce pro plovoucí objekty (`p`). Nejde o pořadí příkazů, které by LaTeX musel postupně vykonat.

**Ověření:** Tabulka má automaticky očíslovaný popisek. Po opakované kompilaci by měl fungovat i odkaz `\ref{tab:stellar-properties}` v kapitole.

### Úkol 4: Vylepši vzhled pomocí `booktabs`

Odborné články obvykle používají čisté tabulky bez svislých čar. Balíček `booktabs` nabízí tři typy vodorovných linek.

Do preambule `main.tex`, za `\usepackage{graphicx}` a před `\title`, přidej:

```latex
\usepackage{booktabs}
```

V tabulce použij:

```latex
\begin{table}[htbp]
    \centering
    \caption{Illustrative properties of selected stars}
    \label{tab:stellar-properties}
    \begin{tabular}{lcr}
        \toprule
        Star & Type & Approx. mass (solar masses) \\
        \midrule
        Sun & G-type & 1.0 \\
        Sirius A & A-type & 2.1 \\
        Betelgeuse & Red supergiant & 16.5 \\
        \bottomrule
    \end{tabular}
\end{table}
```

| Příkaz        | Význam                      |
| ------------- | --------------------------- |
| `\toprule`    | Horní linka tabulky.        |
| `\midrule`    | Linka mezi záhlavím a daty. |
| `\bottomrule` | Spodní linka tabulky.       |

**Ověření:** Tabulka je čitelná bez svislých linek a záhlaví je jasně oddělené od dat.

### Úkol 5: Zarovnej čísla pomocí `siunitx`

Číselné údaje bývají přehlednější, pokud jsou zarovnané podle desetinné značky. K tomu slouží sloupec `S` z balíčku `siunitx`.

Do preambule `main.tex`, bezprostředně za `\usepackage{booktabs}`, přidej:

```latex
\usepackage{siunitx}
```

Pro experiment v `tables/stellar-properties.tex` dočasně změň třetí sloupec z `r` na `S[table-format=2.1]`. Protože záhlaví obsahuje text, vlož jej do `\multicolumn`:

```latex
\begin{table}[htbp]
    \centering
    \caption{Illustrative properties of selected stars}
    \label{tab:stellar-properties}
    \begin{tabular}{lcS[table-format=2.1]}
        \toprule
        Star & Type & \multicolumn{1}{c}{Mass ($M_\odot$)} \\
        \midrule
        Sun & G-type & 1.0 \\
        Sirius A & A-type & 2.1 \\
        Betelgeuse & Red supergiant & 16.5 \\
        \bottomrule
    \end{tabular}
\end{table}
```

`table-format=2.1` rezervuje prostor pro nejvýše dvě číslice před desetinnou tečkou a jednu za ní. Symbol `$M_\odot$` označuje hmotnost Slunce, kterou zde používáme jako jednotku porovnání.

**Ověření experimentu:** Sestav PDF a exportuj Word. V PDF jsou čísla `1.0`, `2.1` a `16.5` zarovnaná podle desetinné tečky; v Pandocu sloupec `S` není spolehlivě podporovaný a tabulka se může změnit na obyčejný text.

**Výsledný stav pro další úkoly:** V `tables/stellar-properties.tex` vrať deklaraci na `\begin{tabular}{lcr}` a hlavičku třetího sloupce ponech jako `Mass ($M_\odot$)`. Obal `\multicolumn{1}{c}{...}` odstraň. Znovu sestav oba formáty a ověř skutečnou tabulku se třemi sloupci. V tomto příkladu mají všechny hodnoty jedno desetinné místo, takže pravé zarovnání srovná i desetinné tečky. Balíček `siunitx` ponech pro následující jednotky.

### Úkol 6: Vyzkoušej fyzikální jednotky

Balíček `siunitx` umožňuje zapisovat čísla a jednotky jednotným způsobem. V `chapters/stars-and-galaxies.tex`, v podsekci *The Life Cycle of Stars*, mezi první odstavec končící *initial mass* a odstavec s `\textcite{carroll2007}` vlož nový odstavec:

```latex
The Sun has a mass of approximately
\qty{1.989e30}{\kilogram}.
Its effective surface temperature is about
\qty{5772}{\kelvin}.
```

| Příkaz                | Účel                             |
| --------------------- | -------------------------------- |
| `\num{1.989e30}`      | Vysází číslo ve vědeckém zápisu. |
| `\unit{\kilogram}`    | Vysází samostatnou jednotku.     |
| `\qty{5772}{\kelvin}` | Vysází hodnotu včetně jednotky.  |

**Poznámka:** Používáme syntaxi moderního `siunitx` verze 3. Pokud příkaz `\qty` nefunguje, ověř aktualizaci své distribuce LaTeXu.

### Úkol 7: Přidej druhou tabulku

Ve složce `tables/` vytvoř soubor `galaxy-types.tex` a vlož do něj:

```latex
\begin{table}[htbp]
    \centering
    \caption{Basic galaxy classifications}
    \label{tab:galaxy-types}
    \begin{tabular}{ll}
        \toprule
        Galaxy type & Typical characteristic \\
        \midrule
        Spiral & Disk with spiral arms \\
        Elliptical & Smooth, rounded appearance \\
        Irregular & No regular overall shape \\
        \bottomrule
    \end{tabular}
\end{table}
```

V `chapters/stars-and-galaxies.tex`, v podsekci *Types of Galaxies*, za `\end{figure}` obrázku `fig:galaxy-types` přidej:

```latex
\input{tables/galaxy-types}
```

Před tabulku vlož větu:

```latex
The main morphological categories are summarized
in Table~\ref{tab:galaxy-types}.
```

Všimni si znaku `~`: jde o nezalomitelnou mezeru, takže `Table` a její číslo zůstanou pohromadě.

### Úkol 8: Experimentuj s šířkou a umístěním

Vyzkoušej u tabulky změnit `\begin{table}[htbp]` na `\begin{table}[ht]` a sleduj rozdíl v PDF. Pokud se tabulka nepřesune, není to chyba: dostupné místo může vést ke stejnému výsledku.

Dále si vyzkoušej změnit zarovnání druhého sloupce tabulky galaxií z `l` na `c` nebo `r` a porovnej čitelnost.

Po experimentu vrať `[htbp]` a u druhé tabulky sloupce `{ll}`.

**Důležité:** Pokud je tabulka širší než stránka, LaTeX ji sám automaticky nezmenší. Pro tento Challenge stačí krátké tabulky; složitější řešení širokých tabulek necháme na později.

### Úkol 9: Ověř výsledný článek

Zkompiluj celý projekt přes **LaTeX Workshop** ve VS Code. Při použití citací z Challenge 04 musí konfigurace kompilace nadále zpracovat také Biber. Po změnách odkazů může být nutné spustit sestavení znovu, aby se čísla tabulek aktualizovala.

V PDF ověř dvě očíslované tabulky a funkční odkazy. Ve Wordu ověř dvě skutečné tabulky se správným obsahem; pokud chybí čísla a funkční odkazy, dokonči je přímo ve Wordu podle postupu v Challenge 08.

## Nápověda

| Příkaz nebo prostředí                 | Význam                                                  |
| ------------------------------------- | ------------------------------------------------------- |
| `table`                               | Plovoucí prostředí pro tabulku s popiskem a číslováním. |
| `tabular`                             | Struktura buněk, řádků a sloupců.                       |
| `l`, `c`, `r`                         | Zarovnání textu vlevo, na střed a vpravo.               |
| `&`                                   | Oddělovač sloupců.                                      |
| `\\`                                  | Konec řádku.                                            |
| `\centering`                          | Vodorovné vycentrování tabulky.                         |
| `\caption{}`                          | Popisek tabulky.                                        |
| `\label{}`                            | Identifikátor pro odkazy.                               |
| `\ref{}`                              | Vložení čísla odkazovaného objektu.                     |
| `\toprule`, `\midrule`, `\bottomrule` | Linky z balíčku `booktabs`.                             |
| `S`                                   | Číselný sloupec z `siunitx`.                            |
| `\num{}`, `\unit{}`, `\qty{}{}`       | Formátování čísel a fyzikálních jednotek.               |

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx --citeproc --bibliography=references.bib --csl=styles/apa.csl
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../přílohy/BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

- [ ] Rozumíš rozdílu mezi `table` a `tabular`.
- [ ] Umíš vytvořit řádky, sloupce a nastavit zarovnání.
- [ ] Tabulky jsou uložené v samostatných souborech ve složce `tables/`.
- [ ] Obě tabulky mají popisek a unikátní `\label` s prefixem `tab:`.
- [ ] Obě tabulky používají `booktabs`.
- [ ] Vyzkoušel jsem sloupec `S`; výsledná tabulka používá přenosné `{lcr}` a správně se převede i do Wordu.
- [ ] Umíš zapsat fyzikální veličinu pomocí `\qty`.
- [ ] Odkazy na tabulky se správně zobrazují v textu.
- [ ] Dokument se kompiluje bez chyb přes LaTeX Workshop.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Dílčí řešení úkolů 01–09 najdeš v [checkpointech](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)
