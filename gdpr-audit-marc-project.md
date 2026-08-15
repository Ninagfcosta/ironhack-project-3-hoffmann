# GDPR Audit — Teammate's Project

**Prepared by:** Janaina Hoffmann
**Project audited:** VR Competitive Intelligence Copilot
**Built by:** Marc Tanguy (teammate, Project 3)
**Source documents:** `SYSTEM_BRIEF.md`, `DATA_PROCESSING_BRIEF.md` (provided by Marc)

*Disclaimer: this is a first-pass audit for coursework purposes, not a legal opinion.*

---

## 1. System summary (plain description)

A person asks a question in Slack (e.g. "compare OTA integrations across
Lodgify, Guesty and Hospitable"). The system extracts companies/topics with an
LLM, searches a local vendor-documentation corpus, scrapes the live web
(vendor pages, pricing, changelogs, and public review sites: G2, Capterra,
Trustpilot, Reddit), asks an LLM to write a comparison report, and publishes it
automatically to Notion with a link posted back in Slack. **No human reviews
the report before publication.**

---

## 2. Phase 1 — Personal data inventory

| Data category | Source | Purpose(s) | Retention | Crosses EU border? |
|---|---|---|---|---|
| Review text written by identifiable/pseudonymous reviewers (G2, Capterra, Trustpilot, Reddit) | Scraped live via Firecrawl, discovered via Tavily | (1) Quoted as evidence in "Customer Sentiment" section; (2) classified as criticism/praise; (3) checked for correct vendor attribution; (4) aggregated into a sentiment characterisation | None defined — persists indefinitely in Notion | Yes — collected in EU (operator's laptop, Spain), sent to US processors (OpenAI, Firecrawl, Tavily, Notion) |
| Reviewer role / employer size (e.g. "Verified User in Real Estate — Small-Business") | Same as above | Same as above (attached to the quote) | Same | Same |
| Pseudonymous usernames (Reddit) | Same as above | Same as above | Same | Same |
| Source URL of the review (links back to author's profile) | Same as above | Attribution / traceability | Same | Same |
| Voluntarily disclosed commercial details (e.g. revenue figures in a review) | Same as above | Quoted as-is if selected as evidence | Same | Same |
| Requester's Slack user ID, channel ID, timestamp | Slack, when a question is asked | Query interpretation, delivering the reply | Not stored by this system; stays in Slack | Depends on Slack workspace region — **not verified** |

**Flag — purpose change:** review text was published by reviewers *for* a
review platform's audience (public, informal complaint/praise). This system
repurposes it as **evidence in an internal, indefinitely-retained business
report**, read later by people (PMs, Sales) the reviewer never intended to
address. This is the classic AI-project purpose-limitation problem the lab
warns about.

---

## 3. Phase 2 — Role map

| Entity | Role | Processing activity | DPA in place? |
|---|---|---|---|
| Marc (operator/builder) | Controller | Decides purpose and means of the whole pipeline | N/A (is the controller) |
| Tavily (search) | Processor | Receives only the search query text — **no personal data outbound** | No DPA executed |
| Firecrawl (scraping) | Processor | Fetches review pages — **this is where personal data enters the system** | No DPA executed |
| OpenAI (LLM) | Processor | Receives requester's question + assembled evidence, **including verbatim review quotes** | No DPA executed |
| OpenAI (embeddings) | Processor | Only the vendor documentation corpus + query strings — review text is **not** embedded | No DPA executed |
| Notion | Processor | Stores the finished report (with quotes) indefinitely — **the durable copy** | No DPA executed |
| Slack | Processor | Question intake, requester identity, link delivery | No DPA executed |
| Review platform reviewers | Data subjects | — | — |

**International transfer:** personal data (review quotes) collected in the EU
is sent to US-based Firecrawl, OpenAI, Notion, Tavily. **No transfer mechanism
(SCCs, adequacy decision) has been assessed or put in place.** This is a gap.

---

## 4. Phase 3 — Lawful basis assessment

| Purpose | Proposed basis | Justification | Flag for legal review? |
|---|---|---|---|
| Quoting review text as evidence in a report | Legitimate interests (Art. 6(1)(f)) | Business need to inform purchasing/competitive decisions | **Yes — LIA below is incomplete** |
| Classifying text as criticism/praise, attribution check | Legitimate interests | Necessary step to make quoting above reliable, not a separate use of the person | TBD |
| Sending requester's question to OpenAI | Contract / legitimate interests (using the internal tool) | Necessary to deliver the requested report | No |

**Legitimate Interests Assessment (LIA) — for quoting review text:**

1. *Is the interest legitimate?* Yes in principle — competitive intelligence
   is a normal, lawful business activity.
2. *Is the processing necessary?* Partially. Quoting star ratings/aggregate
   sentiment would achieve most of the purpose with **less** identifying
   detail than verbatim quotes plus reviewer role/employer size.
3. *Does the individual's interest override?* **Likely yes, currently.**
   Reviewers wrote public complaints expecting a platform audience, not
   indefinite internal republication with no notice, no opt-out, and no
   erasure route. Combined with zero retention limit and no DPA with any
   processor, the imbalance favours the individual.

**Conclusion: mark this basis as TBD — legal review.** As designed today, the
LIA does not clearly pass part 3.

---

## 5. Phase 4 — Risk and rights analysis

**Special category data (Art. 9):** Not deliberately collected. However,
reviews are free text and uncontrolled — a reviewer could disclose health,
disability, or other sensitive detail while venting about a product, and the
system has **no filter to detect this**. Residual risk exists; no Art. 9
condition is currently identified because none is expected to be needed — but
this is an assumption, not a control.

**Automated decision-making (Art. 22):** No decision is made **about the
reviewers**. They are quoted, not scored or ranked. The comparative
verdicts concern **companies**, not individuals, so Art. 22 does not apply
to the reviewer data subjects. Not triggered.

**DPIA trigger check (EDPB 9 criteria):**
- Large-scale data processing — arguably not (small corpus, but continuous
  live scraping)
- Matching/combining datasets — **yes**: quotes are combined with role,
  employer size, source URL and aggregated per vendor
- Innovative technology — **yes**: LLM-driven classification/attribution
  pipeline
- Cross-border transfer preventing rights exercise — **yes**: data leaves the
  EU with no transfer mechanism, and reviewers have no way to exercise rights
  at all

At least two criteria plausibly apply → **a DPIA is generally warranted**
before any production use.

**Data subject rights friction:**
- *Right to erasure:* currently impossible to honour — no mechanism exists to
  locate a specific person's quote once published in Notion (§7 of the brief
  confirms this explicitly).
- *Right of access:* same problem — no index of whose data appears where.
- *Right to object:* reviewers don't even know the processing happens, so
  they cannot exercise this right in practice.

---

## 6. Phase 5 — Law stacking check

- **AI Act:** Not a prohibited practice, not listed in Annex III (it doesn't
  score or decide about people). Likely **minimal-risk** tier. AI Act adds a
  transparency expectation (disclose AI-generated content) that GDPR doesn't
  directly require — worth adding to any published report.
- **ePrivacy:** No cookies/trackers used on end users; scraping is server-side
  page fetching, not device-level tracking of individuals. **Low relevance.**
- **Data Act:** No connected-product or IoT data involved. **N/A.**

---

## 7. Phase 6 — Compliance memo

**To:** Marc Tanguy's Data Protection Officer / legal counsel (hypothetical — none currently engaged)
**From:** Janaina Hoffmann (teammate GDPR audit)
**Re:** GDPR review of the VR Competitive Intelligence Copilot

**Bottom line: Proceed with conditions.** The system does not score or make
automated decisions about individuals, but it processes identifiable review
text with no lawful-basis documentation, no DPAs, no retention limit, and no
way to honour data subject rights — none of this blocks the concept, but all
of it must be fixed before any real (non-local, multi-user) deployment.

**Top three actions:**
1. Complete a documented Legitimate Interests Assessment before relying on
   legitimate interests as the basis for quoting reviewer text; until then,
   treat the basis as unresolved.
2. Execute Data Processing Agreements with OpenAI, Firecrawl, Tavily, Notion
   and Slack, and assess an international-transfer mechanism (SCCs) for data
   leaving the EU — none currently exists for any provider.
3. Define a retention limit for published reports and build a minimal way to
   locate and remove a specific reviewer's quote on request, even if manual
   at first.

**Residual risks (even after the above):**
- Free-text reviews can contain special-category data the system cannot
  detect; some residual exposure remains regardless of process fixes.
- The operator's organisation is a competitor of two of the three vendors
  assessed — a fairness/conflict-of-interest concern for individuals whose
  criticism of those competitors is selectively surfaced.
- Reviewers will likely remain unaware their words were reused, since no
  notice mechanism is planned even after the fixes above.

*This memo is not a legal opinion, a DPIA, or a certification. Legal counsel
should be engaged before this project handles real users' data in production.*

---

## 8. Verify — accountability test

Could this be demonstrated as compliant to a regulator today using only
existing documentation? **No.** Missing: DPAs (all five processors), a
completed LIA, a retention schedule, a privacy notice for reviewers (not
feasible as designed), records of processing activities, and a DPIA.
