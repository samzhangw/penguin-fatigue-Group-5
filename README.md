# PulseAI | 智能辦公健康助理 🛡️

**PulseAI** 是一款結合邊緣運算（Edge AI）、物聯網（IoT）推播與生成式 AI（GenAI）的全端健康管理系統。專為長時間久坐的上班族與學生設計，透過電腦視覺即時監測使用者的坐姿與疲勞狀態，結合番茄鐘工作法與 AI 健康教練，打造全方位的智慧健康防護網。

---

## ✨ 核心功能（Features）

### 🍅 智能番茄鐘與運動引導

* 內建專注模式（Pomodoro Technique）。
* 工作階段結束後自動切換至運動模式。
* 引導使用者進行 Knuckle Stretch、Neck Stretch 等伸展動作。
* 利用 AI 即時判定動作正確性並提供回饋。

### 👁️ 邊緣運算即時健康偵測（Edge AI Vision）

* **剛性特徵測距（IOD）**

  * 採用瞳孔間距（Interocular Distance, IOD）取代傳統臉部佔比估算距離。
  * 提升不同鏡頭環境下的穩定性與準確度。

* **姿勢嚴格校正（Strict Calibration）**

  * 初始化階段強制執行肩膀水平基準檢測。
  * 建立個人化且可靠的健康監測基準值。

* **多維度健康監測**

  * 眼部疲勞偵測（EAR）
  * 打哈欠偵測（MAR）
  * 肩膀傾斜度分析（Postural Slope）
  * 環境光線監測

### ☁️ 雲端同步與數據儀表板

* 使用 Supabase 儲存歷史健康資料。
* 支援每日與每週健康報告生成。
* 透過 Discord Webhook 自動推送健康分析結果。

### 🧠 生成式 AI 健康洞察

* 串接 NVIDIA NIM（Gemma / Llama 3.1）。
* 提供個人化健康建議與工作習慣改善方案。
* 根據使用者歷史紀錄生成專屬健康報告。

---

## 🛠️ 技術架構（Tech Stack）

### 後端

* Python 3
* Flask
* Flask-SocketIO（WebSocket 即時通訊）
* Thread Lock（執行緒安全機制）

### 前端

* HTML5
* Tailwind CSS
* JavaScript

### 電腦視覺

* OpenCV
* MediaPipe

  * Face Mesh
  * Hands
  * Pose

### 雲端服務

* Supabase
* Discord Webhook
* NVIDIA NIM API

---

## 🚀 安裝與執行

### 1. 系統需求

* Python 3.8 以上
* Webcam 攝影機

### 2. 安裝套件

```bash
pip install opencv-python numpy requests mediapipe openai Flask flask-socketio python-dotenv supabase
```

### 3. 環境變數設定

建立 `.env` 檔案：

```env
NVIDIA_API_KEY=your_key_here
SUPABASE_URL=your_url_here
SUPABASE_KEY=your_key_here
```

### 4. 啟動系統

```bash
python app.py
```

---

## 💡 工程設計亮點（Engineering Highlights）

### Thread-Safe Architecture

* 導入 `state_lock` 保護全域狀態。
* 降低多執行緒競爭條件（Race Condition）風險。

### Robust Vision System

* 採用 IOD 剛性特徵進行距離估測。
* 有效降低光線、鏡頭角度與臉型差異造成的誤差。

### Strict Calibration

* 強制肩膀水平校正機制。
* 提升長期健康數據的可信度與一致性。

### Capsule UX Design

* 圓潤膠囊式介面設計。
* 支援置頂懸浮視窗。
* 提供低干擾、高效率的辦公健康體驗。

---

## 👥 開發團隊（Team Members）

| 組員編號 | 姓名  |
| ---- | --- |
| 14   | 曾仁宥 |
| 15   | 吳承誼 |
| 22   | 章惟善 |
| 33   | 林冠廷 |

---

## 📜 License

本專案僅供學術研究與競賽展示用途。
