# 엑셀 업체 위치 지도 - HTML 버전

Python/Streamlit 없이 정적 HTML 파일만으로 실행되는 업체 위치 지도입니다.
GitHub Pages에 바로 배포할 수 있습니다.

## 주요 기능

- 엑셀 파일 업로드: `.xlsx`, `.xls`, `.xlsm`, `.csv`
- 위도·경도 기준 지도 핀 표시
- 지도 핀 hover/클릭 시 표시 항목
  - 회사명
  - 주소
  - 업종
- 담당자, 연락처는 표시하지 않음
- 회사명, 주소, 업종 검색
- 가까운 위치 핀 자동 묶기
- 표시 데이터 CSV 다운로드

## 기본 컬럼 매핑

첨부 엑셀처럼 헤더가 없거나 자동 인식이 어려운 경우 아래 기준을 기본값으로 사용합니다.

| 항목 | 기본 컬럼 |
|---|---:|
| 회사명 | A열 |
| 업종 | B열 |
| 주소 | F열 |
| 위도 | G열 |
| 경도 | H열 |

화면 왼쪽에서 컬럼을 직접 바꿀 수 있습니다.

## 로컬에서 실행하기

압축을 푼 뒤 `index.html` 파일을 더블클릭하면 실행됩니다.

다만 브라우저 보안 정책이나 인터넷 CDN 차단 환경에서는 지도가 안 뜰 수 있습니다. 그 경우 아래처럼 간단한 로컬 서버를 실행하세요.

```bash
python -m http.server 8000
```

브라우저에서 아래 주소로 접속합니다.

```text
http://localhost:8000
```

## GitHub Pages 배포 방법

1. GitHub에서 새 저장소 생성
2. 이 폴더 안의 `index.html`, `README.md`, `.gitignore` 파일 업로드
3. 저장소의 `Settings` → `Pages` 이동
4. `Build and deployment`에서 Source를 `Deploy from a branch`로 선택
5. Branch를 `main`, Folder를 `/root`로 선택
6. `Save` 클릭
7. 잠시 후 GitHub Pages 주소가 생성됩니다.

## 개인정보 주의

실제 업체명, 주소, 담당자, 연락처가 들어있는 원본 엑셀은 GitHub에 올리지 않는 것을 권장합니다.
이 HTML 앱은 사용자가 브라우저에서 직접 엑셀을 업로드해서 사용하는 구조입니다.
엑셀 데이터는 서버로 전송되지 않고 브라우저 안에서만 처리됩니다.

## 사용 라이브러리

- Leaflet
- Leaflet.markercluster
- SheetJS

위 라이브러리는 CDN을 통해 불러옵니다. 인터넷 연결이 필요합니다.
