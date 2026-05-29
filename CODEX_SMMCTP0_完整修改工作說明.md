# Codex 修改工作說明：SMMCTP0 南亞科技互動式學習網頁內容整合與資料校正

## 0. 任務目標

請直接修改本地專案根目錄中的 `index.html`，把根目錄內五份南亞科分析資料的核心內容完整整合到既有互動式單頁網站中，同時維持頁面精簡、圖像化、可互動與雙語一致。

本次修改不是把五份 Markdown 逐篇搬上網頁，也不是為每份檔案新增長篇章節。請以現有頁面架構為主，將內容嵌入既有區塊，使網站形成一條完整敘事：

> 南亞科處於 DRAM 價格循環與 AI 記憶體需求擴張的交會點；公司透過產品升級、新廠投資與策略夥伴合作，避開與全球前三大廠進行全面規模競爭，並建立下一階段成長動能。

---

## 1. 開始前必讀檔案

請先讀取以下檔案，再修改 `index.html`：

```text
./index.html
./STP+4P.md
./競合策略.md
./五力分析+pestel.md
./價值鏈分析+知識基礎觀點.md
./投資組合策略+資本配置.md
```

`競賽說明.md` 不作為本次分析內容來源；現有網站已具備的課程功能不可因重構內容而損壞。

---

## 2. 強制實作限制

1. **只保留單一 HTML 成品**：網站主體仍為 `index.html`，CSS 與 JavaScript 均內嵌，不引入需要額外部署的框架、圖表套件或外部媒體素材。
2. **保留現有功能**：
   - 繁體中文／英文切換。
   - 明暗模式切換。
   - 語音導覽與進度控制。
   - 翻轉字卡。
   - 五題以上互動測驗。
   - RWD 手機／桌機版。
   - 資料來源與 AI 使用揭露。
3. **雙語同步**：所有新增的標題、數據標籤、圖表內容、互動說明與測驗，均需有 `zh` 與 `en` 版本；切換語言後不可留有上一語言文字。
4. **優先改造既有 section**：除非結構無法承載，禁止為五份資料各新增獨立的大型 section。
5. **視覺優先**：每個分析觀點以數字、圖、矩陣、流程圖、關係圖或小型卡片呈現；單一展開說明控制於繁體中文約 80 字以內。
6. **不要在畫面顯示不確定性標籤**：移除使用者可見的 `已確認`、`推論`、`混合`、`待核實`、`Confirmed`、`Inference`、`Mixed`、`Unverified` status chip。
7. **事實與分析分開**：
   - 查證過的公司資料、數字與已發布事件可直接顯示。
   - 理論解讀請標成 `策略判讀` / `Strategic reading`，不要寫成公司已公開宣稱的事實。
   - 無公開可靠依據的具體合作、客戶、合約年限、設備導入或財務預測，直接移除，不改用模糊或待核實標籤保留。
8. **不要把私募寫成併購**：2026 事件為私募增資與策略投資，不是併購。
9. **保留資料來源追溯性**：每張新增圖表／互動視覺旁提供可展開的 `來源` / `Sources` 小區塊，並同步更新頁面底部總來源區。

---

## 3. 資料權威順序

若五份分析檔與查證資料不一致，請依下列順序採用資料：

1. 南亞科技官方投資人關係、官方公司資料、官方產品頁、官方里程碑。
2. TrendForce 產業統計與產業新聞。
3. Reuters 對私募投資及供應協議之報導。
4. 五份本地 Markdown：僅作為分析框架、策略解讀與待整合主題來源；涉及數字或已發生事件時，必須以上述來源核定後才呈現。

---

## 4. 已查證、可直接使用的資料表

### 4.1 公司與資本資料

| 項目 | 可呈現數值／事實 | 用途 |
|---|---|---|
| 公司名稱 | 南亞科技股份有限公司 / Nanya Technology Corporation | 公司概覽 |
| 成立 | 1995 年 3 月 | 公司概覽／時間軸 |
| 上市 | 2000 年 8 月，TWSE 2408 | 公司概覽／時間軸 |
| 資本額 | 新台幣 345 億元，截至 2026 年 4 月 | 首頁或公司基本資料；取代現有 309.9 億元 |
| 員工 | 3,700+ | 公司資料／PESTEL Social |
| 公司官方定位 | 專注 DRAM 研發、設計、製造與銷售；官方公司介紹稱全球 DRAM 產業排名第 4 | 首頁可保留「全球第 4 大 DRAM」，但必須附官方來源 |

來源：南亞科技官方 Investor Relations / Company Profile 與 Our Company。

### 4.2 2025 財務結果與 2026 投資

| 項目 | 可呈現數值／事實 |
|---|---:|
| 2025 全年營收 | NT$66,587 million = **665.87 億元** |
| 2025 稅後淨利 | NT$6,603 million = **66.03 億元** |
| 2025 EPS | **2.13 元** |
| 2025 Q4 營收 | NT$30,094 million = **300.94 億元** |
| 2025 Q4 毛利率 | **49.0%** |
| 2025 Q4 營業利益率 | **39.1%** |
| 2025 Q4 EPS | **3.58 元** |
| 2025 董事會核准 CapEx 上限 | **196 億元** |
| 2025 實際 CapEx | **134 億元** |
| 遞延至 2026 之 CapEx | **62 億元** |
| 2026 計畫 CapEx | **約 500 億元**，官方表述為 pending Board approval |
| 128GB DDR5 RDIMM | **5600 / 6400 Mb/s 已達成功能驗證** |
| Mono-die 速度 | **最高 7200 Mb/s** |
| 新廠設備進駐 | **規劃於 2027 年初** |
| 1C / 1D 與客製化 AI 專案 | 官方表示按計畫推進 |

來源：南亞科技官方 2026/01/19 新聞稿 `Nanya Technology Reports Results for the Fourth Quarter 2025`。

### 4.3 4Q25 DRAM 產業比較資料

| 公司 | 4Q25 DRAM 營收 | 營收市占 |
|---|---:|---:|
| Samsung | US$19.30B | 36.0% |
| SK hynix | US$17.22B | 32.1% |
| Micron | US$11.98B | 22.4% |
| Nanya | US$0.97B | 約 1.8%（以 0.97 / 53.58 計算） |

| 產業／南亞科指標 | 數值 |
|---|---:|
| 4Q25 DRAM 產業營收 | US$53.58B |
| 4Q25 DRAM 產業營收季增 | +29.4% |
| 4Q25 conventional DRAM 合約價漲幅 | +45% 至 +50% |
| 1Q26 conventional DRAM 合約價預估漲幅 | +90% 至 +95% |
| Nanya 4Q25 營收季增 | +54.7% |
| Nanya 4Q25 ASP | 季增 30s% |
| Nanya 4Q25 營業利益率 | 39.1% |

計算欄位：
- Top 3 市占合計 = `36.0 + 32.1 + 22.4 = 90.5%`。
- Nanya 市占顯示為 `約 1.8%`，並在來源說明註記「依 TrendForce 公布之 Nanya 營收與產業總營收計算」。

來源：TrendForce，2026/02/26，`漲價帶動4Q25 DRAM產業營收季增29.4%，Samsung重返市占率第一`。

### 4.4 官方產品資料

| 產品 | 可顯示規格 | 官方狀態 | 用途 |
|---|---|---|---|
| DDR5 Standard DRAM | 16Gb、5600 Mbps、Commercial / Industrial | Available | 產品配置、STP |
| DDR5 Standard DRAM 高速版本 | 16Gb、6400 / 7200 / 8000 Mbps | In Development | 產品規格卡 |
| LPDDR5/5X | 8 / 16 / 32 / 64Gb、6400 / 7500 Mbps；含 Commercial / Industrial / Automotive 型號 | In Development | 產品配置、低功耗市場 |
| KGD LPDDR5/5X | 8 / 16Gb、7500 Mbps | In Development | 產品配置、互補合作解讀 |
| DDR5 RDIMM Available | 16GB / 32GB、5600 Mbps | Available | Server / Data Center 產品卡 |
| DDR5 RDIMM 高容量 | 128GB、5600 / 6400 / 7200 Mbps | In Development；另有官方新聞稿確認 5600 / 6400 Mb/s 功能驗證 | Server / Data Center 產品卡 |

注意：`Available` 與 `In Development` 是產品頁官方 availability 欄位，可正常呈現；它們不是網站內部的不確定性標記。

來源：南亞科技官方 DDR5、LPDDR5/5X、KGD LPDDR5/5X、RDIMM 產品頁。

### 4.5 官方里程碑與 ESG

| 年份 | 已發布事件 | 可整合位置 |
|---:|---|---|
| 2021 | 第一代 10nm class process technology (1Anm) pilot run；DDR5 product development | 公司時間軸 |
| 2022 | New Fab Groundbreaking Ceremony | 公司時間軸／CapEx |
| 2024 | 與 Kioxia 合作開發 Vertical Channel Transistor DRAM Technology | 公司時間軸／Value Net |
| 2024 | 投資 PieceMakers 發展 Customized Ultra-high-bandwidth Memory | 公司時間軸／Value Net |
| 2024 | MSCI ESG `AA` Rating | 如需歷年 ESG 可用 |
| 2026 | CDP Climate Change `A List` 與 Water Security `A List` | PESTEL Environmental |
| 2026 | MSCI ESG Rating `A` | PESTEL Environmental；不要仍寫 AA 為當期評級 |

來源：南亞科技官方 Corporate Milestone。

### 4.6 2026 私募增資與策略投資

| 項目 | 可呈現內容 |
|---|---|
| 事件類型 | 私募增資／策略投資 |
| 募資規模 | 約 US$2.5B，約新台幣 790 億元 |
| 每股認購價格 | NT$223.9 |
| 投資者 | SanDisk Technologies、Solidigm、Cisco Systems、Kioxia |
| SanDisk 投資額 | 約 NT$31B = 約 310 億元 |
| Solidigm 投資額 | 約 NT$16B = 約 160 億元 |
| Cisco 投資額 | 約 NT$16B = 約 160 億元 |
| Kioxia 投資額 | 約 NT$16B = 約 160 億元 |
| 資金用途 | 工廠設施與先進記憶體生產設備投資 |
| 已公開確認的供應協議 | SanDisk：multi-year strategic DRAM supply agreement；Kioxia：long-term DRAM supply agreement |
| 不可延伸書寫 | 不得寫 Cisco 或 Solidigm 已簽 DRAM 長約；不得寫所有投資人都有三年供應協議；不得把私募稱為併購 |

來源：Reuters，2026/03/26，`Nanya Technology shares surge 10% after $2.5 billion fundraising`。

---

## 5. 必須刪除、替換或降為分析語句的現行內容

### 5.1 直接替換

| 現行內容 | 修改後 |
|---|---|
| 公司基本資料中的「實收資本額新台幣 309.9 億元」 | 「資本額新台幣 345 億元，截至 2026 年 4 月」 |
| 市占資料 `SK hynix 36.0%、Samsung 33.7%、Micron 24.3%、Nanya 0.81%` | 改為 4Q25：Samsung 36.0%、SK hynix 32.1%、Micron 22.4%、Nanya 約 1.8% |
| ESG 敘述若把 MSCI `AA` 當作目前評級 | 改為「2026 年 3 月 MSCI ESG Rating A」；可在時間軸另呈現 2024 年曾獲 AA |
| `valueNetData` 中 status 欄位及 UI status chips | 全面刪除，不再以真偽狀態呈現內容 |
| LPDDR5 / KGD 點位的 `inference`、`mixed` 狀態 | 改為顯示官方規格與官方 availability |

### 5.2 移除

| 現行內容 | 移除理由 |
|---|---|
| `TSMC` / `Vera Rubin` / `LPDDR5X` 合作假設節點 | 未有可靠公開來源支撐南亞科與該合作關係 |
| `ASML` 作為南亞科 Value Net 的直接節點，以及「EUV 裝機未確認」字樣 | 不在主頁展示未確認設備導入關係；供應商壓力可改寫成泛稱先進製程設備與高額 CapEx |
| Cisco 或 Solidigm 具體 DRAM 供應／長約綁定說法 | 目前可確認其為私募投資者，未在查證來源中確認 DRAM supply agreement |
| 「所有私募投資者皆有 3 年供應協議／3 年 LTA」 | 無足夠已查證來源 |
| 「已打入 NVIDIA 供應鏈」或具名 AI 客戶合作 | 無足夠已查證來源 |
| EUV 已裝機或已採購的描述 | 無官方確認 |
| WACC、NPV、良率 85%、ASP 溢價 15% 作為事實數據 | 屬模型假設；如使用只可放在課堂情境模擬器，不可寫成公司實績或預測 |

### 5.3 改為「策略判讀」而非事實敘述

| 分析主張 | 可保留的安全寫法 |
|---|---|
| 南亞科避開正面規模戰 | `策略判讀：4Q25 前三大 DRAM 廠營收市占合計 90.5%，南亞科較適合以產品升級與合作關係尋求差異化。` |
| HBM 排擠傳統產品供給 | `策略判讀：TrendForce 指出 AI 需求擴散至 general server，帶動 RDIMM 與 conventional DRAM 訂單及價格上升。` |
| FAE 提升轉換成本 | `策略判讀：客戶驗證與技術支援可提高合作黏著度。` |
| KGD 是 AI memory 機會 | `策略判讀：KGD LPDDR5/5X 規格可支援客製化與合作型記憶體方案。` |
| 新廠為 Real Option | `課堂模型：新廠投資可視為產品升級與產能擴張的策略選擇權。` |

---

## 6. 現有頁面架構的整合改造規格

### 6.1 `Hero`：只改 KPI，不新增長篇內容

保留現有 Hero 版面與主敘事，將 quick stats 更新為四張可查證 KPI 卡：

| 卡片 | 中文顯示 | 英文顯示 | 點擊／hover 補充 |
|---|---|---|---|
| 2025 營收 | `665.87 億元` | `NT$66.587B` | `全年營收 / FY2025 revenue` |
| 2025 EPS | `2.13 元` | `NT$2.13` | `2025 Q4 EPS：3.58 元` |
| 2026 計畫 CapEx | `約 500 億元` | `Approx. NT$50B` | `Pending Board approval` |
| 新廠節點 | `2027 年初裝機` | `Equipment move-in: early 2027` | `新廠 / New fab` |

處理原有「全球第 4 大 DRAM」：
- 可移到公司概覽的簡短 badge，並附官方 Our Company 來源。
- 首頁 KPI 改用上表的可量化數據，資訊密度更高。

視覺：
- 右側原 console card 保留。
- 可在 card 下方增加三個切換按鈕：`營收 Revenue`、`EPS`、`CapEx`，用原生 SVG 顯示迷你趨勢；不可引入圖表 CDN。

---

### 6.2 `#company`：現有時間軸升級為策略事件軸

保留基本資料、產品矩陣、應用市場、全球據點四行，更新資本額。將原本粗略時間軸改成可點選時間軸：

| 年份 | 卡片標題 | 一行內容 |
|---:|---|---|
| 1995 | 成立 | 專注 DRAM 研發、設計、製造與銷售 |
| 2000 | TWSE 2408 | 於台灣證券交易所上市 |
| 2021 | 製程與 DDR5 | 1Anm pilot run；DDR5 product development |
| 2022 | 新廠動土 | New Fab Groundbreaking Ceremony |
| 2024 | Kioxia 合作 | VCT DRAM Technology |
| 2024 | PieceMakers 投資 | Customized Ultra-high-bandwidth Memory |
| 2025 | 重新轉盈 | Revenue 665.87 億；EPS 2.13 |
| 2026 | ESG 與資本 | CDP 雙 A List；MSCI ESG Rating A；資本額 345 億 |
| 2027 | 新廠節點 | 設備預計於年初進駐 |

互動形式：
- 桌機：水平年份標籤＋右側 detail panel。
- 手機：垂直時間軸＋點擊展開。
- Detail panel 僅包含一筆事件、最多兩個數字及來源連結。

吸收檔案：
- `競合策略.md`：Kioxia／PieceMakers 關係。
- `投資組合策略+資本配置.md`：新廠里程碑。
- `價值鏈分析+知識基礎觀點.md`：技術與 ESG 能力。

---

### 6.3 `#market`：改造成三頁籤分析控制台

保留 section id 與導航文字，將內容組織為：

```text
[產業結構 Industry] [市場選擇 STP] [外部環境 PESTEL]
```

#### Tab A：產業結構 `Industry`

##### 圖表 1：4Q25 DRAM 營收／市占橫條圖

使用原生 HTML/CSS bar 或 SVG：

| Bar | Value Label |
|---|---|
| Samsung | `US$19.30B · 36.0%` |
| SK hynix | `US$17.22B · 32.1%` |
| Micron | `US$11.98B · 22.4%` |
| Nanya | `US$0.97B · 約 1.8%` |

圖表旁顯示高亮數字：

```text
Top 3 = 90.5%
Nanya 4Q25 revenue growth = +54.7% QoQ
```

##### 圖表 2：市場週期數據列

四張小卡：

| 指標 | 值 |
|---|---:|
| DRAM 產業營收季增 | `+29.4%` |
| 4Q25 conventional DRAM 合約價 | `+45–50%` |
| 1Q26 conventional DRAM 合約價預估 | `+90–95%` |
| Nanya 4Q25 營業利益率 | `39.1%` |

##### 五力互動按鈕

保留目前五力按鈕與 detail panel，但 detail panel 每次只輸出「數字／判讀／回應」三列：

| 力量 | 數字或事實 | 策略判讀 | 策略回應 |
|---|---|---|---|
| 現有競爭者 | 前三大市占 90.5%；Nanya 約 1.8% | 規模差距明顯 | 聚焦產品升級與合作型需求 |
| 供應商 | 2026 計畫 CapEx 約 500 億元 | 升級需要高資本投入 | 以新廠與製程計畫支撐升級 |
| 買方 | SanDisk、Kioxia 已公布 DRAM 供應協議 | 客戶重視穩定供應 | 以策略投資結合長期供應 |
| 替代品 | AI 需求推升 RDIMM / HBM / LPDDR5X 記憶體需求 | 產品需求重組 | 展示 RDIMM、LPDDR5/5X、客製化記憶體 |
| 新進入者 | 只在找到可公開引用且可直接驗證的 CXMT 資料時顯示數字 | 成熟與主流 DRAM 競爭增加 | 強化差異化；若無可直接保存來源，只保留不含數字的分析句 |

#### Tab B：市場選擇 `STP`

不要寫 STP 長文，新增可點擊矩陣：

| 市場區隔 | 需求重點 | 已公開產品／合作依據 | 定位 |
|---|---|---|---|
| Server / Data Center | 高容量、高速 | DDR5 RDIMM；128GB 5600/6400 Mb/s 功能驗證 | 高容量伺服器記憶體 |
| Mobile / Low Power | 低功耗、高速度 | LPDDR5/5X 8–64Gb、6400/7500 Mbps 開發中 | 低功耗產品布局 |
| Industrial / Automotive | 高溫度範圍、可靠度 | DDR5 Industrial Available；LPDDR5/5X Industrial / Automotive 型號開發中 | 高可靠度產品布局 |
| SSD / NAND Partners | 穩定 DRAM 供應 | SanDisk、Kioxia 供應協議 | 策略互補供應合作 |
| Customized Memory | 客製化記憶體方案 | PieceMakers 投資；官方客製化 AI 專案按計畫推進 | 客製化記憶體合作 |

互動規格：
- 點擊 row 或 tile，右側 detail card 顯示「需求／產品數據／策略定位」。
- 不出現未證實客戶名稱（例如 NVIDIA、MediaTek、NXP）。
- 此 tab 吸收 `STP+4P.md` 的 Segmentation、Targeting、Positioning，而不另開 STP 大段落。

#### Tab C：外部環境 `PESTEL`

將目前四卡擴展成完整六卡，每卡僅一個事實＋一句策略讀法：

| 面向 | 顯示事實 | 策略判讀 |
|---|---|---|
| Political | 台灣為南亞科主要研發與製造基地 | 全球客戶更重視供應來源配置 |
| Economic | 2025 EPS `2.13`；4Q25 conventional DRAM price `+45–50%` | 景氣與價格直接影響獲利 |
| Social | 員工 `3,700+` | 技術升級需要人才與知識累積 |
| Technological | DDR5 16Gb 5600 Mbps Available；128GB RDIMM 已功能驗證 | 產品升級以公開規格呈現 |
| Environmental | 2026 CDP Climate Change / Water Security `A List` | 永續表現支撐供應鏈信任 |
| Legal / Governance | 私募投資者四家；資金投向先進記憶體設備與廠房 | 合作與資本配置須以公開資料呈現 |

吸收檔案：
- `五力分析+pestel.md`：五力、PESTEL。
- `STP+4P.md`：市場區隔與定位。
- `競合策略.md`：策略夥伴。
- 移除 OLI、Cournot、Bertrand 等長篇理論敘述；可在理論地圖保留名稱或以 tooltip 說明，不佔主畫面。

---

### 6.4 `#finance`：加入 `CapEx / New Fab` 互動頁籤

保留目前營收、EPS、FCF、DuPont、Beta 切換結構。新增第六個頁籤：

```text
CapEx / New Fab
```

資料卡：

| Label | Value |
|---|---:|
| 2025 CapEx Budget Ceiling | `196 億元` |
| 2025 Actual CapEx | `134 億元` |
| Deferred to 2026 | `62 億元` |
| 2026 Planned CapEx | `約 500 億元` |

視覺：
- 使用對照長條圖呈現 `2025 actual 134` 與 `2026 planned 500`。
- 顯示計算資訊：`2026 planned / 2025 actual ≈ 3.7x`。
- 圖下加一條新廠時程：
  ```text
  2022 新廠動土 → 2026 計畫 CapEx 約 500 億 → 2027 年初設備進駐
  ```

分析短句：
> `策略判讀：2025 轉盈改善資金基礎，2026 的資本投入將決定產品升級與新產能落地速度。`

情境模型：
- 如要吸收來源檔案中的 NPV、WACC、Real Options，只新增一個折疊面板 `課堂情境模型 / Classroom scenario model`。
- 不使用來源檔案中的 WACC、良率門檻或 ASP 溢價作為公司事實。
- 面板可讓使用者切換 `價格下降 / 基準 / 價格上升` 與 `裝機較慢 / 按計畫`，輸出「現金流壓力」與一行解讀；不得顯示假設為已公布預測。

---

### 6.5 `#portfolio`：擴充產品象限與 4P 資訊卡

保留現有象限圖，但將點位擴充至六項：

| 產品點位 | 顯示策略角色 | 規格卡應顯示內容 |
|---|---|---|
| DDR4 | Cash Cow | 官方產品線存在；成熟產品與現金流支撐 |
| DDR5 | Star | 16Gb；5600 Mbps Available；6400/7200/8000 Mbps In Development |
| DDR5 RDIMM | Star / Server Upgrade | 16/32GB 5600 Mbps Available；128GB 5600/6400 Mbps 功能驗證；最高 7200 Mb/s |
| LPDDR5/5X | Growth Option | 8–64Gb；6400/7500 Mbps；Industrial / Automotive 型號；In Development |
| KGD LPDDR5/5X | Strategic Complement | 8/16Gb；7500 Mbps；In Development |
| MCP/eMCP/uMCP | Portfolio Coverage | 官方列有 MCP LPDDR4X、eMCP LPDDR3/eMCP LPDDR4X、uMCP LPDDR4X |

重要：
- 不再顯示 `status: confirmed/inference/mixed`。
- 官方產品的 `Available` / `In Development` 可以正常顯示。
- 不要給 LPDDR5/5X 虛構市占或具名客戶。

在右側產品 detail panel 底部，整合 4P 為四個小欄，不新增長篇 4P section：

| 4P | 顯示方式 |
|---|---|
| Product | 產品規格與官方 availability |
| Price | 不顯示未公開售價；顯示 `B2B specification / supply agreement driven` 等定性描述 |
| Place | 對應應用市場：Server、Mobile、Industrial、Automotive、SSD partner |
| Promotion | 顯示 `功能驗證`、`客戶技術支援`、`供應合作` 等公開或合理策略詞 |

產品例：DDR5 RDIMM 詳情卡：

```text
DDR5 RDIMM
Product：16 / 32GB 5600 Mbps Available；128GB 5600 / 6400 Mbps 已達成功能驗證
Price：高容量 B2B 產品；不揭露未公開定價
Place：Server / Data Center
Promotion：Functional validation + technical support
```

吸收檔案：
- `STP+4P.md`：Product / Price / Place / Promotion 的簡化整合。
- `投資組合策略+資本配置.md`：BCG / GE / Ansoff 產品角色。
- `競合策略.md`：KGD、MCP 與互補合作。

---

### 6.6 `#resources`：將 VRIN 下方流程改成 `Value Chain × KBV`

保留既有 VRIN 表；更新下方 `capabilityFlow` 為五節點可點擊流程：

```text
研發製程 → 晶圓製造 → 產品組合 → 客戶驗證／合作 → 財務回饋與再投資
```

| 節點 | 主畫面只顯示 | Detail panel 顯示 |
|---|---|---|
| 研發製程 | `1C / 1D + Customized AI` | 官方表示專案按計畫推進；KBV：製程知識累積支撐產品升級 |
| 晶圓製造 | `CapEx 約 500 億` | 新廠設備預計 2027 年初進駐 |
| 產品組合 | `DDR5 · RDIMM · LPDDR5/5X · KGD` | 點擊導回產品象限 |
| 客戶驗證／合作 | `SanDisk · Kioxia` | 已公布 DRAM supply agreements；Kioxia 另有 VCT DRAM 合作 |
| 財務回饋 | `Revenue 665.87 億 · EPS 2.13` | 轉盈支撐下一階段投資判讀 |

KBV 呈現方式：
- 不寫 Grant、Kogut & Zander 的長篇文章。
- 在 detail panel 加一行 `理論連結：知識基礎觀點（KBV）— 製程知識、驗證經驗與客戶合作形成累積能力。`
- `theoryMapData` 中保留完整理論名稱與提出者即可。

若要加入五年研發費用長條圖：
- 必須由 Codex 先從官方財務報告逐年核對 `2021–2025 R&D expenses`。
- 若無法在本次修改過程查證，不要從分析檔直接抄數值上線；本次以已查證流程圖完成 KBV 整合即可。

---

### 6.7 `#growth`：整合私募圓餅圖、Value Net 與 Ansoff / Real Options

#### A. 私募投資視覺化

在目前成長策略三步驟下方、Value Net 上方加入 donut chart 或 stacked allocation bar：

標題：
```text
2026 策略私募投資配置｜約 NT$790 億
2026 Strategic Private Placement | Approx. NT$79B
```

資料：

| 投資者 | 投資額（約） | 顯示關係 |
|---|---:|---|
| SanDisk | NT$310 億 | 投資者＋multi-year DRAM supply agreement |
| Solidigm | NT$160 億 | 投資者 |
| Cisco | NT$160 億 | 投資者 |
| Kioxia | NT$160 億 | 投資者＋long-term DRAM supply agreement＋VCT DRAM 合作 |

圓餅圖數值皆使用 `約` / `Approx.`，因 Reuters 為概約金額。

#### B. 重做 Value Net 節點

將 `valueNetData` 改為僅保留可支撐、具有學習價值的角色：

| 公司／角色 | 類型 | 關係內容 |
|---|---|---|
| SanDisk | 客戶＋互補者＋投資者 | 投資約 310 億；多年期 DRAM 供應協議 |
| Kioxia | 客戶＋互補者＋投資者 | 投資約 160 億；長期 DRAM 供應協議；2024 VCT DRAM 合作 |
| Solidigm | 投資者 | 投資約 160 億 |
| Cisco | 投資者 | 投資約 160 億 |
| PieceMakers | 技術／投資合作 | 2024 客製化超高頻寬記憶體 |
| Samsung | 競爭者 | 4Q25 DRAM 市占 36.0% |
| SK hynix | 競爭者 | 4Q25 DRAM 市占 32.1% |
| Micron | 競爭者 | 4Q25 DRAM 市占 22.4% |

可選節點：
- `CXMT` 僅在 Codex 能加入可保存與可引用的可靠來源時呈現；如納入，請寫為競爭者，不寫特定合作關係。
- 不加入 `ASML`、`TSMC`，避免使用未確認的南亞科直接關係。

#### C. 成長三步驟角標

保留目前三張策略卡，加入策略工具角標：

| 現有步驟 | 新角標 | 一行內容 |
|---|---|---|
| 把握 DRAM 上行週期 | `Market Penetration` | 使用既有產品承接價格與需求回升 |
| 提高 DDR5 / LPDDR5 與 AI 產品比重 | `Product Development` | 新產品服務伺服器、低功耗與客製化應用 |
| 新廠與策略投資 | `Real Option` | 以新產能與合作保留下一階段成長選擇權 |

這樣可把 `Ansoff` 與 `Real Options` 融入現有卡片，不新增理論文章。

---

### 6.8 `#career`：以三個職缺連接價值鏈

保留現有三張職缺卡與薪資資料。於卡片上方加簡短能力對應圖：

| 職缺 | 對應策略能力 |
|---|---|
| 軟體開發工程師 | MES / 智慧製造資料系統 |
| 製程技術開發工程師 | 1C / 1D、新廠與製程升級 |
| FAE 技術工程師 | 客戶驗證與技術服務 |

此處只作為 Value Chain / KBV 的人才承接，不增加人才理論長文。

---

### 6.9 翻轉字卡與小測驗同步更新

#### 翻轉字卡新增／修正

保留現有框架字卡，新增或更新下列內容：

| 字卡 | 背面內容重點 |
|---|---|
| `DDR5 RDIMM` | 128GB 5600/6400 Mb/s 已達成功能驗證，對應伺服器高容量需求 |
| `Private Placement` / `私募增資` | 2026 約 NT$790 億策略投資，引進 SanDisk、Solidigm、Cisco、Kioxia |
| `Value Net` | 顧客、互補者、競爭者與投資者共同塑造南亞科策略 |
| `KBV` | 製程知識與驗證經驗是可累積能力 |
| `Real Option` | 新廠與產品升級保留未來擴張選擇權 |

刪除或改寫：
- 不得在字卡寫 TSMC／Vera Rubin 合作。
- 不得寫 Cisco／Solidigm 已簽 DRAM 供應長約。

#### 測驗替換建議

至少保留五題，改成與視覺化數據對應：

| 題目重點 | 正解 |
|---|---|
| 2025 南亞科 EPS | 2.13 元 |
| 4Q25 DRAM 市占最高者 | Samsung |
| 2026 計畫 CapEx | 約 500 億元 |
| 128GB DDR5 RDIMM 已完成的里程碑 | 5600/6400 Mb/s 功能驗證 |
| 已公布 DRAM 供應協議的策略投資者 | SanDisk 與 Kioxia |
| 私募事件性質 | 策略私募增資，不是併購 |

---

## 7. JavaScript 資料結構修改指示

目前 `index.html` 透過 `translations`、`interactiveData`、`valueNetData`、`theoryMapData`、`quizData` 與 rendering functions 動態建立內容。修改時請不要只改靜態 HTML，必須同步調整資料物件與 render functions。

### 7.1 建議新增／更新的資料物件

```js
const verifiedFacts = {
  company: { ... },
  financials: { ... },
  dramMarket4Q25: { ... },
  products: { ... },
  milestones: { ... },
  privatePlacement: { ... },
  sources: { ... }
};
```

用途：
- 將同一數據集中保存，避免中文版、英文版、圖表與測驗各自寫死不同數字。
- `translations` 僅保存文案；數值從 `verifiedFacts` 讀取。

建議結構：

```js
const verifiedFacts = {
  company: {
    founded: "1995-03",
    listed: "2000-08",
    stockCode: "2408",
    capitalTwdBn: 34.5,
    capitalAsOf: "2026-04",
    employees: "3,700+"
  },
  fy2025: {
    revenueTwd100m: 665.87,
    netIncomeTwd100m: 66.03,
    eps: 2.13,
    q4RevenueTwd100m: 300.94,
    q4GrossMargin: 49.0,
    q4OperatingMargin: 39.1,
    q4Eps: 3.58
  },
  capex: {
    fy2025ApprovedTwd100m: 196,
    fy2025ActualTwd100m: 134,
    deferredTo2026Twd100m: 62,
    fy2026PlannedTwd100m: 500,
    newFabEquipmentMoveIn: "early 2027"
  },
  market4Q25: {
    industryRevenueUsdBn: 53.58,
    industryQoq: 29.4,
    conventionalContractPriceQoqRange: [45, 50],
    conventionalContractPrice1Q26ForecastRange: [90, 95],
    vendors: [
      { id: "samsung", revenueUsdBn: 19.30, share: 36.0 },
      { id: "skhynix", revenueUsdBn: 17.22, share: 32.1 },
      { id: "micron", revenueUsdBn: 11.98, share: 22.4 },
      { id: "nanya", revenueUsdBn: 0.97, share: 1.8, shareDerived: true, qoq: 54.7 }
    ]
  },
  privatePlacement: {
    totalTwdBnApprox: 79,
    pricePerShare: 223.9,
    investors: [
      { id: "sandisk", amountTwdBnApprox: 31, supplyAgreement: "multi-year DRAM" },
      { id: "solidigm", amountTwdBnApprox: 16 },
      { id: "cisco", amountTwdBnApprox: 16 },
      { id: "kioxia", amountTwdBnApprox: 16, supplyAgreement: "long-term DRAM", technologyCooperation: "VCT DRAM (2024)" }
    ]
  }
};
```

### 7.2 移除 status 系統

刪除／停止使用下列可見邏輯：

```js
statusLabel(...)
status-chip
status: "confirmed"
status: "inference"
status: "mixed"
status: "unverified"
```

產品 official availability 請使用不同欄位，例如：

```js
availability: "Available"
availability: "In Development"
```

### 7.3 更新既有資料

- `interactiveData.zh.shares` / `interactiveData.en.shares`：改為 4Q25 TrendForce 數據。
- `interactiveData.portfolio`：加入 `ddr5-rdimm` 與 `mcp`，並更新 LPDDR5、KGD 內容為官方規格。
- `valueNetData`：依第 6.7 節重建，不包含 ASML、TSMC 或 status 欄。
- `translations.zh.companyRow1Body` / `translations.en.companyRow1Body`：資本額更新為 345 億／NT$34.5B as of April 2026。
- `interactiveData.finance`：新增 `capex` 頁籤。
- `quizData`：改為已查證數據題。
- `flipCards`：新增私募、RDIMM、KBV、Real Option；移除沒有可靠來源的具名合作敘述。

---

## 8. 來源呈現設計

### 8.1 每個圖表旁的來源抽屜

每個視覺化 component 加 `<details class="source-note">`，預設收合：

```html
<details class="source-note">
  <summary>來源 / Sources</summary>
  <p>南亞科技官方 2025 Q4 財務結果，2026/01/19。</p>
</details>
```

### 8.2 `#integrity` 總來源清單新增以下來源

請加入可點擊連結，並在雙語文案中對應：

1. Nanya Technology — Investor Relations — Company Profile  
   `https://www.nanya.com/en/IR/35/Company%20Profile`
2. Nanya Technology — Nanya Technology Reports Results for the Fourth Quarter 2025 — 2026/01/19  
   `https://www.nanya.com/en/IR/16/Press%20Release?IRId=11068`
3. Nanya Technology — Corporate Milestone  
   `https://www.nanya.com/en/About/27/Corporate%20Milestone`
4. Nanya Technology — DDR5 Product List  
   `https://www.nanya.com/en/Product/List/450/2478`
5. Nanya Technology — LPDDR5/5X Product List  
   `https://www.nanya.com/en/Product/List/547/6587`
6. Nanya Technology — KGD LPDDR5/5X Product List  
   `https://www.nanya.com/en/Product/List/452/6587`
7. Nanya Technology — RDIMM Product List  
   `https://www.nanya.com/en/Product/List/2418/7610`
8. TrendForce — 漲價帶動4Q25 DRAM產業營收季增29.4%，Samsung重返市占率第一 — 2026/02/26  
   `https://www.trendforce.com.tw/presscenter/news/20260226-12938.html`
9. Reuters — Nanya Technology shares surge 10% after $2.5 billion fundraising — 2026/03/26  
   `https://www.reuters.com/world/asia-pacific/nanya-technology-shares-surge-10-after-25-billion-private-placement-2026-03-26/`

### 8.3 AI 揭露保留並補充

保留既有 AI 使用揭露，增加一句：

中文：
> 外部數據以官方投資人關係、官方產品資料、TrendForce 與 Reuters 交叉核對後呈現；課堂策略模型與公司已發布事實分開標示。

英文：
> External data are presented after cross-checking official investor-relations materials, official product information, TrendForce, and Reuters; classroom strategy models are distinguished from published company facts.

---

## 9. 視覺與互動規格

### 9.1 圖表原則

- 全部使用原生 HTML/CSS/SVG/JavaScript。
- 不引入 Chart.js、D3、外部圖示 CDN 或遠端圖片。
- 色彩延續現有網站變數與深綠／海軍藍／珊瑚橘基調。
- 各圖表必須支援 dark mode。
- 圖表內容必須可被語音導覽讀到：每張圖旁應有隱藏或可見文字摘要；不可只靠 SVG 圖形傳達資訊。
- 手機版圖表不可水平溢出造成頁面破版；表格需可橫向捲動或轉為卡片。

### 9.2 建議視覺元件清單

| 既有 section | 元件 | 互動 |
|---|---|---|
| Hero | KPI cards + mini SVG trend | 切換 Revenue / EPS / CapEx |
| Company | Event timeline | 點擊年份更新 detail |
| Market / Industry | Horizontal revenue/share bars | Hover / click 顯示公司數據 |
| Market / Five Forces | Five force controls | 點擊顯示數字／判讀／策略 |
| Market / STP | Segment matrix | 點擊市場顯示產品與定位 |
| Market / PESTEL | Six signal cards | 點擊展開來源與策略讀法 |
| Finance | Indicator tabs + CapEx bar + fab timeline | 切換指標 |
| Portfolio | Quadrant scatter + product detail | 點擊產品點位 |
| Resources | Value Chain flow + VRIN | 點擊流程節點 |
| Growth | Private placement donut/stacked bar + Value Net | 點擊投資者／競爭者 |
| Career | Capability linkage | 靜態簡潔對應 |
| Quiz | Updated verified-data questions | 作答回饋 |

---

## 10. 文字密度要求

請控制主頁文字量：

| 元件 | 字數／行數限制 |
|---|---|
| Section lead | 中文最多 42 字；英文最多 20 words |
| KPI card | 數值＋一行標籤 |
| 圖表策略判讀 | 中文最多 45 字；英文最多 22 words |
| Detail card | 三欄或三行，每行最多 32 中文字 |
| Five Forces detail | 固定三列：數字／判讀／回應 |
| STP detail | 固定三列：需求／依據／定位 |
| Product detail | 規格＋應用＋4P 微卡，不寫段落 |
| Source note | 預設收合 |

不要將五份 Markdown 原文直接貼入 UI，也不要在畫面呈現大段理論歷史說明。

---

## 11. 驗收標準

### 11.1 內容完整性

完成後，五份資料至少需在網站中有以下落點：

| 本地分析檔案 | 必須可在網站找到的內容 |
|---|---|
| `STP+4P.md` | STP 市場矩陣＋產品 detail 中的 4P 微卡＋B2B 定位 |
| `競合策略.md` | Value Net＋私募投資視覺＋SanDisk/Kioxia 已公布供應合作＋競爭者市占 |
| `五力分析+pestel.md` | 五力互動＋完整 PESTEL 六卡＋DRAM 產業市占與價格循環數據 |
| `價值鏈分析+知識基礎觀點.md` | Value Chain 流程＋KBV 理論連結＋人才／製程／驗證對應 |
| `投資組合策略+資本配置.md` | 產品象限＋CapEx/New Fab 頁籤＋Ansoff／Real Option 角標或情境模型 |

### 11.2 資料正確性

- 頁面不可再顯示資本額 `309.9 億元`。
- 頁面不可再顯示舊的 DRAM 市占排列 `SK hynix 36.0%、Samsung 33.7%、Micron 24.3%、Nanya 0.81%`。
- 頁面不可包含 `TSMC / Vera Rubin / LPDDR5X` 南亞科合作說法。
- 頁面不可包含 `EUV 已裝機` 或 `ASML 與南亞科已確認直接合作`。
- 頁面不可包含 `Cisco / Solidigm 已簽 DRAM 長約`。
- 頁面不可包含 `私募 = 併購`。
- 頁面不可出現使用者可見的 `推論／待核實／confirmed/inference/mixed/unverified` 標籤。
- 頁面可顯示官方產品 availability：`Available`、`In Development`。

### 11.3 功能驗收

修改完成後自行測試：

1. 開啟 `index.html`，預設繁體中文內容正常。
2. 切換英文後，新增元件完整翻譯，數值一致。
3. 明暗模式下所有新圖表對比清楚。
4. 語音導覽可以讀到圖表文字摘要，不朗讀隱藏程式碼或重複資料。
5. 五力、STP、產品象限、財務頁籤、Value Net、時間軸均可點擊運作。
6. 測驗重新開始、下一題與計分運作正常。
7. 手機寬度 375px 下無破版、無不可操作元件。
8. 所有來源連結可點擊，並以 `target="_blank"`、`rel="noreferrer"` 處理。
9. 檢查頁面全文不存在以下字串：
   ```text
   推論
   待核實
   mixed
   unverified
   Vera Rubin
   EUV 裝機
   長鑫存儲已取得
   已打入 NVIDIA
   ```
   `In Development` 不在禁用清單中，因其為官方產品狀態。

---

## 12. 建議實作順序

請依下列順序工作，避免一次重寫整頁造成既有功能損壞：

1. 讀取 `index.html` 與五份 Markdown，記錄現有 component id、translations keys、render functions。
2. 建立 `verifiedFacts` 單一資料物件。
3. 更新公司資料、Hero KPI 與 footer 更新日期／來源說明。
4. 替換 market share 數據，完成 Market / Industry 圖表。
5. 新增 Market / STP 與完整 PESTEL 六卡。
6. 新增 Finance / CapEx 頁籤與新廠時程。
7. 擴充 Portfolio 六產品點位及 4P 微卡。
8. 將 Resources 能力流程重構為 Value Chain × KBV。
9. 重構 Growth 的私募投資視覺與 Value Net。
10. 更新 flip cards 與 quiz。
11. 更新 `#integrity` 來源與 AI 揭露。
12. 移除所有 status chip 與未查證節點。
13. 全面測試中英文、dark mode、voice guide、mobile layout、互動與來源連結。

---

## 13. 完成回報格式

完成修改後，請回報：

```markdown
## 已修改項目
- [ ] Hero KPI 更新
- [ ] Company strategy timeline
- [ ] Market Industry / STP / PESTEL tabs
- [ ] Finance CapEx / New Fab tab
- [ ] Portfolio six-product map + 4P cards
- [ ] Value Chain × KBV flow
- [ ] Private placement + Value Net redesign
- [ ] Career capability linkage
- [ ] Flip cards / quiz update
- [ ] Sources / AI disclosure update
- [ ] Removed unverified visible claims and status chips

## 資料校正
- 舊值 → 新值清單
- 移除的未查證內容清單

## 測試
- Language toggle:
- Theme toggle:
- Voice guide:
- Desktop layout:
- Mobile layout:
- Interactive components:
- Source links:

## 修改檔案
- `index.html`
```

---

## 14. 不要做的事

- 不要另建五個長篇分析頁。
- 不要把 Markdown 原文整段複製到 UI。
- 不要自行新增尚未查證的 AI 客戶、NVIDIA／TSMC 合作、設備採購或長約年限。
- 不要把模型假設寫成已發布數據。
- 不要為了增加內容量而犧牲網站清晰度。
- 不要移除既有的雙語、dark mode、語音導覽、翻轉卡、測驗、RWD 或來源揭露功能。
