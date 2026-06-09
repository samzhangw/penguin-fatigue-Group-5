# PulseAI | 智能辦公健康助理 🛡️

![Status](https://img.shields.io/badge/Status-Active-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Flask](https://img.shields.io/badge/Framework-Flask-lightgrey)
![AI](https://img.shields.io/badge/AI-MediaPipe%20%7C%20NVIDIA%20NIM-green)

**PulseAI** 是一款結合邊緣運算（Edge AI）、物聯網推播與生成式 AI 的全端健康管理系統，專為長時間久坐的上班族、遠距工作者及學生設計。透過電腦視覺即時監測坐姿與疲勞狀態，搭配番茄鐘與 AI 健康教練，打造零穿戴設備的智慧健康防護系統。

---

# ✨ 核心功能

## 🍅 智能番茄鐘與防摸魚機制

* 支援 25 分鐘標準模式
* 52 分鐘護眼模式
* 90 分鐘深度工作模式
* 自訂工作時間

### 離席偵測

若專注期間離開鏡頭超過 120 秒：

* 自動判定番茄鐘失敗
* 記錄摸魚時間
* 加入每日報告
* AI 教練進行嚴厲評語

---

## 👁️ Edge AI 即時健康偵測

### 剛性特徵測距（IOD）

利用雙眼瞳孔間距（Inter-Pupillary Distance）估算與螢幕距離，相較臉部寬高比更不受表情影響。

### 疲勞監測

#### Eye Aspect Ratio (EAR)

偵測：

* 長時間閉眼
* 頻繁眨眼
* 疲勞狀態

#### Mouth Aspect Ratio (MAR)

結合嘴巴高度與寬度比例：

* 打哈欠
* 摀嘴動作
* 過濾講話誤判

#### 高低肩監測

利用 MediaPipe Pose：

* 計算肩膀水平斜率
* 偵測姿勢歪斜

#### 環境亮度監測

利用灰階平均值：

* 光線過暗提醒
* 保護視力

---

## 🤸 AI 運動引導

完成番茄鐘後進入強制休息：

### 1. 手部伸展

* 握拳
* 張開

### 2. 頸部伸展

* 左轉
* 右轉

### 3. 肩臂伸展

* 雙手高舉
* 舒展肩頸

---

## 🧠 NVIDIA GenAI 毒舌教練

串接：

* NVIDIA NIM
* Llama 3.1 8B
* Llama 3.1 70B

根據：

* 專注時數
* 摸魚時間
* 高低肩次數
* 疲勞狀況

生成客製化健康分析與毒舌評語。

---

## ☁️ 雲端同步

### Supabase

儲存：

* 健康資料
* 番茄鐘紀錄
* 使用者統計

### Discord Webhook

每日自動推播：

* 日報
* 週報
* 成就稱號

例如：

* 薪水小偷
* 過勞社畜
* 入定高僧
* 超級卷王

---

# 🏗 系統架構

```text
WebCam
   ↓
OpenCV + MediaPipe
   ↓
健康特徵分析
(EAR、MAR、IOD、Pose)
   ↓
EMA + IQR Filter
   ↓
system_state
   ↓
Flask-SocketIO
   ↓
Dashboard
   ↓
Supabase
   ↓
Discord
   ↓
NVIDIA NIM
```

---

# 🛠 技術架構

## 後端

* Python 3
* Flask
* Flask-SocketIO
* Threading

## 前端

* HTML5
* Tailwind CSS
* JavaScript
* Chart.js

## AI 與影像處理

* OpenCV
* MediaPipe Face Mesh
* MediaPipe Hands
* MediaPipe Pose
* NumPy

## 資料處理

* EMA Filter
* IQR Filter

## 雲端服務

* Supabase PostgreSQL
* Discord Webhook
* NVIDIA NIM API

---

# 📂 專案目錄

```text
PulseAI/
│
├── app.py
├── README.md
├── .env
├── requirements.txt
│
├── templates/
│     └── index.html
│
├── static/
│     ├── css/
│     │     └── style.css
│     │
│     ├── js/
│     │     └── main.js
│     │
│     ├── img/
│     │     ├── logo.png
│     │     ├── dashboard.png
│     │     └── exercise.png
│     │
│     └── audio/
│           ├── alert.wav
│           └── finish.wav
│
├── models/
├── reports/
├── logs/
└── data/
```

---

# 🚀 Quick Start

## 安裝需求

Python 3.8+

需要：

* Webcam
* 麥克風（選配）

---

## 安裝套件

```bash
pip install opencv-python mediapipe numpy requests flask flask-socketio python-dotenv supabase
```

---

## 建立 .env

```env
NVIDIA_API_KEY=your_nvidia_api_key

SUPABASE_URL=your_project_url
SUPABASE_KEY=your_anon_key

DISCORD_WEBHOOK=your_webhook_url
```

---

## 啟動系統

```bash
python app.py
```

預設網址：

```text
http://127.0.0.1:5001
```

---

# 🧪 核心演算法

## EAR

```text
EAR =
(||p2-p6|| + ||p3-p5||)
/ 2||p1-p4||
```

用途：

* 疲勞
* 閉眼

---

## MAR

```text
MAR =
mouth_height
/
mouth_width
```

用途：

* 打哈欠
* 摀嘴

---

## EMA Filter

```python
ema = alpha * current + (1-alpha) * previous
```

降低感測抖動。

---

## IQR Filter

移除異常值：

```python
Q1 = percentile(data,25)
Q3 = percentile(data,75)

IQR = Q3-Q1

lower = Q1 - 1.5*IQR
upper = Q3 + 1.5*IQR
```

---

# 💡 Engineering Highlights

## Thread Safe

多執行緒：

* Flask Server
* AI Detection
* Discord Report
* Scheduler

使用：

```python
state_lock
frame_lock
```

避免 Race Condition。

---

## EMA + IQR

提升穩定性：

* 距離偵測
* 肩膀斜率
* EAR
* MAR

降低誤判。

---

## 嚴格校正

校正時要求：

✅ 坐正

✅ 光線充足

✅ 不遮擋嘴巴

✅ 面向鏡頭

否則拒絕建立基準值。

---

# 📊 Dashboard

顯示：

* 專注時數
* 摸魚時間
* 高低肩次數
* 疲勞指數
* 歷史趨勢
* 成功番茄鐘數

---

# 🔮 Future Work

* YOLOv11 姿勢辨識
* 多使用者模式
* 手機 APP
* Telegram Bot
* Line Notify
* Gemini / GPT 教練模式
* RAG 健康知識庫
* LangChain Agent

---

# 👥 開發團隊

| 編號 | 姓名  | 工作內容            |
| -- | --- | --------------- |
| 14 | 曾仁宥 |       |
| 15 | 吳承誼 |  |
| 22 | 章惟善 |    |
| 33 | 林冠廷 |          |

---

# 📄 License

MIT License

Copyright © 2026 Group 5
