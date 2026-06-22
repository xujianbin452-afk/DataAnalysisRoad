# 信贷逾期风险分析

## 项目背景

信贷业务需要在业务规模与资产质量之间取得平衡。本项目基于 Give Me Some Credit 公开数据，以未来两年是否发生严重逾期为风险标签，识别具有较高风险的客群特征，并评估不同准入规则对通过率和风险水平的影响。

## 分析目标

- 审计数据质量，识别缺失值、异常值和无效字段；
- 分析年龄、收入、负债率、额度使用率及历史逾期行为与坏客户率的关系；
- 识别具有稳定风险差异的单变量和组合客群；
- 构建可解释的规则型风险分层；
- 比较不同准入阈值下的通过率、坏客户捕获率和好客户误伤率；
- 根据分析结果提出准入、额度和风险监控建议。

## 数据说明

- 数据集：Give Me Some Credit
- 样本量：150,000
- 目标变量：`SeriousDlqin2yrs`
- 坏客户定义：未来两年发生严重逾期或财务困境
- 整体坏客户率：6.684%

镜像数据额外包含 `timestamp` 和 `id`。其中 `timestamp` 为全量相同的占位时间，不作为业务字段；`id` 仅用于记录定位，不参与风险分析。

## 项目结构

```text
01_Credit_Risk_Analysis/
├── data/
│   ├── raw/                 # 原始数据，本地保存
│   └── processed/           # 清洗和样本划分结果
├── docs/
│   └── 数据说明.md
├── notebooks/
│   ├── 01_business_understanding.ipynb
│   ├── 02_data_quality_cleaning.ipynb
│   ├── 03_risk_factor_analysis.ipynb
│   ├── 04_risk_segmentation.ipynb
│   └── 05_strategy_simulation.ipynb
├── output/
│   ├── figures/
│   └── tables/
├── sql/
├── requirements.txt
└── README.md
```

## 分析流程

1. 业务理解与字段审计
2. 数据质量检查与清洗
3. 开发集、验证集划分
4. 单变量及组合客群风险分析
5. 规则型风险分层
6. 准入策略模拟
7. 业务建议与项目复盘

## 核心评价指标

- 通过率与拒绝率
- 通过客群坏客户率
- 坏客户捕获率
- 好客户误伤率
- 不同风险层级的样本占比与坏客户率

## 项目边界

该数据不包含完整的申请、放款、应还和实还时间，也缺少贷款金额、利率与资金成本，因此本项目不开展严格的 Vintage、MOB、迁徙率或利润测算。策略模拟用于比较规则的风险区分效果，不代表真实线上策略的因果收益。

## 运行环境

```bash
pip install -r requirements.txt
jupyter notebook
```

按编号顺序运行 `notebooks` 下的文件即可复现分析流程。

