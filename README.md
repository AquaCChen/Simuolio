# Simuolio
# 投資組合策略模擬器（Portfolio Simulator）

以 **[Google Colab](https://colab.research.google.com/) + ipywidgets** 實作的投資組合策略工具，提供：
- 資產配置表（含再平衡建議）
- 10 年回測波動率（年化）與週報酬相關性熱力圖
- 可調參數的蒙地卡羅模擬（結果以 YYYY/MM 顯示）
- 相關性壓力測試（將負相關調整為 0 或 0.5，避免過度樂觀）

> 本專案為開源工具型模板，預設數據僅為示範，請自行填入你的資產與參數。

---

## 功能特色

### 1) 資產配置與再平衡
- 支援最多 12 檔資產
- 每檔可設定：
  - `鎖定`（不參與再平衡）
  - `市值`
  - `目標%`
  - `預期%`
- 表格顯示：
  - `目前%`（市值 / 投資組合總資產）
  - `操作`（買 / 賣 / 持有）
  - `調整後`（再平衡後的目標市值）

### 2) 風險區塊
- `Volatility`：以週報酬計算年化波動，並顯示實際回測年數（至少嘗試 10 年）
- `Correlation Heatmap`：週報酬相關性熱力圖（TradingView 深色風格）

### 3) 壓力測試：負相關處理
有些情境下，負相關可能使模擬結果過度樂觀，因此提供壓測選項：
- `負相關→0（保守）`
- `負相關→0.5（更保守）`
- `保持原樣`

> 注意：此處是「壓力測試假設」，並非統計學上唯一正確做法。

### 4) 蒙地卡羅模擬
- X 軸使用 YYYY/MM 顯示（可設定起始年月）
- 顯示中位數 / 悲觀線 / 門檻線（可視為目標/預算門檻）

---

## 使用方式（Google Colab）

1. 開啟 Google Colab 新 notebook
2. 將 `Simuolio_colab.py` 的內容貼到一個 cell
3. 執行 cell，等待套件安裝完成
4. 在 UI 中填入你的資產與參數後，按下「🚀 執行運算」

---

## Ticker 格式（非常重要）

本專案使用 `yfinance` 抓取行情，Ticker 必須符合 Yahoo Finance 規則，例如：

- 台股上市：`2330.TW`
- 台股上櫃：`xxxx.TWO`
- 美股 / ETF：`VT`、`XAR`
- 現金可用：`CASH` 或 `現金`（不會抓行情）

---

## 免責聲明（Disclaimer）

本工具僅供教育、研究與壓力測試用途，**不構成任何投資建議**。  
使用者須自行承擔任何交易、投資、財務決策之風險與後果。

---

## 授權（License）

建議使用 **MIT License**。  
你可以在 GitHub 建 repo 時選擇 `MIT License`，並保留作者與 copyright。

---

## 貢獻（Contributing）

歡迎：
- 回報問題（Issues）
- 提 PR 改善 UI/效能/統計方法
- 增加新的風險指標（例如 CVaR、stress scenario、jump risk 等）

---

## 致謝

- pandas / numpy / plotly / seaborn / ipywidgets
- yfinance（Yahoo Finance 資料來源）
