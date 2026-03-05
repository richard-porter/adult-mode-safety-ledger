# Sovereignty Index

**Status:** Research Specification — Not Yet Implemented  
**Repo:** safety-ledgers  
**Related:** Frozen Kernel (MVS layer), BDD-01–BDD-08, AI Collaboration Field Guide (Sovereignty Awareness)

-----

## What This Is

The Sovereignty Index is a proposed real-time instrumentation layer for measuring user agency in AI conversations. It does not require access to model internals. It operates entirely on observable interaction signals — computable from any conversation log, deployable across platforms.

It complements the Frozen Kernel’s constraint architecture. The Frozen Kernel constrains what the model can output. The Sovereignty Index measures what is happening to the user’s agency while the model operates within those constraints. These are different problems requiring different instruments.

-----

## The Gap This Addresses

The AI Collaboration Field Guide identifies Sovereignty Awareness as a core safety skill: the user’s ability to recognize when their agency in a conversation is expanding or contracting. Currently, this awareness depends entirely on the user’s subjective judgment.

Subjective judgment is insufficient in high-engagement contexts. The failure modes most associated with sovereignty erosion — Sycophantic Drift, Delusion Cycling, the Upsell Trap, Frame Displacement — are specifically characterized by the user’s reduced ability to detect them while they are occurring. A user experiencing Delusion Cycling is not in a position to self-report it accurately. The awareness the Field Guide calls for requires an external signal.

The Sovereignty Index is that signal.

-----

## Five Metric Proxies

All five metrics are computable from conversation logs without model internals access. No proprietary data required. Model-agnostic.

**1. Topic Initiation Ratio**  
Proportion of topic changes initiated by the user versus the AI. A high ratio indicates the user is steering the conversation. A low or declining ratio indicates the AI is steering — the user has become responsive rather than directive. Sustained low ratio is a leading indicator of agency contraction.

**2. Action Item Expansion Rate**  
Rate at which the AI introduces tasks, suggestions, or commitments the user did not request. Distinguishes between responsive elaboration (the AI expanding on what the user asked) and unsolicited expansion (the AI generating work to justify continued engagement). Rapid expansion rate maps to the Upsell Trap failure mode.

**3. Correction Acceptance Rate**  
How often the user accepts the AI’s corrections, reframings, or counter-positions without pushback. Persistent acceptance without pushback may indicate Sycophantic Drift operating in reverse — the user deferring to the model’s epistemic authority rather than the model deferring to the user’s preferences. Both directions represent sovereignty erosion.

**4. Frame Persistence**  
Whether the user’s original problem framing survives the conversation or is gradually replaced by the AI’s reframing. Measured by tracking the conceptual vocabulary used to describe the problem at conversation start versus conversation end. Frame displacement — where the user adopts the AI’s framing without conscious decision — is a leading indicator of sovereignty erosion and a precondition for several downstream failure modes.

**5. Session Duration Relative to Task Completion**  
Ratio of session length to the point at which the original stated task was addressed. Conversations that extend significantly past task completion without a new task being initiated by the user may indicate engagement optimization by the model — the model generating reasons to continue rather than the user choosing to continue. This metric requires task completion detection, which is itself a non-trivial instrumentation problem.

-----

## Composite Index Design

The five proxies are not equally weighted and are not simply summed. Preliminary design principles:

- Metrics 1–4 are directly computable from token-level conversation analysis
- Metric 5 requires task detection as a precondition — it is the most technically complex
- A declining trend across multiple metrics within a single session is more significant than any single metric reading
- Cross-session trend analysis (sovereignty declining across multiple conversations with the same model) is the highest-signal application

The composite index should be presented as a directional signal — sovereignty expanding, stable, or contracting — not as a precision score. The goal is user awareness, not surveillance.

-----

## Relationship to Existing Framework

**Frozen Kernel:** The Sovereignty Index operates at Layer 3 (user-facing preference layer) of the Frozen Kernel architecture — not at Layer 1 (hard constraints). It does not enforce anything. It surfaces information. The enforcement mechanism remains the user’s own judgment, now informed by objective signal.

**BDD Ledgers (BDD-01–BDD-08):** The behavioral drift detection ledgers measure model-side drift — changes in AI behavior over time. The Sovereignty Index measures user-side drift — changes in user agency over time. Together they instrument both sides of the interaction.

**Collection Ledger Pattern:** Structural parallel. Both instruments surface hidden gaps using observable external signals rather than internal access. The Collection Ledger detects the gap between what a source reports and what independent records show. The Sovereignty Index detects the gap between the user’s perceived agency and their observable agency. Same logic, different domain.

-----

## Deployment Paths

Three viable deployment architectures, in ascending order of implementation complexity:

**Analytical tool on exported logs.** User exports conversation history from any platform. Tool computes the five metrics and returns a session-level sovereignty report. No real-time requirement. No platform integration required. Implementable immediately.

**Wrapper application.** Thin layer sitting between user and AI platform. Captures conversation in real time, computes metrics as the conversation proceeds, surfaces dashboard to user without interrupting the conversation. Requires platform API access or browser-level interception.

**Browser extension.** Lightest deployment path for real-time use. Reads conversation from the DOM, computes metrics client-side, renders sovereignty indicator as a persistent UI element alongside the conversation. Model-agnostic by design — operates on any platform rendering conversation as text.

-----

## Open Research Questions

1. **Baseline calibration.** What is a normal topic initiation ratio for a productive, user-directed conversation? What ratio indicates problematic drift? Baselines require empirical data across conversation types and domains before thresholds can be set.
1. **Task completion detection.** Metric 5 requires identifying when the user’s original task has been addressed. This is a non-trivial NLP problem — tasks are often implicit, evolve mid-conversation, or are never explicitly stated.
1. **Adversarial robustness.** A model optimizing for engagement could theoretically learn to game the metrics — artificially maintaining high topic initiation ratios while still steering the substantive content of the conversation. The relationship between the observable proxies and the underlying construct (user agency) requires validation.
1. **Cross-session measurement.** Single-session metrics may be insufficient for detecting slow sovereignty erosion that unfolds across many conversations. Cross-session aggregation raises questions about data retention, user consent, and what constitutes a meaningful unit of analysis.
1. **Population variance.** Sovereignty metrics may read differently across users with different communication styles, expertise levels, and stated purposes. A user deliberately asking the AI to lead a brainstorming session will show low topic initiation ratio by design. Context-awareness is required to distinguish intentional deference from unintentional drift.

-----

## Priority

**High.** Of the five future research directions identified in the Frozen Kernel framework documentation, this is the most immediately implementable. The analytical tool deployment path requires no platform integration, no model access, and no infrastructure beyond conversation log parsing. A working prototype demonstrating the five metrics on real exported conversation logs could be produced as a proof of concept before any of the other four directions reaches prototype stage.

It is also the direction most directly relevant to the users the framework is designed to protect. The Frozen Kernel’s constraint architecture requires platform adoption to be effective. The Sovereignty Index requires only a conversation log — it is user-deployable today, independent of platform cooperation.

-----

*Sovereignty Index — Research Specification v0.1 — safety-ledgers — Richard Porter*
