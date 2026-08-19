# Project 3 Brief — Company Research Agent

**Industry:** Market Research & Competitive Intelligence

## The idea

I wanted to build an agent that does the annoying part of company research
for you — you give it a company name, and it searches the web, checks
recent news, and pulls basic financial data, then writes it all up as one
report. Something an analyst could actually use instead of opening ten
browser tabs.

## MVP scope

- User types a company name
- Agent searches the web for general info
- Agent checks recent news
- Agent pulls basic financial data (stock price, key numbers)
- Agent puts it all together into a written report

## APIs (needed at least 3)

I ended up using:
1. **Tavily** — general web search
2. **NewsAPI** — recent news
3. **Alpha Vantage** — financial data

## Architecture

- **Pinecone (RAG):** stores reference docs so the agent has extra context
- **ReAct agent:** this is the part that decides which tool to use at each
  step
- **LangGraph:** the workflow — Research → Analysis → Report
- **N8N:** connects everything and triggers the Python agent
- **Flask:** exposes the agent as an API
- **Telegram:** where the user actually talks to the bot and gets the
  report back

## 5-day plan (roughly how it went)

| Day | What I did |
|---|---|
| Day 1 | Set up API accounts, project structure |
| Day 2 | Built the Pinecone vector store with sample docs |
| Day 3 | Built the ReAct agent + LangGraph workflow |
| Day 4 | Connected everything through N8N |
| Day 5 | Testing, writing docs, recording the demo |

## Test reports

I generated sample reports for Tesla, Apple, and Adidas to check the
output made sense (see `sample_reports/`).
