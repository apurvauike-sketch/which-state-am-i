# Which State Am I?

## Challenge
Mini Challenge 2 — PromptWars Virtual (Hack2Skill × Google for Developers)

## Live Demo
[apurvauike-sketch.github.io/which-state-am-i/](https://apurvauike-sketch.github.io/which-state-am-i/)

---

## Approach

An AI-generated image built entirely from **visual cultural markers** — tribal
wall art, rock-cut cave architecture, regional cuisine on a banana leaf, and a
silk saree with a temple-border weave — without ever naming the state. Viewers
must identify the state from these cues alone.

---

## How It Works

| File | Purpose |
|------|---------|
| `index.html` | Single-page challenge with guess form, feedback, and hint system |
| `state.png` | AI-generated image representing the state through visual culture |

### Features

- **Interactive guess form** — type a state name and receive instant feedback
- **Hint rotation** — wrong guesses reveal progressive hints
- **Attempt & correct-answer tracking** — counters update in real time
- **In-browser self-tests** — 14 unit tests run on load (check browser console)

---

## Accessibility

- Skip-navigation link for keyboard users
- `aria-live` region for screen-reader feedback
- Meaningful `alt` text describing every cultural cue in the image
- WCAG AA colour contrast throughout
- `prefers-reduced-motion` respected
- Minimum 44 × 44 px touch targets
- `forced-colors` / high-contrast mode supported

---

## Security

- Content Security Policy via `<meta>` header
- All user input sanitized before DOM insertion (no `innerHTML` usage)
- `referrer` policy set to `no-referrer`
- Input length capped at 64 characters

---

## Performance

- Fonts loaded non-render-blocking (`media="print"` swap technique)
- Hero image marked `fetchpriority="high"` and `decoding="async"`
- CSS custom properties for a single source of truth (no repeated values)
- DOM references cached; no repeated `querySelector` calls in hot paths
- `aspect-ratio` on image frame prevents cumulative layout shift (CLS)

---

## Testing

Open the deployed page and check the **browser console** — 14 self-tests run
automatically on load:

```
✓ PASS  sanitize() trims whitespace
✓ PASS  sanitize() lowercases input
✓ PASS  sanitize() strips non-alpha
✓ PASS  sanitize() handles empty string
✓ PASS  isCorrect() accepts "maharashtra"
✓ PASS  isCorrect() accepts "Maharashtra" (case)
✓ PASS  isCorrect() accepts "maha" (abbreviation)
✓ PASS  isCorrect() rejects "Kerala"
✓ PASS  isCorrect() rejects "Goa"
✓ PASS  isCorrect() rejects empty string
✓ PASS  nextHint() returns a string
✓ PASS  nextHint() advances index each call
✓ PASS  feedback element exists
✓ PASS  input element exists
─────────────────────────────
Results: 14 passed, 0 failed
```

---

## Code Quality

- Strict mode (`'use strict'`)
- IIFE module pattern — no global namespace pollution
- JSDoc comments on every function and type
- Semantic HTML5 (`<main>`, `<article>`, `<header>`, `<section>`, `<footer>`)
- Design tokens via CSS custom properties
- Single responsibility — each function does one thing
- `Object.freeze()` on constant arrays to prevent mutation

---

## Repository Constraints

- Two files: `index.html` + `state.png` — well under 10 MB
- Single `main` branch
- No build step required — open `index.html` in any browser
