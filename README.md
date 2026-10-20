# Production agent prompts

19 task-specific prompt examples from 9 real product codebases, collected for private development and study.

Each prompt file begins with `Model:`, followed by the extracted prompt text. Where a workflow has separate system and user messages, simple role headings preserve those boundaries.

## Inventory

| Prompt file | Task | Model pairing |
| --- | --- | --- |
| [posthog_assistant.md](posthog_assistant.md) | Product support, search, and escalation | `claude-3-5-sonnet-20241022` — historical |
| [chat_langchain_assistant.md](chat_langchain_assistant.md) | Documentation support and troubleshooting | `gemini-3.5-flash-lite`; GPT-5.4 nano / Haiku 4.5 fallbacks |
| [chatwoot_captain_assistant.md](chatwoot_captain_assistant.md) | Customer support and specialist handoff | `gpt-5.2` — Captain V2 default |
| [chatwoot_captain_scenario.md](chatwoot_captain_scenario.md) | Specialist support after a handoff | `gpt-5.2` — same account routing |
| [pr_agent_reviewer.md](pr_agent_reviewer.md) | Pull request review and structured findings | `gpt-6.1-sol`; `gpt-6-luna` fallback |
| [anthropic_security_reviewer.md](anthropic_security_reviewer.md) | Security audit of a pull request | `claude-opus-4-1-20250805` — historical default |
| [anthropic_security_finding_verifier.md](anthropic_security_finding_verifier.md) | Filter individual findings and false positives | `claude-opus-4-1-20250805` — historical default |
| [anthropic_security_review_command.md](anthropic_security_review_command.md) | Interactive branch security review | Inherits the Claude Code session model |
| [holmes_incident_investigation.md](holmes_incident_investigation.md) | Investigate infrastructure incidents | Configurable; unconfigured OpenAI path: `gpt-5.4` |
| [elastic_attack_discovery.md](elastic_attack_discovery.md) | Identify correlated attack chains | Configured Elastic connector/model |
| [elastic_attack_discovery_refinement.md](elastic_attack_discovery_refinement.md) | Refine existing attack discoveries | Same configured model as generation |
| [elastic_attack_discovery_skill.md](elastic_attack_discovery_skill.md) | Investigation workflow and reference instructions | Agent Builder execution model/connector |
| [midday_assistant.md](midday_assistant.md) | Business finances, invoices, and connected tools | `gpt-4.1-mini` |
| [inbox_zero_assistant.md](inbox_zero_assistant.md) | Inbox actions and automation management | Configured `CHAT_LLMS` or user model |
| [posthog_trends_query.md](posthog_trends_query.md) | Convert an analytics plan into a trends query | `gpt-5.2`; reasoning effort `none` |
| [midday_weekly_summary.md](midday_weekly_summary.md) | Write a weekly financial summary | `gpt-4.1-mini` — overridable default |
| [holmes_conversation_compaction.md](holmes_conversation_compaction.md) | Summarize an investigation conversation | Same model as the investigation |
| [inbox_zero_rule_selector.md](inbox_zero_rule_selector.md) | Select the best automation rule for an email | Configured default category; caller can override |
| [inbox_zero_multi_rule_selector.md](inbox_zero_multi_rule_selector.md) | Select matching rules and a primary rule | Configured default category; caller can override |

## Reading the files

The original instruction wording, examples, tool names, output definitions, and template variables are preserved. Static prompt fragments are inlined where needed so the instructions can be read in one place. Host-language imports, SDK calls, tool implementations, and application control flow are excluded.

Some sources build prompts dynamically. Their optional instruction branches are retained as readable template conditions, and runtime customer data remains placeholders. These are reference documents, not guaranteed drop-in templates for a particular rendering engine. The `Model:` line, role headings, and any license comments are collection annotations; exclude those annotations when using a prompt body.

[SOURCES.md](SOURCES.md) records the exact upstream commits, prompt files, model-selection evidence, and extraction boundaries. Source snapshots were collected on **2026-10-20**.

## Model notes

- Model labels describe the inspected public implementation: an explicit callsite, a configurable default, or an inherited model. They do not establish every hosted deployment's live model or which model the prompt was originally optimized against.
- PostHog's support sidebar hardcodes `claude-3-5-sonnet-20241022`, retired on 2025-10-28. Anthropic's security-review Action defaults to `claude-opus-4-1-20250805`, retired on 2026-08-05. These remain historical source examples. See [Anthropic's model lifecycle documentation](https://platform.claude.com/docs/en/about-claude/model-deprecations).
- Chatwoot Captain V2's runtime router selects `gpt-5.2`; a valid account override can replace it. HolmesGPT's current unconfigured OpenAI path selects `gpt-5.4`, although older configuration constants and setup documentation can differ.
- PR-Agent's label refers to the community repository represented here. Inbox Zero and Elastic select models through deployment, account, or execution configuration.

## Scope and upstream terms

This is a **private personal development/testing reference collection**. Each extraction retains its upstream terms; the collection does not relicense those works. Full licenses and notices are in [LICENSES](LICENSES/).

- **PostHog and Chatwoot enterprise prompts:** included under their explicit development/testing copying permission. Those licenses restrict redistribution and production use; keep these copies private unless separate rights are obtained.
- **Chat LangChain, PR-Agent, and Anthropic security review:** MIT; copyright and permission notices are preserved.
- **HolmesGPT:** Apache-2.0; license, attribution, and modification notices are preserved.
- **Elastic x-pack prompts:** Elastic License 2.0; its use and redistribution conditions continue to apply.
- **Midday:** AGPL-3.0. Copyright (c) 2023-present Midday Labs AB. Extracted and template-normalized on 2026-10-20; upstream terms retained.
- **Inbox Zero:** its upstream license is AGPL-3.0 with additional terms, including stated personal, educational, and research exemptions. Copyright (C) 2025 Inbox Zero Inc. Extracted and template-normalized on 2026-10-20; the complete upstream terms are preserved.
