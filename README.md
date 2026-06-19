#小企鵝陪你工作 🛡️

![Status](https://img.shields.io/badge/Status-Active-success)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Flask](https://img.shields.io/badge/Framework-Flask-lightgrey)
![AI](https://img.shields.io/badge/AI-MediaPipe%20%7C%20NVIDIA%20NIM-green)

## 🚀 專案簡介

PulseAI 是一套結合 Edge AI、Computer Vision 與 Generative AI 的智慧辦公健康助理，專為長時間久坐的上班族、遠距工作者及學生設計。

系統透過 Webcam 即時分析使用者的坐姿、疲勞程度、離席狀況與工作專注度，並結合番茄鐘管理、健康運動引導、Discord 推播及 NVIDIA NIM 大語言模型分析，在不需任何穿戴裝置的情況下，提供完整的健康管理與工作效率提升方案。

---

# ✨ 核心特色

✅ Zero Wearable Design（零穿戴設備）

✅ Edge AI 即時健康監測

✅ 智能番茄鐘與防摸魚機制

✅ NVIDIA GenAI 健康教練

✅ Discord 自動推播日報／週報

✅ Supabase 雲端同步

---

# 🏆 創新亮點

## 🔹 Zero Wearable Health Monitoring

不需智慧手環、智慧手錶或額外感測器。

僅透過 Webcam 即可完成：

* 距離監測
* 疲勞偵測
* 高低肩分析
* 專注度分析

---

## 🔹 Edge AI Real-Time Detection

所有影像分析皆於本地端完成：

* OpenCV
* MediaPipe Face Mesh
* MediaPipe Pose
* MediaPipe Hands

降低延遲並保護使用者隱私。

---

## 🔹 AI Health Coach

透過 NVIDIA NIM 與 Llama 3.1：

* 分析專注時數
* 分析疲勞狀況
* 分析摸魚時間
* 提供個人化健康建議

---

## 🔹 Gamification Productivity

將專注時間轉換為實際價值：

例如：

* 累積 1 小時專注
* 換算為努力成果
* 形成正向激勵循環

---

# ✨ 核心功能

## 🍅 智能番茄鐘

支援：

* 25 分鐘標準模式
* 52 分鐘護眼模式
* 90 分鐘深度工作模式
* 自訂工作模式

---

## 🚫 防摸魚機制

### 離席偵測

專注期間若：

* 離開鏡頭超過 120 秒

系統將：

* 判定本次番茄鐘失敗
* 記錄摸魚時間
* 累計失敗次數
* 納入 AI 報告分析

---

## 👁️ Edge AI 健康偵測

### IOD 距離監測

Inter-Ocular Distance

利用雙眼瞳孔間距估算：

* 與螢幕距離
* 過近用眼風險

---

### EAR 疲勞偵測

Eye Aspect Ratio

偵測：

* 閉眼
* 頻繁眨眼
* 疲勞狀態

---

### MAR 打哈欠偵測

Mouth Aspect Ratio

辨識：

* 打哈欠
* 摀嘴動作
* 排除講話誤判

---

### 高低肩監測

利用 Pose Landmarks：

* 計算肩膀斜率
* 偵測姿勢歪斜

---

### 環境亮度監測

利用影像灰階平均值：

* 過暗提醒
* 保護視力

---

# 🤸 AI 運動引導

每次完成番茄鐘後：

強制進入休息模式。

---

## 手部伸展

* 握拳
* 張開手掌

---

## 頸部伸展

* 左轉
* 右轉

---

## 肩頸伸展

* 雙手高舉
* 肩膀放鬆

---

# 🧠 NVIDIA GenAI 健康教練

串接：

* NVIDIA NIM
* Llama 3.1 8B

依據：

* 專注時間
* 摸魚時間
* 疲勞程度
* 高低肩次數

生成：

* 每日健康分析
* 每週健康報告
* 個人化改善建議

---

# ☁️ 雲端同步

## Supabase

儲存：

* 健康數據
* 專注紀錄
* 番茄鐘紀錄
* 歷史統計

---

## Discord Webhook

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
Feature Extraction
(IOD / EAR / MAR / Pose)
   ↓
EMA + IQR Filter
   ↓
System State Manager
   ↓
Flask-SocketIO
   ↓
Dashboard
   ↓
Supabase
   ↓
Discord Report
   ↓
NVIDIA NIM
```

# 🛠 技術架構

## Backend

* Python 3
* Flask
* Flask-SocketIO
* Threading

## Frontend

* HTML5
* Tailwind CSS
* JavaScript
* Chart.js

## Computer Vision

* OpenCV
* MediaPipe Face Mesh
* MediaPipe Pose
* MediaPipe Hands

## Data Processing

* NumPy
* EMA Filter
* IQR Filter

## Cloud Service

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
├── requirements.txt
├── .env
│
├── templates/
│     └── index.html
│
├── static/
│     ├── css/
│     ├── js/
│     ├── img/
│     └── audio/
│
├── reports/
├── logs/
├── data/
└── models/
```

# 🚀 Quick Start

## 安裝需求

* Python 3.8+
* Webcam
* 網路連線

---

## 安裝套件

```bash
pip install opencv-python mediapipe numpy requests flask flask-socketio python-dotenv supabase
```

## 建立 .env

```env
NVIDIA_API_KEY=your_nvidia_api_key

SUPABASE_URL=your_project_url
SUPABASE_KEY=your_anon_key

DISCORD_WEBHOOK=your_webhook_url
```

## 啟動系統

```bash
python app.py
```

開啟：

```text
http://127.0.0.1:5001
```

# 🧪 核心演算法

## EAR

```text
EAR =
(||p2-p6|| + ||p3-p5||)
/
2(||p1-p4||)
```

用途：

* 疲勞監測
* 閉眼偵測

---

## MAR

```text
MAR =
mouth_height
/
mouth_width
```

用途：

* 打哈欠偵測
* 嘴部遮擋分析

---

## EMA Filter

```python
ema = alpha * current + (1 - alpha) * previous
```

降低感測抖動。

---

## IQR Filter

```python
Q1 = percentile(data,25)
Q3 = percentile(data,75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR
```

移除異常值。

---

# 🔒 系統穩定性設計

## Multi-Thread Architecture

獨立執行：

* Flask Server
* AI Detection
* Scheduler
* Discord Report

---

## Thread Safe

使用：

```python
state_lock
frame_lock
```

避免 Race Condition。

---

## Calibration Validation

校正時要求：

✅ 坐姿端正

✅ 光線充足

✅ 面向鏡頭

✅ 嘴部無遮擋

否則拒絕建立基準值。

---

# 📊 Dashboard

提供：

* 專注時數
* 摸魚時間
* 疲勞指數
* 高低肩次數
* 番茄鐘成功率
* 歷史趨勢分析

---

# 🔮 Future Work

## YOLO 姿勢辨識

辨識：

* 駝背
* 翹腳
* 身體前傾

---

## Multi-User System

支援：

* 多帳號
* 團隊排行榜

---

## Mobile App

開發：

* Android
* iOS

版本

---

## RAG 健康知識庫

整合：

* 健康指南
* 人體工學知識
* 醫療公開資料

---

## AI Agent Coach

建立長期健康管理代理人。

---

# 👥 開發團隊

## Core Developers

### 吳承誼

Frontend Engineer

負責：

* Dashboard UI 開發
* Tailwind CSS 介面設計
* JavaScript 前端邏輯
* WebSocket 即時資料顯示
* Chart.js 資料視覺化
* 使用者互動流程設計

---

### 章惟善

Backend & AI Engineer

負責：

* 系統架構設計
* Flask 後端開發
* Flask-SocketIO 即時通訊
* OpenCV 與 MediaPipe 整合
* EAR / MAR / IOD / Pose 演算法
* EMA / IQR 濾波設計
* 防摸魚判定邏輯
* NVIDIA NIM 整合
* Supabase 雲端同步
* Discord Webhook 推播
* 多執行緒同步控制

---

## Project Contributors

### 曾仁宥

* 功能需求討論
* 遊戲化機制發想
* 系統測試與回饋

### 林冠廷

* 摸魚機制規則討論
* 展示素材協助
* 系統測試與成果展示

---

# 📄 License

NUTC

Copyright © 2026 Group 5
