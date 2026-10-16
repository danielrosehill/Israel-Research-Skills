---
name: personal-import-tax
description: Work out whether an order from abroad (AliExpress, Amazon, Temu, eBay, iHerb and similar) will be charged Israeli VAT or customs on arrival, and how to keep a basket under the personal-import exemption. Takes listings or a cart the user pastes or describes, converts to USD, applies the VAT-free threshold per shipment, computes landed cost, and flags items that sit close to the line. Use for "will I pay VAT on this", "is this under the customs limit", "how much can I add before tax kicks in", "find me things that land tax-free", "what will this actually cost delivered to Israel".
---

# Israeli personal-import tax

Read `references/israel-import-tax.md` first. It has the current figures, how
they were verified, and the history of the threshold, which has changed several
times since late 2025.

**Before quoting any figure, check that the threshold has not moved since the
date in the reference.** Search `פטור ממע"מ יבוא אישי` or
`Israel VAT exemption personal imports threshold` for news newer than that date.
If the figure has changed, use the new one and say so.

## The two rules that cause most mistakes

1. **The threshold applies to goods only; the tax applies to the whole cost.**
   - **Threshold test:** the exemption is tested on the **goods value excluding
     shipping**.
   - **Tax base:** once it is crossed, VAT is charged on **goods + shipping +
     insurance** (CIF).

   Always report the two figures separately.
2. **It is a cliff, not a ramp.** Crossing the threshold puts VAT on the
   **whole** shipment, not just the excess. At $75 and 18%:
   $74 of goods costs ~$74, but $76 costs ~$76 × 1.18 ≈ $89.70.

A third rule: **the exemption is per shipment, not per item.** Three $60 items in
one order are $180 of goods, and fully taxable.

## Inputs

Accept whatever the user has:

- pasted listing text or a cart;
- a list of `title, price, currency, qty, shipping`;
- screenshots described in words.

You cannot open the user's cart or log in to their account. Work from what you
are given. If a price is a range (`₪10–₪25`), ask which variant they want. The
low end is only the cheapest variant.

## Procedure

1. **FX rate.** The threshold is in USD. Convert ILS prices with today's rate,
   from the Bank of Israel representative rate or an ECB-based source. Print the
   rate, its source and the date. If you cannot get a rate, stop and say so.
   Do not guess.
2. **Goods value:** the sum of unit price × qty in USD. Keep shipping separate.
3. **Classify the basket:**

   | Goods (USD) | Status | Meaning |
   |---|---|---|
   | ≤ 80% of the threshold (≤ $60 at $75) | GREEN | Comfortably exempt |
   | 80% up to the threshold | AMBER | Exempt. Report the headroom (threshold − goods) |
   | Over the threshold, up to $500 | RED | VAT on the whole CIF value. No customs duty. Purchase tax only on goods that carry it (e.g. TVs, car parts). |
   | Over $500 | RED+ | VAT plus possible customs duty and purchase tax, by product type. Out of scope; point to a customs broker. |

4. **Landed cost:**
   - Exempt: goods + shipping.
   - Taxed: (goods + shipping) × (1 + VAT rate). Carrier handling or clearance
     fees come on top; they are not modelled here.
5. **On RED, quantify and suggest:**
   - how far over the line the basket is, and the VAT that triggers;
   - which low-value items could be dropped to get back under, and the saving;
   - splitting into separate orders, each under the line. This is legitimate,
     but see the 72-hour rule below.

## Hunting for tax-free items

For "find me X that lands tax-free", use web search or the store's own search,
or work from listings the user pastes. Use tighter working lines than the law:

| Test | Line | Why |
|---|---|---|
| Item price | ≤ $70 | About 7% buffer against FX movement between checkout and assessment |
| Item + shipping | < $75 | Operational ceiling, tighter than the legal goods-only test |

Classify each candidate:

- **CLEAR** if landed is under $70.
- **TIGHT** if landed is $70–75. Show the USD/ILS rate at which it would cross
  the line.
- **OVER** if landed is $75 or more.

Rank candidates by headroom, not by price. Every qualifying item qualifies **on
its own**. Say so in the output whenever you list more than one.

## Output

```
Import tax check — threshold $<75> goods value (verified <date>), VAT <18>%
FX: 1 USD = ₪<rate> (<source>, <date>)

Items: <n>   Goods: $<x> (₪<y>)   Shipping: $<s>
Status: <GREEN | AMBER | RED | RED+>
<one-line verdict, e.g. "AMBER — $6.20 headroom; one more ~$6 item puts VAT on the whole order">

Landed estimate: goods $<x> + shipping $<s> + VAT $<v> = $<total> (₪<total_ils>)
<RED: what to drop or how to split>
```

## Caveats to pass on

- **Some stores collect Israeli VAT at checkout.** AliExpress and others
  sometimes do. If the checkout shows a tax line, do not add VAT again.
- **Split orders are combined under a 72-hour rule.** Two or more parcels from
  the **same supplier** to the same customer within **72 hours** are treated as
  one split shipment, and taxed on their total value (Kol Zchut, 2026-10-16).
  Splitting only helps across different suppliers, or with more than 72 hours
  between shipments. Consolidated lanes such as AliExpress Choice may also ship
  several "orders" as one parcel. Never promise that a split will work.
- **Shipping must be separable.** If the invoice does not show shipping
  separately from the goods, the whole amount is tested against the threshold.
- **Promotional prices expire.** Assess on what the user will actually pay.
- **Bulk-quantity tiers** are a common way to cross the line unnoticed. Check
  the tier total, not the unit price.
- **Out of scope:**
  - Advice on undervaluing, misdeclaring or labelling goods as gifts. Do not
    give it.
  - Vehicles and other special regimes.
  - A guaranteed customs outcome. This is an estimate against published
    thresholds.
- For whether the item will work in Israel at all (plug, voltage, restricted
  categories), see the `israel-electrical-compatibility` skill.
