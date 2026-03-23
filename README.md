# ARIA v2.0：花蓮縣避難收容處所地形風險自動化分析系統 🗺️
> **Automated Risk Intelligence Analyst (ARIA) - Phase II**

## 📖 專案簡介
本專案為針對台灣花蓮縣 198 處避難收容處所開發之「地形風險自動化分析系統」。系統整合 Python 空間運算工具、GeoPandas 幾何處理及 NumPy Gradient 坡度演算法，落實環境配置分離、精準座標重投影與多準則風險判定，完整符合作業 Requirement B/C/D 之各項技術指標。

## 🚀 核心技術亮點 (Captain's Log)
* **🌐 環境自適應引擎 (Adaptive Engine)**：自動偵測 Google Colab 與 Local 環境，動態切換工作目錄並背景安裝依賴套件，解決路徑硬編碼問題。
* **🔤 字體強硬註冊技術**：克服 Linux/雲端環境中文字體缺失痛點，建立自動下載與檔案毀損驗證機制，達成 100% 零警告、全中文化視覺化產出。
* **📐 高精度空間運算**：
    * **座標對齊**：全面採用 `EPSG:3826` (TWD97 121 分帶) 確保 500m 緩衝區運算之物理精確度。
    * **地形微分分析**：利用 `NumPy Gradient` 演算法從 20m 解析度網格中提取地表坡度特徵。
    * **分區統計 (Zonal Stats)**：執行空間聚合運算，提取避難所暴露範圍內的最大風險指標。

## 📊 成果展示
### 1. 地理視覺化地圖
![Terrain Risk Map](terrain_risk_map.png)
*(註：若無法顯示圖片，請確認已執行 Notebook 產出圖檔)*

### 2. 多準則風險判定摘要
根據系統演算，花蓮縣 198 處點位風險分佈如下：
* **Extreme High (極高風險)**: 51 筆 (近河川且地處陡坡，需優先關注)
* **High (高風險)**: 73 筆
* **Medium (中等風險)**: 22 筆
* **Low (低風險)**: 52 筆 (位於平原且遠離水系)

## 🛠️ 快速啟動 (Quick Start)
1. Clone 本專案至您的環境。
2. 將 `env_template` 重新命名為 `.env`，並可依需求微調門檻值。
3. 確保 `requirements.txt` 內之套件已安裝。
4. 依序執行 `ARIA_v2.ipynb` 即可自動產出地圖與 `terrain_risk_audit.json` 稽核清單。

## ⚖️ 規範符合性 (Compliance)
- [x] **Requirement B**: 座標重投影 (B-1)、坡度與距離空間運算 (B-2)。
- [x] **Requirement C**: 環境變數配置分離 (C-1)、跨環境自適應路徑 (C-2)。
- [x] **Requirement D**: 結構化 JSON 產出 (D-3)、高品質中文化地圖 (D-4)。