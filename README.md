# Israel Research Skills

A plugin of Israel-specific research and know-how skills for AI agents. It covers
rights and entitlements, civil defence, travel warnings, medicines, government
offices, phone numbers, opening hours, salaries and shopping.

Every skill is **instruction-only**. The skills need only the agent's own web
search and web fetch. They do not run local scripts, drive a browser or need an
MCP server. That is what lets the same plugin run on:

- **Claude** (Claude Code, and Claude apps that support plugins);
- **ChatGPT**, where Business and Enterprise workspaces can import
  Claude-format plugin marketplaces from GitHub.

The skills follow the [Agent Skills](https://agentskills.io) layout: one folder
per skill, a `SKILL.md` with `name` and `description` frontmatter, and bulky
reference data in that skill's own `references/` folder.

## Skills

| Skill | What it does | Derived from |
|---|---|---|
| `kol-zchut-rights` | Researches Israeli rights and entitlements on Kol Zchut, with Hebrew search terms by domain, the public MediaWiki API patterns, citation format, and when to escalate to gov.il or Bituach Leumi | `kol-zchut-lookup` (Claude-Israel-Agent-Skills-Plugin) |
| `home-front-command-guidelines` | Answers civil-defence questions from a bundled snapshot of the Home Front Command's English guidelines (22 pages, captured 2026-03-20), with source links | `home-front-command-guidelines` (Claude-Israel-Agent-Skills-Plugin) |
| `nsc-travel-warnings` | Finds the National Security Council's travel-warning level for a country, by web research | `nsc-travel-threat` (Claude-Israel-Agent-Skills-Plugin) |
| `israeli-medications` | Finds a medicine's registration, Israeli names and generics, basket status, health-fund price and leaflet, and the rules for carrying medication abroad | `drug-co-il-lookup`, `israel-drugs-registry-lookup`, `maccabi-medicine-lookup`, `medicine-availability-check` (Claude-Israel-Agent-Skills-Plugin); Israel-ADHD-Medication-Access research notes |
| `israeli-offices-guide` | Works out which office handles what, finds its details, reconciles conflicting hours, and gives a first-year checklist for new immigrants | `israeli-org-sources`, `olim-essential-contacts`, `reference/hebrew-vocabulary.md` (Israel-Phonebook-Manager) |
| `israeli-phone-numbers` | Explains number types, local and +972 formats, why 1-800 numbers and star codes fail from abroad, and the short codes | `israeli-phone-numbers`, `reference/numbering-plan.md` (Israel-Phonebook-Manager); Israel-Telephone-Numbering |
| `israel-opening-hours` | Turns Shabbat- and holiday-relative hours into clock times for a given city and date | `check-opening-hours`, `shabbat-anchors`, `easy-co-il-lookup` (Claude-Israel-Opening-Hours-Plugin) |
| `salary-conversion` | Converts monthly shekel salaries to annual foreign ones and back, plus plain price conversion | `salary-conversion` (Claude-Israel-Agent-Skills-Plugin); `convert-currency` (Claude-Israel-Shopping-Plugin) |
| `israel-price-check` | Checks local prices (Zap and `.il` retailers) against the international RRP, gives a markup verdict and a "freier check", and compares imports with buying locally | `rrp-check`, `freier-check`, `search-zap`, `tech-product-search`, `general-search`, `store-zap-lookup`, `docs/search-strategies.md`, `compare-to-local` (Claude-Israel-Shopping-Plugin) |
| `brand-and-part-number-check` | Identifies Israel-only brands (white-label or importer label) and maps local part numbers to international ones | `whats-this-brand`, `pn-check` (Claude-Israel-Shopping-Plugin) |
| `personal-import-tax` | Works out the VAT-free personal-import threshold, the cliff above it and landed cost, and finds items that land tax-free | `cart-vat-nudge`, `find-under-75`, `reference/israel-tax.md` (Aliexpress-Israel-Skills) |
| `israel-electrical-compatibility` | Checks plug type, voltage and frequency, and flags restricted import categories | `check-il-compatibility` (Aliexpress-Israel-Skills) |

Facts that go out of date carry the date they were checked. That covers VAT,
the import threshold, which sites block automated fetches, API endpoints, and
candle-lighting offsets. Each skill tells the agent to re-check before relying
on them.

## Install

### Claude Code

```
/plugin marketplace add danielrosehill/Israel-Research-Skills
/plugin install israel-research@israel-research
```

### ChatGPT (Business / Enterprise)

In *Admin console → Plugins → Marketplaces*, add this repository as a
marketplace source. The repo is a Claude-format marketplace with
`.claude-plugin/marketplace.json` and source `./`. Then set the plugin's
installation policy for your workspace.

## Not included

These were left out on purpose:

- Skills built around driving a browser or running local code.
- Bookings and submissions.
- Hebrew and RTL formatting (a separate RTL plugin).
- The Jewish calendar (a separate plugin).
- Things general-purpose assistants already do well, such as news and
  translation.

## Disclaimer

General information, not legal, medical, tax or safety advice. In an emergency,
follow the Home Front Command and call 100, 101 or 102.

## License

MIT
