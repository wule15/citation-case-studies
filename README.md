# AI Visibility Case Studies

AEO (Answer Engine Optimisation) audits of public industrial companies, showing
how AI answer engines see them, and where the gaps are.

I build and run these to a simple standard: **every finding is measured, and the
report says plainly what was not measured.** No invented numbers, no
screenshots-as-proof. Where a claim about a named company appears, it was read
from the primary source (its live robots.txt, its rendered pages, or a direct
query to the AI engine).

## Method

Each audit has two independent halves.

1. **Structural scan.** A custom engine fetches the site over HTTP, standing in
   for an AI crawler, and measures the signals those crawlers depend on: robots
   access for GPTBot / CCBot / PerplexityBot, Product schema (JSON-LD),
   HTML-versus-PDF product data, semantic authority, and entity metadata. It
   grades only real measured signals, and reports "unreachable" honestly rather
   than grading a page it could not read.
2. **Citation test.** The same market queries are run live across four AI engines
   (ChatGPT, Perplexity, Kimi, Gemini) to see who is actually named when an
   engineer asks for a supplier.

Keeping the two apart is the point. The recurring finding is that they are
largely independent: companies that are structurally invisible to a crawler are
often cited heavily anyway, because today's AI citation runs on third-party
sources rather than the companies' own sites.

## The case studies

- **[Emerson (Fisher control valves)](emerson-ai-visibility-audit.md)** — a
  single-company teardown. Emerson is cited as the benchmark across all four
  engines, but on third-party pages, because its own catalogue carries no
  machine-readable product schema. The gap is structural, not reputational.
- **[Bürkert (fluid control systems)](burkert-ai-visibility-audit.md)** — a
  single-company teardown. Crawlers are welcome and AI cites Bürkert in its niche,
  but a product-family page hides its specifications behind 35 PDF datasheets with
  no product schema, so the data an engine needs is the data it cannot read.
- **[Flow-control sector landscape](flow-control-sector-ai-readiness.md)** — a
  structural scan of 17 valve and flow-control makers and distributors, with a
  citation overlay. A third of the sector is unreachable to an AI crawler; one
  company blocks AI crawlers outright yet is still cited.

## Limits, stated up front

These read server-delivered HTML, not JavaScript-rendered pages, so a
single-page-app site can look thinner than it is to a human. The citation tests
are snapshots on a given day; AI answers move with time and phrasing. Both
reports say so in their own words.

---

Nikola Vukadin. Mechanical engineer and B2B technical content, working on AI
visibility for industrial companies. [github.com/wule15](https://github.com/wule15)
