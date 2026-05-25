# Nanya Finance Content Integration Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Integrate the teammate-provided Nanya Technology financial research into `index.html` while closing the competition-spec gaps around company history, organizational structure, financial strategy linkage, sources, and bilingual completeness.

**Architecture:** This repository is a static one-page site centered on `index.html`. Keep the final user-facing experience in `index.html`; treat `南亞科-財務.html`, `競賽說明.md`, `網站建置說明.md`, and `資料分析.md` as source/reference material, not separate navigation destinations. Preserve the existing visual system, bilingual `translations` object, static SVG/chart approach, local interaction scripts, and GitHub Pages compatibility.

**Tech Stack:** Single-file HTML/CSS/JavaScript, inline SVG, Web Speech API, localStorage, static GitHub Pages deployment.

---

## Source Materials

- `競賽說明.md`: competition requirements. The required content set is 小組成員介紹、公司介紹（歷史與組織架構-事業與功能層級單位等、財務資訊）、市場分析、資源評價、成長策略. The required interaction set is bilingual switching, dark/light mode, voice guide, quiz, flip cards, anchor navigation, RWD, and footer course/teacher information.
- `南亞科-財務.html`: teammate financial research. Use it for content ideas and cross-checking, but do not copy its Tailwind/Chart.js page structure into `index.html`.
- `index.html`: production page and only user-facing surface to update.
- `資料分析.md` and `網站建置說明.md`: context and original site spec/reference material.

## Current Assessment

### Already strong enough

- Team member introduction and collaboration statement exist in the `#team` section.
- Core financial section exists with 2021-2025 revenue, EPS direction, 2025 revenue, net income, and EPS.
- Market analysis exists as a SWOT section.
- Resource evaluation exists as a VRIN table.
- Growth strategy exists as short/mid/long-term strategy cards.
- Required interactions are already implemented: language switch, dark/light mode, voice guide, quiz, flip cards, anchor navigation, and RWD.
- Footer already includes course name and teacher name.
- GitHub Pages deployment already serves the current `index.html`.

### Main gaps to close

- Company introduction is missing an explicit history/timeline and organizational structure view.
- Financial analysis is present but too number-focused; it does not fully explain DRAM concentration, operating leverage, capital expenditure pressure, and the strategic meaning of the cycle.
- Market and growth strategy sections mention AI, DDR5, and supply chain partnerships, but they can be better grounded in the teammate financial research.
- AI/source disclosure is acceptable but should name financial reports as a source, make AI-tool use more concrete, and clarify visual/chart copyright or self-made status.
- A few fixed strings remain untranslated in English mode, especially footer/source/UI labels.
- Financial figures conflict between `南亞科-財務.html` and `index.html`; this must be resolved before importing any numbers.

## File Map

- Modify: `index.html`
  - Add company timeline/organization content near the existing `#company` section.
  - Expand financial interpretation inside `#finance`.
  - Strengthen market/growth/resource copy through the existing `translations` object.
  - Update source and AI disclosure.
  - Keep all visible content bilingual.
- Reference only: `南亞科-財務.html`
  - Extract DRAM concentration, regional market, operating leverage, capital expenditure, AI/HBM capacity crowding, Edge AI, DDR5 transition, China Plus One, and final watchpoints.
- Reference only: `競賽說明.md`
  - Confirm all required content and interactions remain covered.
- Optional temporary verification script: `scripts/verify-index-content.mjs`
  - Create only if manual browser verification is not enough. Delete it before final commit unless it is useful for future checks.

## Content Decisions

### Financial numbers need one final source of truth

`index.html` currently states:

- 2025 revenue: 665.87
- 2025 net income: 66.03
- 2025 EPS: 2.13
- Q4 2025 revenue: 300.94
- Q4 2025 EPS: 3.58

`南亞科-財務.html` chart data states:

- 114 revenue: 665.87
- 114 net income: 150.00
- 114 EPS: 4.80

These cannot be mixed. Before implementation, verify the correct annual consolidated values from Nanya Technology investor relations or the annual financial report. Once verified, update every place consistently:

- Hero/quick stats if affected.
- Finance chart labels/data.
- Finance metric cards.
- Quiz answer explanation.
- Footer update note if the data date changes.
- Chinese and English translations.

### Financial research content to integrate

Use these points from `南亞科-財務.html`:

- Nanya has gone through a DRAM cycle from high point to bottom to recovery to rebound.
- DRAM accounts for more than 99.8% of revenue, so earnings are highly exposed to DRAM pricing and supply-demand conditions.
- Semiconductor manufacturing has high fixed costs and operating leverage; revenue recovery can amplify gross margin and cash-flow improvement.
- During 111-113 downturn years, process migration and DDR5 investments still required capital spending.
- AI/HBM demand causes capacity crowding among large memory makers, supporting supply tightness in DDR4/mainstream DDR5.
- Edge AI, AI PCs, and AI smartphones increase memory content per device.
- DDR4 to DDR5 transition and 1A/1B nm progress are key to margin improvement.
- China Plus One and regional supply-chain restructuring strengthen the strategic value of Taiwan-based DRAM supply.
- Future watchpoints: 1B nm yield, DDR5 revenue mix, capital expenditure efficiency, and strategic customer binding.

### Content to avoid

- Do not import Tailwind CSS or Chart.js from `南亞科-財務.html`.
- Do not add a second standalone finance page unless explicitly requested later.
- Do not overfill the homepage with raw accounting details.
- Do not mention internal file names like `南亞科-財務.html` in visible site copy.
- Do not show uncertain financial numbers as confirmed.

---

## Task 1: Verify Financial Source of Truth

**Files:**
- Read: `南亞科-財務.html`
- Read: `index.html`
- Read: annual consolidated financial report / investor relations page used by the team
- Modify after verification: `index.html`

- [ ] **Step 1: Extract conflicting values from current files**

Run:

```powershell
rg -n "665.87|66.03|2.13|150.00|4.80|300.94|3.58|EPS|稅後淨利|營收" index.html '南亞科-財務.html'
```

Expected: command shows both the `index.html` values and the teammate finance-page values.

- [ ] **Step 2: Check the authoritative financial report**

Open the Nanya Technology investor-relations source used by the team and verify these final annual values:

```text
2021/110 revenue
2021/110 net income
2021/110 EPS
2022/111 revenue
2022/111 net income
2022/111 EPS
2023/112 revenue
2023/112 net income
2023/112 EPS
2024/113 revenue
2024/113 net income
2024/113 EPS
2025/114 revenue
2025/114 net income
2025/114 EPS
```

Expected: one consistent data table with source URL or source document name and retrieval date.

- [ ] **Step 3: Record the chosen final numbers before editing**

Add a local implementation note in the commit message or PR notes, not visible page copy:

```text
Financial source of truth:
- Source: [Nanya investor-relations or financial-report title]
- Retrieval date: 2026-05-25
- Final 2025 annual values: revenue [value], net income [value], EPS [value]
- Reason for resolving conflict: [finance report / company IR source takes priority]
```

Expected: future maintainers can explain why the chosen values replaced the conflicting values.

---

## Task 2: Add Company History and Organizational Structure

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Find the current company section**

Run:

```powershell
rg -n "id=\"company\"|companyTitle|companyRow|valuesTitle|Financial performance" index.html
```

Expected: output points to the `#company` section and the translation keys around `companyTitle`.

- [ ] **Step 2: Add a compact timeline block after the existing company rule list**

Add a new visual block under the existing company rows. Keep it concise and consistent with the current `rule-list` / `grid-3` style. Suggested Chinese visible content:

```text
公司沿革
1995 成立南亞科技，聚焦 DRAM 研發、設計、製造與銷售。
2000 於台灣證券交易所上市，擴大資本市場支持。
2010s 持續推進製程微縮與全球客戶支援，服務 PC、伺服器、車用與工業市場。
2020s 以 DDR5、LPDDR5、10 奈米級製程與新廠投資支撐下一階段成長。
```

Suggested English visible content:

```text
Company history
1995 Nanya Technology was founded with a focus on DRAM R&D, design, manufacturing, and sales.
2000 The company listed on the Taiwan Stock Exchange, expanding capital-market support.
2010s Nanya continued process migration and global customer support across PC, server, automotive, and industrial markets.
2020s DDR5, LPDDR5, 10nm-class processes, and new fab investment became the next growth base.
```

Expected: the page clearly satisfies the competition requirement for company history.

- [ ] **Step 3: Add an organizational structure block**

Add a compact structure view near the same company section. Suggested Chinese visible content:

```text
組織架構與層級
事業層級：以 DRAM 產品線為核心，連結標準型 DRAM、低功耗行動 DRAM、KGD、模組與 Elixir 品牌。
市場層級：服務智慧型手機、伺服器、資料中心、車用、工業與消費性電子客戶。
功能層級：研發與製程、製造與產能、銷售與客戶支援、財務與永續、人力資源共同支撐策略執行。
```

Suggested English visible content:

```text
Organization and levels
Business level: DRAM product lines connect standard DRAM, low-power mobile DRAM, KGD, modules, and the Elixir brand.
Market level: Nanya serves smartphone, server, data-center, automotive, industrial, and consumer-electronics customers.
Functional level: R&D/process, manufacturing/capacity, sales/customer support, finance/sustainability, and HR jointly support execution.
```

Expected: the company section explicitly covers organization, business-level units, and functional-level units.

- [ ] **Step 4: Add translation keys**

Add keys under both `translations.zh` and `translations.en`. Suggested key names:

```javascript
historyTitle
history1995
history2000
history2010s
history2020s
orgTitle
orgBusiness
orgMarket
orgFunctional
```

Expected: language switching updates the new company content.

---

## Task 3: Strengthen Financial Strategy Interpretation

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update the finance lead after source verification**

Use the verified numbers from Task 1. Suggested Chinese copy:

```text
南亞科財務表現高度反映 DRAM 循環：2021 高點後進入修正，2023 觸底，2024 回穩，2025 隨價格與需求改善重新轉盈。
```

Suggested English copy:

```text
Nanya's financial performance closely tracks the DRAM cycle: a 2021 high, a downturn into 2023, stabilization in 2024, and a 2025 return to profit as pricing and demand improved.
```

Expected: the finance section frames the numbers as a cycle, not just as isolated metrics.

- [ ] **Step 2: Add three financial interpretation cards or rows**

Place them below the existing metric cards or below the finance chart. Suggested Chinese content:

```text
DRAM 營收集中度
財務研究顯示 DRAM 長期占營收 99.8% 以上，讓公司獲利高度連動全球 DRAM 報價、庫存與供需循環。

營運槓桿
半導體製造固定成本高，當營收從谷底回升，產能利用率、毛利率與營運現金流會被同步放大。

資本支出壓力
即使在 111-113 年低谷期，1A/1B 奈米、DDR5 與新廠投資仍需持續投入，考驗資產負債表與現金流韌性。
```

Suggested English content:

```text
DRAM revenue concentration
The finance research shows DRAM has accounted for more than 99.8% of revenue, making earnings highly linked to global DRAM pricing, inventory, and supply-demand cycles.

Operating leverage
Semiconductor manufacturing carries high fixed costs, so recovery from the trough can amplify capacity utilization, gross margin, and operating cash flow.

Capital spending pressure
Even during the 2022-2024 trough, 1A/1B nm, DDR5, and fab investment still required spending, testing balance-sheet and cash-flow resilience.
```

Expected: financial data now supports a strategy-management interpretation.

- [ ] **Step 3: Keep the visual density under control**

Implementation guidance:

```text
Use 3 compact cards, short rows, or a small callout.
Do not add a large Chart.js chart.
Do not add a second finance page.
Do not exceed one viewport of extra financial text on desktop.
```

Expected: the section remains scannable during peer review.

---

## Task 4: Ground Market Analysis in Finance Research

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Expand the market lead**

Suggested Chinese copy:

```text
南亞科處在 DRAM 價格循環、AI 產能排擠、DDR5 世代轉換與區域化供應鏈重組交會的位置。
```

Suggested English copy:

```text
Nanya sits where DRAM pricing cycles, AI-driven capacity crowding, DDR5 migration, and regionalized supply chains intersect.
```

Expected: the market section directly reflects the teammate financial research.

- [ ] **Step 2: Update SWOT Opportunities**

Suggested Chinese copy:

```text
AI/HBM 產能排擠使主流 DDR4、DDR5 供給趨緊；Edge AI、AI PC 與 AI smartphone 提升單機記憶體搭載量；China Plus One 增加台灣供應來源的策略價值。
```

Suggested English copy:

```text
AI/HBM capacity crowding tightens mainstream DDR4 and DDR5 supply; Edge AI, AI PCs, and AI smartphones raise memory content per device; China Plus One increases the strategic value of Taiwan-based supply.
```

Expected: opportunities are no longer generic AI/DDR5 language.

- [ ] **Step 3: Update SWOT Threats**

Suggested Chinese copy:

```text
DRAM 景氣反轉、價格下跌、大廠擴產、先進製程落差、資本支出壓力與中國市場需求波動，仍會影響復甦品質。
```

Suggested English copy:

```text
DRAM downcycles, falling prices, large-player capacity expansion, advanced-node gaps, capital spending pressure, and China-market demand volatility can still affect recovery quality.
```

Expected: threats connect market risk to financial resilience.

---

## Task 5: Tie Growth Strategy to Financial Watchpoints

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Refine short-term strategy**

Suggested Chinese copy:

```text
短期策略是把握供給吃緊與報價回升，改善產能利用率、毛利率與營運現金流。
```

Suggested English copy:

```text
The short-term strategy is to capture tight supply and pricing recovery to improve utilization, gross margin, and operating cash flow.
```

Expected: short-term strategy explicitly links to operating leverage.

- [ ] **Step 2: Refine mid-term strategy**

Suggested Chinese copy:

```text
中期策略是提高 DDR5、LPDDR5 與 AI/Edge AI 應用比重，降低對低階成熟產品與單一景氣循環的依賴。
```

Suggested English copy:

```text
The mid-term strategy raises DDR5, LPDDR5, and AI/Edge AI application share, reducing dependence on lower-end mature products and a single cycle.
```

Expected: mid-term strategy incorporates Edge AI and product-mix logic.

- [ ] **Step 3: Refine long-term strategy**

Suggested Chinese copy:

```text
長期策略是追蹤 1B 奈米良率、新廠產能、資本支出效率與策略客戶綁定，建立更穩定的需求與技術升級基礎。
```

Suggested English copy:

```text
The long-term strategy tracks 1B nm yield, new fab capacity, capital-spending efficiency, and strategic customer binding to build a more stable base for demand and technology migration.
```

Expected: long-term strategy uses the financial report's final watchpoints.

---

## Task 6: Update VRIN and Keyword Cards Where Useful

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Strengthen VRIN capacity/resource wording**

Update the `vrin3` row to make capital intensity and new fab capability clearer.

Suggested Chinese copy:

```text
新廠、資本支出與製程升級能力
```

Suggested English copy:

```text
New fab, capital spending, and process-upgrade capability
```

Expected: resource evaluation reflects financial pressure and strategic investment.

- [ ] **Step 2: Consider one new flip card for Operating Leverage**

Add only if the flip-card grid still feels balanced. Suggested content:

```javascript
["Operating Leverage", "高固定成本產業中，營收變動會放大毛利率與現金流變化。"]
["Operating Leverage", "In high-fixed-cost industries, revenue changes can amplify gross margin and cash-flow movement."]
```

Expected: interactive learning covers the new financial concept.

- [ ] **Step 3: Consider one new flip card for China Plus One**

Add only if the market section uses this term visibly. Suggested content:

```javascript
["China Plus One", "企業分散中國以外供應來源，以降低地緣政治與供應鏈集中風險。"]
["China Plus One", "A sourcing strategy that diversifies supply beyond China to reduce geopolitical and concentration risk."]
```

Expected: users can understand the new supply-chain term from the interactive cards.

---

## Task 7: Update Source and AI Disclosure

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add financial-report source wording**

Suggested Chinese disclosure:

```text
本網站使用南亞科技官方網站、年度合併財務報告、投資人關係資料、公開新聞、產業研究資料與 104 人力銀行職缺頁面作為公司介紹、財務資訊、市場分析與職涯洞察之基礎。
```

Suggested English disclosure:

```text
This website uses Nanya Technology's official website, annual consolidated financial reports, investor-relations materials, public news sources, industry research, and 104 Job Bank postings as references for company introduction, financial information, market analysis, and career insights.
```

Expected: financial figures have an explicit source category.

- [ ] **Step 2: Make AI use more concrete**

Suggested Chinese disclosure continuation:

```text
AI 工具使用於資料初步整理、雙語文案草稿、網頁架構規劃、互動題目設計與程式碼輔助；最終數字、事件與分析結論由組員人工查核、改寫與整合。
```

Suggested English disclosure continuation:

```text
AI tools were used for initial data organization, bilingual drafting, website-structure planning, quiz design, and coding support; final figures, events, and conclusions were manually checked, rewritten, and integrated by team members.
```

Expected: the page better satisfies the academic-integrity and AI-use requirement.

- [ ] **Step 3: Clarify visual/copyright status**

Suggested Chinese sentence:

```text
頁面圖表與視覺元件為本組依公開資料自行整理與製作，未使用外部圖片或影片素材。
```

Suggested English sentence:

```text
Charts and visual elements were produced by the team from public information; no external image or video assets are used.
```

Expected: copyright/source status is clear and the "no broken media" risk remains low.

- [ ] **Step 4: Update source links**

Add or replace source links so they include:

```text
Nanya company profile
Nanya annual reports or investor-relations financial reports
Nanya corporate commitment or ESG/vision page
TrendForce DRAM industry research
Reuters private-placement news
104 Job Bank source or exact job-search result used by the team
```

Expected: source list supports all major content categories.

---

## Task 8: Complete Bilingual Coverage

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Search for fixed Chinese visible text**

Run:

```powershell
rg -n "[\p{Han}]" index.html
```

Expected: Chinese appears inside `translations.zh`, bilingual source labels, or intentionally Chinese names. Fixed visible Chinese outside translation handling should be reviewed.

- [ ] **Step 2: Translate footer metadata**

The footer currently contains fixed text such as:

```text
1142 國際策略管理
授課教師：梅筱珍
GitHub Pages Ready
```

Add translation keys such as:

```javascript
footerCourse
footerTeacher
footerDeploy
```

Suggested English copy:

```text
1142 International Strategic Management
Instructor: Mei Hsiao-Chen
GitHub Pages Ready
```

Expected: English mode no longer leaves footer metadata in Chinese except for proper names when intentionally retained.

- [ ] **Step 3: Translate source-link labels if feasible**

Source links can keep official Chinese organization names, but visible category labels should be bilingual or neutral. Suggested approach:

```text
南亞科技公司簡介 / Company profile
年度合併財務報告 / Annual reports
104 人力銀行職缺資料 / Career data
```

Expected: English-mode readers can understand source categories.

---

## Task 9: Verify Interactions and Layout

**Files:**
- Verify: `index.html`

- [ ] **Step 1: Static checks**

Run:

```powershell
rg -n "historyTitle|orgTitle|financeInterpret|Operating Leverage|China Plus One|annual consolidated|年度合併財務報告" index.html
```

Expected: output shows all newly added content and translation keys.

- [ ] **Step 2: Open local file in browser**

Use:

```text
file:///C:/Users/ofire/Desktop/SMMCTP0/index.html
```

Expected:

- Page loads without console errors.
- Company section includes history and organization.
- Finance section includes cycle, DRAM concentration, operating leverage, and capital-spending interpretation.
- Market section includes AI/HBM capacity crowding, Edge AI, DDR5 transition, and China Plus One.
- Growth section includes 1B nm yield, DDR5 mix, capital-spending efficiency, and strategic customer binding.

- [ ] **Step 3: Interaction smoke test**

Manually verify:

```text
Language switch: Chinese and English both update new content.
Dark mode: new cards/rows remain readable.
Voice guide: new text is included in readable content and controls still work.
Quiz: first answer updates score.
Flip cards: existing cards and any new cards flip.
Mobile menu: opens, closes, and anchor links work.
```

Expected: no interaction regression.

- [ ] **Step 4: Mobile layout check**

Check at roughly 390px width and 768px width.

Expected:

```text
No text overlap.
No horizontal overflow except the existing VRIN table if intentionally scrollable.
Finance and company additions remain scannable.
Footer metadata wraps cleanly.
```

---

## Task 10: Final Publishing Check

**Files:**
- Verify: `index.html`
- Verify: GitHub Pages output after commit/push

- [ ] **Step 1: Review git status**

Run:

```powershell
git status --short
```

Expected: only intended files are modified or untracked. Existing untracked source files such as `競賽說明.md` and `南亞科-財務.html` should not be accidentally committed unless the team wants them in the repository.

- [ ] **Step 2: Commit only final intended changes**

Suggested commit scope if only `index.html` changes:

```powershell
git add index.html
git commit -m "content: strengthen Nanya finance and strategy analysis"
```

If committing this plan document too:

```powershell
git add index.html docs/superpowers/plans/2026-05-25-nanya-finance-content-integration.md
git commit -m "content: strengthen Nanya finance and strategy analysis"
```

Expected: commit excludes unrelated untracked source files unless intentionally included.

- [ ] **Step 3: Verify deployed page after push**

After push and GitHub Pages deployment, run:

```powershell
curl.exe -I -L --max-time 15 https://novoicefire.github.io/SMMCTP0/
```

Expected:

```text
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
```

- [ ] **Step 4: Compare local and deployed content if needed**

Run:

```powershell
$tmp=New-TemporaryFile
curl.exe -L --max-time 20 -o $tmp.FullName https://novoicefire.github.io/SMMCTP0/
(Get-FileHash -Algorithm SHA256 index.html).Hash
(Get-FileHash -Algorithm SHA256 $tmp.FullName).Hash
Remove-Item -LiteralPath $tmp.FullName
```

Expected: hashes match after GitHub Pages finishes deploying.

---

## Completion Gate

This work is complete only when all of the following are true:

- Financial values are consistent across chart, metrics, text, quiz, and bilingual translations.
- Company section explicitly covers history and organization/business/function levels.
- Finance section explains DRAM concentration, operating leverage, and capital-spending pressure.
- Market and growth sections incorporate AI/HBM capacity crowding, Edge AI, DDR5 transition, China Plus One, 1B nm yield, DDR5 mix, and capital-spending efficiency.
- Sources and AI disclosure mention annual consolidated financial reports, concrete AI use categories, and self-made visual/chart status.
- English mode covers new and existing fixed footer/source labels well enough for an English reader.
- Existing interactions still work on desktop and mobile.
- GitHub Pages serves the updated `index.html`.

