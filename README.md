## DSC 공유대학 캡스톤디자인 우수상 - 해외교통 표지판 번역 시스템

<div align="center">
  <img src="https://github.com/user-attachments/assets/04ea3e45-2e11-40ae-999b-7a9ed1300409" alt="손에 든 스마트폰과 정지 표지판" height="200" style="margin-right: 10px;">
  <img src="https://github.com/user-attachments/assets/548dcbfd-b8ce-4fce-b78b-2c6f8e770359" alt="교통 표지판 인식 시스템 아키텍처" height="200" style="margin-left: 10px;">
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
  <img src="https://github.com/user-attachments/assets/c9cb5616-dd2a-404a-8485-ce3bc0f56a5a" alt="데이터 수집 이미지" height="200" style="width: auto;">
  <img src="https://github.com/user-attachments/assets/c2e1d9e1-f095-4ee0-9e46-3317a52b5594" alt="데이터 클래스 구성" height="200" style="width: auto;">
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
<div align="center" style="display: flex; justify-content: center; gap: 20px; margin-top: 20px;">
  <img src="https://github.com/user-attachments/assets/eb0d4eb3-c0df-42c9-8961-3b947c9d4a11" alt="LLaVA 관련 논문 이미지" height="300" style="width: auto;">
  <img src="https://github.com/user-attachments/assets/ca84ce35-e0c6-4a9f-b4f3-8cb827302a73" alt="LLaVA 아이콘 이미지" height="300" style="width: auto;">
</div>

**1️⃣ 강력한 멀티모달 추론 능력**
CLIP 기반 이미지 인코더와 LLaMA 언어 모델을 연결한 멀티모달 구조, 시각적 지시문 데이터를 이용하여 end-to-end 방식으로 학습한 모델로 이미지를 보고 질문에 답하거나 설명을 생성하는 VQA, Image Captioning, Grounded Reasoning 등 고차원적 작업 수행 가능

**2️⃣ 상황 맟춤형 심층 가이드 제공**
Yolov11이 표지판 영역을 잘라내어 전달하면, LLaVA는 단순한 분류를 넘어 "이 표지판이 의미하는 바가 무엇인지", "어떻게 행동해야 하는지" 등 사용자의 질문에 대한 자연어 형태의 대답을 생성하여 여행자에게 깊이 있는 상호작용과 맥락적 가이드 제공

## LoRA Fine-Tuning 
본 프로젝트에서는 무거운 LLaVA 모델을 교통 표지판 도메인에 맞게 최적화하기 위해 파라미터 효율적 미세조정 기법 사용

* **1️⃣ 압도적인 리소스 효율성**
원본 파라미터를 전부 업데이트 하는 경우 메모리와 연산 비용이 너무 거대해질 수 있음. LLaVA같은 경우 대규모 모델을 효율적으로 Fine-Tunning 하기 위해서 도입. VRAM 사용량과 연산량을 최소화하면서도 비슷한 성능을 기대 가능

* **2️⃣ 특정 Task(교통 표지판 해석) 특화**
이미지 특징을 언어 모델의 임베딩 공간으로 projection하는 multi_modal_projector 모듈에서 저차원 어댑터만 학습. 이를 통해 모델 전체를 건드리지 않고도 원하는 Task(표지판 의미 파악 및 답변 생성)에 필요한 표현만 섬세하게 조절

* **3️⃣ 적은 데이터로도 안정적인 수렴 (Troubleshooting)**
전체 가중치가 아닌 adapter 파라미터만 업데이트하므로, 한정적이고 적은 데이터셋으로도 학습 과정이 불안정해지지 않고 안정적으로 수렴하는 효과 획득

---

## 결과물 정리 
* 영상을 업로드하는 경우 Yolov11이 먼저 표지판을 탐지 진행 ➡️ 이후 탐지된 표지판에 대해서 STT 기능을 활용하여 말을 전달 ➡️ 탐지된 표지판을 바탕으로 LLaVA가 인식한 후 정보를 사용자에게 전달 

<table align="center">
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/83635bbc-da82-4ff2-a18e-7a4df81353a0" alt="결과 이미지 1" width="300" height="400" />
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/859a32b0-c8bf-44e3-a846-a12da3454d33" alt="결과 이미지 2" width="300" height="400" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/49179dbe-a932-4c44-b173-081bc02b0877" alt="결과 이미지 3" width="300" height="400" />
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/6dbdcff6-06a6-4ae9-a611-ed2d4b387651" alt="결과 이미지 4" width="300" height="400" />
    </td>
  </tr>
</table>

---

## 개선 방향 및 기대효과

* 1️⃣ LLaVA가 아닌 Video LLaVA를 이용하여 영상 자체를 인식하여 실시간성 개선 가능성 확보
* 2️⃣ 실제 해외 운전자 대상 운전 환경 보조로 편의성 증가. 관광 및 안전 서비스에 응용 가능
* 3️⃣ 양방향 AI 음성 비서 구현 ➡️ STT와 LLaVA의 완전한 통합을 통해 운전자와 실시간 음성 대화가 가능한 인터렉티브 챗봇 서비스 제공
* 4️⃣ Video-LLaVA 도입 ➡️ 단일 프레임 분석의 한계를 넘어, 영상의 연속적인 흐름과 주행 문맥 파악하는 인식 기술 적용
* 5️⃣ 모빌리티 산업 확장성 ➡️ 운전자 보조 시스템 고도화, 관광 가이드, 교통 안전 교육 플랫폼 등 다양한 산업으로 기술 응용 및 사업화 

---

## 참고자료

* Kalchbrenner: Kalchbrenner, N., Elias, M., & Vinyals, O. (2018). Efficient neural audio synthesis. International Conference on Machine Learning, PMLR.
* Video-LLaVA: Lin, B., Xu, P., Wang, Z., & Li, Y. (2023). Video-llava: Learning united visual representation by alignment before projection. arXiv preprint arXiv:2311.10122.
* 성능 지표 (Rouge): Lin, C. Y. (2004). ROUGE: A package for automatic evaluation of summaries. Text summarization branches out.
* LLaVA: Liu, H., Li, C., Wu, Q., & Lee, Y. J. (2023). Visual instruction tuning. Advances in neural information processing systems, 36, 34892–34916.
* STT: Macháček, D., Dabre, R., & Bojar, O. (2023). Turning whisper into real-time transcription system. arXiv preprint arXiv:2307.14743.
* 성능 지표 (Bleu): Papineni, K., Roukos, S., Ward, T., & Zhu, W. J. (2002). Bleu: a method for automatic evaluation of machine translation.
 Proceedings of the 40th annual meeting of the Association for Computational Linguistics.
* YOLO: Redmon, J., Divvala, S., Girshick, R., & Farhadi, A. (2016). You only look once: Unified, real-time object detection. Proceedings of the IEEE conference on computer vision and pattern recognition.
* 배경: 한국관광 데이터랩 통계. (2025년 1월). 2025년 1월 출입국 관광통계. 관광지식정보시스템.
* 배경: 순고은. (2025년 1월). 해외여행도 뚜벅이로는 힘들어…렌터카 예약 '쑥’. 여행신문.

<div align="center">
  <img src="https://github.com/user-attachments/assets/782a346b-01db-47ea-8ee9-24d4fd27ef17" alt="수상 이미지1" width="400" height="400" style="margin-right: 10px;">
  <img src="https://github.com/user-attachments/assets/de43f5b1-3485-4a48-bc5d-ede9c1c447fe" alt="수상 이미지2" width="400" height="400" style="margin-left: 10px;">
</div>









