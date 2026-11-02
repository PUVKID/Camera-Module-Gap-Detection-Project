<div align="center">

# 📏 사진 포함 최종 · 정렬부터 측정까지 읽는 원고

**사진·본문·소속·사사를 포함한 최종 HWPX와 같은 판의 12쪽 PDF로 갭 검출 연구를 읽는 단계입니다.**

**기술 분류:** 컴퓨터 비전 › 제조 영상 전처리 › 이진화·동적 ROI·갭 길이 측정

[목적](#purpose) · [기능](#features) · [입출력](#flow) · [구성](#files) · [준비](#setup) · [사용법](#usage) · [결과](#results) · [제약](#limits) · [변경](#changes)

</div>

<a name="purpose"></a>

## 🎯 이 단계에서 하는 일

이 연구는 이진화 영상 자체의 모양뿐 아니라 ROI에서 얻는 갭 길이의 안정성을 비교합니다. 현재 원문을 읽으면서 초기·최종 HWP·사진 포함 최종의 편집 차이를 아래 비교와 함께 확인할 수 있습니다.

<a name="features"></a>

## 🧩 주요 기능과 처리 방식

| 구성 | 실제 역할 |
| --- | --- |
| 삽입 연구 그림 | 정렬·ROI·필터·이진화의 차이를 사진과 도표로 확인합니다. |
| 최종 원문 | 편집 원본과 PDF의 본문·그림을 같은 연구 단계로 연결하고 저자·소속·사사를 원문 그대로 제공합니다. |
| 동적 정렬 | YOLO 키포인트의 left_top·right_top을 기준으로 회전·위치를 맞춥니다. |
| 전처리 비교 | 공간·주파수·비국소 필터와 순차 조합이 이진화에 미치는 영향을 설명합니다. |
| 갭 측정 | ROI의 6개 샘플라인과 1D 투영을 이용해 길이를 산출합니다. |
| 평가 지표 | 평균·표준편차·누락률·이상치율과 PSNR·SSIM·처리시간을 구분합니다. |

<a name="flow"></a>

## 🔄 입력 → 처리 → 출력

| 입력 | 처리 | 출력·읽을 결과 |
| --- | --- | --- |
| 카메라 모듈 검사 영상 | 키포인트 기반 회전·위치 정렬 | 비교할 ROI |
| 정렬 영상 | 필터와 이진화·1D 투영 | 샘플라인의 갭 길이 |
| 측정값과 기준 영상 | 편차·누락·이상치·영상 품질 비교 | 조건별 신뢰성과 처리 비용 |

<a name="files"></a>

## 📁 파일과 핵심 처리

| 파일 | 이용 방법 |
| --- | --- |
| [논문/최종_논문.pdf](../../%EB%85%BC%EB%AC%B8/%EC%B5%9C%EC%A2%85_%EB%85%BC%EB%AC%B8.pdf) | 전체 원문·도표 읽기 |
| [논문/최종_논문.hwpx](../../%EB%85%BC%EB%AC%B8/%EC%B5%9C%EC%A2%85_%EB%85%BC%EB%AC%B8.hwpx) | 같은 판의 편집 원본 |

<a name="setup"></a>

## ⚙️ 환경과 설정

| 항목 | 조건·기본값 |
| --- | --- |
| 자료 | 원고 PDF와 같은 판의 HWPX |
| 측정 | 동적 ROI와 6개 샘플라인 |
| 비교 대상 | 전처리 필터·이진화·순차 조합 |
| 입력 준비 | 제조 영상과 정렬·임계값 조건은 별도 실험 환경에서 준비 |

<a name="usage"></a>

## 📖 읽고 활용하는 순서

1. 연구 질문에서 갭 길이 측정의 안정성과 이진화 품질이 어떻게 연결되는지 읽습니다.
2. 키포인트 정렬→ROI→필터→이진화→샘플라인 측정 순서로 처리 방법을 따라갑니다.
3. 필터별 표·예시 그림에서 길이 편차와 누락·이상치 비율을 함께 확인합니다.
4. 영상 품질 지표와 실제 측정 신뢰성·처리시간이 같은 지표가 아님을 구분해 결과를 읽습니다.

<a name="results"></a>

## 📊 결과를 읽는 방법

갭 평균만으로 조건을 고르지 않고 표준편차·누락률·이상치율을 함께 읽습니다. PSNR·SSIM이 높아도 갭 경계를 더 안정적으로 찾는지는 측정 결과로 따로 확인합니다.

원고의 장수·시간·필터 서술에는 내부 차이가 있습니다. 이 차이는 원고를 읽는 제약으로 설명하고 숫자를 새 측정값으로 정정하지 않았습니다.

<a name="limits"></a>

## 🛠️ 알려진 제약과 확인 지점

| 상황 | 확인할 내용 |
| --- | --- |
| 자료 수 표기 | 초록의 약 1000장과 본문의 546장 등 내부 표기를 위치별로 확인합니다. |
| 시간 비교 | 일부 그래프 축과 본문의 초 단위가 달라 해당 그림·문단을 함께 읽습니다. |
| 재현 준비 | 공개 자료는 연구 원고와 그림입니다. 제조 원영상 전체·실행 가중치·장비 설정은 별도로 필요합니다. |

<a name="changes"></a>

## 🔀 이전 단계와의 변화

HWP 단계를 바탕으로 사진 포함 최종 HWPX와 같은 판의 PDF를 연결했습니다. 기존 원고 단계의 설명과 직전 비교는 보존합니다.

[🔎 직전 단계 전체 비교·구성](../revision-diffs/illustrated.diff) · [📋 전체 파일 크기·해시](../revision-manifests/illustrated.json)

<details>
<summary>📎 이 단계의 파일 기록과 전체 해시</summary>

아래 표는 해당 단계가 기록될 당시의 파일 정보입니다. 현재 첨부는 [프로젝트 자료 안내](../PAPERS.md)에서 확인할 수 있습니다.

| 파일 | 종류 | 바이트 | SHA-256 |
|---|---|---:|---|
| [최신 편집 원문](../../%EB%85%BC%EB%AC%B8/%EC%B5%9C%EC%A2%85_%EB%85%BC%EB%AC%B8.hwpx) | .hwpx | 9341032 | `15a861e0c2e32f065966cf7524dd5933b86aab2fd62ec0781017aeb2df44e3c5` |
| `논문/최종_논문.pdf` | .pdf | 800724 | `1dbb7d4d6d39fad3d271d0eb3d1c1384b17280ca00374fc2528bf6a76f5a698a` |
| [원고단계/사진 포함 최종/그림/image1.jpeg](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image1.jpeg) | .jpeg | 189454 | `9430d62ae17c3f880fa7565037f0afeda2afcff6fdc29560a687091dbba5d1b0` |
| [원고단계/사진 포함 최종/그림/image10.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image10.png) | .png | 135008 | `c5c93d6fa301b8702f14511b5cb824faeed84b8da36854d71da92b208ee4b62f` |
| [원고단계/사진 포함 최종/그림/image11.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image11.png) | .png | 218137 | `ef768e7708269f9c6e1384a9f085cddefdb421ecac248cd8bc1fcb4480acd5eb` |
| [원고단계/사진 포함 최종/그림/image2.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image2.png) | .png | 90183 | `2eb0e7d384c82ca00f872b57dd244786871dbb895299676f04a953993a1f5641` |
| [원고단계/사진 포함 최종/그림/image3.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image3.png) | .png | 1173238 | `6d54a2d528a514382b1bf94d757c68085be154b41bd354b9b0fdb88587796ac3` |
| [원고단계/사진 포함 최종/그림/image4.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image4.png) | .png | 48046 | `21a0b70cb0cb91dcfdff7a4213bf7044407fea2a12484ad5af701869242ba334` |
| [원고단계/사진 포함 최종/그림/image5.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image5.png) | .png | 335971 | `0788420f9f1c58bbfa57f5740566be0e36311a3fd1dbd97993dfb89fc4fe0a40` |
| [원고단계/사진 포함 최종/그림/image6.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image6.png) | .png | 152195 | `2baa50867211717a6073754140fb1cd8e4c12e8c4b7f7bd7d5433e90d16670b9` |
| [원고단계/사진 포함 최종/그림/image7.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image7.png) | .png | 48593 | `86d62918b54da1b7a9227e6aac994ee3ea1eecbdc00cc9cca26fd9c399f80000` |
| [원고단계/사진 포함 최종/그림/image8.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image8.png) | .png | 36662 | `24d9cd997504fcbfa4671ea3fd5158553a9fddc9578d2c2f7cc9d1ef81556696` |
| [원고단계/사진 포함 최종/그림/image9.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/image9.png) | .png | 207660 | `9c0ed08abd5c9678aa3f38d928ab37bf630a7c283c07d732b8178d1135a0c266` |
| [원고단계/사진 포함 최종/그림/result.png](../../%EC%9B%90%EA%B3%A0%EB%8B%A8%EA%B3%84/%EC%82%AC%EC%A7%84%20%ED%8F%AC%ED%95%A8%20%EC%B5%9C%EC%A2%85/%EA%B7%B8%EB%A6%BC/result.png) | .png | 3528774 | `29099f15e669ae0405104fb8a953545c910780a1a2b343324709601a13860b29` |

</details>

---

[🏠 프로젝트](../../README.md) · [🗂️ 전체 차수](../REVISION_INDEX.md) · [📁 자료 폴더](../../%EB%85%BC%EB%AC%B8) · [⬅️ 최종 원고 · HWP/PDF 단계](final.md)
