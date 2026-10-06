# 财务报表录入与勾稽校验

将审计报告或最新一期财务报表录入 Excel 台账，分别处理合并与母公司口径，保留来源记录、公式和格式，并以来源披露的汇总值复核结果。

仓库提供的是 **Codex Skill 和 Excel 模板**，不包含独立的一键识别程序。录入、OCR、表格计算及文件操作由使用此 Skill 的环境完成，实际支持情况取决于可用工具与来源质量。

## 当前模板

[financial-statement-template.xlsx](template/financial-statement-template.xlsx) 于 2026-10-06 按提供文件原样替换，包含 12 个工作表：

- 基本信息、资产负债表、利润表、现金流量表、补充资料表。
- 主要财务指标、资产结构、负债结构、盈利能力、现金流量、偿债能力、运营能力。

主报表 B:E 是**元**录入区，右侧是同口径的**万元**公式展示。分析表使用万元、亿元或比率，不能将左右区域分别填写为合并与母公司。期间表头由“基本信息”统一控制，初始占位年份须在录入前明确。

模板原文件保持不变，在输出副本中录入和适配。有关查找键、固定引用、默认 0、最新一期月份、每股收益展示等检查点见 [模板说明](skill/references/template-guide.md)。空模板显示 0 或没有错误提示不代表已验证财务数据。

## 模板没有来源科目时

1. 有依据的同义科目映射到现有行，保留原标签。
2. 分列/合列按同期间、同口径的来源明细汇总或拆分，记录组成，不重复累计。
3. 独立主科目没有合理映射时，在输出副本的相应分类中新增行，并同步小计、单位展示、分析表和指标引用。
4. 用户要求固定结构或分类依据不足时，列出未解决项目及影响，继续其他录入，不跳过非零项目、不填“其他”补差、不硬写总计。

完整规则和典型情形见 [缺失科目处理](skill/references/missing-items.md)。

## 安装与使用

将 **整个 `skill/` 目录的内容**复制到本机技能目录，不能只复制 `SKILL.md`：

```text
~/.codex/skills/financial-statement-entry/
├─ SKILL.md
└─ references/
   ├─ template-guide.md
   ├─ missing-items.md
   └─ reconciliation.md
```

Windows 目录通常为 `C:\Users\<your-user>\.codex\skills\financial-statement-entry\`。再将仓库的 `template/financial-statement-template.xlsx` 复制到任务目录，连同来源报告交给 Codex。用户另有指定模板时优先使用用户模板。

```text
请使用 financial-statement-entry，将当前目录的来源报表录入这份 Excel 模板。
分别生成合并与母公司输出副本，按实际表头期间和来源单位取数。
新科目按经济含义映射，独立缺失科目可作最小必要扩展，并更新受影响公式和分析表。
保留原文件，提供来源映射及勾稽结果，说明未披露资料和不可计算的指标。
```

更多任务提示词与验收情形见 [使用示例](examples/demo-usage.md)。

## 校验与交付

- 保留每个来源项目的主体、期间、口径、页码、金额单位与目标位置，各年度取对应年度报表期末/本期数，不用后续报表期初或比较数替代；重述差异另列说明。
- 核对三大报表的中间小计、最终合计和内部勾稽关系，同时检查新增科目覆盖、父子项重复和符号方向。
- 检查补充资料与指标依赖。缺少加权平均净资产、利息明细、期初余额或最新一期月份时，不把公式显示的 0 当作真实指标。
- 使用可用计算引擎重算、重新打开并复查输出。不能重算或有未解决项目时，明确说明具体限制。

完整性及验收细则见 [完整性与勾稽复核](skill/references/reconciliation.md)。另外检查其他综合收益分组、平均余额的实际日期及指标是否年化；仅增补最新一期时保留未要求更新的历史列。

## 仓库结构

```text
financial-statement-entry-skill/
├─ README.md
├─ LICENSE
├─ SECURITY.md
├─ skill/
│  ├─ SKILL.md
│  └─ references/
│     ├─ template-guide.md
│     ├─ missing-items.md
│     └─ reconciliation.md
├─ template/
│  └─ financial-statement-template.xlsx
└─ examples/
   └─ demo-usage.md
```

仅将通用模板和脱敏/合成样例用于公开分享，真实报告与录入结果保存在任务目录。详见 [SECURITY.md](SECURITY.md)。项目采用 [MIT 许可证](LICENSE)。
