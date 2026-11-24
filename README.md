# 轮展简报的统计资料和编目

以下台账为合成数据，不涉及真实访客、供应商或展馆。CSV 采用 UTF-8，首行为字段名，空字段代表源资料未给出。标识仅在字段明示的实体范围内使用。`data/agreements.json` 是当期业务方提供的运营资料，`data/formats.json` 记录文件列顺序和确定的外键引用。

- `data/zones.csv` 记录展区、主办馆和开放类型。列为 `zone`、`venue`、`type`、`edition`、`capacity_grade`。
- `data/eligibility.csv` 记录开放机会抽样与资格的已知范围。列为 `elig_id`、`zone`、`period`、`groups_low`、`groups_high`、`complete`、`received`、`hours_basis`。
- `data/visits.csv` 记录组级人工观测。列为 `obs`、`elig_id`、`group`、`audience`、`persons`、`status`、`received`。
- `data/followup.csv` 记录抽访期、记录分数与追踪回执。window 为以期为单位的到期滞后。列为 `group`、`elig_id`、`window`、`rating`、`received`、`result`。
- `data/claims.csv` 记录编辑登记的统计判词和显示约定。列为 `claim`、`operation`、`focus`、`scope`、`period`、`reference`、`numerator`、`denominator`、`measure`、`rounding`、`qualifier`、`threshold`。
- `data/artifacts.csv` 记录各渠道实际成稿状态。列为 `artifact`、`channel`、`audience`、`edition`、`state`、`received`。
- `data/references.csv` 记录印稿、图层及脚注所引用的判词与联合解释组。列为 `artifact`、`claim`、`location`、`group_label`。
- `data/printed_values.csv` 记录已成稿材料保存的字面备注和采用的资料截点，原稿可能已有错引。列为 `artifact`、`claim`、`display_text`、`fact_cutoff`。
- `data/corrections.csv` 记录资格台账补回记录；verified 为 0 时由编辑决定是否采用为待核信息。列为 `fix`、`elig_id`、`received`、`verified`、`low_delta`、`reason`。
- `data/receipts.csv` 记录真实送达和馆方签收或待查。列为 `receipt`、`artifact`、`venue`、`sent`、`result`。

使用 Python 3.11，无第三方依赖。用 `python3 -m unittest discover -s tests -v` 核对文件的可读性、列结构和确定引用，源文件保持只读。
