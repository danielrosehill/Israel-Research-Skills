# Kol Zchut — public MediaWiki API

Kol Zchut runs on MediaWiki. Each language edition has its own API base:

| Edition | Action API | REST API |
|---|---|---|
| Hebrew (main) | `https://www.kolzchut.org.il/w/he/api.php` | `https://www.kolzchut.org.il/w/he/rest.php/v1/` |
| Arabic | `https://www.kolzchut.org.il/w/ar/api.php` | `…/w/ar/rest.php/v1/` |
| Russian | `https://www.kolzchut.org.il/w/ru/api.php` | `…/w/ru/rest.php/v1/` |

There is no English edition. It was removed on 2023-02-02. `https://www.kolzchut.org.il/w/api.php`,
with no language segment, returns 404.

Everything below is a plain `GET` with no key. URL-encode the query parameters.

## Verification record — 2026-10-16

Tested with `curl` from an Israeli residential IP, and with one AI web-fetch tool
running in the cloud:

| Request | Browser User-Agent | `curl` default UA | AI fetch tool |
|---|---|---|---|
| `/w/he/api.php?action=query&list=search…` | 200 JSON | 403 Cloudflare "Just a moment…" | 403 |
| `/w/he/api.php?action=opensearch…` | 200 JSON | 403 | not tested |
| `/w/he/api.php?action=parse…` | 200 JSON | 403 | not tested |
| `/w/he/rest.php/v1/search/page…` | 200 JSON | 403 | not tested |
| `/he/<article>` | 200 HTML | 403 | 403 |
| `/w/he/index.php?title=<t>&action=raw` | 200 wikitext | 403 | not tested |
| `/robots.txt`, `/sitemap.xml` | 200 | 200 | — |

A full browser User-Agent string got through. The bare UA `Mozilla/5.0` and
curl's default UA did not. The result did not depend on the IP: an Israeli IP
was refused when the UA looked automated. `robots.txt` asks crawlers not to
fetch `/w/*/api.php` or `/w/*/index.php`, and allows article paths. Expect some
agent fetch tools to be refused either way, so the skill treats the API as
optional.

## Full-text search (best for questions)

```
https://www.kolzchut.org.il/w/he/api.php?action=query&list=search&srsearch=<QUERY>&srlimit=8&srprop=snippet&format=json&formatversion=2
```

The response shape (verified with `srsearch=פיצויי פיטורים`, which returned
`totalhits: 573`):

```json
{"query":{"searchinfo":{"totalhits":573},
  "search":[{"ns":0,"title":"פיצויי פיטורים","pageid":10359,
             "snippet":"האם אתם זכאים <span class=\"searchmatch\">לפיצויי</span> …"}]},
 "continue":{"sroffset":8}}
```

Strip the `<span class="searchmatch">` tags from the snippet. To build the
article URL, replace the spaces in `title` with underscores:
`https://www.kolzchut.org.il/he/<title>`. Page further with `&sroffset=N`.

The REST equivalent returns cleaner JSON, with `key` already in URL form:

```
https://www.kolzchut.org.il/w/he/rest.php/v1/search/page?q=<QUERY>&limit=5
→ {"pages":[{"id":10359,"key":"פיצויי_פיטורים","title":"פיצויי פיטורים","excerpt":"…"}]}
```

## Title suggestions (fast, for short terms)

```
https://www.kolzchut.org.il/w/he/api.php?action=opensearch&search=<QUERY>&limit=8&format=json
→ ["<query>", [titles…], [descriptions — usually empty], [full percent-encoded URLs…]]
```

REST: `…/w/he/rest.php/v1/search/title?q=<QUERY>&limit=5`.

## Reading an article

| Need | URL |
|---|---|
| Section list | `…/api.php?action=parse&page=<TITLE>&prop=sections&format=json` |
| One section's wikitext | `…/api.php?action=parse&page=<TITLE>&prop=wikitext&section=<N>&format=json&formatversion=2` |
| Whole article as wikitext | `https://www.kolzchut.org.il/w/he/index.php?title=<TITLE>&action=raw` |
| Rendered HTML | `…/api.php?action=parse&page=<TITLE>&prop=text&format=json` |
| Last edit and canonical URL | `…/api.php?action=query&prop=info|revisions&rvprop=timestamp&inprop=url&titles=<TITLE>&format=json&formatversion=2` → `fullurl`, `touched`, `revisions[0].timestamp` |

Wikitext is the most compact to read. Templates such as `{{תקציר|…}}` hold
the summary box, and `[[link|text]]` gives the related-article titles to follow.

Section numbers are not stable: transcluded sections are listed with indexes
such as `T-1`. Always fetch the section list first. Never hard-code a section
number.

## Human-facing search page (fallback to give the user)

```
https://www.kolzchut.org.il/he/מיוחד:חיפוש?search=<QUERY>&fulltext=1
```

Without `fulltext=1`, a query that exactly matches a title redirects straight
to that article.
