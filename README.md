# Traffic-sign-Detection-Muti-Modal-Service
## DSC 공유대학 캡스톤디자인 우수상 - 해외교통 표지판 번역 시스템

<div align="center" style="display: flex; justify-content: center; gap: 20px; margin-top: 20px;">
  <img src="https://github.com/user-attachments/assets/04ea3e45-2e11-40ae-999b-7a9ed1300409" alt="손에 든 스마트폰과 정지 표지판" height="250" style="width: auto;">
  <img src="https://github.com/user-attachments/assets/548dcbfd-b8ce-4fce-b78b-2c6f8e770359" alt="교통 표지판 인식 시스템 아키텍처" height="250" style="width: auto;">
</div>

# 팀원 소개
- **김준규** : 건양대 융합IT학과 / 팀장 / Data PreProcessing, React, Flask
- **유대영** : 건양대 의료인공지능학과 / 팀원 / LLaVA, Yolo, Data PreProcessing 
- **김동현** : 건양대 의료인공지능학과 / 팀원 / LLaVA, Yolo 
- **허연주** : 충남대 인공지능학과 / 팀원 / Presentation, React, Flask

# **CONTENTS**
* **프로젝트 개요** : 문제 정의 및 배경
* **데이터 처리** : 데이터 전처리, 구성, 증강
* **사용 모델 소개** : Yolov11, LLaVA
* **개선 방향 및 기대효과** : 한계점, 개선방안, 기술 고도화 계획
* **참고자료**

---

# 프로젝트 개요
본 프로젝트는 "일본 도로 교통 표지판 번역"주제로 한 React와 Falsk를 활용한 애플리케이션

일본 여행자들이 일본에서 차량을 타고 여행을 다닐 때 생소한 도로 교통 표지판을 보고 혼동하지 않도록 해석해주는 어플 제작

## 1️⃣ 주제 선정 배경

* **해외여행 수요 급증** : 2023년 대비 2024년 상반기 1,402만 명 출국
* **여행 트랜드 변화** : 자유 여행 + 헨터카 이용 급증 | 대중교통이 불편한 소도시 및 자연경관 지역 방문 증가
* **낯선 주변 환경과 교통 표지판** : 다양한 외곽 지역 이동으로 국가별 상이한 도로 및 교통 시스템 이해 필요성 증대
  
## 2️⃣ 문제점 

* **심각한 언어 장벽** : 현지 언어로 표기된 교통 표지판의 정보 습득이 불가한 경우 ➡️ 길을 잃거나 사고 발생 가능
* **기존 수단의 한계** : 운전 중 스마트폰 번역 앱 조작은 전방 주시 태만 야기 ➡️ 주행 상황의 즉각적 대응 불가능
* **블랙박스 부재** : 사고 발생 시 현지 언어 및 법규 장벽으로 인해 과실 증명 과정에서 불리한 위치에 놓임

## 3️⃣ 해결 방안

* **맥락 인지형 시각 지능 가이드 제작**

<div align="center" style="display: flex; justify-content: center; gap: 20px; margin-top: 20px;">
  <img src="https://github.com/user-attachments/assets/ee04613a-2b79-406e-9d4c-606ad12a6edf" alt="Yolov11 이미지" height="250" style="width: auto;">
  <img src="https://github.com/user-attachments/assets/cfbc7c60-1790-4885-acf8-9f48394b3ee2" alt="LLaVA 이미지 아이콘" height="250" style="width: auto;">
</div>

* **Yolov11 기반 실시간 탐지** : 이전 버전 대비 파라미터 최적화로 지연 없는 실시간 영상 인식 수행

* **LLaVA를 통 한 맥락 분석** : 탐지된 표지판 정보를 바탕으로 주변 상황 통합 분석 후 운전자에게 실질적 행동 지침 제공

--- 

# 데이터 처리 

## 1️⃣ 데이터 수집 및 클래스 구성

* ** 🗼 일본 교통 표지판 데이터** : 한국인이 가장 많이 가는 나라 중 하나를 예시로 제작을 목적으로 사용
* **데이터 클래스 구성** : 데이터 클래스는 총 8개 | 흔하지 않은 표지판을 대상으로 프로젝트를 제작

<div align="center" style="display: flex; justify-content: center; gap: 20px; margin-top: 20px;">
  <img src="https://github.com/user-attachments/assets/c9cb5616-dd2a-404a-8485-ce3bc0f56a5a" alt="데이터 수집 이미지" height="300" style="width: auto;">
  <img src="https://github.com/user-attachments/assets/c2e1d9e1-f095-4ee0-9e46-3317a52b5594" alt="데이터 클래스 구성" height="300" style="width: auto;">
</div>

## 2️⃣ 데이터 문제점 및 해결 방법

**😡데이터 부족 문제 발생** : kaggle, roboflow 등 opensource를 제공하는 사이트를 참고했으나 데이터가 현저히 부족
<div align="center">
<img width="600" height="337" alt="image" src="https://github.com/user-attachments/assets/057f1609-31bd-4baa-ad3e-1026cc9922ea" />
</div>

**1️⃣해결 방법** : 데이터 증강 기법 (argumentation) 사용
<div align="center">
<img width="600" height="439" alt="image" src="https://github.com/user-attachments/assets/8491e699-3acb-4518-804f-bc8388b31a6e" />
</div>

**2️⃣해결 방법** : 데이터 불균형 해소 | down sampling ➡️ data.yaml 파일에서 가중치 조절 후 균형 조정
<div align="center">
  <img width="600" height="295" alt="image" src="https://github.com/user-attachments/assets/ede48c6c-16c9-4ad7-bf45-d754268e7fc0" />
</div>

---

# 사용 모델 소개

## Yolov11 

<div align="center">
<img width="600" height="597" alt="image" src="https://github.com/user-attachments/assets/580d5123-11c0-4fbe-a64d-51c733a32ff8" />
</div>

**1️⃣ 초고속 실시간 탐지**

여행자가 스마트폰을 들고 이동하면서 표지판을 비출 때, Yolov11은 이전 버전 대비 줄어든 파라미터 수로 모바일 기기에서도 지연 없는 실시간 탐지를 수행

**2️⃣ 높은 정확도와 강건성**

다양한 각도, 날씨, 빛 번짐이 심한 해외 야외 환경에서도 표지판 객체를 정확하게 선별해내는 아키텍처 보유

**3️⃣ 멀티모달 시스템의 전처리 최적화**

Yolov11이 표지판을 먼저 빠르게 찾아내면, LLaVA는 해당 영역에 집중하여 설명을 생성하므로 전체 시스템의 Latency를 획기적으로 낮춤


<div align="center">
<img width="452" height="202" alt="image" src="https://github.com/user-attachments/assets/709d820a-54c2-45fe-80da-82d9551eea7b" />
</div>


## LLaVA 















