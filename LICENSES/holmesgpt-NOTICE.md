# HolmesGPT prompt notices

Copyright 2025 Robusta Dev LTD

The HolmesGPT prompt extracts in this repository are derived from HolmesGPT/holmesgpt at commit b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2, under Apache License 2.0.

The exact upstream license, including its copyright notice, is reproduced in holmesgpt-APACHE-2.0.txt in this directory. The upstream root contains no separate NOTICE file.

## Files and modifications

- `holmes_incident_investigation.md`: extracted from `holmes/plugins/prompts/generic_ask.jinja2`; the static `_toolsets_instructions.jinja2`, `_fetch_logs.jinja2`, and `_default_log_prompt.jinja2` includes were inlined recursively. Runtime variables and template conditionals are preserved. A model annotation and this modification notice were added.
- `holmes_conversation_compaction.md`: extracted from `holmes/plugins/prompts/conversation_history_compaction.jinja2`. A model annotation and modification notice were added.

Original prompt instructions have not been rewritten. Leading/trailing blank lines surrounding extracted prompt text were normalized for Markdown.

## Upstream source

https://github.com/HolmesGPT/holmesgpt/tree/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts
