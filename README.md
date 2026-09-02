# 🛠️ Project Portfolio

제조, 헬스케어, 에듀테크 등 다양한 도메인에서 수집된 데이터를 바탕으로 문제 정의부터 데이터 전처리, 모델링, **XAI(설명 가능한 AI) 기반 구조적 원인 분석 및 비즈니스 인사이트 도출**까지 수행한 프로젝트 포트폴리오입니다.

---

## 📌 Projects Summary

* 🏭 **CNC Machine Defect Prediction** [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/cnc-defect-prediction)
  * **한 줄 요약:** CNC 센서 데이터 기반 불량 예측 및 SHAP 원인 분석을 통한 공정 개선
  * **핵심 성과:** DNN 정확도 96.7%, CNN F1-Score 96.5% 달성
* 🧠 **AI Dementia Prevention Platform** [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/dementia-prediction-platform)
  * **한 줄 요약:** 음성 STT 및 Bi-LSTM 기반 비대면 치매 선별/예방 헬스케어 플랫폼
  * **핵심 성과:** 라이프로그 시계열 학습 및 음성 CIST 검사 자동화, Tableau 대시보드 구축
* 📚 **MOOC Platform User Analysis** [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/mooc-user-behavior-analysis)
  * **한 줄 요약:** edX 64만 건 데이터 기반 AARR 퍼널 분석 및 Tableau 대시보드 구축
  * **핵심 성과:** 이탈 병목 구간(Activation $\rightarrow$ Retention 48% 이탈) 규명

---

## 🏭 CNC Machine Defect Prediction [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/cnc-defect-prediction)

### 💡 Core Summary
* **목적:** 가공 센서 데이터를 분석하여 공정 불량을 사전에 예측하고, 예측 실패 원인을 분석하여 공정 파생변수 설계
* **핵심 기술:** `LightGBM`, `DNN`, `CNN (ResNet-50)`, `STFT`, `SHAP`, `MinMaxScaler`, `SMOTE`
* **주요 성과 & 역할:**
  * **데이터 균형화:** SMOTE를 활용해 불균형 데이터(양품 70.7% : 불량 29.3%)를 50:50으로 보정.
  * **딥러닝 고도화:** 1D 센서 신호를 STFT로 스펙트로그램화하여 **CNN F1-Score 96.5%**, **DNN 정확도 96.7%** 달성.
  * **XAI 기반 공정 개선:** SHAP 분석으로 특정 변수(`M_CURRENT_FEEDRATE`) 과의존에 의한 예측 실패 원인을 발견하고, 공정 물리 의미를 반영한 파생변수(`Torque_Estimate` 등)를 설계하여 모델 안정성 강화.

---

## 🧠 AI Dementia Prevention Platform [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/dementia-prediction-platform)

### 💡 Core Summary
* **목적:** 접근성이 낮은 고령자를 위해 음성 인터페이스 기반 비대면 치매 선별 플랫폼 및 모니터링 시스템 구축
* **핵심 기술:** `Bi-LSTM`, `NAVER CLOVA STT`, `GPT-4`, `Tableau`, `Optuna`
* **주요 성과 & 역할 (팀장):**
  * **파이프라인 구축:** `사용자 음성` $\rightarrow$ `STT` $\rightarrow$ `GPT CIST 응답 분석` $\rightarrow$ `치매 위험도 예측` $\rightarrow$ `리포트 생성` 프로세스 자동화.
  * **시계열 모델링:** Smart Ring 라이프로그 및 지역사회건강조사 데이터를 병합하고, 시간적 연속성을 학습하는 **Bi-LSTM**을 적용해 예측 성능 개선.
  * **Tableau 대시보드 시각화:** 검사 결과, 위험도 분석, 생활습관 모니터링을 위한 Tableau 대시보드 설계 및 구축.

---

## 📚 MOOC Platform User Analysis [:link: 바로가기](https://github.com/Data-YihyunSong/Projects/tree/main/mooc-user-behavior-analysis)

### 💡 Core Summary
* **목적:** edX 수강생의 학습 행동 및 이탈 구간 분석을 통한 수료율 개선 인사이트 도출
* **핵심 기술:** `Tableau`, `Pandas`, `AARR Funnel Framework`
* **주요 성과 & 역할:**
  * **AARR 퍼널 분석:** 64만 건 데이터 분석을 통해 초기 콘텐츠 미시청(Acquisition $\rightarrow$ Activation 26% 이탈) 및 반복 학습 정체(Activation $\rightarrow$ Retention 48% 이탈) 등 핵심 이탈 구간을 규명.
  * **Tableau 대시보드 제작:** Overview, Marketing, Product 관점의 KPI 및 유저 행동 시각화 대시보드 3종 설계 및 구현.

---

### 🛠️ Tech Stack Matrix
* **Languages & Data:** Python (Pandas, NumPy)
* **ML / DL:** LightGBM, CatBoost, XGBoost, DNN, CNN (ResNet-50), Bi-LSTM, Optuna
* **XAI & Signal:** SHAP, STFT
* **API & BI:** NAVER CLOVA STT, OpenAI GPT, Tableau
