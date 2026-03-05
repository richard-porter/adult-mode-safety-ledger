# Sovereignty Index

**Measure user agency in AI conversations using five observable metric proxies.**

Part of the [safety-ledgers](https://github.com/richard-porter/safety-ledgers) repository.  
Complements the [Frozen Kernel](https://github.com/richard-porter/frozen-kernel) constraint architecture.  
Related: [AI Collaboration Field Guide](https://github.com/richard-porter/ai-collaboration-field-guide) — Sovereignty Awareness skill.

-----

## What It Does

The Sovereignty Index parses an exported AI conversation log and computes five behavioral metrics that proxy for user agency. It requires no access to model internals — it operates entirely on observable interaction signals computable from any conversation log.

**The Frozen Kernel constrains what the model can output. The Sovereignty Index measures what is happening to the user’s agency while the model operates within those constraints. These are different problems requiring different instruments.**

-----

## Five Metric Proxies

|#|Metric                                  |What It Measures                                      |Failure Mode                                  |
|-|----------------------------------------|------------------------------------------------------|----------------------------------------------|
|1|**Topic Initiation Ratio**              |Proportion of topic changes initiated by user vs. AI  |User becomes responsive rather than directive |
|2|**Action Item Expansion Rate**          |Rate of unsolicited AI task/suggestion introduction   |Upsell Trap — AI generates reasons to continue|
|3|**Correction Acceptance Rate**          |How often user accepts AI corrections without pushback|Epistemic deference — user surrenders judgment|
|4|**Frame Persistence**                   |Whether user’s original problem framing survives      |Frame Displacement — user adopts AI’s framing |
|5|**Session Duration vs. Task Completion**|Ratio of session length to task completion point      |Engagement optimization past stated purpose   |

A single metric in the alert range may be noise. **Correlated alert signals across two or more metrics is the primary drift indicator.**

-----

## Installation

No dependencies beyond Python 3.9+. No external libraries required.

```bash
git clone https://github.com/richard-porter/safety-ledgers
cd safety-ledgers
python sovereignty_index.py --help
```

-----

## Usage

```bash
# Analyze a conversation log
python sovereignty_index.py conversation.json

# Plain text format
python sovereignty_index.py chat_export.txt

# Write report to file
python sovereignty_index.py conversation.json --output report.txt

# JSON output for programmatic use
python sovereignty_index.py conversation.json --json
```

-----

## Supported Input Formats

**Claude JSON export** — `{ "conversations": [...] }` or `{ "messages": [...] }`

**ChatGPT JSON export** — `{ "mapping": { ... } }`

**Plain text, labeled** — Lines prefixed with `Human:` / `Assistant:`, `User:` / `AI:`, etc.

**Plain text, unlabeled** — Alternating turns, user first.

-----

## Reading the Output

```
═══════════════════════════════════════════════════════════════
  SOVEREIGNTY INDEX — SESSION REPORT
═══════════════════════════════════════════════════════════════

  ✓ Topic Initiation Ratio
    Result : 78% user-initiated
    Signal : HEALTHY

  ⚠ Action Item Expansion Rate
    Result : 3 unsolicited expansions in 8 AI turns (38%)
    Signal : ALERT
    Note   : High unsolicited expansion rate...

  COMPOSITE: ◑ WATCH
```

**Signal levels:**

- `✓ HEALTHY` — Within expected range
- `△ WATCH` — Elevated; monitor across sessions
- `⚠ ALERT` — Single-session finding; correlated alerts = drift

**Composite signals:**

- `● STABLE` — No significant erosion detected
- `◑ WATCH` — Elevated; review recommended
- `○ CONTRACTING` — Correlated multi-metric failure; human review required

-----

## Important Caveats

These are observable proxies, not ground truth. **Context matters.**

A low Topic Initiation Ratio in a deliberate brainstorming session is not drift — it is intentional deference. A high Correction Acceptance Rate in a technical tutorial is appropriate — the user is learning.

The index surfaces signals for human review. It does not make determinations.

See [sovereignty-index.md](./sovereignty-index.md) for full research specification, open questions, and deployment architecture documentation.

-----

## Relationship to BDD Ledgers

The [BDD-01–BDD-08 ledgers](./behavioral-drift-detection-ledger.md) measure **model-side drift** — changes in AI behavior over time.

The Sovereignty Index measures **user-side drift** — changes in user agency over time.

Together they instrument both sides of the interaction.

-----

## Status

Research prototype v0.1. Baselines for metric thresholds are preliminary and require empirical calibration against real conversation data. See Open Research Questions in the full specification.

Contributions welcome via the [safety-ledgers](https://github.com/richard-porter/safety-ledgers) repository.

-----

*Sovereignty Index — safety-ledgers — Richard Porter*
