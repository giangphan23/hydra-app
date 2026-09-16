---
title: Hydra — Water Intake Tracker
updated: 2026-09-16
---

# Hydra

A simple, mobile-first daily water tracker built as a Claude Artifact (no login, no backend — everything is saved in the browser's local storage on the device it's opened on).

**Live app:** https://claude.ai/code/artifact/66f6fa8d-ef32-4c87-aaa9-4ef6e679778c
**Source code:** [`index.html`](index.html) — the full standalone HTML file behind the live app, kept in sync with every publish.

## Purpose

Track daily water intake against a goal, logged in fixed servings, with minimal taps, and make the habit fun to keep up with (celebrations, streak badges, playful feedback) rather than just a plain counter. Built for one-handed use on iPhone.

## Defaults

- Daily goal: **4,000 ml**
- Serving size: **700 ml** (one tap = one bottle = one serving)
- Both are user-adjustable in-app via the Settings panel

## Core features

- **Log a drink** button — one tap adds one serving; plays a short synthesized "glug" sound and a haptic buzz on supported devices
- **Today's bottles** — two sub-rows (AM / PM) of bottle icons, together covering every serving needed to hit the goal; each bottle pops in with a bounce + a teal ripple flash as you log it, so progress reads at a glance. Bottles logged past the goal render gold instead of teal.
- **Undo last** — a compact icon button next to "Log a drink" that removes the most recent log; plays a soft descending tone + triple-pulse vibration
- **Stats row** — Today (ml logged, plus a playful comparison like "≈ 3 cans of soda" underneath — the comparison unit rotates daily), Remaining (ml to goal, or over by X), Streak (consecutive days goal was met, with a 🔥 3-day / ⭐ 7-day / 🏆 30-day badge once earned)
- **"Did you know?" popup** — appears centered on screen right after each log, showing one of 28 hydration facts (cycling in order) paired with a large, bounce-animated emoji icon. High-contrast presentation (dark blurred backdrop, accent-colored border, deep shadow) with a centered "Got it" button; auto-dismisses after 7 seconds or can be closed early by tapping the button, the backdrop, or Esc. See the facts list at the bottom of this doc.
- **Celebrations** — confetti (150-piece, physics-based outward burst + gravity fall + air-resistance wobble, ~3s) with a big rotating pop-in message (YAY!, CONGRATS!, WOO HOO!, etc. — 9 messages cycling) the moment the daily goal is reached, plus lighter toast messages at 25/50/75% progress; each fires once per day, paired with sound (chime/arpeggio) and a matching vibration pattern
- **Over-goal celebrations** — two zones above 100% of goal: a **bonus zone** (100%–200%) with three escalating tiers — 💦 Overflow!, 🌊 Making waves, 🐋 Whale mode — each with a rising-bubble effect (blue/teal palette, distinct from the falling multicolor goal confetti) and its own toast + sound; and a **wind-down zone** (200%+) that shows one calm, muted "You're all set" popup (no auto-dismiss — stays until manually closed) the first time it's crossed each day, then stays quiet on further logs that day
- **Last 7 days** — small bar chart with a goal reference line, today's bar highlighted separately
- **Settings** — opened via a gear icon in the header; a centered high-contrast modal (matching the "Did you know?" popup style) to change goal (ml), serving size (ml), and toggle **Sound effects** / **Vibration** on or off (both default on, take effect immediately). Closes via the X, tapping the backdrop, the gear icon again, or Esc.
- **Info / About screen** — a small circled "i" next to the app title opens a full-screen About page (purpose + numbered how-to-use steps + a privacy note that nothing leaves the device), with a "Home" back button to return to the tracker

## Design notes

- Palette: teal/aqua accent (`#0E7C86` light / `#49CBD3` dark) on a cool off-white ground, full light/dark theme support via CSS custom properties
- Type: Lexend (headings/numbers, tabular figures) + Manrope (body/UI)
- All sound is synthesized in-browser via the Web Audio API (short oscillator tones) — no audio files, works fully offline
- Data resets automatically at local midnight (date-keyed entries in local storage); no manual reset needed
- No footer/tips section — trimmed so the whole app fits one iPhone screen without scrolling

## Data & privacy

All data (daily logs, goal, serving size, sound/vibration preferences) lives in `localStorage` on whichever device/browser opens the artifact — nothing is synced or uploaded. Opening the link on a different device starts a fresh log.

## Updating the app

`index.html` in this project is the authored source for the live artifact — it is a complete, standalone HTML file.

To make changes in a future session:
1. Read `index.html` with the `Read` tool and edit it as needed.
2. Publish with the Artifact tool, passing `url: "https://claude.ai/code/artifact/66f6fa8d-ef32-4c87-aaa9-4ef6e679778c"` so it updates the existing app instead of creating a new one.
3. Write the updated file back to `index.html` with the `Write` tool so this copy stays in sync, and update the change history below.

## Change history

[List entries here — what changed and when]

## "Did you know?" facts (28)

1. 💧 Your body is about 60% water.
2. 🧬 Water helps carry nutrients to your cells.
3. 😴 Mild dehydration can leave you feeling tired and unfocused.
4. 🧠 Your brain is around 75% water.
5. 🍽️ Drinking water can help control hunger and cravings.
6. 🦴 Water helps keep your joints moving smoothly.
7. 💨 You lose water just by breathing, even without sweating.
8. 🫘 Water helps your kidneys clear out waste.
9. ✨ Your skin needs water to stay soft and elastic.
10. 🎯 Losing just 1–2% of your body's water can hurt focus and mood.
11. 🌡️ Water helps regulate your body temperature.
12. ❤️ Blood is about 90% water.
13. ⚡ Staying hydrated can boost your energy levels.
14. 💓 Water helps your heart pump blood more easily.
15. 💪 Muscles are about 75% water, so they need it to work well.
16. 🤕 Dehydration is a common trigger for headaches.
17. 🫁 Your lungs are about 83% water.
18. 🌅 A glass of water in the morning helps kick-start digestion.
19. 🥵 Feeling thirsty is a sign you're already a little dehydrated.
20. 0️⃣ Water has zero calories, making it the easiest way to refresh.
21. 🌟 Good hydration supports healthy, glowing skin.
22. 🥕 Water helps your body absorb vitamins and minerals.
23. 🐢 Even mild dehydration can slow down your metabolism.
24. 🏃 Sweating during exercise means you need more water than usual.
25. 🛡️ Water cushions and protects your spinal cord and joints.
26. 🦠 Staying hydrated helps your body fight off illness.
27. ☕ Tea and coffee count toward your fluids, but water is still best.
28. 😊 Drinking enough water can improve mood and reduce fatigue.
