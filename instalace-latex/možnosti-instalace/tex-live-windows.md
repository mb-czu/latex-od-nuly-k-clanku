# Krok 1: Instalace LaTeXu (Windows – TeX Live)

> [!NOTE]
> [Zpět na přehled](../02-instalace.md)
> 
🎯 Cíl etapy: Mít na Windows funkční LaTeX včetně angličtiny, češtiny, citací (biblatex, biber) a nástroje latexmk, aby bylo možné vytvářet PDF dokumenty přímo z VS Code.

## 1a) Instalace

1. Na Windows budeme používat distribuci TeX Live, která obsahuje stejné nástroje jako BasicTeX na macOS.

2. Otevři oficiální stránky [TeX Live](https://tug.org/texlive/acquire-netinstall.html) a stáhni instalační program install-tl-windows.exe.

3. Spusť instalátor.

4. V pokročilém nastavení vyber instalační schéma scheme-basic (základní  schéma), pokud chceš instalovat pouze základní komponenty a další balíčky doplnit ručně. Nebo plnou instalaci a pak lze instalaci balíčků (viz. 1e - 1f) přeskočit

5. Dokonči instalaci.

**Poznámka:** Výchozí instalace TeX Live může zabírat několik GB. Základní schéma je výrazně menší, ale vyžaduje následnou instalaci potřebných balíčků.

## 1b) Načtení cest

Po instalaci zavři PowerShell nebo terminál ve VS Code a znovu jej otevři.

Instalátor TeX Live na Windows standardně přidává potřebné cesty do systémové proměnné PATH.

Pokud příkazy LaTeXu nejsou dostupné, ověř nastavení pomocí:

`where.exe pdflatex`
`where.exe tlmgr`

Očekávaný výstup bude podobný:

`C:\texlive\2026\bin\windows\pdflatex.exe`
`C:\texlive\2026\bin\windows\tlmgr.bat`

Konkrétní cesta se může lišit podle roku a umístění instalace.

## 1c) Ověření instalace

Otevři PowerShell a spusť:

`pdflatex --version`
`tlmgr --version`

Oba příkazy by měly vypsat informace o nainstalovaných nástrojích.

## 1d) Aktualizace správce balíčků

Spusť:

`tlmgr update --self`

Na Windows se nepoužívá příkaz sudo. Pokud je TeX Live nainstalován pro všechny uživatele, může být potřeba spustit PowerShell jako správce.

## 1e) Instalace balíčků – varianta 1

Tato varianta instaluje pouze konkrétní balíčky potřebné pro základní práci s LaTeXem.

Použijeme stejné balíčky jako na macOS.

`tlmgr install latexmk biber biblatex csquotes babel hyphen-english lm graphics hyperref microtype cleveref booktabs geometry biblatex-ieee biblatex-iso690 biblatex-apa siunitx amsmath todonotes float`

Příkaz zahrnuje i balíčky pro navazující LaTeX Hack. Další balíčky doplň podle vlastního dokumentu.

## 1f) Instalace kolekcí balíčků – varianta 2 (doporučeno)

Pro výuku doporučujeme instalaci kolekcí, které obsahují větší množství běžně používaných balíčků.

|Kolekce / balíček|Co přinese|
|-----------------|----------|
|collection-latexrecommended|Běžné balíčky pro sazbu dokumentů|
|collection-latexextra|Rozšířené možnosti sazby, tabulek, obrázků a dalších prvků|
|collection-bibtexextra|Citační styly včetně IEEE, APA a ISO 690|
|collection-fontsrecommended|Doporučená písma včetně Latin Modern a TeX Gyre|
|collection-langczechslovak|Podpora češtiny a slovenštiny|
|latexmk|Automatizace kompilace dokumentů|
|biber|Zpracování bibliografie|
|latexindent|Automatické formátování LaTeXového kódu|
|chktex|Kontrola typických chyb v LaTeXovém zdrojovém kódu|

Všechny kolekce a nástroje nainstalujeme jedním příkazem:

`tlmgr install collection-latexrecommended collection-latexextra collection-bibtexextra collection-fontsrecommended collection-langczechslovak latexmk biber latexindent chktex`

Instalace může chvíli trvat, zejména kvůli větším kolekcím.

## 1g) Ověření kompletní instalace

Po dokončení instalace spusť:

`pdflatex --version`
`latexmk -v`
`biber --version`
`chktex --version`

Pokud všechny příkazy fungují, základní prostředí je připravené.

> [!IMPORTANT]
> Důležité: Nástroj latexmk vyžaduje na Windows funkční Perl. TeX Live pro Windows standardně poskytuje potřebné prostředí pro jeho spuštění. Při nestandardní instalaci může být potřeba Perl doinstalovat.