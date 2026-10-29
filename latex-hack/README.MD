# LaTeX Hack: Tvorba vědeckého článku

V deseti navazujících úkolech vytvoříš anglický výukový článek **Exploring the Universe: From Stars to Black Holes**. Pracuješ stále na jednom projektu. Po každém úkolu sestavíš **PDF i MS Word (.docx)**, oba otevřeš a sám zkontroluješ změny.

## Přehled Challenges

| Challenge | Zadání | Nové dovednosti | Řešení |
|---|---|---|---|
| 01 | [Struktura projektu](challenges/01-struktura-projektu.md) | Adresáře, minimální funkční dokument, `csquotes`, první PDF a Word. | [Řešení challange 01](./checkpoints/01/) |
| 02 | [První kostra článku](challenges/02-prvni-kostra-clanku.md) | Titul, autor, datum, první sekce a odstavec. |[Řešení challange 02](/latex-hack/checkpoints/02/) |
| 03 | [Struktura a formátování](challenges/03-formatovani-textu.md) | `\input`, abstrakt, sekce, seznamy a speciální znaky. | [Řešení challange 03](./checkpoints/03/) |
| 04 | [Citace a bibliografie](challenges/04-citace.md) | Původní publikace → Zotero → Better BibLaTeX → Biber a citeproc. | [Řešení challange 04](./checkpoints/04/) |
| 05 | [Obrázky a ilustrace](challenges/05-obrazky-a-ilustrace.md) | PNG, rozměry, popisky a identifikátory. | [Řešení challange 05](./checkpoints/05/) |
| 06 | [Tabulky a číselné údaje](challenges/06-tabulky-a-ciselne-udaje.md) | `booktabs`, `siunitx`, dvě samostatné tabulky. | [Řešení challange 06](./checkpoints/06/) |
| 07 | [Matematické rovnice](challenges/07-rovnice.md) | Matematické režimy, `equation`, `align`, identifikátory. | [Řešení challange 07](./checkpoints/07/) |
| 08 | [Křížové odkazy](challenges/08-krizove-odkazy.md) | `\ref`, `\eqref`, `\cref`, číslování a klikatelnost. | [Řešení challange 08](./checkpoints/08/) |
| 09 | [Pokročilé funkce](challenges/09-pokrocile-funkce.md) | Poznámky pod čarou, uvozovky, makra, TODO experiment a jeden obsah. | [Řešení challange 09](./checkpoints/09/) |
| 10 | [Finální článek](challenges/10-finalni-clanek.md) | Kontrola obou formátů a přenosný projekt. | Řešení challange 10 |

## Příprava a práce

Nejprve dokonči [instalaci a úvodní návody](/instalace-latex/README.MD). Potřebuješ VS Code s LaTeX Workshop, pdfLaTeX, latexmk, Biber, **Pandoc**, Zotero a Better BibTeX. Pro osobní kontrolu DOCX používej MS Word. Článek používá třídu `article`, 11 pt, A4 a angličtinu. Od Challenge 04 je společným citačním stylem **APA**; IEEE zkoušíme dočasně v obou výstupech a pak APA vrátíme.

1. Otevři `latex-hack/project/` ve VS Code a postupuj od úkolu 01.
2. U každého vložení respektuj soubor, sekci, odstavec a kotevní text uvedený v zadání. Při přesunu nebo nahrazení odstraň původní verzi.
3. Po úkolu sestav PDF přes **LaTeX Workshop** a Word exportuj přímým příkazem **Pandocu** uvedeným v zadání.
4. Otevři PDF a `build/main.docx`, ověř novinky i dosavadní obsah a teprve potom pokračuj.

## Uspořádání repozitáře

```text
latex-hack/
├── README.MD
├── BUILD.md
├── ZDROJE.md
├── DILCI-RESENI.md
├── challenges/           # 10 zadání
├── project/              # tvoje práce; soubory vytvoříš v Challenge 01
├── solution/             # kompletní finální reference
└── styles/
    ├── apa.csl           # výchozí citační styl pro Word
    └── ieee.csl          # porovnání stylů v Challenge 04
```

Pracovní projekt obsahuje `main.tex`, `references.bib`, pět souborů v `chapters/`, obrázky ve `figures/images/` a tabulky v `tables/`. `build/` vytvoříš před prvním exportem do Wordu. Nezačínej kopírováním celého finálního řešení, protože obsahuje i pozdější úkoly.

[Původní zdroje pro Zotero](ZDROJE.md) obsahují ISBN/DOI a přesné klíče pro automatický export.

Článek je výuková ukázka. Tabulkové hodnoty nejsou přesným datovým souborem. Původ a licence přiložených ilustrací zatím nejsou doloženy; podrobnosti a postup před zveřejněním jsou v seznamu zdrojů.
