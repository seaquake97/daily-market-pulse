# Daily Market Pulse · 每日市场脉搏

> Deterministic, desensitized A-share market research — published daily, archived forever.
> 确定性、可复现的 A 股每日研判 —— 每日发布，长期归档。

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](LICENSE)
[![Pages](https://img.shields.io/badge/live-GitHub%20Pages-0075DA)](https://seaquake97.github.io/daily-market-pulse/)
[![Daily](https://img.shields.io/badge/published-daily%20%28trading%20days%29-0075DA)](https://seaquake97.github.io/daily-market-pulse/)

**Live site 线上站点**： https://seaquake97.github.io/daily-market-pulse/

---

## 这是什么 / What this is

每交易日收盘后，把当天的基金与股票研判结论**脱敏后**发布成静态网页，长期累积成一份
可回溯的市场判断记录。不是行情搬运，是**判断轨迹的存档**。

Every trading day after close, the day's fund and equity research conclusions are
**desensitized** and published as static pages, building a permanent, traceable
archive of decision-making — not a quote feed, but a record of *judgement over time*.

## 核心特征 / What makes it different

大多数每日复盘是「一次性消息」。本仓库刻意反向设计：

| 设计选择 | 理由 |
|---|---|
| **确定性引擎**，非人工撰写 | 同一份数据必然得出同一结论 —— 结论可复现、可审计 |
| **五档评级**（进攻/均衡/信号矛盾/防守/回避） | 强制区分「有方向」与「数据打架」，不允许骑墙却给方向 |
| **有效权重封顶** | 过半信号缺失时强制降级为「信号矛盾」，宁缺勿滥 |
| **观点台账四态** | 观点必须事后结算：触发/未触发/不可评估/**漏报**（骑墙也有成本） |
| **完全脱敏** | 持仓金额、成本价、网格区间、账户标识一律不出库；公开市场数据（成交额、涨跌家数占比）**完整保留** |
| **静态预渲染** | 无JS 依赖，纯 HTML，十年后仍可读 |

Most daily reviews are disposable. This one is deliberately built the other way around:

- **Deterministic, not hand-written** — same data always yields the same conclusion.
- **Five-tier rating** — forces an explicit split between "has direction" and "signals conflict".
- **Effective-weight cap** — when most signals are missing, the engine *must* downgrade rather than guess.
- **Four-state viewpoint ledger** — every past view gets settled: triggered / not triggered / unevaluable / **missed**.
- **Fully desensitized** — no holdings, cost basis, grid ranges or account identifiers, ever.
- **Static pre-rendered** — no JavaScript dependency; still readable in ten years.

## 站点结构 / Site layout

```
docs/
├── index.html                # 聚合首页 · Aggregated landing page
├── daily/YYYY-MM-DD/         # 当日全部产出 · All outputs for that day
│   ├── daily-review.html     #   每日总复盘 · Daily consolidated review
│   ├── fund-market.html      #   基金盘面 · Fund market analysis
│   ├── fund-guide.md         #   基金操作指引 · Fund action guide
│   ├── stock-assistant.html  #   股票助手 · Stock assistant
│   ├── stock-review.md       #   股票复盘 · Stock review round-table
│   └── meta.json             #   机器可读元数据 · Machine-readable metadata
├── weekly/YYYY-Www/          # 周归档 · Weekly archive
├── monthly/YYYY-MM/          # 月归档 · Monthly archive
├── methodology/              # 方法论与评分规则 · Methodology & scoring rules
├── feed.xml                  # RSS 订阅
└── sitemap.xml
```

## 五档评级 / The five-tier rating

| 评级 | Σ 区间 | 含义 |
|---|---|---|
| 进攻 | Σ ≥ +0.20 | 信号一致向上，可主动加仓 |
| 均衡 | 0 ≤ Σ < +0.20 | 中性偏积极，维持仓位 |
| **信号矛盾** | 有效权重不足或方向冲突 | **只列证据，不给方向** |
| 防守 | -0.20 ≤ Σ < 0 | 转弱，降低风险敞口 |
| 回避 | Σ < -0.20 | 明确转空，收缩至底仓 |

`信号矛盾` 是本设计的关键档位：它是一个**诚实的「不知道」**，而不是用少数信号硬凑
出一个方向。

## 配套引擎 / Companion engine

工具开源在 **[daily-decision-engine](https://github.com/seaquake97/daily-decision-engine)**（MIT），
包含确定性信号评分、数据硬校验、决策卡规范与观点台账结算脚本。

## 许可与免责 / License & Disclaimer

内容采用 [CC BY-NC-SA 4.0](LICENSE) —— 署名、非商业、相同方式共享。完整声明见 [NOTICE](NOTICE)。

**投资风险提示**：本仓库仅为个人投资方法论记录，不构成投资建议。所有数据已脱敏，
不含任何个人持仓信息。市场有风险，决策需独立判断。

Content is licensed under CC BY-NC-SA 4.0. This repository contains personal
investment methodology notes only and **does not constitute investment advice**.
All data is desensitized and contains no personal holdings information.

---

*由「老北京的热干面」维护 · Maintained by Laobei Beijing Hot Dry Noodles*