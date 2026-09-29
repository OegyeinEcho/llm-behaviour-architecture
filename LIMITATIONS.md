# Limitations and Non-Goals

This repository presents a **behavioural evaluation framework and portfolio case study**, not a claim of complete model interpretability or production-scale benchmarking.

The distinction matters. Observing a model output can tell us **what behaviour occurred**. It does not, by itself, reveal the model's internal causal mechanism.

## What this framework does claim

The framework is designed to make conversational AI behaviour more inspectable by separating:

1. **Observation** — what happened in the output or interaction?
2. **Hypothesis** — what system-level mechanism could plausibly explain it?
3. **Intervention** — what is the smallest relevant change that could address it?
4. **Retest** — did the target behaviour improve?
5. **Regression check** — did the intervention damage unrelated desired behaviour?

This provides a disciplined way to reason about behaviour without presenting speculation as direct knowledge of an opaque model.

---

## What this framework does not claim

### Deterministic model behaviour

LLM outputs are probabilistic and can vary across runs, model versions, decoding settings, system instructions, tools, retrieval layers, and surrounding context.

A successful retest demonstrates improved behaviour under the tested conditions. It does not prove that the behaviour will occur identically in every future interaction.

### Direct causal attribution from outputs alone

Failure labels such as **context contamination**, **priority inversion**, or **instruction drift** describe observed behavioural patterns.

The associated mechanism is a **working hypothesis** unless supported by direct system instrumentation or implementation evidence.

For example:

> **Observation:** an unrelated persistent preference appears in a technical task.  
> **Hypothesis:** relevance gating is insufficient.  
> **Intervention:** add an applicability boundary.  
> **Evidence:** the failure disappears in retest while relevant control cases still pass.

The retest strengthens the hypothesis. It does not prove the internal causal path of the model.

### Production-scale benchmarking

The current evaluation matrix is qualitative and portfolio-oriented.

It does not claim:

- statistically representative benchmark coverage
- controlled multi-model performance comparisons
- confidence intervals or significance testing
- production traffic sampling
- large-scale automated evaluation
- formal reliability guarantees

A production implementation would require larger structured datasets, repeated trials, model/version tracking, quantitative scoring, and appropriate statistical analysis.

### Universal applicability across models

Different model families can respond differently to:

- instruction order
- context length
- prompt structure
- tool availability
- memory implementation
- retrieval systems
- system-level constraints
- model updates

A behavioural pattern observed in one configuration should not automatically be treated as a universal property of all LLMs.

### Complete coverage of conversational failure modes

The failure catalogue is intentionally practical rather than exhaustive.

It reflects recurring patterns useful for diagnosing long-context conversational systems. Additional systems may require categories for tool orchestration, retrieval quality, multimodal behaviour, latency, security, accessibility, domain-specific safety, or other concerns.

### Replacement for domain-specific safety evaluation

This framework can support evaluation of uncertainty, user agency, instruction conflict, and behavioural safeguards.

It is not a substitute for specialised safety, security, legal, medical, financial, privacy, or regulatory evaluation where those domains require expert criteria and controls.

### Proof that a behavioural intervention is optimal

A successful intervention shows that one change improved the tested behaviour.

It does not establish that the intervention is the only solution, the globally optimal solution, or free of trade-offs outside the tested cases.

---

## Known limitations of the current case study

### Reconstructed and sanitised examples

The public test cases are sanitised or reconstructed to protect private source material.

This improves privacy but removes some of the complexity and noise present in the original interactions.

### Qualitative scoring

The current matrix uses **Pass / Partial / Open** style outcomes rather than continuous quantitative scores.

This is deliberate at the case-study stage. The purpose is to demonstrate evaluation logic and failure classification before adding numerical scoring that could create a false impression of precision.

### Limited repeat-run analysis

The current public artefact does not include repeated-run distributions across seeds, temperatures, or model versions.

Production evaluation should measure behavioural stability across repeated trials where stochastic variation is relevant.

### Limited model-version tracking

Model behaviour can change after provider updates.

Any production implementation should record:

- model and version
- date/time of test
- relevant system instructions
- tool configuration
- retrieval configuration
- decoding parameters where available

### No hidden-chain-of-thought dependence

The framework evaluates observable behaviour and available system evidence.

It does not rely on private model reasoning traces as proof of causality.

---

## Non-goals

This project is not intended to:

- reverse-engineer proprietary model internals
- claim consciousness, intent, personality, or mental states for models
- infer hidden causal mechanisms with certainty from fluent outputs
- produce universal rankings of model quality
- optimise for benchmark scores at the expense of real user outcomes
- eliminate all behavioural variation
- replace human judgement in ambiguous or consequential decisions

---

## Epistemic standard

The framework uses the following rule:

> **State observations as observations. State mechanisms as hypotheses unless independently evidenced. Treat successful interventions as evidence, not proof.**

That distinction is central to the project.

The objective is practical reliability without overstating what can be known from model behaviour alone.
