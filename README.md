# Prado Ride

Personal-use iPhone web app to measure ride comfort and safety in a 2022 Toyota Prado 150 with Tough Dog Foam Cell shocks (9-click) and 265/65R17 mud terrain tyres (OEM size).

Uses the phone's motion sensors and GPS via standard web APIs. No server, no tracking — everything stays in the browser's local storage.

## Open it on your phone

1. Visit the GitHub Pages URL in Safari on your iPhone.
2. Tap **Grant Sensor Access** and approve the motion + location prompts.
3. (Optional) Share → **Add to Home Screen** for an app-like icon and full-screen mode.
4. Mount the phone on the windscreen, tap **Start trip**, hold still for 1 second while it calibrates, then drive.

## What it measures

- **Wk-RMS** — 1-second RMS of vertical acceleration. ISO 2631-1 comfort scale (<0.315 = comfortable, >2.0 = extremely uncomfortable).
- **Cumulative VDV** — 4th-power vibration dose value. Daily health-guidance-caution zone starts at 8.5 m/s^1.75.
- **Roll / Pitch** — from gravity vector after vehicle-frame calibration.
- **Lateral g** — peak cornering load.
- **Click change log** — log front/rear shock click changes mid-trip for A/B comparison.

## Limits

Browser-based prototype — sample rate caps at ~60 Hz (a native Swift app would hit 800 Hz). Wk weighting is simplified to a high-pass filter. No FFT, no road classifier, no recommender — see the [implementation plan](https://github.com/naickert/prado-ride) for the native iOS version those features need.

## Export

Each trip can be exported as JSON or CSV for Power BI analysis. All data is local to the browser — clear by tapping **Delete all trips** under Settings.
