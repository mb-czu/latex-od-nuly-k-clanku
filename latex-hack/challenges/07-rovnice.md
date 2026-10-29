# Challenge 07: Matematické rovnice

## Scénář

V předchozích Challenges jsi do vědeckého článku *Exploring the Universe: From Stars to Black Holes* přidal citace, obrázky a tabulky. Odborné články však často obsahují také matematické vztahy, které je potřeba zapisovat přehledně a konzistentně.

V tomto Challenge se naučíš zapisovat matematické výrazy přímo do textu i na samostatné řádky, vytvářet číslované rovnice a zarovnávat několik navazujících výpočtů. Vše si vyzkoušíš na jednoduchých astronomických příkladech.

## Cíle

Po dokončení tohoto Challenge budeš umět:

- Rozlišit matematický režim v textu a samostatně vysazené rovnice.
- Používat `$...$`, `\[...\]`, `equation` a `align`.
- Zapisovat zlomky, mocniny, dolní indexy a řecká písmena.
- Pracovat s balíčkem `amsmath`.
- Číslovat rovnice a přiřazovat jim identifikátory pomocí `\label`.
- Zarovnat více řádků výpočtu pomocí `&` a `\\`.
- Správně zapisovat matematické symboly a rozlišovat veličiny od textu.

## Zadání

### Úkol 1: Připrav balíček pro matematiku

Otevři soubor `main.tex` a do preambule, bezprostředně za `\usepackage{siunitx}` a před `\title`, přidej:

```latex
\usepackage{amsmath}
```

Balíček `amsmath` rozšiřuje možnosti LaTeXu pro sazbu matematiky. Budeme jej potřebovat zejména pro prostředí `align` a příkaz `\text{}`.

**Ověření:** Zkompiluj dokument pomocí rozšíření LaTeX Workshop ve VS Code. Dokument musí nadále fungovat bez chyb.

### Úkol 2: Vlož matematický výraz přímo do textu

Otevři `chapters/black-holes.tex`. V podsekci *Event Horizons*, za `\end{figure}` obrázku `fig:black-hole`, přidej jako nový odstavec větu o Schwarzschildově poloměru:

> The Schwarzschild radius is denoted by r with the subscript s and depends on the mass M of the object.

Zapiš veličiny matematicky pomocí `$...$`:

```latex
The Schwarzschild radius is denoted by $r_s$ and
 depends on the mass $M$ of the object.
```

Zápis `$...$` označuje **matematický režim uvnitř odstavce** (*inline math*). LaTeX matematické symboly automaticky přizpůsobí okolnímu textu.

### Úkol 3: Vytvoř samostatnou nečíslovanou rovnici

Za předchozí odstavec vlož vztah pro Schwarzschildův poloměr:

```latex
\[
r_s = \frac{2GM}{c^2}
\]
```

Kde:

- `r_s` představuje Schwarzschildův poloměr.
- `G` je gravitační konstanta.
- `M` je hmotnost objektu.
- `c` je rychlost světla ve vakuu.

**Všimni si:** `\frac{čitatel}{jmenovatel}` vytváří zlomek, `_` označuje dolní index a `^` horní index (mocninu).

Samostatné nečíslované rovnice se zapisují pomocí `\[...\]`. Na rozdíl od `$...$` se zobrazují na vlastním řádku.

### Úkol 4: Porovnej způsoby zápisu matematiky

Stejný matematický vztah lze vysázet několika způsoby:

| Zápis | Výsledek a použití |
|---|---|
| `$E = mc^2$` | Matematika uvnitř běžného odstavce, bez čísla rovnice. |
| `\[E = mc^2\]` | Samostatná nečíslovaná rovnice. |
| `\begin{equation} ... \end{equation}` | Samostatná automaticky číslovaná rovnice. |
| `\begin{align} ... \end{align}` | Více řádků, které lze zarovnat; standardně čísluje jednotlivé řádky. |

**Experiment:** Za právě vloženou rovnici v `chapters/black-holes.tex` dočasně vyzkoušej čtyři varianty. Porovnej PDF a poté všechny experimentální varianty odstraň; vztah pro Schwarzschildův poloměr z úkolu 3 zůstane jednou.

### Úkol 5: Vytvoř číslovanou rovnici pomocí `equation`

V souboru `chapters/stars-and-galaxies.tex`, v podsekci *The Life Cycle of Stars*, za odstavec s hodnotami hmotnosti a teploty Slunce a před odstavec s `\textcite{carroll2007}`, doplň jednoduchý vztah mezi energií a hmotností:

```latex
The mass--energy equivalence is expressed as:

\begin{equation}
    E = mc^2
    \label{eq:mass-energy}
\end{equation}
```

Prostředí `equation` vytvoří samostatnou **číslovanou rovnici**. Číslo přidává LaTeX automaticky.

Příkaz `\label{eq:mass-energy}` přiřazuje rovnici identifikátor, který později využiješ pro odkazy. Prefix `eq:` je doporučená konvence pro rovnice.

**Ověření:** Rovnice musí mít ve výsledném PDF automaticky přiřazené číslo.

### Úkol 6: Zapiš řecká písmena a další matematické symboly

V souboru `chapters/observations.tex` za odstavec se speciálními znaky končící *suitable measurements* vytvoř nový odstavec o vlnové délce a frekvenci elektromagnetického záření:

```latex
The wavelength $\lambda$ and frequency $\nu$ of
 electromagnetic radiation satisfy the relation

\[
    c = \lambda \nu
\]
```

Vyzkoušej si také následující příkazy:

| Příkaz | Význam |
|---|---|
| `\alpha`, `\beta`, `\gamma` | Malá řecká písmena. |
| `\Delta`, `\Omega` | Velká řecká písmena. |
| `\lambda`, `\nu` | Vlnová délka a frekvence. |
| `\times`, `\cdot` | Násobení. |
| `\leq`, `\geq` | Menší nebo rovno; větší nebo rovno. |
| `\approx`, `\neq` | Přibližně rovno; nerovná se. |
| `\infty` | Nekonečno. |
| `\sqrt{x}` | Druhá odmocnina. |
| `x_{max}` | Dolní index složený z více znaků. |
| `x^{n+1}` | Horní index složený z více znaků. |

**Pozor:** Příkazy pro matematické symboly zapisuj uvnitř matematického režimu, například `$\lambda$`, nikoliv přímo do běžného textu.

### Úkol 7: Zarovnej více rovnic pomocí `align`

V `chapters/observations.tex`, za nečíslovanou rovnici `c = \lambda \nu` z úkolu 6, vlož krátký výpočet frekvence z vlnové délky:

```latex
The frequency can be obtained from the wavelength:

\begin{align}
    c &= \lambda \nu \\
    \nu &= \frac{c}{\lambda}
    \label{eq:frequency}
\end{align}
```

V prostředí `align` mají dva znaky zvláštní význam:

- `&` označuje **místo zarovnání**. V tomto příkladu se oba řádky zarovnají podle znaménka rovnosti.
- `\\` ukončuje řádek a začíná další.

**Důležité:** `align` standardně čísluje **každý řádek zvlášť**. Pokud některý řádek číslovat nechceš, přidej na jeho konec `\notag` (nebo `\nonumber`):

```latex
\begin{align}
    c &= \lambda \nu \notag \\
    \nu &= \frac{c}{\lambda}
    \label{eq:frequency}
\end{align}
```

Porovnej PDF a Word. Pro výsledný článek pak v `chapters/observations.tex` tento celý blok `align` **nahraď** následující variantou, která se přímo převádí na zarovnanou Wordovou rovnici:

```latex
\begin{equation}
    \begin{aligned}
        c &= \lambda \nu \\
        \nu &= \frac{c}{\lambda}
    \end{aligned}
    \label{eq:frequency}
\end{equation}
```

`aligned` zarovná oba řádky uvnitř jediné číslované rovnice. V PDF má číslo celý blok. Pandoc převede matematiku, ale číslo rovnice automaticky nepřenese; jeho doplnění a odkazy ve Wordu řeší Challenge 08. Nikdy neponechávej obě varianty zároveň.

Pokud chceš mít celý blok bez číslování, můžeš použít prostředí `align*`.

### Úkol 8: Zapiš text uvnitř matematického výrazu

V matematickém režimu se běžná písmena chápou jako matematické proměnné. Pokud potřebuješ do rovnice vložit slovní označení, použij příkaz `\text{}` z balíčku `amsmath`.

V `chapters/black-holes.tex` za nečíslovanou rovnici pro `r_s` dočasně vyzkoušej:

```latex
\[
    v_{\text{escape}} = \sqrt{\frac{2GM}{r}}
\]
```

Porovnej vzhled dolního indexu s variantou `v_{escape}`. V prvním případě je slovo *escape* vysázené jako text, ve druhém jako posloupnost matematických symbolů.

Po porovnání tento experiment s únikovou rychlostí odstraň.

**Poznámka:** Ve fyzikálních vztazích je vhodné používat ustálené značky veličin a jejich význam vysvětlit v okolním textu.

### Úkol 9: Připrav rovnice pro budoucí odkazy

Zkontroluj, že číslované rovnice obsahují jednoznačné identifikátory:

```latex
\label{eq:mass-energy}
\label{eq:frequency}
```

V Challenge 08 se naučíš na tyto rovnice odkazovat pomocí `\ref`, `\eqref` a dalších příkazů. Identifikátory proto zachovej.

**Ověření:** Dokument se kompiluje bez chyb a čísla rovnic se generují automaticky. Každý identifikátor `\label` musí být v celém dokumentu jedinečný.

## Nápověda

| Příkaz nebo prostředí | K čemu slouží |
|---|---|
| `$...$` | Matematický výraz přímo v textu. |
| `\[...\]` | Samostatný nečíslovaný matematický výraz. |
| `equation` | Samostatná číslovaná rovnice. |
| `equation*` | Samostatná nečíslovaná rovnice. |
| `align` | Zarovnání více matematických řádků s možností číslování. |
| `align*` | Zarovnání více řádků bez číslování. |
| `\frac{a}{b}` | Zlomek. |
| `x^2`, `x^{n+1}` | Mocnina. |
| `r_s`, `r_{max}` | Dolní index. |
| `\sqrt{x}` | Odmocnina. |
| `\text{...}` | Běžný text uvnitř matematického režimu. |
| `\notag` | Potlačí číslo jednoho řádku v `align`. |
| `\label{eq:...}` | Identifikátor rovnice pro křížové odkazy. |

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

- [ ] Do preambule jsi přidal balíček `amsmath`.
- [ ] Umíš zapsat matematický výraz pomocí `$...$`.
- [ ] Rozumíš rozdílu mezi `$...$`, `\[...\]`, `equation` a `align`.
- [ ] V článku máš samostatnou nečíslovanou rovnici pro Schwarzschildův poloměr.
- [ ] V článku máš číslovanou rovnici `E = mc^2`.
- [ ] Umíš zapisovat zlomky, horní a dolní indexy a řecká písmena.
- [ ] Vyzkoušel jsem `align`; pro výsledný článek používám `equation` s `aligned` a oba řádky jsou ve Wordu zachovány.
- [ ] Víš, k čemu slouží `&`, `\\` a `\notag`.
- [ ] Číslované rovnice mají jedinečné identifikátory `\label`.
- [ ] Dokument se bez chyb kompiluje ve VS Code pomocí LaTeX Workshop.

## Referenční řešení

Konečný článek je v [`solution/`](../solution/). Obsahuje i pozdější úpravy, proto jej nepoužívej jako výchozí stav tohoto úkolu. Návrh samostatných řešení po každém kroku najdeš v [dílčích řešeních](/latex-hack/checkpoints/README.MD).

[Zpět na přehled Hacku](../README.MD)
