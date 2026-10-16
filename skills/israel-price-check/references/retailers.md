# Israeli retailers and URL patterns

These URL patterns are the last ones known to work, not a guarantee. If one
redirects to the homepage, fall back to `site:<domain>` web search.

## Zap — price-comparison aggregator

| Purpose | URL |
|---|---|
| Keyword search | `https://www.zap.co.il/search.aspx?keyword=<URL-encoded Hebrew query>` |
| Model page (vendor price table) | `https://www.zap.co.il/model.aspx?modelid=<id>` |
| Category browse | `https://www.zap.co.il/models.aspx?sog=<category>` |
| Store profile (rating, reviews) | `https://www.zap.co.il/shop.aspx?sog=shop-<id>` |

On 2026-10-16 the keyword search returned a normal results page to a fetch with
a browser User-Agent. It may still bot-check other clients.

To vet an unfamiliar shop, search `site:zap.co.il "<store name>"`, open its
`shop.aspx` profile, and read the rating and review count. No Zap profile is a
weak signal, not a verdict.

## Major consumer-tech chains

| Retailer | Search URL | Notes |
|---|---|---|
| Ivory | `https://www.ivory.co.il/catalog.php?act=cat&q=<Hebrew>` | Usually readable |
| KSP | `https://ksp.co.il/web/cat/?search=<Hebrew>` | Bot-protected. Shows **regular** and **Eilat** prices; quote the regular one. |
| Bug | `https://www.bug.co.il/` (search box) | Bot-protected, and its search URL changes |
| TMS | `https://tms.co.il/index.php?route=product/search&search=<Hebrew>` | Usually readable |

## Broader retail

| Retailer | Best for |
|---|---|
| Ace | Hardware, tools, garden, some electronics |
| Home Center | Home improvement, appliances, fixtures |
| Office Depot | Office supplies, tech accessories |
| Audioline | Audio |

For niche categories, such as tactical, lighting, photography or smart home,
search `<Hebrew term> <brand> site:il` and use whichever specialist shops come
up.

## Search patterns

- `"<brand model>" site:il`: anyone in Israel selling it. Quote the model.
- `"<brand model>" site:co.il`: commercial sites only, when the first is noisy.
- `<brand model> site:<retailer domain>`: search-engine indexes of a retailer
  often beat the retailer's own search.
- Google Shopping with Israel locale: `https://www.google.com/search?tbm=shop&gl=il&hl=he&q=<Hebrew query>`.
  Its coverage is patchy.
- A retailer with no results: retry with a Hebrew synonym, then with brand and
  model only.
