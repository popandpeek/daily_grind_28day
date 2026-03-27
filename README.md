# Daily Grind — 28-Day Progressive Workout Program

A self-contained, single-file workout app. No dependencies, no build step, no accounts. Open the HTML file and go — or use the live hosted version.

**Live:** [dailygrind-28-day.netlify.app](https://dailygrind-28-day.netlify.app)

---

## What It Is

A browser-based workout tracker for a full-body 28-day progressive training program. Built for intermediate athletes returning from a detraining period. Uses an adjustable kettlebell, rotating push-up handles, and bodyweight — nothing else.

**Structure:**
- 28 days across 4 weeks
- 20 workout days, 8 rest days (baked in)
- ~15–20 minutes per session
- Balanced upper body, lower body, and core each day

**Progression:**
| Week | Intensity | Sets | Rest |
|------|-----------|------|------|
| 1 | Foundation — easy, form focus | 2–3 | 40–50s |
| 2 | Building — moderate, ramp begins | 3 | 35–40s |
| 3 | Hard Ramp — heavier, shorter rest | 3–4 | 20–30s |
| 4 | Peak — max intensity | 4–5 | 15–25s |

---

## Features

- **Per-day difficulty selector** — Easy / Moderate / Hard / Peak on every workout card
- **Apply to week** — set difficulty for all days in a week with one tap
- **Week tabs** — jump between weeks instantly
- **Day picker** — see and navigate all 7 days of the current week at a glance
- **Exercise instructions** — tap any exercise name for step-by-step form cues, muscle targets, a coach tip, and a YouTube link
- **Checkboxes** — mark exercises done as you go
- **Progress bar** — tracks completion percentage for the current day
- **Reset button** — clear a day's checkboxes (prominent red button at the bottom of each card)
- **Persistent state** — progress saves to `localStorage` (survives page refresh, same browser)
- **Rest day cards** — rest days are clearly marked
- **Zero dependencies** — one HTML file, no npm, no framework, no internet required after font load

---

## Equipment Required

- Adjustable kettlebell
- Rotating push-up handles
- Bodyweight (chair for dips, step-ups, and foot elevation)

---

## Difficulty Levels

Each of the 20 workout days has 4 independently programmed difficulty levels. Switching difficulty swaps the entire workout — exercises, sets, reps, and rest periods — without affecting progress on other days.

| Level | Sets | Rest | Notes |
|-------|------|------|-------|
| Easy | 2–3 | 45–50s | Reduced volume, beginner-friendly moves |
| Moderate | 3 | 35–40s | Default — balanced intermediate load |
| Hard | 3–4 | 20–25s | Heavier KB, more reps, shorter rest |
| Peak | 4–5 | 15–20s | Max volume, hardest exercise variants |

Progress is tracked per difficulty level — switching levels gives you a clean slate for that day without losing other days' progress.

---

## Usage

### Local
```bash
open index.html
```
No server required. Works in any modern browser.

### Hosted (Netlify)
The repo is connected to Netlify via GitHub. Every push to `main` auto-deploys within ~30 seconds.

### Embed in Notion
1. Deploy to Netlify (above)
2. In any Notion page, type `/embed`
3. Paste the Netlify URL

> **Note:** Notion sandboxes iframes and blocks inline `onclick` handlers. This app uses event delegation exclusively for Notion compatibility.

### iPhone Home Screen (recommended)
1. Open the URL in Safari
2. Tap the Share icon → **Add to Home Screen**
3. Sits on your home screen like a native app, opens full screen

---

## Deployment

This repo is connected to Netlify for continuous deployment. Pushing to `main` triggers an automatic redeploy.

If the live site doesn't reflect recent changes after a deploy, force a cache clear:

1. Go to [app.netlify.com](https://app.netlify.com) → your site → **Deploys**
2. Click the most recent deploy
3. Click **"Clear cache and retry deploy"**

---

## File Structure

```
index.html    # Entire app — HTML, CSS, JS, and program data in one file
README.md
```

Everything is in one file by design. No build artifacts, no asset folders, no dependencies.

---

## Modifying the Program

Workout data lives in the `P` array inside the `<script>` block. Each entry is either a workout day or a rest day:

```js
// Workout day
{
  w: 1,                          // week number (1–4)
  t: "First Steps",             // workout title
  eq: ["Bodyweight", "Push-up handles"],  // equipment tags
  easy: { rs:"50s rest", up:[...], lo:[...], co:[...] },
  mod:  { rs:"40s rest", up:[...], lo:[...], co:[...] },
  hard: { rs:"30s rest", up:[...], lo:[...], co:[...] },
  peak: { rs:"20s rest", up:[...], lo:[...], co:[...] }
}

// Rest day
{ w: 1, rest: true }

// Exercise entry
{ n: "Push-Up", r: "3×12", s: "handles, full range" }
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

Works in all modern browsers (Chrome, Safari, Firefox, Edge). Requires JavaScript enabled.

`localStorage` is used for state persistence — progress is per-browser and per-origin and will not sync across devices.

---

## License

MIT
