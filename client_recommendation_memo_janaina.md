# GDPR Check-In: AI Resume Screening Tool

**From:** Janaina Hoffmann
**To:** Head of Human Resources

---

Dear Head of Human Resources,

This memorandum presents the findings of an initial GDPR compliance review conducted on the AI-assisted resume screening tool your organization intends to implement. The underlying objective of the system is sound, as the use of AI to support candidate evaluation is a well-established and legitimate practice. Nonetheless, several matters require remediation prior to the system's deployment against real applicant data.

**Recommendation: Proceed, subject to the conditions set out below.**

---

## Primary Finding

Under the system's current configuration, only top-ranked candidates are presented to the recruiter by default, with lower-ranked candidates reviewed solely at the recruiter's discretion. This configuration raises a material concern under GDPR Article 22, which restricts decisions producing legal or similarly significant effects on an individual where such decisions are made without meaningful human involvement. As implemented, the majority of applicants are effectively excluded from consideration absent any human review. This should be treated as the priority issue requiring resolution.

## Secondary Findings

**Undefined retention period.** Applications are currently retained indefinitely on the premise that they may prove relevant to future vacancies. This practice does not satisfy GDPR requirements unless candidates are clearly informed and afforded the opportunity to consent to that specific purpose. A defined retention period is recommended for the original application (for example, six to twelve months), with any extended retention for future opportunities treated as a distinct, opt-in processing purpose.

**International data transfer.** The AI tool and its supporting infrastructure are hosted in the United States. While this arrangement is not inherently non-compliant, it necessitates appropriate safeguards, namely executed Data Processing Agreements with each relevant provider and a valid transfer mechanism, such as Standard Contractual Clauses supported by a Transfer Impact Assessment.

## Areas of Existing Compliance

The system's underlying purpose and design intent are appropriate, and this review does not recommend suspension of the initiative. Rather, it identifies a limited set of gaps to be addressed prior to production deployment.

## Residual Risk

Certain risks will persist notwithstanding the implementation of the above measures. AI ranking models may introduce bias correlated with factors such as educational background or nationality referenced within a resume, and such bias may be difficult to detect absent periodic monitoring and validation. Candidates may further request an explanation of the basis for a low ranking; a consistent internal procedure for responding to such requests is therefore advisable. Finally, given that this system likely qualifies as high-risk under the EU AI Act, additional obligations beyond GDPR compliance will apply and should be tracked in parallel with the remediation items above.

---

This assessment constitutes a first-pass review and does not represent formal legal advice. Prior to processing real applicant data, a comprehensive review by legal counsel and the Data Protection Officer is recommended, with particular attention to the human oversight requirement identified above.

Kind regards,
Janaina Hoffmann
