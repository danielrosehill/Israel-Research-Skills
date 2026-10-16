# Israeli personal-import tax — current figures

**Last verified: 2026-10-16**, by web search of Israeli press, VAT-news sites and
Kol Zchut. This topic has been politically volatile. Re-check before relying on
a figure, and if a newer source contradicts this file, trust the newer source.

## Current position (as of 2026-10-16)

| Item | Value | Confidence |
|---|---|---|
| Standard VAT rate | **18%**, since 2025-01-01. It was 17% before. | Confirmed by several sources. The 2026 budget kept 18%. |
| VAT-free personal-import threshold | **USD 75** goods value per shipment. It went back to $75 on **2026-06-02**. | Confirmed: VATupdate (2026-06-10, citing ICL Global), Kol Zchut's personal-import digest, and Israeli press. |
| What the threshold is tested on | Goods value **excluding** shipping and insurance | Confirmed by a Kol Zchut worked example ($70 of goods + $20 shipping is exempt), and reported by Times of Israel and ICL Global |
| Band above the threshold, up to USD 500 | **VAT (18%), no customs duty.** Purchase tax (מס קנייה) still applies to goods that carry it, such as TVs and car parts. | Kol Zchut, "זכותון בנושא יבוא אישי (חבילות מחו"ל)" (read 2026-10-16) |
| Split parcels | **Two or more parcels from the same supplier to the same customer within 72 hours count as one split shipment**, and are taxed on their combined value | Kol Zchut digest (read 2026-10-16) |
| Shipping not separable | If the shipping and insurance cannot be separated from the declared value, the whole declared amount is treated as goods value | Kol Zchut digest |
| USD 500–1,000 | VAT, and for some goods customs duty and purchase tax | Kol Zchut digest; not modelled here |
| Over USD 1,000, and tobacco or alcohol | A separate regime, and may require a customs broker | Kol Zchut digest |
| VAT base once taxable | CIF: goods + shipping + insurance | Standard import-VAT practice; consistent with all the sources above |

## Threshold history

Reconstructed from press coverage; the dates come from multiple outlets.

| Period | Threshold | What happened |
|---|---|---|
| Long-standing until late 2025 | $75 | |
| Late 2025 (order published 2025-11-26) → early 2026 | $150 | Finance Minister's order doubling the exemption. Retailers objected. |
| 2026-02-24 | $75 | The Knesset revoked the order. |
| 2026-02-25 → 2026-06-01 | $130 | A new ministerial order. Kol Zchut gives these dates. |
| From 2026-06-02 | $75 | Tax Authority and Customs systems updated back to $75. |

Several outlets disagree on the exact February sequence. What matters for a
calculation is the figure in force on the day of import. Search for the latest
figure before quoting it.

## Sources

- VATupdate, "Israel Restores $75 VAT Exemption Threshold for Personal Imports" (2026-06-10)
- Kol Zchut, `https://www.kolzchut.org.il/he/זכותון_בנושא_יבוא_אישי_(חבילות_מחו"ל)`
- Times of Israel, "Ad hoc tax changes for overseas online orders cause confusion for Israelis about charges"
- Haaretz (2025-11-26) and Ynetnews coverage of the $150 order
- Kintsugi / PwC tax summaries for the 18% rate

## Working figures used by the skill

- Threshold `T = 75` USD on goods value. Update this if the threshold changes.
- `VAT = 0.18`
- Split-parcel rule: same supplier, same customer, within 72 hours → combined
- Hunting buffer: item ≤ $70, landed < $75
- AMBER band: goods > 0.8 × T
