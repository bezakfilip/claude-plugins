# redeem — čistá reštartovaná relácia pre Claude Code

`/redeem` nahradí aktuálnu reláciu v Claude Code (desktopová aplikácia Claude) novou, čistou reláciou:

1. napíše podrobný handoff (čo je hotové, čo je otvorené, rozhodnutia, cesty) do `~/.claude/handoffs/`,
2. spustí novú reláciu s rovnakým názvom, skupinou a pripnutím v bočnom paneli,
3. nová relácia si handoff prečíta a po tvojej prvej správe starú reláciu zmaže (aplikácia sa pýta na potvrdenie).

Výsledok: menší kontext → menej tokenov na správu a menej zmätku v dlhých reláciách.

**Funguje iba v Claude Code v desktopovej aplikácii Claude** (používa jej nástroje na správu relácií). V termináli `claude` ani na claude.ai nefunguje.

## Inštalácia

Najprv nahraj tento priečinok ako repozitár na GitHub (napr. `bezakfilip/claude-plugins`). Potom v Claude Code:

```
/plugin marketplace add bezakfilip/claude-plugins
/plugin install redeem@moje-pluginy
```

Alebo z terminálu:

```
claude plugin marketplace add bezakfilip/claude-plugins
claude plugin install redeem@moje-pluginy
```

Pre súkromný repozitár musí byť Git na danom PC prihlásený na GitHub.

## Použitie

V relácii, ktorú chceš „prečistiť“, napíš `/redeem` (ak by sa nenašiel, tak `/redeem:redeem`). Najlepšie pri prechode na novú tému, nie uprostred rozrobenej práce.

## Štruktúra

```
.claude-plugin/marketplace.json        ← katalóg (marketplace) „moje-pluginy“
plugins/redeem/.claude-plugin/plugin.json
plugins/redeem/skills/redeem/SKILL.md  ← samotný postup
```

Ďalšie pluginy pridáš ako nový priečinok v `plugins/` a záznam v `marketplace.json`.
