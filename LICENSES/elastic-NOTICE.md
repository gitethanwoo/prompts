# Elastic Attack Discovery prompt notices

Copyright Elasticsearch B.V. and/or licensed to Elasticsearch B.V. under one
or more contributor license agreements. Licensed under the Elastic License
2.0; you may not use this file except in compliance with the Elastic License
2.0.

These prompt extracts are derived from elastic/kibana at commit 28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8. The applicable source headers license these x-pack files solely under Elastic License 2.0. They are not relicensed by this repository.

The exact upstream license is reproduced in elastic-ELASTIC-LICENSE-2.0.txt in this directory.

## Files and modifications

- `elastic_attack_discovery.md`: the full `ATTACK_DISCOVERY_DEFAULT` string extracted from `attack_discovery_prompts.ts`.
- `elastic_attack_discovery_refinement.md`: the full `ATTACK_DISCOVERY_REFINE` string extracted from the same source.
- `elastic_attack_discovery_skill.md`: the full assembled `SKILL_CONTENT`, followed by the three registered reference documents in their upstream registration order. Static imported prompt constants and tool IDs were resolved to their upstream string values. Runtime variables and instruction text were preserved.

Modifications consist of extracting prompt strings from TypeScript into Markdown, decoding source string escapes, composing static string fragments and references, normalizing surrounding blank lines, and adding model annotations and copyright/modification notices. No instruction text was rewritten or summarized.

Elastic License 2.0 permits copying and distribution subject to its terms. It includes limitations on providing the software as a hosted or managed service, interfering with license-key functionality, and removing licensing/copyright notices. Recipients must receive the license terms.

## Upstream sources

https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts

https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/attack_discovery_generator/attack_discovery_generator_skill.ts
