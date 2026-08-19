# EU AI Act Self-Audit — Company Research Bot

**Lab:** Audit your own project — AI Act

## What it is

A Telegram bot that takes a company name and generates a research report
using web search, news, and financial data. An LLM (through a LangGraph
workflow) writes the actual report. It doesn't make decisions about
people — it just writes about companies.

## Classification

**I'd put this at minimal risk.**

Reasoning:
- It doesn't score, profile, or make decisions about real people.
- It doesn't fall into any of the Annex III high-risk categories
  (employment, credit, law enforcement, biometrics, none of that).
- It's not pretending to be human or replacing a human decision, so the
  formal transparency requirements don't really bite hard here — but I'd
  still want to be upfront that it's AI-generated if I ever shared it
  outside this class.

## How it's built

- **Pinecone (RAG):** reference documents for context
- **ReAct agent:** decides what tool to call
- **LangGraph:** Research Node → Analysis Node → Report Node
- **N8N:** triggers and connects everything
- **Telegram:** where the user actually gets the report

## Who does what

| Role | Who |
|---|---|
| Provider (built it) | Me |
| Deployer (uses it) | Me, for the class demo |
| Vendors involved | OpenAI, Tavily, Pinecone, Telegram |

## What this means in practice

- **Transparency:** if this ever went beyond a personal/class demo, I'd
  add a line saying the report was AI-generated — good practice even if
  not strictly required at this risk level.
- **Prohibited practices:** none of this applies — no manipulation, no
  social scoring, no biometrics.
- **High-risk triggers:** doesn't touch jobs, credit, education, or
  anything like that, so none of the Annex III stuff applies.

## Bottom line

I'm comfortable classifying this as minimal risk and moving on. If it
ever became a real product used by other people, the one thing I'd
actually add is a disclosure that the report is AI-written — more as
good practice than a legal requirement at this classification.

*Self-assessment for a class assignment, not a legal opinion.*
