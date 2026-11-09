# clickless.co.kr 랜딩페이지 소스

(주)비욘드메디슨 클릭리스(Clickless) 공식 랜딩페이지 소스입니다.
2026-11-09 기준으로 운영 중인 https://clickless.co.kr 과 같은 파일입니다(배포본과 대조 완료).

## 구성

```
index.html          페이지 전체 (HTML + CSS + JS가 한 파일에 들어 있음)
favicon.ico
assets/
  clickless-logo.png
  app-home-ko.png, app-pain-ko.png, app-face-ko.png,
  app-habit-ko.png, app-report-ko.png   앱 화면 캡처
  dashboard.png                          의료진 대시보드 캡처
  favicon-32.png, favicon-512.png, apple-touch-icon.png
```

- 정적 페이지 1장입니다. 빌드 도구나 프레임워크, npm 패키지를 쓰지 않습니다.
- 외부 리소스는 Pretendard 웹폰트(jsDelivr CDN) 하나뿐입니다.
- 서버, DB, 폼 전송, API 키, 분석 스크립트가 없습니다.

## 페이지 섹션 (index.html)

| id | 내용 |
|---|---|
| `#problem` | 턱관절 증상 셀프 체크리스트 |
| `#what` | 클릭리스 소개 |
| `#evidence` | 임상 근거(막대그래프) |
| `#adoption` | 도입 현황 |
| `#clinics` | 처방 가능 치과 목록과 검색 |
| (aud 탭) | 환자용 / 의료진용 탭, 대시보드 이미지 |
| `#faq` | 자주 묻는 질문 |
| `#cta` | 문의와 언론보도 링크 |

## 자주 바뀌는 항목

- **처방 치과 목록:** `index.html` 하단 `<script>` 안의 `const CLINICS = [...]` 배열을 고칩니다.
  - 형식은 `['병원명','전화번호',1]`입니다.
  - 세 번째 값 `1`은 "처방 진행 중"이라는 뜻이고, 빼면 "처방 가능"으로 표시됩니다.
  - 현재 데이터는 2026.10.20 기준입니다.
  - 상단 총 개수 `<b id="clTotal">`도 함께 고칩니다.
- **수치와 카운트업 숫자:** 각 요소의 `data-count` 속성을 고칩니다.
- **그래프 길이:** `.bar-fill`의 `data-w`(%) 값을 고칩니다.
- **언론보도 링크:** `#cta` 근처의 `<a href>` 목록을 고칩니다.

## 로컬 확인

`index.html`을 브라우저로 열면 됩니다. 서버를 띄우려면 다음 명령을 씁니다.

```
python -m http.server 8000
```

## 배포

- 현재 Vercel 프로젝트 `clickless-landing`에 정적 사이트로 배포되어 있고, clickless.co.kr 도메인이 연결되어 있습니다.
- 배포 권한(Vercel 팀 초대)과 도메인 DNS 관리는 회사(운영 총괄 이나래)에 요청해 주세요.
- 배포 명령 예시(권한을 받은 뒤): 이 폴더에서 `vercel --prod`

문의: 이나래 COO, nr1322@beyondmedicine.kr
