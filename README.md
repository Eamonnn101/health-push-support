**English** | [简体中文](README.zh-Hans.md)

---

# Health Push — Support

Health Push is an iOS app that exports your Apple Health (HealthKit)
data as clean, structured JSON files designed to be consumed by LLM
agents (ChatGPT, Claude, local models, etc.).

This page is the official support channel for the app.

---

## Get Help

- **Email**: eamon.pangyu@gmail.com
- **Bug reports / feature requests**: please open an
  [Issue](https://github.com/Eamonnn101/health-push-support/issues)
  on this repository

Response time is best-effort, usually within a few days.

---

## FAQ

### Where do the exported files go?
Inside the app's private sandbox, under `Documents/exports/`, with
file names like `health-20260518-093015-30d.json`. Use the share
button next to any entry in the in-app history list to send the file
to Files, Mail, Messages, or any other destination via the system
share sheet.

### Does Health Push send my data anywhere?
No. Every byte of HealthKit data is processed on-device. There are
no network calls, no analytics, no crash reporting, no third-party
SDKs. The only time a file leaves the app is when **you** trigger
the share sheet.

### How does incremental export work?
Health Push uses HealthKit's `HKAnchoredObjectQuery`. After every
successful export, it saves the anchor that HealthKit returns. On
the next incremental export, only data that was added or modified
since that anchor is included, along with a list of deletions for
workouts you removed in the Health app.

### Why didn't my workout / metric appear?
Two common reasons:

1. **Authorization** — Health Push can only read data types you
   approved. Open the Health app → Sharing → Apps → Health Push and
   make sure every metric you care about is enabled.
2. **Date range** — confirm the metric falls inside the range you
   exported. Incremental export only returns data since the last
   anchor.

### How do I delete my data?
Health Push doesn't store HealthKit data outside of the JSON files
it writes to its own sandbox. To remove everything:

- Delete exported JSON files: use the trash icon next to any entry
  in the in-app history list, **or** uninstall the app — iOS will
  delete the sandbox automatically.
- Revoke HealthKit access: Settings → Privacy & Security →
  Health → Health Push → turn off all categories.

### Is Health Push compatible with Health Auto Export format?
The per-day metric structure (one record per date × source, with
`qty` for cumulative metrics and `Min`/`Max`/`Avg` for discrete
ones) follows the same shape commonly used by JSON-based health
export tools. Workout payloads include per-minute time-series for
active energy, distance, heart rate, and step cadence.

### What's in a workout payload?
Each workout includes: name, start / end, duration, active energy
burned, distance, elevation change, intensity, step cadence,
temperature, humidity, indoor / outdoor flag, plus per-minute
arrays for active energy, step count, walking-running distance,
heart rate (Min / Max / Avg), and heart-rate recovery during the
60s after the workout.

---

## Requirements

- iOS 18.0 or later
- An iPhone with HealthKit data (the simulator lets you authorize
  HealthKit but won't have any data)

---

## Privacy

See [PRIVACY.md](./PRIVACY.md) for the full Privacy Policy.

Short version: Health Push reads HealthKit data on your request,
writes JSON files to its own sandbox, and never sends anything over
the network.

---

© 2026 Yu Pang
