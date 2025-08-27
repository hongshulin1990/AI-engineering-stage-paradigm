---
mode: agent
model: GPT-5 mini (Preview)
---
# Your Task
Group the documents by topic. Consolidate the content of the same topic markdown documents into a topic based single, comprehensive, and well-structured document.

## Topic Identification
The documents share a common topics. For example, 2025-01-28_feature_artemis_sdk_migration.md and 2025-06-24_feature_artemis_service.md are both about "Artemis Integration".2025-08-19T220000_feature_http_endpoint_tdd_implementation.md and 2025-08-20T001200_Refactor_http_endpoint_cross_check.md are both about "HTTP Endpoint".

You may got input from user, the input could be topic name or topic description.

**Argument:** `${input:topics: Enter topic or description to group}`

analyze ${input:topics}:
- if the input is "all", then you have to analyze all documents in the repository.
- If no input is provided, you have to ask the user for the topic or description with tips: "Input \"all\" or specific topics".
- if user reply "all", then you have to go through all documents to analyze the content and learn the topics.

## Core Instructions

- Analyze the documents thoroughly to understand their content and context.
- Identify Key Themes: Look for recurring themes, concepts, or keywords across the documents. This will help in grouping them effectively.
- Establish Connections: Determine how the documents relate to each other. Are they part of a larger project? Do they address different aspects of the same problem? Understanding these relationships will aid in consolidation.
- Group by Topic: Based on the identified themes and connections, group the documents into ${input:topics}. This will make it easier to consolidate their content.
- Repeat Topic Analysis for Each Group and Synthesize documents:
    - Read and understand the content of each document. Identify the purpose of each one (e.g., initial feature, bug fix, refactor, enhancement).
    - Generate New File Name: Propose a new, descriptive file name for the consolidated document, following the rule: "Implementation document rules" defined in `../copilot-instructions.md`.
    - Think and synthesize the new document in very detail as a principal architect. Start with a summary of the overall topic, then present the implementation details in a coherent way. If the documents represent a chronological progression, reflect that in the new document.