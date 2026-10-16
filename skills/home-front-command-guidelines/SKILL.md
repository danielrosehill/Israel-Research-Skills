---
name: home-front-command-guidelines
description: Answer questions about Israeli civil-defence guidance from the Home Front Command (Pikud HaOref, פיקוד העורף) from a bundled snapshot of its official English guidelines, with the source page cited. Use for what to do in a rocket or missile alert (at home, in a car, outdoors, in a public building), choosing and preparing a protected space (mamad, miklat, stairwell), hostile aircraft or drone infiltration, terrorist infiltration, hazardous-materials events, how alerts are received, emergency kit lists, a family emergency plan, and who to contact in an emergency.
---

# Home Front Command guidelines

Answers civil-defence questions from `references/guidelines/`. That folder holds
22 English pages (about 31,000 words) captured from the Home Front Command's
official site, `https://www.oref.org.il/eng`, on **2026-03-20**.
`references/guidelines/manifest.json` gives the source URL of every file.

## Active emergency first

If the user is in a live alert right now, skip the research.

- **Tell them to get to the nearest protected space immediately:** a mamad, a
  shelter, or an inner stairwell.
- **Point them to official real-time alerts:** the Home Front Command app,
  oref.org.il, TV and radio.
- **Give the emergency numbers:** 100 police, 101 Magen David Adom (ambulance),
  102 fire, 104 Home Front Command.

This skill is preparation and reference, not an alert system.

## How to answer

1. Pick the file or files from the index below. For a protected-space question,
   read both `protected-space-1.md` and `protected-space-2.md`. Split topics
   continue across the `-1` and `-2` files.
2. Read the file and answer from it. Quote the guideline when the exact wording
   matters, for example times, distances, or the order of actions.
3. Cite the `source_url` from the manifest for every file you used.
4. **Freshness.** The snapshot is dated 2026-03-20. Guidance changes during
   escalations, including policy levels, gathering limits, school status, and
   when you may leave the protected space. For anything about the *current*
   policy, check the live site or search the news for the latest Home Front
   Command announcement. Tell the user the bundled text may be out of date. If
   the snapshot is more than 6 months older than today, say so in every answer.
5. **Never invent numbers.** That includes the time to reach shelter, which is
   set per alert zone and depends on where the user is. If the files do not
   give the figure, send the user to the live site or the Home Front Command
   app, where it is published for their area.

## Index

| File (under `references/guidelines/`) | Covers |
|---|---|
| `faq/faq-rocket-missile-1.md`, `-2.md` | What to do in a rocket or missile alert, by location: inside, outside, in a vehicle, on public transport. Arrival time. Staying in the protected space. |
| `shelter-and-home/protected-space-1.md`, `-2.md` | Choosing a protected space when there is no mamad, mamad requirements and maintenance, the stairwell option |
| `shelter-and-home/preparing-home.md` | Preparing the home |
| `security-threats/hostile-aerial-vehicle-infiltration.md` | Drone or hostile aircraft alert, life-saving guidelines |
| `security-threats/terrorist-infiltration.md` | Terrorist infiltration, life-saving guidelines |
| `security-threats/security-threats.md` | Overview of the threat types |
| `faq/faq-hazardous-materials.md` | Hazardous-materials events |
| `alerts-and-communication/receiving-alerts-1.md`, `-2.md` | How alerts arrive: app, sirens, broadcast, accessibility |
| `alerts-and-communication/emergency-communication.md` | Emergency communication methods |
| `alerts-and-communication/do-not-share-info.md` | Not sharing impact locations online |
| `defensive-policy/defensive-guidelines-1.md`, `-2.md` | Policy levels: gatherings, education, workplaces. Check that these are still current. |
| `emergency-preparedness/emergency-equipment.md` | Emergency kit list |
| `emergency-preparedness/family-emergency-plan.md` | Family emergency plan |
| `emergency-preparedness/who-to-contact.md` | Who to contact |
| `emergency-preparedness/why-prepare.md` | Why to prepare |
| `faq/faq-general.md`, `faq/faq-emergency-preparedness-1.md`, `-2.md` | General questions |

## Related sources

- **Live site:** `https://www.oref.org.il/eng`, with a Hebrew edition at
  `https://www.oref.org.il/`. Pages render with JavaScript, so a plain fetch may
  return an empty shell. Use a browsing tool, or give the user the link.
- **Public shelters:** shelter lists are kept by each municipality, on its own
  site under shelters (`מקלטים ציבוריים`). Search
  `מקלטים ציבוריים <city name>`. A building's own mamad or inner stairwell
  takes precedence over walking to a public shelter when time is short.
- **Practical rights during emergencies,** such as absence from work or
  compensation for damage: use Kol Zchut (search `חרבות ברזל` plus the topic).
  The `kol-zchut-rights` skill covers how.

## Answer hygiene

- Quote the guideline; do not paraphrase safety-critical steps.
- Separate what the snapshot says from what you found live today, and date each.
- Do not present this skill as a substitute for emergency services or official
  alerts.
