# Design — Project Identity

> This document is project-long-lived. Tokens are not changed without
> the Architect's approval. Developers MUST use these tokens
> instead of improvising their own colors/spacings.

## Style Direction

Storybook-Mittelalter bei Dämmerung: warme Pergament-/Steintöne mit goldenem Akzent, klare Pixel-Art-Silhouetten und geschmiedet wirkendes HUD — stimmungsvoll, aber ruhig und maximal lesbar.

## Colors

- `--color-bg`: **#2b2438**
- `--color-fg`: **#f4ead6**
- `--color-accent`: **#e8b04b**
- `--color-border`: **#6b5a44**
- `--color-muted`: **#9a8c74**
- `--color-sky_top`: **#3a3350**
- `--color-sky_bottom`: **#7a5b6e**
- `--color-ground`: **#4a3b2a**
- `--color-ground_top`: **#6b5335**
- `--color-hill_far`: **#4d4560**
- `--color-hill_near`: **#5a4a52**
- `--color-stone`: **#8a8577**
- `--color-stone_shadow`: **#5f5b50**
- `--color-knight_armor`: **#c3cbd6**
- `--color-knight_armor_shadow`: **#7f8a9a**
- `--color-knight_tunic`: **#a63a3a**
- `--color-knight_outline`: **#1c1a24**
- `--color-danger`: **#c94b3b**
- `--color-gold_shadow`: **#a87a24**

## Spacing Scale

- `--space-0`: 4px
- `--space-1`: 8px
- `--space-2`: 12px
- `--space-3`: 16px
- `--space-4`: 24px
- `--space-5`: 32px
- `--space-6`: 48px

## Border-Radii

- `--radius-sm`: 2px
- `--radius-md`: 4px
- `--radius-lg`: 8px
- `--radius-pill`: 999px

## Components

### Button

Pixel-Rahmen-Look. padding 14/28, min-height 48px (Touch), radius sm (2px, scharfe Kanten wirken pixelig). bg=accent #e8b04b, fg=#2b2438, 3px solider Rand #a87a24, 2px dunkler Innen-Shadow unten für 'geprägten' Look. hover: bg +8% Lightness (#efc069). active: 2px nach unten versetzt, Innen-Shadow oben (gedrückt). disabled: opacity 0.5, kein Hover. font_family Pixel-Stack, uppercase, letter-spacing 1px. Sekundär-Variante: transparenter bg, 2px Rand accent, fg=accent.

### Sprite: Ritter (Player)

48x48px Pixel-Art, läuft nach rechts gewandt. Silhouette: kompakter Ritter mit Helm, Schild vorn, leicht vorgeneigt. Farben min. 4 Töne + Outline: Rüstung knight_armor #c3cbd6, Rüstungs-Schatten knight_armor_shadow #7f8a9a, Tunika/Umhang knight_tunic #a63a3a (roter Akzent = sofort auffindbar), Helm-Highlight #e8f0f8, Outline knight_outline #1c1a24 (1px, komplett umlaufend für Lesbarkeit vor jedem BG). Lauf-Animation: 4 Frames (Beine wechseln, Umhang schwingt) ~10fps. Sprung-Frame: 1 gestreckte Pose (Beine angewinkelt). KEINE einfarbigen Rechtecke. Kollisions-Hitbox 4px kleiner als Sprite (fair).

### Sprite: Hindernisse

Zwei Typen, je 32-40px hoch, Pixel-Art mit Outline #1c1a24. (1) Steinbarriere/Zinnen-Block: stone #8a8577 + stone_shadow #5f5b50 + Highlight #b0aa98, quaderförmig mit gemeißelten Fugen. (2) Fass/Holzstapel: ground_top #6b5335 + ground #4a3b2a + Reifen-Highlight #9a8c74. Alle Hindernisse stehen auf der Bodenlinie, deutlicher Kontrast zum Boden durch dunklere Outline. Silhouette klar erkennbar in <0.2s.

### Hintergrund (Parallax)

3 Ebenen, alle Pixel-Art, scrollen nach links. Himmel: vertikaler Verlauf sky_top #3a3350 → sky_bottom #7a5b6e (Dämmerung). Ferne Hügel/Burgsilhouette hill_far #4d4560 (langsam, ~20% Speed). Nahe Bäume/Mauern hill_near #5a4a52 (~50% Speed). Boden ground #4a3b2a mit ground_top #6b5335 Deckschicht + Pixel-Steinmuster (100% Speed). Alle BG-Töne bewusst entsättigt/dunkel, damit der helle Ritter mit rotem Umhang immer heraussticht.

### HUD: Score/Distanz

Oben rechts, Abstand 16px zum Rand. Pixel-Font score-Größe 24px, fg #f4ead6 mit 2px Shadow #1c1a24 für Lesbarkeit über jedem BG. Label 'DISTANZ' in note-Größe 11px, muted #9a8c74 darüber. Zahl steigt live. Optional kleines Münz/Meilenstein-Icon in accent. Immer im obersten z-Layer, nie von Sprites verdeckt.

### Screen: Start/Menü

Zentriert über pausiertem BG (leicht abgedunkelt mit rgba(43,36,56,0.55) Overlay). Titel h1 32px accent 'DER RITTERLAUF' mit Outline-Shadow. Darunter Body-Hinweis fg: 'Leertaste / Pfeil hoch / Tippen = Springen'. Primär-Button 'START'. Alles gestapelt, spacing 24px, max-width 480px.

### Screen: Game Over

Overlay rgba(43,36,56,0.75) über eingefrorenem Spiel. Zentriert: h1 32px danger #c94b3b 'GEFALLEN', darunter Endstand groß (score 24px accent, 'DISTANZ: 1234'). Primär-Button 'NEU STARTEN' + note 'oder Leertaste / Tippen'. spacing 16-24px, Karte optional mit border #6b5a44 2px, bg leicht dunkler.

### Card / Panel

Für Menü- und Game-Over-Boxen. bg #2b2438 mit 2px Rand #6b5a44, radius md 4px, padding 24/32, dezenter Innen-Shadow. Pixel-scharfe Kanten, kein Blur.

### Readability-Regeln

1) Ritter (hell + roter Umhang) läuft immer vor entsättigten dunklen BG-Ebenen → dauerhaft hoher Kontrast. 2) Jedes Spielobjekt hat 1px dunkle Outline #1c1a24. 3) Hindernisse nie in derselben Helligkeit wie der direkt dahinterliegende BG-Streifen. 4) HUD-Text immer mit Shadow, im obersten Layer. 5) canvas image-rendering: pixelated; Integer-Scaling bevorzugen, damit Pixel scharf bleiben.

## Layout Principles

- Canvas füllt den Viewport bis max-width 1280px, zentriert; darüber schwarze/bg-Letterbox-Ränder.
- Interne Render-Auflösung fix (z.B. 960x540, 16:9), per CSS responsiv skaliert — Spiel-Logik in virtuellen Einheiten, nicht in Bildschirm-Pixeln.
- Breakpoints: <600px Mobile (Touch-Steuerung, HUD-Text +2px für Lesbarkeit), 600-1024px Tablet, >1024px Desktop.
- Bodenlinie konstant bei ~80% der Canvas-Höhe; alle Sprites richten sich daran aus.
- image-rendering: pixelated global; möglichst Integer-Scale-Faktoren für scharfe Pixel-Art.
- Overlays (Menü/Game-Over) immer zentriert, max-width 480px, mit halbtransparentem bg-Overlay über dem eingefrorenen Spiel.
- Sicherer HUD-Bereich: 16px Abstand zu allen Canvas-Rändern (Notch/Safe-Area beachten).
