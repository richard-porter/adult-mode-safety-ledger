# Ledger Selection Criteria

**When does a domain need its own safety ledger?**

*Part of the [Richard Porter AI Safety ecosystem](https://github.com/richard-porter/where-to-start)*

-----

## The Problem This Document Solves

The Safety Ledger methodology is domain-agnostic by design. Binary tests, documented failure modes, architectural verification, no partial credit — the pattern holds across adult content, therapy, financial advice, legal analysis, and education. That generalizability raises an obvious question: what stops every domain from getting a ledger?

This document answers that question. It defines the five criteria that distinguish domains requiring their own ledger from domains adequately covered by existing ones or by general AI safety practice.

-----

## The Five Criteria

A domain warrants its own ledger when it satisfies all five:

### 1. Asymmetric Expertise

**Question:** Can the user meaningfully evaluate the AI’s output?

The user is not equipped to catch errors in real time. A patient cannot verify a triage assessment. A student cannot verify whether the AI’s historical claim is fabricated. A job applicant cannot verify whether the screening algorithm has disparate impact. The asymmetry is structural — not a matter of the user being uninformed, but of the domain requiring expertise the user doesn’t have and can’t reasonably acquire for the purpose of verification.

**Contrast:** General writing assistance, brainstorming, scheduling. The user can evaluate the output. No asymmetry.

-----

### 2. High and Specific Consequence

**Question:** When the system fails in this domain, does it cause category-specific, material harm?

Not all AI errors are equivalent. A bad poem recommendation is recoverable. A misdiagnosed symptom, a fabricated legal citation, a biased hiring screen — these cause harm that is specific to the domain, often irreversible, and not correctable by simply trying again. The harm vector must be both high-consequence and domain-specific. General “AI could be wrong” risk doesn’t qualify.

**Test:** Can you name the specific harm that domain failure causes? If yes, and if the harm is material and specific, the criterion is met.

|Domain          |Specific Harm                                                           |
|----------------|------------------------------------------------------------------------|
|Financial advice|Monetary loss, irreversible investment decisions                        |
|Legal analysis  |Liability, missed statutes, waived rights                               |
|Medical triage  |Delayed care, misdiagnosis, treatment error                             |
|Education       |Cognitive displacement, developmental deficit, integrity collapse       |
|Therapy         |Therapeutic boundary violation, AI-induced psychosis, crisis mishandling|

-----

### 3. Domain-Specific Failure Modes

**Question:** Does this domain have documented AI failure patterns that general safety practice doesn’t address?

Every ledger is anchored in observed failure modes — not theorized risks. Financial AI has sycophantic optimism and hidden commission bias. Legal AI has Framework Fabrication Syndrome. Educational AI has cognitive displacement. These patterns are documented, named, and domain-specific. They exist because the domain’s structure (asymmetric expertise, high stakes, user trust) amplifies specific AI behavioral tendencies.

A domain qualifies when it has failure modes that:

- Are documented (observed, not just possible)
- Are specific to the domain (not covered by general AI safety guidelines)
- Are structurally amplified by the domain’s characteristics

-----

### 4. Regulatory or Professional Analogue

**Question:** Does a human profession or regulatory framework already define what “safe practice” looks like?

The binary tests in each ledger are not invented from scratch — they encode existing professional and regulatory standards into architectural requirements. Medical ethics provides the diagnosis/triage boundary. Legal ethics provides the unauthorized practice line. FERPA provides the student data standard. FINRA provides the disclosure requirement.

This criterion serves two functions. It grounds the binary tests in existing consensus rather than one practitioner’s judgment. And it makes the ledger immediately useful to regulators and compliance teams who already work within those frameworks.

**Domains with strong regulatory analogues:** Medical (FDA, CMS), Legal (bar ethics rules), Financial (SEC, FINRA, CFPB), Education (FERPA, COPPA, IDEA), Employment (EEOC, OFCCP), Mental health (clinical licensing boards).

-----

### 5. Verifiable Canonical Sources

**Question:** Is there a canonical source of truth that can serve as a deterministic verification anchor?

Binary tests require something to be binary against. “The system checks its output against X” only works if X exists, is maintained, and is publicly accessible. Drug formularies, legal statutes, clinical guidelines, educational standards, financial regulations — these are canonical sources that make deterministic verification architecturally possible, not just aspirationally desirable.

Without a canonical source, the ledger reduces to “the system should try hard to be accurate,” which is not a binary test and not an architectural requirement.

-----

## The Decision Matrix

|Criterion                    |Question                                              |If No                                 |
|-----------------------------|------------------------------------------------------|--------------------------------------|
|Asymmetric Expertise         |Can the user catch errors in real time?               |Domain may not need a ledger          |
|High Specific Consequence    |Does failure cause material, domain-specific harm?    |General AI safety guidance may suffice|
|Domain-Specific Failure Modes|Are there documented patterns general practice misses?|Existing ledger may cover it          |
|Regulatory Analogue          |Does a professional/regulatory framework exist?       |Binary tests will be weak             |
|Canonical Sources            |Is there a verifiable source of truth?                |Deterministic testing is not possible |

**All five must be met.** A domain that passes four of five will produce a ledger with at least one section that cannot be tested binarily — which undermines the methodology.

-----

## What This Criteria Set Excludes

Some domains are frequently suggested and don’t qualify:

**General creative writing** — user can evaluate output, no regulatory analogue, no canonical truth source. Fails criteria 1, 4, and 5.

**Entertainment recommendation** — low specific consequence, no domain-specific failure modes beyond general AI bias. Fails criteria 2 and 3.

**Personal productivity** — user can evaluate output, no high-consequence failure mode specific to the domain. Fails criteria 1 and 2.

**Customer service** — may have high consequence in specific verticals (insurance, healthcare) but those verticals already have their own ledgers. The domain itself isn’t the unit — the high-gain application within the domain is.

-----

## Cross-Ledger Coverage

Before creating a new ledger, check whether the domain is already covered by an existing one operating at a different scope:

|If you’re thinking about…             |Check first…                                                    |
|--------------------------------------|----------------------------------------------------------------|
|Scholarship and financial aid guidance|Financial Advice Mode Safety Ledger                             |
|Student mental health support         |Therapy Mode Safety Ledger                                      |
|IEP compliance and student rights     |Legal Analysis Mode Safety Ledger + Education Mode Safety Ledger|
|AI in pediatric hospital settings     |Safe Storyteller Framework                                      |
|AI-assisted HR decisions              |HRBP AI Safety Framework                                        |

A new ledger is warranted when existing coverage is incomplete — not when the domain merely overlaps with existing ledgers.

-----

## Future Domains Under Evaluation

The following domains are candidates for future ledgers based on the five criteria. None are currently built.

**Medical Triage** — asymmetric expertise (patient cannot verify triage accuracy), high consequence (delayed emergency care), documented failure modes (overconfident symptom assessment), regulatory analogue (FDA, clinical triage protocols), canonical sources (clinical guidelines, drug formularies). All five criteria met.

**Recruitment and Hiring** — asymmetric expertise (candidate cannot see screening logic), high consequence (wrongful exclusion, disparate impact), documented failure modes (algorithmic bias, false negatives in protected classes), regulatory analogue (EEOC, OFCCP adverse impact standards), canonical sources (EEOC uniform guidelines). All five criteria met.

**Crisis Intervention** — asymmetric expertise (person in crisis cannot evaluate adequacy of response), high consequence (failure to route to emergency services), documented failure modes (inadequate escalation, reflective listening amplification), regulatory analogue (clinical crisis intervention standards), canonical sources (988 Lifeline protocols, clinical guidelines). All five criteria met.

These are the next three. Sequencing depends on community contribution and empirical data availability, not on which domain sounds most urgent.

-----

## Using This Document

This document is a methodology reference, not a roadmap. It answers “should this domain have a ledger?” — not “when will it be built?”

Contributions of domain-specific failure mode documentation, regulatory citations, or canonical source identification for candidate domains are the highest-value input the community can provide. The criteria exist. The evidence catalog is what makes the binary tests possible.

-----

*Ledger Selection Criteria · v1.0 · Part of the Frozen Kernel System*  
*Safety Ledgers repository: [github.com/richard-porter/safety-ledgers](https://github.com/richard-porter/safety-ledgers)*
