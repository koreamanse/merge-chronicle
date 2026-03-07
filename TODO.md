# MERGE CHRONICLE - TODO

## 진행 예정

- [ ] Google 로그인 인앱 브라우저 차단 문제 해결
  - 증상: 카카오톡 등 SNS에서 URL 공유 후 인앱 브라우저로 열면 Google 로그인 시 403 오류 (disallowed_useragent)
  - 원인: Google이 보안 정책상 인앱 브라우저(WebView)에서의 OAuth 로그인을 차단
  - 대상 인앱 브라우저: 카카오톡, 라인, 페이스북, 인스타그램, 네이버, 트위터 등
  - 해결 방안:
    1. User-Agent 기반 인앱 브라우저 감지 스크립트 추가
       - KAKAOTALK, Line, FBAN(페이스북), Instagram, NAVER, Twitter 등 키워드 감지
    2. 감지 시 외부 브라우저로 자동 리다이렉트
       - Android: intent:// 스킴으로 Chrome 실행
       - iOS: window.open() 또는 location.href로 Safari 유도
       - 공통 폴백: 외부 브라우저에서 열어달라는 안내 메시지 표시
    3. 적용 위치: index.html 최상단 script에서 페이지 로드 전 즉시 실행
    4. 로그인 버튼 클릭 시에도 한번 더 체크하여 이중 방어

- [ ] 라이트 모드 시각 품질 개선 - 뿌연 효과(blur/overlay) 제거/조정
  - 증상: 다크모드에서는 자연스러운 blur/반투명 효과가 라이트모드에서는 화면이 뿌옇게 보이고, 텍스트 가독성 저하, 이미지가 흐리게 보임
  - 원인: 다크모드 기준으로 디자인된 backdrop-filter blur, 반투명 오버레이, 배경 오브(title-bg-orbs) 등이 라이트모드에서 역효과
  - 해결 방안:
    1. 타이틀 배경 오브(.title-bg-orbs) - 라이트모드에서 opacity 대폭 줄이거나 제거
    2. backdrop-filter: blur() - 라이트모드에서 blur 값 줄이거나 제거
    3. 반투명 배경(rgba) - 라이트모드에서 불투명도 높여서 선명하게
    4. 텍스트 색상 대비 - 라이트모드 전용 색상 변수 점검
  - 대상 화면: 타이틀 화면 우선, 이후 전체 화면 점검

---

## 완료
