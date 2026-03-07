# MERGE CHRONICLE - 프로젝트 규칙

> 공통 규칙은 상위 폴더의 CLAUDE.md 참조

## 프로젝트 구조
- `index.html`: 게임 메인 파일 (HTML + CSS + JS 올인원)
- `terms.json`: 이용약관 내용 (버전 관리, 동적 로드)
- 기술: HTML5, CSS3, Vanilla JavaScript, Web Audio API, localStorage
- 외부 의존성: Google Fonts (Noto Sans KR) - 폰트만 CDN 사용

## 개발 참고 문서
- 상세 개발 문서: `개발문서.md` 참조 (게임 엔진, 데이터 구조, 밸런스 등 전체 명세)

## 랭킹 산정 기준
- 1순위: 트로피 개수 (명예의 전당 획득 수가 많을수록 상위)
- 2순위: 종합 점수 (트로피 개수가 동일한 경우 총 점수가 높을수록 상위)

## Google 로그인 및 개인정보 현황
- Firebase Auth 기반 Google 로그인 사용
- Firestore 컬렉션:
  - `users`: 회원 데이터 (uid를 문서 ID로 사용, 유저당 1개)
    - name, email, photoURL, createdAt(가입일), lastLogin(마지막 로그인)
    - agreedAt(약관 동의일), agreedVersion(동의한 약관 버전)
    - 최초 로그인 시 약관 동의 팝업 표시 → 동의 시 회원 문서 생성, 거부 시 로그아웃
    - 재로그인 시 프로필 정보 및 lastLogin 업데이트
  - `scores`: 게임 점수 기록 (게임 오버 시마다 추가)
    - uid, name, email, photoURL, score, merges, maxCombo, hof, timestamp
- displayName은 실명 인증 아님 (사용자가 자유롭게 수정 가능한 닉네임 성격)
- 탈퇴 기능: 설정 > DELETE ACCOUNT (users 문서 + scores 전체 기록 + Auth 계정 삭제)
- 약관 동의: 최초 로그인 시 terms.json 기반 약관 팝업 표시, 동의 기록(agreedAt, agreedVersion) 저장
- 약관 내용: terms.json 파일에서 관리 (버전, 섹션별 내용)

## 작업 시 주의사항
- 게임 밸런스 상수는 스크립트 상단 GAME BALANCE 섹션에 집중되어 있음 (Single Source of Truth)
- 보드 크기는 GRID 상수(6x6)로 제어
- 테마는 CSS 커스텀 속성 기반 (다크/라이트 모드)
- 저장 데이터 키: `mc_save` (localStorage)
