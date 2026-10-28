<div align="center">

<a name="카메라-모듈-갭-검출"></a>
<a name="동적-roi-정렬과-이진화-기반-카메라-모듈-갭-검출"></a>
<a name="gap-detection-for-compact-camera-modules-based-on-dynamic-roi-alignment-and-optimized-image-binarization"></a>

# 📏 Camera Module Gap Project

영상 정렬과 영역별 필터로 카메라 모듈의 틈 위치와 길이를 측정하는 연구입니다.

**기술 분류:** 컴퓨터 비전 › 기하 정렬·영상 처리 › ROI·이진화·1차원 갭 측정

![Paper](https://img.shields.io/badge/Research-Paper-2563EB?style=flat-square) ![Document](https://img.shields.io/badge/Document-HWPX-475569?style=flat-square)

[원고 읽기](#quick-start) · [저장소 구성](#structure) · [자료·설정](#data)

[예시 이미지](#preview)

<details>
<summary>📄 원고 제목</summary>

Gap Detection for Compact Camera Modules Based on Dynamic ROI Alignment and Optimized Image Binarization

</details>

</div>

<a name="overview"></a>

## 🗺️ 한눈에 보는 구성

<p align="center"><img src="assets/overview.png" width="960" alt="프로젝트의 입력·처리·출력을 정리한 설명도" /></p>
보관한 프로젝트 자료의 흐름을 정리한 설명도입니다.

## ✨ 최종 원고에서 살펴볼 점

정렬·전처리·이진화와 ROI 측정으로 카메라 모듈 갭을 비교하는 원고입니다.

원고의 5픽셀 기준은 초기 배치 실험의 경험적 설정이며 모든 제조 환경에 검증된 기준은 아닙니다. HWPX 페이지 배치는 렌더 검증하지 않았습니다.






- 관심영역과 측정선을 이용한 갭 측정에서 화질 지표와 실제 갭 오차의 역할을 구분합니다.
- 5픽셀 기준은 초기 배치의 경험적 설정입니다. 필터 처리시간을 전체 생산라인 지연으로 해석하지 않으며 학습 기반 방식은 후속 과제로 구분합니다.

**자료별 안내:** [최종 원고](docs/versions/final-paper.md) · [전체 기록](docs/VERSIONS.md)

<a name="preview"></a>

## 🖼️ 예시로 보기

<p align="center"><img src="assets/previews/paper-processing-pipeline.png" width="773" alt="논문 그림 · Camera-Module-Gap-Detection-Project" /></p>

**논문 그림** — 공개 HWPX 원고의 처리 흐름도: 정렬·전처리·이진화·ROI 기반 갭 측정 과정입니다.

[근거 파일 보기](%EB%85%BC%EB%AC%B8/%EC%B5%9C%EC%A2%85_%EB%85%BC%EB%AC%B8.hwpx)


<a name="input-processing-output"></a>

## 🔄 입력·처리·출력

| 단계 | 이 프로젝트에서 다루는 내용 |
| :--- | :--- |
| 입력 | 카메라 모듈 검사 영상 |
| 처리 | 기준 위치 검출·ROI 정렬, 영역별 필터·임계값, 주사선 길이 측정 |
| 출력 | 갭 위치·길이와 검사 지표 |


---

## ✨ 프로젝트 소개

저자: **곽윤석 · 김남기**

원고는 개인 연구 문서 형식이며 특정 학회 게재 완료가 확인되지 않았습니다. 파일명보다 본문의 연구 제목을 사용했습니다.

| 항목 | 원고에서 다루는 내용 |
|---|---|
| 동적 정렬 | YOLO 키포인트의 left_top/right_top으로 회전·이동을 보정합니다. |
| 갭 측정 | 6개 ROI 안의 샘플 라인에서 검정 픽셀 연속 구간을 분석합니다. |
| 필터 비교 | 공간·주파수·비국소 필터와 순차 조합을 비교합니다. |
| 품질·비용 분석 | 갭 편차·누락률·이상치율·PSNR·SSIM·처리시간을 설명합니다. |

```mermaid
flowchart LR
A[제조 부품 영상] --> B[키포인트 기반 회전·이동 정렬]
B --> C[전처리 필터]
C --> D[전역·적응형·영역별 이진화]
D --> E[ROI와 샘플 라인]
E --> F[갭·누락·이상치·화질·시간 비교]
```

<a name="structure"></a>
## 📁 저장소 구성

```text
.
├── README.md
├── CHANGELOG.md
└── 논문/
    └── 최종_논문.hwpx
```

- [전체 최종 원고](논문/최종_논문.hwpx)

## 🧩 갭 측정과 필터 비교

원고는 ROI별 6개 샘플 X좌표, 최소 5픽셀의 검정 그룹, 5픽셀 이하 간격의 그룹 병합 규칙을 설명합니다. 상단에는 Anisotropic 필터와 임계값 100, 하단에는 Wiener 필터와 임계값 130을 적용하는 예도 제시합니다. 5픽셀 기준은 초기 배치 실험에서 정한 경험적 설정입니다. 통계적 최적화나 환경별 적응 기준의 검증은 후속 과제로 남아 있으므로, 모든 제조 환경에 통용되는 기준으로 사용하지 않습니다.

Fast Global Smoother+Sharpen, Bilateral+Sharpen, Median+Sharpen 등 조합의 측정 안정성과 연산 비용을 비교합니다. ROI 그룹의 평균 차이와 표준편차 합으로 후보를 정렬하고 상위 10% 필터군을 고르는 절차도 설명합니다. PSNR·SSIM은 화질 유사도, 갭 편차·누락률·이상치율은 측정 안정성을 보는 지표이므로 서로 대신하지 않습니다. 학습 기반 denoiser는 비교 대상으로 서술한 부분과 향후 연구로 남긴 부분이 있어 실제 수행 범위를 구분해야 합니다.

<a name="quick-start"></a>
## 🚀 원고 읽기

1. 위의 최종 원고 링크를 엽니다.
2. 서론의 연구 질문과 방법을 먼저 읽습니다.
3. 결과표와 함께 한계·후속 연구를 확인합니다.

이 저장소에는 실행 코드가 없어 원고를 내려받아 읽으면 됩니다. 기존 원본 폴더 조사에서도 지정한 코드 확장자의 일반 파일은 찾지 못했습니다. 다만 압축 파일 내부까지 조사한 것은 아닙니다.

<a name="data"></a>
## 📊 자료 구성과 결과 해석

최종 원고 한 개를 HWPX 형식으로 보존하는 구성입니다. 내장 그림은 제조 부품, 이진화 결과, 흐름도와 연구 도표입니다. 제조 원데이터 폴더는 포함하지 않습니다. 문서의 전체 본문과 내장 그림을 확인했으나 HWPX의 최종 페이지 배치는 렌더로 검증하지 않았습니다.

<a name="원고가-보고한-결과와-한계"></a>

### 🔎 원고가 보고한 결과와 한계

원고 초록은 갭 편차 28.6% 감소, 누락률 3.9→1.2%, 이상치율 6.8→2.5%, PSNR 35.2dB·SSIM 0.94를 보고합니다. 이 값은 재실행 검증 결과가 아닙니다.

본문에는 546장과 약 1,000장 실험 서술이 함께 있습니다. Fast Global Smoother의 처리 비용을 가장 우수하다고 설명한 문장과 가장 느린 조합이라고 설명한 문장이 병존하고, 누락률 도표와 설명도 일치하지 않는 부분이 있습니다. 어느 조건의 결과인지 추가 확인 없이 하나의 성능으로 합치지 않습니다. 본문의 0.1266 s/image도 해당 필터 처리시간 보고값으로 읽어야 하며, 장비 입출력을 포함한 생산라인 전체 지연이 검증되었다는 뜻은 아닙니다.

## 🛠 문제 해결

| 상황 | 확인할 내용 |
|---|---|
| GitHub에서 HWPX 본문이 바로 보이지 않습니다. | 원고 파일을 내려받아 HWPX를 지원하는 문서 프로그램에서 여세요. |
| PDF와 HWPX를 모두 찾고 있습니다. | 최종 원고 하나 원칙에 따라 사진 포함 최종 HWPX를 선택하는 구성입니다. |
| 처리시간 단위가 혼동됩니다. | 일부 그래프 축 숫자와 본문의 초 단위가 달라 원고의 위치를 함께 확인해야 합니다. |

<div align="center">

연구 방법과 결과, 다음에 확인할 과제를 함께 살펴볼 수 있습니다.

</div>
