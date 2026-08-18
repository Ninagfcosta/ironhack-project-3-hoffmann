LAB | Classify your product
Prepared by: Janaina Hoffmann
Based on Marc-fact-pattern (3).md

Case – NordSecure Health AI Underwriting
Client Summary

NordSecure Health, a German health insurer, wants to use AI to help decide individual health insurance applications across five EU countries. The AI reads personal and medical data and suggests accept, decline, or a different price. A human checks the AI's suggestion, but usually agrees with it.

First-pass Classification

High GDPR Risk – Special Category Data + International Transfer

Why

The AI uses health data (medical conditions, smoking, BMI), which needs extra legal protection. The data is also stored on a US cloud server, which means it leaves the EU. Both of these raise the risk level a lot.

Data Map
Data Type	Special Category?
Name, address, contact info	No
Claims history	No
Medical conditions, smoking, BMI	Yes – health data
Key Risks
Risk	Why it matters
Health data used	Needs explicit consent, not just a normal legal reason
Data sent to US	Needs a special data transfer contract (SCCs)
Human "usually agrees" with AI	May not count as real human review
Big scale, multiple countries	Legally requires a DPIA (risk checklist) before launch
Consulting Decision

-> Approve with Controls

The project can move forward, but only after: (1) getting clear consent from applicants to use their health data, (2) signing a data transfer contract with the US cloud provider, (3) completing a DPIA before launch, and (4) making sure the human reviewer can genuinely disagree with the AI, not just approve it automatically.
