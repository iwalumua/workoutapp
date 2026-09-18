# Groundwork — daily training plan

A single-file web app that builds a **knee-smart, dumbbell-only** daily workout,
tracks your history, and adapts tomorrow's plan from what you did today.

Built around a specific set of needs:

- **Goal:** fat loss + strength, moving toward a healthy weight/BMI.
- **Equipment:** dumbbells + an adjustable (incline) bench only.
- **Constraints:** patellar-tendon knee rehab (all knee work stays pain-free and
  complements your physio) and ankle-stability work (for ankles prone to rolling).
- **Schedule:** 4 training days/week, ~60-minute sessions.

## What it does

- **Today** — the day's session laid out in blocks (warm-up → main lifts →
  accessories → ankle/knee rehab → core → cardio). Each exercise has:
  - the **target muscles**,
  - an **ℹ️ info button** with set-up, step-by-step instructions, what you should
    feel, a "your form is wrong if…" warning, and precautions,
  - inline logging of **weight used, reps/time, effort, and a knee/joint-pain flag**.
- **Submit → plan tomorrow** — analyses the day and builds the next one.
  - Uses **Claude** for a tailored coaching note + progression when available
    (via the artifact `sample` capability); otherwise falls back to a built-in
    **progressive-overload rule engine**. The app always works either way.
  - Skip a day? Tomorrow simply repeats — nothing is lost.
- **Plan** — the week ahead and the rotating 4-day split.
- **Progress** — BMI + healthy-range snapshot, bodyweight trend, and
  **per-muscle-group** top-weight/volume charts.
- **History** — every session, expandable, with **CSV export** (save to Google
  Drive / back up) and **CSV import**.
- **Cross-device sync** — when opened as a Claude Artifact, data syncs
  automatically across devices signed into the same Claude account (via the
  artifact `db` capability, stored privately under `data/users/<you>/state`).
  If the database isn't available, the app stays device-local — nothing breaks.
  A sync-status chip in the header shows the current state.
- **Setup** — your details, dumbbell list, bench type, days/week, AI toggle, and a
  physio/safety note shown on every Today screen.

## Running it

Open `index.html` in any browser — no build step, no server. Data is saved
privately in your browser (`localStorage`); use **Download CSV** to back it up.

> The AI daily-analysis feature uses Claude when the page runs as a Claude
> Artifact. Opening the raw `index.html` locally still works fully — it uses the
> built-in rule engine for progression. A future standalone app can wire in a
> Gemini API key for the AI analysis.

## Safety

This is a training aid, not medical advice. Keep all knee work pain-free and
follow your physiotherapist's guidance first.
