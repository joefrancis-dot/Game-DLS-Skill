# DLS — Color System

> Apply these color tokens everywhere unless explicitly overridden.

---

## Base Colors

| Token        | Value                    | Hex / RGBA                  | Usage                                              |
|--------------|--------------------------|-----------------------------|---------------------------------------------------|
| Primary      | `#000000`                | `#000000`                   | Main text, strongest emphasis, primary foreground |
| Secondary    | Black @ 50% opacity      | `rgba(0, 0, 0, 0.5)`        | Secondary text, medium emphasis                   |
| Tertiary     | Black @ 25% opacity      | `rgba(0, 0, 0, 0.25)`       | Low-emphasis text, subtle UI elements             |
| Border       | Black @ 10% opacity      | `rgba(0, 0, 0, 0.1)`        | Light borders, dividers, subtle strokes           |
| Border Dark  | Black @ 16% opacity      | `rgba(0, 0, 0, 0.16)`       | Stronger borders, separators, input outlines      |
| Default White| `#FFFFFF`                | `#FFFFFF`                   | White surfaces, cards, backgrounds, inverse text  |
| Error        | `#FF554B`                | `#FF554B`                   | Error states, destructive actions, validation     |
| Success      | `#3E9E3E`                | `#3E9E3E`                   | Success states, confirmations, positive indicators|

---

## Theme Colors

| Token    | Hex       | Swatch |
|----------|-----------|--------|
| Theme 1  | `#FFDB19` | 🟡     |
| Theme 2  | `#81D7FF` | 🔵     |
| Theme 3  | `#D4A8FF` | 🟣     |
| Theme 4  | `#BEE95F` | 🟢     |
| Theme 5  | `#FFAA89` | 🟠     |
| Theme 6  | `#D6ECA3` | 🍃     |
| Theme 7  | `#FAE3B2` | 🌾     |
| Theme 8  | `#DDA6D2` | 🌸     |
| Theme 9  | `#FEAAAA` | 🌷     |
| Theme 10 | `#C7E2DE` | 🩵     |

---

## CSS Custom Properties

```css
:root {
  /* Base Colors */
  --color-primary:      #000000;
  --color-secondary:    rgba(0, 0, 0, 0.5);
  --color-tertiary:     rgba(0, 0, 0, 0.25);
  --color-border:       rgba(0, 0, 0, 0.1);
  --color-border-dark:  rgba(0, 0, 0, 0.16);
  --color-white:        #FFFFFF;
  --color-error:        #FF554B;
  --color-success:      #3E9E3E;

  /* Theme Colors */
  --color-theme-1:  #FFDB19;
  --color-theme-2:  #81D7FF;
  --color-theme-3:  #D4A8FF;
  --color-theme-4:  #BEE95F;
  --color-theme-5:  #FFAA89;
  --color-theme-6:  #D6ECA3;
  --color-theme-7:  #FAE3B2;
  --color-theme-8:  #DDA6D2;
  --color-theme-9:  #FEAAAA;
  --color-theme-10: #C7E2DE;
}
```

---

## JSON Token Reference

```json
{
  "colors": {
    "primary": "#000000",
    "secondary": "rgba(0, 0, 0, 0.5)",
    "tertiary": "rgba(0, 0, 0, 0.25)",
    "border": "rgba(0, 0, 0, 0.1)",
    "borderDark": "rgba(0, 0, 0, 0.16)",
    "white": "#FFFFFF",
    "error": "#FF554B",
    "success": "#3E9E3E",
    "theme1": "#FFDB19",
    "theme2": "#81D7FF",
    "theme3": "#D4A8FF",
    "theme4": "#BEE95F",
    "theme5": "#FFAA89",
    "theme6": "#D6ECA3",
    "theme7": "#FAE3B2",
    "theme8": "#DDA6D2",
    "theme9": "#FEAAAA",
    "theme10": "#C7E2DE"
  }
}
```
