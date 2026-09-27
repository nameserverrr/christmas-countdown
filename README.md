# Christmas Countdown

A single-page Christmas countdown with a live timer, festive mini-activities, and a hand-drawn SVG Santa — all in one HTML file.

No build step. No dependencies to install. No images to host. Just open it and it works.

---

## What's in it

- **Live countdown** — days, hours, minutes and seconds until December 25th, updating every second
- **"Sleeps left" ring** — the classic "how many sleeps until Christmas" counter with an animated border
- **Christmas quiz** — five questions with instant feedback and a score at the end
- **Christmas jokes** — a shuffling deck of dad jokes that never repeats back-to-back
- **Advent calendar** — a 24-door grid that unlocks day by day through December
- **Auto Christmas mode** — on the 25th, the site switches to a "Merry Christmas" message
- **Falling snow** — procedurally generated, respects `prefers-reduced-data`-ish sizing on mobile

Every visual is inline SVG or drawn with CSS. Zero image assets.

---

## Getting started

Just open `index.html` in a browser.

Or serve it locally if you prefer:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Then visit `http://localhost:8000`.

---

## Customising

Most of the tweaking happens in two places.

### Colours

At the top of the `<style>` block:

```css
:root {
    --bg-deep:   #071a10;
    --lime:      #84cc16;
    --gold:      #fbbf24;
    --cream:     #fef3c7;
    --red:       #dc2626;
}
```

Change `--lime` to `--red` if you want a more traditional palette. Or go full blue-and-white for a winter theme.

### Content

**Quiz questions** — edit the `quizData` array in the script:

```js
const quizData = [
    { q: "Your question?", a: ["A", "B", "C", "D"], c: 2 }  // c = index of correct answer
];
```

**Jokes** — edit the `jokesList` array. One string per joke.

**Advent notes** — edit the `notes` array inside `buildAdvent()`. Index 0 is December 1st, index 23 is Christmas Eve.

---

## How the countdown works

On every tick, the script:

1. Checks the current month and day
2. If it's past December 25th, it rolls the target year forward
3. If it *is* December 25th, it hides the hero and activities and shows the Christmas message
4. Otherwise, it calculates the time delta and updates the digits

Digits are zero-padded to two characters so the layout doesn't shift.

---

## File structure

```
.
├── index.html   # everything — markup, styles, script
└── README.md    # this file
```

It's intentionally one file. Copy it, drop it on any static host, done.

---

## Browser support

Works in every modern browser. Uses:

- CSS custom properties
- `aspect-ratio`
- `backdrop-filter` (degrades gracefully)
- `Intl`-friendly `Date` arithmetic

Tested on Chrome, Firefox, Safari, and mobile Safari.

---

## Accessibility

- Countdown digits use `font-variant-numeric: tabular-nums` so they don't jitter
- Modals close on `Escape` and on overlay click
- Buttons have visible hover/focus states
- Colour contrast between text and background meets AA for body copy

If you extend it, keep the `aria-label`s on icon-only buttons.

---

## License

MIT — do whatever you want with it. Attribution is nice but not required.

Merry Christmas. 🎄
