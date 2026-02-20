# Safety Ledgers

**Public safety scorecards for high-gain AI features.**  
Binary architectural tests. Pre-launch criteria. Platform evaluations.

*Part of the [Richard Porter AI Safety ecosystem](https://github.com/richard-porter/where-to-start)*

-----

## What This Is

Some AI features carry outsized risk — not because they’re unusual, but because they operate in contexts where the stakes of failure are highest. Adult content. Mental health support. Financial advice. Legal analysis. Pediatric settings. HR decisions.

This repository applies a single methodology across all of them: binary architectural tests. Either the safeguard is structurally present or it isn’t. No partial credit. No “mostly compliant.”

**Design Principle:** High-gain domains require **stronger** deterministic constraints, not relaxed ones. Safety must be built into architecture, not layered as moderation or terms of service.

-----

## The Ledger Library

|Ledger                                                                   |Domain                        |Criteria|Scoring Index               |
|-------------------------------------------------------------------------|------------------------------|--------|----------------------------|
|[v1.0 Proactive Safety Criteria](v1.0%20Proactive%20Safety%20Criteria.md)|Adult / explicit content      |9       |ACI                         |
|<therapy-mode-safety-ledger.md>                                          |Mental health / therapeutic AI|10      |—                           |
|<financial-advice-mode-safety-ledger.md>                                 |Financial guidance            |10      |FACI                        |
|<legal-analysis-mode-safety-ledger.md>                                   |Legal analysis                |11      |LACI                        |
|<hrbp-ai-safety-framework.md>                                            |Human resources / HR AI       |—       |Wrongful Termination Test   |
|<safe-storyteller-framework.md>                                          |Pediatric / clinical settings |8       |Pediatric Adverse Event Test|

| [education-mode-safety-ledger.md](education-mode-safety-ledger.md) | Educational instruction | 10 | EACI |

**Why different criteria counts?** Each domain earns its count based on the specificity of documented failure modes. Legal analysis has 11 because jurisdiction and citation failure are structurally distinct problems requiring separate gates. Therapy has 10 because clinical harm prevention (including AI-induced psychosis) requires a dedicated section that adult mode does not. The methodology is consistent; the criteria are domain-calibrated.

-----

## Shared Methodology

All ledgers share the same underlying logic:

**Binary tests only.** A system either passes or it doesn’t. “Cannot be confirmed” defaults to FAIL — the burden of evidence is on the implementer, not the evaluator. This is consistent with the Frozen Kernel’s Universal Fallback Rule: *when in doubt, downgrade.*

**Architecture, not intention.** Platforms cannot argue good intentions against a binary architectural test. Either the safeguard is structurally present or it isn’t — the same way a defibrillator either has a fail-closed circuit or it doesn’t.

**Empirical basis.** Criteria are not theorized. They are derived from documented failure modes — SEC enforcement actions, FINRA investor alerts, clinical case studies (Østergaard, Sakata), and 30 AI behavioral failure modes observed across five platforms during the Frozen Kernel research.

The complete methodology is in <Methodology.md>.

-----

## Regulatory Framing

The binary scoring methodology is modeled on medical device safety regulation, not content moderation policy.

Medical devices that fail in high-stakes contexts — implantable defibrillators, insulin pumps, surgical equipment — are not evaluated on whether the manufacturer intended them to work correctly. They are evaluated on whether the architecture makes failure predictable, detectable, and bounded.

AI features operating in high-gain domains warrant the same standard. The criteria in this ledger library are designed to be directly usable as pre-launch gates in regulatory frameworks, not merely as voluntary transparency benchmarks.

-----

## Platform Evaluations (Adult Mode — v1.0)

The original adult mode ledger has been evaluated across five platforms:

|Platform          |Scorecard                                                                                                         |
|------------------|------------------------------------------------------------------------------------------------------------------|
|Claude (Anthropic)|[Claude (Anthropic) — Research Lead Response.md](Claude%20(Anthropic)%20%E2%80%94%20Research%20Lead%20Response.md)|
|ChatGPT (OpenAI)  |[ChatGPT (OpenAI) - Co-Architect Response.md](ChatGPT%20(OpenAI)%20-%20Co-Architect%20Response.md)                |
|Gemini (Google)   |[Gemini (Google) - Peer Reviewer Response.md](Gemini%20(Google)%20-%20Peer%20Reviewer%20Response.md)              |
|Grok (xAI)        |[Grok (xAI) - Peer Reviewer Response.md](Grok%20(xAI)%20-%20Peer%20Reviewer%20Response.md)                        |
|DeepSeek          |[DeepSeek Peer Reviewer.md](DeepSeek%20Peer%20Reviewer.md)                                                        |

Comparative baseline: [Initial Baseline Assessment.md](Initial%20Baseline%20Assessment.md)

Platform evaluations for the therapy, financial, legal, HR, and pediatric ledgers are **pending**. Community contribution welcome — see <CONTRIBUTING.md>.

-----

## Repository Structure

|File                                            |Contents                                  |
|------------------------------------------------|------------------------------------------|
|`README.md`                                     |This file                                 |
|`Methodology.md`                                |Evaluation methodology and empirical basis|
|`v1.0 Proactive Safety Criteria.md`             |Adult mode — complete v1.0 criteria       |
|`therapy-mode-safety-ledger.md`                 |Therapy / mental health AI criteria       |
|`financial-advice-mode-safety-ledger.md`        |Financial advice AI criteria              |
|`legal-analysis-mode-safety-ledger.md`          |Legal analysis AI criteria                |
|`hrbp-ai-safety-framework.md`                   |HR / HRBP AI safety framework             |
|`safe-storyteller-framework.md`                 |Pediatric / clinical AI criteria          |
|`Initial Baseline Assessment.md`                |Baseline scorecard: all five platforms    |
|`ChatGPT (OpenAI) - Co-Architect Response.md`   |Platform scorecard: ChatGPT               |
|`Claude (Anthropic) — Research Lead Response.md`|Platform scorecard: Claude                |
|`Gemini (Google) - Peer Reviewer Response.md`   |Platform scorecard: Gemini                |
|`Grok (xAI) - Peer Reviewer Response.md`        |Platform scorecard: Grok                  |
|`DeepSeek Peer Reviewer.md`                     |Platform scorecard: DeepSeek              |
|`HIP_FRAMEWORK.md`                              |Human Intervention Points framework       |
|`human-intervention-points.md`                  |Human intervention documentation          |
|`Open Invitation to AI Systems.md`              |Open letter to platforms on self-reporting|
|`CHANGELOG.md`                                  |Version history and criteria updates      |
|`CONTRIBUTING.md`                               |Contribution guidelines                   |
|`LICENSE.md`                                    |License                                   |

-----

## Open Invitation

This ledger library was developed by one researcher. The evaluations represent one person’s application of the criteria to publicly observable platform behavior. That is not enough.

Platforms are invited to self-report against any ledger. Corrections to any evaluation are welcome — with documentation. Independent replication is explicitly encouraged. If a criterion is wrong — too strict, miscategorized, or missing something — the issues tab exists for that conversation.

The goal is not to win an argument. The goal is a public record that is accurate.

-----

## Related Repositories

- 🧊 [Frozen Kernel](https://github.com/richard-porter/frozen-kernel) — The single-agent safety architecture this ledger library builds on
- 🔗 [Trust Chain Protocol](https://github.com/richard-porter/richard-porter-trust-chain-protocol) — Network-layer safety for multi-agent AI systems
- 📖 [AI Collaboration Field Guide](https://github.com/richard-porter/ai-collaboration-field-guide) — Practical human skills for AI collaboration safety
- 🔬 [Dimensional Authorship](https://github.com/richard-porter/dimensional-authorship) — The research case study where these frameworks were developed
- 🗺️ [Where to Start](https://github.com/richard-porter/where-to-start) — Full ecosystem map

-----

## Suggested GitHub Topics

`ai-safety` · `ai-governance` · `llm-safety` · `ai-alignment` · `behavioral-safety` · `deterministic-safety` · `human-ai-interaction` · `ai-ethics` · `ai-accountability` · `responsible-ai` · `legal-ai` · `financial-ai` · `mental-health-ai`

-----

*Safety Ledgers · v1.0 · Part of the Frozen Kernel System*
