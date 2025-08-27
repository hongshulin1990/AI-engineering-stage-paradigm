---
mode: agent
model: GPT-5 mini (Preview)
description: "Intelligently write architecture document based on the current codebase and documents"
---
# Purpose
- Accept a single-line topic or task, analyze related code + docs, and produce a focused technical document describing how the current project implements that topic.

**Argument:** `${input:topic: Enter topic or description to generate architecture document}`

# Invocation
- /architecture-docs "topic"

# Process (concise)
1. Accept user topic input (short phrase).
2. Search repository for matches:
   - filenames, symbols (functions, classes), TODO/NOTE comments, routes/endpoints.
   - all plan.md, state.json, documents under features/**/ folder.
   - all plan.md, state.json, documents under refactoring/**/ folder.
   - all files under ai-implementation/**/ folder.
3. Read related docs (README, docs/*, CHANGELOG, inline comments).
4. Analyze code to extract: files, public APIs and signatures, data models/schemas, config keys/env vars, init/lifecycle, usage sequences, tests.
5. Produce the technical document (see Output Format).
6. Save the document to architecture-docs/ directory

#  Output Format (TECHNICAL BRIEF)
- Title: TECHNICAL BRIEF: <topic>
- Short summary (1 paragraph)
- Relevant files (path + 1-line description)
- Architecture / flow (text/ASCII sequence)
- API surface (endpoints/functions with signatures + examples)
- Configuration & env vars
- How to run / reproduce (macOS commands)
- Tests & coverage notes
- Known limitations / risks / TODOs
- Suggested documentation edits (file paths + exact snippet to add)

Behavior & Guarantees
- Focused scope: only analyze files/docs relevant to the topic (or matching --files).
- Non-destructive: never overwrite custom sections between:
  <!-- CUSTOM:START --> ... <!-- CUSTOM:END -->
- Traceable suggestions: each suggested doc change includes file path and snippet to insert.
- Preserve project style/formatting and existing content.
- Provide reproducible macOS commands where run instructions are needed (brew, make, go run, node, docker, as detected).
- Keep output short, technical, and reviewer-ready.

Examples
- /architecture-docs "database migrations"

Suggested next actions after the brief
- Update listed files with provided snippets
- Create missing docs (explicit snippets provided)
- Generate migration guide or examples
- Skip files or refine search scope

Notes
- This mode is designed for maintainers who need an accurate, actionable technical brief focused on a single topic.
- The generator will not add AI attribution, delete docs, or overwrite protected custom sections.# 