---
mode: agent
model: GPT-5 mini (Preview)
---
Commit changes to the codebase, including adding new features, fixing bugs, and improving performance. Ensure that all changes are well-documented and tested before committing.

**Your step-by-step process is as follows:**

1. Analyze the current session context
    - if current session is a feature, analyze the plan, state under features/{feature name}/ folder, conversations to identify the changes of codes.
    - if current session is a refactor, analyze the plan, state under refactor/{refactor name}/ folder, conversations to identify the changes of codes.
    - if can not identify the session type, analyze all relevant files, conversations and codebase changes via `git status`.
    - summarize the changes to summary no more than 10 words.
2. Ask user for input "Coding URL: <URL>" with tips of "continue or Coding URL", if the user input <URL> under the domain of "https://kikitrade.coding.net/" then append the <URL> to the commit message. If the user input is to continue, proceed to the next step.
3. Write a concise commit message following the `# Commit Message Guidelines`.
4. Commit the changes to the codebase.

# Commit Message Guidelines
Write a short english commit message (no more than 10 words) for every change you make, and always format it in a code block. Use the following guidelines for consistent and descriptive commit messages:

prefix: summary (no more than 10 words)

## Commit Prefixes:
feat: Introduce a new feature.
fix: Fix a bug or issue.
tweak: Make minor adjustments or improvements.
style: Update code style or formatting.
refactor: Restructure code without changing functionality.
perf: Improve performance or efficiency.
test: Add or update tests.
docs: Update documentation.
chore: Perform maintenance tasks or updates.
ci: Change CI/CD configuration.
build: Modify build system or dependencies.
revert: Revert a previous commit.
hotfix: Apply an urgent bug fix.
init: Initialize a new project or feature.
merge: Merge branches.
wip: Mark work in progress.
release: Prepare for a release.

