---
name: israel-price-check
description: Judge whether an Israeli price is fair — find who sells a product in Israel and for how much (Zap price comparison, the big tech chains, other .il retailers), compare it with the international RRP or an Amazon/B&H price converted to shekels, and give a verdict on the markup, including a light-hearted "freier check". Also compares an AliExpress or other import price against local availability, accounting for landed cost and warranty. Use for "is this a good price", "am I being a freier", "where is X cheapest in Israel", "check Zap for X", "is it cheaper to import", "is this sold in Israel".
---

# Israel price check

Three questions, usually asked together:

1. **Local market.** Who sells it in Israel, and for how much?
2. **International reference.** What does it cost abroad, in shekels?
3. **Verdict.** Is the Israeli price fair? Would importing beat it once landed?

Reference material:

- `references/hebrew-retail-terms.md`: build queries Israeli sites understand.
- `references/retailers.md`: Zap, the big chains, URL patterns and price
  quirks.
- `references/verdict-scales.md`: thresholds for the verdict and the freier
  scale.

## 1. Local market

**Build the query in Hebrew.** Use a Hebrew category noun, followed by the brand
and model in Latin script, for example `עכבר Logitech MX Master 3S`. Israeli
retail search returns little for English category nouns. Brand and model stay
Latin because retailers index SKUs that way.

Run **two separate web searches** and report them separately. They answer
different questions:

- `<brand model> site:zap.co.il` — Zap is the national price-comparison
  aggregator. A Zap **model page** (`zap.co.il/model.aspx?modelid=…`) lists
  every vendor's price side by side. That page is the result you want. If you
  land on a category page, look for the model page.
- `<brand model> site:il` — "who sells this in Israel". This covers every `.il`
  domain: chains, small shops and manufacturer pages. Do not narrow it to
  `site:co.il`.

If your browsing tool can open pages, open the Zap model page and the top two or
three retailer pages to read live prices. If it cannot, use the prices shown in
search snippets, and label them as such.

Rules for prices:

- Quote **VAT-inclusive** shekel prices. Israeli retail prices include VAT
  (18% as of 2026-10-16). If a listing is ex-VAT (B2B, some Zap rows, Eilat),
  add VAT before comparing.
- **Eilat prices are VAT-free.** KSP and others show an Eilat price next to the
  regular one. Quote the regular, higher price unless the user is in Eilat.
- Zap's cached prices can lag by a day or more. Treat a vendor page as more
  current than the Zap table.
- Zap's headline "from" price is the cheapest vendor, whatever its reputation.
  Zap shows store ratings, so mention a low-rated cheapest vendor.
- **Official vs parallel import.** Parallel import (יבוא מקביל) is often cheaper,
  but the brand's Israeli service centre will not honour the warranty. The
  official importer is the יבואן רשמי. Note which one a listing is, if it says.
- Match on the **model number**, not the title. Israeli listings mix Hebrew
  titles with Latin model numbers, and near-identical models differ in suffix.
  If the exact model is not sold, name the closest one and flag the difference.

## 2. International reference

In order of authority:

1. the manufacturer's list price (RRP or MSRP) on its own site;
2. Amazon US, UK or DE;
3. B&H, for cameras, audio and computing.

Convert to shekels at today's rate, and state the rate, source and date.

**Live US prices may be unreliable from where you are.** Amazon and others
localise prices and availability by the visitor's country. From an Israeli
connection they may show shekel prices or "doesn't ship". Use the manufacturer
RRP, or a price the user gives you, if you cannot see a clean US listing. Say
which you used.

## 3. Verdict

The markup is `(Israeli price − international price in ₪) ÷ international price in ₪ × 100`.

Apply the markup scale in `references/verdict-scales.md`. Do not recommend
importing on the sticker price alone. Compute the **landed** cost, which
includes:

- shipping to Israel;
- Israeli VAT if the goods value is over the personal-import threshold ($75 as
  of 2026-10-16; see the `personal-import-tax` skill);
- the cost of no local warranty.

A 30–40% Israeli markup is often still cheaper than importing once all of that
is counted.

**Freier check** (פראייר, "sucker"). When the user asks "am I a freier?", give
the playful verdict from the freier scale on top of the real numbers. Keep it
light. Never freier-shame on an unverified RRP; if you could not confirm the
reference price, say so and skip the verdict.

## Comparing an import listing to local

When the user brings an AliExpress, Temu or Amazon listing:

1. Extract the exact product and model.
2. Run the local searches above.
3. Put the two side by side:
   - import price landed (with VAT if over the threshold) vs the cheapest
     credible local price;
   - delivery time (weeks vs days);
   - warranty (seller dispute only, vs the Israeli importer's 1 year or more).

## Output

```
## <product> — Israeli price check
Hebrew query: <query>

Local (Zap): ₪<low>–₪<high> across <n> vendors — cheapest <vendor> (<rating>) <url>
Local (site:il): <vendor> ₪<price> <url> · <vendor> ₪<price> <url>
International: <source> <ccy><price> ≈ ₪<x> (1 <ccy> = <rate>, <source>, <date>)

Markup: <pct>%   Verdict: <scale bucket>
<Freier verdict if asked>
Import instead? landed ≈ ₪<y> (<incl./excl. VAT>, <lead time>, <warranty note>) → <buy local | import | wait>
Notes: <VAT/Eilat adjustments, parallel import, snippet-only prices, closest-model substitutions>
```

Never invent a vendor, price or rating. A search that found nothing is a result.
Report it, and suggest another Hebrew term or the brand-only query.
