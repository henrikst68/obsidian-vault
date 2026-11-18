---
created: '2026-11-18'
machine: Sage Oracle Dual Boiler SES995
tags:
  - espresso
  - reference
---
# Sage Oracle Dual Boiler (SES995) — machine reference

Back to [[Areas/Espresso/README|Espresso]]

Collected 2026-11-18 from the Sage Nordic user guide and two hands-on reviews. Sources at the bottom.

## Key points for dialing in
1. **Shot stop is volumetric, not by weight.** The machine counts water through the flow meter. In volume mode the volume cannot be adjusted (manual example: about 30 ml for a single shot). The weight in the cup depends on how much water the puck holds back, so the scale and the machine can disagree a lot (e.g. 27 g in cup on 2026-11-18 19:14 with a dense, cold-ground puck).
2. **Brew control can be switched between volume-based and time-based**, in both auto and manual mode. Time-based example in the manual: 25 s per drink.
3. **Auto Dial-In** adjusts the grind for the next shot when a shot is "not ideal". Sage does not say what it measures or the target. Coffeeblog: it moves about 3 grind settings per shot and does **not** prompt a grinder purge between shots. The reviewer only got close after 6 shots, once they started purging manually. Likely reason: grounds retained from the previous setting end up in the next shot, so each shot lags one change behind.
4. **Purge:** double-tap the grind icon to purge the grinder (double-tap brew or steam icon purges those systems).
5. **Manual mode** (swipe up on the coffee drinks screen): real-time pressure gauge, pre-infusion, bloom, extraction time, temperature in 1 °C steps. Useful for diagnosing drift, because the pressure is visible.

## Grinder
- Baratza M2 burrs (same as Baratza ESP per Tom's Coffee Corner). Motor-driven grind adjustment, no dial.
- 45 digital grind settings + 10 inner (upper) burr settings. Lower number = finer.
- Upper burr: move one number at a time, one adjustment at a time.
- Grinder dosing can be switched between volumetric and timed with a long press (Coffeeblog).
- Hopper 340 g. Do not run the grinder without the hopper lid.
- Light, dense roasts can strain burrs and motor (Tom's Coffee Corner).

## Dose and tamp
- Grounds are spun into the basket and filled until they reach the spinning tamp fan. When resistance is detected, the grinder stops and the fan polishes the puck (about 25 s for 18 g).
- Factory dose about 22 g (large basket), about 12 g (small basket). Lowering tamp depth brought one reviewer to about 18.5 g.
- Dose varies about ±1.5 g shot to shot (reviewer: usually 18.5 g, outliers 16–20 g). Matches our own ±1–2 g.
- Tamp height: adjust at the grind collar with the hex key, machine off and unplugged. Max 1 turn at a time, then recheck. Connector must not exceed **29.2 mm**. Clockwise shortens, anticlockwise lengthens.
- A missing tamp fan causes overfilling and continuous grinding.
- Baskets: single-wall 1 cup and 2 cup, 58 mm. An IMS basket can lower the dose.

## Temperature, pressure, pre-infusion
- Two PID boilers: 450 ml brew, 950 ml steam, plus heated group.
- Heat-up about 3–5 min. Espresso best after about 10 min, when the portafilter is warm.
- Pre-infusion: automatic in auto mode, "gradually increases water pressure". Manual mode: full control incl. bloom.
- Over-pressure valve limits max pressure (no bar value given).
- Auto-off after 5–20 minutes, cannot be disabled. Relevant for drift tests: the machine cools in standby.

## Troubleshooting (manual)
- Too fast: grind too coarse or stale beans → lower grind number, adjust time, fresher beans.
- Slow, restricted flow: grind too fine → raise grind number, check shot volume.
- Yield changes with identical settings: beans age → lower grind number, fresher beans.
- Beans: use 5–20 days after roast date.

## Implications for our setup
- Judge every shot by the scale, not by the machine's stop.
- When the grind changes (by hand or by Auto Dial-In), purge the grinder before the next shot.
- For drift testing and cold starts, use manual mode or time-based brewing, and watch the pressure gauge.
- The Supreme bag (packed 2026-10-01) is outside Sage's 5–20 day window.

## Sources
- [Sage SES995 user guide (Nordic)](https://assets.sageappliances.com/BES995/Nordic/SES995_the+Oracle_Dual_Boiler_Nordics_A25.pdf)
- [Tom's Coffee Corner: Oracle Dual Boiler review](https://tomscoffeecorner.com/sage-breville-oracle-dual-boiler-review/)
- [Coffeeblog: Oracle Jet & Oracle Dual Boiler review](https://coffeeblog.co.uk/sage-oracle-review/)
- [Home Assistant integration (sageha)](https://github.com/simonjgreen/sageha)
