---
name: brand-and-part-number-check
description: Identify what an Israeli-market product really is — an unfamiliar brand seen only in Israel (white-label, importer's own label, rebadged OEM, or genuinely Israeli), or an Israeli listing's local part number for a consumable (toner, filter, spare part, accessory) mapped to the manufacturer's international part number. Use for "what is this brand", "is X any good", "what's the international model of this", "what's the real part number for this toner", or before buying the same item abroad.
---

# Brand and part-number check

Israeli retail has two quirks that make like-for-like comparison hard:

- **Importer labels.** Local distributors put their own brand on generic,
  usually Chinese, OEM products.
- **Local part numbers.** Consumables are relabelled with local part numbers
  (PNs) that match nothing in the manufacturer's global catalogue.

This skill resolves both. It is often the step before a price comparison (the
`israel-price-check` skill).

## A. "What is this brand?"

1. **Search with Israeli context:**
   - `"<brand>" יבואן` (importer);
   - `"<brand>" Israel importer`;
   - `"<brand>" OEM` / `white label`.
2. **Read the brand's Israeli site,** if it has one. Look at the address, the
   importer details, any OEM references, and the country of manufacture.
   Israeli consumer-protection rules require the importer to be identified on
   many product categories, so the label or site often names them.
3. **Compare product photos.** Rebrands often keep the OEM's exact moulding.
   A reverse image search, if available, usually finds the source product.
4. **Check forums:** Zap reviews, HWzone, and Facebook buyer groups.
5. **Classify:**
   - **white-label of a known OEM** — name the OEM and the equivalent global
     product;
   - **importer label** — a generic ODM product under a distributor's brand;
   - **genuinely Israeli brand**;
   - **unknown**.

## B. "What is the international part number?"

1. From the Israeli listing, extract:
   - the brand;
   - the parent device ("for HP LaserJet M404");
   - the local PN or SKU;
   - capacity or yield;
   - the photos.
2. Cross-reference, in this order:
   1. the manufacturer's global site, which is authoritative for PNs;
   2. Amazon, from the product details;
   3. B&H, for imaging, audio and computing;
   4. AliExpress, for compatibles.
3. **Confirm on three axes,** not on PN alone: the photo, the spec
   (capacity, yield, dimensions), and the device-compatibility list.
4. Flag **genuine vs compatible** (third-party). Note if the Israeli PN is an
   importer relabel of a standard part.

## Output

```
## <brand / product> — what is it?
Verdict: <white-label of OEM | importer label | Israeli brand | unknown>   Confidence: <confident | tentative | unknown>
Probable OEM / equivalent: <brand + model, link>
International PN: <pn> (IL listing: <local pn>)   Genuine/compatible: <…>

Evidence:
- <importer disclosure / photo match / spec match / forum consensus — with links>

Recommendation: <buy local / buy the international equivalent / need more info>
```

## Rules

- Do not name an OEM without evidence. Acceptable evidence is a visual match,
  an importer disclosure, a spec match, or a credible forum consensus. Otherwise
  the answer is "unknown".
- White-label is not a defect. Report it factually.
- For consumables, match capacity or yield and the compatibility list before
  declaring two parts equivalent.
