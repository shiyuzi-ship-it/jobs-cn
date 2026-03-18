# 美国职业市场可视化（中文版）

这是一个面向中文读者的职业数据可视化页面，基于美国劳工统计局（BLS）《职业展望手册》整理而成。你可以用树图的方式快速浏览美国职业结构，观察不同职业的岗位规模、薪资水平、教育要求、就业前景，以及数字化 AI 暴露度。

## 在线访问

<a href="https://shiyuzi-ship-it.github.io/jobs-cn/" target="_blank" rel="noopener noreferrer">
  <img src="https://img.shields.io/badge/GitHub%20Pages-访问中文版-2ea44f?style=for-the-badge" alt="访问中文版">
</a>

页面地址：

[https://shiyuzi-ship-it.github.io/jobs-cn/](https://shiyuzi-ship-it.github.io/jobs-cn/)

## 页面内容

页面收录了 **342 个职业**，覆盖美国经济中的约 **1.43 亿个岗位**。

每个矩形代表一个职业：

- 面积表示岗位数量
- 颜色表示当前选择的观察维度
- 点击职业块可跳转到对应的 BLS 原始页面

当前可切换的维度包括：

- 就业前景
- 工资中位数
- 教育要求
- 数字化 AI 暴露度

## 数据来源

本页面主要基于美国劳工统计局（BLS）的职业展望手册数据：

- BLS Occupational Outlook Handbook: [https://www.bls.gov/ooh/](https://www.bls.gov/ooh/)

## 关于 AI 暴露度

“数字化 AI 暴露度”是一个辅助观察指标，用来估计 AI 对不同职业工作方式的潜在重塑程度。

它不是失业预测，也不代表某个职业一定会被替代。更准确地说，它反映的是：当工作内容越偏向数字化、信息处理、写作、分析、沟通或生成时，AI 对该职业产生影响的可能性通常越高。

## 来源项目

本仓库基于原项目 [karpathy/jobs](https://github.com/karpathy/jobs) 制作，并在其基础上完成了中文化改写与页面适配。原项目作者整理了抓取、清洗、评分和可视化这套完整流程，本仓库保留其数据结构与展示逻辑，并提供中文版本页面。

## 本地运行

如果你希望在本地打开页面，可以使用：

```bash
cd site && python3 -m http.server 8000
```

然后访问 `http://localhost:8000`。

## 部署说明

仓库已配置 GitHub Pages 工作流。首次启用时，需要在仓库的 `Settings -> Pages` 中将发布来源设置为 `GitHub Actions`。

部署完成后，页面地址为：

[https://shiyuzi-ship-it.github.io/jobs-cn/](https://shiyuzi-ship-it.github.io/jobs-cn/)
