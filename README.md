# GTO 德州扑克助手

手机上用的德州扑克决策助手。翻前查内置 GTO 图表,翻后实时算胜率与各选项 EV。
全部计算在浏览器本地完成,不依赖任何后端。

## 用法

打开 GitHub Pages 地址,在 iPhone Safari 里「添加到主屏幕」即可当 App 用,离线可用。

## 结构

- `src/evaluator.js` — 7 张牌牌型评估器(查表顺子 + 位运算)
- `src/ranges.js` — 169 手起手牌、范围解析、翻前 GTO 图表
- `src/ranking.js` — 自动生成的 169 手牌强度排序(`tools/gen-ranking.js`)
- `src/equity.js` — 蒙特卡洛胜率、河牌精确枚举、范围收窄
- `src/advisor.js` — 决策引擎:混合频率 + 各选项 EV
- `src/glossary.js` — 39 条术语的大白话解释
- `src/ai.js` — 可选的大模型教练(OpenAI 兼容接口)
- `src/ui.js` / `src/styles.css` / `src/app.html` — 界面

## 构建

```
node tools/build.js      # → dist/index.html(单文件)与 site/(带 service worker)
node tools/test.js       # 牌型评估 / 范围解析 / 胜率
node tools/scenarios.js  # 决策场景
node tools/smoke.js      # 参数矩阵冒烟
```

## 说明

EV 为单街近似,不含后续街的隐含赔率。面向复盘学习与线下自用;
在线上真钱牌局中实时使用求解器辅助违反几乎所有平台的规则。
