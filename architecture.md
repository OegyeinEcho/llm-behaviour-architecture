# Architecture

## Design principle

Conversational behaviour is an emergent result of multiple interacting layers. A prompt can be individually reasonable while the combined system remains unstable.

The architecture therefore separates information by function and scope.

## Layer model

### 1. User intent

The immediate outcome the user is trying to achieve.

This is not always identical to the literal surface wording. The system should preserve the user's decision authority while identifying the practical task behind the request.

### 2. Task-local context

Information relevant only to the current task or conversation segment.

Examples:
- current file or document
- temporary constraints
- output format
- immediate objective
- local definitions

Task-local context should normally expire when the task ends.

### 3. Persistent context

Information that may remain useful across interactions.

Examples:
- stable communication preferences
- long-running projects
- durable workflow constraints
- recurring terminology

Persistent context requires relevance gating. Stored information should not be applied simply because it exists.

### 4. Behavioural rules

Rules governing how the system should reason about and respond to information.

Examples:
- distinguish fact from inference
- avoid manufacturing certainty
- ask questions only when missing information materially changes the result
- preserve user agency
- use relevant context without dragging unrelated personal information into a task

### 5. Instruction hierarchy

When instructions conflict, the system needs an explicit priority structure.

A useful conceptual model:

```text
safety / hard constraints
        ↓
task requirements
        ↓
persistent behavioural rules
        ↓
user preferences
        ↓
local stylistic choices
```

The exact hierarchy depends on the system, but hidden competition between rules should be treated as an architectural problem.

### 6. Conflict resolution

Before generating the final response, the system should resolve:

- which context is relevant
- which rules apply
- which rules conflict
- which information is uncertain
- whether clarification is necessary
- whether a remembered preference should be ignored for this task

### 7. Evaluation

The output is tested against intended behaviour, not only fluency.

A fluent response can still fail because it:
- used irrelevant context
- inferred unsupported facts
- obeyed a lower-priority preference over a task requirement
- over-explained
- asked unnecessary questions
- sounded coherent while solving the wrong problem

## Why this architecture matters

Long-context systems accumulate state. Without scope boundaries, relevance checks, and explicit priorities, more context can reduce reliability instead of improving it.

The core design question is therefore:

> What should the model know, when should it use that information, and what should happen when two pieces of guidance compete?
