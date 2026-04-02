# 台股 AI 財經戰情室 🚀

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![React](https://img.shields.io/badge/React-18.x-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript)
![Vite](https://img.shields.io/badge/Vite-6.x-646CFF?logo=vite)

一個即時監控台灣股市新聞情緒的智能分析儀表板，透過 AI 關鍵字演算法自動判讀財經新聞多空傾向，協助投資人快速掌握市場脈動。

## 📋 目錄

- [專案簡介](#專案簡介)
- [核心功能](#核心功能)
- [技術架構](#技術架構)
- [快速開始](#快速開始)
- [演算法說明](#演算法說明)
- [API 整合](#api-整合)
- [專案結構](#專案結構)
- [開發指南](#開發指南)
- [使用說明](#使用說明)
- [注意事項](#注意事項)
- [未來規劃](#未來規劃)

---

## 🎯 專案簡介

台股 AI 財經戰情室是一個專為台灣股市投資人設計的即時新聞情緒分析工具。系統透過 Google Apps Script 爬蟲自動蒐集主流財經媒體的最新報導，並運用關鍵字情緒分析演算法，將新聞自動分類為「利多」、「利空」或「中立」，並計算出 0-100 分的市場情緒指數。

### 🎨 設計理念

- **即時性**：每次刷新都能獲取最新財經新聞
- **視覺化**：直觀的儀表板設計，一眼看懂市場情緒
- **智能化**：AI 關鍵字演算法自動判讀新聞多空傾向
- **輕量級**：純前端實現，無需後端伺服器
- **響應式**：完美適配桌面端與移動端

---

## ✨ 核心功能

### 1. 📰 即時新聞爬蟲
- 自動抓取 **4 大主流財經媒體**：
  - 自由財經 (ltn)
  - 聯合新聞網 (udn)
  - Yahoo 財經 (yahoo)
  - ETtoday 財經 (ettoday)
- 即時更新，點擊按鈕即可同步最新資料
- API 連線失敗時自動切換至備用資料

### 2. 🤖 AI 情緒分析
- **關鍵字字典**：內建 40+ 個多空關鍵字
  - 利多關鍵字：創新高、漲停、買進、擴產、外資喊進等
  - 利空關鍵字：創新低、跌停、裁員、賣出、虧損等
- **智能評分**：每個關鍵字賦予不同權重（1-3 分）
- **自動分類**：根據總分自動判定新聞情緒

### 3. 📊 市場情緒指數
- **0-100 分制**：量化市場整體情緒
- **動態指針儀表板**：視覺化呈現當前市場氛圍
  - 65+ 分：市場樂觀 🔴
  - 55-64 分：偏向多方 🟠
  - 45-54 分：中立觀望 ⚪
  - 36-44 分：偏向空方 🟢
  - 0-35 分：市場悲觀 🟢
- **即時動畫**：指針平滑轉動，增強視覺反饋

### 4. 📈 情緒分布統計
- 利多新聞數量
- 利空新聞數量
- 中立新聞數量
- 直觀的卡片式呈現

### 5. 🎨 精美 UI/UX
- **響應式設計**：完美適配各種螢幕尺寸
- **Tailwind CSS**：現代化設計語言
- **Lucide Icons**：精美圖標庫
- **Loading 動畫**：骨架屏載入效果
- **Hover 效果**：豐富的互動反饋

---

## 🛠 技術架構

### 前端技術棧

```
├── React 18.x          # UI 框架
├── TypeScript 5.x      # 類型安全
├── Vite 6.x           # 極速建構工具
├── Tailwind CSS       # 樣式框架 (CDN)
└── Lucide React       # 圖標庫
```

### 後端服務

```
Google Apps Script API
└── 爬蟲服務
    ├── 定時抓取財經新聞
    ├── 資料清洗與格式化
    └── JSON API 輸出
```

### 核心演算法

```typescript
情緒分析引擎
├── 關鍵字匹配
├── 權重計算
├── 分數歸一化
└── 情緒分類
```

---

## 🚀 快速開始

### 環境需求

- Node.js 18+ 
- npm 或 yarn

### 安裝步驟

```bash
# 1. 克隆專案
git clone <repository-url>
cd taiwan-stock-sentiment

# 2. 安裝依賴
npm install

# 3. 啟動開發伺服器
npm run dev

# 4. 開啟瀏覽器
# 訪問 http://localhost:5173
```

### 建構生產版本

```bash
# 建構
npm run build

# 預覽
npm run preview
```

---

## 🧠 演算法說明

### 情緒分析演算法流程

```
新聞標題
    ↓
關鍵字匹配
    ↓
加權計分 (score)
    ↓
情緒分類
    ├─ score >= 2  → bullish (利多)
    ├─ score <= -2 → bearish (利空)
    └─ 其他        → neutral (中立)
    ↓
市場指數計算
```

### 關鍵字權重系統

#### 利多關鍵字 (Bullish)

| 關鍵字 | 權重 | 說明 |
|--------|------|------|
| 創新高 | 3 | 強烈利多信號 |
| 漲停 | 3 | 強烈利多信號 |
| 外資喊進 | 3 | 強烈利多信號 |
| 創紀錄 | 3 | 強烈利多信號 |
| 大漲 | 2 | 中度利多 |
| 優於預期 | 2 | 中度利多 |
| 買進 | 2 | 中度利多 |
| 強勁 | 2 | 中度利多 |
| 供不應求 | 2 | 中度利多 |
| 上修 | 2 | 中度利多 |
| 擴產 | 1 | 輕度利多 |
| 旺季 | 1 | 輕度利多 |
| 獲利 | 1 | 輕度利多 |

#### 利空關鍵字 (Bearish)

| 關鍵字 | 權重 | 說明 |
|--------|------|------|
| 創新低 | -3 | 強烈利空信號 |
| 跌停 | -3 | 強烈利空信號 |
| 下修 | -3 | 強烈利空信號 |
| 不如預期 | -2 | 中度利空 |
| 重挫 | -2 | 中度利空 |
| 賣出 | -2 | 中度利空 |
| 裁員 | -2 | 中度利空 |
| 升息 | -2 | 中度利空 |
| 虧損 | -2 | 中度利空 |
| 衰退 | -2 | 中度利空 |
| 通膨 | -1 | 輕度利空 |
| 保守 | -1 | 輕度利空 |

### 市場指數計算公式

```typescript
// 1. 計算所有新聞的總分數
totalScore = Σ(每則新聞的情緒分數)

// 2. 歸一化至 0-100 區間
normalizedScore = 50 + (totalScore × 3)

// 3. 限制範圍
marketScore = Math.min(100, Math.max(0, normalizedScore))
```

**計算範例**：
- 假設有 10 則新聞
- 利多新聞 5 則，平均分數 +2 → 總計 +10
- 利空新聞 3 則，平均分數 -2 → 總計 -6
- 中立新聞 2 則，分數 0 → 總計 0
- totalScore = 10 - 6 = 4
- marketScore = 50 + (4 × 3) = 62 (偏向多方)

---

## 🔌 API 整合

### Google Apps Script API

#### 端點資訊
```
URL: https://script.google.com/macros/s/AKfycbwl67_kmGSwBLy3pRqK2W0DZwLgN3Q7cNCDqPr1sucWvUPEr08lFV6IdGazexDmM6ZEXg/exec
Method: GET
Response: JSON
```

#### 回應格式

```json
{
  "news": [
    {
      "source": "ltn",
      "sourceName": "自由財經",
      "title": "焦點股》台積電：先進製程 客戶需求強勁",
      "link": "https://...",
      "timestamp": "2025-11-25 11:15:28"
    },
    ...
  ]
}
```

#### 資料欄位說明

| 欄位 | 類型 | 說明 |
|------|------|------|
| source | string | 來源代碼 (ltn/yahoo/udn/ettoday) |
| sourceName | string | 來源中文名稱 |
| title | string | 新聞標題 |
| link | string | 新聞連結 |
| timestamp | string | 發布時間 |

### 備用資料機制

當 API 連線失敗時，系統會自動切換至內建的備用資料 (`FALLBACK_DATA`)，確保應用程式正常運作。

```typescript
try {
  const response = await fetch(API_URL);
  // 處理 API 資料
} catch (error) {
  // 自動使用備用資料
  processRawData(FALLBACK_DATA);
  setDataSourceType("備用資料 (API連線受阻)");
}
```

---

## 📁 專案結構

```
taiwan-stock-sentiment/
├── public/              # 靜態資源
├── src/
│   ├── assets/         # 圖片、SVG 等資源
│   │   └── react.svg
│   ├── App.tsx         # 主應用程式組件 ⭐
│   ├── App.css         # 應用程式樣式
│   ├── main.tsx        # 應用程式入口
│   └── index.css       # 全域樣式
├── index.html          # HTML 模板
├── package.json        # 專案配置
├── tsconfig.json       # TypeScript 配置
├── vite.config.ts      # Vite 配置
└── README.md           # 專案說明文件
```

### 核心檔案說明

#### `src/App.tsx` - 主應用程式 (約 500 行)

```typescript
// 主要組件
├── TaiwanStockSentimentApp  # 主容器
├── MarketScoreGauge          # 市場情緒儀表板
└── NewsCard                  # 新聞卡片

// 主要函數
├── analyzeNewsSentiment()    # 情緒分析
├── processRawData()          # 資料處理
└── fetchAndAnalyzeData()     # API 抓取
```

#### `src/App.css` - 樣式定義

包含所有自定義樣式：
- 頁面佈局
- 按鈕樣式
- 卡片樣式
- 情緒標籤
- 響應式設計

#### `index.html` - HTML 模板

重要配置：
```html
<!-- Tailwind CSS CDN -->
<script src="https://cdn.tailwindcss.com"></script>
```

---

## 👨‍💻 開發指南

### 本地開發

```bash
# 啟動開發伺服器
npm run dev

# 自動開啟瀏覽器並啟用熱重載
```

### 程式碼規範

- 使用 TypeScript 嚴格模式
- 遵循 React Hooks 最佳實踐
- 組件使用函數式寫法
- CSS 類名遵循 Tailwind 規範

### 新增關鍵字

在 `src/App.tsx` 中修改關鍵字字典：

```typescript
// 新增利多關鍵字
const BULLISH_KEYWORDS = [
  ...
  { word: "新關鍵字", score: 2 }
];

// 新增利空關鍵字
const BEARISH_KEYWORDS = [
  ...
  { word: "新關鍵字", score: -2 }
];
```

### 調整情緒閾值

修改 `analyzeNewsSentiment` 函數：

```typescript
let sentiment: 'bullish' | 'bearish' | 'neutral' = 'neutral';
if (score >= 2) sentiment = 'bullish';  // 調整此值
if (score <= -2) sentiment = 'bearish'; // 調整此值
```

### 自定義 API

替換 API 端點：

```typescript
const API_URL = "你的 API 網址";
```

確保 API 回應格式符合專案需求。

---

## 📖 使用說明

### 基本操作

1. **開啟應用程式**
   - 訪問部署後的網址或本地開發伺服器

2. **查看市場情緒**
   - 頁面左側顯示當前市場情緒指數
   - 指針指向對應的情緒區間

3. **瀏覽即時新聞**
   - 頁面右側列出最新財經新聞
   - 每則新聞標註情緒類型與分數

4. **更新資料**
   - 點擊右上角「更新即時新聞」按鈕
   - 系統自動抓取最新資料並重新分析

### 新聞卡片解讀

```
┌─────────────────────────────────────┐
│ 📰 自由財經  11:15                   │
│                                     │
│ 焦點股》台積電：先進製程 客戶需求強勁  │  🔴 利多
│                                     │    +3
│ #強勁 #需求                          │
└─────────────────────────────────────┘
```

- **來源標籤**：新聞來源媒體
- **時間戳**：發布時間
- **標題**：可點擊跳轉至原文
- **關鍵字標籤**：匹配到的情緒關鍵字
- **情緒指標**：利多/利空/中立
- **情緒分數**：該則新聞的量化分數

### 情緒分布

左側下方顯示當前新聞的情緒分布：
- 🔴 利多：看漲新聞數量
- 🟢 利空：看跌新聞數量
- ⚪ 中立：中性新聞數量

---

## ⚠️ 注意事項

### 免責聲明

> **重要提醒**：本系統僅供參考，不構成任何投資建議。
> 
> - 情緒分析結果基於關鍵字匹配，可能存在誤判
> - 新聞情緒不等於股價走勢
> - 投資有風險，決策需謹慎
> - 請勿將本工具作為唯一的投資依據

### 技術限制

1. **關鍵字局限性**
   - 僅能識別預設關鍵字庫中的詞彙
   - 無法理解複雜語境和反諷
   - 中文分詞可能影響匹配準確度

2. **資料延遲**
   - 新聞更新頻率取決於 API 爬蟲
   - 非即時逐秒級更新
   - 手動刷新才能獲取最新資料

3. **API 依賴**
   - 需要穩定的網路連線
   - Google Apps Script 有使用配額限制
   - API 失效時僅能使用備用資料

### 瀏覽器兼容性

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

---

## 🚧 未來規劃

### 功能優化

- [ ] 新增更多財經媒體來源
- [ ] 整合社群媒體情緒 (PTT、Dcard)
- [ ] 歷史數據圖表 (情緒走勢)
- [ ] 個股新聞篩選
- [ ] 自定義關鍵字管理
- [ ] 情緒警報通知

### 技術升級

- [ ] 使用 NLP 模型提升分析準確度
- [ ] WebSocket 實現真正即時推送
- [ ] 後端 API 服務化
- [ ] 資料庫持久化儲存
- [ ] 使用者帳號系統
- [ ] PWA 支援 (離線使用)

### UI/UX 改進

- [ ] 暗黑模式
- [ ] 多語言支援
- [ ] 更多視覺化圖表
- [ ] 關鍵字雲圖
- [ ] 自定義主題配色

---

## 📄 授權

本專案採用 MIT 授權條款

---

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

1. Fork 本專案
2. 創建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

---

## 📧 聯絡資訊

如有問題或建議，歡迎透過以下方式聯繫：

- 📮 Email: your-email@example.com
- 💬 GitHub Issues: [提交問題](https://github.com/your-username/your-repo/issues)

---

## 🙏 致謝

- React 團隊提供優秀的框架
- Vite 提供極速開發體驗
- Tailwind CSS 提供現代化樣式方案
- Lucide 提供精美圖標庫
- 所有財經媒體提供資訊來源

---

<p align="center">
  Made with ❤️ by Taiwan Stock AI Team
</p>

<p align="center">
  ⭐ 如果這個專案對你有幫助，請給我們一顆星！
</p>