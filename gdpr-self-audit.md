# GDPR Self-Audit — Company Research Bot

**Lab:** Audit your own project — GDPR lens
**System:** my own Project 3 (Company Research Bot, via Telegram)

## What the system actually does

Someone sends a company name through Telegram. The bot searches the web,
checks recent news, grabs some financial data, and sends back a written
report. That's it.

## Personal data — is there any?

Honestly, barely. The only personal data point involved is the Telegram
user ID, and that's not something I'm even choosing to collect — Telegram
just attaches it to every message automatically so the reply goes back to
the right chat. I don't store it anywhere, log it, or use it for anything
else.

## Lawful basis

1. Is there a lawful basis? I'd say **legitimate interest** — the ID is
   only there to route the reply.
2. Is it necessary? Yes, there's no way to reply on Telegram without it.
3. Does it override the person's interest? No, because nothing happens
   with it beyond that one reply.

## Risk check

- **Special category data:** not something I'm collecting on purpose. The
  bot only really processes a company name, so there's not much room for
  sensitive info to sneak in.
- **Automated decisions about people:** none — the bot writes about
  companies, not people, so this doesn't apply.
- **Do I need a full DPIA?** Going through the EDPB's list of triggers,
  I don't think so — the amount of personal data is tiny, nothing is
  scored, and nobody is being monitored.
- **What if someone wants their data deleted?** This is actually easy to
  answer — there's nothing to delete, because the ID is never saved
  anywhere. It's used live, then gone.

## Checking against other laws

- **AI Act:** the bot doesn't score or decide anything about people, so
  I'd classify it as minimal risk. If I ever shared it outside of class,
  I'd probably add a small note saying the report is AI-generated.
- **ePrivacy:** no cookies or tracking involved, so not relevant here.
- **Data Act:** no IoT/connected devices, so not applicable.

## My conclusion

I think this project is fine as it is. The only personal data involved
(the Telegram ID) is never stored, so there isn't much to get wrong here.

If I were to actually turn this into something real people used, I'd
still want to:
1. Write down somewhere that "legitimate interest" is the basis for
   using the Telegram ID, just so there's a record of it
2. Get proper data agreements in place with the services I'm using
   (n8n, Telegram, OpenAI, Tavily) if this ever left the "class project"
   stage
3. Come back and redo this audit if I start saving reports or letting
   multiple people use it, since more usage = more risk

One thing I'll admit is a gap: if someone typed something personal by
accident into the "company name" field, there's currently no filter
catching that. Low risk, but worth knowing.

*This is a self-check for a class assignment, not an actual legal
opinion.*
