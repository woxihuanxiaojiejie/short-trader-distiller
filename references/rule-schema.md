# 交易规则证据Schema

每条交易规则至少包含以下字段。字段缺失时不得删除该规则，应在 `unresolved_fields` 中记录缺口。

```yaml
rule_id: "R-001"
rule_name: "规则名称"
category: "system_positioning | market_environment | sentiment_cycle | sector_selection | stock_selection | entry | position_management | exit | risk_control | veto | exception"
rule_type: "explicit | inferred | unresolved | conflict"
rule_text: "用中性中文描述规则，不冒充交易员原话"
applicable_environment:
  - "适用市场环境；未知则写未解决"
trigger_conditions:
  - "触发条件"
confirmation_conditions:
  - "确认条件"
action: "规则触发后的动作或分析结论"
veto_conditions:
  - "否决条件"
invalidation_conditions:
  - "信号失效条件"
priority: "hard_veto | high | medium | low | unresolved"
source_file: "材料文件路径"
source_location: "页码、章节、行号、段落或截图编号"
source_summary: "来源片段摘要，不大段复制原文"
confidence: "high | medium | low"
unresolved_fields:
  - "缺失字段或无法确认的条件"
```

## 字段定义

### category

`category` 表示交易规则所属业务类别，允许值至少包括：

- `system_positioning`：交易体系定位。
- `market_environment`：市场环境。
- `sentiment_cycle`：情绪周期。
- `sector_selection`：题材和板块选择。
- `stock_selection`：个股筛选。
- `entry`：买入系统。
- `position_management`：持仓和仓位管理。
- `exit`：卖出系统。
- `risk_control`：风险控制。
- `veto`：否决条件。
- `exception`：例外和优先级。

### rule_type

`rule_type` 表示证据类型，只允许：

- `explicit`：原文明确表达的规则或观点。原文明说过一次即可保留，置信度可低。
- `inferred`：根据多个材料或案例归纳出来，但交易员没有直接表述为规则。
- `unresolved`：材料提到相关问题，但定义、条件或阈值不足，暂时不能形成规则。
- `conflict`：不同材料、不同时间或不同案例之间存在冲突，当前不能直接合并。

每条规则必须同时存在 `category` 和 `rule_type`，不得把证据类型写入 `category`。

## inferred规则门槛

归纳规则至少满足一项：
- 至少两个不同材料片段支持。
- 至少两个不同交易案例支持。
- 一个明确观点加一个实际案例支持。

## 禁止项

- 不得因原文只出现一次而删除 `explicit` 规则。
- 不得把AI归纳写成交易员原话。
- 不得补充材料中不存在的阈值、收益率、仓位比例、止损幅度或胜率。
- 不得在缺少真实行情数据时假装已经完成当前市场判断。
