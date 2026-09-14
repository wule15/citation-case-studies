# AI Visibility Audit
**Bürkert (fluid control systems)**
**Domain:** burkert.com
*Conducted: 2026-08-11*
*By: citAtIon*

Built entirely from public observation of burkert.com and public AI-engine
queries. No client data, no insider information.

---

## Scope

Two independent halves, the same method used across these case studies. A
**structural** scan, whether an AI crawler can reach Bürkert's content, read its
product data, and recognise it as an entity, measured live over HTTP. And a
**citation** test, whether AI engines actually name Bürkert when an engineer asks
for a supplier, run live against four engines. Every figure is measured.

---

## Summary

Bürkert is a recognisable fluid-control brand, and AI engines cite it in its
niche. The front door is open: robots.txt blocks no AI crawler. But the product
layer is where an AI procurement tool would struggle. On the pages scanned there
is no machine-readable Product schema, and a single product family page links
**35 separate PDF datasheets**, which is exactly where specifications go to be
invisible to a machine.

So Bürkert sits in the same place as much of this sector: the reputation is real
and AI-cited, while the site gives an engine prose and PDFs rather than
structured facts. It grades a **D** on structure.

---

## The 3-Test result

| Test | Result | Detail |
|---|---|---|
| **1. Crawler access** | ✅ OPEN | robots.txt is 4.7 KB and names no AI crawler in a block. GPTBot, CCBot, PerplexityBot and the rest are free to crawl. |
| **2. AI citation** | ✅ CITED (in its niche) | Named for control and solenoid valves by two of the four engines tested, and listed as a fluid-control manufacturer to buy from directly. Cited on reputation, not on its own structured data. |
| **3. Content structure** | ⚠️ PDF-HEAVY | No JSON-LD Product schema on the pages scanned. A product-family page carries 35 PDF datasheet links and no Open Graph tags. Specs are human-readable, not machine-readable. |

---

## Test 1: Crawler access (verified)

Bürkert's robots.txt was read directly: 4.7 KB, and it names no AI crawler in a
Disallow. GPTBot, CCBot, ClaudeBot, PerplexityBot and Google-Extended are all
free to crawl. This is the right posture, and it is not universal in this sector,
some manufacturers block AI crawlers outright. Bürkert does not.

**Result: OPEN. No action needed.**

---

## Test 2: AI citation (measured)

Procurement queries were run live across four engines, ChatGPT, Perplexity, Kimi
and Gemini, on 2026-08-11.

- **Control valve suppliers.** Bürkert was named by two of the four engines,
  placed mid-list, and described as a specialist in process and solenoid control
  valves for precision, hygienic and analytical applications.
- **Distributors and direct purchase.** One engine listed Bürkert among the
  manufacturer-direct options an engineer can buy from, pointing at its e-shop.
- **Actuators.** Bürkert did not appear, correctly, it is not primarily an
  actuator maker. The engines placed it where it belongs.

The pattern is consistent with the rest of these audits: the engines name Bürkert
from third-party market summaries and directories, not from Bürkert's own
structured data. The reputation is doing the work.

**Result: CITED in its fluid-control niche, on reputation. Accurate, but not
anchored to Bürkert's own machine-readable data.**

---

## Test 3: Content structure (verified)

Two pages were read directly: the products landing page and a product-family
(type) page.

- The products landing page carries Open Graph tags and some JSON-LD, but **none
  of it is Product schema**. It is site-level markup (organisation, breadcrumb),
  not product data an engine can turn into facts.
- The product-family page is worse for a machine: **no Open Graph tags at all**,
  no Product schema, and **35 links to PDF datasheets**. The specifications an
  engineer needs, pressure, media, materials, Kv, live inside those PDFs.

PDFs are the classic AI-visibility trap. A human downloads and reads them; an AI
crawler indexing the page sees a list of links, not a spec table. So the exact
data that would let a tool answer "which Bürkert valve fits this service" is the
data an engine cannot read.

**Result: PDF-heavy. Rich documentation, but not machine-readable at the point
it matters.**

---

## Root cause

Bürkert has the reputation and the open door. What it does not have, on the pages
scanned, is a machine-readable product layer. The specification data exists, in
PDFs and in the page for a human, but not in the JSON-LD Product schema an AI
procurement engine reads. This is the cheaper half of AI readiness left undone,
sitting on top of the expensive half, brand and authority, that is already there.

---

## Priority fixes

1. **Lift the key specs out of the datasheet PDFs into HTML, with Product
   JSON-LD.** Not delete the PDFs, add an HTML spec table beside them and mark it
   up. That single change turns a page a crawler skims into a page it can quote.
2. **Add Open Graph tags to the deep product pages.** The landing page has them,
   the product-family page does not, so the pages that matter most for a specific
   query are the ones an engine can least categorise.
3. **Re-run the citation test after the markup work.** Bürkert is already cited on
   reputation, this measures whether the engines start citing burkert.com directly
   for the specs, rather than a directory.

---

## What is not in this audit

- **Two pages, not the whole catalogue.** The products landing and one
  product-family page were read. The schema and PDF findings were consistent
  across both, but a full-site census was not run.
- **Citation is a snapshot.** Four engines on one day (2026-08-11). AI answers
  move with time and phrasing.
- **No JavaScript rendering.** Signals were read from server-delivered HTML, so
  anything Bürkert injects client-side after load would not be counted here.

---

*citAtIon. AI Visibility for Industrial B2B.*
*nikola@getcitation.org*
