# AGENTS.md

Tento repozitář slouží pro free‑form tvorbu softwaru pomocí Codexu, řízenou vzdáleně ze Slacku. Cílem je rychle zkoušet nápady v izolovaných složkách bez těžkého toolingu.

## Struktura repozitáře

- Každý nápad/projekt má vlastní složku v rootu repozitáře.
- Pojmenování složek: kebab-case nebo snake_case, bez mezer a bez diakritiky (např. `email-summarizer`, `image_tools`).
- Každá složka je „izolovaný“ implementační celek: neodkazuje na soubory v jiných složkách a nevyžaduje globální konfiguraci.

## Obsah složky nápadu/projektu

- `README.md`: krátký popis nápadu, jak spustit/zkusit, použité jazyky/nástroje, případně omezení či TODO.
- `.gitignore`: lokální pro daný nápad; přidej dle potřeby (závisí na použitém jazyce/nástrojích). Pokud existuje soubor `.env`, vždy ho ignoruj a přidej `/.env` a `/.env.*`.
- Volitelné: jednoduché skripty (`run.sh`, `run.ps1`, `Makefile`) pro rychlé spuštění — pouze pokud dávají smysl a zůstanou triviální.

Minimální šablona README nápadu:

```
# Název nápadu

Krátký popis, co to dělá a proč.

## Rychlý start
- Jak spustit / vyzkoušet (co nejjednodušeji)

## Závislosti
- Co je potřeba mít nainstalováno (minimalizovat knihovny)

## Poznámky
- Omezení, další nápady, TODO
```

Základní šablona `.gitignore` (rozšiř dle potřeby):

```
# OS/IDE
.DS_Store
Thumbs.db
.idea/
.vscode/
*.log

# Prostředí / build artefakty
.env
.env.*
venv/
__pycache__/
node_modules/
dist/
build/
*.tmp
```

## Hlavní README v rootu

- `README.md` v rootu obsahuje stručný a aktuální seznam složek/nápadů (odkaz + jednovětný popis).
- Při každém přidání/odstranění či přejmenování složky tento seznam aktualizuj.

Doporučený formát položky:

```
- [název-složky](název-složky/) – jednověté shrnutí.
```

## Zásady vývoje

- Jednoduchý, ne‑profesionální vývoj: žádný komplexní tooling, testy se neřeší.
- Minimalizovat závislosti; preferovat standardní knihovny.
- Každý nápad by měl jít snadno spustit lokálně (bez globální instalace nástrojů, pokud to jde).

## Workflow přes Slack a commity

- Každý požadavek ze Slacku se po implementaci commituje.
- Commit message je stručná a česky; pokud je změna větší, použij i Description.
- Doporučený formát zprávy: „Krátké, výstižné sdělení v oznamovací větě“ (např. „Přidán nápad email-summarizer a aktualizován seznam v README“).
- Commit provede agent (Codex) a v případě změny seznamu nápadů zároveň aktualizuje root `README.md`.

## Konvence a omezení

- Pojmenování souborů/adresářů: malá písmena, `kebab-case` nebo `snake_case`.
- Soubory s tajemstvími (API klíče apod.) se do repozitáře neukládají — použij `.env` a přilož `README.md` s popisem proměnných (`.env.example`).
- Velké binární soubory sem nepatří; pokud nutné, dej je do pod-složky `assets/` v rámci projektu a zvaž jejich ignorování.
- Projekty by si navzájem nesdílely kód. Pokud se objeví opakující se utilita, zkopíruj ji do daného projektu nebo explicitně vytvoř novou izolovanou utilitu jako samostatnou složku.

## Co ještě držet na paměti (doporučení navíc)

- Licence: pokud bude potřeba, uveď v rootu `LICENSE` (např. MIT). Jinak ponech prázdné.
- Archivace: staré/ukončené nápady můžeš přesunout do složky `archive/` (se stejnými pravidly struktury).
- Verzování závislostí: pokud nějaké použiješ, preferuj pevné verze (lockfile / konkrétní verze balíčku), ale bez těžkého toolingu.

—
Tyto pokyny se vztahují na celý repozitář. Pokud bude třeba udělat výjimku, uveď ji v příslušném `README.md` daného nápadu.
