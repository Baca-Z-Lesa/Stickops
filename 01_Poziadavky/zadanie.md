# Zadanie projektu – Stickops

| | |
|---|---|
| **Názov** | Stickops (pôvodne STICK-OVERKILL) |
| **Typ** | ročníkový projekt – 2D bojová hra pre Windows |
| **Autor** | Patrik Nottny |
| **Technológie** | C++20, CMake, raylib (grafika), SoLoud (zvuk), nlohmann/json, Dear ImGui, doctest, Python (voliteľný tréning AI) |
| **Stav k 16. 10. 2026** | hrateľná verzia: boj, kampaň (25 levelov), 5 natrénovaných bossov, zvuk, menu, replaye |

## Cieľ

Vytvoriť 2D bojovku paličkových postáv (stickmanov) zameranú na **boj zblízka** – údery, kopy, kombá,
blok na načasovanie a úhyby. Nadprirodzené útoky nie sú samostatné kúzla, ale **posilnené verzie bežných
úderov** (SILA), ktoré si hráč musí vybojovať. Zápas končí filmovým **finisherom**.

Súperov ovláda **umelá inteligencia** – skriptované osobnosti a bossovia natrénovaní neuroevolúciou.
AI používa rovnaké povely ako hráč (nepodvádza).

## Rozsah

1. **Boj** – pohyb, skok, lezenie po plošinkách, ľahký/ťažký útok, kop, blok (Ctrl), úhyb (Shift), chmat,
   klinč, SILA, zásahové zóny, kolá, finishery.
2. **Režimy** – kampaň (25 levelov v 5 kapitolách, každý piaty level boss, presily a výzvy),
   rýchly zápas proti AI alebo druhému hráčovi, prehranie posledného replayu.
3. **AI** – 14 osobností súperov, 5 natrénovaných bossov, nástroje na tréning a turnaje (`stick_trainer.exe`, `stick_cli.exe`).
4. **Obsah ako dáta** – postavy, útoky, arény, finishery, kampaň a osobnosti AI sú v súboroch JSON;
   chyby v nich hra hlási po slovensky so súborom a riadkom. Zmeny sa dajú načítať za behu (F5).
5. **Zvuk a menu** – hudba a efekty, rozvetvené menu ovládané klávesnicou, myšou aj gamepadom.

## Mimo rozsahu

Hra cez internet, registrácia používateľov, grafický editor obsahu, iné OS ako Windows, dotykové ovládanie.

## Obsah dokumentácie

| priečinok | obsah |
|---|---|
| `01_Poziadavky` | zadanie, funkcionálne a nefunkcionálne požiadavky (MoSCoW + stav), roly |
| `02_Analyza` | prípady použitia (use cases) a diagram |
| `03_Navrh` | dátový model (ERD), schéma uložených súborov, návrh rozhraní |
| `04_Implementacia` | popis implementácie a štruktúry zdrojového kódu |
| `05_Testovanie` | testovacie scenáre a zistené chyby |
| `06_Dokumentacia` | inštalačná a používateľská príručka |
