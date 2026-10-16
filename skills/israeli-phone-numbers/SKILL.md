---
name: israeli-phone-numbers
description: Read, format and sanity-check Israeli phone numbers — what kind of number it is (landline, mobile, VoIP 07X, 1-800 toll-free, 1-700/1-599 caller-pays, 19XX premium, *XXXX star code, short codes like 100/101/106), how to write it locally and in +972 form, whether it can be dialled from abroad or from a foreign SIM, and how to find a reachable alternative when it cannot. Use when saving or tidying Israeli contacts, when a number "doesn't connect", when calling Israel from abroad, or when converting between 0XX and +972 formats.
---

# Israeli phone numbers

The useful question is often not "is this number well formed?" but "will it
connect, and from where?". In Israel these come apart more than in most
countries, and the failure is silent: the number looks fine and simply does not
ring. `references/numbering-plan.md` has the full prefix table and the short
codes.

## Formatting

| Kind | Local form | International (E.164) |
|---|---|---|
| Landline (02 Jerusalem, 03 Tel Aviv area, 04 Haifa and north, 08 south and Shfela, 09 Sharon) | `02-629-4666` | `+972 2-629-4666` — drop the leading 0 |
| Mobile (05X) | `054-123-4567` | `+972 54-123-4567` |
| Non-geographic / VoIP (07X) | `077-123-4567` | `+972 77-123-4567` |
| 1-800 / 1-700 / 1-599 | as printed, e.g. `1-800-22-1000` | none that works reliably from abroad |
| Star code `*XXXX` | `*3450`, keep the asterisk | **none** |

Rules:

- **To convert local to international,** drop the trunk `0` and prefix `+972`.
  To go back, reverse it. `+972 0…` is always wrong.
- **Keep printed groupings for 1-800 and 1-700 numbers.** `1-800-22-1000` and
  `1-800-221-000` are the same number, and customers recognise the agency's own
  grouping.
- **Keep extensions out of the number.** Extensions appear as `שלוחה 4`, `ext 4`
  or `,,4`. Put the extension in a label or note. Pause characters differ by
  phone, and contact syncs have been seen to mangle them.
- **The mobile prefix does not identify the carrier.** Israel has had mobile
  number portability since 2007, so a 052, 054 or 050 number may belong to any
  operator.

## The traps

**1-800 does not travel.** Toll-free `1-800` and `1-801` numbers, and
caller-pays `1-700` and `1-599` numbers, are unreachable from most countries
outside Israel. Often they also fail from a foreign SIM roaming in Israel. This
hits new immigrants and anyone calling from abroad.

**Star codes are not phone numbers.** `*XXXX` is an alias that the Israeli
carrier converts inside its own network to a hidden "shadow number" (מספר צל).
A call from abroad, from a VoIP platform or from a roaming foreign SIM never
reaches that conversion, so it resolves to nothing. No setting changes this.
There is no public register mapping star codes to numbers; the Ministry of
Communications' own 2022 decision describes the carriers' records as
inconsistent.

**1-800 and 1-700 look alike but cost differently.** `180X` is free to the
caller. `1700` and `1599` are paid by the caller, and are not always cheap from
a mobile plan. Record which one the source actually printed.

## Finding a number that works from abroad

When the main number is 1-800, 1-700, 1-599, 19XX or a star code:

1. Look on the organisation's **contact page** (`צור קשר`) and **"calling from
   abroad"** section (`לפונים מחו"ל` / `מחוץ לישראל`). Organisations that
   advertise a star code or a 1-800 number usually also publish an ordinary
   `0X` number for overseas callers.
2. Search `"<organisation>" טלפון מחו"ל` or `"<organisation>" +972`.
3. If none exists, say so plainly. Suggest the organisation's online channels
   (web form, WhatsApp, email), or calling through an Israeli number such as an
   Israeli SIM or an Israeli VoIP number. Knowing there is no route is itself
   useful.

## Short codes

These are three digits, work from any Israeli phone, and do not work from
abroad:

- 100 police;
- 101 Magen David Adom (ambulance);
- 102 fire;
- 104 Home Front Command;
- 103 Israel Electric (outages);
- the **municipal call centre: 106 in most cities**, but some use 107, 108 or
  109. Check the city's own site rather than assuming 106.

The full list is in the reference file. Short codes are worth knowing, but not
worth saving as contacts. The exception is the municipal one, precisely because
it varies.
