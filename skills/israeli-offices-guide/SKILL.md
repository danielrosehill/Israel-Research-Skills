---
name: israeli-offices-guide
description: Work out which Israeli office handles something and find its current contact details, hours and appointment route — Population and Immigration Authority (Misrad HaPnim), Ministry of Aliyah and Integration, Bituach Leumi, Tax Authority, health funds, municipality, Employment Service, Israel Electric — including the names people actually use versus the official names, Hebrew search terms that find branch pages, which sites block automated fetches, and how to decide between conflicting hours. Also builds a first-year checklist of offices for new immigrants and returning residents. Use for "who do I call about X", "which office handles Y", "what are the hours of the Bituach Leumi branch in Z", "what offices does a new oleh need".
---

# Israeli offices guide

Israel's bureaucracy is divided along lines that make little sense until you
have been through it. This skill does three things:

1. routes a task to the right office;
2. finds that office's current details;
3. reconciles the conflicting details agencies publish about themselves.

`references/agencies.md` maps the agencies' colloquial names to their official
ones, and lists what each one handles.

## 1. Route the task

Match the user's task against the "Handles" column in `references/agencies.md`.
Some splits catch people out:

- **Misrad HaPnim vs the Ministry of Aliyah.**
  - Misrad HaPnim (Population and Immigration Authority) handles the teudat
    zehut and its appendix (ספח), passports, address changes and civil status.
  - The Ministry of Aliyah and Integration handles the absorption basket
    (סל קליטה) and olim benefits.

  They are different ministries.
- **Health insurance enrolment goes through Bituach Leumi,** or for new olim
  sometimes the post office or the absorption process, not through the health
  fund. You then choose a fund.
- **Arnona (municipal property tax)** and its discounts are handled by the
  municipality. So are parking permits and local services.
- **Rights questions** ("am I entitled to…") go to Kol Zchut first. See the
  `kol-zchut-rights` skill. Kol Zchut's articles name the responsible office
  under `גורמים מסייעים`.

## 2. Find the details

**Search in Hebrew.** An office's own page rarely ranks for its English name.
Use the colloquial name to search, and expect the official name on the page:

- `<agency> שעות קבלת קהל <city>` — counter hours;
- `<agency> מוקד טלפוני` — call centre;
- `<agency> סניף <city>` / `לשכת <city>` — branch page;
- `<agency> זימון תור` — book an appointment.

**What fetches.** As tested with a browser-like client from an Israeli IP on 2026-10-16:

| Host | Automated fetch |
|---|---|
| `www.gov.il` (most ministries, including Misrad HaPnim and the Ministry of Aliyah) | **Usually blocked.** Cloudflare challenge, HTTP 403, even from Israel. There is no JSON back door; the `/api/*` paths are blocked too. |
| `btl.gov.il` (Bituach Leumi) | Readable |
| `taxes.gov.il` (Tax Authority) | **Now redirects to `www.gov.il`** and is blocked there. It was readable on 2026-08-03. |
| `iec.co.il` (Israel Electric), `taasuka.gov.il` (Employment Service), `israelpost.co.il`, `parks.org.il` | Readable |
| `kolzchut.org.il` | Readable with a browser-like client; bot clients are challenged |
| Health funds' clinic finders | JavaScript widgets; need a real browser |
| Municipality sites | Vary |

If a page is blocked:

1. use search-result snippets;
2. try a real browsing tool, if you have one;
3. or ask the user to paste the page. They are often already looking at it.

Do not retry a blocked host with different settings. Appointments for Misrad
HaPnim and many other offices run through **MyVisit** (`myvisit.com`, also an
app).

## 3. Decide what to trust

Agencies contradict themselves. The branch page, the national page and the
appointment system often give different hours for the same office. In order of
trust:

1. a recent photo of the sign on the door;
2. the branch's own page, over the national page;
3. the appointment system, for whether a service needs an appointment;
4. Google's hours, which lose to all of the above.

Say which source you used, and that the sources disagreed.

**Hours vocabulary:**

- `קבלת קהל` is counter or walk-in hours.
- `מוקד טלפוני` is the phone line.
- `מענה אנושי` is the hours when a person, not the automated menu (IVR),
  answers. This is often shorter than the line's hours; quote it when it is
  stated.
- `א׳–ה׳` is Sunday–Thursday.

The `israel-opening-hours` skill covers Friday and holiday hours.

## First-year checklist for new arrivals

Ask about the person's situation before listing anything: oleh or returning
resident, children or not, arriving with a job or not. Twenty irrelevant
offices bury the four that matter. The usual order:

| When | Office | Why |
|---|---|---|
| Week 1 | Misrad HaPnim (Population and Immigration Authority) | Teudat zehut and ספח. Appointment-only, often weeks out. |
| Week 1 | Ministry of Aliyah and Integration | Absorption basket and olim benefits |
| Weeks 1–2 | Health fund (Clalit, Maccabi, Meuhedet, Leumit) | You must choose one. Enrolment runs through Bituach Leumi or the absorption process. |
| Week 2 | Bituach Leumi | National insurance, benefits, health-insurance registration |
| Month 1 | Bank | The **branch** is the unit that matters |
| Month 1 | Municipality | Arnona, and arnona discounts for olim |
| As needed | Employment Service (לשכת התעסוקה / שירות התעסוקה) | Required for some benefits |
| As needed | Tax Authority | Self-employed, refunds, olim tax benefits |
| Ongoing | Kol Zchut | Not an office: the rights wiki that explains the offices, with an `עולים` hub page |

For each office worth saving, record:

- the **name people use** and the official name;
- what it actually does, in plain words;
- **languages of service**, and where they apply: the counter, or the phone
  line;
- **what to bring.** Counters turn people away over a missing ספח or original
  document.
- **a number that works from abroad.** 1-800 numbers and star codes do not; see
  the `israeli-phone-numbers` skill.

Never fill in hours or numbers from memory. Fetch them, or leave them blank and
say so.
