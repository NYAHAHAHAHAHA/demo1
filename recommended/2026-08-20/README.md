# Daily paper recommendations — 2026-08-20

## 검색 정보

- **연구 기준일**: 2026-08-20 (Asia/Seoul 기준 어제)
- **실제 검색 범위**: 2026-08-20(당일) → 결과 없음, 2026-08-14 ~ 2026-08-20(7일) → 결과 없음, **2026-07-22 ~ 2026-08-20(30일)** → 최종 채택
- **검색 쿼리**: `chest X-ray deep learning multi-label classification`

## 코호트 요약 (환자 단위 값 없음)

- 총 272건의 영상 레코드, 153명의 고유 환자(patient_key 기준)
- 5개 기관(INST01~05)에서 수집, 기관별 48~62건으로 비교적 고르게 분포
- 성별: 남성 136 / 여성 136, 연령 범위 9~87세 (평균 약 51.5세)
- 촬영 자세: PA 184건, AP 88건
- 소견(findings_label) 분포: No Finding 145건이 최다이며, 나머지는 Infiltration(21), Atelectasis(16), Nodule(7), Fibrosis(6), Effusion(6), Cardiomegaly(5) 등 단일 소견과 Effusion|Infiltration(5), Effusion|Pneumothorax(4), Atelectasis|Infiltration(4) 등 다중 소견 공존 사례가 다수 포함
- 전체 레코드가 합성 데이터(is_synthetic = true)로 표시됨

## 채택 축 (axes)

- **기관 간 일반화**: 5개 기관에 걸친 데이터 특성상 모델의 기관 간 성능 일반화가 핵심 관심사
- **다중 병리 라벨 및 공존**: 다수 증례가 2개 이상 소견을 동시에 가지는 다중 라벨 구조
- **보고서 텍스트-영상 결합**: findings_label/report_text와 image_file이 함께 존재해 텍스트-영상 결합 연구와 맞물림
- **합성 데이터 활용**: 코호트 전체가 합성 데이터로 구성되어 있어 합성 데이터 기반 학습·증강 연구와 직결

## 채택 논문

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
*Nature Biomedical Engineering, 2026-07-22*

임상 개념 임베딩 기반의 감사 가능한(auditable) 흉부 X-ray 파운데이션 모델로, 미국·유럽·아시아 4개 외부 데이터셋에서 검증되었다. 우리 코호트는 5개 기관, 다중 병리 공존 구조를 갖고 있어 CLEAR가 검증한 다기관·다중 병리 설정과 유사하다. 다만 우리 데이터는 272건 규모로 CLEAR의 23만 명 이상 검증 코호트와 규모 차이가 커 동일한 일반화 수준을 재현하기는 어렵다.

- 링크: https://doi.org/10.1038/s41551-026-01741-4

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
*npj Digital Medicine, 2026-07-28*

판독문 전체 텍스트를 영상 특징과 결합해 픽셀 단위 주석 없이도 병변 분할을 학습하는 프레임워크. 우리 데이터는 image_file, findings_label, report_text가 함께 저장되어 있고 다중 소견 공존 사례가 다수 있어 텍스트-영상 결합 분할 접근을 시험해볼 구조를 갖췄다. 다만 우리에게는 전문가 분할 주석이 없어 분할 정확도 자체는 검증할 수 없다.

- 링크: https://doi.org/10.1038/s41746-026-03051-0

### 3. UniMedDiff: a knowledge-enhanced diffusion model for medical image generation from clinical reports
*npj Digital Medicine, 2026-08-13*

판독문 텍스트로부터 병리학적으로 다양한 흉부 X-ray를 생성하는 확산 모델로, 실제 데이터 1% 증강만으로 전체 데이터 학습에 근접한 분류 성능을 보고한다. 우리 코호트는 전 증례가 합성 데이터이며 11개 안팎의 폐 병리가 단독·복합으로 기록되어 있어 관련성이 높다. 다만 이미 합성된 데이터이므로 실제 데이터 기반 증강 효과를 직접 검증해줄 수는 없다.

- 링크: https://doi.org/10.1038/s41746-026-03135-x

## 검토 안내

위 추천은 자동 검색·요약 결과이며, 임상 적용 전 반드시 담당 의료진의 검토가 필요합니다.
