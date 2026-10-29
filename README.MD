# LaTeX krok za krokem

🚀 Praktický návod v češtině, ve kterém projdeš cestu od instalace LaTeXu přes první dokument až k vícesouborovému odbornému článku. Naučíš se pracovat s textem, citacemi ze Zotera, obrázky, tabulkami, rovnicemi a odkazy a připravíš výstupy do **PDF i MS Wordu (.docx)**.

Návody jsou určené především začátečníkům na macOS a Windows. Zadání jsou česky; ukázkové články píšeme anglicky.

## Kde začít a instalace LaTeX

Pokud s LaTeXem začínáš, postupuj podle [následujícího pořadí](./instalace-latex/README.MD). Máš-li už funkční prostředí a zvládáš jednoduchý dokument s citacemi, přejdi rovnou na LaTex Hack. //TODO Sem přidat odkaz

## Co budeš využívat

- **LaTeXovou distribuci** s pdfLaTeXem, latexmk a Biberem.
- **Visual Studio Code** s rozšířením **LaTeX Workshop** pro práci se zdroji a PDF.
- **Zotero** s doplňkem **Better BibTeX**; pro náš postup vybírej exportní formát **Better BibLaTeX** a volbu **Keep updated**.
- **Pandoc** pro přímý export do Wordu a **MS Word** pro osobní kontrolu a dokončení DOCX.

Instalaci a nastavení projdi podle odkazů výše. U bibliografie opravuj metadata v Zoteru; automaticky exportovaný `references.bib` se při další aktualizaci přepíše.

## LaTeX Hack

V deseti praktických úkolech vytvoříš výukový článek **Exploring the Universe: From Stars to Black Holes**. Každá Challenge obsahuje scénář, cíle, konkrétní zadání, nápovědu a kontrolní seznam.

Postupně si vyzkoušíš strukturu projektu, formátování textu, citace, obrázky, tabulky, matematiku, křížové odkazy a závěrečnou přípravu článku. Všechny úkoly rozšiřují **jeden pracovní projekt** ve složce /TODO Doplnit odkaz na složku.

Začni //TODO Doplnit odkaz. Do kompletního referenčního řešení /TODO Doplnit odkaz nahlížej pro porovnání; obsahuje i úpravy z pozdějších úkolů.

## Jak vytvářet a kontrolovat výstupy

Po každé Challenge ulož změny, vytvoř oba formáty a oba osobně otevři:

1. **PDF:** Ve VS Code spusť **LaTeX Workshop: Build LaTeX project**. Při práci s bibliografií musí kompilační recept zahrnovat také Biber. PDF otevři přes **LaTeX Workshop: View LaTeX PDF**.
2. **Word:** V terminálu otevřeném v kořenové složce pracovního článku spusť přímý příkaz **Pandocu** uvedený v zadání. Potom otevři výsledný DOCX v MS Wordu.
3. **Kontrola:** Porovnej úplnost textu, citace, obrázky, tabulky, rovnice a odkazy. Teprve po kontrole pokračuj dalším úkolem.

> [!IMPORTANT]
> PDF a Word používají odlišné způsoby sazby. Přímý export Pandocem nezaručuje shodné stránkování ani úplný převod číslování rovnic, popisků a křížových odkazů. Tyto prvky ve Wordu podle zadání zkontroluj a případně ručně dokonči. Podrobnosti a příkazy pro jednotlivé etapy najdeš v návodu sestavení a exportu //TODO Doplnit odkaz.

Úvodní dokument používá citační styl IEEE, LaTeX Hack standardně APA. Při exportu vybírej odpovídající soubor CSL podle konkrétního zadání.

## Orientace v repozitáři

```text
.
├── README.MD            # úvod a doporučený postup
├── docs/                # instalace, nastavení a základní návody
├── first-document/      # první ukázkový dokument s bibliografií
└── latex-hack/
    ├── README.MD        # přehled všech Challenges
    ├── challenges/      # 10 navazujících zadání
    ├── project/         # tvoje pracovní složka
    ├── solution/        # finální referenční zdroje
    ├── styles/          # citační styly CSL pro Word
    ├── BUILD.md         # sestavení PDF, export a kontrola Wordu
    ├── ZDROJE.md        # publikace a identifikátory pro Zotero
    └── DILCI-RESENI.md   # návrh publikování průběžných řešení
```

Původní publikace pro cvičení, jejich ISBN/DOI a citační klíče najdeš v [seznamu zdrojů](latex-hack/ZDROJE.md). 

> [!WARNING]
> Veškeré materiály v rámci LaTeX Hacku slouží výhradně k výukovým účelům. Uvedené odborné texty, číselné údaje, tabulky a ilustrace mají především demonstrační charakter a nemusí odpovídat aktuálním vědeckým poznatkům či přesným naměřeným hodnotám. Materiály proto nepovažujte za ověřený vědecký zdroj a nepoužívejte je jako podklad pro odborné závěry bez dalšího ověření.