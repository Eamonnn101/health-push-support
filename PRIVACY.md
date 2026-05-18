**English** | [简体中文](PRIVACY.zh-Hans.md)

---

# Health Push — Privacy Policy

**Effective date: May 18, 2026**

This policy describes how Health Push ("the app") handles your data.

---

## Summary

Health Push processes Apple Health (HealthKit) data **entirely on
your device**. The app does not run any network requests, does not
include third-party SDKs, and does not collect analytics or crash
reports. Data only leaves the app when **you** explicitly share an
exported file via the iOS system share sheet.

---

## What data the app reads

When you grant permission, Health Push reads samples from
Apple HealthKit for the metric types you authorize, which may
include:

- Activity & energy (steps, distance, floors climbed, active energy,
  basal energy, exercise / stand / move minutes)
- Heart rate family (heart rate, resting heart rate, walking heart
  rate average, heart-rate variability, cardio recovery)
- Cardiovascular & respiratory (respiratory rate, blood oxygen,
  VO₂ max, blood pressure, six-minute walk)
- Body measurements & vitals (body temperature)
- Gait & running dynamics (walking speed / step length / asymmetry,
  stair speeds, running power / vertical oscillation / ground contact
  time / stride length / step cadence)
- Environmental & behavioral (environmental sound levels, headphone
  audio exposure, mindful minutes, hand washing, alcohol consumption)
- **Sleep analysis** (in-bed / asleep boundaries plus core, deep,
  REM, and awake stage durations)
- **Workouts** including per-minute time-series for energy, distance,
  heart rate, and step cadence

The app only reads the data types you have approved in
Settings → Privacy & Security → Health → Health Push. You can change
this at any time.

---

## What the app does with that data

1. Transforms the raw HealthKit samples into a structured JSON file
2. Writes the JSON file to the app's own private sandbox at
   `Documents/exports/`
3. Stores a small history record (file name, timestamp, range,
   sample count) using Apple's SwiftData framework, also inside the
   sandbox
4. Persists an opaque "anchor" token returned by HealthKit so the
   next incremental export only fetches new or changed data

That's it. The app does not modify your HealthKit data and never
writes back to HealthKit.

---

## What the app does NOT do

- **No network requests.** The app contains no networking code. It
  does not contact any server operated by the developer or by anyone
  else.
- **No third-party SDKs.** No analytics, no advertising, no crash
  reporting frameworks of any kind.
- **No accounts.** The app has no login, no user identifiers, and
  no telemetry.
- **No tracking.** The app does not use the Advertising Identifier
  (IDFA) and does not request App Tracking Transparency permission.

---

## When data leaves the device

The only way an exported file leaves your device is when **you**
tap the share button next to an entry in the in-app history list.
That action invokes the iOS system share sheet, which is operated
by Apple. The destination (Files, Mail, Messages, AirDrop, a
third-party app, etc.) is chosen by you. Once a file reaches a
third-party destination, that destination's privacy policy applies.

---

## Data retention and deletion

- **Exported files** live in the app sandbox until you delete them
  from the in-app history list, **or** until you uninstall the app.
  Uninstalling Health Push removes the entire sandbox, including all
  exports and the history database.
- **HealthKit access** can be revoked at any time in Settings →
  Privacy & Security → Health → Health Push.

---

## Children

Health Push is not directed at children under 13 and is not designed
to collect data from children.

---

## Changes to this policy

If this policy changes materially, the updated version will be
published in this repository with a new effective date. The history
of changes is visible in the repository's commit log.

---

## Contact

For privacy questions or requests, contact:

**Email**: eamon.pangyu@gmail.com

---

© 2026 Yu Pang
