# DLS — Typography System

> Apply this typography system everywhere unless explicitly overridden.

---

## Font Family

```
Noto Sans, sans-serif
```

---

## Font Weights

| Name     | Value |
|----------|-------|
| Bold     | 700   |
| SemiBold | 600   |
| Regular  | 400   |

---

## Typography Scale

| Style                   | Font Size | Line Height | Font Weight    |
|-------------------------|-----------|-------------|----------------|
| Display 1               | 32px      | 42px        | 700 (Bold)     |
| Display 2               | 28px      | 40px        | 700 (Bold)     |
| Headline 1              | 24px      | 36px        | 600 (SemiBold) |
| Headline 2              | 20px      | 30px        | 600 (SemiBold) |
| Headline 3 / Button 1   | 18px      | 26px        | 600 (SemiBold) |
| Headline 4 / Button 2   | 16px      | 24px        | 600 (SemiBold) |
| Headline 5 / Button 3   | 14px      | 22px        | 600 (SemiBold) |
| Body 1                  | 18px      | 28px        | 400 (Regular)  |
| Body 2                  | 16px      | 26px        | 400 (Regular)  |
| Body 3                  | 14px      | 22px        | 400 (Regular)  |
| Label                   | 12px      | 18px        | 600 (SemiBold) |

---

## CSS Reference

```css
/* Font Import */
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;600;700&display=swap');

/* Base */
body {
  font-family: 'Noto Sans', sans-serif;
}

/* Display */
.display-1 { font-size: 32px; line-height: 42px; font-weight: 700; }
.display-2 { font-size: 28px; line-height: 40px; font-weight: 700; }

/* Headlines */
.headline-1 { font-size: 24px; line-height: 36px; font-weight: 600; }
.headline-2 { font-size: 20px; line-height: 30px; font-weight: 600; }
.headline-3, .button-1 { font-size: 18px; line-height: 26px; font-weight: 600; }
.headline-4, .button-2 { font-size: 16px; line-height: 24px; font-weight: 600; }
.headline-5, .button-3 { font-size: 14px; line-height: 22px; font-weight: 600; }

/* Body */
.body-1 { font-size: 18px; line-height: 28px; font-weight: 400; }
.body-2 { font-size: 16px; line-height: 26px; font-weight: 400; }
.body-3 { font-size: 14px; line-height: 22px; font-weight: 400; }

/* Label */
.label  { font-size: 12px; line-height: 18px; font-weight: 600; }
```
