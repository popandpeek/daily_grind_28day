# Daily Grind — 28-Day Progressive Workout Program

A self-contained, single-file workout app for a full-body 28-day progressive training program. No dependencies, no build step, no accounts. Just open the HTML file and go.

---

## What It Is

A browser-based workout tracker built for intermediate athletes returning from a detraining period. The program uses adjustable kettlebells, rotating push-up handles, and bodyweight — nothing else.

**Structure:**
- 28 days across 4 weeks
- 20 workout days, 8 rest days (baked in)
- ~15–20 minutes per session
- Balanced upper body, lower body, and core each day

**Progression:**
| Week | Intensity | Sets | Rest |
|------|-----------|------|------|
| 1 | Foundation — easy, form focus | 3 | 40–45s |
| 2 | Building — moderate, ramp begins | 3 | 35–40s |
| 3 | Hard Ramp — heavier, shorter rest | 3–4 | 30s |
| 4 | Peak — max intensity | 4 | 25–30s |

---

## Features

- **Week tabs** — jump between weeks
- **Day picker** — see and navigate the full week at a glance
- **Exercise instructions** — tap any exercise name for step-by-step form cues, muscle targets, a coach tip, and a YouTube link
- **Checkboxes** — mark exercises done as you go
- **Progress bar** — tracks completion of the current day
- **Persistent state** — progress saves to `localStorage` (survives page refresh, same browser)
- **Rest day cards** — rest days are clearly marked, no accidental workouts
- **Zero dependencies** — one HTML file, no npm, no framework, no internet required after initial font load

---

## Equipment Required

- Adjustable kettlebell
- Rotating push-up handles
- Bodyweight (chair for dips/step-ups/elevated feet)

---

## Usage

### Local
```bash
# Just open it
open daily-grind-28day.html
```
No server required. Works in any modern browser.

### Hosted (Netlify — recommended for Notion embed)
1. Go to [netlify.com/drop](https://app.netlify.com/drop)
2. Drag `daily-grind-28day.html` onto the deploy zone
3. Netlify gives you a public URL (e.g. `your-app.netlify.app`)

### Embed in Notion
1. Deploy to Netlify (above)
2. In any Notion page, type `/embed`
3. Paste your Netlify URL
4. Resize the embed block to fit

> **Note:** Notion sandboxes iframes and blocks inline `onclick` handlers. This app uses event delegation exclusively for full Notion compatibility.

---

## File Structure

```
daily-grind-28day.html   # Entire app — HTML, CSS, JS, and program data
README.md
```

Everything is in one file by design. No build artifacts, no asset folders.

---

## Modifying the Program

The workout data lives in the `P` array in the `<script>` block. Each entry is either a workout day or a rest day:

```js
// Workout day
{
  w: 1,               // week number (1–4)
  t: "First Steps",  // workout title
  eq: ["Bodyweight", "Push-up handles"],  // equipment tags
  rs: "45s between sets",                 // rest note
  up: [{ n: "Push-Up", r: "3×12", s: "handles, full range" }],  // upper exercises
  lo: [...],  // lower exercises
  co: [...]   // core exercises
}

// Rest day
{ w: 1, rest: true }
```

Exercise instructions live in the `EX` object. To add a new exercise:

```js
"My Exercise": {
  m: "Muscles targeted",
  s: ["Step 1", "Step 2", "Step 3"],
  t: "Coach tip goes here",
  yt: "https://www.youtube.com/results?search_query=my+exercise+form"
}
```

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires JavaScript enabled.

`localStorage` is used for state persistence. Progress is per-browser and per-origin — it will not sync across devices.

---

## License

MIT
