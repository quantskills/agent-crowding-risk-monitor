---
name: agent-crowding-risk-monitor
description: "Monitor crowded-trade risk from Pandadata price, turnover, margin, and LHB heat evidence. Use when a research or trading AI agent needs Pandadata-backed monitoring, evidence-backed interpretation, user-readable reports, watchlists, and review materials without automated order placement."
metadata:
  organization: QuantSkills
  organization_url: https://github.com/quantskills
  repository: quantskills/agent-crowding-risk-monitor
  repository_url: https://github.com/quantskills/agent-crowding-risk-monitor
  project_type: agent
  collection: pandadata-research-monitor-agents-8
  license: GPL-3.0
  category: risk-agent
  tags: [crowding, margin, risk-monitoring, pandadata]
  platforms: [claude-code, codex, openclaw, cursor]
  language: zh-en
  status: active
  validation_level: verified
  maintainer_type: official
  requires: [skill-pandadata-api]
  pandadata_methods: [get_margin, get_lhb_list]
  summary_zh: 用价格、成交、融资、龙虎榜热度识别抱团、过热、踩踏和去杠杆风险。
  summary_en: Monitor crowded-trade risk from Pandadata price, turnover, margin, and LHB heat evidence.
quantSkills:
  organization: QuantSkills
  organization_url: https://github.com/quantskills
  repository: quantskills/agent-crowding-risk-monitor
  repository_url: https://github.com/quantskills/agent-crowding-risk-monitor
  project_type: agent
  collection: pandadata-research-monitor-agents-8
  license: GPL-3.0
  category: risk-agent
  tags: [crowding, margin, risk-monitoring, pandadata]
  platforms: [claude-code, codex, openclaw, cursor]
  language: zh-en
  status: active
  validation_level: verified
  maintainer_type: official
  requires: [skill-pandadata-api]
  pandadata_methods: [get_margin, get_lhb_list]
  summary_zh: 用价格、成交、融资、龙虎榜热度识别抱团、过热、踩踏和去杠杆风险。
  summary_en: Monitor crowded-trade risk from Pandadata price, turnover, margin, and LHB heat evidence.
---

# Crowding Risk Monitor

Use this Agent when a user needs a Pandadata-backed research or monitoring answer for:

> Is a hot trade becoming crowded enough to raise risk attention?

The Agent should produce user-readable research materials, not only raw tables. Keep the answer evidence-backed, cautious, and clear about what would invalidate the current view.

## User-Facing Workflow

1. State the current answer in plain language.
2. Show the key evidence and explain why it matters.
3. Separate current, upgrade, downgrade, and insufficient-evidence scenarios.
4. Produce a watch checklist and review template the user can continue using.
5. Keep order execution outside the Agent boundary.

## Primary Watch Focus

龙虎榜热度、融资余额、成交金额和承接质量。

## Materials To Produce

| Material | Use |
| --- | --- |
| `outputs/live/report.html` | Start with the conclusion, evidence charts, scenarios, and invalidation conditions. |
| `outputs/live/decision_matrix.csv` | Turns base, upgrade, downgrade, and insufficient-evidence cases into next actions. |
| `outputs/live/monitoring_checklist.csv` | Prioritized watch items for the next review window. |
| `outputs/live/research_journal_template.md` | Template for evidence, counter-evidence, and rerun conditions. |
| `outputs/live/handoff_card.md` | Short handoff for another researcher or AI agent. |
| `outputs/live/data_dictionary.csv` | Tables, fields, and row counts used in the run. |

## Reference Documents

- `references/methodology.md`: Agent logic, metric interpretation, and intended use.
- `references/data-and-outputs.md`: Public output files under `outputs/live/` and how to use them.
- `references/agent-boundary.md`: What the Agent can do, what it cannot do, and trading boundaries.

## Python Utility Script

- `scripts/agent_package.py validate`: validate the public Agent package, references, outputs, and chart files.
- `scripts/agent_package.py summarize`: read `outputs/live/` and emit a JSON summary for another AI agent.
- `scripts/agent_package.py summarize --brief outputs/live/generated_brief.md`: write a Markdown brief for research notes.

## Pandadata Methods

- `get_margin`
- `get_lhb_list`

## Boundary

- Use Pandadata or user-provided data only.
- Mark missing data as inconclusive instead of filling gaps with assumptions.
- Do not produce unconditional buy/sell commands.
- Do not connect to broker order execution.
