![배너](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/banner.png?raw=true)

# 🚲 서울시 공공자전거 수요 예측 및 분석

## 1. 프로젝트 개요

이 프로젝트는 **탐색적 데이터 분석(EDA)** 을 기반으로, 서울시 공공자전거 서비스인 **따릉이**의 **수요 예측**과 **신규 대여소 설치 위치 추천** 기능을 구현하기 위한 데이터 분석 프로젝트입니다.

> **📅 프로젝트 기간: 2025.03.24 ~ 2025.03.27**

![1-2](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/1-2.png?raw=true)

서울시 따릉이는 현재 서울시민 10명 중 4명이 이용할 정도로 일상에 깊숙이 자리 잡은 교통수단이지만, **대여소별 자전거 부족 문제**는 여전히 해결되지 않은 과제로 남아 있습니다.

따릉이는 **One-Way 방식**으로 운영되어, 사용자가 **어디서든 대여하고 다른 곳에 반납**할 수 있습니다. 이러한 구조로 인해 특정 대여소에서는 **공급 부족**, 다른 대여소에서는 **자전거 과잉** 문제가 반복적으로 발생합니다.

| 운영상 문제점 | 설명 |
|---------------|------|
| 자전거 부족 | 수요 대비 공급이 항상 모자란 대여소 |
| 자전거 과잉 | 자전거가 반납만 되고 회수되지 않는 대여소 |
| 급변 대응 한계 | 특정 시간대 수요 폭증 시 실시간 대응 불가 |

  

현재는 수량 기준 초과/미달 상황에 따라 자전거를 회수하거나 옮기는 **사후적 대응 방식**으로만 운영되고 있으며, 이는 **예측이 없는 수동적 운영**이기 때문에 **실시간 수요 변화에 선제적으로 대응하기 어려운 구조**입니다.

---

## 2. 기술 스택

| 분류 | 기술 | 배지 |
|------|------|------|
| **개발환경** | Linux (Ubuntu)<br>VS Code | ![Linux](https://img.shields.io/badge/linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)<br>![VS Code](https://img.shields.io/badge/VSCode-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white) |
| **언어** | Python | ![Python](https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white) |
| **데이터 분석** | Pandas<br>Matplotlib<br>Seaborn<br>Jupyter Notebook | ![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)<br>![Matplotlib](https://img.shields.io/badge/matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)<br>![Seaborn](https://img.shields.io/badge/seaborn-4B8BBE?style=for-the-badge&logo=python&logoColor=white)<br>![Jupyter](https://img.shields.io/badge/jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white) |
| **모델링** | XGBoost<br>scikit-learn | ![XGBoost](https://img.shields.io/badge/xgboost-FF6600?style=for-the-badge&logo=apache&logoColor=white)<br>![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white) |
| **DB** | MySQL<br>AWS RDS | ![MySQL](https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white)<br>![AWS](https://img.shields.io/badge/amazonaws-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white) |
| **시각화** | Folium | ![Folium](https://img.shields.io/badge/folium-77B829?style=for-the-badge&logo=leaflet&logoColor=white) |
| **UI** | PyQt5 | ![PyQt5](https://img.shields.io/badge/PyQt5-41CD52?style=for-the-badge&logo=qt&logoColor=white) |
| **형상 관리** | Git / GitHub | ![Git](https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white) |
| **협업 도구** | Confluence<br>Jira<br>Slack | ![Confluence](https://img.shields.io/badge/confluence-172B4D?style=for-the-badge&logo=confluence&logoColor=white)<br>![Jira](https://img.shields.io/badge/jira-0052CC?style=for-the-badge&logo=jira&logoColor=white)<br>![Slack](https://img.shields.io/badge/slack-4A154B?style=for-the-badge&logo=slack&logoColor=white) |




---

## 3. 프로젝트 목적 / 필요성

> 🕒🚲 **필요한 시간에, 필요한 곳에**

서울시 따릉이 운영의 비효율 문제를 해결하기 위해서는 **데이터 기반 수요 예측 모델링**과 이를 바탕으로 한 **운영 전략 수립**이 필요합니다.

1. 다양한 요인(기상, 고도, 인구, 교통 등)을 반영한 정교한 **수요 예측 모델** 구축  
2. 이를 바탕으로 다음 기능 구현:
   - **시간대별·대여소별 수요 예측** → 선제적 자전거 재배치  
   - **장소 기반 수요 예측** → 신규 대여소 설치 위치 추천  

> 🎯 **궁극적인 목표** : "어디에, 언제 자전거가 필요할지"를 예측하여 공공자전거 운영을 **더 효율적으로 만드는 것**

---

## 4. 요구사항 정의

사용자의 요구사항을 분석하여, 시스템 수준의 기능 요구사항으로 구체화하였습니다.

| 사용자 요구사항 (UR) | 설명 |
|----------------------|------|
| UR_01 | 특정 대여소의 시간대별 대여량을 예측받을 수 있어야 한다. |
| UR_02 | 신규 대여소 설치에 적합한 위치를 추천받을 수 있어야 한다. |

| 시스템 요구사항 (SR) | 설명 |
|----------------------|------|
| SR_01 | **시간 및 환경 정보**를 기반으로 특정 대여소의 대여량을 예측하는 기능 |
| SR_02 | **공간 및 위치 정보**를 바탕으로 설치가 필요한 위치를 추천하는 기능 |

---

## 5. 데이터베이스 구성 및 출처

**(추가 예정)**  

### 5-1. 데이터 출처
- ...

### 5-2. 데이터베이스 구조
![ERD](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/4-1.png?raw=true)
- ...

### 5-3. 데이터 통합 및 전처리
- ...

---

## 6. EDA (탐색적 데이터 분석)

본 프로젝트는 **"공공자전거 수요에 영향을 주는 요인은 무엇인가?"** 라는 질문을 중심으로 두 가지 카테고리의 가설을 설정하고, 이를 분석을 통해 검증하는 형태로 탐색적 분석을 진행하였습니다.

| 시간 및 환경 특성       | 공간 및 위치 특성               |
|------------------------|-------------------------------|
| 시간                   | 대중교통 근접성                |
| 공휴일                 | 대중교통 승하차량              |
| 요일                   | 생활인구                      |
| 기온                   | 산업 및 고용 환경             |
| 강수량                 | 소득                          |
| 습도                   | 상권(주변 점포 수)            |
| 풍속                   | 자전거 인프라(자전거 도로)    |
| 일사량                 | 여가 인프라(공원)             |

> **위와 같은 요소들이 대여량 변화에 영향을 줄 것이다**


---

## ⏱️ 가설 그룹 A. 시간 및 환경 특성

### 🧪 가설 A-1. 시간 요인은 수요에 유의미한 영향을 미친다

#### 📌 분석 내용
- 시간대/요일/월별로 수요를 집계
- 출퇴근 시간, 금요일, 봄/가을에 수요 집중

#### 📊 시각화
![시간대](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/5-2.png?raw=true)  
![주중vs주말](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-3.png?raw=true)
![평일vs휴일](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-4.png?raw=true)
![요일별](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-5.png?raw=true)
![계절별](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-6.png?raw=true)

#### ✅ 결론
- 출근 시간(7-9시), 퇴근 시간(17-19시)에 수요 급등  
- ...
- 
→ **SR_01 기능의 주요 feature로 채택**

---

### 🧪 가설 A-2. 날씨 조건은 수요를 크게 변화시킨다

#### 📌 분석 내용
- 기온, 강수량, 일조량에 따른 수요 변화 확인
- 날씨 API 예보 데이터를 연동하여 대응 가능성 검토

#### 📊 시각화
![기온 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-7.png?raw=true)
![강수량 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-8.png?raw=true)
![습도 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-9.png?raw=true)
![일사량 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-10.png?raw=true)

#### ✅ 결론
- 최적 기온은 약 22도 전후  
- 강수량이 존재하면 수요 급감  
- 날씨는 **단기 수요 예측(SR_01)** 에서 반드시 고려해야 할 요소

---

## 📍 가설 그룹 B. 공간 및 위치 특성

공공자전거의 수요는 **대여소의 공간적 입지 조건**에 따라 크게 달라질 수 있다는 가정 하에, 다양한 입지 요인별로 개별 가설을 설정하여 검증을 진행하였습니다.

---

### 🧪 가설 B-1. 고도가 높을수록 자전거 수요는 낮아진다

#### 📌 분석 내용
- 대여소 위치의 고도 정보와 수요 비교
- 고도별 구간 나눠 그룹 평균 분석

#### 📊 시각화
![서울시 자치구별 평균 고도](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-11.png?raw=true)
![자치구별 평균 고도 vs 따릉이 대여 수](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-12.png?raw=true)
![대여소별 고도에 따른 평균대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-13.png?raw=true)

#### ✅ 결론
- 평균 고도가 높을수록 대여량이 감소하는 경향 명확  
- 고도는 **SR_02 설치 위치 추천 모델의 핵심 feature** 중 하나

---

### 🧪 가설 B-2. 지하철역/버스정류장과 가까울수록 수요가 높다

#### 📌 분석 내용
- 각 대여소와 가장 가까운 지하철역/버스정류장 거리 계산
- 거리 단위 구간별 수요 비교

#### 📊 시각화
![지하철/버스정류장 거리 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-15.png?raw=true)

#### ✅ 결론
- 지하철역 반경 300m 이내 대여소에서 수요가 집중됨  
- 반경 거리 feature 생성 → **SR_02에 포함**

---

### 🧪 가설 B-3. 가까운 지하철역/버스정류장의 이용량이 높을수록 수요가 높다

#### 📌 분석 내용
- 각 대여소와 가장 가까운 지하철역/버스정류장의 이용량을 계산

#### 📊 시각화
![지하철/버스정류장 이용량 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-16.png?raw=true)

#### ✅ 결론
- 지하철역 반경 300m 이내 대여소에서 수요가 집중됨  
- 반경 거리 feature 생성 → **SR_02에 포함**

---

### 🧪 가설 B-3. 생활인구가 많을수록 자전거 수요도 많다

#### 📌 분석 내용
- 자치구 단위 생활인구 데이터와 대여소 수요 매핑
- 
#### 📊 시각화
![유동 인구 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-17.png?raw=true)

#### ✅ 결론
- 생활 인구와 대여량 간 양의 상관관계 존재  

---

### 🧪 가설 B-4. 공원이 가까울수록 수요가 많다

#### 📌 분석 내용
- ...

#### 📊 시각화
![공원수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-22.png?raw=true)

#### ✅ 결론
- ...
---

### 🧪 가설 B-5. 산업 및 고용 환경은 수요를 크게 변화시킨다.

#### 📌 분석 내용
- ...

#### 📊 시각화
![자치구별 사업체 종사자 수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-18.png?raw=true)
![행정동별 사업체 종사자 수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-19.png?raw=true)
![자치구별 사업체 수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-20.png?raw=true)
![행정동별 사업체 수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-21.png?raw=true)

#### ✅ 결론
- ...

---

### 🧪 가설 B-6. 자전거도로가 많을수록 수요가 많다.

#### 📌 분석 내용
- ...

#### 📊 시각화
![자치구별 자전거도로 노선 수 vs 대여량](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-23.png?raw=true)

#### ✅ 결론
- ...

---

## 7. 기능 설명

### 🚴‍♀️ SR_01. 대여소별 시간대별 수요 예측

- XGBoost 기반 회귀 모델 사용
- 입력: 대여소 ID, 날짜, 시간, 기온, 풍속 등
- 출력: 예상 대여량 숫자 (GUI로 실시간 확인)

![SR_01_출력화면](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-1.png?raw=true)

### 🗺 SR_02. 신규 대여소 설치 위치 추천

- 지정된 좌표 범위 내 격자 후보지 생성
- 위치 특성 기반 수요 예측 모델 적용
- 예측값 상위 후보지 지도에 마커로 시각화

![SR_02_출력화면](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/6-2.png?raw=true)

---

## 8. 모델 설명 및 성능

본 프로젝트는 시간 기반 수요 예측(SR_01)과 공간 기반 설치 위치 추천(SR_02)이라는 두 가지 기능을 중심으로, 각각에 최적화된 모델을 구축하였습니다. 주요 성능 평가지표는 RMSE, MAE, (S)MAPE, R² 등을 활용하였으며, 아래와 같은 결과를 도출하였습니다.

### 📍 SR_01 (시간대별 예측)

- **모델**: XGBoost 회귀
- **입력 변수**: 날짜, 시간, 기온, 풍속, 강수량, 습도, 고도, 요일 등
- **출력 변수**: 시간대별 대여량

![모델](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/7-1.png?raw=true)

| 지표 | 값 |
|------|----|
| RMSE | 9.60 |
| MAE  | 6.66 |
| MAPE | 23.24% |
| R²   | 0.835 |

- 전체 구간 대비 실수요 구간에서 MAPE가 크게 개선되어, 실제 운영에 적합한 수준의 정밀도를 확보함  
- R² = 0.860으로, 주요 변수들이 수요 변동을 충분히 설명하고 있음

---

### 🗺 SR_02 (설치 위치 예측)

- **모델**: 3-Stage XGBoost 모델 (수요 구간별 분리 학습)
- **입력 변수**: 위도, 경도, 고도, 주변 인구, 유동 인구, 교통 접근성, 상업시설 수 등
- **출력 변수**: 일 평균 대여 수요 예측값

![모델](https://github.com/addinedu-ros-9th/eda-repo-1/blob/main/img/7-2.png?raw=true)

| 지표 | 값 |
|------|----|
| RMSE  | 20.49 |
| MAE   | 12.60 |
| MAPE  | 41.59% |
| SMAPE | 33.96% |
| R²    | 0.761 |

- 위치 기반 변수만을 활용했음에도 R²가 0.76으로, 공간적 수요 분포를 파악하는 데 충분한 설명력을 보임  
- 절대적 예측 정확도보다는 후보지 간 **상대적 수요 비교**에 유용하며, 입지 전략 수립 시 **실제 의사결정에 도움이 될 수 있음**  
- 다만, 고수요 대여소(일수요 > 100)에 대해서는 성능 개선이 필요하며, 그 구조적 한계에 대해서는 [9. 한계점](#9-한계점)에서 다루었습니다.


---

### ✅ 기능별 성능 요약

| 기능 | 설명 | R² | MAPE / SMAPE | 활용 가능성 |
|------|------|----|----------------|---------------|
| **SR_01** | 시간대별 수요 예측 | **0.860** | **23.2%** (실수요 기준) | 실시간 운영에 활용 가능 |
| **SR_02** | 설치 위치 수요 예측 | **0.761** | **33.96%** (SMAPE) | 입지 전략 수립에 활용 가능 |

> **SR_01**은 **실수요 중심의 정밀 예측**, **SR_02**는 **상대적 수요 비교 기반의 전략 지원 도구**로 작동하며 **현장 운영 및 정책 수립 모두에 활용 가능한 수준의 성능을 확보**하였습니다.


---

## 9. 한계점

### 9-1. 고수요 대여소가 예측 어려운 구조적 이유

#### **비선형적 스케일 효과 (threshold effect)**
- 고수요 대여소는 단순히 "지하철역이 가깝다" 하나만으로 설명되지 않음
- **특정 feature 조합이 임계치를 넘을 때** 수요가 폭발적으로 증가하는 경향이 있음
- 회귀 모델이 패턴을 포착하기 어려울 수 있음

#### **고수요 대여소는 지역 맥락이 특수할 수 있음**
- 서울숲, 여의도공원, 강남역 주변 → 고수요지만 매우 특화된 입지 조건
- 이건 **데이터에 있는 일반적인 feature로는 잘 반영되지 않음**
  (랜드마크, 관광, 업무 밀집도, 브랜드, 정책 등)

---

### 9-2. 공공데이터 수집의 구조적 한계

#### **공공데이터의 해상도 한계로 분석 단위에 제약이 존재함**
- 공공 API는 시간·공간 해상도가 낮은 경우가 많음. 이로 인해 **미세한 수요 변동이나 위치 기반 패턴**을 정밀하게 반영하기 어려움
- 특히, **원래 의도했던 ‘행정동 단위 세밀 분석’이 불가능**했던 경우가 있었고, 위치 기반 수요 분석 시 **공간 분해능이 낮아지는 한계**로 이어짐

#### **중복 및 불일치 문제 발생**
- 예: 좌표계 상이, 행정동 코드 매핑 오류 등
- → 전처리 단계에서 수작업이 많이 필요함

#### **민간 데이터에 비해 한계가 명확함**
- 유동 인구, 상권 정보 등은 정밀 예측에 한계
- → 추후 민간 API(카카오, SKT, Tmap 등) 연계 필요

> 따라서, 본 프로젝트의 예측 성능과 분석 정밀도는 **공공데이터 품질 및 해상도에 직접적인 영향을 받으며**, 향후에는 **민간 데이터 연동 또는 공공데이터 고도화가 필요**합니다.

---

## 10. 디렉토리 구조

**(추가 예정)**

---

## 11. 실행 방법

**(추가 예정)**

---

## 12. 팀 소개

### 👨‍💼 팀장

| 이름 | 역할 |
|------|------|
| 장진혁 | - 프로젝트 기획 및 총괄<br>- 데이터베이스 설계, 구축 및 관리<br>- 실시간 대여량 예측 시스템 설계 및 구현 : 시간 특성 기반 예측 모델 및 사용자 기능 개발<br>- 신규 대여소 설치 위치 추천 시스템 설계 및 구현 : 공간 특성 기반 예측 모델 및 위치 추천 알고리즘 개발 |

### 👥 팀원

| 이름 | 역할 |
|------|------|
| 김대인 | - 위치 기반 대중교통 접근성 분석 지표 설계 및 구현<br>- 지하철/버스/따릉이 이용량 데이터 병합 및 시간대별 상관관계 분석<br>- 프로젝트 문서 통일 및 코드 정리, GitHub 배포 전 사전 점검 |
| 김민수 | - 위치 기반 대중교통 접근성 분석 지표 설계 및 구현<br>- 지하철/버스/따릉이 이용량 데이터 병합 및 시간대별 상관관계 분석<br>- 프로젝트 문서 통일 및 코드 정리, GitHub 배포 전 사전 점검 |
| 김범진 | - 다양한 분석 가설 수립<br>- 공공데이터 수집 및 전처리<br>- 데이터 분석 및 시각화 |



