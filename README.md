# 🎲 ChaosGrid

<p align="center">
  <strong>完全离线随机数与随机表格生成器</strong><br>
  Offline Random Number & Random Table Generator
</p>

<p align="center">
  <img alt="Version" src="https://img.shields.io/badge/version-v0.5.1-blue">
  <img alt="Offline" src="https://img.shields.io/badge/offline-ready-brightgreen">
  <img alt="Single File" src="https://img.shields.io/badge/single--file-HTML-orange">
  <img alt="Privacy" src="https://img.shields.io/badge/privacy-local--only-purple">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-lightgrey">
</p>

---

## ✨ 项目简介

ChaosGrid 是一个使用 HTML、CSS 和 JavaScript 构建的完全离线随机数据生成工具。

它不需要服务器、不需要数据库、不需要登录、不需要网络连接。用户只要打开一个本地 HTML 文件，就可以生成随机数、随机表格、随机分组、抽奖结果、时间序列、模拟数据集、矩阵数据和概率模型模拟结果，并导出为 CSV、TXT、JSON、XLSX 等格式。

ChaosGrid 默认使用浏览器的 Web Crypto API 作为随机源，比普通 Math.random 更适合需要较高不可预测性的普通随机数据场景。同时，它也提供 Seed Mode，用于可复现实验、教学演示和测试数据复现。

> 注意：ChaosGrid 不是物理真随机数发生器，也不应作为加密密钥或高风险安全系统的唯一随机来源。

---

## 🚀 当前版本

当前版本：v0.5.1 Bugfix Edition

v0.5.1 修复了 Data Quality 中 Duplicate Row Rate 导致 ID / Index / Participant ID 序号错乱的问题。现在重复行仍然可以模拟重复数据，但显示用序号会保持连续、可读、可导出。

---

## 🧩 核心功能总览

### 🎯 随机数生成

- 生成整数
- 生成小数
- 设置最小值、最大值、数量
- 设置小数位数
- 允许或禁止重复
- 排序输出
- 打乱输出
- 显示序号列
- 支持大批量生成

### 🔐 随机源选择

- Secure Crypto Random：默认模式，使用 Web Crypto API
- Seed Mode：相同 seed + 相同参数可复现相同结果
- Fallback Random：兼容模式，用于不支持 Web Crypto 的浏览器

### 🧠 Human-like No Obvious Pattern Mode

用于减少人眼容易察觉的明显规律，例如：

- 连续重复
- 连续递增
- 连续递减
- 固定差值
- 重复率过高
- 区间过度集中

该模式只是让结果在视觉上更不容易看出规律，不代表数学上更随机。

---

## 📊 支持的生成模式

### 1. 🔢 Single Number List

生成一列随机数字。

适合：

- 随机编号
- 抽样数字
- 测试输入
- 简单随机数列表

### 2. 📋 Random Table

生成多行多列随机表格。

支持字段类型：

- Integer
- Decimal
- Percentage
- Boolean
- Category
- Group
- ID
- Date
- Time
- DateTime
- Random Code
- Score
- Normal Distribution Number
- Weighted Category

支持快速字段：

- User ID
- Order ID
- Price
- Age
- Score
- Status
- Risk Level
- Rating
- Created Time

### 3. 👥 Group Assignment

随机分组工具。

支持：

- 输入参与者数量
- 输入组数和组名
- 平均分配
- 打乱参与者
- 粘贴真实参与者名单
- 导出分组结果

适合课堂分组、实验组分配、A/B 测试、比赛分队。

### 4. 🎟️ Lottery Mode

抽奖号码生成工具。

支持：

- 设置号码范围
- 设置中奖数量
- 设置备用号码数量
- 不重复中奖号码
- 排序中奖号码
- 隐藏结果直到点击 Reveal
- 中奖号码卡片展示
- Range Position Chart 展示中奖号码在范围内的位置

### 5. ⏱️ Time Series Mode

生成时间序列数据。

支持：

- 开始时间
- 行数
- 时间间隔
- 数值范围
- 小数位数
- 自定义数值列名
- 趋势：None / Upward / Downward
- 季节性：None / Daily Wave / Weekly Wave
- 噪声强度
- 尖峰比例

适合图表测试、传感器数据模拟、价格数据模拟、机器学习练习数据。

### 6. 🧪 Mock Dataset Mode

生成结构化模拟数据集。

内置模板：

- Mock Users
- Mock Orders
- Survey Dataset
- Student Scores

适合前端表格测试、后端接口 mock、数据库导入测试、Excel 练习和数据分析练习。

### 7. 🧮 Random Matrix

生成随机矩阵。

支持：

- 行数
- 列数
- 最小值
- 最大值
- 整数或小数
- 行列标签
- 热力图可视化

适合数学练习、算法测试、线性代数演示、机器学习矩阵输入。

### 8. 🎲 Probability Model Mode

概率模型模拟器。

支持模型：

- Coin Toss
- Dice Roll
- Weighted Outcome
- Bernoulli Trial
- Binomial Experiment
- Multinomial Experiment
- Card Draw / Gacha
- Rare Event
- Poisson Event Count
- Custom Scenario

可以对比理论概率和实际频率，并显示偏差图表。

---

## 📈 图表与分析

ChaosGrid 内置 Charts Dashboard，用于直观理解生成结果。

图表全部采用纵向排列，一张一张往下显示，避免并排导致看不全。

支持的图表包括：

- Distribution Histogram
- Sorted Value Strip
- Numeric Column Means
- Category Frequency
- Expected vs Observed Counts
- Deviation from Expectation
- Time Series Line Chart
- Matrix Heatmap
- Group Balance Chart
- Lottery Result Cards
- Range Position Chart

每个图表尽量包含：

- 标题
- 简短解释
- 数据标签
- 坐标或图例
- 自动分析说明
- SVG / PNG 导出

---

## 📐 数据预览与 DataGrid 功能

结果预览区支持更接近专业 DataGrid 的操作：

- 搜索结果
- 分页显示
- 每页行数选择
- 点击表头排序
- 显示或隐藏列
- 筛选后导出 CSV
- 大数据只预览部分行，完整数据仍可下载

这使 ChaosGrid 不只是生成数据，也可以快速检查数据是否合理。

---

## 🧾 统计摘要与质量检测

生成数据后，系统会自动计算统计信息：

- Count
- Min
- Max
- Mean
- Median
- Mode
- Standard Deviation
- Variance
- Unique Count
- Duplicate Count
- Duplicate Rate
- Sum

同时提供：

- Randomness Score
- Pattern Warning
- Distribution Summary
- Probability Deviation Warning
- Report Tab
- Generate Report
- Copy Report

---

## 🧬 Advanced Data Quality

ChaosGrid 支持模拟真实世界数据中的质量问题：

- Missing Value Rate
- Duplicate Row Rate
- Outlier Rate
- Null Format：empty / null / N/A

用途：

- 数据清洗练习
- 机器学习预处理练习
- 数据库测试
- Excel / Python / R / Weka 练习
- 前端表格异常状态测试

v0.5.1 已修复 Duplicate Row Rate 造成 ID 序号错乱的问题。

---

## 📦 导出功能

支持导出：

- Copy：复制到剪贴板
- CSV：适合 Excel、Google Sheets、Python、R
- Filtered CSV：导出当前筛选后的结果
- TXT：适合简单列表和纯文本记录
- JSON：适合前端开发和 API mock
- XLSX：适合直接使用 Excel 打开
- Config：导出当前参数配置
- Chart SVG：导出图表 SVG
- Chart PNG：导出图表 PNG
- Report：生成分析报告

---

## 🌗 界面与交互

ChaosGrid v0.5.1 包含：

- Light / Dark Mode
- 中文 / English 切换
- Simple View / Professional View
- Template Gallery
- Fixed Action Bar
- Preview / Charts / Summary / Export / Report Tabs
- History Restore / Regenerate / Download CSV
- Self Test
- Help Dialog
- Local Settings Save

---

## 🧭 快速开始

### 方法一：直接打开

1. 下载 `chaosgrid_index_v0.5.1.html`
2. 双击文件
3. 在浏览器中打开
4. 选择模式
5. 设置参数
6. 点击 Generate
7. 复制或下载结果

### 方法二：放入项目目录

推荐文件结构：

```text
ChaosGrid/
├── chaosgrid_index_v0.5.1.html
├── README.md
├── LICENSE
└── screenshots/
    ├── preview.png
    ├── charts.png
    └── export.png
```

### 方法三：改名为 index.html

如果你想把它作为 GitHub Pages 或本地网页展示，可以把文件改名为：

```text
index.html
```

然后直接打开或部署。

---

## 📁 文件内容说明

ChaosGrid 当前是一个单文件离线网页项目。

### `chaosgrid_index_v0.5.1.html`

主程序文件，包含所有页面、样式和逻辑。

内部主要由三部分组成：

#### 1. HTML Structure

负责页面结构，包括：

- Header 顶部状态栏
- Settings 设置区
- Mode Parameters 模式参数区
- Template Gallery 模板库
- Result Workspace 主工作区
- Preview / Charts / Summary / Export / Report Tabs
- Insight Panel 右侧分析面板
- Help Dialog 帮助面板

#### 2. CSS Styles

负责界面视觉，包括：

- Light / Dark theme
- Card layout
- Button styles
- DataGrid preview
- Chart dashboard
- Responsive layout
- Simple / Professional View
- Badge and status style

#### 3. JavaScript Logic

负责核心功能，包括：

- 随机源管理
- Secure random integer generation
- Seeded PRNG
- 各模式数据生成
- 表格字段生成器
- 概率模型模拟
- 时间序列增强
- 数据质量模拟
- 统计摘要计算
- 规律检测
- 图表渲染
- 表格预览搜索、分页、排序
- 文件导出
- 历史记录
- 配置导入导出
- 中英文切换
- 暗色模式
- 自检

---

## 🧠 技术亮点

### 🔐 Web Crypto API

默认使用浏览器原生 Web Crypto API：

```js
window.crypto.getRandomValues(...)
```

整数生成使用 rejection sampling，尽量减少简单取模带来的偏差。

### 🌱 Seeded Random

Seed Mode 使用确定性伪随机序列，适合复现实验。

相同 seed 和相同参数会得到相同结果。

### 📊 SVG Charts

图表使用原生 HTML / CSS / JavaScript 渲染，不依赖外部图表库。

优点：

- 离线可用
- 无 CDN
- 可导出 SVG / PNG
- 深色模式兼容
- 容易自定义

### 📴 完全离线

ChaosGrid 不加载外部脚本，不请求远程 API，不上传用户数据。

所有数据只在当前浏览器本地生成和处理。

---

## 🛡️ 隐私说明

ChaosGrid 的设计原则：

- 不需要用户登录
- 不需要服务器
- 不需要数据库
- 不上传生成结果
- 不读取本地文件内容，除非用户主动导入配置
- 设置和历史记录只保存在 localStorage
- 可以在断网环境下使用

---

## ✅ 测试建议

发布或提交前建议测试：

### 基础测试

- 生成 10 个整数
- 生成 10 个小数
- 生成不重复数字
- 生成随机表格
- 生成随机分组
- 生成抽奖结果
- 生成时间序列
- 生成 Mock Dataset
- 生成矩阵
- 生成概率模型结果

### 导出测试

- Copy
- CSV
- Filtered CSV
- TXT
- JSON
- XLSX
- Config
- Report
- Chart SVG
- Chart PNG

### 边界测试

- 最小值大于最大值
- 数量为 0
- 不重复数量超过范围
- Seed 为空
- 权重格式错误
- 概率小于 0 或大于 1
- 大数据量预览
- Data Quality 中 Duplicate Row Rate

### UI 测试

- 中文 / English 切换
- Light / Dark Mode
- Simple / Professional View
- Preview Tabs
- 搜索、分页、排序
- 历史记录恢复
- Self Test
- 离线打开

---

## 📌 适用场景

ChaosGrid 适合：

- 课堂教学
- 数据分析练习
- Excel / Google Sheets 测试
- Python / R / Weka 数据练习
- 前端表格 mock
- 后端接口测试
- 数据库导入测试
- 随机分组
- 抽奖编号
- 概率实验模拟
- 时间序列图表测试
- 机器学习样本模拟
- 项目展示和课程作业

---

## 🗺️ 版本记录

### v0.5.1

- 修复 Duplicate Row Rate 导致 ID / Index / Participant ID 错乱的问题
- 保持重复数据模拟能力
- 保持显示序号连续

### v0.5.0

- Professional UI Edition
- 新增 Simple / Professional View
- 新增 Welcome 首屏引导
- 新增 Report Tab
- Template Gallery 卡片化
- 图表全部改为纵向排列
- DataGrid 视觉升级

### v0.4.0

- 新增 Preview / Charts / Summary / Export Tabs
- 新增表格搜索、分页、排序、列显示
- 新增 Data Quality 模拟
- 新增时间序列趋势、季节性、噪声和尖峰
- 新增图表导出和报告生成

### v0.3.x

- 图表 Dashboard 重构
- 增强概率模型可视化
- 增强矩阵热力图
- 增强时间序列折线图

### v0.2.x

- 新增概率模型模式
- 新增中英文切换
- 新增多种模板

---

## 📄 License

推荐使用 MIT License。

```text
MIT License

Copyright (c) 2026 ChaosGrid

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files, to deal in the Software
without restriction, including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.
```

---

## ⭐ 一句话总结

ChaosGrid 的核心不是“生成一个随机数”，而是在完全离线环境下，按用户要求生成高质量、可配置、可下载、可分析、视觉上无明显规律的随机数据表。

