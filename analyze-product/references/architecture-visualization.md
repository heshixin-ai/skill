# Architecture visualization specification

## General rules

1. Lead with one main diagram; use supporting ER, sequence, state, or swimlane diagrams only when they clarify different relationships.
2. Put components from the same layer in the same container or Mermaid `subgraph`.
3. Label every important edge with a semantic action: call, read, write, event, confirmation, asset reference, status update, invalidation, retry, or handoff.
4. Show critical data and state nodes, not only service boxes.
5. Attach evidence IDs to important nodes or include a traceability table next to the diagram.
6. Keep current architecture, inference, recommendation, unknown, and conflict visually distinct.

Recommended visual semantics:

- green solid: confirmed;
- amber dashed: reasonable inference;
- blue thick: recommended design;
- gray dotted: unknown;
- red: observed conflict or failed completion.

Include a legend in every standalone architecture diagram.

## Product panorama

Default top-to-bottom layers:

1. users and channels;
2. interaction and workbench;
3. product applications;
4. Agent and workflow orchestration;
5. tools and services;
6. model access and routing;
7. global context and data;
8. knowledge and public/private assets;
9. infrastructure and governance.

Combine adjacent layers when a single image would otherwise become unreadable. Preserve the semantic distinction through internal panels.

The main diagram should let a product manager answer where demand enters, who chooses the Agent, where inputs come from, which tools are called, who generates media, where assets are stored and versioned, how handoff and modification work, how failures and billing blocks work, where knowledge comes from, how identity consistency is maintained, why state surfaces disagree, and what proves true completion.

## Mermaid

Use quoted Mermaid labels when labels contain punctuation or parentheses. Prefer `flowchart TB` for architecture, `sequenceDiagram` for execution, `stateDiagram-v2` for Agent states, and `erDiagram` for analytical entities.

Do not use Mermaid node IDs as user-facing component names. Keep IDs short and put readable text in labels.

## HTML deliverable

1. Make it responsive and readable without editing.
2. Add a compact table of contents for long reports.
3. Use consistent evidence badges.
4. Keep tables horizontally scrollable.
5. Embed Mermaid using a supported pinned version when internet access is acceptable; otherwise provide SVG fallback or state the dependency.
6. Parse-check the HTML and count expected sections and diagram blocks.
7. Avoid leaking local source paths except through explicit deliverable links.

## SVG and PNG deliverable

For a text-dense architecture image, prefer deterministic SVG over generative image synthesis so labels remain exact.

1. Match the user's visual reference through layout, spacing, palette, containers, arrows, and typography without copying unrelated content.
2. Use rounded pastel layer panels, lightly tinted cards, and clear left-side layer labels when the reference uses this format.
3. Keep editable SVG as the source of truth.
4. Validate with `xmllint --noout` when available.
5. Render a full-height PNG using a deterministic renderer such as headless Chrome, not a square thumbnail generator.
6. Inspect for clipping, text overlap, arrow collisions, and evidence legend accuracy.
7. Preserve both `.svg` and `.png` unless the user asks for only one format.

## Sequence diagram

Choose participants supported by evidence, then add inferred system services only with explicit status. Show input, parameter confirmation, context write, Agent call, tool call, asynchronous wait, asset writeback, user confirmation, modification, failure, interruption, and downstream handoff.

## Entity diagrams

State that entity names are analytical unless the product exposes real schema names. Mark relationships with direct page evidence separately from inferred relationships. Include version and confirmation entities when they explain visible behavior.

## Final visual QA

- Verify all required layers are present.
- Verify legend meanings match node and edge styles.
- Verify no recommendation is presented as current implementation.
- Verify conflicts remain visible rather than being resolved silently.
- Verify the PNG includes the entire SVG canvas.
- Verify output dimensions and file paths.
