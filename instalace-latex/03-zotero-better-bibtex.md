# Krok 3: Zotero a Better BibTeX

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

🎯 Cíl etapy: Zotero bude automaticky udržovat soubor references.bib ve složce projektu. Každý zdroj, který přidáš do Zotera, se v něm objeví sám a v LaTeXu ho hned můžeš citovat.

## 3a) Ověř, že Better BibTeX funguje

Nainstaluj [Zotero](https://www.zotero.org/download/) a doplněk [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/). Používej verzi doplňku kompatibilní s verzí Zotera.

## 3b) Kolekce pro projekt

V Zoteru si vytvoř novou kolekci pro článek (pravý klik na Moje knihovna → Nová kolekce). Přidej do ní pár zdrojů na zkoušku.

## 3c) Automatický export

1. Pravým tlačítkem klikni na kolekci → Exportovat kolekci…
2. Jako formát zvol Better BibLaTeX. Pozor, ne „Better BibTeX“, protože používáme biblatex.
3. Zaškrtni Keep updated (Udržovat aktualizované).
4. Ulož do složky projektu jako references.bib.

## 3d) Ověření

1. Otevři references.bib v textovém editoru. Měly by tam být záznamy začínající @article{... nebo @book{....
2. Přidej do kolekce v Zoteru další zdroj a za pár sekund se objeví i v souboru ✅
