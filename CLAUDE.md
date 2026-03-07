# MERGE CHRONICLE - 프로젝트 규칙

> 공통 규칙은 상위 폴더의 CLAUDE.md 참조

## 프로젝트 구조
- 단일 파일: `index.html` (HTML + CSS + JS 올인원)
- 기술: HTML5, CSS3, Vanilla JavaScript, Web Audio API, localStorage
- 외부 의존성: Google Fonts (Noto Sans KR) - 폰트만 CDN 사용

## 개발 참고 문서
- 상세 개발 문서: `개발문서.md` 참조 (게임 엔진, 데이터 구조, 밸런스 등 전체 명세)

## 작업 시 주의사항
- 게임 밸런스 상수는 스크립트 상단 GAME BALANCE 섹션에 집중되어 있음 (Single Source of Truth)
- 보드 크기는 GRID 상수(6x6)로 제어
- 테마는 CSS 커스텀 속성 기반 (다크/라이트 모드)
- 저장 데이터 키: `mc_save` (localStorage)
