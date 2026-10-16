---
name: kol-zchut-rights
description: Research Israeli rights and entitlements on Kol Zchut (כל זכות, kolzchut.org.il), the plain-language rights wiki, and answer with cited article links. Use for any question of the form "what are my rights when…", "am I entitled to…", "what does Israeli law say about…" — employment (severance, notice, sick days, recuperation pay, overtime), National Insurance (Bituach Leumi) benefits, maternity and parental leave, reserve duty, tenancy, consumer cancellations, health basket, tax credits, olim and returning residents, disability, elderly, debts and enforcement. Covers Hebrew search terms by domain, the public MediaWiki API, how to cite, and when to escalate to gov.il or Bituach Leumi.
---

# Kol Zchut rights research

Kol Zchut (כל זכות, "All Rights") at `https://www.kolzchut.org.il` is a nonprofit
wiki that explains Israeli rights and entitlements in plain language. For any
question that hinges on Israeli law or benefits, it is the first source to check,
before general web results or memory. Each article states who is eligible, how to
claim, and links to the law and the responsible authority.

## Know what you are searching

- **Hebrew is the main edition and the one to use.** Search in Hebrew even when
  the user writes in English, then answer in the user's language.
- **There is no English edition.** It was removed on 2 February 2023, and
  `kolzchut.org.il/en/...` URLs now redirect to a Hebrew notice saying so
  (verified 2026-10-16). Do not send English speakers to `/en/`, and do not cite
  an old English page from a search cache as current.
- **Arabic (`/ar/`) and Russian (`/ru/`) editions exist** and have their own
  APIs. They cover fewer topics than Hebrew. Offer them to Arabic or Russian
  speakers, but check the Hebrew article for anything time-sensitive.
- **Not for:** case law, court procedure or a specific ruling. Kol Zchut
  summarises rights, not litigation. For that, point the user to Nevo or Takdin
  (paid legal databases) or to a lawyer.

## Workflow

1. **Translate the question into Hebrew terms.** Use the domain table in
   `references/hebrew-search-terms.md`. Most terms there are exact article
   titles, verified against the site on 2026-10-16. Prefer a specific term
   (`הודעה מוקדמת לפיטורים`) to a broad one (`עבודה`), because broad terms
   return portal pages.
2. **Find the article.** Try these in order and stop at the first that works:
   - **Web search** restricted to the site: `site:kolzchut.org.il <Hebrew terms>`.
     This works in every environment, and search snippets often already show
     the article title.
   - **The site's search API**, if your fetch tool can read it. It returns
     ranked titles with snippets as JSON. Patterns are in `references/api.md`.
   - **The article URL directly**, if you already know or can guess the title:
     `https://www.kolzchut.org.il/he/<title with spaces as underscores>`.
3. **Read the article before answering.** Do not answer substance from a
   snippet. If your fetch tool is blocked (see "When fetching fails"), say that
   you are working from search snippets, and give the user the link.
4. **Answer from the article.**
   - Lead with the direct answer: entitled or not, how much, how long.
   - Give the conditions that decide eligibility.
   - Give the steps to claim and who handles it.
   - Quote figures exactly as the article states them, including the date they
     apply from. Kol Zchut updates amounts such as minimum wage, benefit rates
     and the reserve-duty compensation floor when they change, and old figures
     linger elsewhere on the web.
5. **Cite.** See the citing section below.

## Reading an article

Articles share a structure, so you can go straight to the part you need:

| Section (Hebrew) | What it holds |
|---|---|
| Summary box at the top (`תקציר`) | One-paragraph answer |
| `מי זכאי` / `תנאים` | Eligibility conditions |
| `כיצד מממשים את הזכות` | How to claim: forms, deadlines, which office |
| `גורמים מסייעים` | Who can help: government call centres, aid organisations, the responsible authority |
| `מקורות משפטיים ורשמיים` / `חקיקה ונהלים` | The statute, regulations and official circulars |
| `פסקי דין` | Selected rulings |
| `זכותון ...` pages | Rights digests: a whole topic on one page, for example domestic workers or personal imports. Good for overview questions. |

Portal pages (`פורטל`) list every article in a domain. Use one when the user's
situation does not match a single article. For example, the `עולים` page
is the right starting point for a new immigrant.

## Citing

Give the article title in Hebrew, with an English gloss, and its full URL. Add
the last-updated date if you can see it. The footer of each article shows
`עודכן לאחרונה ב־<date>`, and the API returns `touched`.

```
Source: Kol Zchut — "פיצויי פיטורים" (Severance pay)
https://www.kolzchut.org.il/he/פיצויי_פיטורים  (last updated <date>)
```

Some chat surfaces break Hebrew URLs. If that happens, use the percent-encoded
form, which the search API returns as `fullurl`, or which you can build by
URL-encoding the title. When several articles are relevant, cite each one next
to the claim it supports.

## When to escalate to an official source

Kol Zchut is secondary and says so: its footer states that binding rights come
from statute, regulations and court rulings. Go to the primary source, and tell
the user you did, when:

- **The user is about to act on a number.** Benefit amounts, contribution rates
  and thresholds come from National Insurance (`btl.gov.il`), the Tax Authority
  (`taxes.gov.il`) or the relevant ministry page on `gov.il`. Each Kol Zchut
  article links to the responsible body under `גורמים מסייעים`.
- **The article is visibly stale**, or the topic changed recently. This is
  common for wartime arrangements such as `חרבות ברזל` benefits, which are often
  temporary and extended by order.
- **A deadline or a claim decision matters**, such as an appeal window, a
  medical committee (`ועדה רפואית`) or a dismissal hearing (`שימוע`).
- **The question is about one specific case** (a dismissal, an eviction, a
  benefit refusal). Give the rights from Kol Zchut and the relevant aid
  organisation from `גורמים מסייעים`. Mention free legal aid (`סיוע משפטי חינם`)
  where it applies.

`btl.gov.il` usually fetches cleanly. `www.gov.il` blocks most automated
fetches with a Cloudflare challenge. `taxes.gov.il` now redirects there
too (checked 2026-10-16). When a page is blocked, give the user the link,
or ask them to paste the page, rather than retrying.

## When fetching fails

The whole site sits behind Cloudflare. As tested from an Israeli IP on
2026-10-16:

- Requests that look like a browser got through: articles, `api.php` and
  `rest.php` all returned content.
- Requests with a generic or bot User-Agent got `403` and a "Just a moment…"
  page. That covered plain `curl` and one AI fetch tool.
- `robots.txt` disallows `/w/*/api.php` and `/w/*/index.php` for crawlers,
  but allows article paths (`/he/`, `/ar/`, `/ru/`).

So your fetch tool may be refused even though the site is up. If it is:

1. Rely on `site:kolzchut.org.il` web search. Snippets and titles still
   identify the right article.
2. Try the article URL once in a real browsing tool, if you have one.
3. Give the user the article link, and say you could not open the full text.

Do not loop on a refused URL.

## Answer hygiene

- Never invent an article title or URL. If search finds nothing, say so, and
  suggest the user search the site directly:
  `https://www.kolzchut.org.il/he/מיוחד:חיפוש?search=<terms>`.
- Keep Hebrew legal terms next to their English gloss, for example "recuperation
  pay (דמי הבראה)". The user will meet the Hebrew term on forms and payslips.
- Close every answer about a specific case with exactly this line:
  *Kol Zchut is general information, not legal advice. For a specific case, check with a lawyer or the responsible authority.*
