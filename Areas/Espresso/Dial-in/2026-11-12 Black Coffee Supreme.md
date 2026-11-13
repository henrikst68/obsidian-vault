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

Next test: 93 °C, grind 15, 34–35 s, to round off the acidity (one change).

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
