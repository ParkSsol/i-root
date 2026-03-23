# Software Design Specification (SDS)

## 아이루트





**Team information:**
|    **Project title**    |                                                                                                                  아이루트                                                                                                                   |
| :---------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|         **학번**          |                                                                                                                 **이름**                                                                                                                  |
|                 |                                                                                                                                                                                                                                      |
|                 |                                                                                                                                                                                                                                       |
|                 |                                                                                                                                                                                                                                      |
|                 |                                                                                                                                                                                                                                      |
|                |                                                                                                                                                                                                                                      |
|                 |                                                                                                                        
---

## Revision history

| Revision date | Version # | Description | Author |
|---------------|-----------|-------------|--------|
| 11/07/2025    | 1.00      | 1차완성 | Author name |
| | | | |
| | | | |
| | | | |
| | | | |
---

## Contents
1. Introduction  -------------------[Introduction](#1-introduction)
2. Use case analysis  --------------[Use case analysis](#2-use-case-analysis)
3. Class diagram  ------------------[Class diagram](#3-class-diagram)
4. Sequence diagram  ---------------[Sequence diagram](#4-sequence-diagram)
5. State machine diagram  ----------[State machine diagram](#5-state-machine-diagram)
6. User interface prototype  -------[User interface prototype](#6-user-interface-prototype)
7. Implementation requirements  ----[Implementation requirements](#7-implementation-requirements)
8. Glossary  -----------------------[Glossary](#8-glossary)
9. References  ---------------------[References](#9-references)

---

## Authors for each section

- Introduction – 
- Use case analysis – 
- Class diagram – 
- Sequence diagram – 
- State machine diagram – 
- User interface prototype –  
- Implementation requirements – 
- Glossary – 
- References – 

---

## 1. Introduction





---

## 2. Use case analysis
- Use case diagram




## 회원관리

1. 소셜 로그인
2. 일반 로그인
3. 회원가입
4. 내 프로필 조회
5. 내 프로필 수정
6. 소프트 삭제(계정 탈퇴)
7. 로그아웃
8. 토큰 재발급
9. 비밀번호 변경
10. 비밀번포 찾기
11. 사용자 유형 선택(학부모, 학원, 관리자)

## AI

12. 학생 성적 입력
13. 성적 그래프 추이
14. 맞춤 학습 자료 추천
15. 성적 분석 리포트
16. 학습 패턴 분석
17. 자주 틀리는 문제 분석
18. 자주 틀리는 유형으로 복습 문제 생성
19. 학생 맞춤 학습 진도 설계
20. 학생 맞춤 과목별 공부 방식 제안
21. 학생 자기 평가 입력란 (메타 인지)
22. 학생 학습 패턴 분석
23. 강사 피드백 입력란
24. 성장 예측 (지금 추세로 갔을 때 다음 시험 성적 예상)
25. 위험 학생 탐지 (성적 하락 추세, 학습량 감소 등)
26. 목표 기반 학습 추천
27. 강점 영역 분석(안정적인 부분)
28. 요약 리포트(성적 상승, 하락, 오답 유형 등)
29. 강사용 지도 포인트 추천
30. 복습 주기 및 복습 내용 추천
31. 문제 난이도 설정

## GPS

1. 학생 탑승 알림
2. 학생 하차 알림
3. 실시간 위치 추적
4. 도착 예정 시간
5. 정류장별 도착 예정 시간 조회
6. 차량 이동 경로 및 노선 조회
7. 경로 이탈 감지 (등록된 경로에서 크게 벗어나면 알림)
8. 비정상 정차 알림(너무 긴 시간 차량 정차 시)
9. 지각 위험 알림(도착 지연 예상 시 알림)
10. 탑승 학생 미리 알림 (3호차-누구, 누구, 누구 탑승)
11. 차량 및 기사 정보 조회(기사 연락처, 차량 번호 등)
12. 미탑승, 미하차 시 알림
13. 긴급 연락 (문제 시 차량 기사나 학원 관리자가 보호자와 빠른 연락 가능)
14. 지연 원인 표시(교통체증, 장시간 정차 등)
15. 기사님께 최적의 노선 추천(빠른 경로 및 안전 경로 추천)
16. 탑승 가능 좌석 수 표시 (차량 별 남은 자리 확인 용도)
17. 위치 공유 시간 제한(운행 시간에만 차 위치 공유)

## 게시판

1. 개시판 생성
2. 게시판 목록 조회
3. 게시판 글 올리기
4. 게시판 사진 등록
5. 학원 페이지 조회
6. 다이렉트 메시지
7. 댓글 작성
8. 게시글 수정/삭제
9. 게시글 태그
10. 공지사항 안내
11. 이벤트, 홍보 게시판
12. 1:1 문의 게시판

---
## 회원 관리

### **Use case #1 : GitHub OAuth 회원가입**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
  User level  

- **Author**  
  박솔

- **Last Update**  
  2026.03.24

- **Status**  
  Design

- **Primary Actor**  
  Non-member User (비회원 사용자)

- **Preconditions**  
  1. 사용자는 GitHub 계정을 보유하고 있으며 GitHub 인증에 정상적으로 접근할 수 있어야 한다.
  2. 서버는 GitHub OAuth App(Client ID / Client Secret)과 연결된 상태여야 한다.
  3. 백엔드는 다음 엔드포인트를 제공한다.
   - GET /api/auth/github/login : GitHub 인증 요청
   - GET /api/auth/github/callback : GitHub Access Token & user info 처리
  4. Supabase PostgreSQL DB 연결이 정상이어야 한다.

- **Trigger**  
  사용자가 “GitHub 로그인” 버튼 클릭 → GitHub OAuth 흐름 시작.

- **Success Post Condition**  
  1. GitHub에서 제공한 github_id로 새로운 UserEntity가 자동 생성됨.
   - githubId: GitHub API에서 받은 고유 ID
   - isAdmin = false
   - createdAt = now
   - deletedAt = null
   - commitCount, issueCount, prCount = 0
  2. 생성된 유저는 DB(users 테이블)에 저장된다.
  3. 서버는 유저 정보 기반으로 JWT AccessToken + RefreshToken을 발급해 클라이언트에 반환한다.
  4. 사용자는 로그인된 상태로 서비스 메인 페이지로 이동한다.

- **Failed Post Condition**  
 1.  GitHub Access Token이 정상 발급되지 않음 (“GitHub 액세스 토큰이 응답에 없습니다.” 오류 포함)
  2.GitHub API 호출 실패
  3. DB 저장 실패
  4. OAuth redirect URL 오류
   → UserEntity 생성 X / JWT 발급 X
 클라이언트는 GitHub 오류 팝업 또는 ‘다시 시도’ 안내 메시지를 표시한다.

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | 사용자가 “GitHub 로그인” 버튼을 클릭한다.                                                                           |
| 1    | 클라이언트는 GitHub Authorization Endpoint로 리다이렉트한다.                                                        |
| 2    | 사용자는 GitHub에서 로그인 및 권한 동의를 완료한다.                                                                      |
| 3    | GitHub은 `authorization_code`를 서버의 `/callback` URL로 전달한다.                                              |
| 4    | 서버의 `GithubAuthService`는 code를 이용해 GitHub Access Token을 요청한다.                                         |
| 5    | GitHub Access Token 획득 성공 시, 서버는 GitHub User API를 호출한다.                                               |
| 6    | GitHub API 응답에서 `github_id`(고유 식별자)를 추출한다.                                                            |
| 7    | 서버는 DB에서 `githubId`가 존재하는지 조회한다.<br> - 존재하면 → 기존 계정으로 로그인 처리<br> - 존재하지 않으면 → 새로운 `UserEntity`를 생성한다. |
| 8    | 생성된(or 조회된) UserEntity 정보를 기반으로 JWT AccessToken & RefreshToken을 생성한다.                                 |
| 9    | 서버는 200 OK와 함께 JWT 및 사용자 정보를 클라이언트에 반환한다.                                                             |
| 10   | 클라이언트는 로그인 성공 상태로 메인 화면 또는 대시보드로 이동한다.                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | GitHub Access Token 응답에 `access_token`이 없으면 “GitHub 액세스 토큰이 응답에 없습니다.” 오류 반환(현재 네가 만난 오류). |
| 5a   | GitHub API 서버 장애 또는 rate limit 초과 시 “GitHub 사용자 정보를 가져올 수 없습니다.” 오류 반환.                    |
| 7a   | DB 조회 중 장애 발생 시 “계정 정보를 확인할 수 없습니다.” 메시지를 반환하고 OAuth 프로세스를 종료한다.                           |
| 7b   | UserEntity 저장 실패 시 트랜잭션 롤백 후 “회원 생성 과정에서 오류가 발생했습니다.” 안내.                                  |
| 8a   | JWT 생성 오류 시 클라이언트는 로그인 실패 메시지를 표시한다.                                                       |
| 9a   | 응답 파싱 실패 시 클라이언트는 “로그인 처리 중 오류가 발생했습니다.” 메시지를 표시하고 다시 시도하도록 한다.                            |




#### RELATED INFORMATION
- **Performance**: 회원가입 전체 과정(요청 ~ 응답)은 평균 5초 이내에 완료되어야 한다.
비밀번호 암호화 및 DB 저장은 1초 이내 처리되는 것을 목표로 한다.
- **Frequency**: 신규 사용자마다 최초 1회 실행.
동일 이메일로 중복 가입은 허용하지 않는다.


- **Concurrency**: 최대 500명 동시 가입 요청을 처리할 수 있도록 API 서버 및 DB connection pool을 설정한다.
- **Due Date**: 2025. 11. 01 (예정)
