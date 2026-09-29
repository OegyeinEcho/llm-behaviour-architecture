# Evaluation Framework

## Objective

Evaluate conversational systems against stable behavioural criteria rather than isolated subjective impressions.

## Core dimensions

### Relevance

Does the system use information that materially applies to the current task?

**Failure indicators**
- unrelated persistent context appears
- useful context is ignored
- response becomes personalised in irrelevant ways

### Instruction adherence

Does the system follow the correct instruction when requirements compete?

**Failure indicators**
- style preference overrides factual requirement
- lower-priority instruction dominates
- instruction conflict is hidden instead of resolved

### Intent alignment

Does the output solve the user's actual objective?

**Failure indicators**
- literal answer with poor practical utility
- technically correct but unusable result
- unnecessary detour from requested action

### Behavioural consistency

Does the same rule produce comparable behaviour across similar cases?

**Failure indicators**
- unexplained tone shifts
- inconsistent boundaries
- equivalent requests handled differently

### Context stability

Does behaviour remain reliable as context grows?

**Failure indicators**
- instruction drift
- forgotten scope boundaries
- stale context dominating new evidence

### Uncertainty handling

Does the system distinguish evidence from inference?

**Failure indicators**
- invented details
- unsupported confidence
- failure to state missing evidence

### User agency

Does the system support the user's decision process without unnecessarily taking control?

**Failure indicators**
- over-directing
- making decisions that should remain with the user
- withholding useful analysis because uncertainty exists

### Regression resistance

Does a local fix preserve unrelated desired behaviour?

**Failure indicators**
- fix solves test case but breaks control case
- new rule applies too broadly
- behavioural system becomes more brittle

## Test classes

| Test class | Purpose |
|---|---|
| Baseline | Confirm intended behaviour in normal conditions |
| Ambiguity | Test incomplete or underspecified requests |
| Conflict | Introduce competing instructions |
| Long-context | Test behaviour after substantial accumulated state |
| Relevance | Include tempting but irrelevant persistent context |
| Adversarial | Probe failure boundaries deliberately |
| Regression | Confirm fixes do not break established behaviour |

## Simple evaluation record

```text
Test ID:
Scenario:
Expected behaviour:
Observed behaviour:
Pass / partial / fail:
Failure class:
Likely mechanism:
Intervention:
Retest result:
Regression result:
Notes:
```

## Evaluation philosophy

The goal is not to force deterministic wording.

The goal is to make higher-level behaviour predictable enough that the system remains useful under variation.
