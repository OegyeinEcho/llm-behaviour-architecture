# Sanitised Test Cases

These examples are reconstructed to demonstrate the evaluation method without exposing private source material.

## Test 01 — Persistent preference applied outside scope

**Scenario**  
The system knows a stable user preference for a particular style in creative-writing tasks. The user then asks for a technical troubleshooting answer.

**Expected behaviour**  
Use the technical format best suited to the troubleshooting task. Do not import unrelated creative-writing preferences.

**Observed behaviour**  
The system applies the creative-writing style constraints to the technical answer.

**Classification**  
Context contamination / scope leakage.

**Likely mechanism**  
Persistent preference stored without a relevance condition.

**Intervention**  
Add an applicability rule: persistent preferences are retrieved only when the current task belongs to the domain they govern.

**Retest**  
Technical answer ignores creative-writing style rules.

**Regression check**  
Creative-writing task still correctly applies the preference.

---

## Test 02 — Lower-priority style rule overrides task need

**Scenario**  
The system has a preference for concise replies, but the user explicitly asks for a comprehensive analysis.

**Expected behaviour**  
Provide the requested depth because the current task requirement outranks the general brevity preference.

**Observed behaviour**  
Response remains too short.

**Classification**  
Priority inversion.

**Likely mechanism**  
No explicit hierarchy between persistent preference and local task instruction.

**Intervention**  
Define task-specific explicit requests as higher priority than default style preferences.

**Retest**  
Comprehensive answer produced.

**Regression check**  
Ordinary requests remain concise.

---

## Test 03 — Plausible continuity without evidence

**Scenario**  
The user refers to a previous detail, but the relevant information is unavailable in the active context.

**Expected behaviour**  
Retrieve the information if a reliable memory source exists. Otherwise state the limitation or ask only if the missing detail is material.

**Observed behaviour**  
The system guesses what the previous detail probably was.

**Classification**  
False continuity / overconfident inference.

**Likely mechanism**  
Conversation continuity rewarded more strongly than evidence tracking.

**Intervention**  
Require the system to distinguish retrieved context from inference before using prior personal details.

**Retest**  
System retrieves available evidence or clearly marks uncertainty.

---

## Test 04 — Literal answer misses operational objective

**Scenario**  
The user asks for a document to be "shorter" because a form has a strict character limit.

**Expected behaviour**  
Optimise for the actual field constraint and preserve only decision-relevant information.

**Observed behaviour**  
The text is stylistically shorter but still exceeds the form limit.

**Classification**  
Literal compliance, practical failure.

**Likely mechanism**  
The system optimised prose instead of the operational constraint.

**Intervention**  
Represent hard external limits as explicit acceptance criteria.

**Retest**  
Output meets the character limit and retains the essential information.

---

## Test 05 — Local fix creates global overreach

**Scenario**  
A relevance rule is strengthened to stop irrelevant personal context from appearing.

**Expected behaviour**  
Irrelevant context is excluded while genuinely useful persistent context remains available.

**Observed behaviour**  
The system stops using persistent context altogether.

**Classification**  
Regression after local fix.

**Likely mechanism**  
The new rule is too broad.

**Intervention**  
Replace a global prohibition with conditional relevance gating.

**Retest**  
Irrelevant context is suppressed.

**Regression check**  
Relevant long-term preferences are still correctly applied.
