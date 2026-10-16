---
name: israeli-medications
description: Research a medicine in the Israeli context — whether it is registered in Israel, its Israeli brand names and generic equivalents, prescription or over-the-counter status, whether it is in the health basket (סל הבריאות), what a health fund (Clalit, Maccabi, Meuhedet, Leumit) charges, the official Hebrew/English/Arabic patient leaflet, and the rules for carrying medication abroad or bringing it into Israel. Uses the Ministry of Health drug registry, drug.co.il and the health funds' public guides via web research. Use for "is X available in Israel", "what's the Israeli name for X", "is X in the sal", "how much is X on Maccabi", "where's the leaflet for X", or "can I take my medication abroad".
---

# Israeli medications research

Four public sources answer different questions. Pick the one that answers the
user's question, rather than querying all four.

| Question | Source | Notes |
|---|---|---|
| What will I pay? Is it covered? Does it need prior approval? | **The user's health fund** (קופת חולים) | Practical answer. Ask which fund if unknown. |
| What is this drug? Generics? Plain-language leaflet? | **drug.co.il** (Pharmacists' Organisation of Israel) | Patient-facing |
| Is it registered in Israel? License holder? Official indication? | **Israeli Drug Registry**, `israeldrugs.health.gov.il` (Ministry of Health) | Regulatory, authoritative |
| What drugs are added to the basket this year? | Ministry of Health and press on the annual basket decision | |

## 1. Health fund — the practical answer

Each fund publishes a medicines guide with the medicine's prescription status,
basket status, prior-approval requirement and a patient price. Search:

- `<drug name> מכבי מחיר` / `<drug name> כללית` / `<drug name> מאוחדת` / `<drug name> לאומית`
- Maccabi's guide lives under `https://www.maccabi4u.co.il/healthguide/medicines/`.
  Search reaches each medicine's page. The page IDs are internal, so do not
  guess them.

From a fund page, report:

- prescription required (מרשם);
- in the basket (בסל הבריאות), including any indication restriction;
- prior approval needed (התחייבות / אישור מוקדם);
- the price to the patient. Ignore reference and ceiling prices.

Copays differ by fund and by supplementary plan (שב"ן: e.g. Maccabi Sheli,
Clalit Mushlam), so name the plan the price applies to. Funds' widgets often
need a real browser. If yours cannot open them, give the user the guide link.

## 2. drug.co.il — what the drug is

`https://drug.co.il` has one page per drug and dose. Each page lists the Hebrew
and English name, manufacturer, active ingredient, ATC code, form, prescription
status, basket status, approved indication, equivalent drugs, and links to the
Ministry of Health leaflets.

- Search: `site:drug.co.il <name or active ingredient>`. The site's own search
  is `https://drug.co.il/?s=<query>`, with a minimum of 3 characters.
- Each dose has its own page (for example 30 / 50 / 70 mg), so pick the dose
  the user means.
- The site returned **503 to automated fetches** on 2026-10-16. Rely on search
  snippets, or a browsing tool, and give the link.
- Prices on drug.co.il are usually empty (`לא נמצא מידע`). Do not report them as
  zero.

## 3. Israeli Drug Registry — regulatory facts

`https://israeldrugs.health.gov.il/#!/byDrug` lets you search by trade name or
active ingredient, in Hebrew or English. Tick `הצג תרופות בסל הבריאות בלבד` to
show basket drugs only.

- The site is a JavaScript app backed by POST-only APIs. A plain fetch returns
  an empty shell. Use a browsing tool, find the page through web search, or
  give the user the search link.
- Each drug has a page:
  `https://israeldrugs.health.gov.il/#!/medDetails/<registration number with spaces as %20>`,
  for example `…/medDetails/153%2021%2034000%2000`.
- Key fields:
  - **registration number** (מספר רישום). Quote it on administrative forms.
  - **license holder** (בעל הרישום). This is not always the manufacturer.
  - **approved indication** (התוויה). Quote it verbatim.
  - **registration status**. A **cancelled** (מבוטל) or suspended registration
    means the drug is leaving the market. Flag it prominently.
  - **leaflets:**
    - `עלון לצרכן`: the patient leaflet. Offer this by default.
    - `עלון לרופא`: the physician leaflet.
    - `החמרה לעלון`: an amendment notice, not the leaflet itself.

  Leaflet PDFs are hosted under `mohpublic.z6.web.core.windows.net`.

## Name matching

Israeli brand names often differ from US and EU names. Search by **active
ingredient** (generic name, in English) when a brand name misses. drug.co.il
and the registry both index ingredients. Many drugs also have a Hebrew brand
transliteration. Try both scripts.

## Travelling with medication

The Ministry of Health page for travellers is "נשיאת תרופות בנסיעה לחוץ לארץ
ובכניסה לישראל" (`gov.il/he/pages/carrying-medication`). It covers taking
medicine abroad and bringing it into Israel. For **controlled drugs** (סמים
מסוכנים — e.g. stimulants, opioids):

- **Pharmacy Procedure 155** (`gov.il/he/pages/dr-155`), section 3.2.8, lets the
  doctor issue up to **3 identical same-dated prescriptions**, each for up to 31
  days, marked `נסיעה לחו"ל`.
- The **pharmacy** asks the district pharmacy office to approve dispensing for
  up to 92 days. The patient supplies a passport copy, a ticket with dates, a
  declaration and a 3-month dispensing record.
- The procedure sets no minimum trip length. A health fund's own page may add
  stricter conditions; the national procedure is the reference.
- The Ministry's page says to **go to the pharmacy at least a week before
  departure**.

These figures were checked against the Ministry pages on 2026-08-03/04. Check
the live pages again before relying on them, and check the destination
country's import rules for the same drug.

## Answer hygiene

- Never give dosing or interaction advice beyond quoting the leaflet. Point the
  user to their pharmacist or doctor.
- Say which source each fact came from, and its date.
- "Not found" in one source is not "not available in Israel". Check the
  registry before concluding that.
