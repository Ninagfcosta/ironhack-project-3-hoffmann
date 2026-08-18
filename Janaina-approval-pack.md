Based on Marc-client-briefs.md

Case 1 – Travel Platform Virtual Assistant
Client Summary

A global online travel platform wants to launch an AI-powered virtual assistant that helps customers search for accommodation, answer booking questions, recommend destinations, and generate personalized travel itineraries. The assistant interacts directly with users through the website and mobile app and can also create promotional images for suggested trips. Customer support agents can take over conversations whenever needed, but most interactions are handled autonomously.

First-pass Classification

Limited Risk – Transparency Obligations

WHY

The assistant interacts directly with users and generates content on its own (itineraries, promotional images). It does not make decisions about a person's rights, safety, or access to essential services, so it does not qualify as high-risk. Because it is a conversational AI system interacting with natural persons and generating synthetic content, it triggers the Article 50 transparency obligation.

Proposed Architecture
Component	Description
Business trigger	Customer opens the assistant on the website or app.
AI behaviour	Answers booking questions, recommends destinations, generates itineraries and promotional images.
Inputs	Customer queries, booking history, destination data.
Human review	Support agent can take over any conversation.
Output	Conversational responses, itineraries, AI-generated images.
Role Map
Role	Entity
Provider	AI platform vendor developing the assistant.
Deployer	Travel company operating the platform.
Third-party vendor	Generative AI vendor (image generation), possibly separate LLM provider.
Compliance Implications

The platform must clearly disclose to users that they are interacting with an AI system, and AI-generated promotional images should be labeled as synthetic content in line with Article 50.

Consulting Decision

-> Approve with Conditions

The project may proceed provided a clear "you're chatting with an AI" disclosure appears at the start of every session, and any AI-generated images used in promotions are visibly labeled as AI-generated. Support agents should remain easy to reach at any point in the conversation. No further AI Act obligations apply beyond these transparency measures.

Case 2 – Hotel Guest Emotion Monitoring Used to Evaluate Staff
Client Summary

An international luxury hotel group wants to deploy an AI platform that continuously analyzes CCTV footage across its properties to estimate guests' emotional reactions during their stay. Management also wants to evaluate front-desk and concierge staff based on how guest emotions change after each interaction, using weekly AI-generated performance reports to inform bonuses and promotion decisions. Hotel managers can review the reports before taking action but are generally expected to follow the system's recommendations unless there is clear evidence to the contrary.

First-pass Classification

Prohibited AI (Article 5)

WHY

The system infers people's emotional state from CCTV footage, and the results are used to evaluate and score employees for bonuses and promotions. The EU AI Act bans AI systems that infer the emotions of a person in the workplace, except for narrow medical or safety reasons. Using guest-emotion inference to score staff performance falls squarely within this prohibited practice, and it also touches employment decisions, which would separately be high-risk if the underlying method were lawful at all.

Proposed Architecture
Component	Description
Business trigger	CCTV footage collected continuously across hotel properties.
AI behaviour	Infers guest emotional reactions and links them to individual staff interactions.
Inputs	Live CCTV video streams.
Human review	Manager reviews weekly report but is expected to follow it.
Output	Staff performance score tied to bonuses and promotions.
Role Map
Role	Entity
Provider	AI software vendor developing the emotion recognition platform.
Deployer	Hotel group operating the properties.
Third-party vendor	CCTV/cloud infrastructure and computer vision providers (if applicable).
Compliance Implications

Because the proposed functionality falls within prohibited AI practices, there is no compliance pathway under the AI Act.

Consulting Decision

-> Deny and Redesign

The proposed solution should not be deployed in its current form, as it falls within prohibited AI practices under the EU AI Act. There is no compliance pathway that would make this use lawful through additional documentation or governance alone. Instead, the client should redesign the solution to remove emotion inference entirely. A compliant alternative would be to use standard guest satisfaction surveys, direct guest ratings per interaction, or manager observation to evaluate service quality — none of which involve inferring an employee's emotional state through AI.

Case 3 – Health Insurance Underwriting AI
Client Summary

A medium-sized health insurance company wants to implement an AI system that evaluates applications for individual health insurance policies. The model combines medical questionnaires, historical claims, demographic information, and lifestyle indicators to estimate each applicant's risk profile and recommend whether to approve the application and at what premium. Underwriters review the recommendation before making the final decision, although they generally follow the model unless supporting evidence suggests otherwise.

First-pass Classification

High-risk AI (Annex III – Access to Essential Private Services)

WHY

The AI directly influences whether a person can access health insurance and at what price, an Annex III high-risk area covering risk assessment and pricing for health and life insurance. Although an underwriter reviews the recommendation, the pattern of generally following the model unless there is contrary evidence means the AI's output is effectively determinative for most applicants.

Proposed Architecture
Component	Description
Business trigger	Application submitted for individual health insurance.
AI behaviour	Estimates applicant risk profile and recommends approval and premium.
Inputs	Medical questionnaires, claims history, demographics, lifestyle indicators.
Human review	Underwriter reviews recommendation before final decision.
Output	Approval/denial recommendation and premium.
Role Map
Role	Entity
Provider	AI model vendor developing the underwriting system.
Deployer	Health insurance company.
Third-party vendor	Data vendor supplying claims/demographic history (if applicable).
Compliance Implications

The system would require the full set of applicable high-risk obligations, including risk management, technical documentation, bias and fairness testing, logging, applicant notice, and meaningful human oversight. The current level of oversight appears borderline because underwriters generally defer to the model.

Consulting Decision

-> Approve with Controls

The proposed system may proceed only if the client implements the governance and compliance controls required for high-risk AI systems. These include a documented risk management process, technical documentation and decision logs, bias and fairness testing across protected groups, a Fundamental Rights Impact Assessment (FRIA), applicant notice and a right to explanation, and evidence that underwriters exercise genuine independent judgment rather than routinely accepting the model's recommendation. Deployment should only occur once these controls are operational and documented.

Case 4 – Internal Bug Triage Assistant
Client Summary

A SaaS company wants to build an internal AI assistant that helps its Product and Engineering teams manage software defects. The system summarizes bug reports, clusters duplicate issues, recommends likely root causes based on historical tickets, and suggests priority levels for the engineering backlog. Product managers and engineers decide whether to accept or ignore the recommendations before any work is scheduled.

First-pass Classification

Minimal Risk

WHY

The AI supports internal engineering workflow and prioritization. It does not make decisions affecting individuals' rights, safety, or access to services, and product managers and engineers retain full authority over which recommendations to act on.

Proposed Architecture
Component	Description
Business trigger	New bug report filed.
AI behaviour	Summarizes reports, clusters duplicates, suggests root cause and priority.
Inputs	Bug reports and historical ticket data.
Human review	Product managers and engineers decide whether to accept suggestions.
Output	Internal recommendation only (summary, cluster, suggested priority).
Role Map
Role	Entity
Provider	Internal tool or AI vendor supplying the assistant.
Deployer	SaaS company (internal use only).
Third-party vendor	LLM provider (if applicable).
Compliance Implications

No specific AI Act obligations apply. The company should still check whether any personal data (e.g., customer names or emails pasted into bug reports) appears in tickets, for GDPR purposes.

Consulting Decision

-> Approve

The proposed system represents a low-risk internal decision-support tool that assists engineering workflow without producing decisions that have legal or similarly significant effects on individuals. The company may proceed with deployment while maintaining standard governance practices and periodically checking bug reports for accidental personal data exposure.
