# Espresso

Shot parameters, bean notes, grinder settings, and dialing-in logs.

## Machine
- **Sage SES995**, installed 2026-11-14. Not dialed in yet.
- Previous machine: Sage Oracle Touch (SES990), replaced 2026-11-14.
- Reference: [[Areas/Espresso/SES995 Machine Reference|SES995 Machine Reference]] (manual + reviews: volumetric stop, Auto Dial-In, purge, tamp height limits)
- Tamper height adjustment screw: factory default **22.86 mm** (noted 2026-11-17, before any adjustment).

| Date | Change | Screw (mm) | Effect on shots |
|---|---|---|---|
| 2026-11-17 | Factory default | 22.86 | — |
| 2026-11-17 15:40 | Extended 1 revolution (≈0.74 mm/rev) | 23.6 | 15:46 shot: grind 14, dose fell to 20.5 g (from 22.7 at same grind), 40 g in 24 s — faster |

## Current setting
- Black Coffee Roasters Supreme (2026-11-17): grind 13, tamper screw 23.6 mm, ~21 g → 40 g in ~33 s. Straight: good mouthfeel, some chocolate. Dose varies ±1 g; weigh each shot.

## Dial-in logs
### 2026-11-17 Black Coffee Roasters Supreme (SES995)
Beans look medium roast (not light), matte, one quaker in a handful.

| Time | Grind | Dose (g) | Out (g) | Ratio | Time (s) | Taste |
|---|---|---|---|---|---|---|
| 08:08 | ? | 22.5 | 37 | 1:1.6 | 32 | Slightly bitter |
| 10:38 | 18 | 22.1 | 49 | 1:2.2 | 26 | — |
| 10:44 | 16 | 21.5 | 54 | 1:2.5 | 25 | Still bitter |
| 10:49 | 14 | 22.7 | 44 | 1:1.9 | ~30? | OK, no distinct notes; good as americano |
| 13:54 | 15 | 22.0 | 43 | 1:2.0 | 30 | Americano harsh/astringent |
| 15:46 | 14 | 20.5 | 40 | 1:2.0 | 24 | (tamper 23.6 mm) |
| 15:53 | 13 | 22.4 | 30.6 | 1:1.4 | 37 | (tamper 23.6 mm) — slow, near choke |
| 15:59 | 13 | 21.2 | 40 | 1:1.9 | 33 | (tamper 23.6 mm) — same settings as 15:53; dose −1.2 g. Straight: nice, good mouthfeel, maybe a bit of chocolate |

### 2026-11-18 Black Coffee Roasters Supreme (SES995), tamper 23.6 mm

| Time | Grind | Dose (g) | Out (g) | Ratio | Time (s) | Taste |
|---|---|---|---|---|---|---|
| ~07:15 | 14 | ? | — | — | — | First shot, cold machine. Choked completely |
| 07:24 | 18 | 21.4 | 23 | 1:1.1 | 39 | Grind set manually to 18. Still choked (0.59 g/s). Yesterday 10:38 at grind 18 (warm): 49 g in 26 s (1.9 g/s, tamper 22.86 mm) |
| 19:14 | 20 | 21.6 | 27 | 1:1.25 | 31 | Cold machine (evening). 0.87 g/s, still slow. Grind 20 set by Auto Dial-In. Cold flow ≈ +0.14 g/s per step → ~grind 23 for 1.3 g/s cold. Auto Dial-In stayed at 20 after this shot despite 1:1.25 ratio — it may judge by shot time, not yield (to check: how the shot was stopped). Next: grind 22 set manually |
| 19:21 | 22 | 19.8 | 41 | 1:2.07 | 28 | 1.46 g/s. Good ratio, slightly fast. Dose fell with coarser grind. Harsh, a bit bitter. Next: grind 21, purge first (machine still warming) |

| 19:25 | 22 | ? | 43.5 | — | 20 | 2.18 g/s. Same grind as 19:21, flow +50% in 4 min = warm-up drift. Next: grind 19, purge first |

| 19:29 | 19 | 20.2 | 40.6 | 1:2.01 | 31 | 1.31 g/s. On target. More pleasant, no distinct taste notes → beans likely the limit |

### 2026-11-21 Black Coffee Roasters Supreme (SES995), machine on 07:30

| Time | Grind | Dose (g) | Out (g) | Ratio | Time (s) | Taste |
|---|---|---|---|---|---|---|
| 08:03 | 20 | 22.3 | 22.8 | 1:1.02 | 34 | ~30 min after power-on. Ristretto (0.67 g/s). Good taste |

Practical idea: power on 45–60 min before the first shot (timer or Home Assistant), so shots are pulled on a warm, stable grinder. To check: does standby/auto-off (5–20 min, cannot be disabled) cool the grinder again?

Pattern across both machines (~40 shots): harshness recurs at many settings; best result only "nice, a bit of chocolate" (2026-11-17 15:59). Beans (Supreme, packed 2026-10-01, ~7 weeks) are outside Sage's 5–20 days window. Test a fresh bag (roasted within 2–3 weeks, roast date on bag) to separate bean age from settings.

Auto Dial-In is ON (does not change grind while idle; only after shots). After the 07:24 shot it moved grind 18 → 20 by itself. From here: no manual grind changes, log the grind Auto Dial-In picks after each shot, to see if it follows the warm-up drift.

**Finding: cold machine grinds much finer, same as on the Oracle Touch.** At grind 18, flow cold 0.59 g/s vs warm 1.9 g/s (~3×). Yesterday's warm setting grind 13 → today cold grind 14 choked. Same grinder-on-heated-machine design, same effect. Plan: cold start at ~grind 22, step finer as the machine warms (toward 13–14 when fully warm). Log time of each shot to map the drift.

Notes: grind time cannot be set on the SES995 — the machine sets the dose itself. Dose link to grind and tamper height is NOT confirmed: at 23.6 mm the dose was 20.5 g at grind 14 but 22.4 g at grind 13. Dose appears to vary ±1–2 g shot to shot. Weigh every dose; measure spread with repeated shots at one setting before concluding.

## Archive — Sage Oracle Touch (SES990)
- [[Archive/Espresso - Sage Oracle Touch SES990/2026-11-12 Black Coffee Supreme|2026-11-12 Black Coffee Supreme]] — shots 1–29 (12–14 Nov). Findings: hopper beans staling, single dose vs loaded hopper, grinder drifting ~7 steps coarser over ~3 h of power-on. Last settings: grind 15 cold, grind 8–10 after 1–3 h, 93 °C, ~19 g → ~39 g.
