# 财务报表自动化录入与勾稽校验工作流

本仓库提供一个面向审计报告财务报表录入场景的 Codex Skill 和 Excel 模板，用于将审计报告中的资产负债表、利润表、现金流量表及补充资料录入至既有 Excel 工作簿。

项目重点关注财务口径一致性与录入质量控制，支持合并口径与本部/母公司口径分开处理，按审计报告年份分别取数，保留 Excel 原有格式和公式，并通过关键勾稽关系校验录入结果。

## 能力概览

- 支持从审计报告中提取并录入三大报表：资产负债表、利润表和现金流量表。
- 支持合并口径与本部/母公司口径分离，降低口径串表风险。
- 支持按年份逐份审计报告取数，避免用期初数回填上一年导致跨年错填。
- 支持补充资料录入，包括计提折旧额、无形资产摊销额和长期待摊费用摊销。
- 录入时保留 Excel 原有格式、公式、边框、列宽和工作表结构。
- 通过报表关键汇总项和勾稽关系复核录入结果，定位错行、错列、漏填和 OCR 识别误差。

## 仓库结构

```text
financial-statement-entry-skill/
├─ README.md
├─ LICENSE
├─ SECURITY.md
├─ skill/
│  └─ SKILL.md
├─ template/
│  └─ financial-statement-template.xlsx
└─ examples/
   └─ demo-usage.md
```

## 推荐工作流

1. 读取 Excel 模板结构，确认工作表、年份列、输入单元格和公式行。
2. 分别定位审计报告中的合并报表和母公司报表。
3. 按年份从对应审计报告中取数，不跨年借用期初数或比较数。
4. 建立“审计报告项目 -> Excel 行”的映射关系。
5. 只写入输入单元格，保留模板中的公式和格式。
6. 录入后核对资产负债表、利润表、现金流量表及补充资料的关键汇总值。
7. 对不一致项目逐级追溯到具体明细行，而不是直接修改总计行。

## 重点校验项

### 资产负债表

- 流动资产合计
- 非流动资产合计
- 资产总计
- 流动负债合计
- 非流动负债合计
- 负债合计
- 所有者权益合计
- 负债和所有者权益总计

### 利润表

- 营业利润
- 利润总额
- 净利润
- 综合收益总额

### 现金流量表

- 经营活动产生的现金流量净额
- 投资活动产生的现金流量净额
- 筹资活动产生的现金流量净额
- 现金及现金等价物净增加额
- 期末现金及现金等价物余额

## 快速开始

将 [skill/SKILL.md](skill/SKILL.md) 复制到本机 Codex skills 目录：

```text
~/.codex/skills/financial-statement-entry/SKILL.md
```

Windows 环境通常为：

```text
C:\Users\<your-user>\.codex\skills\financial-statement-entry\SKILL.md
```

随后即可在 Codex 中使用 `financial-statement-entry` 工作流处理类似任务。

## 使用示例

示例提示词见 [examples/demo-usage.md](examples/demo-usage.md)。

典型任务可以描述为：

```text
请使用 financial-statement-entry skill，将目录中的审计报告数据录入到财务报表 Excel 模板中。
要求合并口径和本部口径分开处理，只填写输入单元格，保留模板公式和格式，并在录入后核对三大报表关键勾稽关系。
```

## 数据与合规说明

本仓库仅提供工作流说明、技能文件和通用模板，不应包含真实客户资料、真实审计报告或未脱敏的业务文件。公开 fork、二次分发或演示时，建议仅使用脱敏模板或合成样例。

更多说明见 [SECURITY.md](SECURITY.md)。

## 许可证

This repository is released under the MIT License. See [LICENSE](LICENSE).
