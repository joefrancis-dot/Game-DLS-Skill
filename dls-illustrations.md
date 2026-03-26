# DLS — Illustrations Library

> Illustrations are multi-color, context-rich visuals used to communicate states, emotions, and game mechanics. They are distinct from icons — use illustrations for empty states, feedback screens, feature highlights, and onboarding moments.
> Always use the exact SVG file as provided. Do not recolor or resize illustrations without explicit approval.

---

## Illustration Specs

| Property    | Value                        |
|-------------|------------------------------|
| Format      | SVG                          |
| Default Size| 96 × 96 px (most); exceptions noted |
| Usage       | Contextual / decorative screens |
| Style       | Flat + gradient, multi-color |

---

## Batch 1 — Game & Quiz UI Illustrations

| Illustration      | File                   | Size       | Primary Colors                        | Usage Context                                               |
|-------------------|------------------------|------------|---------------------------------------|-------------------------------------------------------------|
| Gift Received     | `Gift_Received.svg`    | 240 × 164  | `#31B0D8` `#FF6D2F` `#FFB927`         | Reward / prize received success state                       |
| Cup               | `Cup.svg`              | 96 × 96    | `#FEC417` `#FFA828` `#D1701C`         | Trophy / tournament win, top ranking                        |
| Player            | `Player.svg`           | 96 × 96    | `#2F73E0` `#2C3E50` `#582A1A`         | Individual player profile / avatar placeholder              |
| Match             | `Match.svg`            | 96 × 96    | `#2B77C4` `#E67E22` `#F1C40F`         | Match / game in progress, fixture card                      |
| Team              | `Team.svg`             | 96 × 96    | `#276AD6` `#21B55C` `#2ECC71`         | Team selection / squad view                                 |
| Leaderboard       | `Leaderboard.svg`      | 96 × 96    | `#FF9811` `#FF5023` `#427EEC`         | Rankings / leaderboard screen                               |
| All Correct       | `All_correct.svg`      | 96 × 96    | `#5DB72C`                             | Perfect score / all answers correct success state           |
| Your Rank         | `Your_Rank.svg`        | 96 × 96    | `#FBAE24` `#FA6F4A` `#FFD540`         | Personal rank reveal / position display                     |
| Timer             | `Timer-1.svg`          | 96 × 96    | `#3AC9F7` `#CDF0FF` `#8C9EAA`         | Countdown / time-limited quiz state                         |
| No Back Allowed   | `No_back_allowed.svg`  | 96 × 96    | `#F4343D` `#FFE2E4` `#444444`         | Warning — cannot go back once started                       |
| Lucky Draw        | `Luckydraw.svg`        | 96 × 96    | `#FDCC1A` `#307EEE` `#EE5656`         | Lucky draw / spin wheel / random prize feature              |
| Prediction        | `Prediction.svg`       | 96 × 96    | `#8E3AEE` `#711ED0` `#CA6134`         | Prediction game / forecasting feature                       |
| Fire              | `Fire.svg`             | 96 × 96    | Radial gradient (orange → red)        | Hot streak / trending / on fire state                       |
| Target            | `Target.svg`           | 96 × 96    | `#FF2A23` `#1F87FD` `#006CA9`         | Goal / target / aim feature                                 |
| Play Quiz         | `Play_Quiz.svg`        | 96 × 96    | Linear gradient (blue → purple)       | Start quiz / play now CTA illustration                      |
| Countdown         | `Countdown.svg`        | 96 × 96    | `#F5BF00` `#E6705E` `#EFEFED`         | Countdown timer / hourglass / waiting state                 |
| Are You Sure?     | `Are_you_sure.svg`     | 96 × 96    | `#8750FC` `#5017C9` `#39A935`         | Confirmation dialog / double-check state                    |
| Oho! You Lose     | `Oho__You_lose.svg`    | 96 × 96    | `#A26CCC` `#603813` `#EBEBEB`         | Loss / game over / incorrect answer state                   |
| Won               | `Won.svg`              | 96 × 96    | `#FF9D00` `#FBAE24` `#FA6F4A`         | Win / victory / correct answer celebration state            |

---

## Usage Guidelines

### When to use illustrations
- **Feedback screens** — Won, Oho! You Lose, All Correct, Are You Sure?
- **Feature entry points** — Play Quiz, Lucky Draw, Prediction, Target
- **Game context** — Match, Team, Player, Cup, Leaderboard, Your Rank
- **State indicators** — Timer, Countdown, No Back Allowed, Fire

### When NOT to use illustrations
- Do not use illustrations as inline icons — use the icon library instead
- Do not place two illustrations side by side without sufficient spacing (min 24px gap)
- Do not stretch or distort; always maintain original aspect ratio

### Sizing
- Most illustrations are designed at **96 × 96 px**. Display at 1× or 2× (192 × 192 px) for retina
- `Gift_Received.svg` is a **banner/wide format** illustration (240 × 164 px) — use for header or reward banners only
- Scale uniformly if resizing; never scale width and height independently

### Theming
- Illustrations use their own fixed color palette — they do **not** inherit DLS color tokens
- Do not apply CSS `filter` or color overrides unless explicitly approved

---

## File Inventory

```
dls/illustrations/
├── Batch 1 — Game & Quiz UI
│   ├── Gift_Received.svg       240×164
│   ├── Cup.svg                 96×96
│   ├── Player.svg              96×96
│   ├── Match.svg               96×96
│   ├── Team.svg                96×96
│   ├── Leaderboard.svg         96×96
│   ├── All_correct.svg         96×96
│   ├── Your_Rank.svg           96×96
│   ├── Timer-1.svg             96×96
│   ├── No_back_allowed.svg     96×96
│   ├── Luckydraw.svg           96×96
│   ├── Prediction.svg          96×96
│   ├── Fire.svg                96×96
│   ├── Target.svg              96×96
│   ├── Play_Quiz.svg           96×96
│   ├── Countdown.svg           96×96
│   ├── Are_you_sure.svg        96×96
│   ├── Oho__You_lose.svg       96×96
│   └── Won.svg                 96×96
```

---

---

## Batch 2 — Feedback, Reward & State Illustrations (Final)

| Illustration   | File                | Size    | Primary Colors                              | Usage Context                                          |
|----------------|---------------------|---------|---------------------------------------------|--------------------------------------------------------|
| Time's Up 2    | `Time_s_Up_2.svg`   | 96 × 96 | `#A533FF` `#5A1882` `#172B4D`               | Time expired — dark/dramatic variant                   |
| Time's Up 1    | `Time_s_Up_1.svg`   | 96 × 96 | `#9455FF` `#7041C2` `#242424`               | Time expired — primary variant                         |
| Submitted 2    | `Submitted_2.svg`   | 96 × 96 | `#8E3AEE` `#1F9C42` `#FFC639`              | Answer/form submitted — purple accent variant          |
| Submitted 1    | `Submitted_1.svg`   | 96 × 96 | `#C83E80` `#D56B4B` `#FFCB0A`              | Answer/form submitted — warm/pink accent variant       |
| Gift           | `Gift.svg`          | 96 × 96 | Linear gradient `#F54959` → `#D00A4B`       | Gift / reward / prize unwrap moment                    |
| Confetti       | `Confetti.svg`      | 96 × 96 | `#AA25E8` `#24A7FF` `#27F253` `#F9C32B`    | Celebration / win / achievement burst                  |
| Brain Score    | `Brain_Score.svg`   | 96 × 96 | `#DA2E75` `#F4B400` `#FDD835`              | Intelligence score / quiz result / brain challenge     |
| Timer          | `Timer.svg`         | 96 × 96 | `#3AC9F7` `#E56353` `#8C9EAA`              | Stopwatch / timed question / countdown in-game         |
| Hint           | `Hint.svg`          | 96 × 96 | `#FFDC13` `#FFE45F`                         | Hint / lifeline / help prompt                          |

---

## Usage Guidelines (Updated)

### Variant pairs
Some illustrations come in two variants for different visual contexts. Use consistently within the same screen:
- **Time's Up 1** — primary usage (lighter purple tones)
- **Time's Up 2** — dramatic / high-stakes variant (deeper violet + dark background)
- **Submitted 1** — warm pink/orange tone (casual or social contexts)
- **Submitted 2** — purple/green tone (achievement or confirmation contexts)

### Gradient illustrations
`Gift.svg` is entirely gradient-based (linear `#F54959` → `#D00A4B`). Do not attempt to flatten or recolor.

---

## Complete File Inventory

```
dls/illustrations/
├── Batch 1 — Game & Quiz UI
│   ├── Gift_Received.svg       240×164
│   ├── Cup.svg                 96×96
│   ├── Player.svg              96×96
│   ├── Match.svg               96×96
│   ├── Team.svg                96×96
│   ├── Leaderboard.svg         96×96
│   ├── All_correct.svg         96×96
│   ├── Your_Rank.svg           96×96
│   ├── Timer-1.svg             96×96
│   ├── No_back_allowed.svg     96×96
│   ├── Luckydraw.svg           96×96
│   ├── Prediction.svg          96×96
│   ├── Fire.svg                96×96
│   ├── Target.svg              96×96
│   ├── Play_Quiz.svg           96×96
│   ├── Countdown.svg           96×96
│   ├── Are_you_sure.svg        96×96
│   ├── Oho__You_lose.svg       96×96
│   └── Won.svg                 96×96
│
└── Batch 2 — Feedback, Reward & State (Final)
    ├── Time_s_Up_1.svg         96×96
    ├── Time_s_Up_2.svg         96×96
    ├── Submitted_1.svg         96×96
    ├── Submitted_2.svg         96×96
    ├── Gift.svg                96×96
    ├── Confetti.svg            96×96
    ├── Brain_Score.svg         96×96
    ├── Timer.svg               96×96
    └── Hint.svg                96×96
```

---

*Last updated: Batch 2 added — 28 illustrations total. Illustration library COMPLETE.*
*Batches: Game & Quiz UI (19) · Feedback, Reward & State (9)*
