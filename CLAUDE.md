# Israel-Research-Skills: agent notes

Public Claude plugin `israel-research`. It holds instruction-only skills for
Israel-specific research and know-how (rights, civil defence, travel warnings,
medicines, offices, phone numbers, opening hours, salaries, shopping). The
skills must work on both Claude and ChatGPT. Created 2026-10-16.

## Consumers

- **Claude:** installable directly. The repo is its own marketplace
  (`.claude-plugin/marketplace.json`, source `./`).
- **The household ChatGPT Business workspace.** The repo is vendored into
  `danielrosehill/Residence-Skills-Marketplace-ChatGPT` by
  `danielrosehill/Residence-Skills` → `skills/publish-to-chatgpt/scripts/publish.sh`,
  through its `EXTERNAL` map (`[israel-research]="danielrosehill/Israel-Research-Skills"`).
  - The script shallow-clones the pushed default branch.
  - It copies only `.claude-plugin/`, `skills/` and `README.md`. This repo's
    `marketplace.json` is dropped in the copy.
  - It upserts the plugin entry in the ChatGPT marketplace manifest.

  So: push here first, then run `publish.sh` from Residence-Skills. Do not edit
  the vendored copy or `publish.sh` from this repo.

## Invariants

- **Instruction-only.** No `.mcp.json`; ChatGPT would mark the plugin
  *Desktop only*. No scripts that a skill depends on. The skills assume only a
  web search tool and a web fetch or browsing tool.
- **ChatGPT cannot reach the maintainer's machine.** It cannot run local Python,
  Playwright or Chrome, or call a private MCP gateway. Any skill whose core
  needs those does not belong here.
- **Framework-agnostic, per the Agent Skills spec.**
  - Frontmatter `name` equals the folder name.
  - `description` says what the skill does and when to use it.
  - Refer to capabilities generically ("your web search tool"). Never use
    vendor tool names (`mcp__…`, `claude-in-chrome`, Playwright, Tavily).
- **Each skill is self-contained.** Bulky data goes in that skill's own
  `references/`, because only `skills/` is vendored. Cross-references to sibling
  skills are by name only, as optional hand-offs.
- **Date every time-sensitive fact,** with an absolute date. Say whether it was
  verified or inferred. That includes VAT, thresholds, fetchability, endpoints
  and the snapshot date. Re-verify when editing.
- **Public repo.** No personal identifiers, household addresses or credentials.
- **Out of scope:**
  - driving a browser or running local code;
  - bookings and submissions (Israel Post appointments, 106 reports, Netek
    cancellations);
  - RTL and Hebrew formatting (`danielrosehill/RTL-Conformity-Skills`);
  - the Jewish calendar (its own plugin);
  - things assistants do natively (news, translation).
- **Bump `version`** in both `.claude-plugin/plugin.json` and
  `.claude-plugin/marketplace.json` when skill content changes.

## Verification log (2026-10-16)

- **Kol Zchut.** The whole site is behind Cloudflare.
  - A browser User-Agent gets 200 on `/he/<article>`, `/w/he/api.php` (search,
    opensearch, parse), `/w/he/rest.php/v1/search/*` and `index.php?action=raw`.
  - curl's default UA, the bare `Mozilla/5.0` UA, and a cloud AI fetch tool get
    `403` "Just a moment…", even from an Israeli IP.
  - `robots.txt` disallows `/w/*/api.php` and `/w/*/index.php` for crawlers.
  - The English edition was removed 2023-02-02; `/en/*` redirects to a notice.
  - The Arabic and Russian APIs answer.

  Details: `skills/kol-zchut-rights/references/api.md`.
- **Import tax.** VAT is 18%. The personal-import threshold is $75 goods value
  from 2026-06-02, after $150 and $130 periods. There is a 72-hour rule for
  same-supplier split parcels.
  Source: `skills/personal-import-tax/references/israel-import-tax.md`.
- **gov.il and taxes.gov.il:** 403 Cloudflare. `taxes.gov.il` now redirects to
  gov.il.
- **Readable:** `btl.gov.il`, `iec.co.il`, `taasuka.gov.il`, `zap.co.il`
  search, and Hebcal's Shabbat API.
- **drug.co.il:** 503 to automated fetches.
- **Candle lighting.** Hebcal by GeoNames ID gave Jerusalem 17:26, Haifa 17:35
  and Tel Aviv 17:47, against a Jerusalem sunset of 18:06. This confirms the
  40, 30 and 20 minute customs.

## Sources the skills were derived from

- `danielrosehill/Claude-Israel-Agent-Skills-Plugin`
- `danielrosehill/Claude-Israel-Shopping-Plugin`
- local `ai-claude-plugins/`:
  - `Aliexpress-Israel-Skills`
  - `Israel-Phonebook-Manager`
  - `Claude-Israel-Opening-Hours-Plugin`
- `israel/Israel-Telephone-Numbering`
- `israel/Israel-ADHD-Medication-Access` (the general rules only, not the case)

The README maps each skill to its source.
