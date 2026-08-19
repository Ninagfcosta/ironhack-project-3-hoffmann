# Audit Your Tech Stack

**Student:** Janaina Hoffmann
**Lab:** LAB | Audit your tech stack (W16D01)
**Project:** Company Research Bot — Project 3

## What this lab is about

I use several AI tools to build and run my Company Research Bot. This lab
asks me to look past the marketing language and check what these vendors
actually prove about their environmental impact — using only official
sources, not blog posts or opinions.

For each tool, I filled in three things:

- **Claim** — what the company says about itself
- **Evidence** — the official link that backs up the claim
- **Unknown** — what the company does *not* tell us

If a tool makes a claim with no official evidence behind it, that's a red
flag for greenwashing (saying something sounds green without proving it).

## The tools I use in my project

| Tool | What I use it for | How it's deployed |
|---|---|---|
| **OpenAI (GPT models)** | AI text generation for the bot's reasoning and report writing | Cloud, hosted on Microsoft Azure |
| **Anthropic (Claude)** | AI assistant used while building the project | Cloud, Anthropic-operated and leased data centers |
| **n8n** | Workflow automation, connects the bot to Telegram | Self-hosted (I could choose a European host) |

## Claim → Evidence → Unknown

| Tool | What the vendor publicly says (claim) | Evidence (official source) | What is unclear or not disclosed (unknown) | Why this matters |
|---|---|---|---|---|
| **OpenAI** | Relies on Microsoft Azure's push toward renewable-powered data centers. No OpenAI-specific carbon report exists. | trust.openai.com / Azure sustainability pages — accessed Aug 18, 2026 | The exact energy or CO2 cost per query. There is no OpenAI-specific emissions report. | Shows that sustainability info can come from the cloud provider, not the AI company itself. |
| **Anthropic** | Publicly committed to covering grid upgrade costs, investing in water-efficient cooling, and funding new power generation for its data centers. | anthropic.com (news / commitments page) — accessed Aug 18, 2026 | No public per-query energy number. Renewable-energy percentage is not fully specified for every site. | Shows a company can be transparent about *commitments* while still not sharing hard numbers. |
| **n8n** | Public docs describe the "Sustainable Use License" and list hosting options (Azure, GCP, self-host). | docs.n8n.io/sustainable-use-license — accessed Aug 18, 2026 | No environmental or energy sustainability page exists at all. | Good example of a misleading keyword — here "sustainable" means the software *license*, not the environment. |

## What I learned (reflection)

Of the three tools, **Anthropic** gives the clearest public information,
because it names concrete actions — funding grid upgrades, investing in
water-efficient cooling — instead of only using a slogan. The biggest
unknown is with **OpenAI**: there is no OpenAI-specific emissions report,
so its sustainability story is really borrowed from Microsoft Azure. The
biggest surprise for me was **n8n** — in their official docs, the word
"sustainable" refers to their software *license*, not to the environment
at all. That was a good reminder to always check what a keyword actually
means before assuming it supports a green claim.

One decision I'd consider changing on a future bootcamp project: choosing
**self-hosted, EU-region hosting for n8n**, since region-level carbon
intensity data is more publicly documented than any single tool's own
environmental claims.

**Takeaway:** if my functional unit (R) is "one AI-assisted task," public
disclosures help me understand which infrastructure and cloud choices a
vendor is making — but they don't tell me the real energy or carbon cost
of my own, individual requests. For that, I'd need data none of these
vendors currently publish.

*Self-assessment for a class assignment — not a certified sustainability audit.*
