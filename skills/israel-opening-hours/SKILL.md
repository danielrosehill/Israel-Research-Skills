---
name: israel-opening-hours
description: Answer "is this Israeli business or office open", "what time does it close Friday", "will it be open after Shabbat", or "is it open on chol hamoed" — gather the stated hours (Google, the business's own site, easy.co.il, Hebrew listings), translate Shabbat- and holiday-relative wording (e.g. "until an hour before Shabbat", "an hour after Shabbat ends") and turn it into clock times for the actual date using that city's candle-lighting and havdalah times. Use for any opening-hours question about a business or office in Israel, especially around Friday, Saturday night and Jewish holidays.
---

# Israeli opening hours

Many Israeli businesses set their Friday and Saturday hours relative to Shabbat,
not to the clock. Candle lighting moves by about 1 hour 40 minutes between
midwinter and midsummer. So a Google listing saying "Friday 08:00–16:00" is
often simply wrong for the week in question. "Saturday: Closed" also hides the
Saturday-night (motzei Shabbat) reopening, which is usually what the user wants
to know.

The job:

1. collect what the sources state;
2. work out the rule behind it;
3. evaluate the rule for the real date.

## 1. Pin down the business, the city and the date

- **The city matters.** Candle-lighting customs differ:
  - Jerusalem: **40 minutes** before sunset;
  - Haifa (and Zikhron Ya'akov): **30**;
  - most other places: **20**.

  Verified on 2026-10-16 for Friday 16 October: Jerusalem 17:26, Haifa 17:35,
  Tel Aviv 17:47. Mixing up Jerusalem and Tel Aviv puts every derived time out
  by about 20 minutes. Ask for the city if it is unclear.
- Default to today. "Before Shabbat" means the coming Friday.

## 2. Classify the date first

Find out what kind of day the date is:

- ordinary weekday;
- Friday / erev Shabbat;
- Shabbat;
- erev chag;
- Yom Tov;
- chol hamoed;
- a fast day;
- Yom Kippur.

Get the candle-lighting and havdalah times for that city and date:

- **Hebcal's public API** returns JSON for a city. These calls worked on
  2026-10-16:
  `https://www.hebcal.com/shabbat?cfg=json&geonameid=<id>&M=on`.
  - Jerusalem `281184`, Tel Aviv `293397`, Haifa `294801`.
  - Other places: look up the GeoNames ID.
  - **Address the location by city or GeoNames ID, not latitude and longitude.**
    The city-specific candle-lighting custom is applied only by city.
- Or search "candle lighting <city> <date>" / `זמני כניסת שבת <city>`.

If the date is **Yom Kippur**, answer now. Essentially everything Jewish-run is
closed nationwide, including Ben Gurion airport, until after havdalah.

## 3. Collect the stated hours

Sources, by what they are good for:

| Source | Good for | Watch out for |
|---|---|---|
| Google Business listing | Sunday–Thursday clock times; phone number | Fixed clock times only. Friday is often stale, and Saturday "Closed" hides the evening reopening. |
| The business's own site or social pages | Current hours, holiday notices | Holiday notices are often posted only a few days ahead |
| easy.co.il (Israeli business directory) | The merchant's own Hebrew wording, with the Shabbat phrasing intact | Often years out of date. Behind a Cloudflare challenge, so it may need a real browser or search snippets. |
| A phone call | Certainty | Recommend it before a trip |

When sources disagree, the business's own current notice beats the directories.
Use easy.co.il for the *rule* and Google for the clock times, and tell the user
about the disagreement.

## 4. Translate the wording into a rule

`references/hebrew-hours-phrases.md` has the phrase table. For example,
`עד שעה לפני כניסת השבת` means "until candle lighting minus 60 minutes".

## 5. Resolve and answer

- **Lead with the concrete time,** then the reasoning. For example: "Closes
  about 15:56 this Friday — 90 minutes before candle lighting, which is 17:26 in
  Jerusalem on 16 Oct."
- **State your confidence and its source.** Sunday–Thursday clock times from a
  recent listing are usually right. A Friday time you *derived* is an estimate;
  say so.
- **For Saturday questions, give the reopening time,** not just "closed".
- **Never present a derived time as authoritative** for a trip. Suggest calling,
  and give the number if you have it.

## Israeli context that changes the answer

- **Not everything closes on Shabbat.** Much of Tel Aviv and Haifa trades on
  Saturday, as do Arab- and Christian-owned businesses everywhere, some
  kibbutz-run malls, and many restaurants. Apply a Shabbat rule only when the
  source says so, or the business type clearly implies it (kosher-certified,
  most supermarket chains, government offices).
- **The working week is Sunday–Thursday.** Government offices and many services
  are closed on Friday, or open only a short morning. `א׳–ה׳` means Sun–Thu, not
  Mon–Fri.
- **Erev chag behaves like Friday.** Yom Tov behaves like Shabbat. Israel keeps
  one day of Yom Tov, not two. Rosh Hashana is still two days.
- **Chol hamoed** hours are reduced and vary by branch. Treat any answer as low
  confidence.
- **Fast days** other than Yom Kippur mostly affect restaurants and cafés.
- **Ramadan** shifts hours in Arab-majority areas, such as East Jerusalem,
  Nazareth and Umm al-Fahm. The Shabbat calendar does not cover this; say so.
- **Government offices** run on appointment systems, and their stated counter
  hours often differ between the branch page, the national page and the booking
  system. Trust them in that order: the branch page beats the national page,
  and the booking system decides whether you need an appointment.
