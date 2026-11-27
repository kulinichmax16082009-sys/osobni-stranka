# Osobní stránka – Maksym Kulynych

## O projektu

Osobní webová stránka představující mě, mé dovednosti, zkušenosti a dosavadní programátorské projekty. Stránka slouží jako jednoduché osobní portfolio, ve kterém lze najít informace o mně, přehled mých projektů a kontaktní údaje.

Web je vytvořen pomocí HTML5 a CSS3 s důrazem na přístupnost podle standardu WCAG 2.2 na úrovni AA.

## Nasazená verze

[Otevřít osobní stránku](https://kulinichmax16082009-sys.github.io/osobni-stranka/)

## Obsah stránky

- **O mně** – základní informace o mém studiu a zájmech.
- **Projekty** – ukázky mých programátorských projektů:
  - Sample Five
  - Minesweeper Remake
  - NanoOmega
- **Dovednosti** – přehled mých IT znalostí.
- **Kontakt** – e-mailová adresa.

## Použité technologie

- HTML5
- CSS3
- Git a GitHub
- GitHub Actions
- GitHub Pages

## Přístupnost a Media rules

Stránka respektuje nastavení operačního systému a uživatelské preference pomocí CSS media queries. Cílem je zajistit přístupnost, čitelnost a správné zobrazení na různých zařízeních.

| Media rule / funkce | Popis |
|---|---|
| `@media (min-width: ...)` | Rozvržení se přizpůsobuje šířce obrazovky pomocí minimálně tří zlomových bodů, aby stránka fungovala od mobilů až po široké monitory bez vodorovného posuvníku. |
| `prefers-color-scheme: dark` | Přepíná stránku do tmavého barevného schématu včetně posuvníků, aby byla pohodlně čitelná i při používání tmavého režimu. |
| `prefers-contrast: more` | Zvyšuje kontrast textu na úroveň WCAG AAA, zvýrazňuje okraje, podtrhává odkazy a odstraňuje přechody a obrázky na pozadí pro lepší čitelnost. |
| `prefers-reduced-motion: reduce` | Vypíná animace, přechody a plynulé rolování, aby stránka omezila pohybové efekty pro uživatele citlivé na animace. |
| `prefers-reduced-transparency: reduce` | Nahrazuje průhledná pozadí karet plnými barvami a vypíná rozostření pozadí, aby byl obsah lépe čitelný. |
| `forced-colors: active` | Přizpůsobuje stránku systémovým barvám a pomocí okrajů a obrysů zachovává viditelnost tlačítek, karet a klávesnicového fokusu. |
| Kombinace nastavení (`prefers-color-scheme: dark` a `prefers-contrast: more`) | Samostatně ošetřuje současné použití tmavého režimu a vyššího kontrastu, aby zůstala zachována dobrá čitelnost i při kombinaci obou nastavení. |

Stránka dále podporuje ovládání klávesnicí, viditelné zvýraznění fokusu, přeskočení navigace na hlavní obsah a responzivní rozložení pro různá zařízení.

## Automatické nasazení

Projekt využívá GitHub Actions pro automatické nasazení na GitHub Pages. Po aktualizaci hlavní větve `main` se automaticky spustí workflow, který připraví a nasadí aktuální verzi stránky.