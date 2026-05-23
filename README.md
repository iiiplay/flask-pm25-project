# 🌫️ PM2.5 即時空氣品質監測系統

這是一個基於 Flask 開發的即時空氣品質監測 Web 應用程式，專門用於追蹤與展示台灣各縣市的 PM2.5 數據。透過圖表與數據表格，使用者可以直觀地了解當前的空氣品質狀況。

## 🚀 功能特色

- **即時數據展示**：從資料庫獲取最新的 PM2.5 監測數據。
- **關鍵指標 (KPI)**：自動標示全台 PM2.5 最高與最低的測站。
- **動態圖表視覺化**：
    - 可選擇特定縣市查看各測站的 PM2.5 數值。
    - 一鍵對比「六都」的平均 PM2.5 濃度。
- **響應式設計**：採用現代化的 CSS 樣式與捲軸容器，確保在不同裝置上皆有良好的閱讀體驗。
- **RESTful API**：提供 JSON 格式的數據介面，方便後端數據擴充或前端調用。

## 🛠️ 技術棧

- **後端**: [Flask](https://flask.palletsprojects.com/) (Python)
- **資料處理**: [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/)
- **資料庫**: MySQL (使用 [PyMySQL](https://github.com/PyMySQL/PyMySQL) 連接)
- **前端**: HTML5, CSS3, JavaScript, [Chart.js](https://www.chartjs.org/)
- **部署支援**: Gunicorn

## 📦 安裝與環境設定

### 1. 複製專案
```bash
git clone <repository-url>
cd flask-pm25-project-master
```

### 2. 安裝依賴套件
建議使用虛擬環境 (Virtual Environment)：
```bash
python -m venv venv
# Windows 啟動虛擬環境
venv\Scripts\activate
# macOS/Linux 啟動虛擬環境
source venv/bin/activate

pip install -r requirements.txt
```

### 3. 環境變數設定
在專案根目錄建立 `.env` 檔案，並填入您的資料庫連線資訊：
```env
HOST=您的資料庫主機地址
PORT=3306
USER=您的使用者名稱
PASSWORD=您的密碼
NAME=資料庫名稱
```

### 4. 資料庫準備
請確保您的 MySQL 資料庫中有名稱為 `data` 的資料表，且包含以下欄位（對應程式邏輯）：
- `county`: 縣市名稱
- `sitename`: 測站名稱
- `pm25`: PM2.5 數值
- `datacreationdate`: 資料建立時間

## 🏃 執行程式

開發模式下運行：
```bash
python main.py
```
啟動後，開啟瀏覽器造訪 `http://127.0.0.1:5000` 即可看到頁面。

## 🔗 API 說明

| 端點 | 描述 |
| :--- | :--- |
| `/api/counties` | 取得所有不重複的縣市列表 |
| `/api/data/<county>` | 取得指定縣市的最新各站數據 |
| `/api/data/six-county` | 取得六都（台北、新北、桃園、台中、台南、高雄）的平均 PM2.5 數據 |

## 📝 專案結構
```text
.
├── database.py         # 資料庫連線與查詢邏輯
├── main.py             # Flask 主程式與路由設定
├── requirements.txt    # 專案依賴清單
├── templates/          # HTML 模板檔案
│   ├── index.html      # 首頁與圖表展示
│   └── 404.html        # 錯誤頁面
└── .env                # 環境變數 (需手動建立)
```

## 📜 聲明
本專案資料來源為環境部即時 API。數據僅供參考。
