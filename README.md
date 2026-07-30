# 短线交易员蒸馏元Skill V0.1

这是从原“女娲.skill”副本改造出的短线交易员蒸馏元Skill，用于把用户提供的文章、帖子、访谈、复盘、截图转写、笔记和交易案例，整理成独立、可运行、可追溯的交易员Skill。

## 使用边界

- 默认只分析用户提供的本地材料。
- 除非用户明确允许，否则不联网补充。
- 不开发应用、网页、Agent系统、交易系统或自动下单系统。
- 不虚构交易规则、阈值、案例、历史收益或交易员观点。
- 不直接模仿、扮演交易员本人。
- 不直接代替用户作出真实交易决策。

## 触发示例

```text
蒸馏短线交易员
蒸馏某某交易体系
把这些文章做成Skill
提炼某某的交易方法
更新某某交易员Skill
分析这些交易文章
提取选股规则
提取买卖规则
```

## 输出目录

生成的交易员Skill默认放在：

```text
~/.codex/skills/trader-<slug>/
```

目录结构：

```text
trader-<slug>/
├── SKILL.md
├── references/
│   ├── source-index.md
│   ├── trading-system.md
│   ├── rulebook.md
│   ├── conflicts.md
│   ├── unresolved.md
│   └── test-cases.md
└── FIDELITY.md
```

## 主要文件

- `SKILL.md`：元Skill主流程。
- `references/extraction-framework.md`：交易体系提炼框架。
- `references/rule-schema.md`：规则证据字段规范。
- `references/skill-template.md`：生成交易员Skill的模板。
- `references/fidelity-scorecard.md`：保真度评分卡。
- `examples/qianfan-yidu-mini/`：最小示例。

## 来源说明

本目录保留原项目许可证。当前版本只保留与短线交易员Skill蒸馏相关的必要说明，删除了与本Skill无关的人物角色扮演示例、宣传素材、无关脚本和人物研究案例。
