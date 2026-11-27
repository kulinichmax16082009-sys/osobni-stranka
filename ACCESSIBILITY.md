# Zpráva o přístupnosti

Příklady řádků nahraďte vlastními výsledky. Zapište alespoň tři skutečné nálezy
a u každého hash commitu, který ho opravil (najdete ho v `git log --oneline`).

## Výsledky nástrojů

| Nástroj | Před opravami | Po opravách |
| --- | --- | --- |
| Lighthouse (Accessibility) | Nebyla nalezena žádná chyba (100%) | Není potřeba opravovat |
| WAVE (Errors a Contrast Errors) | 0 errors, 0 contrast errors, 0 alerts | Není potřeba opravovat |
| Test klávesnicí | Všechno je v pořádku a web lze volně projít klávesnicí | Není potřeba opravovat |

## Nalezené problémy a jejich opravy

| Problém | Jak jsem ho našel | Oprava (commit) | Kritérium WCAG |
| --- | --- | --- | --- |
| Neplatná cesta v `src` u obrázku, v názvu souboru je mezera (Hláška chyby v html validátoru) | Použíl jsem na to https://validator.w3.org/ | `ed82efd` | 4.1.1 Parsing |
| Neplatný rozměr textu v px | při čtení kriterií WCAG (Ovladatelnost) | `b15218c` | 2.5.8 |

## Test media rules 

| Nastavení | Co jsem při emulaci viděl | V pořádku |
| --- | --- | --- |
| prefers-color-scheme: dark | Tmavé pozadí `#121212`, světlý text, světle modré odkazy, karty a tabulka tmavě azurové | Ano |
| prefers-contrast: more | Čistě bílé pozadí, černý text, 2px okraje, odkazy podtržené, kontrast textu 21 | Ano |
| prefers-reduced-motion: reduce | Karta se při najetí nezvedne, odkazy mění barvu okamžitě, rolování na kotvu skočí hned | Ano |
| prefers-reduced-transparency: reduce | Karty mají plnou barvu, rozostření pozadí zmizelo | Ano |
| forced-colors: active | Systémové barvy, okraje karet a tabulky i obrys fokusu jsou vidět, stín zmizel | Ano |

## Kritéria WCAG 2.2 úrovně A a AA

Specifikace: https://www.w3.org/TR/WCAG22/ (kritérium najdete podle čísla).
Úrovně A a AA mají dohromady 55 kritérií (31 úrovně A a 24 úrovně AA). Kritérium
4.1.1 Parsing bylo ve verzi 2.2 odstraněno, proto v tabulce není.

U každého kritéria nahraďte TODO. Ve sloupci Stav ponechte jedno ze tří slov:

- **Splněno**: do posledního sloupce napište, kde a jak (například „všechny obrázky mají alt“).
- **Nevztahuje se**: do posledního sloupce napište, proč (například „na stránce není video“).
- **Nesplněno**: kritérium opravte a stav změňte. V odevzdané verzi nesmí zůstat žádné
  Nesplněno ani TODO.

Kritéria označená „nové“ přibyla ve verzi 2.2.

### 1 Perceivable (vnímatelnost)

| Kritérium | Název | Úroveň | Stav | Kde a jak / proč ne |
| --- | --- | --- | --- | --- |
| 1.1.1 | Non-text Content | A | Splněno | Všechny 4 obrázky (fotografie a 3 snímky projektů) mají `alt`; WAVE hlásí 0 chyb. |
| 1.2.1 | Audio-only and Video-only (Prerecorded) | A | Nevztahuje se | Na stránce není žádné audio ani video. |
| 1.2.2 | Captions (Prerecorded) | A | Nevztahuje se | Na stránce není video se zvukem. |
| 1.2.3 | Audio Description or Media Alternative (Prerecorded) | A | Nevztahuje se | Na stránce není video. |
| 1.2.4 | Captions (Live) | AA | Nevztahuje se | Na stránce není živý přenos. |
| 1.2.5 | Audio Description (Prerecorded) | AA | Nevztahuje se | Na stránce není video. |
| 1.3.1 | Info and Relationships | A | Splněno | Sémantické prvky `header`, `nav`, `main`, `section`, `article`, `address`, `footer`; nadpisy h1–h3 bez přeskočení; tabulka má `caption` a `th` se `scope`; sekce mají `aria-labelledby`. |
| 1.3.2 | Meaningful Sequence | A | Splněno | Pořadí v HTML odpovídá vizuálnímu pořadí, layout řeší jen CSS flex a grid bez `order`. |
| 1.3.3 | Sensory Characteristics | A | Splněno | Text nic neurčuje podle tvaru, barvy ani polohy. |
| 1.3.4 | Orientation | AA | Splněno | Orientace displeje není nijak zamčená, layout je responzivní. |
| 1.3.5 | Identify Input Purpose | AA | Nevztahuje se | Na stránce není formulář ani pole pro osobní údaje. |
| 1.4.1 | Use of Color | A | Splněno | Odkazy mají podtržení (při vysokém kontrastu zesílené), informace nejsou předávány jen barvou. |
| 1.4.2 | Audio Control | A | Nevztahuje se | Na stránce se nepřehrává žádný zvuk. |
| 1.4.3 | Contrast (Minimum) | AA | Splněno | Lighthouse i WAVE: 0 chyb kontrastu; barvy jsou v CSS proměnných pro světlý, tmavý a vysoký kontrast. |
| 1.4.4 | Resize Text | AA | Splněno | Velikosti jsou v `rem`; při zvětšení na 200 % se nic neztrácí ani nepřekrývá. |
| 1.4.5 | Images of Text | AA | Splněno | Text je skutečný text, nepoužívám obrázky textu. |
| 1.4.10 | Reflow | AA | Splněno | Na úzkých displejích se layout skládá do jednoho sloupce, `img` má `max-width: 100%`, `body` má `overflow-wrap: break-word`; při 320 px není vodorovné posouvání. |
| 1.4.11 | Non-text Contrast | AA | Splněno | Ohraničení tabulky a karet (`#767676`, ve tmavém režimu `#8a8a8a`) a focus outline mají kontrast alespoň 3:1. |
| 1.4.12 | Text Spacing | AA | Splněno | Žádné pevné výšky; po přepsání `line-height`, `letter-spacing` a `word-spacing` v DevTools nic nemizí ani se nepřekrývá. |
| 1.4.13 | Content on Hover or Focus | AA | Nevztahuje se | Při najetí ani zaostření se nezobrazuje nový obsah, jen se změní pozadí a stín karty. |

### 2 Operable (ovladatelnost)

| Kritérium | Název | Úroveň | Stav | Kde a jak / proč ne |
| --- | --- | --- | --- | --- |
| 2.1.1 | Keyboard | A | Splněno | Veškeré ovládání tvoří nativní odkazy dostupné klávesou Tab. |
| 2.1.2 | No Keyboard Trap | A | Splněno | Při procházení Tabem se focus nikde nezasekne. |
| 2.1.4 | Character Key Shortcuts | A | Nevztahuje se | Stránka nemá žádné klávesové zkratky. |
| 2.2.1 | Timing Adjustable | A | Nevztahuje se | Stránka nemá žádný časový limit. |
| 2.2.2 | Pause, Stop, Hide | A | Nevztahuje se | Nic se samo nehýbe ani neaktualizuje; jsou jen krátké přechody při najetí a ty respektují `prefers-reduced-motion`. |
| 2.3.1 | Three Flashes or Below Threshold | A | Splněno | Na stránce nic neblikává. |
| 2.4.1 | Bypass Blocks | A | Splněno | Skip link „Přejít na obsah“ vede na `<main id="obsah">`; stránka má i landmarky. |
| 2.4.2 | Page Titled | A | Splněno | `<title>Maksym Kulynych – osobní stránka</title>`. |
| 2.4.3 | Focus Order | A | Splněno | Pořadí focusu odpovídá pořadí v HTML, nepoužívám `tabindex`. |
| 2.4.4 | Link Purpose (In Context) | A | Splněno  | Texty odkazů (O mně, Projekty, Dovednosti, Kontakt, e-mail) jsou srozumitelné samy o sobě. |
| 2.4.5 | Multiple Ways | AA | Nevztahuje se | Web tvoří jediná stránka; k jejím sekcím vede navigace v hlavičce. |
| 2.4.6 | Headings and Labels | AA | Splněno | Nadpisy popisují obsah sekcí a projektů, tabulka má `caption`. |
| 2.4.7 | Focus Visible | AA | Splněno | `:focus-visible` má outline 3 px v barvě odkazu (zesílený při vysokém kontrastu a ve forced colors). |
| 2.4.11 | Focus Not Obscured (Minimum) (nové) | AA | Splněno | Na stránce není žádný prvek s `position: fixed` ani `sticky`, takže nic nezakryje prvek se zaostřením. |
| 2.5.1 | Pointer Gestures | A | Nevztahuje se | Stránka nepoužívá žádná gesta, jen klik na odkazy. |
| 2.5.2 | Pointer Cancellation | A | Splněno | Používám jen nativní odkazy, které se spustí až po uvolnění tlačítka. |
| 2.5.3 | Label in Name | A | Splněno | Přístupný název odkazů je jejich viditelný text, nepoužívám `aria-label`. |
| 2.5.4 | Motion Actuation | A | Nevztahuje se | Stránka se neovládá pohybem zařízení. |
| 2.5.7 | Dragging Movements (nové) | AA | Nevztahuje se | Na stránce není žádné tažení. |
| 2.5.8 | Target Size (Minimum) (nové) | AA | Nesplněno | Odkazy v navigaci mají mezi sebou odstupy (`gap`), čímž splňují výjimku pro rozestupy; e-mail je odkaz uvnitř věty; Rozměr musí být minimálně 24px, což není |

### 3 Understandable (srozumitelnost)

| Kritérium | Název | Úroveň | Stav | Kde a jak / proč ne |
| --- | --- | --- | --- | --- |
| 3.1.1 | Language of Page | A | Splněno | `<html lang="cs">`. |
| 3.1.2 | Language of Parts | AA | Splněno | Text je česky; anglické výrazy jsou názvy projektů a odborné termíny (Command Pattern, JSON, JAR), pro které WCAG výjimku dává. |
| 3.2.1 | On Focus | A | Splněno | Zaostření na prvek nevyvolá žádnou změnu. |
| 3.2.2 | On Input | A | Nevztahuje se | Na stránce nejsou žádná vstupní pole. |
| 3.2.3 | Consistent Navigation | AA | Nevztahuje se | Web má jedinou stránku, navigace se neopakuje na více stránkách. |
| 3.2.4 | Consistent Identification | AA | Nevztahuje se | Web má jedinou stránku. |
| 3.2.6 | Consistent Help (nové) | A | Nevztahuje se | Web má jedinou stránku a žádný mechanismus nápovědy; kontakt je jen sekce s e-mailem. |
| 3.3.1 | Error Identification | A | Nevztahuje se | Na stránce není formulář, kontakt je jen odkaz `mailto:`. |
| 3.3.2 | Labels or Instructions | A | Nevztahuje se | Na stránce nejsou žádná pole k vyplnění. |
| 3.3.3 | Error Suggestion | AA | Nevztahuje se | Na stránce není formulář. |
| 3.3.4 | Error Prevention (Legal, Financial, Data) | AA | Nevztahuje se | Stránka neobsahuje právní, finanční ani datové transakce. |
| 3.3.7 | Redundant Entry (nové) | A | Nevztahuje se | Uživatel na stránce nic nezadává. |
| 3.3.8 | Accessible Authentication (Minimum) (nové) | AA | Nevztahuje se | Na stránce není přihlašování. |

### 4 Robust (robustnost)

| Kritérium | Název | Úroveň | Stav | Kde a jak / proč ne |
| --- | --- | --- | --- | --- |
| 4.1.2 | Name, Role, Value | A | Splněno | Používám nativní prvky (odkazy, tabulka); `nav` má `aria-label`, sekce `aria-labelledby`; WAVE hlásí 0 chyb. |
| 4.1.3 | Status Messages | AA | Nevztahuje se | Na stránce není JavaScript a nic se samo nemění, takže není potřeba `aria-live`. |
