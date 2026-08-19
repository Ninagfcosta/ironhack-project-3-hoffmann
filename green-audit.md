# Project 3 Green Audit — Company Research Bot

**Lab:** LAB | Project 3 Green Audit

## Quick system rundown

The bot takes a company name from Telegram and returns a research report.
Behind the scenes, a ReAct agent (running on `gpt-4o-mini`) figures out
which tools to call, pulls data from three APIs, then writes up the
report. Flask and N8N handle the plumbing that connects it all to
Telegram.

## Phase 1 — Compute map

| Component | What it does | Type | Calls per report |
|---|---|---|---|
| `gpt-4o-mini` (reasoning) | Decides which tool to call next | LLM inference | 1–2 |
| `gpt-4o-mini` (writing) | Writes the final report | LLM inference | 1 |
| Tavily | General search | Lightweight API | 1 |
| NewsAPI | Recent news | Lightweight API | 1 |
| Alpha Vantage | Financial data | Lightweight API | 1 |
| Flask | Runs the agent | Small server | continuous |
| N8N | Triggers everything, bridges to Telegram | Small server | 1 run |

So roughly **5 calls per report**, and most of the actual compute is
happening in those 2-3 LLM calls, not the 3 API calls.

## Phase 2 — Functional unit and SCI

**Functional unit (R):** one finished report delivered to the user.

**SCI = (O + M) / R**

- **O:** basically all coming from the `gpt-4o-mini` calls. The three
  data APIs are just quick lookups, barely register next to model
  inference.
- **M:** the footprint of whatever machine ran the dev/testing, plus some
  unknown slice of OpenAI's and the API providers' server hardware —
  I honestly can't get real numbers for this since none of these
  companies publish per-call energy data.
- **R:** 1 report.

I want to be upfront that I can't give an actual number here (no one
publishes kWh-per-call data), so this audit is more about figuring out
where the compute is going than putting a precise figure on it.

## Phase 3 — Where the compute actually goes (hotspots)

1. **The LLM calls, by far.** 2–3 calls to `gpt-4o-mini` per report is
   where almost all the energy is going.
2. **Reasoning loops.** If the ReAct agent goes back and forth more than
   necessary before picking a tool, that's extra LLM calls I'm not
   accounting for above.
3. **No caching.** If someone researches the same company twice, the bot
   runs the whole pipeline again from scratch.
4. **The APIs.** Small hotspot compared to the LLM, but if a call fails
   and retries without a limit, it adds up.

## Phase 4 — What I could actually do about it

| Idea | Why it helps | What it costs |
|---|---|---|
| Already using `gpt-4o-mini` instead of full `gpt-4o` | Smaller model, less energy per call | Slightly less reasoning power, but fine for this use case |
| Cap how many reasoning loops the agent can take | Stops runaway multi-step reasoning from quietly adding LLM calls | Might occasionally cut a legit multi-step research off early |
| Cache recent duplicate requests | No point re-running everything for the same company twice in an hour | News/financials could be a little stale |
| Trim the API responses before sending to the LLM | Shorter prompt = less compute | A bit more preprocessing code to write |

## Phase 5 — Memo

I looked at the compute footprint of the Company Research Bot, which
generates a report through roughly five calls: 2-3 to `gpt-4o-mini` for
reasoning and writing, and 3 lightweight lookups to Tavily, NewsAPI, and
Alpha Vantage.

The language model is where basically all the energy use is coming from
— not the data APIs. One good decision already baked in: the project uses
`gpt-4o-mini` instead of the full-size `gpt-4o`, which cuts down on energy
per call without really hurting the report quality for what this bot
needs to do.

Two changes would help further, without much effort. Capping the number
of reasoning steps the agent takes before deciding on a tool would stop
occasional runaway loops from silently adding extra LLM calls. Adding a
short-term cache for repeat requests — researching the same company
twice within an hour, say — would avoid re-running the whole pipeline
for no reason, at the small cost of sometimes returning slightly older
news or financial numbers.

I don't have exact carbon numbers here, since none of the providers I'm
using publish that data per call. What I can say with more confidence is
where the compute is actually being spent, and that's squarely on the
LLM side, not the APIs.

**My take:** nothing urgent needs fixing right now — it's a reasonably
efficient setup for what it is. If this ever got used a lot more,
caching would be the first thing I'd add.

*Self-assessment for a class assignment, not an official carbon audit.*
