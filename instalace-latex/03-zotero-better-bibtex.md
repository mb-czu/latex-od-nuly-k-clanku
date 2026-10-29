# Krok 3: Zotero a Better BibTeX

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

🎯 Cíl etapy: Zotero bude automaticky udržovat soubor references.bib ve složce projektu. Každý zdroj, který přidáš do Zotera, se v něm objeví sám a v LaTeXu ho hned můžeš citovat.

## 2a) Ověř, že Better BibTeX funguje

Nainstalovat plugin [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/)

## 2b) Kolekce pro projekt

V Zoteru si vytvoř novou kolekci pro článek (pravý klik na Moje knihovna → Nová kolekce). Přidej do ní pár zdrojů na zkoušku.

## 2c) Automatický export

1. Pravým tlačítkem klikni na kolekci → Exportovat kolekci…
2. Jako formát zvol Better BibLaTeX. Pozor, ne „Better BibTeX“, protože používáme biblatex.
3. Zaškrtni Keep updated (Udržovat aktualizované).
4. Ulož do složky projektu jako references.bib.

## 2d) Ověření

1. Otevři references.bib v textovém editoru. Měly by tam být záznamy začínající @article{... nebo @book{....
2. Přidej do kolekce v Zoteru další zdroj a za pár sekund se objeví i v souboru ✅
