---
name: salary-conversion
description: Convert salaries between the Israeli convention (gross monthly, in shekels) and the international one (annual, in local currency such as USD, EUR or GBP), in either direction, at today's exchange rate. Also handles plain ILS ↔ foreign-currency price conversions for shopping. Use for "what is ₪25,000 a month in dollars", "how much is $120k a year in shekels per month", "compare this Israeli job offer to a US one", or "convert this price to shekels".
---

# Salary conversion (Israel ↔ world)

Israeli salaries are quoted **monthly, gross, in shekels** (₪ / NIS / ILS). Most
other countries quote **annual** salaries in their own currency. Mixing the two
conventions is the usual error. This skill converts between them.

## Defaults (ask only when the input is truly ambiguous)

- A shekel figure with no period is **monthly**.
- A foreign-currency figure with no period is **annual**.
- If a figure could be either, such as "60k USD" from a contractor, ask.
- With no target named, Israel → world converts to **USD**.
- Assume salaries are **gross** unless the user says otherwise.

## Israel → world

1. Annual shekels = monthly × 12.
2. Get today's ILS → target rate.
3. Annual foreign = annual shekels × rate. Round to whole units, or to the
   nearest hundred. Never quote cents on a salary.

Example: ₪25,000 a month → ₪300,000 a year. At 1 USD = 3.70 ILS that is
300,000 ÷ 3.70 ≈ **$81,100 a year**.

## World → Israel

1. Get today's source → ILS rate.
2. Annual shekels = annual foreign × rate.
3. Monthly = annual ÷ 12, **rounded to the nearest whole shekel**. No decimals
   on the shekel side, ever.

Example: $120,000 a year. At 3.70 that is ₪444,000 a year → **₪37,000 a month**.

## Exchange rate

Use a rate from today, from a reputable source. Real-time is not needed.
Preferred sources:

1. **Bank of Israel representative rate** (שער יציג). This is the official daily
   reference, and what Israeli payslips and contracts use. Search
   "Bank of Israel representative rate USD".
2. An ECB-based API, such as `https://api.frankfurter.app/latest?from=USD&to=ILS`,
   if you can fetch it.
3. A web search for "USD to ILS today", reading the rate from a reputable
   source.

Always state the rate, the source and the date, for example:
`Rate used: 1 USD = 3.703 ILS (Bank of Israel representative rate, 2026-10-16)`.
Re-fetch the rate on a new day; do not reuse an old one. If you cannot get a
rate, say so. Do not guess one.

## Comparing offers fairly

Nominal conversion is only the first step. Name these differences, and do not
model them unless the user asks:

- **Employer pension and severance contributions in Israel** come on top of the
  gross salary. Under the mandatory-pension rules, these are roughly 6.5%
  pension plus 6% or 8.33% severance, and they often include a study fund
  (קרן השתלמות) of 7.5%. These contributions are part of the
  "employer cost" (עלות מעביד). A US offer of $X is not comparable to an
  Israeli gross figure without them. Check current rates on Kol Zchut, using
  the `kol-zchut-rights` skill.
- **A 13th salary, car allowance (רכב צמוד / החזר רכב) and meal cards** appear in
  some Israeli packages and not others.
- **Net pay** depends on income tax, Bituach Leumi and health tax, and on tax
  credit points (נקודות זיכוי). This skill does not compute net. If the user
  needs it, say so, and point them to an Israeli net-salary calculator or to
  Kol Zchut. Or give a rough estimate, with the assumptions named.
- Cost of living and purchasing power are out of scope. This is nominal FX only.

## Plain price conversion

For "₪X in dollars" or "€Y in shekels", convert with the same rate rules. Show:

```
<amount> <from> = <result> <to>
Rate: 1 <from> = <rate> <to> (<source>, <date>)
```

For a list of prices, use a small table. Prices in Israeli shops include VAT.
Foreign shelf prices often do not. Mention this when the user is comparing.
