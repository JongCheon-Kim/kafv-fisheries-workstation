# 수산정보 워크스테이션 v1.2 — PASS 승인 새 이미지 반영 및 회귀검수

- **기준 디자인:** `수산정보_워크스테이션_포스터.png` (사용자 PASS 이미지, 1672×941px)
- **기준 배포본:** `v1.1` (기능·접속 주소 보존)
- **제작일:** 2026-11-08
- **판정:** 정적 제작·QR·클릭/렌더링 로컬 검수 대상. GitHub Pages 게시 후 최종 확인 필요.

## 적용 범위
1. PASS한 새 이미지의 모든 제목·상세 문구·마크·일러스트를 원본으로 사용한다.
2. 이미지 안에 그려진 비기능성 QR 패턴 **8곳만** 실제 URL로 인코딩한 QR로 치환했다.
3. 기존 CSS/SVG 문자 덧씌우기 방식을 제거하여 글자 굵기·해상도 불일치가 발생하지 않게 했다.
4. 8개 카드 전체에 해당 주소의 투명 클릭 영역을 연결했다. 새 탭으로 열린다.
5. 제3차시 `?step=theory`를 유지하여 이론 우선 시작한다.
6. 수산정보 5종은 `AI`·`앱` 접미사 없이 표시한다.
7. PC 이미지·모바일 카드 별도 레이아웃 및 브라우저 축소 시 세로 중앙 배치를 유지한다.

## 검수 항목
| 검사 | 결과 |
|---|---|
| 승인 이미지 원본 대조 | QR 8개 영역 외 변경 픽셀 **0개** |
| 교육교재 3 + 수산정보 5 | 8/8 존재 |
| PC 카드 클릭 ↔ links.json | 8/8 정확히 일치 |
| 모바일 카드 클릭 ↔ links.json | 8/8 정확히 일치 |
| 개별 QR 파일 실제 디코딩 | 16/16 정확히 URL과 일치 |
| 완성 포스터 내 QR 크롭 디코딩 | 8/8 정확히 URL과 일치 |
| 제3차시 이론 진입 | `?step=theory` 연결 유지 (온라인 서버 화면은 재확인 필요) |
| 브라우저 크기별 렌더링 | 5/5 PASS — desktop 1672×1000, laptop 1366×768, zoomout 2300×1200, tablet 900×1120, mobile 390×844 |
| ZIP 무결성 | ZIP 검수 PASS — 파일 CRC 및 테스트 결과 확인 |

## 유의점
- QR에 인코딩된 URL과 외부 사이트의 실제 접속 가능 여부는 서로 다르다. 수산 정보 서비스 5종의 정상 접속·내부 작동은 사용자의 GitHub Pages 공개 환경에서 최종 확인해야 한다.
- 이미 공개한 `v1.1`의 `README.md`의 저작권 고지는 유지한다.
- 이 버전은 GitHub 저장소 `kafv-fisheries-workstation`의 기존 루트 파일을 교체하는 배포본이다. **압축 파일 자체가 아닌 내부 파일 전체**를 업로드한다.

## QR 매핑
- `marketing`: PASS — https://jongcheon-kim.github.io/kafv-fishing-village-consultant/?step=theory
- `quality`: PASS — https://jongcheon-kim.github.io/kafv-lesson4-fish-quality-distribution/
- `customer`: PASS — https://jongcheon-kim.github.io/kafv-lesson5-seafood-customer-service-rpg/
- `tourism`: PASS — https://jongcheon-kim.github.io/kafv-fishing-village-tourism/
- `company`: PASS — https://jongcheon-kim.github.io/fisheries-company-info-ai-v2/
- `price`: PASS — https://jongcheon-kim.github.io/kafv-fish-price-ai-v4/
- `direct`: PASS — https://jongcheon-kim.github.io/fisheries-direct-payment-ai/
- `dictionary`: PASS — https://jongcheon-kim.github.io/kafri-health-encyclopedia/

## 최종 브라우저 회귀검수

| 뷰포트 | 판정 | 내용 |
|---|---|---|
| Desktop 1672×1000 | PASS | 승인 이미지, 8개 카드 클릭 판정, 정적 이미지 로드 |
| Laptop 1366×768 | PASS | 카드 클릭 8/8, 세로 중앙 정렬, 가로 넘침 없음 |
| Zoom-out 유사 뷰포트 2300×1200 | PASS | 상단 밀착 방지, 가운데 정렬, 8개 클릭 판정 |
| Tablet 900×1120 | PASS | 반응형 2열 카드, QR/이미지 8개 로드 |
| Mobile 390×844 | PASS | 반응형 1열 카드, QR/이미지 8개 로드 |

검수 방법: 브라우저 DOM 기준 `elementFromPoint` 클릭영역과 이미지 `naturalWidth`, 스크립트 예외, 가로 넘침을 검사한 뒤 실제 렌더링 이미지를 시각 검토했다. 보안 제한으로 인한 브라우저 로컬 파일 탐색 차단을 피하기 위해 검수 시에만 정적 이미지들을 `data:` URL로 대체하였으며, 배포본 자체는 정상적인 상대 경로로 유지했다.

### 최종 검수 판정
**배포용 ZIP 파일 구성: PASS / 로컬 브라우저 5종 및 QR 연결: PASS / 공개 GitHub Pages 운영 PASS: 배포 후 확인.**
