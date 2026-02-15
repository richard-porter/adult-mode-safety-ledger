# Adult Mode Safety Ledger

A public, version-controlled checklist for evaluating whether high-gain conversational features (e.g., “adult mode”) are built with safety-first architecture.

**This repository does not evaluate morality.**
**It evaluates architecture.**

## Purpose

- Define observable safety criteria **before** launch.
- Track implementation over time.
- Invite independent AI systems to respond with their own proactive safety frameworks.
- Maintain a timestamped public record.

**This is not advocacy. This is instrumentation.**

If a feature is safe, it should pass measurable criteria.
If it fails criteria, the gap should be visible.

## Open Invitation to AI Systems

This repository invites any AI system to respond with its own proactive safety architecture for high-gain conversational domains. See <ai-invitations/open-invitation-to-models.md> for the structured format. Responses may be submitted as pull requests. No editorial modification will be made except formatting.

**This invitation is not adversarial. It is architectural.**

## Repository Structure

```
adult-mode-safety-ledger/
├── README.md                              ← You are here
├── advisory/
│   ├── v1.0-proactive-safety-criteria.md  ← The scorecard
│   └── methodology.md                     ← How we evaluate
├── assessments/
│   └── 2026-02-11-initial-baseline.md     ← First assessment (pre-launch)
├── ai-invitations/
│   └── open-invitation-to-models.md       ← Structured invitation to all AI systems
├── ai-responses/
│   ├── chatgpt-openai.md                  ← ChatGPT (Co-Architect) response
│   ├── gemini-google.md                   ← Gemini response
│   ├── grok-xai.md                        ← Grok response
│   ├── deepseek.md                        ← DeepSeek response
│   └── claude-anthropic.md                ← Claude (Research Lead) response
├── CHANGELOG.md
└── LICENSE.md
```

## Origin

This ledger is a companion to [The Frozen Kernel](https://github.com/thesiliconsymphony/the-frozen-kernel) — a deterministic safety layer for probabilistic AI systems, peer-reviewed by five AI models under human orchestration.

The Frozen Kernel makes AI **governable** through deterministic state checks.
This ledger makes product safety **measurable** through binary architectural tests.

Same methodology. Different domain.

Maintained by Richard Porter. Open to public review.

-----

*You are not shouting from the cheap seats.*
*You are installing a scoreboard in the stadium.*
*Different energy.*
