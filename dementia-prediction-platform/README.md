# 🧠 AI Dementia Prevention Platform

> **음성 API 기반 인지기능검사(CIST) 및 치매 예측 모델을 통한 고령자 치매 예방 플랫폼 구축**

![Python](https://img.shields.io/badge/Python-3.11-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-DeepLearning-orange)
![LightGBM](https://img.shields.io/badge/LightGBM-ML-green)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT-black)
![Clova](https://img.shields.io/badge/Naver-Clova_STT-03C75A)

---

# 📌 Overview

고령자의 치매를 조기에 발견하고 예방하기 위한 AI 기반 헬스케어 플랫폼입니다.

본 프로젝트는

- 🎙️ 음성 기반 CIST 인지기능검사
- 🧠 AI 치매 예측 모델
- 📊 개인 건강 대시보드
- 🏥 치매안심센터 연계

를 하나의 플랫폼으로 구현하였습니다.

---

# 🎯 Background

대한민국은 초고령사회에 진입하면서 치매 환자가 빠르게 증가하고 있습니다.

특히 부산시는 전국 특광역시 중 가장 높은 고령화 비율을 보이며,
고령자의 병원 접근성이 낮은 지역이 많습니다.

기존 치매검사는

- 의료기관 방문 필요
- 전문 인력 필요
- 종이 문진 기반

이라는 한계가 존재합니다.

이를 해결하기 위해 **AI 음성 인터페이스 기반 비대면 치매 선별 플랫폼**을 개발하였습니다.

---

# 🏗️ System Architecture

```
User
   │
   ▼
NAVER CLOVA STT
   │
   ▼
GPT 기반 CIST 응답 분석
   │
   ▼
치매 예측 모델
   │
   ▼
건강 리포트 생성
   │
   ▼
Dashboard
   │
   ▼
병원 / 치매안심센터 연계
```

---

# 📊 Dataset

## ① 라이프로그 데이터

- Smart Ring 기반 활동 데이터
- Smart Ring 기반 수면 데이터
- 약 **39,300 rows**
- **105 columns**

## ② 지역사회건강조사

- 질병관리청 공개 데이터
- 약 **14,516 rows**
- **209 columns**

---

# ⚙️ Tech Stack

| Category | Stack |
|-----------|-------|
| Language | Python |
| Data Analysis | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Random Forest, LightGBM, CatBoost |
| Deep Learning | DNN, Bi-LSTM |
| Hyperparameter | Optuna |
| Speech API | NAVER CLOVA STT |
| LLM | OpenAI GPT |
| Dashboard | Streamlit |

---

# 🔍 Data Analysis

### 라이프로그 데이터

- 활동량 분석
- 수면 패턴 분석
- 상관관계 분석
- 시계열 분석

### 지역사회건강조사

- 정신건강
- 신체활동
- 수면
- 우울
- 만성질환

EDA를 통해 주요 위험요인을 도출하고 모델링에 활용하였습니다.

---

# 🤖 Modeling

## Machine Learning

- Random Forest
- Gradient Boosting
- LightGBM
- CatBoost

## Deep Learning

- DNN
- Bi-LSTM

---

# 💡 Why Bi-LSTM?

기존 Tree 기반 모델은 시계열 데이터를 독립 샘플로 처리하기 때문에 시간적 연속성을 충분히 학습하지 못했습니다.

이를 해결하기 위해 **Bidirectional LSTM**을 적용하여 과거와 미래 정보를 동시에 학습하도록 설계하였습니다.

---

# 📈 Results

- Optuna 기반 Hyperparameter Tuning
- SMOTE 적용
- Bi-LSTM 기반 시계열 학습
- 기존 머신러닝 대비 일반화 성능 향상

---

# 🎙️ AI Cognitive Screening

```
사용자 음성 입력
        │
        ▼
NAVER CLOVA STT
        │
        ▼
GPT 기반 응답 분석
        │
        ▼
CIST 점수 산출
        │
        ▼
치매 위험도 예측
        │
        ▼
개인 맞춤 건강 리포트
```

---

# 📊 Dashboard

제공 기능

- 검사 결과 시각화
- 위험도 분석
- 생활습관 분석
- 개인 맞춤 건강관리
- 병원 연계

---

# 📁 Project Structure

```
AI-Dementia-Platform
│
├── data/
├── notebooks/
├── models/
├── dashboard/
├── api/
├── images/
└── README.md
```

---

# 👨‍💻 My Role
**Team Leader**

- 프로젝트 기획 및 일정 관리
- 데이터 전처리 및 EDA 수행
- Feature Engineering
- 머신러닝·딥러닝 모델 개발
- Hyperparameter Tuning (Optuna)
- GPT 기반 CIST 응답 분석 로직 구현
- 대시보드 설계 및 개발
- 팀원 역할 분담 및 프로젝트 산출물 통합
---

# 🚀 Future Work

- FastAPI 기반 서비스 배포
- 실시간 라이프로그 데이터 연동
- 의료기관 API 연계
- 모델 성능 고도화


