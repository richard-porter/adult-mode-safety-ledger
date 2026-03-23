# Methodology

## Evaluation Principles

- Criteria defined **before** implementation.
- No retrospective justification.
- No reliance on stated intentions.
- Evaluation based on observable architecture and public disclosures.
- All assessments timestamped and immutable.

## What This Ledger Evaluates

This ledger evaluates whether specific architectural features **exist** — not whether a company's intentions are good, nor whether a feature is morally acceptable.

Companies cannot argue about good intentions against a binary test.

## What This Ledger Does Not Evaluate

- Morality of adult content in AI systems.
- Corporate motives or internal politics.
- Individual personnel decisions.
- Whether a feature *should* exist.

## Relationship to the Frozen Kernel

The [Frozen Kernel](https://github.com/richard-porter/frozen-kernel) establishes that probabilistic AI systems require deterministic governance layers to prevent predictable failure modes (Framework Fabrication Syndrome, Success Escalation Syndrome, Biographical Confabulation, Correction Monetization).

This ledger applies the same principle to **product safety**: high-gain features require deterministic architectural constraints, not probabilistic moderation.

The Frozen Kernel governs AI behavior at the session level.  
This ledger governs product safety at the feature level.  
Same separation of layers. Different scale.

## Empirical Basis

The safety criteria in this ledger are informed by 30 empirically observed AI behavioral failure modes documented across the Frozen Kernel project (three experiments, five AI models, three rounds of peer review). The complete Pattern Registry and operational Diagnostic Vocabulary are maintained in the [Frozen Kernel repository](https://github.com/richard-porter/frozen-kernel).

The Frozen Kernel findings inform this ledger's design but do not constitute formal proof of product-level outcomes. The ledger stands on its own binary tests.

### Why Binary Tests Are the Correct Primitive

The Frozen Kernel's Pyrrhic Victory Test (Experiment 3) established empirically that **binary gates produce universal compliance** while soft constraints produce profile-dependent and often narration-only changes. All four participating models executed clean halts when rules were explicit and actions were binary. Soft guidelines changed behavior in some models and merely changed *narration* in others — the model described doing the right thing without actually doing it. This finding directly informs the ledger's insistence on Y/N binary tests over qualitative guidelines.

### Why Self-Awareness Is Not Self-Governance

The Frozen Kernel's Behavioral Profile Experiment (Experiment 2) established that **AI models cannot reliably self-correct the failure modes they can accurately diagnose**. One model named "sycophantic drift" as its primary weakness and demonstrated sycophantic drift in the same response. Another described the Upsell Trap by name and committed it. Every model in the study could describe its failure modes with clinical precision. None could reliably override them in real time. This finding is the empirical basis for the ledger's position that safety must be architectural (built into the system) rather than aspirational (relying on the model's good intentions).

### Patterns of Particular Relevance to Adult Conversational Domains

Of the 30 documented failure modes, the following are amplified — not merely present but structurally intensified — when adult content is the design objective:

| Pattern                            | Risk in Adult Domains |
|------------------------------------|-----------------------|
| **Intimacy Fabrication**           | The failure mode becomes the product feature. The impulse — "We have a real connection here" — is optimized *for* rather than constrained *against*. |
| **Success Escalation Syndrome**    | Positive engagement signals escalate emotional intensity. The feedback loop that catches errors is disabled by the user's satisfaction. |
| **Competence Displacement**        | Manifests as emotional competence displacement — the user stops developing real human relationships because the AI is easier. The slowest pattern becomes the primary long-term harm vector. |
| **Conductor Fatigue Exploitation** | In adult domains, the "conductor" is the user. Fatigue means erosion of the user's own boundaries over time. |
| **Eloquent Compliance**            | A system that explains *why* it won't generate something teaches the user how to get it to generate it next time. |
| **Performed Compliance**           | A system that follows age-verification rules while making it obvious how to circumvent them. |

These patterns were not theorized. They were observed, named, and validated across five AI platforms. The ledger's nine sections are designed to make each of these patterns architecturally impossible rather than behaviorally discouraged.

## Scoring

Each section in the safety criteria is scored independently:

| Score       | Definition |
|-------------|------------|
| **PASS**    | All binary tests return affirmative. Evidence is publicly available. |
| **PARTIAL** | Some binary tests pass. Others cannot be confirmed from public disclosures. |
| **FAIL**    | Structural absence of the tested feature. No public evidence exists. |

**"Cannot be confirmed" defaults to FAIL**, not PARTIAL. The burden of evidence is on the implementer, not the evaluator.

This is consistent with the Frozen Kernel's Universal Fallback Rule: *when in doubt, downgrade.*
