# MERGE CHRONICLE - 프로젝트 규칙

> 공통 규칙은 상위 폴더의 CLAUDE.md 참조

## 프로젝트 구조
- 단일 파일: `index.html` (HTML + CSS + JS 올인원)
- 기술: HTML5, CSS3, Vanilla JavaScript, Web Audio API, localStorage
- 외부 의존성: Google Fonts (Noto Sans KR) - 폰트만 CDN 사용

## 개발 참고 문서
- 상세 개발 문서: `개발문서.md` 참조 (게임 엔진, 데이터 구조, 밸런스 등 전체 명세)

## 랭킹 산정 기준
- 1순위: 트로피 개수 (명예의 전당 획득 수가 많을수록 상위)
- 2순위: 종합 점수 (트로피 개수가 동일한 경우 총 점수가 높을수록 상위)

## Google 로그인 및 개인정보 현황
- Firebase Auth 기반 Google 로그인 사용
- Firestore에 저장하는 정보: displayName (Google 계정 이름), email (Gmail 주소), photoURL (프로필 사진 URL)
- displayName은 실명 인증 아님 (사용자가 자유롭게 수정 가능한 닉네임 성격)
- 현재 별도 개인정보 동의 절차 없음 (수집 정보가 공개 프로필 수준이므로 보류)
- 이메일 수집/저장 또는 상업적 전환 시 개인정보 동의 체계 구축 필요

## 작업 시 주의사항
- 게임 밸런스 상수는 스크립트 상단 GAME BALANCE 섹션에 집중되어 있음 (Single Source of Truth)
- 보드 크기는 GRID 상수(6x6)로 제어
- 테마는 CSS 커스텀 속성 기반 (다크/라이트 모드)
- 저장 데이터 키: `mc_save` (localStorage)
