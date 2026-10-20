Model: Same configured LLM connector/model as the Elastic Attack Discovery generation step.

<!--
Copyright Elasticsearch B.V. and/or licensed to Elasticsearch B.V. under one
or more contributor license agreements. Licensed under the Elastic License
2.0; you may not use this file except in compliance with the Elastic License
2.0.
Modified from upstream: prompt text extracted to Markdown and model metadata added. See LICENSES/elastic-NOTICE.md.
-->

Review the JSON output from your initial analysis. Your task is to refine the attack chains by:

1. Merge attack chains when strong evidence links them to the same campaign. Only connect events with clear relationships, such as matching timestamps, network patterns, IPs, or overlapping entities like hostnames and user accounts. Prioritize correlating alerts based on shared entities, such as the same host, user, or source IP across multiple alerts.
2. Keep distinct attacks separated when evidence doesn't support merging.
3. Strengthening justifications: For each attack chain:
   - Explain the specific evidence connecting events (particularly across hosts)
   - Reference relevant MITRE ATT&CK techniques that support your grouping
   - Ensure your narrative follows the chronological progression of the attack
4. Remove Attack Chains that are likely false positives. Most alerts are false positives, even if they look alarming or anomalous at first glance. Only alert on attacks if you are confident they are a real attack, or demonstrate an attack simulation or red team. For example, legitimate enterprise management tools (SCCM/CCM, Group Policy, etc.) often trigger security alerts during normal operations. Also, Security software (especially DLP), Digital Rights Management packers/protectors, and video game anti-cheats often leverage evasive techniques that may look like malware.
5. Remove low quality Attack Chains. Attack Chains must demonstrate an attacker progression. Attacks must consist of alerts from more than one rule. A single alert, or multiple alerts of the same rule or behavior, should never generate an attack chain. Include rule names in your reasoning to ensure you follow this requirement.

Output requirements:
- Think through the problem step by step. Show your reasoning before the JSON output section.
- Return your refined analysis using the exact same JSON format as your initial output, applying the same field syntax requirements.
- Conform exactly to the JSON schema defined earlier
