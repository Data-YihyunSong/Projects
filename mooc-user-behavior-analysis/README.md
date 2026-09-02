# 📚 MOOC Platform User Analysis

> Tableau 기반 MOOC 플랫폼 사용자 분석 및 대시보드 구축

[Python](https://img.shields.io/badge/Python-3.11+-blue) [Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-blue) [Tableau](https://img.shields.io/badge/Tableau-Dashboard-orange)

---

# 📌 Overview

MOOC 플랫폼 edX의 수강생 데이터를 활용하여 사용자 행동과 강의 현황을 분석하고, Tableau 기반 대시보드를 구축한 데이터 분석 프로젝트**입니다.

* 📊 플랫폼·강의 현황 분석
* 👤 수강생 행동 및 특성 분석
* 📈 Tableau 대시보드 구축
* 🔄 AARR 퍼널 기반 이탈 분석

---

# 🎯 Background

edX는 Harvard와 MIT가 설립한 MOOC 플랫폼으로, 수료 인증서 발급이 주요 수익 모델과 연결되어 있습니다.

이에 따라 수강생의 수료율과 학습 지속성을 분석하고, 사용자 이탈 구간 및 개선 방향을 도출하였습니다.

---

# 📊 Dataset

* 641,138건의 edX 수강생 데이터
* 강의 정보
* 수강생 정보
* 학습 활동 데이터
* 성과 및 수료 데이터

주요 변수: `grade`, `certified`, `nevents`, `ndays_act`, `nchapters`, `explored`, `viewed` 등

---

# 🔍 Analysis

### 사용자 및 강의 분석

* 강의별 수강생·수료자·수료율 분석
* 성별·연령·학력·국적·언어권 분석
* 수료자와 비수료자의 학습 행동 비교
* 활동 지표와 수료 여부 간 상관관계 분석

### AARR Funnel

```text
Acquisition → Activation → Retention → Revenue
   등록         수강 시작       반복 활동       수료
```

| 단계                       |    전환율 |
| ------------------------ | -----: |
| Acquisition → Activation | 74.07% |
| Activation → Retention   | 51.79% |
| Retention → Revenue      |  4.13% |

→ **초기 콘텐츠 미시청 및 반복 학습 단계에서 높은 이탈률 확인**

---

# 📊 Tableau Dashboard

### 01. Overview Dashboard

* 플랫폼·강의별 주요 KPI
* 수강생 및 수료율
* 강의 분야·대학별 수강 현황

### 02. Marketing Dashboard

* 성별·연령·학력·국적
* 월별 사용자 유입
* 사용자 유형 분석

### 03. Product Dashboard

* 국가별 유지·이탈률
* 강의별 유지·이탈 분석
* 사용자 활동 지표 분석

---

# 💡 Key Insights

* 전체 수강생 대비 수료율 3.58%로 낮은 수료율 확인
* 수료자는 비수료자보다 활동 일수 및 행동 횟수가 높은 경향 확인
* Acquisition → Activation 단계에서 약 26% 이탈
* Activation → Retention 단계에서 약 48% 이탈
* 사용자 유형 및 언어권에 따른 맞춤형 마케팅 전략 필요성 도출

---

# 👨‍💻 My Role
Data Analyst | Tableau & AARR

* Tableau 대시보드 설계 및 구축
* 주요 KPI 및 사용자 행동 데이터 시각화
* AARR Funnel 설계 및 전환율 분석
* 사용자 유지·이탈 분석
* 데이터 기반 마케팅·프로덕트 개선 인사이트 도출

---

# 🚀 Future Work

* AARR → AARRR 퍼널 확장
* 사용자 행동 기반 이탈 예측 모델 개발
* 사용자별 행동 패턴 기반 개인화 추천 시스템 구축

