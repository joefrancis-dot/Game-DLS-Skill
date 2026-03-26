# DLS — UI Components

> Refer to this file every time a design is requested.

## ⚠️ Core Composition Rule
**All UI components are built exclusively from DLS primitives.** This means:
- **Colors** — only from `dls-colors.md` (Base Colors + Theme palette). No ad-hoc hex values.
- **Typography** — only Noto Sans at the exact sizes/weights defined in `dls-typography.md`.
- **Icons** — only from the 70-icon set in `dls-icons.md`. Never use external icon libraries.
- **Illustrations** — only from `dls-illustrations.md` when a contextual visual is needed.
- **Logos** — only from `dls-logos.md`. Never recreate or approximate.
- **Spacing, radius, shadow** — follow the exact values defined per component in this file.

When building any screen or component, always compose it upward from these primitives. Do not introduce colors, fonts, icons, or styles outside the DLS.

---

## Component Index

1. [Nav Bar](#1-nav-bar)
2. [Buttons — Solid](#2-buttons--solid)
3. [Buttons — Hollow](#3-buttons--hollow)
4. [Button — Disabled](#4-button--disabled)
5. [Button — Icon Only](#5-button--icon-only)
6. [Pause Popup](#6-pause-popup)
7. [Streak Counter](#7-streak-counter)
8. [Streak Days (sub-component)](#8-streak-days-sub-component)
9. [Bottom Options Pill](#9-bottom-options-pill)

---

## 1. Nav Bar

**Figma node:** `226:1882`

The game navigation bar sits at the top of a game screen. It contains a home button, a level title, a retry button, plus a timer and life counter row beneath.

**Visual preview:**
- Background: `#FAE3B2` (Theme 7)
- Padding: `12px` all sides, gap `16px` between rows
- Row 1 — Icon button (Home, black, 40×40 rounded-12) + centered Headline 3 title + Icon button (Retry, black, 40×40 rounded-12)
- Row 2 — Life counter pill (`rgba(255,255,255,0.6)` bg, 5× Heart Solid icons at 20px) + Timer pill (black bg, pause icon + time text in white, Headline 4)

**CSS spec:**
```css
.nav-bar {
  background: #FAE3B2;
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
  padding: 12px;
  width: 100%;
}

/* Icon buttons in top row */
.nav-btn {
  background: #000;
  border-radius: 12px;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8px;
}

/* Life pill */
.life-pill {
  background: rgba(255, 255, 255, 0.6);
  border-radius: 32px;
  padding: 4px 8px;
  display: flex;
  gap: 4px;
  align-items: center;
}

/* Timer pill */
.timer-pill {
  background: #000;
  border-radius: 32px;
  padding: 2px 8px;
  display: flex;
  gap: 4px;
  align-items: center;
  color: #fff;
  font-size: 16px;
  font-weight: 600;
  line-height: 24px;
}
```

---

## 2. Buttons — Solid

All solid buttons share: `background: #000`, `color: #fff`, `border-radius: 12px`, `padding: 14px vertical`. They support optional start icon + label + end icon (Arrow Forward).

### Button Big Solid
**Figma node:** `226:1953`
- Font: Headline 2 (20px / 30px / 600)
- Padding: `14px 16px`
- Icon size: 24px
- Height: ~54px

### Button Medium Solid
**Figma node:** `226:1973`
- Font: Headline 4 / Button 2 (16px / 24px / 600)
- Padding: `14px 12px`
- Icon size: 20px

### Button Small Solid
**Figma node:** `226:1997`
- Font: Headline 5 / Button 3 (14px / 22px / 600)
- Padding: `14px 12px`
- Icon size: 16px

**CSS spec (Big Solid as base):**
```css
.btn-solid {
  background: #000;
  color: #fff;
  border-radius: 12px;
  padding: 14px 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  font-family: 'Noto Sans', sans-serif;
  font-weight: 600;
  overflow: hidden;
  cursor: pointer;
}
.btn-solid.big   { font-size: 20px; line-height: 30px; padding: 14px 16px; }
.btn-solid.medium { font-size: 16px; line-height: 24px; padding: 14px 12px; }
.btn-solid.small  { font-size: 14px; line-height: 22px; padding: 14px 12px; }
```

---

## 3. Buttons — Hollow

All hollow buttons share: `background: transparent`, `border: 2px solid #000`, `color: #000`, `border-radius: 12px`. Same size/font rules as solid variants.

### Button Big Hollow
**Figma node:** `226:2033`
- Font: Headline 2 (20px / 30px / 600)
- Padding: `14px 16px`
- Icon size: 24px

### Button Medium Hollow
**Figma node:** `226:2057`
- Font: Headline 4 / Button 2 (16px / 24px / 600)
- Padding: `14px 12px`
- Icon size: 20px

### Button Small Hollow
**Figma node:** `226:2081`
- Font: Headline 5 / Button 3 (14px / 22px / 600)
- Padding: `14px 12px`
- Icon size: 16px

**CSS spec:**
```css
.btn-hollow {
  background: transparent;
  color: #000;
  border: 2px solid #000;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  font-family: 'Noto Sans', sans-serif;
  font-weight: 600;
  cursor: pointer;
}
.btn-hollow.big    { font-size: 20px; line-height: 30px; padding: 14px 16px; }
.btn-hollow.medium { font-size: 16px; line-height: 24px; padding: 14px 12px; }
.btn-hollow.small  { font-size: 14px; line-height: 22px; padding: 14px 12px; }
```

---

## 4. Button — Disabled

**Figma node:** `226:2117`

Used when an action is not yet available. No icon shown.

- Background: `rgba(0, 0, 0, 0.25)` (Tertiary)
- Text color: `rgba(0, 0, 0, 0.5)` (Secondary)
- Font: Headline 2 (20px / 30px / 600)
- Border-radius: 12px
- Padding: `14px 16px`
- No pointer interaction (`cursor: not-allowed`)

```css
.btn-disabled {
  background: rgba(0, 0, 0, 0.25);
  color: rgba(0, 0, 0, 0.5);
  border-radius: 12px;
  padding: 14px 16px;
  font-size: 20px;
  font-weight: 600;
  line-height: 30px;
  font-family: 'Noto Sans', sans-serif;
  pointer-events: none;
  cursor: not-allowed;
  text-align: center;
}
```

---

## 5. Button — Icon Only

Square icon-only buttons at 40×40px. Support solid and hollow variants.

### Button Icon Only Solid
**Figma node:** `226:2021`
- Background: `#000`
- Padding: 8px
- Border-radius: 12px
- Icon: 24px, white

### Button Icon Only Hollow
**Figma node:** `226:2105`
- Background: `transparent`
- Border: `2px solid #000`
- Padding: 8px
- Border-radius: 12px
- Icon: 24px, black

```css
.btn-icon {
  width: 40px;
  height: 40px;
  border-radius: 12px;
  padding: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.btn-icon.solid  { background: #000; }
.btn-icon.hollow { background: transparent; border: 2px solid #000; }
```

---

## 6. Pause Popup

**Figma node:** `226:2230`

A modal card that appears when a game is paused mid-session.

**Structure:**
- Container: `background: #fff`, `border-radius: 20px`, `padding: 40px 24px`, `box-shadow: 0 20px 60px rgba(0,0,0,0.3)`, `width: 320px`
- Timer illustration: 48×48px (use `Timer.svg` from illustrations library)
- Headline: Headline 1 (24px / 36px / 600), centered, black
- Sub-text: Body 1 (18px / 28px / 400), centered, black
- CTA button: Button Big Solid, width 240px

```css
.pause-popup {
  background: #fff;
  border-radius: 20px;
  padding: 40px 24px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  width: 320px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 36px;
}
.pause-popup__content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  width: 100%;
}
.pause-popup__text {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  text-align: center;
}
.pause-popup__title {
  font-size: 24px;
  font-weight: 600;
  line-height: 36px;
  font-family: 'Noto Sans', sans-serif;
  color: #000;
}
.pause-popup__subtitle {
  font-size: 18px;
  font-weight: 400;
  line-height: 28px;
  font-family: 'Noto Sans', sans-serif;
  color: #000;
}
```

---

## 7. Streak Counter

**Figma node:** `226:2146`

A weekly streak card showing which days the user has played. Contains 7 Streak Days sub-components (Mon–Sun).

**Structure:**
- Container: `background: #fff`, `border-radius: 12px`, `padding: 12px`, `width: 320px`
- Header row: "Weekly Streak" label (Headline 3 / 18px / 600) + Fire icon (24px, right-aligned)
- Days row: 7× Streak Days, spaced with `justify-content: space-between`

```css
.streak-counter {
  background: #fff;
  border-radius: 12px;
  padding: 12px;
  width: 320px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.streak-header {
  display: flex;
  align-items: center;
  gap: 8px;
  width: 100%;
}
.streak-title {
  font-size: 18px;
  font-weight: 600;
  line-height: 26px;
  font-family: 'Noto Sans', sans-serif;
  color: #000;
  flex: 1;
}
.streak-days-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
```

---

## 8. Streak Days (sub-component)

**Figma node:** `226:2203`

Each day in the streak counter is a 32×32px column with an icon and a day label. Comes in 4 states:

| State       | Icon                         | Label color                |
|-------------|------------------------------|----------------------------|
| Completed   | Selection Right Tick Solid (green) | `#000`                |
| Missed      | Close Circle Solid (red)     | `#000`                     |
| Today       | Selection Right Tick Solid + dashed ring highlight | `#FF554B` (Error) |
| Upcoming    | Selection Unselected (empty circle, grey) | `rgba(0,0,0,0.5)` |

```css
.streak-day {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 32px;
}
.streak-day__icon { width: 24px; height: 24px; position: relative; }
.streak-day__label {
  font-size: 12px;
  font-weight: 600;
  line-height: 18px;
  font-family: 'Noto Sans', sans-serif;
  text-align: center;
  width: 32px;
}
.streak-day--completed .streak-day__label { color: #000; }
.streak-day--missed    .streak-day__label { color: #000; }
.streak-day--today     .streak-day__label { color: #FF554B; }
.streak-day--upcoming  .streak-day__label { color: rgba(0,0,0,0.5); }
/* Today state has an animated dashed ring around the icon */
.streak-day--today .streak-day__icon::before {
  content: '';
  position: absolute;
  inset: -12px;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  border: 2px dashed #FF554B;
}
```

---

## 9. Bottom Options Pill

**Figma node:** `226:2307`

A circular pill button with an icon and a label below it. Used in game UIs for quick actions (e.g. Reset, Hint).

**Structure:**
- Pill button: `background: rgba(0,0,0,0.5)`, `border-radius: 60px`, `width: 60px`, `height: 60px`, `padding: 14px`
- Icon: 24×24px, white
- Label: Headline 5 / Button 3 (14px / 22px / 600), centered, black, below the pill

```css
.bottom-pill {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  width: 60px;
}
.bottom-pill__btn {
  background: rgba(0, 0, 0, 0.5);
  border-radius: 60px;
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 14px;
  cursor: pointer;
}
.bottom-pill__label {
  font-size: 14px;
  font-weight: 600;
  line-height: 22px;
  font-family: 'Noto Sans', sans-serif;
  color: #000;
  text-align: center;
  width: 100%;
}
```

---

## Quick Reference Summary

| Component               | Node ID    | Background         | Border-radius | Key Font Style   |
|-------------------------|------------|--------------------|---------------|------------------|
| Nav Bar                 | 226:1882   | `#FAE3B2`          | —             | H3 + H4          |
| Button Big Solid        | 226:1953   | `#000`             | 12px          | H2 (20px/600)    |
| Button Medium Solid     | 226:1973   | `#000`             | 12px          | H4 (16px/600)    |
| Button Small Solid      | 226:1997   | `#000`             | 12px          | H5 (14px/600)    |
| Button Big Hollow       | 226:2033   | transparent        | 12px + 2px border | H2 (20px/600)|
| Button Medium Hollow    | 226:2057   | transparent        | 12px + 2px border | H4 (16px/600)|
| Button Small Hollow     | 226:2081   | transparent        | 12px + 2px border | H5 (14px/600)|
| Button Disabled         | 226:2117   | `rgba(0,0,0,0.25)` | 12px          | H2 (20px/600)    |
| Button Icon Only Solid  | 226:2021   | `#000`             | 12px          | —                |
| Button Icon Only Hollow | 226:2105   | transparent        | 12px + 2px border | —            |
| Pause Popup             | 226:2230   | `#fff`             | 20px          | H1 + Body 1      |
| Streak Counter          | 226:2146   | `#fff`             | 12px          | H3 (18px/600)    |
| Streak Days             | 226:2203   | —                  | —             | Label (12px/600) |
| Bottom Options Pill     | 226:2307   | `rgba(0,0,0,0.5)`  | 60px          | H5 (14px/600)    |

---

## DLS Token Mapping (for implementation reference)

When building any component, always resolve values to their DLS source token:

| Visual property | DLS source |
|---|---|
| `#000000` | Base Colors / Primary |
| `#FFFFFF` | Base Colors / Default White |
| `rgba(0,0,0,0.5)` | Base Colors / Secondary |
| `rgba(0,0,0,0.25)` | Base Colors / Tertiary |
| `rgba(0,0,0,0.1)` | Base Colors / Border |
| `rgba(0,0,0,0.16)` | Base Colors / Border Dark |
| `#FF554B` | Base Colors / Error |
| `#3E9E3E` | Base Colors / Success |
| `#FAE3B2` | Theme / Theme 7 (Nav Bar bg) |
| `font-size: 20px / 600` | Headline 2 |
| `font-size: 18px / 600` | Headline 3 / Button 1 |
| `font-size: 16px / 600` | Headline 4 / Button 2 |
| `font-size: 14px / 600` | Headline 5 / Button 3 |
| `font-size: 12px / 600` | Label |
| `font-size: 18px / 400` | Body 1 |
| `font-size: 16px / 400` | Body 2 |
| `0 20px 60px rgba(0,0,0,0.3)` | Big Drop Shadow (Pause Popup) |

---

*Last updated: Batch 1 — 14 UI components (Buttons, Nav Bar, Popup, Streak, Pills)*
