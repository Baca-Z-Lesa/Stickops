# Implementácia – Stickops

Zdrojový kód nie je v tejto zložke kopírovaný – je v koreni repozitára. Tu je jeho popis.

## Technológie

| oblasť | použité |
|---|---|
| jazyk a zostavenie | C++20, CMake (preset `windows-vs`), Visual Studio 2022 |
| grafika, okno, vstup | raylib (OpenGL 3.3), gamepad cez raylib |
| zvuk | SoLoud (dozvuk, prelínanie hudby) |
| dáta | nlohmann/json (JSON s komentármi, UTF-8 s BOM), vlastné schémy v `_schemas/` |
| animácie finisherov | tweeny |
| ladiace a trénerské UI | Dear ImGui + rlImGui |
| testy | doctest (`stick_tests.exe`, `stick_ai_tests.exe`) |
| tréning AI | C++ neuroevolúcia (`stick_trainer.exe`), voliteľne Python (PPO) v `ai/python` |

Knižnice sa sťahujú automaticky pri prvom zostavení (CMake FetchContent).

## Architektúra

```
game/src/core      herná logika – deterministická simulácia bez grafiky (sim, data, math, replay)
game/src/content   načítanie a kontrola JSON, slovenské chybové hlášky
game/src/render    kreslenie postáv, arén, efektov a HUD (knižnica stick_render)
game/src/app       okno, menu, kampaň, kozmetika, most k AI (AiOpponent)
game/src/input     klávesnica, myš, gamepad -> herné povely
game/src/audio     zvuk a hudba (SoLoud)
ai/src/ai          skriptovaný bot, neurónová sieť, pozorovanie sveta
ai/src/campaign    kampaň, odomykanie, uložený postup
ai/src/cli         stick_cli.exe – kontrola obsahu, turnaje, replaye
ai/src/trainer     stick_trainer.exe – tréning bossov s grafom a náhľadom
```

Hlavné zásady:

- **Logika oddelená od kreslenia** – `core` nevie nič o grafike, preto sa dá simulovať bez okna (tréning AI, testy).
- **Determinizmus** – rovnaký seed a vstupy dajú rovnaký zápas. Na tom stoja replaye (seed + vstupy) aj tréning.
- **AI nepodvádza** – AI aj hráč posielajú rovnaké povely (`MultiDiscrete[3,4,10]`: pohyb, vertikála, tlačidlo).
- **Obsah ako dáta** – postavy, útoky, pózy, finishery, arény, efekty, zvuky, kampaň a osobnosti AI sú v JSON.
  Novú arénu alebo osobnosť pridáš súborom, bez zmeny kódu. F5 načíta zmeny za behu.

## Výstupy zostavenia (`bin/`)

| súbor | popis |
|---|---|
| `Stickops.exe` | hra |
| `stick_trainer.exe` | tréning bossov s vizualizáciou |
| `stick_cli.exe` | nástroj bez grafiky: `validate`, `tournament`, `bot-match`, `replay-verify` |

## Priebeh vývoja (podľa gitu)

| obdobie | čo pribudlo |
|---|---|
| 30. 9. – 1. 10. 2026 | návrh architektúry, M1 (pohyb, údery, 2 hráči), M2 (blok, schopnosti z JSON, hot-reload) |
| 3. – 5. 10. | herný plán v2 (boj zblízka), kroky 1–11: pohyb, úhyb, J/K/L, kombá, blok na načasovanie, SILA, finishery, ladiaci panel, replaye, headless simulácia |
| 6. 10. | skriptovaný bot, turnaje, rozdelenie na `game/` a `ai/`, kampaň, tréner bossov, kozmetika, grafika postáv a arén, logo a názov Stickops |
| 7. 10. | klinč a skok nohami napred, zvuk SoLoud, nové menu, 5 natrénovaných bossov, kampaň 25 levelov |
| 14. – 16. 10. | dokumentácia (požiadavky, use cases, táto zložka) |
