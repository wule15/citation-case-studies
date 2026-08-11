# AI Visibility Audit
**Emerson (Fisher control valves and final-control)**
**Domain:** emerson.com
*Conducted: 2026-08-10*
*By: citAtIon*

---

## Scope of this audit

This audit covers the **structural** half of AI visibility: whether an AI
crawler can reach Emerson's content, read its product data, and recognise the
company as an entity. Every figure below is measured live over HTTP.

The **citation** half, whether ChatGPT, Perplexity, Kimi and Gemini actually name
Emerson or Fisher when an engineer asks for a control-valve supplier, was run live
and is reported in Test 2. It is measured, not guessed, because a fabricated
citation result is worse than an honest gap.

---

## Summary

Emerson scores in the middle band, a **Grade C**. The infrastructure is sound:
AI crawlers are allowed, the company is recognisable as an entity, and the
content is technically dense. The single structural gap is the one that matters
most for an AI procurement tool: there is no machine-readable product schema, so
an AI engine can find Emerson but cannot read the specifics of a Fisher valve in
a form it trusts.

For a market leader in control valves, the risk is specific. When an AI tool
answers "what actuator suits this service," it reaches for sources it can parse
into facts. Emerson's facts are on the page for a human, but not structured for
a machine.

The live citation test (Test 2, below) confirms this reading. Across four AI
engines, Emerson and Fisher are cited as the benchmark for both control valves
and actuators. So the reputation is strong and the gap is not that AI ignores
Emerson. The gap is that AI cites Emerson on the strength of third-party sources,
while Emerson's own site gives the engines nothing machine-readable to quote. As
AI procurement tools move toward first-party structured data, that is the exposure.

---

## The 3-Test result

| Test | Result | Detail |
|---|---|---|
| **1. Crawler access** | ✅ OPEN | robots.txt is 611 bytes and carries no block against GPTBot, CCBot, ClaudeBot, Perplexity or Google-Extended. AI crawlers are free to index the site. |
| **2. AI citation** | ✅ CITED (strong) | Named as the benchmark control-valve and actuator supplier across all four engines tested (ChatGPT, Perplexity, Kimi, Gemini). Emerson.com cited directly for the Fisher brand. |
| **3. Content structure** | ⚠️ MIXED | Content is rich HTML, but no JSON-LD product schema was found, including on the Fisher final-control catalogue pages. Product data is human-readable, not machine-readable. |

---

## Test 1: Crawler access (verified)

Emerson's robots.txt was read directly. It is short, 611 bytes, and contains no
user-agent block against any AI crawler. GPTBot, CCBot, ClaudeBot,
PerplexityBot and Google-Extended are all free to crawl.

This is the right posture and it is worth stating clearly, because it is not
universal in this sector. In a scan of the wider field, Flowserve was found to
block every major AI crawler outright in its robots.txt. Emerson does not. The
front door is open.

**Result: OPEN. No action needed.**

---

## Test 2: AI citation (measured)

Three procurement queries were run live across four AI engines, ChatGPT,
Perplexity, Kimi and Gemini, on 2026-08-11. The question is whether Emerson or
Fisher is actually named.

**Control valve suppliers.** Emerson/Fisher was named #1 by ChatGPT ("the default
benchmark for process control valves") and top-three by Perplexity. The two
engines that read the query as strictly European-headquartered (Kimi and Gemini)
excluded Emerson from the ranked list but named it explicitly as "frequently
recommended, though US-headquartered." So the citation is strong, and the only
thing that drops it is a geography filter, not a visibility failure.

**Valve actuators.** Emerson was named top-tier by all four engines, via Bettis,
EIM, Fisher and Biffi. First or second on every list.

**Who makes Fisher.** All four engines correctly identified Fisher as an Emerson
brand, and two of them cited **emerson.com directly** (the Fisher brand page and
a Fisher document). Emerson was positioned as the benchmark the competitor set is
measured against.

**The important nuance.** When the engines affirm Emerson, they lean on
third-party market reports and directories, and the two times they cited
emerson.com they landed on the brand page and a PDF, not on structured product
data. So AI can confirm the *entity* ("Emerson makes Fisher valves") but still
cannot pull *SKU-level facts* from Emerson's own site, because that machine
readable layer is missing (Test 3). The reputation is doing the work the site
should be doing.

**Result: CITED, strongly, across all four engines. The gap is structural, not
reputational.**

---

## Test 3: Content structure (verified)

Three pages were read directly: the corporate homepage, the Final Control
landing page, and the Actuators catalogue page.

- The pages are large and content-rich, 425 KB to 500 KB of HTML each.
- Open Graph entity tags are present on the corporate and product pages.
- The technical density is high. The content clears the authority threshold
  comfortably.
- **No JSON-LD structured data is present on any of the three pages.** On the
  Actuators catalogue page the word "Product" appears only inside client-side
  JavaScript, not in a schema block an AI crawler reads as structured product
  data.

The consequence is precise. An AI engine crawling Emerson learns that the
company exists, works in automation and final control, and writes with
authority. It does **not** get a structured record it can turn into "this
actuator, this pressure rating, this size." That is the SKU-level layer AI
procurement tools depend on, and it is missing.

**Result: MIXED. Rich content, no machine-readable product schema.**

---

## Root cause

Emerson has done the hard, slow parts of AI readiness. The domain is open to
crawlers, the brand is a recognisable entity, and the writing carries genuine
technical weight. What is missing is the cheap, fast part: wrapping the product
data that is already on the page in JSON-LD Product schema, so a machine can read
the same facts a human already can.

This is a better position to be in than the reverse. A company with schema but
no authority has to earn trust it cannot fake. Emerson has the trust and is
missing a markup layer.

---

## Priority fixes

1. **Add Product JSON-LD schema to the Fisher catalogue pages.** The data is
   already rendered for humans. Wrapping model number, pressure class, size range
   and material in schema makes it readable by AI engines. This is the single
   highest-leverage change and closes the one structural gap.
2. **Re-run the citation test after the schema work, against this baseline.** The
   baseline is set (Test 2): Emerson is already cited as the benchmark across four
   engines, but on third-party sources rather than its own data. Re-measuring
   later shows whether the schema work shifts the engines toward citing
   emerson.com directly for product facts.
3. **Verify schema reaches the deep catalogue, not just flagship pages.** Emerson
   has a large catalogue several clicks below the homepage. Schema needs to reach
   the product pages a crawler lands on, not only the top-level category pages.

---

## Outbound opener (draft)

Short, specific, and built on one verified finding. Not sent, provided as the
sales artifact that follows the audit.

> Subject: Fisher valves are readable by engineers, not by AI
>
> Hi [name],
>
> Quick observation from an AI-visibility scan of emerson.com. Good news first:
> across ChatGPT, Perplexity, Kimi and Gemini, Fisher is named as the benchmark
> control-valve brand. The catch is where that comes from. The engines are
> quoting market reports and directories, not emerson.com, because your catalogue
> pages carry no JSON-LD product schema. So when a tool tries to pull an
> actuator's pressure class or size, it finds prose it cannot parse into facts,
> and it cites someone else's page about you instead of yours.
>
> Competitors who add that markup first become the ones these tools quote from
> directly. It is a markup change on data you already publish, not a content
> project.
>
> If it is useful, I can show the exact pages and the schema they are missing.
>
> [signature]

---

## What is not in this audit

- **Citation test is a snapshot, not a tracking study.** Test 2 was three queries
  across four engines on one day (2026-08-11). AI answers shift over time and with
  phrasing, so it is a baseline, not a permanent ranking.
- **No JavaScript rendering.** Signals were read from server-delivered HTML. If
  Emerson injects schema client-side after load, this scan would not see it, and
  that possibility is left open rather than ruled out.
- **Three pages, not the whole site.** The corporate, Final Control and Actuators
  pages were read. The schema gap was consistent across all three, but a full
  catalogue census was not run.

---

*citAtIon. AI Visibility for Industrial B2B.*
*nikola@getcitation.org*
