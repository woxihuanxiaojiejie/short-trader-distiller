# 预期规则

## explicit

```yaml
rule_id: "QFYD-001"
rule_name: "竞价涨幅过滤"
category: "stock_selection"
rule_type: "explicit"
rule_text: "短线标的竞价涨幅要大于2%。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "竞价涨幅大于2%"
action: "保留为候选条件之一"
veto_conditions: []
invalidation_conditions:
  - "竞价涨幅不大于2%"
priority: "medium"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第3行"
source_summary: "材料明确提出竞价涨幅要大于2%。"
confidence: "high"
unresolved_fields:
  - "未说明单独满足该条件是否足以买入"
```

```yaml
rule_id: "QFYD-002"
rule_name: "竞价成交额过滤"
category: "stock_selection"
rule_type: "explicit"
rule_text: "短线标的竞价成交额要大于1500万元。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "竞价成交额大于1500万元"
action: "保留为候选条件之一"
veto_conditions: []
invalidation_conditions:
  - "竞价成交额不大于1500万元"
priority: "medium"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第3行"
source_summary: "材料明确提出竞价成交额要大于1500万元。"
confidence: "high"
unresolved_fields:
  - "未说明单独满足该条件是否足以买入"
```

```yaml
rule_id: "QFYD-003"
rule_name: "流通市值过滤"
category: "stock_selection"
rule_type: "explicit"
rule_text: "流通市值一般看30亿至1000亿元之间。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "流通市值在30亿至1000亿元之间"
action: "保留为候选条件之一"
veto_conditions: []
invalidation_conditions:
  - "流通市值低于30亿或高于1000亿元"
priority: "medium"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第3行"
source_summary: "材料明确提出流通市值范围。"
confidence: "medium"
unresolved_fields:
  - "原文使用“一般”，例外条件未说明"
```

```yaml
rule_id: "QFYD-004"
rule_name: "量比过滤"
category: "stock_selection"
rule_type: "explicit"
rule_text: "量比要大于5。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "量比大于5"
action: "保留为候选条件之一"
veto_conditions: []
invalidation_conditions:
  - "量比不大于5"
priority: "medium"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第3行"
source_summary: "材料明确提出量比要大于5。"
confidence: "high"
unresolved_fields:
  - "未说明量比计算口径"
```

```yaml
rule_id: "QFYD-005"
rule_name: "剔除ST"
category: "veto"
rule_type: "explicit"
rule_text: "ST股票直接剔除。"
applicable_environment: []
trigger_conditions:
  - "标的带有ST标签"
confirmation_conditions:
  - "股票为ST"
action: "剔除，不进入候选"
veto_conditions:
  - "ST"
invalidation_conditions: []
priority: "hard_veto"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第3行"
source_summary: "材料明确提出ST直接剔除。"
confidence: "high"
unresolved_fields: []
```

## unresolved

```yaml
rule_id: "QFYD-006"
rule_name: "热点板块结合条件"
category: "sector_selection"
rule_type: "unresolved"
rule_text: "筛选还需结合热点板块，但材料没有给出热点板块的具体量化定义。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "热点板块定义不足"
action: "请求补充材料或保持未解决"
veto_conditions: []
invalidation_conditions: []
priority: "unresolved"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第5行"
source_summary: "材料要求结合热点板块，但明确说明没有展开量化定义。"
confidence: "high"
unresolved_fields:
  - "热点板块确认标准"
  - "板块持续性标准"
```

```yaml
rule_id: "QFYD-007"
rule_name: "技术形态结合条件"
category: "stock_selection"
rule_type: "unresolved"
rule_text: "筛选还需结合技术形态，但材料没有给出技术形态的具体量化定义。"
applicable_environment: []
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "技术形态定义不足"
action: "请求补充材料或保持未解决"
veto_conditions: []
invalidation_conditions: []
priority: "unresolved"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第5行"
source_summary: "材料要求结合技术形态，但明确说明没有展开量化定义。"
confidence: "high"
unresolved_fields:
  - "技术形态确认标准"
```

```yaml
rule_id: "QFYD-008"
rule_name: "大盘环境结合条件"
category: "market_environment"
rule_type: "unresolved"
rule_text: "筛选还需结合大盘环境，大盘环境不好时要谨慎，但材料没有给出具体定义。"
applicable_environment:
  - "大盘环境定义不足"
trigger_conditions:
  - "进入短线标的筛选"
confirmation_conditions:
  - "大盘环境定义不足"
action: "请求补充材料或保持未解决"
veto_conditions: []
invalidation_conditions: []
priority: "unresolved"
source_file: "examples/qianfan-yidu-mini/source.txt"
source_location: "第5行"
source_summary: "材料要求结合大盘环境，但没有展开量化定义。"
confidence: "high"
unresolved_fields:
  - "大盘环境好坏的判断标准"
```

## inferred

本次最小材料不足以形成 `inferred` 规则。

## conflict

本次最小材料未发现 `conflict` 规则。
