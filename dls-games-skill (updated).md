---
name: dls-games
description: >
  Use this skill whenever building HTML5 games using the DB Games Design Language System (DLS).
  This skill captures patterns, rules, and best practices learned from building 5 complete games:
  Quiz Master (quiz), Word Khoj (word search), Dino Run (endless runner), Meteor Dodge (dodge game),
  and Tic Tac Toe (board game). Apply this skill for ANY new game request in this DLS.
---

# DLS Games Skill

This skill codifies everything learned from building 5 production-quality HTML5 games
using the DB Games DLS. Always read and follow this skill before starting any new game.

---

## 1. DLS Reference Files (always consult all of these)

Fetch each file from its GitHub URL before starting any game. Always retrieve the latest version at build time.

| File | GitHub URL | What it governs |
|------|------------|----------------|
| `dls-typography.md`   | https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-typography.md | Font family, sizes, weights, line-heights |
| `dls-colors.md`       | https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-colors.md | All color tokens — base + 10 themes |
| `dls-icons.md`        | https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-icons.md | 70 exact SVG icons — use verbatim paths only |
| `dls-illustrations.md`| https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-illustrations.md | 28 illustrations — use exact SVG paths |
| `dls-logos.md`        | https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-logos.md | 15 brand + game logos — use exact SVG paths |
| `dls-components.md`   | https://github.com/joefrancis-dot/Game-DLS-Skill/raw/refs/heads/main/dls-components.md | Nav Bar, Buttons, Pause Popup, Streak, Pills |

**When to fetch each file:**
- **Always fetch before starting**: `dls-colors.md`, `dls-typography.md`, `dls-components.md`
- **Fetch when using icons**: `dls-icons.md`
- **Fetch when using illustrations**: `dls-illustrations.md`
- **Fetch when using logos**: `dls-logos.md`

**Golden rule: NEVER use anything outside these files. No external libraries,
no ad-hoc hex colors, no approximated icons, no outside fonts.**

---

## 2. Non-DLS Assets (Custom SVGs)

Sometimes a game needs a logo or character not in the DLS (e.g. dinosaur, robot).
**Always ask the user for approval before creating custom SVGs.**
If approved, build them as pixel-art using `<rect>` elements on a consistent grid unit (e.g. `P = 3px`).

Custom SVG rules:
- Use only DLS color tokens for fills (e.g. `#BEE95F` for Theme 4, `#000` for primary)
- Keep shapes simple — pixel-art style using `<rect>`, `<circle>`, `<path>` only
- Place logo on a **dark gradient background** for contrast against light theme backgrounds (see Section 18)
- Document the custom SVG clearly in the code with `<!-- custom, approved -->`

---

## 3. Game Screen Structure

Every game has exactly 3 screens in a single HTML file:

```
Screen 1 — Landing
Screen 2 — Game / Play
Screen 3 — Result
```

### Screen switching pattern
```js
function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  const el = document.getElementById(id);
  el.style.animation = 'none'; el.offsetHeight; el.style.animation = ''; // re-trigger
  el.classList.add('active');
}
```

### Screen animation
```css
.screen { display: none; animation: fadeUp 0.3s ease both; }
.screen.active { display: flex; }
@keyframes fadeUp {
  from { opacity:0; transform:translateY(16px); }
  to   { opacity:1; transform:translateY(0); }
}
```

---

## 4. Landing Screen

Structure (top to bottom):
1. **Logo** — DLS logo or custom approved SVG, centred, 120–160px
2. **Title** — Display 1 (32px/700), centred
3. **Subtitle** — Body 1 (18px/400), centred, `color: rgba(0,0,0,0.55)`
4. **Button Big Solid** — "खेल शुरू करें" + Arrow Forward icon

```css
/* Landing card — transparent, no white bg, no shadow */
background: transparent;
border-radius: 20px;
padding: 28px 24px;
```

**All cards (landing, game, result) are transparent** — the theme background colour
shows through on every screen. Never use `background: #fff` or `box-shadow` on cards.

Body background = chosen theme color on **all 3 screens**. Always add two decorative
blobs that persist across all screens (not just landing):
```css
body::before { position:fixed; width:280px; height:280px; top:-90px; right:-90px; background:rgba(255,255,255,0.22); border-radius:50%; }
body::after  { position:fixed; width:200px; height:200px; bottom:-60px; left:-60px; background:rgba(255,255,255,0.15); border-radius:50%; }
```

### Difficulty selector (optional, for games with AI)
```css
.diff-row { display:flex; gap:8px; width:100%; }
.diff-btn {
  flex:1; padding:9px 4px;
  border: 2px solid rgba(0,0,0,0.18); border-radius:10px;
  background: rgba(255,255,255,0.25);
  font-size:14px; font-weight:600; color:rgba(0,0,0,0.5);
}
.diff-btn.active {
  border-color: #000; background: rgba(0,0,0,0.12); color:#000;
}
```

---

## 5. Nav Bar — CRITICAL (DLS 226:1882)

The Nav Bar is a **separate component from the game card**. It sits **above** the game card.
**Nav bar background = game's theme color** (same as body bg for a seamless look).

```
┌─────────────────────────────────┐  ← .nav-bar (background: THEME_COLOR, full-width mobile)
│  [Home btn]  Game Title  [Action btn]  │  ← .nav-row1
│      [score pill]  [turn pill]         │  ← .nav-row2
└─────────────────────────────────┘
┌─────────────────────────────────┐  ← .game-card (background: transparent)
│           game content          │
└─────────────────────────────────┘
```

### Nav Bar CSS
```css
.nav-bar {
  background: THEME_COLOR;         /* use game's chosen theme color — matches body bg */
  border-radius: 0;                /* full-width on mobile — no radius */
  padding: 12px 16px;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 12px;
  align-items: center;
}
/* On wider screens restore card-like radius */
@media (min-width: 480px) {
  .nav-bar { border-radius: 20px 20px 0 0; }
}
.nav-row1 {
  display: flex; align-items: center;
  justify-content: space-between; width: 100%; gap: 8px;
}
.nav-title {
  flex: 1; font-size: 18px; font-weight: 600; line-height: 26px;
  color: #000; text-align: center;
}
```

### Nav Row 1 — always: [Icon Btn] + [Title] + [Icon Btn or spacer]
- Left button: **Home** icon (exact path from `Home-Outline.svg`) → goes to landing
- Right button: context-sensitive — Retry, Pause (Video-Pause icon), or invisible spacer `<div style="width:40px">`
- If only one icon button, use a 40px spacer on the other side to keep title centred

### Nav Row 2 — score pills + turn indicator
```css
/* Score pill — semi-white bg */
.score-pill {
  background: rgba(255,255,255,0.6);
  border-radius: 32px; padding: 4px 10px;
  display: flex; align-items: center; gap: 5px;
  font-size: 14px; font-weight: 600; color: #000;
}
/* Turn pill — black bg */
.turn-pill {
  background: #000;
  border-radius: 32px; padding: 4px 12px;
  font-size: 14px; font-weight: 600; color: #fff;
}
/* Timer pill — black bg */
.timer-pill {
  background: #000; border-radius: 32px; padding: 2px 8px;
  display: flex; align-items: center; gap: 4px;
  font-size: 16px; font-weight: 600; color: #fff;
}
/* Icon inside timer pill: Video-Pause (exact path), NOT Watch-Timer */

/* Life pill — semi-white bg */
.life-pill {
  background: rgba(255,255,255,0.6);
  border-radius: 32px; padding: 4px 8px;
  display: flex; align-items: center; gap: 3px;
}
/* Heart Solid icons inside, coloured with the game's theme color */
```

### Game Card CSS
```css
.game-card {
  background: transparent;         /* no white bg — theme shows through */
  border-radius: 0;                /* flat on mobile */
  padding: 20px 16px 28px;
  width: 100%;
}
@media (min-width: 480px) {
  .game-card { border-radius: 0 0 20px 20px; padding: 20px 24px 28px; }
}
```

### Game Wrapper (responsive container)
```css
.game-wrapper {
  display: flex; flex-direction: column; align-items: stretch;
  width: 100%; max-width: 480px; margin: 0 auto;
}
@media (min-width: 480px) {
  .game-wrapper { padding: 24px; }
}
```

---

## 6. Button System (exact DLS specs)

### Button Big Solid (226:1953)
```css
background: #000; color: #fff;
border: none; border-radius: 12px; padding: 14px 16px;
font-size: 20px; font-weight: 600; line-height: 30px;
display: flex; align-items: center; justify-content: center; gap: 8px;
width: 100%;
```

### Button Big Hollow (226:2033)
```css
background: rgba(255,255,255,0.2); color: #000;
border: 2px solid rgba(0,0,0,0.35); border-radius: 12px; padding: 14px 16px;
font-size: 20px; font-weight: 600; line-height: 30px;
width: 100%; margin-top: 12px;
```
> Note: Hollow button uses semi-transparent white bg so it reads clearly on theme-colored backgrounds.

### Button Icon Only Solid (226:2021)
```css
background: #000; border: none; border-radius: 12px;
width: 40px; height: 40px; padding: 8px;
display: flex; align-items: center; justify-content: center;
```
Icon inside must be white — always use exact SVG paths from `dls-icons.md`.

### Arrow Forward icon (use on every CTA button)
```svg
<path d="M4.99976 12.9998L16.4998 12.9998L11.4998 17.9998C11.0998 18.3998 11.0998 19.0998 11.4998 19.4998C11.8998 19.8998 12.4998 19.8998 12.8998 19.4998L19.6998 12.6998C20.0998 12.2998 20.0998 11.6998 19.6998 11.2998L12.8998 4.4998C12.4998 4.0998 11.8998 4.0998 11.4998 4.4998C11.0998 4.8998 11.0998 5.4998 11.4998 5.8998L16.4998 10.8998L4.99976 10.8998C4.39976 10.8998 3.99976 11.3998 3.99976 11.8998C3.99976 12.5998 4.49976 12.9998 4.99976 12.9998Z" fill="white"/>
```

---

## 7. Pause Popup (DLS 226:2230)

Used in games that can be paused. Always follows this exact structure:

```css
.pause-popup {
  background: #fff;
  border-radius: 20px;
  padding: 40px 24px;
  width: 320px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.3);
  display: flex; flex-direction: column;
  align-items: center;
  gap: 36px;          /* outer gap */
}
.pause-popup-content {
  display: flex; flex-direction: column;
  align-items: center; gap: 20px; width: 100%;
}
.pause-popup-text {
  display: flex; flex-direction: column;
  align-items: center; gap: 8px; text-align: center;
}
```

Inner content (in order):
1. **Timer illustration** (`Timer.svg` from `dls-illustrations.md`) at 48×48px — use exact SVG paths
2. **Title** — Headline 1: 24px / 600 / black — "आपका खेल रुका हुआ है"
3. **Subtitle** — Body 1: 18px / 400 / secondary — "खेलने के लिए तैयार?"
4. **Button Big Solid** — width 240px — "खेल जारी रखें"

**Do NOT add a hollow/secondary button inside the pause popup.**
The pause popup has exactly ONE CTA button.

Overlay:
```css
.pause-overlay {
  position: absolute; inset: 0;
  background: rgba(0,0,0,0.6);
  display: none; flex-direction: column;
  align-items: center; justify-content: center;
  z-index: 20;
}
.pause-overlay.visible { display: flex; }
```

Pause button in nav bar uses **Video-Pause icon** (exact paths):
```svg
<path d="M5.3 21H8.7C9.142 21 9.5 20.642 9.5 20.2V3.8C9.5 3.358 9.142 3 8.7 3H5.3C4.858 3 4.5 3.358 4.5 3.8V20.2C4.5 20.642 4.858 21 5.3 21Z" fill="white"/>
<path d="M15.3 21H18.7C19.142 21 19.5 20.642 19.5 20.2V3.8C19.5 3.358 19.142 3 18.7 3H15.3C14.858 3 14.5 3.358 14.5 3.8V20.2C14.5 20.642 14.858 21 15.3 21Z" fill="white"/>
```

---

## 8. Result Screen

Structure:
1. **Illustration** — semantic color icon (win/lose/draw) — see patterns below
2. **Session scoreboard** — transparent boxes with `rgba(255,255,255,0.25)` bg
3. **Title** — Headline 1 (24px/600)
4. **Subtitle** — Body 2 (16px/400), `color: rgba(0,0,0,0.55)`
5. **Button Big Solid** — "फिर खेलें"
6. **Button Big Hollow** — "होम पर जाएं"

### Result illustrations — semantic colors (NOT theme color)
```svg
<!-- WIN — green tick -->
<svg width="96" height="96" viewBox="0 0 96 96">
  <circle cx="48" cy="48" r="48" fill="#22C55E" fill-opacity="0.18"/>
  <circle cx="48" cy="48" r="34" fill="#22C55E"/>
  <path d="M30 49L42 61L66 35" stroke="white" stroke-width="6"
        stroke-linecap="round" stroke-linejoin="round" fill="none"/>
</svg>

<!-- LOSE — red cross -->
<svg width="96" height="96" viewBox="0 0 96 96">
  <circle cx="48" cy="48" r="48" fill="#EF4444" fill-opacity="0.18"/>
  <circle cx="48" cy="48" r="34" fill="#EF4444"/>
  <path d="M34 34L62 62M62 34L34 62" stroke="white" stroke-width="6" stroke-linecap="round"/>
</svg>

<!-- DRAW — orange equal sign -->
<svg width="96" height="96" viewBox="0 0 96 96">
  <circle cx="48" cy="48" r="48" fill="#F97316" fill-opacity="0.18"/>
  <circle cx="48" cy="48" r="34" fill="#F97316"/>
  <rect x="30" y="41" width="36" height="6" rx="3" fill="white"/>
  <rect x="30" y="53" width="36" height="6" rx="3" fill="white"/>
</svg>
```

> **Rule:** Result icons use fixed semantic colors — green/red/orange — regardless of game theme.
> This replaces the old theme-colored circle pattern.

### Result card & score boxes
```css
/* Result card — transparent like all other cards */
.result-card {
  background: transparent;
  border-radius: 20px;
  padding: 32px 24px 28px;
}

/* Score boxes */
.rs-box {
  background: rgba(255,255,255,0.25);
  border: 2px solid rgba(255,255,255,0.45);
  border-radius: 12px; padding: 12px 6px;
}
.rs-lbl { font-size:11px; font-weight:600; letter-spacing:.6px; text-transform:uppercase; color:rgba(0,0,0,0.5); }
.rs-val  { font-size:28px; font-weight:700; color:#000; }
```

---

## 9. Theme Color Application

Each game uses one theme color. Apply it **consistently across all 3 screens**:
- **Body/page background** — solid theme color on ALL screens (landing, game, result)
- **All cards** — `background: transparent` — never white, never shadowed
- **Board cells / grid** — `rgba(255,255,255,0.25)` background, `rgba(255,255,255,0.45)` border
- **Score/info boxes** — `rgba(255,255,255,0.25)` bg, `rgba(255,255,255,0.45)` border
- **Nav bar** — solid theme color (seamless with body bg)
- **Active/selected states** — solid theme color or white overlay
- **Life/heart icons** — solid theme color
- **Result illustration** — semantic colors only (green/red/orange) — NOT theme color
- **Hi-score badge** — `rgba(255,255,255,0.2)` bg, `rgba(255,255,255,0.45)` border

### Theme color reference
```
Theme 1 — #FFDB19 (Yellow)      → rgb(255,219,25)
Theme 2 — #81D7FF (Sky Blue)    → rgb(129,215,255)
Theme 3 — #D4A8FF (Lavender)    → rgb(212,168,255)
Theme 4 — #BEE95F (Lime)        → rgb(190,233,95)
Theme 5 — #FFAA89 (Peach)       → rgb(255,170,137)
Theme 6 — #D6ECA3 (Lt Green)    → rgb(214,236,163)
Theme 7 — #FAE3B2 (Warm Cream)  → avoid as game theme (too light for text contrast)
Theme 8 — #DDA6D2 (Mauve)       → rgb(221,166,210)
Theme 9 — #FEAAAA (Pink)        → rgb(254,170,170)
Theme 10— #C7E2DE (Teal)        → rgb(199,226,222)
```

---

## 10. Icon Usage Rules

**NEVER approximate or redraw icons.** Always copy the exact `<path>` data from `dls-icons.md`.

Most-used game icons and their correct usage:

| Icon | File | Usage |
|------|------|-------|
| Home Outline | `Home-Outline.svg` | Nav bar left button → go home |
| Retry | `Retry.svg` | Nav bar right button → restart/new round |
| Arrow Forward | `Arrow-Forward.svg` | CTA buttons — always white fill inside btn-solid |
| Video Pause | `Video-Pause.svg` | Pause button in nav bar (NOT Watch-Timer) |
| Heart Solid | `Heart_Solid.svg` | Lives indicator — fill with theme color |
| Win | `Win.svg` | Score/points display pill |
| Watch Timer | `Watch-Timer.svg` | Timer illustration ONLY — NOT as nav pill icon |
| Selection Right Tick Solid | `Selection-Right_Tick_Solid.svg` | Correct answer, found word chips |
| Close Circle Solid | `Close-Circle_Solid.svg` | Wrong answer indicator |

**Timer pill icon = Video-Pause** (two vertical bars)
**NOT Watch-Timer** (stopwatch shape) — this is a common mistake to avoid.

---

## 11. Typography in Games

All text uses `'Noto Sans', sans-serif` — never any other font.

| Context | DLS Style | CSS |
|---------|-----------|-----|
| Game title (landing) | Display 1 | `32px / 700 / 42px` |
| Game title (nav) | Headline 3 | `18px / 600 / 26px` |
| Question text | Headline 1 | `24px / 600 / 36px` |
| Button labels | Headline 2 | `20px / 600 / 30px` |
| Option / cell text | Headline 4 | `16px / 600 / 24px` |
| Score/timer | Headline 4 | `16px / 600 / 24px` |
| Badge / chip labels | Headline 5 | `14px / 600 / 22px` |
| Status hints | Label | `12px / 600 / 18px` |
| Body text | Body 1 | `18px / 400 / 28px` |
| Sub-text | Body 2 | `16px / 400 / 26px` |
| Result score | Custom large | `56px / 700` |

---

## 12. Language

- All UI text in **Hindi** by default unless specified
- Numbers always in **Western Arabic** (0–9), never Devanagari numerals
- Hindi scores: "स्कोर", "जीवन", "समय", "राउंड", "स्तर"
- Hindi CTAs: "खेल शुरू करें", "फिर खेलें", "होम पर जाएं", "जारी रखें", "खेल जारी रखें"

---

## 13. Game Loop Patterns

### Quiz Game pattern
```
landing → game (Q1→Q2→Q3→Q4→Q5, auto-advance on answer) → result
```
- Auto-advance after 1000ms delay showing correct/wrong
- No manual "Next" button
- Progress bar fills per question

### Word Search pattern
```
landing → game (drag to select, LR or TB only) → result
```
- `pointerdown` / `pointerenter` / `pointerup` for drag
- Only straight lines (same row OR same col, forward only)
- Green flash on correct, red flash on wrong, 400ms then clear

### Endless Runner pattern
```
landing → game (tap/space to jump, auto-scroll) → result
```
- `requestAnimationFrame` loop
- Gravity constant + velocity for jump physics
- Score = frame count / divisor

### Dodge Game pattern
```
landing → game (left/right movement, falling obstacles) → result
```
- AABB collision detection
- Invincibility frames after hit (robot blinks)
- Particle explosion on collision
- Lives system with heart icons

### Board Game (Tic Tac Toe) pattern
```
landing → game (click cell, AI responds) → result (auto, no button)
→ "फिर खेलें" returns to game screen with reset board (scores persist)
```
- 3 difficulty levels: Easy / Medium / Hard
  - **Easy**: 25% smart moves, 75% random
  - **Medium**: smart moves with 22% random imperfection (recommended default)
  - **Hard**: pure minimax — unbeatable
- Smart move priority: Win → Block → Center → Corner (shuffled) → Edge
- **Draw rule**: after a draw, computer starts first in the next round
- Scores persist across all rounds within a session
- Win cells highlighted with `winPop` animation
- Result shown after 700ms delay
- AI move delay: 300–600ms random (human-like)

---

## 14. Canvas Games — Key Patterns

For games using `<canvas>`:

```js
// Always use requestAnimationFrame
function loop() {
  if (!gameRunning) return;
  update();
  draw();
  raf = requestAnimationFrame(loop);
}

// Always cancel on game over / home / pause
cancelAnimationFrame(raf);

// Canvas pixel unit for pixel art
const P = 3; // 1 pixel unit = 3px
```

Draw order (back to front):
1. Sky / background gradient
2. Stars / ambient elements
3. Ground
4. Obstacles / enemies
5. Player character
6. Particles / effects
7. HUD (score on canvas if needed)

---

## 15. Mobile Considerations

- `user-select: none` on body — prevents text selection during gameplay
- `touch-action: none` on canvas — prevents scroll interference
- All tap zones minimum 44×44px
- For full-screen mobile games (360×720): use `.phone` wrapper container
- For card-based games: `max-width: 480px` centred (updated from 390px to accommodate nav bar)
- Nav bar is **full-width on mobile** (`border-radius: 0`), gains radius at `≥ 480px`

---

## 16. Common Mistakes to Avoid

| ❌ Wrong | ✅ Correct |
|----------|-----------|
| Watch-Timer icon in timer pill | Video-Pause icon in timer pill |
| Nav bar inside white card | Nav bar separate, above game card |
| Hollow button inside Pause Popup | Only 1 solid button inside Pause Popup |
| Custom hex colors | Only DLS color tokens |
| Approximated icon paths | Exact paths from dls-icons.md |
| Noto Sans Devanagari font | Noto Sans only (supports Devanagari natively) |
| `transform="scale(N)"` on SVG paths | Native viewBox scaling only |
| Manual "Next" button on quiz | Auto-advance after 1 second |
| Numbers in Hindi script | Western Arabic numerals (0–9) always |
| Adding extra buttons to Pause Popup | One CTA only |
| White card background (`#fff`) on screens | Transparent cards — theme bg shows through |
| Nav bar always `#FAE3B2` | Nav bar uses game's theme color |
| Theme-colored result icon (circle + checkmark) | Green `#22C55E` tick / Red `#EF4444` cross / Orange `#F97316` draw |
| Blobs only on landing screen | Blobs persist across all 3 screens via `body::before/after` |
| `max-width: 390px` for card games | `max-width: 480px` for game wrapper |

---

## 17. File Output

- Single `.html` file, self-contained
- No external JS libraries
- No external CSS frameworks
- `@import` Google Fonts for Noto Sans only
- Canvas-based games: inline `<canvas>` + JS
- DOM-based games: inline HTML + CSS + JS

---

## 18. Custom Logo Pattern (High Contrast)

For game logos, use a **dark gradient background** to create strong contrast against
the light theme background. This prevents the logo from blending into the page.

```svg
<!-- Logo structure — dark bg + gradient marks + glow filter -->
<svg viewBox="0 0 160 160" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <!-- Dark bg gradient — deep version of theme hue -->
    <linearGradient id="bgGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#1a0533"/>   <!-- very dark theme hue -->
      <stop offset="100%" stop-color="#2d0d4e"/>
    </linearGradient>
    <!-- Accent gradient for primary mark (X) -->
    <linearGradient id="xGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#E879F9"/>   <!-- lighter theme hue -->
      <stop offset="100%" stop-color="#A855F7"/>  <!-- theme color -->
    </linearGradient>
    <!-- Soft glow filter -->
    <filter id="glow">
      <feGaussianBlur stdDeviation="2.5" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <!-- Background -->
  <rect width="160" height="160" rx="32" fill="url(#bgGrad)"/>

  <!-- Grid lines — subtle white -->
  <line x1="55" y1="18" x2="55" y2="142" stroke="rgba(255,255,255,0.22)" stroke-width="4" stroke-linecap="round"/>
  <!-- ... repeat for other grid lines ... -->

  <!-- X marks — gradient + glow -->
  <g filter="url(#glow)">
    <line x1="24" y1="24" x2="46" y2="46" stroke="url(#xGrad)" stroke-width="6" stroke-linecap="round"/>
    <line x1="46" y1="24" x2="24" y2="46" stroke="url(#xGrad)" stroke-width="6" stroke-linecap="round"/>
  </g>

  <!-- O marks — crisp white -->
  <circle cx="123" cy="30" r="13" stroke="rgba(255,255,255,0.85)" stroke-width="5" fill="none"/>

  <!-- Win line — gradient stroke -->
  <line x1="28" y1="28" x2="132" y2="132" stroke="url(#xGrad)" stroke-width="3.5" stroke-linecap="round" opacity="0.7"/>
</svg>
```

**Logo rules:**
- Background: dark gradient — deep/dark version of the game's theme hue
- Primary marks (X): theme gradient with `feGaussianBlur` glow filter
- Secondary marks (O): `rgba(255,255,255,0.85)` — crisp white
- Grid lines: `rgba(255,255,255,0.22)` — subtle, not overpowering
- Win line: theme gradient at 0.7 opacity
- Always `<!-- custom, approved -->` comment in code
