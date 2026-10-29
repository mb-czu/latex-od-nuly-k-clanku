# Challenge 05: Obrázky a ilustrace

## Scénář

V předchozích Challenges jsi vytvořil strukturovaný vědecký článek *Exploring the Universe: From Stars to Black Holes* a doplnil do něj odborné citace. Nyní článek rozšíříš o vizuální materiály.

Ve vědeckém textu obrázek neslouží jen jako dekorace. Měl by doplňovat argumentaci, mít srozumitelný popisek a být uvedený ve správném kontextu. Naučíš se proto vkládat obrázky, upravovat jejich rozměry, řídit umístění a připravovat popisky a identifikátory pro pozdější automatické odkazy.

## Cíle

Po dokončení Challenge budeš umět:

- Načíst balíček `graphicx`.
- Vložit obrázek pomocí `\includegraphics`.
- Používat prostředí `figure` a rozumět plovoucím objektům.
- Nastavit šířku obrázku vzhledem k šířce textu.
- Vytvořit automaticky číslovaný popisek pomocí `\caption`.
- Přidat identifikátor obrázku pomocí `\label`.
- Rozlišovat formáty PNG, JPG a PDF.
- Organizovat obrazové soubory v projektu.
- Zkontrolovat zdroj a licenci převzatého obrázku.

## Výchozí stav

Pokračuj v projektu z Challenge 04. Dokument má hlavní soubor `main.tex`, kapitoly v `chapters/` a funkční bibliografii.

Zkopíruj soubory `galaxy-types.png` a `black-hole-diagram.png` z `latex-hack/solution/figures/images/` do `project/figures/images/`. Obsah řešení přitom nekopíruj. Obrázky v `attachments/` mají jiné názvy a nejsou vstupem těchto ukázek.

> Vždy pokračuj ve vlastním `project/`; `solution/` slouží ke srovnání.

## Zadání

### Úkol 1: Připrav obrázek a zkontroluj strukturu projektu

Zkontroluj, že v projektu existuje následující struktura:

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
└── figures/
    ├── images/
    │   └── galaxy-types.png
    └── definitions/
```

Adresář `images/` slouží pro obrázky vkládané do dokumentu. Adresář `definitions/` můžeš v budoucnu využít pro jejich zdrojové soubory, například diagramy.

### Úkol 2: Načti balíček `graphicx`

V souboru `main.tex` přidej do preambule, za `\addbibresource{references.bib}` a před `\title`, příkaz:

```latex
\usepackage{graphicx}
```

Balíček `graphicx` zpřístupňuje příkaz `\includegraphics`, který umožňuje vkládat externí obrázky.

### Úkol 3: Vlož první obrázek

Otevři `chapters/stars-and-galaxies.tex`. V podsekci *Types of Galaxies* bezprostředně za `\end{itemize}` přidej obrázek pomocí prostředí `figure`:

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/images/galaxy-types.png}
    \caption{Schematic illustration of three galaxy types.}
    \label{fig:galaxy-types}
\end{figure}
```

**Důležité:** Cesta k obrázku se vyhodnocuje vzhledem k hlavnímu souboru `main.tex`, nikoliv vzhledem k souboru `stars-and-galaxies.tex`.

Zkompiluj dokument přes **LaTeX Workshop** a ověř, že se obrázek zobrazí s automaticky vytvořeným číslem a popiskem.

### Úkol 4: Vyzkoušej změnu velikosti

Postupně vyzkoušej tyto varianty:

```latex
\includegraphics[width=0.5\textwidth]{figures/images/galaxy-types.png}
```

```latex
\includegraphics[width=\textwidth]{figures/images/galaxy-types.png}
```

```latex
\includegraphics[width=8cm]{figures/images/galaxy-types.png}
```

Porovnej výsledné PDF. Nakonec se vrať k `width=0.8\textwidth`.

Při zadání pouze šířky zachovává LaTeX poměr stran obrázku. Pokud potřebuješ omezit oba rozměry, můžeš použít například:

```latex
\includegraphics[
    width=\textwidth,
    height=6cm,
    keepaspectratio
]{figures/images/galaxy-types.png}
```

### Úkol 5: Experimentuj s umístěním obrázku

Prostředí `figure` vytváří **plovoucí objekt**. LaTeX proto může obrázek přesunout na vhodnější místo, aby bylo rozložení stránky kvalitní.

Vyzkoušej postupně volby `[h]`, `[t]`, `[b]` a `[p]` a sleduj změny ve výsledném PDF.

| Volba | Význam |
|---|---|
| `h` | Pokusí se obrázek umístit přibližně na aktuální místo (*here*). |
| `t` | Umožní umístění v horní části stránky (*top*). |
| `b` | Umožní umístění ve spodní části stránky (*bottom*). |
| `p` | Umožní umístění na samostatné stránce plovoucích objektů (*page*). |
| `!` | Uvolňuje některá interní omezení pro umisťování plovoucích objektů. |

#### Kombinování parametrů

Parametry můžeme libovolně kombinovat. Neurčují však pořadí, ve kterém má LaTeX možnosti vyzkoušet. Pouze vymezují povolená umístění.

**Například:**

|Zápis| Chování|
|-----|--------|
|[h]| Pokusí se umístit obrázek na aktuální místo. Pokud to není možné, LaTeX může tuto volbu automaticky rozšířit na [ht].|
|[ht]|Povoluje aktuální místo nebo horní část stránky.|
|[htb]|Povoluje aktuální místo, horní nebo spodní část stránky.|
|[htbp]|Povoluje všechny čtyři základní možnosti umístění.|
|[!htbp]|Stejné možnosti jako [htbp], ale s uvolněním některých omezení pro umístění.|

Důležité: Zápis [htbp] neznamená „nejprve zkus h, potom t, následně b a nakonec p“. LaTeX používá vlastní algoritmus pro umisťování plovoucích objektů a rozhoduje také podle dostupného místa a nastavených pravidel sazby.

Volby jsou **doporučení, nikoliv příkazy k přesnému umístění**. Kombinace `[htbp]` poskytuje LaTeXu více možností a je pro běžný článek vhodným výchozím nastavením.

> Pokud je dokument zatím krátký, rozdíl nemusí být výrazný. To je v pořádku: umístění plovoucích objektů závisí na množství textu a dostupném prostoru.

### Úkol 6: Uprav popisek a identifikátor

V právě vloženém prostředí `figure` nahraď obsah `\caption` tímto textem:

> Major galaxy morphologies: spiral, elliptical, and irregular.

Zachovej identifikátor:

```latex
\label{fig:galaxy-types}
```

Dodrž pořadí **`\caption` a potom `\label`**. Díky tomu bude identifikátor navázán na správné číslo obrázku.

Všimni si, že číslo obrázku nevypisuješ ručně. LaTeX jej generuje automaticky.

### Úkol 7: Přidej druhý obrázek

V souboru `chapters/black-holes.tex` v podsekci *Event Horizons* za odstavec s citací `eventhorizon2019` vlož druhý přiložený obrázek `black-hole-diagram.png`:

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.75\textwidth]{figures/images/black-hole-diagram.png}
    \caption{Simplified schematic of a black hole and its event horizon.}
    \label{fig:black-hole}
\end{figure}
```

Obrázek ulož do stejného adresáře `figures/images/`.

Ověř, že oba obrázky mají odlišné číslo, popisek a identifikátor.

### Úkol 8: Porovnej obrazové formáty

Při práci s pdfLaTeXem se nejčastěji používají tyto formáty:

| Formát | Typické použití | Charakteristika |
|---|---|---|
| PNG | Schémata, snímky obrazovky, grafika | Rastrový formát, bezeztrátová komprese. |
| JPG/JPEG | Fotografie | Rastrový formát, obvykle menší soubory díky ztrátové kompresi. |
| PDF | Grafy, diagramy, vektorové ilustrace | Může zachovat vektorovou grafiku a ostré linie při zvětšení. |

Pro společný výstup do PDF a DOCX zde používej PNG/JPEG. Vektorové PDF je vhodné pro LaTeX, ale pro Word je předem připrav jako PNG.

**Poznámka:** Přímé vložení SVG souboru není standardní funkcí samotného pdfLaTeXu. SVG lze předem převést například do PDF; další postupy vyžadují zvláštní nástroje nebo balíčky.

### Úkol 9: Zamysli se nad zdrojem obrázku

Při použití obrázku z externího zdroje musíš ověřit jeho původ, licenci a požadavky na uvedení autorství.

U vědeckých obrázků si vždy zaznamenej:

- autora nebo organizaci, která obrázek vytvořila,
- původní zdroj (například URL či publikaci),
- licenci nebo podmínky použití,
- informaci, zda jde o převzatý nebo upravený obrázek.

Obrázky zde používáme jako výukové ilustrace. Jejich původní autor ani licence nejsou v repozitáři doloženi; nelze tedy tvrdit, že jde o vlastní nově vytvořená schémata. Před veřejným šířením je nahraď vlastním schématem nebo obrázkem s doloženým původem. Stav podkladů je uveden v [seznamu zdrojů](../ZDROJE.md).

Pokud obrázek nahrazuješ převzatým materiálem, přidej jeho skutečný zdroj do Zotera už nyní; v `\caption` za věcný popis připoj požadovaný kredit a citaci. Astronomický článek EHT automaticky není zdrojem přiloženého schématu.

V DOCX zkontroluj oba obrázky a věcné popisky. Automatická čísla z PDF se nemusí převést; pokud chybí, použij ve Wordu **Reference → Vložit titulek**. Podrobný postup včetně odkazů následuje v Challenge 08.

## Nápověda

| Příkaz / prostředí | K čemu slouží |
|---|---|
| `\usepackage{graphicx}` | Načte podporu pro vkládání obrázků. |
| `\includegraphics{...}` | Vloží obrázek. |
| `width=0.8\textwidth` | Nastaví šířku na 80 % šířky textu. |
| `\begin{figure}[htbp]` | Vytvoří plovoucí objekt s preferencemi umístění. |
| `\centering` | Vystředí obsah obrázku. |
| `\caption{...}` | Vytvoří popisek a automatické číslování. |
| `\label{fig:...}` | Přidá identifikátor pro budoucí odkazy. |

### Časté chyby

**Obrázek nebyl nalezen:** Zkontroluj název souboru, velikost písmen a cestu relativní k `main.tex`.

**Obrázek se objevil jinde, než očekáváš:** Prostředí `figure` je plovoucí objekt. Zkus `[htbp]` a zkontroluj délku okolního textu.

**Obrázek přesahuje okraje:** Nastav šířku například na `0.8\textwidth` nebo `\textwidth`.

**Nefunguje `\includegraphics`:** Ověř, že máš v preambuli načtený balíček `graphicx`.

## Sestavení do PDF a Wordu

1. Ulož všechny soubory. Ve VS Code spusť **LaTeX Workshop: Build LaTeX project** a otevři PDF. Od Challenge 04 musí recept zahrnovat také Biber.
2. V terminálu ve složce `project/` spusť přímý export do Wordu:

```bash
pandoc main.tex --from=latex --number-sections -o build/main.docx --citeproc --bibliography=references.bib --csl=styles/apa.csl
```

3. Otevři `build/main.docx` v MS Wordu a porovnej jej s PDF. Zkontroluj všechny změny z tohoto úkolu podle [kontroly exportu](../BUILD.md). Složku `build/` vytvoř před prvním exportem. Cesta k PDF závisí na nastavení LaTeX Workshop.

## Kontrola výsledku

- [ ] Sestavil jsem PDF i DOCX a oba výstupy osobně otevřel a zkontroloval.

- [ ] V `main.tex` je načtený balíček `graphicx`.
- [ ] V projektu existují oba přiložené obrazové soubory.
- [ ] V kapitole *Stars and Galaxies* se zobrazuje obrázek typů galaxií.
- [ ] V kapitole *Black Holes* se zobrazuje schéma černé díry.
- [ ] Oba obrázky jsou vystředěné a nepřesahují okraje textu.
- [ ] Každý obrázek má popisek vytvořený pomocí `\caption`.
- [ ] Každý obrázek má vlastní `\label`.
- [ ] Rozumíš rozdílu mezi volbami `h`, `t`, `b` a `p`.
- [ ] Dokument se úspěšně kompiluje přes LaTeX Workshop.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)

### Bonusový úkol: Přesné umístění obrázku

V předchozích úkolech jsme používali prostředí `figure` s parametrem `[htbp]`. LaTeX díky tomu automaticky rozhoduje, kam obrázek umístí, aby bylo rozložení dokumentu co nejlepší.

Někdy ale potřebujeme, aby se obrázek zobrazil **přesně na místě, kde jej vložíme do zdrojového kódu**, například bezprostředně za odstavcem, který jej vysvětluje.

K tomu slouží balíček `float` a parametr `[H]`.

**Úkol 1: Přidej balíček `float`**

Do preambule souboru `main.tex` přidej:

```latex
\usepackage{float}
```

**Úkol 2: Změň umístění obrázku**

Vyber jeden z obrázků a změň jeho parametr umístění z `[htbp]` na `[H]`:

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/images/galaxy-types.png}
    \caption{Classification of galaxies}
    \label{fig:galaxy-types}
\end{figure}
```

**Úkol 3: Porovnej výsledky**

Zkompiluj dokument pomocí LaTeX Workshop a porovnej chování obrázku při použití `[htbp]` a `[H]`.

| Parametr | Význam |
|---|---|
| `h` | Here – pokud možno na aktuálním místě. |
| `t` | Top – v horní části stránky. |
| `b` | Bottom – ve spodní části stránky. |
| `p` | Page – na samostatné stránce pro plovoucí objekty. |
| `!` | Uvolní některá omezení pro umístění obrázku. |
| `H` | Here exactly – zabrání běžnému automatickému přesouvání obrázku. |

**Pozor:** Ani `[H]` nedokáže umístit obrázek na stránku, pokud na ní není dostatek prostoru. V takovém případě se obrázek přesune na následující stránku.

**Doporučení:** Ve vědeckých článcích je vhodnější používat `[htbp]`, protože LaTeX dokáže lépe optimalizovat rozložení dokumentu. Parametr `[H]` používej pouze tehdy, když máš konkrétní důvod zachovat obrázek na daném místě.
