# Israeli numbering plan — reference

Checked on 2026-08-03 against the prefix and special-number tables of the
Wikipedia article *Telephone numbers in Israel* (revision 1361192991). The
Ministry of Communications numbering-plan page (`gov.il/he/pages/numbering_plan`)
refused automated fetches on that date. Use it, or the Ministry's
`data.gov.il` numbering-plan datasets, when an authoritative answer matters.

## Prefixes

| Prefix | Service | Local form | From abroad |
|---|---|---|---|
| `02 03 04 08 09` | Geographic landline | `0A-XXX-XXXX` | `+972 A-XXX-XXXX` |
| `05N` | Mobile | `05N-XXX-XXXX` | `+972 5N-XXX-XXXX` |
| `07N` | Non-geographic landline / VoIP | `07N-XXX-XXXX` | `+972 7N-XXX-XXXX` |
| `10X 11X 12XX` | Emergency and public short codes | as dialled | **no** |
| `151` | Voicemail access | | |
| `153` | Fax box | | |
| `1599` | Business number, caller pays | `1-599-XXX-XXX` | usually **no** |
| `1700` | Business number, caller pays | `1-700-XXX-XXX` | usually **no** |
| `180X` | Toll free | `1-80X-XXX-XXX` | usually **no** |
| `19XX` | Premium rate | `1-9XX-XXX-XXX` | **no** |
| `*XXXX` | Business star code | as dialled | **no** — no E.164 form |

`00` and `01X` are prefixes for dialling out of Israel; they are never part of
a stored number.

## Star codes (`כוכבית לעסקים`)

Source: Ministry of Communications decision of 2022-12-05, "שירות מספר מקוצר
לעסקים - כוכבית וארבע ספרות", reference `5000-3001-2022-005404`.

- A business star code is `*` plus four digits in the pattern `AXXX`, where A
  is 2, 3, 5, 6, 8 or 9, plus the `45XX` and `49XX` ranges.
- The holder must have a contract with a licensed fixed-line provider.
- The code is converted to a "shadow number" (מספר צל) inside the terminating
  Israeli carrier. Because the conversion happens there, it cannot be reached
  from outside the Israeli network.
- There is no public mapping from star code to number. `data.gov.il` had no
  star-code dataset when searched on 2026-08-03. Partner and Bezeq publish only
  whether a code is free or taken.

## Emergency and public short codes

| Code | Service |
|---|---|
| 100 | Police |
| 101 | Magen David Adom (ambulance) |
| 102 | Fire and rescue |
| 103 | Israel Electric Corporation |
| 104 | Home Front Command |
| 105 | National child online-protection centre |
| 106–109 | Municipal call centre. 106 in most cities; check yours. |
| 110 | Police information line |
| 118 | Ministry of Welfare emergency line |
| 119 | National Cyber Directorate (cyber incidents) |
| 1201 | ERAN emotional first aid |
| 1202 / 1203 | Sexual assault crisis line (women / men) |
| 1220 / 1223 | ZAKA |
| 1221 | United Hatzalah |
| 144 | Directory enquiries |
| 171 | Israel Post |

The Hebrew service names govern. Confirm a code before publishing it anywhere
people will rely on it.
