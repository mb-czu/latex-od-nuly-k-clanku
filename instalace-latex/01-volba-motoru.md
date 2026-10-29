# Krok 1: Volba motoru

> [!NOTE]
> [Zpět na instalační manuál](README.MD)

LaTeX má tři motory, které ze souboru `.tex` vyrábějí PDF. Liší se hlavně rychlostí a tím, jaká písma umí použít. Nejrozšířenější je pdfLaTeX (výchozí v Overleafu, arXivu i šablonách časopisů), LuaLaTeX je jeho doporučený nástupce.

> [!IMPORTANT]
> V našem projektu budeme využívat především pdfLaTeX. Případná změna na LuaLaTeX je popsána v tomto [souboru](/dalsi-tipy/přechod-z-pdfLaTeX-naLuaLaTeX.md)

| Kritérium                                                    | **pdfLaTeX**             | **XeLaTeX**         | **LuaLaTeX**                    |
| ------------------------------------------------------------ | ------------------------ | ------------------- | ------------------------------- |
| Rychlost                                                     | nejrychlejší          | střední             | nejpomalejší (hlavně první běh) |
| Systémová písma (Times, Calibri, .otf/.ttf)                  | ne, jen písma LaTeXu  | ano (`fontspec`) | ano (`fontspec`)             |
| Čeština                                                      |  ano (`fontenc` T1)    |  ano, nativně     | ano, nativně                 |
| Šablony časopisů (Elsevier, IEEE, Springer…) a arXiv fungují |  počítají s ním        | obvykle fungují  |  obvykle                      |
| Budoucnost                                                   | stabilní, už se nevyvíjí | vývoj stagnuje      | doporučený nástupce             |

### Výhody a nevýhody

**pdfLaTeX**

- ✅ Nejrychlejší a nejspolehlivější, funguje s ním každý balíček i šablona časopisu.
- ✅ Nejvíc návodů a odpovědí na internetu.
- ❌ Nemůže použít písma nainstalovaná v počítači, jen písma dodávaná s LaTeXem.
- ❌ Nepodporuje balíček `fontspec`.

**XeLaTeX**

- ✅ Umí systémová písma a exotická písma (arabština, čínština…).
- ❌ Pomalejší, vývoj stagnuje, některé typografické funkce (`microtype`) umí jen částečně.

**LuaLaTeX**

- ✅ Moderní nástupce pdfLaTeXu: systémová písma plus plná typografie.
- ❌ Nejpomalejší, první spuštění trvá dlouho (vytváří se mezipaměť písem).
- ❌ Občas nefunguje se starším balíčkem.
