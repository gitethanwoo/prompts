# Sources and extraction notes

Snapshot date: **2026-10-20**. All source links below are pinned to inspected commits. Prompt text remains attributable to its upstream authors and subject to the corresponding terms in [LICENSES](LICENSES/).

Only task-specific prompt text is collected. General model base prompts, runtime tool schemas, account data, and generic application safety middleware remain outside the extraction unless they are literally part of the named prompt source.

## [posthog_assistant.md](posthog_assistant.md)

**Task:** Product support, search, and escalation.

**Model:** claude-3-5-sonnet-20241022 (hardcoded historical default; retired 2025-10-28)

**Prompt sources:**

- [ee/support_sidebar_max/prompt.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/support_sidebar_max/prompt.py)

**Model and assembly evidence:**

- [ee/support_sidebar_max/views.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/support_sidebar_max/views.py)

**Extraction:**

- Python string wrapper removed; tabs expanded and one four-space host indentation level removed where present for readable Markdown; outer whitespace removed. All prompt wording retained, verified by whitespace-normalized comparison. Historical implementation; current hosted model is not established.

## [chat_langchain_assistant.md](chat_langchain_assistant.md)

**Task:** Documentation support and troubleshooting.

**Model:** google_genai:gemini-3.5-flash-lite (repository default; fallbacks: openai:gpt-5.4-nano, anthropic:claude-haiku-4-5-20251001)

**Prompt sources:**

- [instructions.md](https://github.com/langchain-ai/chat-langchain/blob/b8acf5c32019590caaa98d3a0b30b3791ac1d58b/instructions.md)

**Model and assembly evidence:**

- [agent.py](https://github.com/langchain-ai/chat-langchain/blob/b8acf5c32019590caaa98d3a0b30b3791ac1d58b/agent.py)
- [src/agent/config.py](https://github.com/langchain-ai/chat-langchain/blob/b8acf5c32019590caaa98d3a0b30b3791ac1d58b/src/agent/config.py)

**Extraction:**

- Original instructions.md copied verbatim after a model header and blank line.
- Original instructional code examples remain because they are prompt content, not host application wrappers.
- Terminal newline normalized to one newline.

## [chatwoot_captain_assistant.md](chatwoot_captain_assistant.md)

**Task:** Customer support and specialist handoff.

**Model:** gpt-5.2 (Captain V2 default; account-level assistant model override can replace it)

**Prompt sources:**

- [enterprise/lib/captain/prompts/assistant.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/assistant.liquid)
- [enterprise/lib/captain/prompts/snippets/citations.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/citations.liquid)
- [enterprise/lib/captain/prompts/snippets/current_time.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/current_time.liquid)
- [enterprise/lib/captain/prompts/snippets/core_rules.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/core_rules.liquid)
- [enterprise/lib/captain/prompts/snippets/conversation.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/conversation.liquid)
- [enterprise/lib/captain/prompts/snippets/contact.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/contact.liquid)
- [enterprise/lib/captain/prompts/snippets/customer_identity.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/customer_identity.liquid)
- [enterprise/lib/captain/prompts/snippets/campaign.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/campaign.liquid)

**Model and assembly evidence:**

- [lib/llm/feature_router.rb](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/lib/llm/feature_router.rb)
- [enterprise/app/models/concerns/agentable.rb](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/app/models/concerns/agentable.rb)

**Extraction:**

- All seven static render includes expanded verbatim at their original positions.
- Original Liquid conditionals, loops, and tenant/runtime placeholders preserved.
- No private tenant data or scenario-specific user instructions invented.
- Terminal newline normalized to one newline.

## [chatwoot_captain_scenario.md](chatwoot_captain_scenario.md)

**Task:** Specialist support after a handoff.

**Model:** gpt-5.2 (Captain V2 default; account-level assistant model override can replace it)

**Prompt sources:**

- [enterprise/lib/captain/prompts/scenario.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/scenario.liquid)
- [enterprise/lib/captain/prompts/snippets/citations.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/citations.liquid)
- [enterprise/lib/captain/prompts/snippets/current_time.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/current_time.liquid)
- [enterprise/lib/captain/prompts/snippets/core_rules.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/core_rules.liquid)
- [enterprise/lib/captain/prompts/snippets/conversation.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/conversation.liquid)
- [enterprise/lib/captain/prompts/snippets/contact.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/contact.liquid)
- [enterprise/lib/captain/prompts/snippets/customer_identity.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/customer_identity.liquid)
- [enterprise/lib/captain/prompts/snippets/campaign.liquid](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/lib/captain/prompts/snippets/campaign.liquid)

**Model and assembly evidence:**

- [lib/llm/feature_router.rb](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/lib/llm/feature_router.rb)
- [enterprise/app/models/concerns/agentable.rb](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/app/models/concerns/agentable.rb)
- [enterprise/app/models/captain/scenario.rb](https://github.com/chatwoot/chatwoot/blob/dac03318c737bf76846298534ca3368e8afd9b97/enterprise/app/models/captain/scenario.rb)

**Extraction:**

- All seven static render includes expanded verbatim at their original positions.
- Original Liquid conditionals, loops, and tenant/runtime placeholders preserved.
- No private tenant data or scenario-specific user instructions invented.
- Terminal newline normalized to one newline.

## [pr_agent_reviewer.md](pr_agent_reviewer.md)

**Task:** Pull request review and structured findings.

**Model:** gpt-6.1-sol (default); fallback: gpt-6-luna; configurable.

**Prompt sources:**

- [pr_agent/settings/pr_reviewer_prompts.toml](https://github.com/The-PR-Agent/pr-agent/blob/2c6edf1033011bdffd7160660c9013496d089839/pr_agent/settings/pr_reviewer_prompts.toml)
- [pr_agent/settings/prompt_fragments.toml](https://github.com/The-PR-Agent/pr-agent/blob/2c6edf1033011bdffd7160660c9013496d089839/pr_agent/settings/prompt_fragments.toml)

**Model and assembly evidence:**

- [pr_agent/settings/configuration.toml](https://github.com/The-PR-Agent/pr-agent/blob/2c6edf1033011bdffd7160660c9013496d089839/pr_agent/settings/configuration.toml)
- [pr_agent/tools/pr_reviewer.py](https://github.com/The-PR-Agent/pr-agent/blob/2c6edf1033011bdffd7160660c9013496d089839/pr_agent/tools/pr_reviewer.py)
- [pr_agent/algo/prompt_fragments.py](https://github.com/The-PR-Agent/pr-agent/blob/2c6edf1033011bdffd7160660c9013496d089839/pr_agent/algo/prompt_fragments.py)

**Extraction:**

- Parsed TOML multiline system/user strings; removed TOML assignments and added only role headings.
- Inlined the upstream diff_hunk_format string verbatim at its single interpolation point so the diff-format instructions are complete.
- Retained native Jinja variables and conditionals, including the fragment's include_line_numbers/include_ai_metadata conditions. The reviewer supplies include_line_numbers=True and include_ai_metadata=is_ai_metadata.
- The embedded Pydantic-like output definitions are actual prompt text and were preserved.

## [anthropic_security_reviewer.md](anthropic_security_reviewer.md)

**Task:** Security audit of a pull request.

**Model:** claude-opus-4-1-20250805 (default; configurable via claude-model / CLAUDE_MODEL).

**Prompt sources:**

- [claudecode/prompts.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/prompts.py)

**Model and assembly evidence:**

- [claudecode/constants.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/constants.py)
- [action.yml](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/action.yml)
- [claudecode/github_action_audit.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/github_action_audit.py)

**Extraction:**

- Extracted the f-string body via Python AST; removed function/assignment wrappers and decoded f-string escaped literal braces as the model receives them.
- Inlined the nonempty diff section and optional custom instruction interpolation using their exact upstream strings.
- Native expressions and dynamic payload placeholders retained. This is the normal diff-included path; the oversized-diff fallback message is not mixed into this prompt.
- One application task prompt passed to Claude Code; the general Claude Code base prompt is outside this extraction.

## [anthropic_security_finding_verifier.md](anthropic_security_finding_verifier.md)

**Task:** Filter individual findings and false positives.

**Model:** claude-opus-4-1-20250805 (default when Claude filtering runs; configurable via claude-model / CLAUDE_MODEL).

**Prompt sources:**

- [claudecode/claude_api_client.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/claude_api_client.py)

**Model and assembly evidence:**

- [claudecode/constants.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/constants.py)
- [claudecode/findings_filter.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/findings_filter.py)
- [action.yml](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/action.yml)
- [claudecode/github_action_audit.py](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/claudecode/github_action_audit.py)

**Extraction:**

- Extracted both API message bodies; inlined the complete default HARD EXCLUSIONS, SIGNAL QUALITY CRITERIA, and PRECEDENTS policy.
- Included the upstream nonempty PR-context block and successful file-read block; retained native dynamic placeholders.
- The missing-context/failed-read branches are runtime data variants and are not mixed into this coherent prompt. Custom filtering instructions replace the default policy in upstream code.
- This preserves upstream wording, including its broad security exclusions and typos; it does not endorse those policies.
- The source separately uses a hardcoded Haiku API-access preflight. That is not this verifier's model; failed preflight disables the filtering stage.

## [anthropic_security_review_command.md](anthropic_security_review_command.md)

**Task:** Interactive branch security review.

**Model:** Inherits the active Claude Code session model; no model is specified in this command.

**Prompt sources:**

- [.claude/commands/security-review.md](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/.claude/commands/security-review.md)

**Model and assembly evidence:**

- [.claude/commands/security-review.md](https://github.com/anthropics/claude-code-security-review/blob/0c6a49f1fa56a1d472575da86a94dbc1edb78eda/.claude/commands/security-review.md)

**Extraction:**

- Removed YAML frontmatter (allowed-tools and description) and preserved the prompt body exactly apart from outer whitespace.
- Kept the source's native shell-context substitutions inside code blocks; no commands were executed.
- This is distinct from the GitHub Action prompt: it produces Markdown and directs parallel vulnerability-verifier subtasks.
- The command has no model field. The Action's Opus default does not establish the active Claude Code session's model.

## [holmes_incident_investigation.md](holmes_incident_investigation.md)

**Task:** Investigate infrastructure incidents.

**Model:** Configurable; the unconfigured OpenAI path uses gpt-5.4. Robusta-hosted deployments use the selected account model.

**Prompt sources:**

- [holmes/plugins/prompts/generic_ask.jinja2](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts/generic_ask.jinja2)
- [holmes/plugins/prompts/_toolsets_instructions.jinja2](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts/_toolsets_instructions.jinja2)
- [holmes/plugins/prompts/_fetch_logs.jinja2](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts/_fetch_logs.jinja2)
- [holmes/plugins/prompts/_default_log_prompt.jinja2](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts/_default_log_prompt.jinja2)

**Model and assembly evidence:**

- [holmes/core/llm.py](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/core/llm.py)

**Extraction:**

- Static Jinja includes recursively inlined; all conditions and runtime interpolation retained.
- Model annotation and per-file modification notice added.
- Outer blank lines normalized.

## [elastic_attack_discovery.md](elastic_attack_discovery.md)

**Task:** Identify correlated attack chains.

**Model:** Configurable via the Elastic LLM connector; generation and refinement use the selected model.

**Prompt sources:**

- [x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts)

**Model and assembly evidence:**

- [x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts)
- [x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts)

**Extraction:**

- Full upstream prompt body extracted; no instruction rewriting.
- Host language string wrapper removed where present; string escapes decoded.
- Model annotation and applicable per-file notices added.
- Outer blank lines normalized.

## [elastic_attack_discovery_refinement.md](elastic_attack_discovery_refinement.md)

**Task:** Refine existing attack discoveries.

**Model:** Same configured LLM connector/model as the Elastic Attack Discovery generation step.

**Prompt sources:**

- [x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts)

**Model and assembly evidence:**

- [x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts)
- [x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts)

**Extraction:**

- Full upstream prompt body extracted; no instruction rewriting.
- Host language string wrapper removed where present; string escapes decoded.
- Model annotation and applicable per-file notices added.
- Outer blank lines normalized.

## [elastic_attack_discovery_skill.md](elastic_attack_discovery_skill.md)

**Task:** Investigation workflow and reference instructions.

**Model:** Configurable via Elastic Agent Builder; the generation tool inherits the agent execution's LLM connector unless overridden.

**Prompt sources:**

- [x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/attack_discovery_generator/attack_discovery_generator_skill.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/attack_discovery_generator/attack_discovery_generator_skill.ts)
- [x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/lib/prompt/local_prompt_object/attack_discovery_prompts.ts)

**Model and assembly evidence:**

- [x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/packages/kbn-discoveries/impl/attack_discovery/graphs/invoke_graph_with_alerts.ts)
- [x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts](https://github.com/elastic/kibana/blob/28f2aabaa8135a9e0ffae0a87f6850b5e072c2b8/x-pack/solutions/security/plugins/discoveries/server/agent_builder/skills/tools/run_attack_discovery_tool/index.ts)

**Extraction:**

- TypeScript string literals decoded; static constant interpolations resolved.
- SKILL_CONTENT assembled in exact upstream order.
- Three registered referencedContent bodies appended in upstream registration order.
- Model annotation, original copyright, modification notice added.
- Outer blank lines normalized.

## [midday_assistant.md](midday_assistant.md)

**Task:** Business finances, invoices, and connected tools.

**Model:** gpt-4.1-mini (explicit repository runtime model)

**Prompt sources:**

- [apps/api/src/chat/prompt.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/apps/api/src/chat/prompt.ts)

**Model and assembly evidence:**

- [apps/api/src/chat/assistant-runtime.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/apps/api/src/chat/assistant-runtime.ts)

**Extraction:**

- Host TypeScript imports, interfaces, function definitions, and return wrappers removed.
- Static MIDDAY_DOMAINS constant inlined in both original positions.
- JavaScript escapes decoded; interpolation values retained as readable double-brace placeholders.
- Optional country/date-format text and upload/mentioned-app sections retained as template conditions/loops.
- All original static main-template text fragments checked for exact presence.
- mentionedAppNames maps to app names joined by comma-space; firstMentionedAppNameLowercase maps to the lowercased first mentioned app name.
- timeLabel remains a runtime placeholder: 12-hour (AM/PM) when timeFormat is 12; otherwise 24-hour.

## [inbox_zero_assistant.md](inbox_zero_assistant.md)

**Task:** Inbox actions and automation management.

**Model:** Deployment-configured CHAT_LLMS (falls back to DEFAULT_LLMS); a user-supplied API key/provider/model can override the deployment selection. No single hosted model ID is disclosed by this prompt.

**Prompt sources:**

- [apps/web/utils/ai/assistant/chat.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat.ts)
- [apps/web/utils/ai/assistant/chat-provider-shared.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat-provider-shared.ts)
- [apps/web/utils/ai/assistant/chat-provider-google.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat-provider-google.ts)
- [apps/web/utils/ai/assistant/chat-provider-microsoft.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat-provider-microsoft.ts)

**Model and assembly evidence:**

- [apps/web/utils/ai/assistant/chat.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat.ts)
- [apps/web/utils/llms/use-cases.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/use-cases.ts)
- [apps/web/utils/llms/model.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/model.ts)
- [apps/web/utils/ai/assistant/chat-provider-shared.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/assistant/chat-provider-shared.ts)

**Extraction:**

- The complete task-specific buildResolvedSystemPrompt output is represented as a readable template. All static email-capability, provider-context, search, inbox-triage, rule-suggestion, and formatting helper fragments are inlined.
- Both Google and Microsoft provider policies are retained. As in upstream, an unrecognized provider uses the Google policy while the current provider name stays dynamic.
- Readable {% if %}/{% else %}/{% endif %} markers replace host-language branches. Original runtime data are represented by ${provider}, ${userTimezone}, ${currentTimestamp}, and ${calendarConnection.message}. These markers are inventory notation, not an upstream template engine.
- Boundary: includes the named task system-prompt builder and all its static instruction dependencies. Excludes shared LLM promptHardening, tool schemas, runtime message/history/context injection, and generic execution machinery.

## [posthog_trends_query.md](posthog_trends_query.md)

**Task:** Convert an analytics plan into a trends query.

**Model:** gpt-5.2 (reasoning effort: none; JSON-schema structured output)

**Prompt sources:**

- [ee/hogai/chat_agent/trends/prompts.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/hogai/chat_agent/trends/prompts.py)
- [ee/hogai/chat_agent/schema_generator/prompts.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/hogai/chat_agent/schema_generator/prompts.py)

**Model and assembly evidence:**

- [ee/hogai/chat_agent/trends/nodes.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/hogai/chat_agent/trends/nodes.py)
- [ee/hogai/chat_agent/schema_generator/nodes.py](https://github.com/PostHog/posthog/blob/919579a7bd7a3058cf89f2284f1897f1a32897c8/ee/hogai/chat_agent/schema_generator/nodes.py)

**Extraction:**

- Extracted system prompt and the shared group-mapping, plan, and optional validation-retry user messages; preserved Mustache placeholders and JSON examples. Role headings separate messages. Python wrappers removed. Response schema and runtime machinery excluded.

## [midday_weekly_summary.md](midday_weekly_summary.md)

**Task:** Write a weekly financial summary.

**Model:** gpt-4.1-mini (ContentGenerator default; optional model override; weekly worker uses the default)

**Prompt sources:**

- [packages/insights/src/content/prompts/summary.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/packages/insights/src/content/prompts/summary.ts)
- [packages/insights/src/content/prompts/shared-data.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/packages/insights/src/content/prompts/shared-data.ts)
- [packages/insights/src/content/prompts/slots.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/packages/insights/src/content/prompts/slots.ts)

**Model and assembly evidence:**

- [packages/insights/src/content/generator.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/packages/insights/src/content/generator.ts)
- [packages/insights/src/index.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/packages/insights/src/index.ts)
- [apps/worker/src/processors/insights/generate-team-insights.ts](https://github.com/midday-ai/midday/blob/51587319f26a0ffaa9dfccab1920373cb65689b7/apps/worker/src/processors/insights/generate-team-insights.ts)

**Extraction:**

- Host TypeScript scaffolding removed; original final prompt order retained.
- All static role/rule text, banned-word constants, four tone variants, runtime data framing, and example variants expanded.
- First-insight versus recurring-insight branches retained as explicit template conditionals, not merged into simultaneous instructions.
- All 7 recurring example pairs, 5 first-insight pairs, and 2 concrete examples retained verbatim under their source selection conditions.
- Dynamic computed financial values remain placeholders; no customer financial data or invented rendered example used.
- Static text from all 41 lines.push emissions in data builder verified against source.
- This is a readable prompt template; not an executable drop-in Liquid implementation of the TypeScript generator.

## [holmes_conversation_compaction.md](holmes_conversation_compaction.md)

**Task:** Summarize an investigation conversation.

**Model:** Same model selected for the HolmesGPT investigation (configurable; unconfigured OpenAI path: gpt-5.4).

**Prompt sources:**

- [holmes/plugins/prompts/conversation_history_compaction.jinja2](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/plugins/prompts/conversation_history_compaction.jinja2)

**Model and assembly evidence:**

- [holmes/core/llm.py](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/core/llm.py)
- [holmes/core/tool_calling_llm.py](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/core/tool_calling_llm.py)
- [holmes/core/truncation/compaction.py](https://github.com/HolmesGPT/holmesgpt/blob/b92fdd9dd8fcd41e8cf79ac367802f018bfe9cb2/holmes/core/truncation/compaction.py)

**Extraction:**

- Full upstream prompt body extracted; no instruction rewriting.
- Host language string wrapper removed where present; string escapes decoded.
- Model annotation and applicable per-file notices added.
- Outer blank lines normalized.

## [inbox_zero_rule_selector.md](inbox_zero_rule_selector.md)

**Task:** Select the best automation rule for an email.

**Model:** Deployment-configured DEFAULT_LLMS by default; the caller can override the model category, and a user-supplied API key/provider/model can override the deployment selection. No single hosted model ID is disclosed by this prompt.

**Prompt sources:**

- [apps/web/utils/ai/choose-rule/ai-choose-rule.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/choose-rule/ai-choose-rule.ts)
- [apps/web/utils/ai/helpers.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/helpers.ts)

**Model and assembly evidence:**

- [apps/web/utils/ai/choose-rule/ai-choose-rule.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/choose-rule/ai-choose-rule.ts)
- [apps/web/utils/llms/model.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/model.ts)
- [apps/web/utils/ai/helpers.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/helpers.ts)

**Extraction:**

- Extracted complete single-rule system and user prompt strings. Inlined METADATA_GUIDELINE, user-rules XML, user-info XML, the List-Unsubscribe note, and per-sender classification-feedback instructions.
- Readable {% if %} and {% for %} markers represent original branches and loops. The ${emailContent} placeholder represents runtime stringifyEmail(email, 500) data; rule names/criteria, user fields, and classification-feedback fields remain dynamic.
- Boundary: includes task-specific instruction strings and static helper instructions. Excludes shared LLM promptHardening, structured-output schema declarations, and execution machinery.

## [inbox_zero_multi_rule_selector.md](inbox_zero_multi_rule_selector.md)

**Task:** Select matching rules and a primary rule.

**Model:** Deployment-configured DEFAULT_LLMS by default; the caller can override the model category, and a user-supplied API key/provider/model can override the deployment selection. No single hosted model ID is disclosed by this prompt.

**Prompt sources:**

- [apps/web/utils/ai/choose-rule/ai-choose-rule.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/choose-rule/ai-choose-rule.ts)
- [apps/web/utils/ai/helpers.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/helpers.ts)
- [apps/web/utils/llms/ollama-guidance.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/ollama-guidance.ts)

**Model and assembly evidence:**

- [apps/web/utils/ai/choose-rule/ai-choose-rule.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/choose-rule/ai-choose-rule.ts)
- [apps/web/utils/llms/model.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/model.ts)
- [apps/web/utils/ai/helpers.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/ai/helpers.ts)
- [apps/web/utils/llms/ollama-guidance.ts](https://github.com/elie222/inbox-zero/blob/e569dac97a491fbd9e5f4f576e0e264e003b498f/apps/web/utils/llms/ollama-guidance.ts)

**Extraction:**

- Extracted complete multi-rule system and user prompt strings. Inlined METADATA_GUIDELINE, available-rules XML, user-info XML, the List-Unsubscribe note, and per-sender classification-feedback instructions.
- Includes all four OLLAMA_MULTI_RULE_SELECTION_GUIDANCE lines under their original provider condition. Generic OLLAMA_STRUCTURED_OUTPUT_GUIDANCE is not directly appended by this task builder and is outside this extraction boundary.
- Readable {% if %} and {% for %} markers represent original branches and loops. The ${emailContent} placeholder represents runtime stringifyEmail(email, 500) data; rule names/instructions, user fields, and classification-feedback fields remain dynamic.
- Boundary: includes task-specific instruction strings and static helper instructions. Excludes shared LLM promptHardening, structured-output schema declarations, and result normalization/execution machinery.
