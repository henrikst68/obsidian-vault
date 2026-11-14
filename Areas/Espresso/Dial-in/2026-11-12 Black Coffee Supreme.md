---
beans: Black Coffee Roasters Supreme
date: '2026-11-12'
machine: Sage Oracle Touch
status: in progress
tags:
  - espresso
  - dial-in
---
# Dial-in 2026-11-12 — Black Coffee Roasters Supreme

Back to [[Areas/Espresso/README|Espresso]]

## Beans
- Black Coffee Roasters **Supreme**, 100% Arabica blend, 900 g bag, roasted in Aarhus
- Listed notes: caramel, hazelnut, dark chocolate. Intensity 7/10 (medium to medium-dark roast)
- Packed 2026-10-01, so about 6 weeks old on the test day
- Storage: Airscape canister. About 20 g (one dose) weighed into the hopper per shot

## Machine behaviour (Sage Oracle Touch)
- Dose is set by a fill sensor: the grinder stops when the basket is full (corrected 2026-11-13, earlier assumed time-based). Finer, more even grounds pack denser, so a finer grind gives a higher dose. The grind setting controls both dose and flow
- Auto tamp. Shot stop set to **time**, not volume
- Manual brew mode: the display switches between stop info and seconds, so time is hard to read. Use the scale timer or a phone stopwatch
- No pressure reading available

## Shot log

| # | Beans | Grind | Temp | Dose | Yield | Time | Ratio | Taste / note |
|---|---|---|---|---|---|---|---|---|
| 1–2 | Hopper, all day | 12 | 93 | 20.0 | ~0 | — | — | Choked. First shots of the day |
| 3 | Airscape | 12 | 93 | 19.3 | 38 | 34 (manual) | 1:1.97 | Nice. Reference shot |
| 4 | Hopper, all day | 12 | 93 | 19.3 | 38 | 34 | 1:1.97 | Same flow, much more sour |
| 5 | Fresh from bag | 12 | 93 | 19.1 | 41 | 30 | 1:2.15 | A bit sour |
| 6 | Bag | 11 | 93 | 18.9 | 40.7 | 30 | 1:2.15 | More bitter. Bottomless: no channeling |
| 7 | Bag | 11 | 93 | 19.1 | 39 | manual | 1:2.04 | Balanced |
| 8 | Bag | 11 | 93 | 18.7 | 42 | 30 | 1:2.25 | More sour |
| 9 | Bag | 11 | 93 | 19.1 | 35 | 30 | 1:1.83 | Balanced but flat, no sweetness |
| 10 | Bag | 11 | 92 | 19.2 | 55 | 32 | 1:2.86 | Thin, sour |
| 11 | Bag | 11 | 92 | 19.0 | 55.8 | 32 | 1:2.94 | Same |
| 12 | Bag | 11 | 93 | 18.9 | 53 | 32 | 1:2.80 | Reached 38 g at ~27 s |
| 13 | Bag | 11 | 93 | 19.1 | 37.8 | 27 | 1:1.98 | OK, not sour, not bitter, still lacking sweetness |

Temperature set to 92 °C at the end of the session.

## Findings
1. **Beans left in the open hopper all day go sour.** At the same dose, yield and time, hopper beans tasted clearly more sour than Airscape beans. Staling (loss of CO₂ and aromatics) removes sweetness and leaves acidity.
2. **First shots of the day choke.** Retained grounds from overnight plus a higher dose (20 g) stopped the flow. Purge a few grams before the first shot.
3. **Dose drives yield with a timed stop.** The time-based grinder varies by ±0.2–0.4 g at the same setting. A lighter puck flows faster, so a fixed time gives more yield (about 3 g more for 0.4 g less dose).
4. **Flow speeds up strongly at the end of the shot.** Up to ~27 s the flow is about 1.4 g/s. From 27 to 32 s it added about 15 g (~3 g/s). Two extra seconds of shot time can add 10–15 g. This, not the temperature, caused the 55 g shots.
5. **1 °C temperature change does not change the flow.** Tested 92 and 93 °C: same fast result.
6. **Single dosing (~20 g in hopper) was used for all shots from #3**, so it did not cause the change. It may add some variation.
7. **No channeling** seen in the bottomless portafilter. Puck firm, shower-screen imprint (little headspace) is normal at ~19 g.

## Current working setting
- Grind **11**, dose ~19 g, timed stop **27 s** → ~38 g (1:2)
- Temperature: 92 °C (changed at end of session, not yet tested at this setting)

## Session 2026-11-13 (morning) — loaded hopper
Grinder purged the night before (empty). 100 g beans put in the hopper. Temp 92 °C.

| # | Hopper | Grind | Dose | Yield | Time | Flow | Taste / note |
|---|---|---|---|---|---|---|---|
| 14 | 100 g | 11 | 20.7 | 36 | 65 | 0.55 g/s | Choked |
| 15 | 100 g | 13 | 19.4 | 38 | 45 | 0.84 g/s | Still slow |
| 16 | 100 g | 15 | 19.0 | 39 | 35 | 1.11 g/s | 1:2.05. Not sour, but a bit too much acidity. Close to target |

| 17 | topped up | 15 | 18.6 | 40 | 35 | 1.14 g/s | 93 °C. 1:2.15. Less acidity than #16 |

- 93 °C confirmed as better than 92 °C for this blend
- Hopper was topped up before #17, so the 18.6 g dose is normal variation (±0.3 g), not popcorning
- Hopper minimum not yet known. Test: fill to 100 g, keep settings fixed, log dose per shot without topping up. A clear dose drop (< ~18.7 g) marks the limit. Until known, top up below ~60 g

| 18 | ~80 g | 15 | 18.6 | 43 | 25 | 1.72 g/s | 93 °C. Bit too sour, not bad. Even flow, no channeling |
| 19 | ~60 g | 15 | 18.4 | 43 | 22 | 1.95 g/s | 93 °C |
| 20 | fresh room-temp beans, purged | 15 | 18.4 | 41 | 24 | 1.71 g/s | 93 °C |

### Open issue: flow jumped between #17 (08:37) and #18 (08:41)
- Same settings, flow went from ~1.1 to ~1.7–1.95 g/s and dose dropped 19.0 → 18.4 g. Looks like a coarser grind (about 5 grind steps)
- Ruled out: channeling (even flow), temperature setting, hopper level, warm beans in hopper (#20 with fresh beans still fast)
- Burr thermal expansion: estimated ~10 µm for 20 °C, and inner/outer burr growth partly cancel. Too small and too slow for a step change in 4 minutes, but not fully ruled out
- Remaining: grinder warming over the session, or mechanical change (upper burr seat)
- Tests: (1) grind 13 now, check if flow returns to ~1.1 g/s; (2) next morning cold start, 100 g hopper, grind 15 — starts at ~1.1 g/s and drifts = warming; starts fast = something moved in grinder

| 21 | 10:44 | 13 | 18.6 | 58 | 25 | 2.32 g/s | Finer setting, but faster flow and no dose increase |
| 22 | 10:58 | 15 | 18.0 | 36 | 17 | 2.1 g/s | After cleaning and reseating upper burr |
| 23 | 11:09 | 15 | 18.5 | 39 | 20 | 1.95 g/s | After cleaning tamp fan |

| 24 | 11:15 | 10 | 19.0 | 40 | 26 | 1.54 g/s | Grinder responds: dose up, flow down. Whole scale shifted ~5 steps vs 08:00 |

| 25 | 11:23 | 8 | 19.3 | 39 | 36 | 1.08 g/s | Back on target (1:2.02). Matches #16 at grind 15 → offset ~7 steps since 08:00. Slightly bitter, drinkable. Next: grind 9 (~30–32 s) |

(For #21–25 the "Hopper" column shows the time of the shot.)

**Working setting at 11:23 (machine on ~3.5 h): grind 8, 93 °C, ~36 s → ~39 g.** Compare with tomorrow's cold start at grind 15.

## Session 2026-11-14 — cold-start test
| # | Time | Grind | Dose | Yield | Time | Flow | Note |
|---|---|---|---|---|---|---|---|
| 26 | 08:11, cold machine | 15 | 19.0 | 39 | 38 | 1.03 g/s | 100 g in hopper, 93 °C. Same flow as #16. A bit too bitter → target ~34–35 s. Next cold start: grind 16 |
| 27 | 08:18 | 15 | 18.9 | 37.1 | 29 | 1.28 g/s | Flow +25% in 7 min. Drift starting. Less bitter than #26, but harsh (rough, dry mouthfeel = astringent, likely uneven extraction from faster flow). Next: grind 14 (~34–35 s) |
| 28 | 08:47 | 14 | 18.7 | 43.6 | 25 | 1.74 g/s | Drift faster than one step can follow. Next: grind 10 |
| 29 | 08:51 | 10 | 19.2 | 38 | 28 | 1.36 g/s | Closer. Still a bit harsh. Next: grind 9 for ~34–35 s; if still harsh: 92 °C, then shorter yield (~34–35 g). If none helps: beans (age) are the limit |

### Conclusion: grind drifts coarser as the machine stays on
- Cold machine at grind 15 gives the reference flow (~1.0–1.1 g/s). After ~1 hour on, the same setting runs at ~1.7–2.3 g/s
- Total drift about 7 grind steps over ~3 hours (grind 15 cold ≈ grind 8 after ~3.5 h)
- On 2026-11-13 the jump appeared about 50 minutes after the machine was turned on
- Likely mechanism: machine heat warms the grinder housing and burr holder (aluminium or plastic, which expand more than steel) and moves the upper burr, widening the gap. Earlier estimate that only counted steel burr expansion was too small
- No fault found. Not a beans, hopper, tamp, scale or temperature-setting issue

### Practical settings (Supreme, loaded hopper, 93 °C)
- First hour after power-on: grind 15, ~35–38 s → ~39 g
- After 1–3 hours: move finer step by step, toward grind 8 (~36 s → ~39 g at 3.5 h)
- Optional: map the drift with a shot every 15–20 min at grind 15, logging time since power-on

### Troubleshooting status (2026-11-13, 11:10)
All beans today came from the Airscape (same bag). Machine on since ~07:45.

Ruled out:
- Beans (same bag, same source all day)
- Hopper level and warm beans in hopper (#20, fresh room-temp beans, still fast)
- Brew temperature (92 vs 93 °C, same flow)
- Channeling (even flow in bottomless portafilter)
- Upper burr seating (cleaned and reseated, no change)
- Grind adjustment (grind 5 vs 25 gives a clear difference in the grounds)
- Tamp fan (cleaned, no problem found, setting never changed)
- Scale (yield difference clearly visible in the cup)

Not ruled out:
- Grinder or machine drift as it stays on (warming). Burr expansion estimate argues against a large effect, but the cause appears after ~1 hour of use
- Pump pressure or pre-infusion behaviour (no pressure reading available)
- An internal grinder fault not visible from outside

Next:
1. For drinkable coffee today: grind 9–10, manual brew, stop at ~38 g
2. Cold-start test next morning: machine cold, 100 g in hopper, grind 15, 93 °C, same as #16. Back at ~1.1 g/s = something drifts while the machine runs. Still fast = fault, contact Sage service with this log

**Setting grind 15, 93 °C, ~35 s → ~39–40 g was valid for #16–17 only. Under review.**

### Finding: hopper load changes the grind
- With a loaded hopper the bean weight feeds the burrs evenly: finer, more even grind, denser puck, higher dose
- With single dosing (~20 g in hopper) the last beans bounce on the burrs (popcorning): coarser grind, lower dose
- **Grind 11 with single dosing ≈ grind 15 with a loaded hopper**
- The choked first shots on 2026-11-12 (#1–2) were the same effect: full hopper, 20 g dose. Not a "first shot of the day" or retained-grounds effect
- Rule: pick one mode and dial in for that mode

### Settings per mode
| Mode | Grind | Dose | Timed stop | Yield |
|---|---|---|---|---|
| Single dose (~20 g) | 11 | ~19 g | 27 s | ~38 g |
| Loaded hopper (~100 g) | 15 | ~19 g | 34–35 s | ~38–39 g |

## Next steps (from 2026-11-12, partly superseded)
1. Purge a few grams before the first shot
2. Baseline: grind 11, 27 s, 92 °C. Compare with shot #13 (93 °C)
3. Then grind 10, timed stop ~30–31 s, target 37–39 g, for more contact time and sweetness
4. If still no sweetness: the beans are likely the limit (age, blend). Try a bag roasted within 2–3 weeks
5. Storage: keep about one week of beans in the Airscape, freeze the rest of the 900 g bag in airtight portions
