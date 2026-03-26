# DLS — Logo Library

> This file documents all brand logos and game logos used across the product. Always use the exact SVG files as provided. Never alter, recolor, stretch, or recreate logos from scratch.

---

## Logo Categories

1. **Publication Logos** — Square and header variants for each masthead brand
2. **Platform Logo** — DB Games (the games platform brand)
3. **Game Logos** — Individual game identities

---

## 1. Publication Logos

These logos represent the four masthead brands. Each brand has two format variants: a **Square Logo** (used for app icons, thumbnails, tiles) and a **Header Logo** (used in navigation bars and headers).

### Brand Color
All publication logos share the same brand orange: **`#F89C1B`**
- Exception: **Bhaskar English** uses `#F89C1B` + `#2B2B2B` (dark wordmark)

---

### Square Logos — 120 × 120 px

| Brand             | File                              | Colors                   | Usage                                      |
|-------------------|-----------------------------------|--------------------------|--------------------------------------------|
| Dainik Bhaskar    | `Square_Logo-Dainik_Bhaskar.svg`  | `#F89C1B`                | App icon, tile, avatar, card header        |
| Divya Bhaskar     | `Square_Logo-Divya_Bhaskar.svg`   | `#F89C1B`                | App icon, tile, avatar, card header        |
| Divya Marathi     | `Square_Logo-Divya_Marathi.svg`   | `#F89C1B`                | App icon, tile, avatar, card header        |
| Bhaskar English   | `Square_Logo-Bhaskar_English.svg` | `#F89C1B` `#2B2B2B`      | App icon, tile, avatar, card header        |

### Header Logos — 32 px height, variable width

| Brand             | File                               | Size      | Colors      | Usage                                       |
|-------------------|------------------------------------|-----------|-------------|---------------------------------------------|
| Dainik Bhaskar    | `Header_Logo-Dainik_Bhaskar.svg`   | 92 × 32   | `#F89C1B`   | Top navigation bar, page header             |
| Divya Bhaskar     | `Header_Logo-Divya_Bhaskar.svg`    | 92 × 32   | `#F89C1B`   | Top navigation bar, page header             |
| Divya Marathi     | `Header_Logo-Divya_Marathi.svg`    | 78 × 32   | `#F89C1B`   | Top navigation bar, page header             |
| Bhaskar English   | `Header_Logo-Bhaskar_English.svg`  | 96 × 32   | `#F89C1B`   | Top navigation bar, page header             |

> **Header logo height is fixed at 32 px.** Width varies per brand — do not force equal widths across brands.

---

## 2. Platform Logo

| Logo      | File           | Size       | Colors                                    | Usage                                   |
|-----------|----------------|------------|-------------------------------------------|-----------------------------------------|
| DB Games  | `DB_Games.svg` | 120 × 120  | Gradient `#FF5918` → `#F89C1D` → `#FF7518` | Games platform brand mark, home screen, loading screens |

> `DB_Games.svg` uses a linear gradient for its background. Do not replace with a flat color.

---

## 3. Game Logos

Each game has its own identity logo at 120 × 120 px.

| Game                 | File                      | Size        | Brand Colors              | Notes                                          |
|----------------------|---------------------------|-------------|---------------------------|------------------------------------------------|
| Switch               | `Switch.svg`              | 120 × 120   | `#BEE95F` `#ADDA48`       | Aligns with DLS Theme 4 (`#BEE95F`)           |
| Number Link          | `Number_Link.svg`         | 120 × 120   | `#03CB53` `#FFA37F`       | Green + peach/salmon palette                   |
| Quiz Master          | `Quiz_Master.svg`         | 120 × 120   | `#B731FF` `#710EA6`       | Purple brand                                   |
| Word Mala            | `Word_Mala.svg`           | 120 × 120   | Pattern fill (raster)     | Uses embedded image pattern — do not scale above 120 px |
| Find the Difference  | `Find_the_Difference.svg` | 121 × 120   | `#C981FF`                 | Purple; close to DLS Theme 3 (`#D4A8FF`)      |
| Word Khoj            | `Word_Khoj.svg`           | 120 × 120   | `#81D7FF`                 | Aligns with DLS Theme 2 (`#81D7FF`)           |

---

## Usage Guidelines

### DO
- Use **Square Logos** for tiles, cards, app icons, and avatar slots
- Use **Header Logos** in top navbars — always at 32 px height
- Use **DB Games** logo on the platform home screen, splash screen, and loading states
- Use **Game Logos** on game cards, lobby screens, and game-specific headers
- Always use SVG source files — they are resolution-independent

### DO NOT
- Do not recolor any logo — all colors are brand-mandated
- Do not stretch logos disproportionately — always preserve aspect ratio
- Do not mix Square and Header logo formats in the same context
- Do not recreate or approximate logos using DLS color tokens — use the files directly
- Do not apply drop shadows, glows, or filters on top of logos unless explicitly approved
- Do not scale `Word_Mala.svg` beyond its native size — it uses an embedded raster pattern

### Clearspace
Maintain a minimum clearspace equal to **the height of the logo × 0.25** on all four sides. For the 32 px header logos, that means at least 8 px of breathing room around the logo.

---

## File Inventory

```
dls/logos/
│
├── Publication — Square (120×120)
│   ├── Square_Logo-Dainik_Bhaskar.svg
│   ├── Square_Logo-Divya_Bhaskar.svg
│   ├── Square_Logo-Divya_Marathi.svg
│   └── Square_Logo-Bhaskar_English.svg
│
├── Publication — Header (32px height)
│   ├── Header_Logo-Dainik_Bhaskar.svg    92×32
│   ├── Header_Logo-Divya_Bhaskar.svg     92×32
│   ├── Header_Logo-Divya_Marathi.svg     78×32
│   └── Header_Logo-Bhaskar_English.svg   96×32
│
├── Platform
│   └── DB_Games.svg                      120×120
│
└── Game Logos (120×120)
    ├── Switch.svg
    ├── Number_Link.svg
    ├── Quiz_Master.svg
    ├── Word_Mala.svg
    ├── Find_the_Difference.svg
    └── Word_Khoj.svg
```

---

*Last updated: Batch 1 — 15 logos (4 square publication + 4 header publication + 1 platform + 6 game logos)*
