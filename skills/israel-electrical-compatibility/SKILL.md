---
name: israel-electrical-compatibility
description: Check whether a product bought abroad (AliExpress, Amazon, eBay, a trip overseas) will work and is sensible to import into Israel — plug type (Israeli Type H socket; which plugs fit), 230 V / 50 Hz mains and 110 V-only traps, the plug variant the listing ships by default, and categories that are restricted or need a permit (drones, radio transmitters, lasers, vapes, medicines, seeds, child car seats). Works from the listing text, specs or photos the user provides. Use for "will this work in Israel", "does this plug fit", "is this 220", "can I even import this".
---

# Will it work in Israel?

An import can fail in three ways:

- **It gets taxed.** See the `personal-import-tax` skill.
- **It never arrives.**
- **It arrives and cannot be used.**

This skill covers the last one. Read the voltage and plug from the listing's own
text and photos. Ask the user to paste the specs or describe the photos if you
cannot open the page. **Never infer them from price or category.**

## Israeli mains

| Property | Israel |
|---|---|
| Voltage | **230 V** |
| Frequency | **50 Hz** |
| Socket | **Type H** (SI 32). Since the 1989 revision it also accepts round pins. |

**Plugs:**

| Plug | Fits an Israeli socket? |
|---|---|
| Type C (Europlug: two round pins, no earth) | **Yes.** This is the usual "EU plug" from Chinese sellers. |
| Type H (Israeli) | Yes. Rarely offered; take it if it is. |
| Type E/F (Schuko: thick round body, earth clips) | **No.** "EU plug" sometimes means Schuko, so check the photo. |
| Type A/B (US), G (UK), I (AU/CN) | No. Needs an adapter. |

**Voltage is the expensive question.** An adapter changes the plug shape, not
the voltage.

- **100–240 V** (dual voltage): fine. Most chargers, laptop bricks and USB
  supplies are dual voltage.
- **220 V or 230 V**: fine.
- **110 V or 120 V only**: will not work on Israeli mains. Plugging it in
  directly can destroy it. A step-down transformer sized to the load costs more
  than most heating or motor appliances. Treat this as a fail.
- **Voltage not stated** on something mains-powered: unknown. Treat it as a fail
  until the seller confirms.
- **60 Hz-only motors and mains-timed clocks** run slow or hot on 50 Hz. This is
  rare, but check motorised goods.

**Plug type is usually a variant, not a listing property.** One listing offers
US, EU, UK and AU plugs, and the default is often US. Name which variant to
select.

## Restricted or awkward categories

Flag these for the user to check. **This is not a customs ruling.** The rules
change, so verify the current rule with a web search or the Tax Authority's
customs pages.

- drones / UAVs;
- radio transmitters, jammers, signal boosters, walkie-talkies outside approved
  bands — Ministry of Communications approval (אישור משרד התקשורת);
- WiFi or Bluetooth devices from unusual bands;
- laser pointers above low classes;
- e-cigarettes and vaping products;
- medicines, supplements, medical devices — Ministry of Health;
- seeds, plants, soil, animal products — Ministry of Agriculture;
- knives and weapon-like items;
- child car seats and other products that must meet an Israeli standard
  (תקן ישראלי).

Ordinary personal imports in reasonable quantities usually do not need an
Israeli standards mark at the border. The goods are still uncertified, which
matters for insurance and for anything hard-wired. Say this plainly, without
overstating or dismissing it.

## Output

```
<product>
VERDICT: works in Israel | works with a caveat | will not work | unknown
Voltage: <value> → <ok / fail / unknown>
Frequency: <value>
Plug: <variant options; default variant> → <fits / adapter / select variant X>
Category flags: <none | list, framed as "check">
Evidence: <spec line / photo / user-supplied text>
Action: <select the EU (Type C) variant / buy a plug adapter (not a converter) / don't buy>
```

| Situation | Verdict |
|---|---|
| Dual voltage, and a Type C or H variant | works |
| Dual voltage, only US/UK/AU plugs | caveat: needs a plug adapter (an adapter, not a converter) |
| 220–230 V and the plug fits | works |
| 110 V only | will not work |
| Mains-powered, voltage unknown | unknown → treat as will not work |
| Restricted category | caveat, whatever the electrics |
