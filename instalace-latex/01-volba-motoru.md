# Krok 1: Volba motoru

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

V LaTeXu se běžně používají tři motory pro vytvoření PDF. Liší se hlavně prací s písmy a typografickými možnostmi. Pro tento kurz používáme pdfLaTeX; LuaLaTeX je alternativou například pro systémová písma. U časopisu nebo archivu se řiď požadavky konkrétní šablony.

> [!IMPORTANT]
> V našem projektu budeme využívat především pdfLaTeX. Případná změna na LuaLaTeX je popsána v tomto [souboru](/dalsi-tipy/přechod-z-pdfLaTeX-naLuaLaTeX.md)

| Kritérium                                                    | **pdfLaTeX**             | **XeLaTeX**         | **LuaLaTeX**                    |
| ------------------------------------------------------------ | ------------------------ | ------------------- | ------------------------------- |
| Rychlost                                                     | obvykle rychlý       | závisí na dokumentu | první běh může být pomalejší |
| Systémová písma (Times, Calibri, .otf/.ttf)                  | ne, jen písma LaTeXu  | ano (`fontspec`) | ano (`fontspec`)             |
| Čeština                                                      |  ano (`fontenc` T1)    |  ano, nativně     | ano, nativně                 |
| Šablony časopisů (Elsevier, IEEE, Springer…) a arXiv fungují |  počítají s ním        | obvykle fungují  |  obvykle                      |
| Zaměření                                                     | tradiční sazba a běžné šablony | systémová písma | systémová písma a rozšíření pomocí Lua |

### Výhody a nevýhody

**pdfLaTeX**

- ✅ Rychlý pro běžné dokumenty, široce podporovaný šablonami; některé balíčky vyžadují jiný motor.
- ✅ Nejvíc návodů a odpovědí na internetu.
- ❌ Nemůže použít písma nainstalovaná v počítači, jen písma dodávaná s LaTeXem.
- ❌ Nepodporuje balíček `fontspec`.

**XeLaTeX**

- ✅ Umí systémová písma a exotická písma (arabština, čínština…).
- ❌ Některé typografické funkce (`microtype`) umí jen částečně.

**LuaLaTeX**

- ✅ Moderní nástupce pdfLaTeXu: systémová písma plus plná typografie.
- ❌ První spuštění může trvat déle kvůli vytváření mezipaměti písem.
- ❌ Občas nefunguje se starším balíčkem.
