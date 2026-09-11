# Output contracts

Use only the sections requested by the user. Preserve their specified order when provided.

## Contents

- User journey evidence table
- Agent inventory
- Agent I/O contract card
- Tool contract
- Single-Agent functional prompt package
- Architecture analysis package
- Five-flow table
- Context architecture
- As-Is and To-Be
- Risk register

## User journey evidence table

| Stage | User goal | User action | Page feedback | Decision | Page/asset state change | Friction | Evidence |
|---|---|---|---|---|---|---|---|

Evidence must include exact visible text, button names, Agent name, visible asset/error, and screenshot ID.

The three-lane journey diagram uses only User, Product interface, and System result. Include normal, correction, and failure/interruption paths. Use diamond decisions with explicit branch labels such as satisfied/not satisfied, success/failure, continue/interrupt, and sufficient/insufficient balance.

## Agent inventory

| Agent | First appearance | Trigger | Predecessor | Observable work | Output/handoff | Re-entry | Evidence |
|---|---|---|---|---|---|---|---|

Record only Agents supported by evidence. Do not infer a fixed canonical Agent count.

## Agent I/O contract card

Use this fixed structure:

1. Agent name
2. Core objective
3. Trigger conditions
4. Inputs by source type: current user input, long-term user information, project global context, upstream Agent output, platform public assets/knowledge, tool or runtime result
5. Observable decisions
6. Tools, marking functional names as non-official
7. Outputs: user reply, page component, structured field, visual/audio/video asset, state, downstream task
8. Context reads/writes
9. Completion conditions
10. Exception and retry behavior
11. Unknowns

For context access, use:

| Field/object | Read/write | Producer | Consumer | Update time | Evidence class | Evidence |
|---|---|---|---|---|---|---|

## Tool contract

| Functional tool name | Agent | Preconditions | Inputs | Observable result | Validation | Failure/retry | State write | Evidence |
|---|---|---|---|---|---|---|---|---|

Do not invent official API names. Explicitly inspect confirmation requirements, duplicate charges/assets, interruption behavior, idempotency, and success-with-state-write-failure.

## Single-Agent functional prompt package

Deliver in this order:

1. target Agent evidence range and boundary;
2. input contract;
3. output contract;
4. tool contract;
5. state machine and Mermaid state diagram;
6. fact, inference, recommendation, and unknown rules;
7. functionally equivalent System Prompt;
8. rule-to-evidence traceability;
9. minimum tests;
10. unresolved questions.

The System Prompt uses:

1. Agent name and role
2. Core goal
3. Task boundary
4. Input contract
5. Global-context protocol
6. Workflow
7. Tool-call rules
8. User-confirmation mechanism
9. Result validation
10. Modification and rollback
11. Exception handling
12. State machine
13. Downstream handoff
14. Completion conditions
15. Output format

Do not present the prompt as recovered vendor text. Use semantic placeholder fields when real names are not visible and label them as derived design.

## Architecture analysis package

Recommended complete order:

1. one-sentence executive summary;
2. evidence sources and gaps;
3. functional domains;
4. end-to-end five-flow table;
5. layered product architecture;
6. Agent/tool/context relationship;
7. global-context architecture;
8. knowledge and public/private assets;
9. model access and routing;
10. infrastructure capability/option/recommendation table;
11. entity table and ER diagram;
12. end-to-end sequence diagram;
13. product panorama diagram;
14. As-Is;
15. To-Be;
16. prioritized risks;
17. component-to-evidence traceability;
18. unresolved questions.

## Five-flow table

| Step | Trigger | Handler | Reads | Decision | Tool | Result/asset | State write | Confirmation | Next/handoff | Failure branch | Evidence |
|---|---|---|---|---|---|---|---|---|---|---|---|

Represent interaction, Agent control, tools, data/context, and media assets either as columns, grouped rows, or parallel swimlanes.

## Context architecture

Use these as analytical template names, never as verified product field names without page evidence: UserContext, ProjectConfig, ScriptContext, CharacterContext, SceneContext, PropContext, StoryboardContext, AssetContext, WorkflowState, BillingContext, and EvaluationContext.

For each, document purpose, visible evidence, inferred fields, producer, consumer, versioning, invalidation, and evidence class.

## As-Is and To-Be

As-Is:

| Area | Confirmed behavior | Inferred mechanism | Current gap | Evidence |
|---|---|---|---|---|

To-Be:

| Gap | Recommendation | Mechanism | Success condition | Priority |
|---|---|---|---|---|

Always evaluate single source of truth, completion gate, quality validation, duration, style, dialogue/audio sync, dependency invalidation, idempotent retry, quota estimation/reservation, traceability, model feedback, local recomputation, and tenant isolation.

## Risk register

| Priority | Risk | Evidence or trigger | Impact | Likely cause | Recommended control |
|---|---|---|---|---|---|

Separate observed failures from hypothetical risks.
