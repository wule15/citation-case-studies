# AI Readiness of the Industrial Flow-Control Sector
**A structural scan of 17 manufacturers and distributors, with a live AI-citation overlay**
*Structural scan: 2026-08-10. Citation test: 2026-08-11.*
*By: citAtIon*

---

## What this is, and what it is not

This is a structural scan. It measures whether an automated engine, standing in
for an AI crawler like GPTBot or PerplexityBot, can reach a company's content,
read its product data, and recognise it as an entity. It runs over HTTP against
the live sites, and every figure below is measured, not estimated.

The structural scan is the core of this report. A second, separate axis, whether
ChatGPT, Perplexity, Kimi and Gemini actually *name* these companies when an
engineer asks for a supplier, was measured afterwards and is reported in its own
section ("The citation axis") near the end. The two are kept apart on purpose,
because the finding is that they are largely independent: several companies that
are structurally unreachable to a crawler are nonetheless cited heavily, and at
least one that blocks AI crawlers outright is still cited. A company can be
perfectly crawlable and uncited, or cited on reputation while its site scores
poorly.

The value of the structural axis is that it is the half a company controls
directly. Reputation is slow to move. robots.txt, schema and page structure can
be fixed in weeks. And as the citation section shows, the reputation companies
currently rely on is mediated by third parties, not their own sites, which is
exactly the exposure the structural work addresses.

---

## The method

Each site is scanned for the signals an AI crawler depends on:

1. **Crawler access.** Does robots.txt allow AI crawlers, or Disallow them? Read
   from the live robots.txt.
2. **Entity metadata.** Are Open Graph tags present, so an AI platform can
   categorise the company as an entity?
3. **Semantic authority.** Does the reachable content carry the technical density
   an AI procurement engine expects, or is it thin?
4. **Product schema.** Is structured Product data (JSON-LD) present on the pages
   the crawler reaches from the homepage?

A grade from A to E follows from how many of these fail. The scan reaches the
homepage plus a few technical sub-pages, so the schema signal reflects what a
crawler finds within a few clicks of the front door, not a full-site census.
That limit matters and is called out where it changes the reading.

---

## Headline finding: a third of the sector is unreachable to an AI crawler

Of 17 sites scanned, 6 could not be scanned at all. Not because they scored
badly, but because an automated request never reached real content:

| Company | Why unreachable |
|---|---|
| Samson | Apex is a country selector; locale pages refuse automated requests |
| Parker | Automated requests refused or served no content |
| IMI | Automated requests refused or served no content |
| RS | Apex serves a JavaScript shell with little crawlable text |
| Digi-Key | Automated requests refused |
| Mouser | Automated requests refused |

This is itself the most important result. A site that refuses or starves an
automated crawler is, to a first approximation, refusing the AI engines that now
sit between a buyer and a shortlist. Whether that is a deliberate bot policy or a
JavaScript-heavy build that never renders for a crawler, the effect on AI
visibility is the same: the crawler leaves with nothing.

Two cases are explicit and verified rather than incidental:

- **Flowserve actively blocks AI crawlers.** Its robots.txt carries an explicit
  `Disallow: /` for GPTBot, CCBot, ClaudeBot, Google-Extended, Applebot-Extended,
  Amazonbot and Bytespider. This is a policy choice, and it removes Flowserve
  from every AI engine that honours robots.txt.
- **Reichelt blocks Common Crawl.** Its robots.txt carries an explicit
  `Disallow: /` for CCBot, but not for GPTBot or PerplexityBot. The distinction
  matters: CCBot feeds training corpora, so blocking it limits how much of
  Reichelt ends up in the models, while leaving the live retrieval crawlers a
  path in. It is a narrower block than Flowserve's, and probably a more
  deliberate one.

---

## The companies that do scan

Eleven sites returned gradeable content. The grade reflects the structural
signals only.

| Company | Grade | Crawler access | Entity (OG) | Authority | Product schema (pages scanned) |
|---|---|---|---|---|---|
| Emerson (Fisher) | C | Open | Present | Strong | Not found within reach of homepage |
| GEMÜ | C | Open | Present | Strong | Not found within reach of homepage |
| Metso | C | Open | Present | Solid | Not found within reach of homepage |
| Swagelok | C | Open | Present | Solid | Not found within reach of homepage |
| Bürkert | D | Open | Present | Moderate | Not found within reach of homepage |
| Danfoss | D | Open | Present | Weak | Not found within reach of homepage |
| Spirax Sarco | D | Open | Present | Weak | Not found within reach of homepage |
| Alfa Laval | D | Open | **Missing** | Weak | Not found within reach of homepage |
| Conrad | D | Open | **Missing** | Weak | Not found within reach of homepage |
| Reichelt | E | **Blocks CCBot** | Not verified | Weak | Not found within reach of homepage |

Notes on reading this table:

- **Crawler access "Open"** means robots.txt did not block AI crawlers. It does
  not mean the whole site renders without JavaScript.
- **Reichelt** blocks CCBot, Common Crawl's crawler, with an explicit
  `Disallow: /` in its robots.txt, read directly and verified. It does not block
  GPTBot or PerplexityBot; only CCBot is named. Its front end is bot-defended and
  answered some automated requests with a 503 rather than a page, so its entity
  metadata could not be read reliably and is left unverified. It grades E on the
  combination of the CCBot block, weak authority and no product schema found.
- **Product schema "Not found within reach of homepage"** reflects two different
  causes, and the scan alone does not separate them. Some sites publish schema
  deeper than the crawl reaches. Others carry none at all. Emerson was checked by
  hand to see which: its Fisher final-control catalogue pages carry no JSON-LD
  block at all, and the word "Product" appears only inside client-side
  JavaScript, which an AI crawler does not read as structured data. So for
  Emerson this is a genuine absence of machine-readable product schema, not a
  depth artifact. For others in the table the cause is not separated here, and
  the honest reading is "no product schema was found near the front door."

---

## What the pattern says

Three things stand out across the sector.

**AI-readiness is not the same as market size.** Some of the largest names here
grade in the C to D band or cannot be scanned at all. The structural work of
being readable by an AI crawler is unrelated to revenue, and the leaders on this
axis are not always the leaders in the market.

**Entity metadata is uneven.** Most sites carry Open Graph tags, but Alfa Laval
and Conrad do not, on the pages scanned. Without them an AI platform has a weaker
basis for categorising the company as an entity.

**Product schema sits too deep.** Across the sector, structured product data was
rarely within a few clicks of the homepage. Where it exists, it is buried in
deep catalogue pages that a crawler entering at the top may never reach. For AI
procurement tools that want SKU-level facts, that depth is a real barrier.

---

## The citation axis: what AI actually names

Separately from the structural scan, four AI engines, ChatGPT, Perplexity, Kimi
and Gemini, were each asked, on 2026-08-11, to name the top control-valve
suppliers, the top valve-actuator manufacturers, and the online distributors of
fluid-control components in Europe. This measures reputation, the other half of
AI visibility. The result, set against the structural grades above, is the most
useful finding in this report.

**Reputation and structure are largely independent.** The companies AI cites most
are often the ones a crawler cannot read at all:

| Company | Structural scan | AI citation (4 engines) |
|---|---|---|
| Samson | Unreachable (selector/bot) | Cited as a top-3 control-valve name; strong |
| IMI | Unreachable | Cited for control valves and actuators |
| Parker | Unreachable | Cited for actuators |
| Festo | Bot-blocked (403) | Cited for pneumatic actuators |
| Flowserve | Grade E, blocks AI crawlers | Cited for control valves and actuators |
| Emerson (Fisher) | Grade C, no product schema | Cited as the benchmark, all four engines |
| RS (distributor) | Unreachable (JS shell) | Cited as a top distributor, every engine |

**Why this happens.** When the engines name these companies, they are quoting
third-party sources, market-research summaries, buyer-guide directories, industry
listicles, not the companies' own sites. Two of the four engines that cited
Emerson linked emerson.com, and even then landed on a brand page and a PDF, not
on structured product data. So today's AI citation runs on other people's pages
about these companies, not on what the companies publish themselves.

**Why it still matters, and where the exposure is.** Relying on third-party
citation is fragile. It is uncontrolled, it carries the phrasing and errors of
whoever wrote the directory, and it breaks down as AI shifts toward first-party
structured data and live retrieval. The company that makes its own site the
machine-readable source of truth stops depending on someone else's summary. That
is the whole point of the structural work: not to *create* a reputation AI
already grants these names, but to *own* it.

**Two engine-specific notes, for honesty.** For the "European suppliers" query,
ChatGPT and Perplexity included Emerson and Flowserve (noting they are
US-headquartered), while Kimi and Gemini applied a stricter European-only filter
and dropped them from the ranked list. And for distributors, the four electronics
specialists in the structural table, Digi-Key, Mouser, Conrad and Reichelt, were
**not** named for fluid-control at all. That is a category-fit gap: AI does not
consider them valve distributors, so their AI visibility for this sector is a
positioning question, not only a structural one. RS and the former Distrelec (now
folded into RS Group, which the engines state) were the distributors named.

---

## Limits of this scan, stated plainly

- **The citation data is a snapshot.** Three queries across four engines on a
  single day. AI answers move with time and phrasing, so treat the citation axis
  as a baseline, not a fixed ranking.
- **No JavaScript rendering.** The engine reads server-delivered HTML. Sites that
  render their content client-side look thinner to it than they are to a human
  with a browser, and some read as unreachable for that reason alone.
- **Schema is a near-the-door signal, not a census.** See the note above.
- **Two robots.txt readings differ in strength.** Flowserve's AI block is read
  directly and verified. The "unreachable" verdicts are honest about the fact
  that content was not reached, without claiming to know exactly why.

---

*citAtIon. AI Visibility for Industrial B2B.*
*nikola@getcitation.org*
