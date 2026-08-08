# 🏭 CNC Machine Defect Prediction

> **CNC 머신 데이터를 활용한 자동차 부품 불량 예측 모델 개발**

---

# 📌 Overview

자동차 부품 CNC 가공 공정에서 발생하는 **센서 데이터와 공정·품질 데이터를 활용하여 양품과 불량품을 예측하는 AI 모델**을 개발한 프로젝트입니다.

본 프로젝트는

* 📊 CNC 가공 장비 센서 데이터 분석
* 🔍 양품 / 불량품 분류
* 🤖 머신러닝·딥러닝 기반 불량 예측
* 🧠 SHAP 기반 예측 실패 분석
* ⚙️ 공정의 물리적 의미를 반영한 Feature Engineering

을 중심으로 진행하였습니다.

---

# 🎯 Background

자동차 부품의 CNC 가공 공정에서는 가공 조건과 장비 상태에 따라 제품 품질이 달라질 수 있습니다.

본 프로젝트에서는 공장 내 CNC 가공 장비에서 수집된 센서 데이터와 공정·품질 데이터를 활용하여 **양품과 불량품의 특징을 파악하고, 불량 발생을 사전에 예측할 수 있는 모델을 개발**하는 것을 목표로 하였습니다.

특히 단순히 높은 정확도의 모델을 구축하는 것에서 끝나지 않고, **모델이 어떤 변수에 의해 판단하고 어떤 상황에서 예측에 실패하는지**를 분석하여 공정 개선 방향까지 도출하고자 하였습니다.

---

# 🏗️ Project Pipeline

```text
CNC Machine Data
        │
        ▼
Data Preprocessing
        │
        ├── Labeling
        ├── SMOTE
        └── MinMax Scaling
        │
        ▼
EDA
        │
        ▼
Machine Learning
        │
        ├── CatBoost
        ├── XGBoost
        ├── LightGBM
        ├── GBM
        └── AdaBoost
        │
        ▼
Deep Learning
        │
        ├── DNN
        └── CNN
        │
        ▼
SHAP Analysis
        │
        ▼
Failure Case Analysis
        │
        ▼
Feature Engineering
        │
        ▼
Final Model Evaluation
```

---

# 📊 Dataset

## ① CNC Process & Quality Data

CNC 가공 조건 및 품질 데이터를 활용하였습니다.

* 작업 번호
* 작업 소재
* Feed Rate
* Clamp Pressure
* Tool Condition
* Machining Finalized
* Passed Visual Inspection

공정 완료 여부와 육안검사 결과를 기반으로 양품과 불량품을 정의하였습니다.

### Label Definition

```text
공정 완료 + 육안검사 통과
        ↓
      양품 (1)

공정 미완료
        ↓
      불량품 (0)

공정 완료 + 육안검사 불합격
        ↓
      불량품 (0)
```

---

## ② CNC Machine Sensor Data

CNC 가공 과정에서 측정된 다양한 장비 센서 데이터를 활용하였습니다.

주요 변수 예시는 다음과 같습니다.

* X / Y / Z Actual Position
* Actual Velocity
* Actual Acceleration
* Spindle Current
* DC Bus Voltage
* System Inertia
* Machining Process
* Current Program Number

총 **25개의 CNC 실험 데이터셋**을 활용하여 분석을 진행하였습니다.

---

# ⚙️ Data Preprocessing

## Class Imbalance

원본 데이터의 클래스 비율은 다음과 같았습니다.

```text
양품 : 70.7%
불량 : 29.3%
```

불량 데이터가 상대적으로 적어 모델이 양품 데이터에 편향될 가능성이 존재했습니다.

이를 해결하기 위해 **SMOTE**를 적용하여 클래스 비율을 균형화하였습니다.

```text
Before

양품 70.7% ██████████████
불량 29.3% ██████


After SMOTE

양품 50%   ██████████
불량 50%   ██████████
```

또한 센서별 단위와 범위가 서로 다른 문제를 해결하기 위해 **MinMaxScaler**를 적용하였습니다.

---

# 🔍 EDA

CNC 장비의 위치, 속도, 가속도, 전류, 전압 및 공정 관련 변수들을 분석하여 양품과 불량품의 데이터 특성을 확인하였습니다.

특히 Feature Importance와 SHAP 분석을 통해 **불량 예측에 영향을 미치는 주요 변수를 확인**하고 모델의 판단 근거를 분석하였습니다.

---

# 🤖 Modeling

## Machine Learning

다양한 Tree-based 모델을 비교하여 불량 예측 성능을 평가하였습니다.

* CatBoost
* XGBoost
* LightGBM
* GBM
* AdaBoost

그중 **LightGBM**이 불량 예측률 96.0%, F1-Score 95%를 기록하였습니다.

---

## Deep Learning

### DNN

초기 DNN 모델에서 과적합이 발생하는 문제를 확인하고,

* Learning Rate 조정
* Dropout
* Batch Size 변경
* Learning Rate Scheduler
* Early Stopping

등을 적용하여 모델을 개선하였습니다.

```text
Accuracy

88.7%
  ↓
96.7%
```

최종 DNN 모델은 **Accuracy 96.7%, F1-Score 95.31%**를 달성하였습니다.

---

### CNN

CNC 센서의 1차원 신호 데이터를 **STFT를 활용하여 스펙트로그램 이미지로 변환**한 뒤 CNN 모델에 입력하였습니다.

ResNet-50 기반 CNN 모델을 적용하고 Dropout, Learning Rate 조정, AdamW 등의 방법을 통해 모델을 개선하였습니다.
최종 CNN 모델:

```text
Accuracy  : 95.10%
F1-Score  : 96.50%
```

---

# 🧠 Explainable AI

## SHAP Analysis

높은 성능의 모델을 구축하는 것뿐만 아니라 **모델이 왜 특정 데이터를 불량 또는 양품으로 판단했는지** 분석하기 위해 SHAP을 활용하였습니다.

SHAP 분석 결과 주요 영향 변수는 다음과 같았습니다.

```text
1. M_CURRENT_FEEDRATE
2. X_OutputCurrent
3. S_SetVelocity
```

특히 `M_CURRENT_FEEDRATE`가 다른 변수보다 압도적으로 큰 영향력을 가지는 것을 확인하였습니다.

---

# 🚨 Failure Case Analysis

예측 실패 사례를 분석한 결과, 모델이 특정 Feature에 **과도하게 의존하는 문제**를 확인하였습니다.

특히 `M_CURRENT_FEEDRATE`가 다수의 예측 실패 사례에서 강한 영향을 미치고 있었으며, 특정 상황에서 모델의 판단 오류를 유발하는 주요 원인으로 분석하였습니다.

```text
특정 Feature 과의존
        ↓
특정 상황에서 판단 편향
        ↓
False Positive / False Negative 발생
        ↓
불량 예측 리스크 증가
```

이를 통해 단순히 모델 성능을 높이는 것뿐만 아니라 **예측 실패 원인을 분석하고 개선하는 과정이 중요함을 확인**하였습니다.

---

# ⚙️ Feature Engineering

SHAP 분석 결과와 CNC 공정의 물리적 의미를 바탕으로 새로운 파생변수를 생성하였습니다.

| Feature                  | Formula | 의미            |
| ------------------------ | ------- | ------------- |
| `Velocity_Current_Ratio` | 속도 / 전류 | 부하 및 공구 마모 감지 |
| `Velocity_Power_Ratio`   | 속도 / 전력 | 에너지 효율성 분석    |
| `Torque_Estimate`        | 속도 × 전류 | 모터 토크 간접 추정   |
| `Load_Increase`          | 전류 / 속도 | 부하 증가 감지      |

Feature Engineering 이후 `Torque_Estimate`가 SHAP 중요도 **2위**로 상승하면서, 단순 센서값뿐만 아니라 **공정의 물리적 의미를 반영한 Feature가 불량 예측에 유의미한 설명력을 가질 수 있음**을 확인하였습니다.

---

# 📈 Results

### Machine Learning

| Model    | Defect Prediction | F1-Score |
| -------- | ----------------: | -------: |
| CatBoost |             92.8% |      96% |
| XGBoost  |             92.5% |      95% |
| LightGBM |         **96.0%** |  **95%** |
| GBM      |             95.7% |      95% |
| AdaBoost |             95.6% |      95% |

### Deep Learning

| Model |  Accuracy |   F1-Score |
| ----- | --------: | ---------: |
| DNN   | **96.7%** | **95.31%** |
| CNN   |     95.1% | **96.50%** |

---

# 💡 Key Insights

### ① 단순 모델 성능 비교를 넘어 실패 원인을 분석

SHAP 기반 분석을 통해 모델의 특정 Feature 과의존 문제를 발견하고, 예측 실패 원인을 구체적으로 분석하였습니다.

### ② Domain Knowledge 기반 Feature Engineering

속도, 전류, 부하, 토크 등 CNC 공정의 물리적 관계를 반영한 파생변수를 설계하여 Feature의 설명력을 강화하였습니다.

### ③ ML과 DL 모델의 성능 비교

머신러닝뿐만 아니라 DNN과 CNN까지 적용하여 모델별 특성과 성능을 비교하였으며, DNN Accuracy 97%, CNN F1-Score 97% 수준의 성능을 확인하였습니다.

---

# 👨‍💻 My Role

**Data Analyst / Model Developer**

* CNC 데이터 전처리 및 EDA
* 양품 / 불량품 Labeling
* SMOTE 기반 데이터 불균형 처리
* 머신러닝 모델 개발 및 비교
* DNN / CNN 모델 개발
* 모델 성능 개선 및 과적합 분석
* SHAP 기반 Feature Importance 분석
* 예측 실패 케이스 분석
* Domain Knowledge 기반 Feature Engineering
* 파생변수 생성 및 성능 비교

---

# 🛠️ Tech Stack

| Category          | Stack                                      |
| ----------------- | ------------------------------------------ |
| Language          | Python                                     |
| Data Analysis     | Pandas, NumPy                              |
| Visualization     | Matplotlib, Seaborn                        |
| Preprocessing     | SMOTE, MinMaxScaler                        |
| Machine Learning  | LightGBM, XGBoost, CatBoost, GBM, AdaBoost |
| Deep Learning     | DNN, CNN, ResNet-50                        |
| Explainable AI    | SHAP                                       |
| Signal Processing | STFT                                       |

---

# 📁 Project Structure

```text
CNC-Defect-Prediction
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── EDA/
│   ├── MachineLearning/
│   └── DeepLearning/
│
├── models/
│   ├── lightgbm/
│   ├── dnn/
│   └── cnn/
│
├── analysis/
│   ├── shap/
│   └── feature_engineering/
│
├── images/
│
└── README.md
```

---

# 🚀 Future Work

* CNC 센서 데이터의 시계열 특성을 반영한 모델 고도화
* 실시간 센서 데이터 기반 불량 조기 탐지
* Feature Engineering 기반 공정 이상 탐지 고도화
* ML / DL 모델 앙상블을 통한 성능 개선
* SHAP 기반 설명 가능한 불량 예측 시스템 구축
* 실제 제조 공정 적용을 위한 실시간 모니터링 시스템 개발

---

# 📝 Conclusion

> **“단순히 불량을 예측하는 모델을 넘어, 예측 실패 원인을 분석하고 공정의 물리적 의미를 반영한 Feature Engineering을 통해 제조 데이터의 실질적인 활용 가능성을 확인한 프로젝트입니다.”**

본 프로젝트를 통해 **데이터 전처리 → 모델링 → 성능 개선 → Explainable AI → 실패 케이스 분석 → Feature Engineering**으로 이어지는 데이터 분석 및 AI 모델 개발 전체 프로세스를 경험하였습니다.
