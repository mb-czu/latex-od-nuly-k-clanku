# Krok 4: VS Code s profilem pro LaTeX

> [!NOTE]
> [Zpět na instalační manuál](README.MD)


🎯 Cíl etapy: Mít ve VS Code samostatný profil LaTeX s rozšířením LaTeX Workshop, ve kterém se dokument po uložení sám zkompiluje do PDF, a to se zobrazí vedle textu.

## 3a) Vytvoř profil

1. Ve VS Code klikni vlevo dole na ozubené kolečko → Profiles → New Profile…
2. Pojmenuj ho LaTeX a můžeš mu dát ikonu.
3. U „Copy from“ nech None, tedy čistý profil bez tvých ostatních rozšíření.
4. Klikni na Create.

## 3b) Nainstaluj rozšíření (už v profilu LaTeX)
V panelu Extensions (Cmd+Shift+X) vyhledej a nainstaluj:

- LaTeX Workshop (autor James Yu)
- LTeX+

## 3c) Nastavení profilu
Otevři Cmd+Shift+P → Preferences: Open User Settings (JSON). Když jsi v profilu LaTeX, upravuješ jen jeho
nastavení. Vlož (případně vlož za již existující text):

```
{
  "latex-workshop.latex.autoBuild.run": "never",
  "latex-workshop.latex.outDir": "%DIR%/build",
  "latex-workshop.view.pdf.viewer": "tab",
  "editor.wordWrap": "on"
}
```

### 💡 Jak spustit kompilaci

PDF se vyrobí jedním z těchto způsobů:
- tlačítkem ▶️ **Build LaTeX project** vpravo nahoře nad otevřeným `.tex` souborem,
- přes ikonu **TeX** v levém panelu → **Build LaTeX project**.