---
name: nsc-travel-warnings
description: Find the Israeli National Security Council (NSC, המטה לביטחון לאומי) travel warning for a country — the threat level from 1 to 4, the recommendation, any region-specific warning, and recent changes — by web research, with the official gov.il page cited. Use for "is it safe for Israelis to travel to X", "what's the NSC warning level for X", "Israeli travel advisory for X", or before booking a trip abroad as an Israeli or Jewish traveller.
---

# NSC travel warnings

The National Security Council's Counter-Terrorism Bureau publishes travel
warnings for Israelis abroad. They are country by country, and some cover a
single region. They are about **terror threats against Israelis and Jews**, not
general crime or health, so they often differ from the US, UK or other foreign
advisories for the same country.

**Official source:** `https://www.gov.il/en/departments/dynamiccollectors/travel-warnings-nsc`
(English). The Hebrew page is the same path under `/he/`. Each country has a card
with:

- the threat level;
- the recommendation;
- the area under threat;
- background details;
- a link to the Foreign and Health Ministries' advice.

## The scale

| Level | Name | Recommendation |
|---|---|---|
| 1 | Low / no special threat | Normal precautions |
| 2 | Potential threat | Increased precautionary measures |
| 3 | Medium threat | Avoid non-essential travel |
| 4 | High threat | Avoid travel; those already there should leave |

These names follow how the NSC and the Israeli press describe the scale. The
exact wording on the cards can differ slightly, so quote the card when you have
it. Separately from the NSC scale, **Israeli law forbids Israelis to enter
enemy states** without a permit. The NSC page notes this.

## Workflow

1. **Try the official page once.** `www.gov.il` often answers automated fetches
   with a Cloudflare 403 challenge. This was seen from an Israeli IP and from a
   cloud fetch tool on 2026-10-16. If your browsing tool renders the page, read
   the country's card and quote it.
2. **Otherwise, research it.** Search for both:
   - `NSC travel warning <country> Israelis` (English press: Times of Israel,
     Ynetnews, JNS, i24);
   - `אזהרת מסע <country> המטה לביטחון לאומי` (Hebrew press: Ynet, Walla, Maariv).

   Take the **most recent** dated report. Warnings change around holidays and
   anniversaries, and during regional escalations, often for a set period.
3. **Report with dates.**

```
<Country> — NSC travel warning
Level: <n> (<name>) — <recommendation>
Area: <whole country | region>
As of: <date of the card or article>   Source: <URL>
Notes: <recent change, temporary period, specific advice (avoid Israeli symbols, Chabad houses, gatherings)>
Official page: https://www.gov.il/en/departments/dynamiccollectors/travel-warnings-nsc
```

4. **Say what you could not confirm.** If you only found a news report, say
   that the official card was not reachable. The user should check it before
   booking. Never infer a level from neighbouring countries, or from an older
   article, and present it as current.

## Context worth adding

- NSC warnings come with standing advice: keep a low profile, do not advertise
  Israeli identity or travel plans on social media, avoid demonstrations, and
  stay alert at Jewish and Israeli venues.
- Health and entry requirements (vaccines, visas) come from the Foreign Ministry
  and the Health Ministry, not the NSC. The card links to them.
- For the user's own government advisory (if they also hold another
  citizenship), check that country's foreign ministry too. The two are
  independent.
