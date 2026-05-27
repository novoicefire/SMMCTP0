# Nanya Framework Rerouting Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rework `index.html` so the former centralized `#deep-analysis` content is integrated into the relevant market, finance, portfolio, resources, growth, career, and integrity sections.

**Architecture:** Keep the project as a single-file static site. Preserve the existing visual system, i18n object, render functions, dark/light theme, voice guide, flip cards, quiz, and responsive behavior while moving data and DOM targets into the main narrative flow.

**Tech Stack:** Static HTML, CSS, and vanilla JavaScript in `index.html`; verification through browser/file URL smoke tests and text searches.

---

## Current File Map

- Modify: `index.html`
  - Navigation: desktop links around current `index.html:2228-2238`; mobile links around `index.html:2290-2299`.
  - Main sections: current `#team` starts near `index.html:2361`; `#company` near `index.html:2442`; `#finance` near `index.html:2538`; `#market` near `index.html:2633`; `#resources` near `index.html:2677`; flip cards near `index.html:2737`; `#portfolio` near `index.html:2750`; `#growth` near `index.html:2771`; `#career` near `index.html:2800`; `#deep-analysis` near `index.html:2847`; `#quiz` near `index.html:2896`; `#integrity` near `index.html:2924`.
  - i18n: `translations.zh` starts near `index.html:2986`; `translations.en` starts near `index.html:3203`.
  - Data: `interactiveData` starts near `index.html:3455`; `deepAnalysisData` starts near `index.html:3574`; `quizData` starts near `index.html:3803`.
  - Render flow: `applyLanguage()` near `index.html:3840`; `renderFinanceExplorer()` near `index.html:3926`; `renderMarketLab()` near `index.html:3952`; `renderPortfolioTool()` near `index.html:3980`; `renderConfidenceTools()` near `index.html:4009`; `renderValueNetMap()` near `index.html:4023`; `renderDeepAnalysis()` near `index.html:4051`.
- Reference only: `發現問題.md`
  - Use as the source of required narrative order and acceptance criteria.
- Reference only: `docs/南亞科技原始資料蒐集.md`
  - Use only if a moved claim needs source-confidence wording checked.

## Target Reading Order

Implement this order in `<main>` and navigation:

1. Hero
2. `#company`
3. `#market`
4. `#finance`
5. `#portfolio`
6. `#resources`
7. `#growth`
8. `#career`
9. Flip cards
10. `#quiz`
11. `#integrity`
12. `#team`

Keep the values block with company content unless it visually interrupts the flow; if retained, place it immediately after `#company` and before `#market`.

---

## Task 1: Navigation and Section Order

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Reorder desktop navigation links**

Replace the desktop `.nav-links` order with:

```html
<a href="#company" data-i18n="navCompany">公司概覽</a>
<a href="#market" data-i18n="navMarket">市場分析</a>
<a href="#finance" data-i18n="navFinance">財務績效</a>
<a href="#portfolio" data-i18n="navPortfolio">產品配置</a>
<a href="#resources" data-i18n="navResources">資源評價</a>
<a href="#growth" data-i18n="navGrowth">成長策略</a>
<a href="#career" data-i18n="navCareer">組織人才</a>
<a href="#quiz" data-i18n="navQuiz">小測驗</a>
<a href="#integrity" data-i18n="navIntegrity">資料揭露</a>
<a href="#team" data-i18n="navTeam">小組協作</a>
```

Remove `href="#deep-analysis"` and `data-i18n="navDeep"` from desktop navigation.

- [ ] **Step 2: Reorder mobile navigation links**

Apply the same link order in `#mobilePanel`, again with no `#deep-analysis` link.

- [ ] **Step 3: Reorder main sections**

Move the existing `#team` section from its current position before `#company` to after `#integrity`. Move the flip-card section from before `#portfolio` to after `#career`.

Expected `<main>` section sequence after the hero:

```text
#company
values block
#market
#finance
#portfolio
#resources
#growth
#career
flip cards
#quiz
#integrity
#team
```

- [ ] **Step 4: Run structural search**

Run:

```powershell
rg -n '<section|#deep-analysis|navDeep|href="#deep-analysis"' index.html
```

Expected:

```text
No matches for #deep-analysis, navDeep, or href="#deep-analysis".
Section lines appear in the target order.
```

- [ ] **Step 5: Commit**

```powershell
git add index.html
git commit -m "refactor: reorder Nanya strategy site flow"
```

---

## Task 2: Market Section Receives Porter Five Forces and PESTEL

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update market title and lead translations**

Set:

```js
marketTitle: "寡占競爭、政策限制與 AI 需求共同決定南亞科的市場空間。",
marketLead: "市場分析先看三大廠寡占與五力壓力，再用 PESTEL 檢查政策、景氣、技術與環境法規訊號。",
```

English:

```js
marketTitle: "Oligopoly, policy limits, and AI demand jointly define Nanya's market space.",
marketLead: "The market section starts with top-three concentration and Five Forces pressure, then uses PESTEL signals to read policy, cycle, technology, and environmental/legal risk.",
```

- [ ] **Step 2: Expand `interactiveData.zh.forces` and `interactiveData.en.forces`**

Keep the existing five IDs: `rivalry`, `supplier`, `buyer`, `substitute`, `entrant`. Expand each detail string with the four-point Porter content:

```js
["rivalry", "同業競爭", "三大廠合計市占超過 94%，南亞科約 0.81%，更像價格接受者；策略重點不應是全面價格戰，而是可被長約鎖定的 DDR5、LPDDR5/5X、KGD 與客製 AI memory。"]
```

Use equivalent English strings in `interactiveData.en.forces`.

- [ ] **Step 3: Add PESTEL DOM below `.market-lab`**

Insert after the market lab:

```html
<div class="signal-grid" id="pestelSignals" aria-label="PESTEL external environment signals"></div>
```

- [ ] **Step 4: Add PESTEL data**

Add `pestel` under both `interactiveData.zh` and `interactiveData.en`:

```js
pestel: [
  { label: "Political", title: "出口管制與台灣供應位置", body: "美國對中國外資晶圓廠升級限制提高台灣本地 DRAM 供應的相對價值。" },
  { label: "Economic", title: "DRAM 景氣循環與 EPS 波動", body: "EPS 從 2021 高點、2023 虧損到 2025 轉盈，顯示短週期會直接穿透損益表。" },
  { label: "Technological", title: "1B、1C / 1D、EUV、HBM 與 AI server", body: "製程推進與 AI server 需求讓傳統 DRAM、HBM 與高容量 DDR5 路線同時競爭資本。" },
  { label: "Environmental / Legal", title: "水資源、CDP、法規與補貼不確定性", body: "水資源再利用與 CDP 表現可作為供應鏈信任訊號；未確認補貼不得寫成已取得。" }
]
```

- [ ] **Step 5: Extend `renderMarketLab()`**

After rendering force detail, add:

```js
const pestel = qs("#pestelSignals");
if (pestel) {
  pestel.innerHTML = data.pestel.map((item) => `
    <article class="signal-card">
      <span>${escapeHtml(item.label)}</span>
      <h3>${escapeHtml(item.title)}</h3>
      <p>${escapeHtml(item.body)}</p>
    </article>
  `).join("");
}
```

- [ ] **Step 6: Add CSS for PESTEL cards**

Add responsive styles near existing `.market-lab` styles:

```css
.signal-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 14px;
  margin-top: 18px;
}

.signal-card {
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 18px;
  background: var(--surface);
}

.signal-card span {
  display: block;
  margin-bottom: 10px;
  font-size: .78rem;
  font-weight: 800;
  color: var(--accent);
}

@media (max-width: 900px) {
  .signal-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .signal-grid {
    grid-template-columns: 1fr;
  }
}
```

- [ ] **Step 7: Verify market behavior**

Run:

```powershell
rg -n 'pestelSignals|signal-grid|Porter 五力|PESTEL|renderMarketLab' index.html
```

Expected:

```text
pestelSignals exists once in HTML.
signal-grid CSS exists.
renderMarketLab renders data.pestel.
No standalone Porter or PESTEL card remains in #deep-analysis.
```

- [ ] **Step 8: Commit**

```powershell
git add index.html
git commit -m "feat: integrate market frameworks into market section"
```

---

## Task 3: Finance Section Receives DuPont, FCF, and CAPM

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update finance title and lead translations**

Set:

```js
financeTitle: "景氣反彈帶動轉盈，但現金流與資本支出仍決定復甦品質。",
financeLead: "財務績效要同時讀營收、EPS、自由現金流、ROE 拆解與系統風險，避免只用單一 EPS 判斷景氣復甦。",
```

English:

```js
financeTitle: "The cycle rebound restored profit, but cash flow and capex still decide recovery quality.",
financeLead: "Financial performance should combine revenue, EPS, free cash flow, ROE decomposition, and systematic risk instead of reading EPS alone.",
```

- [ ] **Step 2: Add CAPM/Beta as a finance tab**

Add a fifth entry to `interactiveData.zh.finance`:

```js
{
  id: "beta",
  label: "Beta",
  title: "Beta 說明南亞科股票風險與景氣敏感度。",
  body: "原始資料找到 2408.TW 5Y monthly Beta 1.69、Micron 1.92，可用 CAPM 說明 DRAM 股票需要承擔較高系統風險溢酬；這不等於公司經營失敗，而是產業循環放大市場波動。",
  cells: [["2408.TW Beta", "1.69"], ["Micron Beta", "1.92"], ["方法", "CAPM"], ["判讀", "高景氣敏感度"]]
}
```

Add equivalent English data.

- [ ] **Step 3: Strengthen existing `fcf` and `dupont` finance bodies**

Ensure `fcf.body` includes the 2020-2025 FCF sequence, and `dupont.body` explicitly states that net margin is the main ROE swing factor.

- [ ] **Step 4: Keep `renderFinanceExplorer()` unchanged unless cells overflow**

The existing render function already displays all `active.cells` and the full `active.body`. Do not introduce `slice(0, 2)` here.

- [ ] **Step 5: Verify finance coverage**

Run:

```powershell
rg -n 'id: "beta"|CAPM|Beta|DuPont|FCF|slice\\(0, 2\\)' index.html
```

Expected:

```text
Finance contains beta/CAPM.
No active finance rendering uses slice(0, 2).
```

- [ ] **Step 6: Commit**

```powershell
git add index.html
git commit -m "feat: expand finance explorer with CAPM risk"
```

---

## Task 4: Portfolio Section Receives BCG, GE, Ansoff, STP, and 4P

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update portfolio title and lead translations**

Set:

```js
portfolioTitle: "產品升級與客戶定位，決定南亞科如何避開規模競爭。",
portfolioLead: "產品象限不只標示成長性，也用資本優先順序、目標客戶與資料信心說明南亞科如何聚焦 B2B 利基。",
```

English:

```js
portfolioTitle: "Product upgrades and customer positioning decide how Nanya avoids scale competition.",
portfolioLead: "The portfolio map reads growth, capital priority, target customers, and confidence status to explain Nanya's B2B focus.",
```

- [ ] **Step 2: Expand each product object**

Replace each `interactiveData.zh.portfolio` object with fields:

```js
{
  id: "ddr5",
  label: "DDR5",
  x: 72,
  y: 74,
  status: "confirmed",
  title: "DDR5 / Star",
  role: "成長主力",
  growth: "伺服器、AI server 與高容量需求帶動升級。",
  priority: "優先投資良率、製程與客戶驗證。",
  customer: "伺服器、資料中心與需要高容量 DRAM 的 B2B 客戶。",
  body: "DDR5 是短中期最需要資本與良率支援的產品線。"
}
```

Apply the same structure to `DDR4`, `LPDDR5`, and `KGD` in Chinese and English.

- [ ] **Step 3: Update `renderPortfolioTool()` detail panel**

Replace the current `detail.innerHTML` with:

```js
detail.innerHTML = `
  <span class="status-chip">${escapeHtml(statusLabel(active.status))}</span>
  <h3>${escapeHtml(active.title)}</h3>
  <p>${escapeHtml(active.body)}</p>
  <dl class="detail-list">
    <dt>${currentLang === "zh" ? "產品角色" : "Product role"}</dt>
    <dd>${escapeHtml(active.role)}</dd>
    <dt>${currentLang === "zh" ? "成長性" : "Growth"}</dt>
    <dd>${escapeHtml(active.growth)}</dd>
    <dt>${currentLang === "zh" ? "資本優先順序" : "Capital priority"}</dt>
    <dd>${escapeHtml(active.priority)}</dd>
    <dt>${currentLang === "zh" ? "主要客戶／應用市場" : "Main customers / applications"}</dt>
    <dd>${escapeHtml(active.customer)}</dd>
  </dl>
`;
```

- [ ] **Step 4: Add B2B positioning module after `.portfolio-tool`**

Insert:

```html
<div class="positioning-panel" id="positioningPanel" aria-label="B2B positioning summary"></div>
```

- [ ] **Step 5: Add positioning data and renderer**

Add `positioning` under both languages:

```js
positioning: [
  "南亞科規模小於三大廠，不適合以全面低成本競爭作為主軸。",
  "目標客戶應聚焦 AI server、策略 NAND 夥伴、需要第二供應來源的國際客戶。",
  "定位應強調台灣製造、長期供應、技術支援與策略合作。"
]
```

At the end of `renderPortfolioTool()`, render:

```js
const positioning = qs("#positioningPanel");
if (positioning) {
  positioning.innerHTML = interactiveData[currentLang].positioning.map((item) => `
    <article class="positioning-item"><p>${escapeHtml(item)}</p></article>
  `).join("");
}
```

- [ ] **Step 6: Verify portfolio coverage**

Run:

```powershell
rg -n 'positioningPanel|detail-list|產品角色|Capital priority|STP|4P|BCG|Ansoff' index.html
```

Expected:

```text
Portfolio detail contains role, growth, priority, customer/application, and status.
Positioning panel exists.
No standalone BCG/STP theory card remains in a deep-analysis grid.
```

- [ ] **Step 7: Commit**

```powershell
git add index.html
git commit -m "feat: integrate portfolio and B2B positioning analysis"
```

---

## Task 5: Resources Section Receives Value Chain

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update resources title and lead translations**

Set:

```js
resourcesTitle: "製程、研發與客戶服務共同形成可累積的競爭能力。",
resourcesLead: "VRIN 判斷哪些資源重要，價值鏈說明這些資源如何轉化為客戶價值與策略優勢。",
```

English:

```js
resourcesTitle: "Process, R&D, and customer service jointly form accumulative competitive capability.",
resourcesLead: "VRIN identifies important resources, while the value chain explains how they become customer value and strategic advantage.",
```

- [ ] **Step 2: Add value-chain DOM after the VRIN table**

Insert after the current VRIN table card:

```html
<div class="capability-flow" id="capabilityFlow" aria-label="Value chain capability flow"></div>
```

- [ ] **Step 3: Add data under `interactiveData`**

Add `capabilities` under both languages:

```js
capabilities: [
  { title: "製程與研發", body: "1B、DDR5 與下一代製程決定產品升級速度。", status: "confirmed" },
  { title: "製造與智慧管理", body: "AI 應用、良率改善與效率管理讓製造資料轉化為營運能力。", status: "confirmed" },
  { title: "客戶驗證", body: "產品認證與長約建立把技術能力轉成穩定需求。", status: "confirmed" },
  { title: "FAE 技術服務", body: "FAE 支援形成客戶信任、問題解決與續約能力。", status: "inference" }
]
```

- [ ] **Step 4: Add `renderCapabilityFlow()`**

Add after `renderPortfolioTool()`:

```js
function renderCapabilityFlow() {
  const flow = qs("#capabilityFlow");
  if (!flow) return;
  flow.innerHTML = interactiveData[currentLang].capabilities.map((item) => `
    <article class="capability-step">
      <span class="status-chip">${escapeHtml(statusLabel(item.status))}</span>
      <h3>${escapeHtml(item.title)}</h3>
      <p>${escapeHtml(item.body)}</p>
    </article>
  `).join("");
}
```

Call `renderCapabilityFlow()` inside `applyLanguage()`.

- [ ] **Step 5: Add CSS**

```css
.capability-flow {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 14px;
  margin-top: 18px;
}

.capability-step {
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 18px;
  background: var(--surface);
}

@media (max-width: 900px) {
  .capability-flow {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .capability-flow {
    grid-template-columns: 1fr;
  }
}
```

- [ ] **Step 6: Verify resources coverage**

Run:

```powershell
rg -n 'capabilityFlow|renderCapabilityFlow|價值鏈|Value Chain|FAE 技術服務' index.html
```

Expected:

```text
Capability flow exists and is rendered from i18n-aware data.
Source confidence chips appear where relationships are inferential.
```

- [ ] **Step 7: Commit**

```powershell
git add index.html
git commit -m "feat: add value chain capability flow"
```

---

## Task 6: Growth Section Receives Value Net

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update growth title and lead translations**

Set:

```js
growthTitle: "產品升級需要客戶合作與供應鏈網絡共同支撐。",
growthLead: "三階段成長策略需要透過策略投資者、客戶、供應商與競爭者構成的 Value Net 落地。",
```

English:

```js
growthTitle: "Product upgrades need customer cooperation and supply-chain networks.",
growthLead: "The three-stage growth strategy depends on a Value Net of strategic investors, customers, suppliers, and competitors.",
```

- [ ] **Step 2: Move Value Net HTML into `#growth`**

After `.strategy-steps`, insert:

```html
<div class="chart-card analysis-table-card">
  <h3 data-i18n="valueNetMapTitle">Value Net 互動節點圖</h3>
  <div class="value-net-map" id="valueNetMap" aria-label="Value Net relationship nodes"></div>
  <div class="value-detail" id="valueNetDetail" aria-live="polite"></div>
</div>
<div class="chart-card analysis-table-card">
  <h3 data-i18n="valueNetTitle">Value Net 生態系彙整</h3>
  <table class="analysis-table" id="valueNetTable"></table>
</div>
```

- [ ] **Step 3: Keep Value Net data, but move ownership out of `deepAnalysisData`**

Create a new top-level object:

```js
const valueNetData = {
  zh: {
    headers: ["公司", "象限", "關係", "核心連結", "依賴程度", "資料狀態"],
    rows: [
      ["ASML", "上游供應商", "供應", "EUV/DUV 設備影響 10 奈米級製程時程", "高", "推論；EUV 裝機未確認"],
      ["SanDisk", "客戶 + 互補者", "聯盟 + 供應", "AI SSD 需求需要長期 DRAM 供應", "中", "已確認"],
      ["Kioxia", "客戶 + 互補者", "聯盟 + 供應", "NAND 夥伴需要穩定 DRAM 供應", "中", "已確認"],
      ["Solidigm Inc.", "客戶 + 互補者", "聯盟", "SK hynix 旗下獨立子公司；DRAM + NAND 互補", "中", "私募已確認；供應細節待核實"],
      ["Cisco", "客戶 + 互補者", "聯盟", "網通與 AI 基礎設施需要分散 DRAM 供應", "中", "私募已確認"],
      ["CXMT", "水平競爭者", "競爭", "成熟製程與區域市場形成價格壓力", "低", "公開報導已確認"],
      ["TSMC", "技術合作假設", "技術合作", "Vera Rubin / LPDDR5X 主張缺乏可靠來源", "未知", "待核實"]
    ]
  },
  en: {
    headers: ["Company", "Quadrant", "Relationship", "Core link", "Dependence", "Status"],
    rows: [
      ["ASML", "Upstream supplier", "Supply", "EUV/DUV tools affect 10nm-class process timing", "High", "Inference; EUV install not confirmed"],
      ["SanDisk", "Customer + complementor", "Alliance + supply", "Long-term DRAM supply for AI SSD demand", "Medium", "Confirmed"],
      ["Kioxia", "Customer + complementor", "Alliance + supply", "NAND partner needs stable DRAM supply", "Medium", "Confirmed"],
      ["Solidigm Inc.", "Customer + complementor", "Alliance", "Standalone SK hynix subsidiary; DRAM + NAND complement", "Medium", "Placement confirmed; supply details pending"],
      ["Cisco", "Customer + complementor", "Alliance", "Diverse DRAM supply for networking and AI infrastructure", "Medium", "Private placement confirmed"],
      ["CXMT", "Horizontal competitor", "Competition", "Mature-node and regional markets create pricing pressure", "Low", "Confirmed public reporting"],
      ["TSMC", "Technology cooperation hypothesis", "Technology cooperation", "Vera Rubin / LPDDR5X claim lacks reliable source", "Unknown", "Unverified"]
    ]
  }
};
```

- [ ] **Step 4: Update `renderValueNetMap()`**

Make it read:

```js
const data = valueNetData[currentLang];
const rows = data.rows;
```

Change the dependency label from `data.valueNetHeaders[4]` to `data.headers[4]`.

- [ ] **Step 5: Add `renderGrowthNetwork()`**

```js
function renderGrowthNetwork() {
  renderTable(qs("#valueNetTable"), valueNetData[currentLang].headers, valueNetData[currentLang].rows);
  renderValueNetMap();
}
```

Call `renderGrowthNetwork()` in `applyLanguage()`.

- [ ] **Step 6: Verify Value Net behavior**

Run:

```powershell
rg -n 'valueNetData|renderGrowthNetwork|valueNetMap|valueNetTable|deepAnalysisData' index.html
```

Expected:

```text
valueNetMap and valueNetTable are inside #growth.
renderGrowthNetwork exists.
Value Net data no longer depends on deepAnalysisData.
```

- [ ] **Step 7: Commit**

```powershell
git add index.html
git commit -m "feat: move value net into growth strategy"
```

---

## Task 7: Career Section Receives Organization Design

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update career title and lead translations**

Set:

```js
careerTitle: "策略升級需要製程、軟體與客戶技術服務人才共同支撐。",
careerLead: "104 職缺資料不是孤立求職資訊，而是觀察南亞科從防守型角色走向分析型組織的證據。",
```

English:

```js
careerTitle: "Strategy upgrades need process, software, and customer-technical talent together.",
careerLead: "104 job postings are evidence of Nanya's shift from a defender role toward an analyzer organization, not isolated career information.",
```

- [ ] **Step 2: Add organization summary before `.career-grid`**

Insert:

```html
<div class="organization-summary" id="organizationSummary" aria-label="Organization capability summary"></div>
```

- [ ] **Step 3: Add organization data**

Add under `interactiveData`:

```js
organization: [
  "南亞科原本偏向專注製程、成本、良率與既有市場的防守型角色。",
  "AI memory、策略合作、新廠與智慧製造讓公司逐步走向同時探索新市場與維持既有能力的分析型角色。",
  "製程、軟體、FAE 與資料應用人才需要共同支援新廠、客戶認證與智慧製造系統。"
]
```

Add equivalent English text.

- [ ] **Step 4: Add `renderOrganizationSummary()`**

```js
function renderOrganizationSummary() {
  const summary = qs("#organizationSummary");
  if (!summary) return;
  summary.innerHTML = interactiveData[currentLang].organization.map((item) => `
    <article class="organization-item"><p>${escapeHtml(item)}</p></article>
  `).join("");
}
```

Call it from `applyLanguage()`.

- [ ] **Step 5: Add CSS**

```css
.organization-summary {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
  margin-bottom: 18px;
}

.organization-item {
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 18px;
  background: var(--surface);
}

@media (max-width: 760px) {
  .organization-summary {
    grid-template-columns: 1fr;
  }
}
```

- [ ] **Step 6: Verify career coverage**

Run:

```powershell
rg -n 'organizationSummary|renderOrganizationSummary|Defender|Analyzer|防守型|分析型|104' index.html
```

Expected:

```text
Career section contains organization-design narrative before job cards.
The three existing job cards remain.
```

- [ ] **Step 7: Commit**

```powershell
git add index.html
git commit -m "feat: connect career section to organization capability"
```

---

## Task 8: Integrity Section Receives Collapsible Framework Map

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Move theory map out of main analysis flow**

In `#integrity`, after `.integrity` and before the section closing container, add:

```html
<details class="framework-disclosure">
  <summary data-i18n="frameworkDisclosureTitle">本研究採用之分析工具</summary>
  <div class="chart-card analysis-table-card">
    <table class="analysis-table" id="theoryMapTable"></table>
  </div>
</details>
```

- [ ] **Step 2: Create top-level `theoryMapData`**

```js
const theoryMapData = {
  zh: {
    headers: ["框架", "提出者或理論來源", "分析用途", "對應章節"],
    rows: [
      ["Porter 五力 / PESTEL", "Porter (1980) / 常用總體環境分析", "判斷產業結構與外部制度環境", "市場分析"],
      ["DuPont / FCF / CAPM", "DuPont / Jensen (1986) / Sharpe (1964)", "拆解 ROE、自由現金流與系統風險", "財務績效"],
      ["BCG / GE / Ansoff / STP + 4P", "BCG (1970) / Ansoff (1957) / Kotler & Armstrong", "判斷產品配置、成長路徑與 B2B 定位", "產品配置與市場定位"],
      ["VRIN / Value Chain", "Barney / Porter (1985)", "判斷資源價值與能力轉化流程", "資源與能力"],
      ["Value Net", "Brandenburger & Nalebuff (1996)", "說明客戶、互補者、供應商與競爭者的競合網絡", "成長策略與供應鏈合作"],
      ["組織型態", "Miles & Snow (1978) / Chandler (1962)", "說明策略升級需要的組織能力與人才", "組織能力與人才需求"]
    ]
  },
  en: {
    headers: ["Framework", "Originator or source", "Analytical use", "Mapped section"],
    rows: [
      ["Porter Five Forces / PESTEL", "Porter (1980) / common macro-environment framework", "Reads industry structure and external institutions", "Market analysis"],
      ["DuPont / FCF / CAPM", "DuPont / Jensen (1986) / Sharpe (1964)", "Reads ROE, free cash flow, and systematic risk", "Financial performance"],
      ["BCG / GE / Ansoff / STP + 4P", "BCG (1970) / Ansoff (1957) / Kotler & Armstrong", "Reads product allocation, growth paths, and B2B positioning", "Product portfolio and market positioning"],
      ["VRIN / Value Chain", "Barney / Porter (1985)", "Reads resource value and capability conversion", "Resources and capabilities"],
      ["Value Net", "Brandenburger & Nalebuff (1996)", "Maps customers, complementors, suppliers, and competitors", "Growth strategy and supply-chain cooperation"],
      ["Organization type", "Miles & Snow (1978) / Chandler (1962)", "Explains organization capabilities and talent needs", "Organization capability and talent demand"]
    ]
  }
};
```

- [ ] **Step 3: Add `renderTheoryMap()`**

```js
function renderTheoryMap() {
  renderTable(qs("#theoryMapTable"), theoryMapData[currentLang].headers, theoryMapData[currentLang].rows);
}
```

Call it from `applyLanguage()`.

- [ ] **Step 4: Add CSS**

```css
.framework-disclosure {
  margin-top: 24px;
}

.framework-disclosure summary {
  cursor: pointer;
  font-weight: 800;
  color: var(--text);
}
```

- [ ] **Step 5: Verify integrity coverage**

Run:

```powershell
rg -n 'frameworkDisclosureTitle|theoryMapData|renderTheoryMap|Nanya application|南亞科應用' index.html
```

Expected:

```text
frameworkDisclosureTitle exists in zh/en translations.
theoryMapData uses "對應章節" / "Mapped section".
Old "Nanya application" wording is gone.
```

- [ ] **Step 6: Commit**

```powershell
git add index.html
git commit -m "feat: move framework map into integrity disclosure"
```

---

## Task 9: Remove Centralized Deep Analysis Code

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Delete the `#deep-analysis` HTML section**

Remove the entire section:

```html
<section class="section stone-band" id="deep-analysis" aria-labelledby="deep-analysis-title">
  ...
</section>
```

This removes `framework-router`, `confidenceTools`, `deepAnalysisGrid`, the old Value Net placement, and the old theory map placement.

- [ ] **Step 2: Delete `deepAnalysisData` after all useful content has been moved**

Remove `const deepAnalysisData = { ... };` only after Tasks 2-8 have moved the useful content into `interactiveData`, `valueNetData`, and `theoryMapData`.

- [ ] **Step 3: Delete centralized render state**

Remove:

```js
let confidenceFilter = "all";
```

Keep:

```js
let valueNetFocus = "SanDisk";
```

- [ ] **Step 4: Delete centralized render functions**

Remove:

```js
function renderConfidenceTools() { ... }
function renderDeepAnalysis() { ... }
```

Keep and update `renderValueNetMap()` because Growth now uses it.

- [ ] **Step 5: Update `applyLanguage()` render calls**

Replace:

```js
renderDeepAnalysis();
```

with:

```js
renderCapabilityFlow();
renderGrowthNetwork();
renderOrganizationSummary();
renderTheoryMap();
```

Ensure `renderMarketLab()`, `renderFinanceExplorer()`, and `renderPortfolioTool()` remain.

- [ ] **Step 6: Remove obsolete translations**

Remove unused i18n keys:

```text
navDeep
deepTitle
deepLead
framework1Label
framework1Title
framework1Body
framework2Label
framework2Title
framework2Body
framework3Label
framework3Title
framework3Body
framework4Label
framework4Title
framework4Body
```

Keep or add:

```text
valueNetMapTitle
valueNetTitle
frameworkDisclosureTitle
navCareer
navIntegrity
```

- [ ] **Step 7: Verify deletion**

Run:

```powershell
rg -n 'deep-analysis|deepAnalysisData|renderDeepAnalysis|renderConfidenceTools|confidenceFilter|deepAnalysisGrid|confidenceTools|framework-router|item.points.slice\\(0, 2\\)|navDeep' index.html
```

Expected:

```text
No matches.
```

- [ ] **Step 8: Commit**

```powershell
git add index.html
git commit -m "refactor: remove centralized deep analysis section"
```

---

## Task 10: CSS and Responsive QA Pass

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Audit new CSS selectors**

Run:

```powershell
rg -n 'signal-grid|signal-card|detail-list|positioning-panel|capability-flow|organization-summary|framework-disclosure|value-net-map|analysis-table-card' index.html
```

Expected:

```text
Each new HTML class has a matching CSS rule.
No unused old deep-analysis-only class is required by remaining DOM.
```

- [ ] **Step 2: Check dark-mode contrast locally**

Open:

```text
file:///C:/Users/ofire/Desktop/SMMCTP0/index.html
```

Manual checks:

```text
Toggle dark mode.
Inspect Market PESTEL cards, Portfolio detail, Resources capability flow, Growth Value Net, Career organization summary, Integrity framework disclosure.
All body text, borders, status chips, and table text remain readable.
```

- [ ] **Step 3: Check mobile layout**

Use a narrow browser viewport around `390x844`.

Manual checks:

```text
Mobile menu opens and contains no Deep Analysis link.
Signal cards stack.
Portfolio detail does not overflow.
Capability flow stacks.
Value Net nodes remain tappable and readable.
Tables either fit their scroll container or remain readable without page-wide overflow.
```

- [ ] **Step 4: Commit**

```powershell
git add index.html
git commit -m "style: tune responsive framework integration"
```

---

## Task 11: Functional Verification

**Files:**
- Verify: `index.html`

- [ ] **Step 1: Static acceptance searches**

Run:

```powershell
rg -n 'deep-analysis|十個分析框架改成分流地圖|navDeep|renderDeepAnalysis|renderConfidenceTools|confidenceFilter|item.points.slice\\(0, 2\\)' index.html
rg -n 'pestelSignals|id: "beta"|positioningPanel|capabilityFlow|valueNetMap|valueNetTable|organizationSummary|theoryMapTable' index.html
```

Expected:

```text
First command returns no matches.
Second command returns all new targets.
```

- [ ] **Step 2: Browser smoke path**

Open:

```text
file:///C:/Users/ofire/Desktop/SMMCTP0/index.html
```

Smoke path:

```text
1. Click each desktop nav item and confirm anchor jumps.
2. Open mobile menu and confirm anchor jumps.
3. Switch language to English and back to Chinese.
4. Toggle dark mode and return to light mode.
5. Click each Five Forces button.
6. Click each finance tab, including Beta.
7. Click each portfolio point.
8. Click each Value Net node.
9. Expand and collapse the framework disclosure under Integrity.
10. Flip one card.
11. Answer the first quiz question and confirm score changes to 1/5.
12. Start and stop voice guide.
```

- [ ] **Step 3: Console check**

Expected:

```text
No JavaScript errors when switching language after interacting with finance, portfolio, Value Net, and quiz.
```

- [ ] **Step 4: Final acceptance report**

Report:

```text
Changed section order:
Hero -> Company -> Market -> Finance -> Portfolio -> Resources -> Growth -> Career -> Flip cards -> Quiz -> Integrity -> Team.

Moved deep-analysis content:
Porter Five Forces and PESTEL -> Market.
DuPont, FCF, CAPM -> Finance.
BCG, GE, Ansoff, STP, 4P -> Portfolio.
Value Chain -> Resources.
Value Net -> Growth.
Organization design -> Career.
Theory map -> Integrity collapsible disclosure.

Removed or refactored JavaScript:
Removed renderDeepAnalysis, renderConfidenceTools, confidenceFilter, deepAnalysisData.
Refactored renderValueNetMap to read valueNetData.
Added renderCapabilityFlow, renderGrowthNetwork, renderOrganizationSummary, renderTheoryMap.

Data confidence still retained:
Value Net node statuses, product detail status chips, and capability-flow confidence chips remain visible.
TSMC/Vera Rubin relation remains unverified.
ASML/EUV installation remains inference or pending confirmation.
LPDDR5/5X market-share/customer details remain inference where public data is incomplete.
```

- [ ] **Step 5: Final commit**

```powershell
git status --short
git add index.html
git commit -m "feat: distribute strategy frameworks across Nanya site"
```

## Completion Gate

The implementation is complete only when:

- `#deep-analysis` and its old navigation link are gone.
- No `renderDeepAnalysis()`, `renderConfidenceTools()`, `confidenceFilter`, or `item.points.slice(0, 2)` remains.
- All moved framework content appears in the assigned section.
- Chinese and English modes show every new title, label, card, panel, table, button, and status chip.
- Desktop and mobile layouts have no horizontal page overflow.
- Dark and light themes preserve readable contrast.
- Quiz, flip cards, finance tabs, Five Forces, portfolio points, Value Net nodes, mobile menu, language switch, theme switch, and voice guide still work.
