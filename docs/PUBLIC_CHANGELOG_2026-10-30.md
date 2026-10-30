# 📝 2026-10-30 연구 원문과 차수 공개 보완

원격 기준 커밋: `ab86f6813e9bd3a26330bd7e4682c55e11ef9b30`

기존 공개 파일을 삭제하지 않고 원본 논문·문서·연구 코드·결과표·발표자료를 추가했습니다. 연구 번호와 원본 폴더 차수·원고 수정·발표 차수를 구별하고 각 파일·직전 단계의 전체 차이와 크기·SHA-256을 연결했습니다. 현재 원문 PDF/HWP와 나중 공식 URL 교체 지점은 [논문 표](PAPERS.md)에 있습니다.

## 실제 수정 파일

- `CHANGELOG.md`: 현재 원문·이전 정제 사본과 차수 안내의 정합성을 보완했습니다.
- `README.md`: 논문 직접 링크·모든 실제 단계·파일 종류·비교를 보완하고 기존 이모지 구조를 유지했습니다.
- `docs/VERSIONS.md`: 현재 원문·이전 정제 사본과 차수 안내의 정합성을 보완했습니다.
- `docs/versions/final-paper.md`: 현재 원문·이전 정제 사본과 차수 안내의 정합성을 보완했습니다.

## 실제 추가 파일

- `docs/PAPERS.md`
- `docs/PUBLIC_CHANGELOG_2026-10-30.md`
- `docs/REVISION_INDEX.md`
- `docs/revision-diffs/final.diff`
- `docs/revision-diffs/illustrated.diff`
- `docs/revision-diffs/initial.diff`
- `docs/revision-diffs/references.diff`
- `docs/revision-manifests/final.json`
- `docs/revision-manifests/illustrated.json`
- `docs/revision-manifests/initial.json`
- `docs/revision-manifests/references.json`
- `docs/revisions/final.md`
- `docs/revisions/illustrated.md`
- `docs/revisions/initial.md`
- `docs/revisions/references.md`
- `원고단계/사진 포함 최종/그림/image1.jpeg`
- `원고단계/사진 포함 최종/그림/image10.png`
- `원고단계/사진 포함 최종/그림/image11.png`
- `원고단계/사진 포함 최종/그림/image2.png`
- `원고단계/사진 포함 최종/그림/image3.png`
- `원고단계/사진 포함 최종/그림/image4.png`
- `원고단계/사진 포함 최종/그림/image5.png`
- `원고단계/사진 포함 최종/그림/image6.png`
- `원고단계/사진 포함 최종/그림/image7.png`
- `원고단계/사진 포함 최종/그림/image8.png`
- `원고단계/사진 포함 최종/그림/image9.png`
- `원고단계/사진 포함 최종/그림/result.png`
- `원고단계/초기/원고.hwp`
- `원고단계/초기/원고.pdf`
- `원고단계/최종/원고.hwp`
- `원고단계/최종/원고.pdf`
- `참고자료/ATTRIBUTION.md`
- `참고자료/Binarization_연구노트.pdf`
- `참고자료/electronics-14-03455.pdf`

## 비교와 검증 범위

- [전체 단계·직전 단계 차이](REVISION_INDEX.md)에 파일별 근거와 원고 설명을 연결했습니다. 공백·주석·코드셀·Markdown·텍스트·수치·실험 설정을 전체 비교하며 ipynb의 바이너리 이미지 출력만 바이트 길이·SHA-256·원문 링크로 표시합니다. 원문 ipynb 자체는 보존합니다.
- UTF-8, 비밀 패턴, 실제 로컬 링크, 노트북 JSON, source/public SHA 및 코드 셀 보존, PDF 열기를 검사했습니다. 원본0바이트 노트북은 그대로 남기며 JSON·실행·성능 근거에서 제외합니다.
- 의료 원본 후보가 포함된 노트북 이미지 출력만 제외한 사본은 비공개 대응표에 source/public 해시와 변환 이유를 구별해 기록했습니다.
- 원문에 실린 본인·공동저자의 성명·소속·이메일·전화·ORCID·이력·사진은 최신 공개 지시에 따라 보존합니다. 기존 원격 정제 사본은 이력으로 유지합니다.
- 인증키·비밀번호, 대용량 모델·원데이터, 연구와 무관한 결제 자료·도구 설치 캐시와 본인 비저자·공개권한 근거 불명확 외부 원고는 별도 제외·보류 근거로 관리합니다. 원본은 수정·삭제하지 않았습니다.
- 새 학습·임상·제조 장비·추천 성능 실험은 수행하지 않았습니다. 저장 표와 원고 보고값을 새 실측으로 소개하지 않습니다.
- 이 변경 기록 시점에는 원격 쓰기·커밋·푸시를 수행하지 않았고 부모 통합 독립 검토와 반영을 기다립니다.
