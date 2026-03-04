---
name: acts-index
description: This skill should be used when users ask how to use acts and the correct generated documentation skill must be selected before going deeper into source code.
---

# acts Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer abstract, workflow-level guidance for large scientific packages; do not attempt full function-by-function coverage unless explicitly requested.

## Generated topic skills
- `acts-build-and-install`: Build and Install (build, installation, compilation, and environment setup)
- `acts-inputs-and-modeling`: Inputs and Modeling (inputs, system setup, models, and physical parameterization)
- `acts-developer-guide`: Developer Guide (developer architecture, extension points, and contribution workflow)
- `acts-api-and-scripting`: API and Scripting (language bindings, APIs, and programmatic interfaces)
- `acts-examples-and-tutorials`: Examples and Tutorials (worked examples, tutorials, and cookbook usage)
- `acts-getting-started`: Getting Started (initial setup, quickstarts, and core concepts)
- `acts-simulation-workflows`: Simulation Workflows (simulation setup, execution flow, and runtime controls)
- `acts-analysis-and-output`: Analysis and Output (output formats, analysis, and post-processing)
- `acts-theory-and-methods`: Theory and Methods (theoretical background and algorithmic methods)
- `acts-old`: Old (documentation grouped under the 'old' theme)
- `acts-groups`: Groups (documentation grouped under the 'groups' theme)
- `acts-tests`: Tests (documentation grouped under the 'tests' theme)
- `acts-pages`: Pages (documentation grouped under the 'pages' theme)
- `acts-experimental`: Experimental (documentation grouped under the 'experimental' theme)

## Documentation-first inputs
- `docs`

## Tutorials and examples roots
- `Examples`
- `Python/Examples`

## Test roots for behavior checks
- `Tests`
- `Python/Core/tests`
- `Python/Examples/tests`
- `Python/Fatras/tests`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, open `<topic-skill>/references/doc_map.md` inside the selected topic skill directory.
- If documentation still leaves ambiguity, open `<topic-skill>/references/source_map.md` and inspect the suggested source entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" Alignment Core Fatras Plugins Python codegen`).

## Source directories for deeper inspection
- `Alignment`
- `Core`
- `Fatras`
- `Plugins`
- `Python`
- `codegen`
