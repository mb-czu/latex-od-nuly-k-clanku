# Krok 4: VS Code s profilem pro LaTeX

> [!NOTE]
> [Zpět na instalační manuál](README.MD)


🎯 Cíl etapy: Mít ve VS Code samostatný profil LaTeX s rozšířením LaTeX Workshop, ve kterém se dokument po uložení sám zkompiluje do PDF, a otevřeš si náhled PDF.

Nejprve si nainstaluj [Visual Studio Code](https://code.visualstudio.com/download).

## 4a) Vytvoř profil

1. Ve VS Code klikni vlevo dole na ozubené kolečko → Profiles → New Profile…
2. Pojmenuj ho LaTeX a můžeš mu dát ikonu.
3. U „Copy from“ nech None, tedy čistý profil bez tvých ostatních rozšíření.
4. Klikni na Create.

## 4b) Nainstaluj rozšíření (už v profilu LaTeX)
V panelu Extensions (macOS: Cmd+Shift+X; Windows: Ctrl+Shift+X) vyhledej a nainstaluj:

- LaTeX Workshop (autor James Yu)
- LTeX+

## 4c) Nastavení profilu
Otevři paletu příkazů (macOS: Cmd+Shift+P; Windows: Ctrl+Shift+P) → Preferences: Open User Settings (JSON). Když jsi v profilu LaTeX, upravuješ jen jeho
nastavení. Je-li soubor prázdný, vlož celý blok níže. Jinak do existujícího objektu doplň pouze uvedené vlastnosti, oddělené čárkami; nevkládej druhý kořenový objekt:

```
{
  "latex-workshop.latex.autoBuild.run": "onSave",
  "latex-workshop.latex.outDir": "%DIR%/build",
  "latex-workshop.view.pdf.viewer": "tab",
  "editor.wordWrap": "on"
}
```

### 💡 Jak spustit kompilaci

PDF se vyrobí jedním z těchto způsobů:
- tlačítkem ▶️ **Build LaTeX project** vpravo nahoře nad otevřeným `.tex` souborem,
- přes ikonu **TeX** v levém panelu → **Build LaTeX project**.