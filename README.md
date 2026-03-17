# 美国职业市场可视化（中文版）

本仓库是对原项目 [karpathy/jobs](https://github.com/karpathy/jobs) 的中文化版本，界面文案已本地化为中文，功能与数据流程保持一致。

## 在线版

GitHub Pages 演示（可在仓库设置中配置）：

- 仓库 Pages 页面：`https://tianyu19920816.github.io/jobs-cn/`

## 项目简介

该项目是一个开发者工具，用于可视化美国劳工统计局（BLS）《职业展望手册》（Occupational Outlook Handbook）中的职业数据。页面展示了 **342 个职业**，覆盖美国经济中的约 **1.43 亿** 岗位。

当前版本支持按下列维度着色与观察：

- BLS 就业前景（就业增长变化）
- 工资中位数
- 教育要求
- 数字化 AI 暴露度（LLM 打分）

## 数据流程

1. `scrape.py` — 使用 Playwright 抓取 BLS 的原始职业页面到 `html/`。
2. `parse_detail.py`、`process.py` — 用 BeautifulSoup 解析 `html/` 并生成 `pages/` 的 Markdown。
3. `make_csv.py` — 生成结构化字段（工资、教育、岗位数、增长率、SOC code）到 `occupations.csv`。
4. `score.py` — 调用 LLM 给每个职业打分（保留原始 prompt 流程），生成 `scores.json`。
5. `build_site_data.py` — 合并 CSV 与评分，输出前端文件 `site/data.json`。
6. `site/index.html` — 树图可视化页面（当前仓库已中文化）。

## 关键文件

| 文件 | 说明 |
|---|---|
| `occupations.json` | 342 个职业的主列表（标题、URL、分类、slug） |
| `occupations.csv` | 汇总指标：工资、教育、岗位数、增长预估 |
| `scores.json` | 342 个职业的 AI 暴露评分与评分理由 |
| `prompt.md` | 用于打分的提示词模板（可直接粘贴到 LLM） |
| `site/data.json` | 前端可视化输入数据 |
| `site/index.html` | 中文可视化页面 |

## 快速启动

```bash
uv sync
uv run playwright install chromium
```

`.env` 需要设置：

```bash
OPENROUTER_API_KEY=your_key_here
```

### 常用命令

```bash
# 抓取 BLS 页面（首次运行一次，html/ 会缓存）
uv run python scrape.py

# 由 HTML 生成 markdown
uv run python process.py

# 生成汇总 csv
uv run python make_csv.py

# 计算 AI 暴露评分（需要 OpenRouter）
uv run python score.py

# 生成页面数据
uv run python build_site_data.py

# 本地预览中文页面
cd site && python -m http.server 8000
```

## GitHub Pages 部署（已配置）

仓库已新增 GitHub Actions 工作流：`.github/workflows/deploy-pages.yml`，会将 `site/` 目录内容发布到 GitHub Pages。

部署步骤：

1. 推送到 `master` 分支（或手动触发 workflow）。
2. 在仓库 Settings → Pages 中将 source 选择为 `GitHub Actions`。
3. 访问你的 Pages 地址：`https://tianyu19920816.github.io/jobs-cn/`。
