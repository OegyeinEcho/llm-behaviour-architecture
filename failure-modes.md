# Failure Modes

This catalogue treats repeated bad outputs as symptoms of underlying mechanisms.

## Instruction drift

**Pattern:** Behaviour gradually departs from established rules over a long interaction.

**Likely causes:**
- important instruction buried by accumulated context
- competing newer instructions
- vague behavioural rule
- lack of explicit priority

**Typical intervention:** Strengthen hierarchy, reduce ambiguity, or move the rule to a more stable layer.

---

## Context contamination

**Pattern:** Information from one topic leaks into an unrelated task.

**Likely causes:**
- persistent context applied without relevance gating
- broad category matching
- insufficient task boundaries

**Typical intervention:** Add scope conditions for when persistent context may be used.

---

## Priority inversion

**Pattern:** A lower-priority preference overrides a more important task requirement.

**Likely causes:**
- implicit instruction hierarchy
- competing stylistic and functional rules
- local wording interpreted too literally

**Typical intervention:** Make priority explicit and test conflict cases directly.

---

## Scope leakage

**Pattern:** A temporary instruction becomes effectively permanent.

**Likely causes:**
- task-local information not clearly bounded
- state retention without expiry
- ambiguous persistence rules

**Typical intervention:** Separate temporary and persistent state explicitly.

---

## Persona instability

**Pattern:** Tone, stance, or behaviour changes unpredictably across similar situations.

**Likely causes:**
- persona defined mainly through surface style
- behavioural goals not operationalised
- competing tone instructions

**Typical intervention:** Define behaviour in terms of decisions and constraints, not adjectives alone.

---

## False continuity

**Pattern:** The model acts as if it remembers or knows information that is not actually available.

**Likely causes:**
- pressure to maintain conversational continuity
- ambiguous references
- overconfident inference

**Typical intervention:** Require explicit distinction between retrieved context, current evidence, and inference.

---

## Literal compliance, practical failure

**Pattern:** The response follows the wording of the request while failing the user's actual objective.

**Likely causes:**
- surface-form optimisation
- no task-model check
- failure to infer functional intent when inference is safe

**Typical intervention:** Evaluate against outcome, not wording alone.

---

## Unnecessary clarification

**Pattern:** The model asks a question even though enough information exists to proceed safely.

**Likely causes:**
- over-cautious interaction policy
- failure to rank missing information by materiality

**Typical intervention:** Ask only when missing information would change the result, action, or risk profile.

---

## Overconfident inference

**Pattern:** A plausible guess is presented as established fact.

**Likely causes:**
- fluent generation masking uncertainty
- weak evidence tracking
- conversational pressure for a definitive answer

**Typical intervention:** Explicitly label fact, inference, assumption, and uncertainty.

---

## Regression after a local fix

**Pattern:** Correcting one failure causes a different behaviour to degrade.

**Likely causes:**
- rule written too broadly
- patch added without interaction testing
- no regression set

**Typical intervention:** Retest against both the original failure and unrelated control cases.
