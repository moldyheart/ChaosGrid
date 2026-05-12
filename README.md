# ChaosGrid

> Offline Random Number & Table Generator  
> 完全离线运行的随机数、随机表格、随机分组与模拟数据生成器

ChaosGrid 是一个纯前端、完全离线运行的随机数据生成工具。用户只需要打开一个本地 `index.html` 文件，就可以在浏览器中生成随机整数、随机小数、不重复随机数、随机表格、随机分组、抽奖号码、时间序列数据、模拟测试数据和随机矩阵，并支持 CSV、TXT、JSON 导出。

本项目默认使用浏览器内置的 Web Crypto API 作为随机源，而不是普通的 `Math.random()`，以提高随机结果的不可预测性。同时，系统提供 Seed Mode 用于可复现实验，也提供 Human-like Mode 用于减少人眼容易察觉的明显规律。

---

## Project Highlights

- Fully offline: no server, no database, no login, no network request
- Single-file deployment: open `index.html` directly in a browser
- Secure random source: uses Web Crypto API by default
- Reproducible generation: Seed Mode supports repeatable results
- Human-like random mode: reduces obvious visible patterns
- Multiple generation modes: numbers, tables, groups, lottery, time series, mock data, matrix
- Data export: CSV, TXT, and JSON
- Statistics summary: mean, median, standard deviation, duplicate rate, unique count, and more
- Pattern detection: repeated values, increasing/decreasing runs, fixed differences, clustering
- Randomness score: visual randomness score from 0 to 100
- Local settings: saves user preferences with `localStorage`
- Dark mode and language switch: supports light/dark theme and Chinese/English switching
- Privacy-first: all data is generated and processed locally in the browser

---

## Demo Usage

1. Download or save `index.html`.
2. Open it directly with Chrome, Edge, Firefox, or Safari.
3. Select a generation mode.
4. Configure the parameters.
5. Click Generate.
6. Preview the result, check statistics, then copy or download the data.

No installation is required. No Node.js, server, database, or internet connection is needed.

---

## Core Features

### 1. Single Number List

Generate a list of random numbers with configurable rules.

Supported options:

- Integer or decimal output
- Minimum and maximum value
- Number count
- Decimal places
- Allow or disallow duplicates
- Sort output
- Shuffle output
- Show index column

Example output:

```text
23
88
4
61
39
72
10
95
41
7
```

Use cases:

- Random sampling
- Lottery preparation
- Teaching examples
- Test input generation
- Random ID or number list generation

---

### 2. Secure Random Integer Generator

ChaosGrid uses `window.crypto.getRandomValues()` by default when the browser supports it.

For integer generation, the system avoids simple modulo mapping and uses rejection sampling to reduce modulo bias.

This makes the random source stronger than ordinary `Math.random()` for general random data generation tasks.

Important note:

ChaosGrid is not a cryptographic key generator. It should not be used as the only source for high-stakes security or cryptographic key generation.

---

### 3. Decimal Random Generator

Generate decimal values within a custom range.

Supported options:

- Minimum value
- Maximum value
- Count
- Decimal places from 0 to 10
- Duplicate control
- Sorting

Example:

```text
0.4821
0.0392
0.7740
0.6105
0.2217
```

When decimal places are set to 0, the result behaves like integer generation.

---

### 4. Unique Random Number Generator

When duplicate values are disabled, ChaosGrid generates values without repetition.

For integers, it checks whether the requested count exceeds the available range.

Example:

```text
Range: 1 to 100
Count: 10
Duplicate: Disabled
```

The output will contain 10 different numbers.

If the user requests 200 unique values from a range of 1 to 100, the system shows a clear validation error.

---

### 5. Seed Mode

Seed Mode allows reproducible random generation.

Rules:

- Same seed + same parameters = same result
- Different seed usually produces different result
- Useful for teaching, experiments, testing, and debugging
- Not suitable for security-sensitive random generation

Example:

```text
Seed: experiment-001
Mode: Integer
Range: 1 to 100
Count: 10
```

Running the same setup again produces the same random sequence.

---

### 6. Human-like No Obvious Pattern Mode

Human-like Mode reduces patterns that are easy for humans to notice.

The system checks and reduces:

- Long repeated values
- Long increasing sequences
- Long decreasing sequences
- Repeated fixed differences
- High duplicate rate
- Over-concentrated distribution
- Visually unnatural clusters

Important note:

Human-like Mode does not make the data mathematically more random. It only reduces obvious visual patterns.

---

### 7. Random Table Generator

Generate structured random tables with custom rows and columns.

Supported options:

- Row count
- Column count
- Custom column names
- Custom column types
- Add ID column
- Add timestamp column
- Preview first 100 rows for large datasets
- Download full data as CSV, TXT, or JSON

Example:

```csv
ID,Score,Age,Group
1,87,20,A
2,64,23,B
3,91,19,A
4,72,25,C
5,80,21,B
```

---

## Supported Table Field Types

ChaosGrid supports many field types for random table generation.

| Field Type | Description |
|---|---|
| Integer | Random integer in a custom range |
| Decimal | Random decimal with custom precision |
| Percentage | Random percentage from 0% to 100% |
| Boolean | Random true or false |
| Category | Random value from a custom category list |
| Group | Random group label such as A, B, C, D |
| ID | Auto-incrementing ID |
| Date | Random date |
| Time | Random time |
| DateTime | Random date and time |
| Random Code | Random alphanumeric code |
| Score | Random score from 0 to 100 |
| Normal Distribution Number | Approximate normal-distribution value |
| Weighted Category | Random category based on custom weights |

---

### 8. Random Group Assignment

Randomly assign participants into groups.

Supported options:

- Participant count
- Group count
- Custom group names
- Balanced assignment
- Shuffle participants
- Export group table

Example:

```csv
Participant ID,Group
1,A
2,B
3,B
4,A
5,A
```

Use cases:

- Classroom grouping
- Experiment/control group assignment
- Team allocation
- A/B test simulation

---

### 9. Lottery Mode

Generate winner numbers for lottery or draw scenarios.

Supported options:

- Number range
- Winner count
- Backup count
- Unique winners
- Sort winners
- Hide result until Reveal

Example:

```text
Winners: 7, 28, 44, 63, 91
Backups: 12, 37
```

Use cases:

- Prize draw
- Random selection
- Lucky number generation
- Backup winner list

---

### 10. Time Series Mode

Generate random time-series data with a time column.

Supported options:

- Start datetime
- Row count
- Time interval in minutes
- Value range
- Decimal places
- Custom value column name

Example:

```csv
Time,Value
2026-01-01 00:00,82
2026-01-01 01:00,79
2026-01-01 02:00,91
```

Use cases:

- Sensor data simulation
- Price data simulation
- Temperature data simulation
- Chart testing
- Machine learning practice data

---

### 11. Mock Dataset Mode

Generate realistic-looking but completely fake test data.

Built-in presets:

- Mock Users
- Mock Orders
- Survey Dataset
- Student Scores

Example fields:

- user_id
- order_id
- age
- score
- price
- quantity
- rating
- group
- status
- percentage
- risk_score
- created_time

Use cases:

- Frontend table testing
- Backend mock API testing
- Database import testing
- Data analysis practice
- CSV/JSON demo data generation

---

### 12. Random Matrix Generator

Generate an `m × n` random matrix.

Supported options:

- Row count
- Column count
- Minimum value
- Maximum value
- Integer or decimal type
- Decimal places
- Optional row and column labels

Example:

```text
12,44,8
91,27,65
33,72,10
```

Use cases:

- Mathematics practice
- Algorithm testing
- Linear algebra examples
- Machine learning input simulation

---

## Templates

ChaosGrid includes one-click templates for common tasks.

| Template | Purpose |
|---|---|
| Quick 10 Numbers | Generate 10 random integers from 1 to 100 |
| Unique Draw | Generate unique random values |
| Lottery 6 | Generate 6 unique lottery numbers from 1 to 49 |
| Student Scores | Generate student score dataset |
| A/B Groups | Generate A/B test group assignment |
| Matrix 10×10 | Generate a 10 by 10 random matrix |
| Time Series | Generate 24 hourly time-series rows |
| Mock Orders | Generate mock order data |
| Survey | Generate survey-style dataset |
| Normal Sample | Generate normal-distribution sample data |

---

## Statistics Summary

After data generation, ChaosGrid automatically calculates numeric statistics.

For number lists and numeric table fields, it can display:

- Count
- Minimum
- Maximum
- Mean
- Median
- Mode
- Standard deviation
- Variance
- Unique count
- Duplicate count
- Duplicate rate
- Sum
- Distribution summary

These statistics help users quickly understand whether the generated data is reasonable.

---

## Pattern Detection

ChaosGrid checks generated data for visible patterns.

Detected pattern types:

- Repeated values in a row
- Increasing sequences
- Decreasing sequences
- Repeated difference patterns
- High duplicate rate
- Concentrated value distribution

Example warnings:

```text
Repeated value detected.
Increasing sequence detected.
Repeated difference pattern detected.
Values are concentrated in one range.
```

If no obvious pattern is detected, ChaosGrid displays a positive message.

---

## Randomness Score

ChaosGrid provides a visual randomness score from 0 to 100.

Score interpretation:

| Score | Meaning |
|---|---|
| 90 - 100 | Very random-looking, no strong visible pattern |
| 70 - 89 | Mostly random-looking, with small visible imbalance |
| 50 - 69 | Some visible patterns or distribution imbalance |
| 0 - 49 | Strong visible pattern or abnormal distribution |

This score is only a visual and statistical helper. It is not a strict mathematical proof of randomness.

---

## Export Formats

ChaosGrid supports three export formats.

### CSV

Best for:

- Excel
- Google Sheets
- Python pandas
- R
- Weka
- Data analysis tools

CSV export includes headers for table data.

### TXT

Best for:

- Simple number lists
- Plain text records
- Code lists
- Quick copying and saving

### JSON

Best for:

- Frontend development
- API mock data
- Program testing
- Data exchange

JSON output is formatted with 2-space indentation.

---

## Copy to Clipboard

The Copy button copies the current result into the clipboard.

Copy format:

- Number list: one value per line
- Table: tab-separated text for Excel or Google Sheets
- JSON export: structured JSON string through the download function

If the browser blocks clipboard access, ChaosGrid shows a clear error message.

---

## Dark Mode

ChaosGrid supports light and dark themes.

The theme switch applies instantly and is saved locally through `localStorage`.

When the user opens the page again, the previous theme is restored automatically.

---

## Language Switch

ChaosGrid supports switching between Chinese and English.

The language button is placed in the top action area. The selected language is saved locally, so the interface can restore the last selected language on the next visit.

---

## Local Settings and History

ChaosGrid stores lightweight local preferences in the browser.

Saved locally:

- Current mode
- Random source
- Seed text
- Number parameters
- Table parameters
- Theme
- Language
- Recent generation history summary

Privacy note:

Only settings and small history summaries are saved. Generated data is not uploaded to any server.

---

## Privacy and Security

ChaosGrid is designed as a privacy-first offline tool.

It does not:

- Require login
- Use a backend server
- Use a database
- Request remote APIs
- Upload generated data
- Track users with cookies
- Read local files
- Execute user-provided code

All generation, preview, statistics, and export operations happen inside the user's browser.

---

## Performance Design

ChaosGrid is designed to handle large generated datasets safely.

Performance rules:

- Large results only preview the first 100 rows
- Full data remains available for download
- Single number generation has an upper limit
- Table row and column counts are limited
- Human-like Mode has a maximum retry count
- Rendering avoids displaying too many DOM rows at once

This prevents the page from freezing when generating large datasets.

---

## Browser Compatibility

Recommended browsers:

- Chrome
- Microsoft Edge
- Firefox
- Safari

Requirements:

- Modern browser
- JavaScript enabled
- Local file opening support
- Web Crypto API recommended

If Web Crypto API is unavailable, ChaosGrid can fall back to a less secure random mode and shows a warning.

---

## Project Structure

The final version is designed as a single-file offline web app.

```text
ChaosGrid/
└── index.html
```

Inside `index.html`:

```text
HTML structure
CSS styles
JavaScript logic
Random generation module
Seed PRNG module
Human-like pattern module
Statistics module
Export module
UI rendering module
LocalStorage module
Language and theme module
```

No external assets are required.

---

## Technical Design

### Random Source Layer

The random source layer provides three modes:

1. Secure Crypto Random
2. Seed Mode
3. Fallback Random

Secure mode uses Web Crypto API. Seed mode uses deterministic pseudo-random generation for reproducibility. Fallback mode exists only for compatibility.

### Generation Layer

The generation layer handles:

- Number list generation
- Unique number generation
- Decimal generation
- Table generation
- Group assignment
- Lottery generation
- Time-series generation
- Mock dataset generation
- Matrix generation

### Analysis Layer

The analysis layer handles:

- Statistics summary
- Distribution summary
- Pattern warning
- Randomness score

### Export Layer

The export layer converts generated data into:

- CSV
- TXT
- JSON
- Clipboard text

### UI Layer

The UI layer handles:

- Mode switching
- Result preview
- Error messages
- Help dialog
- Theme switching
- Language switching
- Local setting restoration

---

## Validation Rules

ChaosGrid validates user input before generation.

Common validation checks:

- Minimum value must be less than or equal to maximum value
- Count must be greater than 0
- Decimal places must be between 0 and 10
- Unique count cannot exceed available range
- Row count must be greater than 0
- Column count must be greater than 0
- Group count cannot exceed participant count
- Category list cannot be empty
- Seed cannot be empty in Seed Mode
- Date and time input must be valid

Errors are shown clearly in the interface.

---

## Example Workflows

### Generate 10 Random Integers

1. Select Single Number List.
2. Select Integer.
3. Set range from 1 to 100.
4. Set count to 10.
5. Click Generate.
6. Copy or download the result.

### Generate a Student Score Table

1. Select the Student Scores template.
2. Set row count if needed.
3. Click Generate.
4. Check average and score distribution.
5. Download as CSV.

### Generate A/B Test Groups

1. Select the A/B Groups template.
2. Set participant count.
3. Enable balanced assignment.
4. Click Generate.
5. Download the group table.

### Generate Reproducible Random Data

1. Select Seed Mode.
2. Enter a seed such as `experiment-001`.
3. Configure mode and parameters.
4. Click Generate.
5. Reuse the same seed and settings to reproduce the same result.

---

## Limitations

ChaosGrid is a practical random data generator, not a formal randomness certification tool.

Limitations:

- It does not generate physical true randomness
- It should not be used as the only source for cryptographic keys
- Human-like Mode improves visual randomness only
- Randomness Score is an auxiliary indicator, not a proof
- Very large datasets may be limited to protect browser performance

---

## Future Improvements

Possible future extensions:

- XLSX export
- Charts and visual distribution graphs
- Heatmap table preview
- More statistical distributions
- More mock data presets
- Import/export configuration files
- Advanced weighted sampling
- More language options
- More field validators
- Better mobile editing experience

---

## Final Project Description

ChaosGrid is a fully offline random number and random table generator built with HTML, CSS, and JavaScript. It allows users to generate secure random integers, decimals, unique numbers, random tables, group assignments, lottery numbers, mock datasets, time-series data, and random matrices directly in the browser. The system uses the Web Crypto API by default to improve unpredictability and provides Seed Mode for reproducible results. It also includes human-like pattern reduction, statistical summaries, randomness scoring, pattern warnings, dark mode, language switching, local settings, and CSV/TXT/JSON export. No server, database, login, or internet connection is required.

ChaosGrid 是一个使用 HTML、CSS 和 JavaScript 构建的完全离线随机数与随机表格生成器。用户可以直接在浏览器中生成安全随机整数、小数、不重复数字、随机表格、随机分组、抽奖号码、模拟测试数据、时间序列数据和随机矩阵。系统默认使用 Web Crypto API 提高随机结果的不可预测性，同时提供 Seed Mode 用于复现实验结果。系统还包含无明显规律模式、统计摘要、随机性评分、规律警告、暗色模式、语言切换、本地设置保存以及 CSV/TXT/JSON 导出功能。整个项目不需要服务器、数据库、登录系统或网络连接。
