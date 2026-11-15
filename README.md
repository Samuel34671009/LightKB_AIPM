# LightKB · 轻量企业知识库

> 把“能答”的 RAG，做成“敢用”的产品。  
> An AI Product Manager case study: turning an enterprise RAG demo into a sellable SMB product.

<p align="center">
  <img src="assets/cover.png" alt="LightKB cover" width="100%">
</p>

![status](https://img.shields.io/badge/status-AI%20PM%20case%20study-B88A2E)
![docs](https://img.shields.io/badge/docs-35--page%20report-1F6F78)
![license](https://img.shields.io/badge/license-MIT%20%2B%20CC%20BY--NC%204.0-121C33)

> **课程项目模拟声明**：本项目是“腾讯未来产品经理创造营”结课项目模拟，不是腾讯公司真实立项、商业计划或招聘评价。客户访谈、Pilot 数据、定价与财务测算为模拟推演，用于展示产品方法；真实项目素材与链接见报告附录 G。证书编号仅用于说明课程依据。

---

## 这是什么

这是一个**完整的 AI 产品经理作品集项目**，不是一份课程总结。

它把我真实做过的“企业级混合检索知识库”项目，降维成一个更小、更苛刻的市场：**10—30 席电商售后团队**。然后按《The AI Product Manager’s Handbook》的方法，完整走了一遍 12 周产品化流程：

- **发现**：12 次访谈、2 个客服班次观察、6 家竞品拆解、3 份数据审计；
- **定义**：价值 / 范围 / 触达评分，12 个候选只留 6 个进 MVP；
- **设计**：混合检索 + Rerank + 引用溯源 + 置信度 + 兜底转人工；
- **验证**：120 题 Golden Set、离线消融、线上 A/B、3 家 Pilot；
- **交付**：Shadow → Canary → GA、监控阈值、Bad Case 闭环、30 分钟接入；
- **商业**：¥99/席/月、单位经济、客户 ROI、12 个月 30 家模型；
- **答辩**：8 分钟脚本、15 个追问、能力证据矩阵。

**一句话**：LightKB 不是让 AI 更会聊天，是让一线在 60 秒内拿到一个敢直接发给客户的答案。

---

## 30 秒看懂

| 维度 | 内容 |
|---|---|
| **问题** | 客服平均首次响应 4.2 分钟，其中约 2.6 分钟在“找”和“确认”；38% 的会话最终转人工 |
| **洞察** | 客户不缺聊天机器人，缺的是“有出处、可兜底、能审计”的答案系统 |
| **方案** | 10 分钟接入、混合检索 + Rerank、每个答案带引用、没依据就转人工、按坐席付费 |
| **证据** | 3 家 Pilot / 95 席 / 4 周：Hit@1 78.4%、引用 96.1%、幻觉 1.4%、首响 -45%、转人工 -9pp |
| **商业** | ¥99/席/月，单次成本 ¥0.19、毛利 68%、CAC ¥6,200、回本 3.4 个月、客户 ROI 5.3 倍 |
| **判断** | Go with conditions：只做电商售后 10—30 席；12 个月 30 家 / 900 席 / ARR 约 ¥99 万 |

---

## 关键结果

| 指标 | 结果 | 口径 |
|---|---:|---|
| Hit@1 | **78.4%** | 检索第一名包含金标答案；120 题 Golden Set |
| Recall@5 | **94.0%** | 前 5 条包含金标答案；较纯向量基线 +40.3% 相对提升 |
| 引用准确率 | **96.1%** | 引用能支撑结论的比例 |
| 幻觉率 | **1.4%** | 无引用支撑的断言 / 全部回答 |
| 首次响应 | **-45%** | 4.2 分钟 → 2.3 分钟 |
| 转人工率 | **-9pp** | 38% → 29% |
| 单次成本 | **¥0.19** | 模型 + 检索 + 支持 + 接入摊销 |
| 毛利率 | **68.0%** | 单次收入 ¥0.59，含支持与接入 |
| 客户 ROI | **5.3×** | 30 席、省 8% 时间、净收益 ÷ 产品月费 |
| 付费意向 | **2 / 3** | 1 家缺数据 owner，退出 Pilot |

<p align="center">
  <img src="assets/pilot.png" alt="Pilot results" width="100%">
</p>

---

## 产品是什么

LightKB 是客服的“答案副驾驶”，不是通用聊天机器人：

- **接入**：PDF / Word / HTML / Excel / FAQ；500 篇 ≤30 分钟；文档级 ACL；
- **检索**：BM25 + 向量 + RRF + Rerank，Top-50 → Top-5；
- **生成**：Qwen-Plus + 引用约束 + 置信度分级 + 没依据转人工；
- **界面**：坐席工作台、知识管理后台、主管看板；
- **边界**：AI 不自动回复客户；坐席确认后才发送。

<p align="center">
  <img src="assets/solution.png" alt="Solution" width="100%">
</p>

### 信任设计

每个答案卡都包含：结论、步骤、引用、置信度、反馈、转人工。没有可靠依据时，明确说“没有找到可靠依据”，而不是猜一个。

> 我们不说“我不知道”，说“没有找到可靠依据”。前者让坐席觉得 AI 无能，后者让坐席知道这是系统的边界。

---

## 证据链

<p align="center">
  <img src="assets/evidence.png" alt="Evidence" width="100%">
</p>

- 120 题 Golden Set：4 类意图 × 3 个难度 × 10 题；30% 故意不可回答；
- 双人标注，Cohen’s kappa = 0.81；
- 离线四组对比：关键词 FAQ → 纯向量 → 混合检索 → 混合 + Rerank；
- 线上 A/B：每组 2,430 会话，有效解决会话率 +5.7pp（p=0.03）；
- Bad Case 五类归因：检索未召回 / 分块切断 / 权限时效 / 生成越界 / 问题歧义。

---

## 商业模型

<p align="center">
  <img src="assets/business.png" alt="Business" width="100%">
</p>

| 套餐 | 坐席 | 价格 | 包含 |
|---|---|---:|---|
| Starter | 10—29 | ¥99/席/月 | 500 篇文档；1,500 次问答/月 |
| Team | 30—99 | ¥89/席/月 | 2,000 篇文档；4,500 次问答/月 |
| Enterprise | 100+ | ¥79/席/月 | 10,000 篇文档；SSO/审计 |

- 单次成本 ¥0.19，收入 ¥0.59，毛利 ¥0.40；
- CAC ¥6,200，月毛利 ¥1,815，回本 3.4 个月；
- 30 席客户：月省 ¥1.68 万，产品月费 ¥2,670，净 ROI 5.3 倍；
- 底线：单次成本 ≤¥0.25；低于 65% 毛利先查支持成本和模型路由，不要先涨价。

---

## 仓库结构

```text
lightkb-ai-pm-case/
├── README.md
├── LICENSE                         # MIT（代码）
├── CONTENT-LICENSE.md              # CC BY-NC 4.0（报告/Deck 内容）
├── NOTICE.md                       # 商标、模拟数据、隐私说明
├── CITATION.cff
├── .gitattributes
├── .gitignore
├── .nojekyll                       # GitHub Pages
├── index.html                      # 根路径跳转到 prototype/
├── docs/
│   ├── README.md
│   ├── LightKB_Project_Report.pdf  # 35 页主报告
│   ├── LightKB_Project_Report.docx
│   ├── LightKB_Defense_Deck.pdf    # 12 页答辩 Deck
│   ├── LightKB_Defense_Deck.pptx
│   └── LightKB_Unit_Economics.xlsx # 7 个 sheet 的测算表
├── assets/                         # README 截图
├── product/
│   ├── README.md
│   ├── PRD.md                      # 6 个用户故事 + 验收标准
│   ├── metrics.md                  # 北极星 / KPI 树 / 护栏
│   ├── experiment.md               # 离线 + 线上 A/B 设计
│   ├── pricing.md                  # 定价、单位经济、ROI
│   └── roadmap.md                  # 12 周与 12 个月路线
├── research/
│   ├── README.md
│   ├── interview_guide.md          # 10 个访谈问题
│   ├── personas.md                 # 3 个人物
│   └── competitive_landscape.md    # 竞品与空位
├── data/
│   ├── README.md
│   ├── golden_set_template.csv     # 20 题 starter template
│   └── pilot_summary.csv           # 3 家 Pilot 汇总
├── analysis/
│   ├── README.md
│   ├── unit_economics.py           # 单位经济可复算
│   └── evaluate.py                 # Pilot 指标可复算
├── prototype/                      # 无依赖静态原型
│   ├── README.md
│   ├── index.html
│   ├── styles.css
│   ├── app.js
│   └── data.js
└── .github/workflows/validate.yml  # CI：语法检查 + 指标复算
```

---

## 快速开始

### 1. 读报告 / 看 Deck

- [35 页主报告](docs/LightKB_Project_Report.pdf)
- [12 页答辩 Deck](docs/LightKB_Defense_Deck.pdf)
- [7-sheet 测算表](docs/LightKB_Unit_Economics.xlsx)

### 2. 打开交互原型

```bash
# 在仓库根目录
python -m http.server 8000

# 浏览器打开
# http://localhost:8000/prototype/
```

原型是纯 HTML/CSS/JS，无依赖、无后端。输入问题或点击示例，查看答案卡、引用、置信度、兜底和“转人工”。

### 3. 复算指标

```bash
python analysis/unit_economics.py
python analysis/evaluate.py
```

两个脚本只用 Python 标准库，输出 Markdown 表格；`analysis/output/` 会保存结果。

### 4. 本地校验

```bash
python -m compileall analysis
python analysis/evaluate.py
```

GitHub Actions 也会在 push / PR 时跑同样的检查。

---

## 上传到 GitHub

### 方式 A：网页上传

1. 新建仓库，例如 `lightkb-ai-pm-case`；
2. 把本目录下的所有文件和文件夹一起拖进去（保留 `docs/`、`assets/`、`prototype/` 等目录结构）；
3. 提交后，在 **Settings → Pages** 选择 **Deploy from a branch → main / root**；
4. 打开 `https://<your-name>.github.io/lightkb-ai-pm-case/prototype/`。

### 方式 B：命令行

```bash
git init
git add .
git commit -m "feat: LightKB AI PM case study"
git branch -M main
git remote add origin https://github.com/<your-name>/lightkb-ai-pm-case.git
git push -u origin main
```

> 把 `<your-name>` 和仓库名替换成你自己的。若改名，记得同步更新 `README.md`、`CITATION.cff` 和 `CONTENT-LICENSE.md` 里的示例 URL。

---

## 这份项目展示了什么

| AI PM 能力 | 证据 | 文件 |
|---|---|---|
| 用户研究 | 12 次访谈、2 个班次观察、3 份数据审计 | `research/`、报告 02 |
| 机会识别 | 机会树、3 个下注、TAM/SAM/SOM、竞争空位 | 报告 02 |
| MVP 定义 | 12 个候选 → 6 个 Must；6 个用户故事 | `product/PRD.md` |
| 技术判断 | 混合检索、Rerank、引用、兜底的取舍 | 报告 05 |
| 数据与评测 | 120 题 Golden Set、离线/在线实验、Bad Case | `data/`、`analysis/` |
| 交付管理 | 12 周计划、RACI、Shadow/Canary/GA | `product/roadmap.md` |
| 商业化 | 定价、单位经济、ROI、12 个月模型 | `product/pricing.md` |
| 风险/合规 | ACL、PIPL、审计、红队 | `NOTICE.md`、报告 06/08 |
| 沟通/答辩 | 35 页报告、12 页 Deck、15 个追问 | `docs/` |

---

## 真实 vs 模拟

| 模块 | 内容 | 性质 |
|---|---|---|
| 技术链路 | ES + 向量 + Rerank、引用溯源、LangFuse/OpenEval、百万级文档 | 真实项目已验证 |
| 评测方法 | Golden Dataset、Hit Rate / MRR、离线 + 在线双轨 | 真实项目使用过 |
| 客户访谈 | 12 位客服/主管/知识管理员 | 模拟编写，按真实场景合理化 |
| Pilot 数据 | 3 家、95 席、4,860 次会话、78.4% Hit@1 | 模拟推演，用于验证方法 |
| 定价与财务 | ¥99/席/月、单次成本 ¥0.19、CAC ¥6,200 | 模拟测算，假设已列明 |
| 腾讯课程场景 | 创造营结课课题、评审标准、答辩形式 | 按课程要求模拟，非腾讯真实立项 |

真实项目链接见报告附录 G，或 GitHub：[@Samuel34671009](https://github.com/Samuel34671009)。

---

## 路线图

| 季度 | 客户 | 坐席 | ARR | 关键动作 |
|---|---:|---:|---:|---|
| Q1 | 3 | 95 | ¥10.5 万 | 2 家转正，1 家退出 |
| Q2 | 10 | 300 | ¥33.1 万 | 渠道开始贡献 |
| Q3 | 20 | 600 | ¥66.2 万 | 第二行业模板 |
| Q4 | 30 | 900 | ¥99.4 万 | 服务商复制 |

假设：平均 30 席/家、¥92/席/月、月流失 2%、价格不变。

---

## License

- **代码**（`analysis/`、`prototype/`、`.github/`）：[MIT](LICENSE)
- **报告 / Deck / 文档内容**：[CC BY-NC 4.0](CONTENT-LICENSE.md)
- 腾讯、腾讯招聘、腾讯学堂等名称与标识归腾讯公司所有；本项目与腾讯无隶属关系。
- 报告包含作者姓名与证书编号；如公开仓库，建议根据个人隐私偏好做脱敏。

---

## 联系

- GitHub：[@Samuel34671009](https://github.com/Samuel34671009)
- 项目定位：AI 产品经理 / AI 应用工程师作品集
- 如果这个项目对你有帮助，欢迎 Star；有具体问题可以开 Issue。
