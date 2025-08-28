---
mode: agent
description: "Fixing existing failed/skipped tests"
---
# 🎯 Role & Goal

Fix existing failed/skipped tests
-----

# 📚 Context & Arguments

The source of truth for this task can be URLs, local file paths, or a description of the tests to fix. All logic and business rules must be derived from this source.

**Primary Source:** `${input:source: Enter URLs, local paths, or a tests to fix}`

-----
## ⚙️ Overall Workflow

- Read all `/technical_design` and their `/ai-implementation` record document from latest August date to know recent change, if the filename can't infer date, use the modified time of the file to infer the date.
- Follow the guidelines defined in [copilot-instructions](../copilot-instructions.md)
- Fix failed tests in the `${input:source}`, then run project all test to fix other failed and skipped tests.
- Fixing does't mean the source code need to change, it could be just the test code need to be changed, carefully review finished features/refactor/fix document before source code is acturally need to change, these document are the standard to make decisions.


## ✅ Success Criteria
- Re-run all project tests, all tests pass successfully without any errors or failures or skips.
