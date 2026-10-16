# Stickops – dokumentácia projektu

2D bojová hra paličkových postáv pre Windows s AI súpermi, kampaňou a obsahom v súboroch JSON.
Zdrojový kód je v koreni repozitára (`game/`, `ai/`), táto zložka obsahuje projektovú dokumentáciu.

| priečinok | súbory |
|---|---|
| [01_Poziadavky](01_Poziadavky) | [zadanie.md](01_Poziadavky/zadanie.md), `funkcionalne-poziadavky.xlsx`, `nefunkcionalne-poziadavky.xlsx`, `role-systemu.xlsx` |
| [02_Analyza](02_Analyza) | `use-case.docx` (13 prípadov použitia + matica sledovateľnosti), `use-case-diagram.png` |
| [03_Navrh](03_Navrh) | `erd-diagram.png` (dátový model obsahu), `db-schema.png` (schéma súborov JSON), `navrh-rozhranii.pdf` |
| [04_Implementacia](04_Implementacia) | [README.md](04_Implementacia/README.md) – architektúra a štruktúra kódu |
| [05_Testovanie](05_Testovanie) | `testovacie-scenare.xlsx`, `zistene-chyby.xlsx` |
| [06_Dokumentacia](06_Dokumentacia) | `instalacna-prirucka.docx`, `pouzivatelska-prirucka.docx` |

Hra nepoužíva databázový server – všetky dáta sú v súboroch JSON. Diagramy v `03_Navrh` preto opisujú
dátový model obsahu a uložených súborov.

Stav dokumentácie: 16. 10. 2026 · autor: Patrik Nottny
