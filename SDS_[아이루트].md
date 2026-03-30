# Software Design Specification (SDS)

## 아이루트





**Team information:**
|    **Project title**    |                                                                                                                  아이루트                                                                                                                   |
| :---------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|         **학번**          |                                                                                                                 **이름**                                                                                                                  |
|     22212006            |            박솔                                                                                                                                                                                                                          |
|    22321594             |          최은수                                                                                                                                                                                                                             |
|     22112056            |           김우주                                                                                                                                                                                                                           |
|     22312049            |          정석희                                                                                                                                                                                                                            |
|   22311952             |           석지윤                                                                                                                                                                                                                           |
|   22321642              |        박정은                                                                                                                
---

## Revision history

| Revision date | Version # | Description | Author |
|---------------|-----------|-------------|--------|
| 1/04/2026    | 1.00      | 1차완성 | Author name |
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
17. 자주 틀리는 문제 분석 및 복습 문제 생성
18. 학생 맞춤 학습 진도 설계
19. 학생 맞춤 과목별 공부 방식 제안
20. 학생 자기 평가 입력란 (메타 인지)
21. 학생 학습 패턴 분석
22. 강사 피드백 입력란
23. 성장 예측 (지금 추세로 갔을 때 다음 시험 성적 예상)
24. 목표 기반 학습 추천
25. 강점 영역 분석(안정적인 부분)
26. 요약 리포트(성적 상승, 하락, 오답 유형 등)
27. 복습 주기 및 복습 내용 추천

## GPS

### 위치/노선
차량의 현재 위치 및 운행 경로를 관리하고 사용자에게 시각적으로 제공하는 기능이다.

28. 실시간 위치 추적
   - 기사 앱에서 5초 주기로 GPS 데이터를 수신
   - 서버는 차량의 최신 위치를 저장 및 갱신
   - 학부모는 차량 위치를 실시간으로 조회 가능
29. 차량 이동 경로 및 노선 조회
   - 차량에 할당된 고정 노선 정보 제공
   - 정류장 순서 기반 경로 시각화
   - 지도 기반 UI로 경로 표시
30. 정류장 진행 상태 표시
   - 현재 차량 위치 기준으로 정류장 상태 구분
31. 위치 공유 시간 제한
   - 차량 운행 시간에만 위치 정보 제공
   - 운행 종료 후 위치 공유 자동 비활성화
32. 차량 및 기사 정보 조회
   - 차량 번호, 기사 이름, 연락처 제공
   - 학부모가 필요 시 확인 가능

### ETA 및 지연 분석 기능
차량 위치와 노선 정보를 기반으로 예상 도착 시간을 계산하고 지연 여부를 판단하는 기능이다.

33. 학생별 도착 예정 시간(ETA) 계산
   - 현재 차량 위치 + 정류장 순서를 기반으로 계산
   - 카카오 길찾기 API 활용
   - 정류장 간 이동 시간 누적 방식 적용
34. 정류장 별 도착 예정 시간 조회
   - 전체 노선의 정류장 별 ETA 제공
   - 학부모 화면에서 정류장 리스트 형태로 확인 가능
   - 학생 하차 정류장은 강조 표시
35. 지각 위험 판단
   - 학생별 하원 예정 시각과 ETA 비교
   - 5분 이상 지연 시 지각 위험 상태로 판단.
36. 지연 원인 표시
   - 교통 혼잡 또는 장시간 정차 여부 기반
   - 단순 텍스트 형태로 제공 (ex) "교통 혼잡", "정차 지연"
  
### 이벤트 및 알림 기능
학생의 탑승/하차 및 차량 상태 변화를 감지하여 학부모에게 알림을 제공하는 기능이다.

37. 학생 탑승 알림
   - NFC 태그를 통한 이벤트 발생
   - 학부모에게 즉시 푸시 알림 전송
38. 학생 하차 알림
   - 하차 시 이벤트 발생
   - 학부모에게 도착 알림 제공
39. 지각 위험 알림
   - ETA 기반 지연 판단 시 자동 알림
   - 예상 도착 시간 및 지연 시간 포함
40. 비정상 정차 알림
   - 일정 시간 이상 차량 정차 시 알림
41. 경로 이탈 감지 알림
   - 차량이 등록된 노선에서 일정 거리 이상 벗어난 경우 알림
   - GPS 오차를 고려한 임계값 적용
42. 알림 중복 방지 정책
   - 동일 이벤트는 5분 이내 재전송 제한
   - 상태 변화 기반 알림 처리

### 기사 지원 기능
차량 운행을 지원하기 위한 기사 전용 기능이다.

43. 탑승 예정 학생 리스트 조회
   - 해당 차량에 등록된 학생 목록 제공
   - 당일 운행 대상 학생 확인 가능

## 게시판

44. 개시판 생성
42. 게시판 목록 조회
43. 게시판 글 올리기
44. 게시판 사진 등록
45. 학원 페이지 조회
46. 다이렉트 메시지
47. 댓글 작성
48. 게시글 수정/삭제
49. 게시글 태그
50. 공지사항 안내
51. 이벤트, 홍보 게시판
52. 1:1 문의 게시판

## NFC 태그
53. 
54.
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

---
## GPS

### **Use case #1 : GitHub OAuth 학생 탑승 알림**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
   

- **Author**  
  

- **Last Update**  
  

- **Status**  
  

- **Primary Actor**  
  

- **Preconditions**  
  1. 

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**: 

### **Use case #1 : GitHub OAuth 학생 하자 알림**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
   

- **Author**  
  

- **Last Update**  
  

- **Status**  
  

- **Primary Actor**  
  

- **Preconditions**  
  1. 

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**:

### **Use case #30 : 실시간 위치 추적**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
   

- **Author**  
  

- **Last Update**  
  

- **Status**  
  

- **Primary Actor**  
  

- **Preconditions**  
  1. 

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**:

### **Use case #31 : 도착 예정 시간**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
   

- **Author**  
  

- **Last Update**  
  

- **Status**  
  

- **Primary Actor**  
  

- **Preconditions**  
  1. 

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**: 

### **Use case #32 : 차량 이동 경로 및 노선 조회**
#### GENERAL CHARACTERISTICS
- **Summary**  
  

- **Scope**  
  아이루트

- **Level**  
   

- **Author**  
  

- **Last Update**  
  

- **Status**  
  

- **Primary Actor**  
  

- **Preconditions**  
  1. 

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**:

### **Use case #35 : 지각 위험 알림(도착 지연 예상 시 알림)**
#### GENERAL CHARACTERISTICS
- **Summary**  
  차량의 실시간 GPS 위치와 고정 노선의 정류장 순서를 기반으로 학생별 예상 하차 시간을 계산하고, 예정 시각 대비 5분 이상 지연이 예상될 경우 학부모에게 지각 위험 알림을 제공하는 기능이다.

- **Scope**  
  아이루트

- **Level**  
   User level

- **Author**  
  박솔

- **Last Update**  
  2026.3.30

- **Status**  
  Design

- **Primary Actor**  
  학부모 (Parent User)
  보조 Actor: 차량 기사 (Driver), 시스템 서버

- **Preconditions**  
  1. 차량에 읶는 GPS 모듈이 탑재되어 있으며 실시간 위치 데이터가 서버로 전송되고 있어야 한다.
  2. 학생은 특정 차량 및 노선(Route)에 등록되어 있어야 한다.
  3. 학생의 예상 도착시간(스케줄)이 DB에 정의되어 있어야 한다.
  4. 기사 앱은 운행 시작 후 5초 주기로 GPS 좌표를 서버에 전송해야 한다.
  5. 서버는 카카오 길찾기 API를 이용하여 정류장 간 이동 시간 계산이 가능해야 한다.
  6. 메시지 큐 기반 비동기 처리 구조가 구성되어 있어야 한다.
  7. 푸시 알림 시스템(FCM)이 정상적으로 동작해야 한다.

- **Trigger**  
  기사 앱으로부터 GPS 위치 데이터가 주기적으로 수신되고, ETA 계산 결과 특정 학생의 도착 지연이 감지될 때.
- **Success Post Condition**  
  1.  서버는 현재 차량 위치와 남은 정류장 순서를 기반으로 학생별 예상 하차 시간을 계산한다.
 2.  각 학생의 ETA는 현재 위치부터 해당 학생의 하차 정류장까지의 경로를 기준으로 누적 계산된다.
 3.  계산된 ETA가 학생의 하원 예정 시각보다 5분 이상 늦을 경우 지각 위험 상태로 판단한다.
 4.  해당 학생의 학부모에게 지각 위험 푸시 알림이 전송된다.
 5.  알림에는 다음 정보가 포함된다.
    - 학생 이름
    - 현재 차량 위치
    - 예상 도착 시간
    - 지연 예상 시간
6. 동일 학생에 대한 동일 유형의 알림은 5분 이내 중복 전송되지 않는다.
- **Failed Post Condition**
  1. GPS 데이터 수신 실패 (30초 이상 위치 갱신 없음)
  2. 카카오 길찾기 API 호출 실패 또는 응답 오류
  3. ETA 계산 로직 실패
  4. 메시지 큐 처리 지연 또는 실패
  5. FCM 푸시 알림 전송 실패
  
#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | 차량 운행이 시작되고 기사 앱이 5초 주기로 GPS 데이터를 서버에 전송한다.                                                                          |
| 1    |     서버는 GPS 데이터를 수신하여 메시지 큐에 위치 이벤트를 적재한다.                                                   |
| 2    |    ETA 계산 워커가 큐에서 위치 이벤트를 소비한다.                                                                   |
| 3    |     서버는 해당 차량의 노선(Route)과 정류장 순서 정보를 조회한다.                                          |
| 4    |   현재 차량 위치 기준으로 다음 정류장부터 각 정류장까지의 이동 경로를 구성한다.                                       |
| 5    |    카카오 길찾기 API를 호출하여 정류장 간 예상 이동 시간을 계산한다.                                          |
| 6    |     남은 정류장 경로를 누적하여 학생별 예상 하차 시각(ETA)을 산출한다.                                                       |
| 7    | 각 학생의 ETA와 DB에 저장된 하원 예정 시각을 비교한다. |
| 8    |  ETA가 예정 시각보다 5분 이상 늦을 경우 지각 위험 상태로 판단한다.                              |
| 9    |    최근 알림 전송 기록을 확인하여 중복 여부를 검사한다.                                                          |
| 10   |     조건을 만족하면 지각 위험 알림을 생성한다.                                                           |
| 11   |     알림 서비스가 FCM을 통해 학부모 앱으로 푸시 메시지를 전송한다.                                                           |
| 12   |     학부모는 앱에서 지연 정보를 확인한다..                                                           |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 1a   |GPS 데이터가 30초 이상 수신되지 않을 경우 “위치 갱신 지연 상태”로 처리하고 ETA 계산을 제한적으로 수행한다. |
| 2a   |  메시지 큐 적재 실패 시 해당 이벤트를 로그로 기록하고 재시도한다.                |
| 5a   | 카카오 길찾기 API 호출 실패 시 평균 속도 기반 ETA 계산으로 fallback 처리한다.                           |
| 6a   |  특정 정류장 정보가 누락된 경우 해당 학생을 ETA 계산 대상에서 제외한다.                                |
| 8a   |  지연 시간이 5분 미만일 경우 정상 상태로 간주하고 알림을 전송하지 않는다.                        |
| 9a   |   동일 학생에 대해 최근 5분 이내 동일 알림이 전송된 경우 알림을 차단한다.                        |
| 11a   |  FCM 전송 실패 시 최대 N회 재시도 후 실패 로그를 저장한다.                       |
| 11b   |  디바이스 토큰이 유효하지 않을 경우 해당 토큰을 비활성화 처리한다.                        |





#### RELATED INFORMATION
- **Performance**:
  GPS 데이터 처리 및 ETA 계산은 1초 이내 수행되어야 한다.
알림 생성 및 전송까지 전체 처리 시간은 3초 이내를 목표로 한다.
- **Frequency**:
  GPS 데이터는 5초 주기로 수신되며, ETA 계산은 위치 이벤트 수신 시마다 수행된다.
지각 위험 알림은 동일 이벤트 기준으로 제한적으로 발생한다.

- **Concurrency**:
  최대 1,000대 차량 동시 운행 상황에서도 처리 가능하도록 메시지 큐 기반 비동기 구조를 적용한다.
- **Due Date**:
  2025. 11. 01 (예정)

### **Use case #36 : 차량 이동 경로 및 노선 조회**
#### GENERAL CHARACTERISTICS
- **Summary**  
  학부모가 앱을 통해 차량의 현재 위치, 이동 경로, 고정 노선의 정류장 정보를 실시간으로 조회하는 기능이다. 이를 통해 학부모는 자녀가 탑승한 차량의 운행 현황과 예상 이동 흐름을 확인할 수 있다.

- **Scope**  
  아이루트

- **Level**  
   User level
- **Author**  
  박솔

- **Last Update**  
  2026.03.30

- **Status**  
  Design

- **Primary Actor**  
  학부모 (Parent User)

- **Preconditions**  
  1. 학부모는 로그인된 상태여야 한다.
  2. 학부모 계정에는 조회 대상 학생이 등록되어 있어야 한다.
  3. 학생은 특정 차량 및 고정 노선(Route)에 배정되어 있어야 한다.
  4. 차량의 노선 정보와 정류장 순서는 DB에 사전 등록되어 있어야 한다.
  5. 기사 앱은 운행 중 5초 주기로 GPS 좌표를 서버에 전송해야 한다.
  6. 서버는 최신 차량 위치 정보를 저장 및 조회할 수 있어야 한다.
  7. 지도 화면 표시를 위한 지도 API 연동이 가능해야 한다.

- **Trigger**  
  학부모가 앱에서 “차량 위치 조회” 또는 “노선 조회” 화면에 접근한다.

- **Success Post Condition**  
  1. 학부모는 자녀가 탑승한 차량의 현재 위치를 지도에서 확인할 수 있다.
  2. 차량의 이동 경로와 고정 노선의 정류장 목록이 화면에 표시된다.
  3. 정류장 목록에는 정류장 순서와 진행 상태가 함께 표시된다.
     - 이미 지난 정류장
     - 현재 이동 중인 구간
     - 앞으로 도착할 정류장
     - 학부모는 자녀의 하차 예정 정류장을 식별할 수 있다.
     - 탑승 중인 학생에 대해서는 실시간 위치 및 이동 경로 정보가 지속적으로 갱신된다.
- **Failed Post Condition**  
 1.  차량 위치 정보 조회 실패
 2.  노선 정보 조회 실패
 3.  GPS 데이터가 30초 이상 갱신되지 않음
 4.  지도 API 렌더링 실패
 5.  학생이 현재 탑승 상태가 아님
    
-> 차량 현재 위치 또는 노선 정보가 정상적으로 표시되지 않음
-> 클라이언트는 “차량 위치를 불러올 수 없습니다” 또는 “현재 운행 중인 차량 정보가 없습니다” 메시지를 표시한다.

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | 학부모가 앱에서 차량 위치 및 노선 조회 화면에 진입한다.                                                                          |
| 1    |  클라이언트는 로그인한 학부모 계정과 연결된 학생 정보를 조회한다.                                                       |
| 2    |   서버는 해당 학생의 현재 탑승 상태와 배정된 차량 정보를 확인한다.                                                                    |
| 3    |     서버는 차량에 연결된 고정 노선(Route)과 정류장 순서 정보를 조회한다.                                          |
| 4    |  서버는 최신 GPS 데이터를 기반으로 차량의 현재 위치를 조회한다.                                        |
| 5    |   서버는 노선 정보, 정류장 목록, 차량 현재 위치를 클라이언트에 반환한다.                                             |
| 6    |   클라이언트는 지도 위에 차량 현재 위치를 표시한다.                                                          |
| 7    | 클라이언트는 정류장 순서에 따라 노선 경로와 정류장 목록을 화면에 렌더링한다. |
| 8    |  현재 차량 위치를 기준으로 이미 지난 정류장, 현재 이동 중인 구간, 남은 정류장을 구분하여 표시한다.                               |
| 9    |   학부모는 자녀의 하차 예정 정류장과 차량의 진행 상태를 확인한다.                                                           |
| 10   |   클라이언트는 주기적으로 최신 위치 정보를 갱신하여 화면을 업데이트한다.                                                             |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 2a   | 학생이 현재 탑승 상태가 아닐 경우 서버는 “현재 탑승 중인 차량 정보가 없습니다.” 메시지를 반환한다.|
| 3a  | 학생에게 차량 또는 노선 정보가 연결되어 있지 않을 경우 노선 조회를 중단하고 오류 메시지를 표시한다.                  |
| 4a   |  최근 30초 이상 GPS 데이터가 갱신되지 않은 경우 서버는 마지막 위치를 반환하고 “위치 갱신 지연” 상태를 함께 전달한다.                          |
| 5a   |  서버 응답 실패 시 클라이언트는 재요청을 수행하거나 오류 메시지를 표시한다.                                 |
| 6a   |  지도 API 로딩 실패 시 지도 표시를 생략하고 정류장 목록만 텍스트 기반으로 제공한다.                                                     |
| 8a   |  차량이 아직 운행 시작 전일 경우 전체 정류장을 “대기 상태”로 표시한다.                         |
| 10a   | 실시간 위치 갱신 요청 실패 시 이전 위치를 유지하고 다음 주기에 재시도한다.                          |




#### RELATED INFORMATION
- **Performance**:
  차량 위치 및 노선 조회 요청에 대한 초기 응답은 2초 이내 제공되어야 한다.
실시간 위치 갱신은 5초 주기로 반영되는 것을 목표로 한다.
- **Frequency**:
  학부모는 차량 운행 중 필요할 때마다 반복적으로 해당 기능을 사용할 수 있다.
위치 정보는 운행 중 지속적으로 갱신된다.


- **Concurrency**:
  다수의 학부모가 동시에 동일 차량의 위치를 조회하더라도 안정적으로 응답할 수 있어야 하며, 최대 1,000명 이상의 동시 조회 요청을 처리할 수 있도록 설계한다. 
- **Due Date**:
  2025. 11. 01 (예정)

### **Use case #37 : 차량 및 기사 정보 조회(기사 연락처, 차량 번호 등)**
#### GENERAL CHARACTERISTICS
- **Summary**  
  학부모가 앱을 통해 차량의 현재 위치, 이동 경로, 고정 노선의 정류장 정보를 실시간으로 조회하는 기능이다. 이를 통해 학부모는 자녀가 탑승한 차량의 운행 현황과 예상 이동 흐름을 확인할 수 있다.

- **Scope**  
  아이루트

- **Level**  
   User level
- **Author**  
  박솔

- **Last Update**  
  2026.03.30

- **Status**  
  Design

- **Primary Actor**  
  학부모 (Parent User)

- **Preconditions**  
  1. 학부모는 로그인된 상태여야 한다.
  2. 학부모 계정에는 조회 대상 학생이 등록되어 있어야 한다.
  3. 학생은 특정 차량 및 고정 노선(Route)에 배정되어 있어야 한다.
  4. 차량의 노선 정보와 정류장 순서는 DB에 사전 등록되어 있어야 한다.
  5. 기사 앱은 운행 중 5초 주기로 GPS 좌표를 서버에 전송해야 한다.
  6. 서버는 최신 차량 위치 정보를 저장 및 조회할 수 있어야 한다.
  7. 지도 화면 표시를 위한 지도 API 연동이 가능해야 한다.

- **Trigger**  
  

- **Success Post Condition**  
  1.
- **Failed Post Condition**  
 1.  

#### MAIN SUCCESS SCENARIO
| Step | Action                                                                                                |
| ---- | ----------------------------------------------------------------------------------------------------- |
| S    | .                                                                           |
| 1    |                                                         |
| 2    |                                                                       |
| 3    |                                               |
| 4    |                                          |
| 5    |                                                |
| 6    |                                                             |
| 7    |  |
| 8    |                                 |
| 9    |                                                              |
| 10   |                                                                |




#### EXTENSION SCENARIOS
| Step | Branching Action                                                                           |
| ---- | ------------------------------------------------------------------------------------------ |
| 4a   | |
| 5a   |                  |
| 7a   |                            |
| 7b   |                                   |
| 8a   |                                                       |
| 9a   |                           |




#### RELATED INFORMATION
- **Performance**: 
- **Frequency**:


- **Concurrency**: 
- **Due Date**:

---
  ## 3. Class diagram
### 유저 관리
```mermaid
classDiagram
    direction LR

    %% =========================
    %% 도메인(Entity)
    %% =========================
    class UserEntity {
        <<entity>>
        - Long userId
        - String githubId
        - boolean isAdmin
        - Instant createdAt
        - Instant deletedAt
        - int commitCount
        - int issueCount
        - int prCount
        + void changeAdmin(boolean isAdmin)
        + void softDelete()
        + boolean isDeleted()
        + void updateStats(int commitCount, int issueCount, int prCount)
    }

    %% =========================
    %% DTOs
    %% =========================
    class AuthTokens {
        - String accessToken
        - String refreshToken
    }

    class GithubAuthDto {
        - String code
        - String state
        - String accessToken
    }

    class GithubProfileDto {
        - Long id
        - String login
        - String avatarUrl
        - String bio
        - String email
    }

    class UserLoginDto {
        - String email
        - String password
    }

    class UserRegisterDto {
        - String email
        - String password
        - String nickname
        - String bio
    }

    class UserResponseDto {
        - Long userId
        - String githubId
        - boolean admin
        - int commitCount
        - int issueCount
        - int prCount
        - Instant createdAt
        - Instant deletedAt
        + static UserResponseDto from(UserEntity user)
    }

    class UserUpdateDto {
        - String nickname
        - String profileImg
        - String bio
    }

    UserResponseDto --> UserEntity : from()

    %% =========================
    %% Repository
    %% =========================
    class UserRepository {
        <<interface>>
        + Optional~UserEntity~ findByGithubId(String githubId)
        + boolean existsByGithubId(String githubId)
        %% JpaRepository 기본 CRUD 상속
    }

    UserRepository --> UserEntity : manages

    %% =========================
    %% Security / JWT
    %% =========================
    class JwtTokenProvider {
        - Key key
        - long accessTokenValidityInMs
        - long refreshTokenValidityInMs
        + String generateAccessToken(Long userId, String role)
        + String generateRefreshToken(Long userId)
        + boolean validateToken(String token)
        + Long getUserIdFromToken(String token)
        + Authentication getAuthentication(String token)
    }

    class CustomJwtUserPrincipal {
        - Long userId
        + Long getUserId()
    }

    JwtTokenProvider --> CustomJwtUserPrincipal : creates

    class JwtAuthenticationFilter {
        - JwtTokenProvider tokenProvider
        + void doFilterInternal(req, res, chain)
        - String resolveToken(req)
    }

    class JwtAuthenticationEntryPoint {
        + void commence(req, res, ex)
    }

    class JwtAccessDeniedHandler {
        + void handle(req, res, ex)
    }

    class CustomUserDetails {
        - Long userId
        - String githubId
        - boolean admin
        - Collection~GrantedAuthority~ authorities
        - boolean accountNonLocked
        - boolean accountNonExpired
        - boolean credentialsNonExpired
        - boolean enabled
        + String getUsername()
        + String getPassword()
        + Collection~GrantedAuthority~ getAuthorities()
        + boolean isAccountNonExpired()
        + boolean isAccountNonLocked()
        + boolean isCredentialsNonExpired()
        + boolean isEnabled()
        + static CustomUserDetails from(UserEntity user)
    }

    class CustomUserDetailsService {
        - UserRepository userRepository
        + UserDetails loadUserByUsername(String username)
    }

    class SecurityConfig {
        - JwtTokenProvider jwtTokenProvider
        - JwtAuthenticationEntryPoint authenticationEntryPoint
        - JwtAccessDeniedHandler accessDeniedHandler
        + CorsConfigurationSource corsConfigurationSource()
        + PasswordEncoder passwordEncoder()
        + SecurityFilterChain filterChain(HttpSecurity http)
    }

    class SecurityUtil {
        + static Long getCurrentUserId()
    }

    JwtAuthenticationFilter --> JwtTokenProvider : uses
    SecurityConfig --> JwtAuthenticationFilter : registers
    SecurityConfig --> JwtAuthenticationEntryPoint : uses
    SecurityConfig --> JwtAccessDeniedHandler : uses
    CustomUserDetailsService --> UserRepository : uses
    SecurityUtil --> CustomJwtUserPrincipal : reads principal

    %% =========================
    %% Service 계층
    %% =========================
    class AuthService {
        - UserRepository userRepository
        - JwtTokenProvider jwtTokenProvider
        + AuthTokens issueTokensForUser(UserEntity user)
        + AuthTokens refresh(String refreshToken)
        + void logout(Long userId)
    }

    class GithubAuthService {
        - String clientId
        - String clientSecret
        - String redirectUri
        - UserRepository userRepository
        - AuthService authService
        - RestTemplate restTemplate
        + String buildAuthorizeUrl()
        + String exchangeCodeForAccessToken(String code)
        + String fetchGithubLogin(String accessToken)
        + AuthTokens loginWithGithub(GithubAuthDto dto)
        - UserEntity createUserFromGithubLogin(String githubLogin)
    }

    class UserService {
        - UserRepository userRepository
        + UserResponseDto getMyProfile()
        + UserResponseDto getByGithubId(String githubId)
        + void deleteMyAccount()
    }

    AuthService --> UserRepository : uses
    AuthService --> JwtTokenProvider : uses

    GithubAuthService --> UserRepository : uses
    GithubAuthService --> AuthService : uses
    GithubAuthService --> GithubAuthDto : uses
    GithubAuthService --> AuthTokens : returns
    GithubAuthService --> UserEntity : creates

    UserService --> UserRepository : uses
    UserService --> UserResponseDto : returns
    UserService --> SecurityUtil : uses

    %% =========================
    %% Controller 계층
    %% =========================
    class AuthController {
        - GithubAuthService githubAuthService
        - AuthService authService
        + ResponseEntity~String~ getGithubAuthorizeUrl()
        + ResponseEntity~AuthTokens~ githubCallback(String code, String state)
        + ResponseEntity~AuthTokens~ loginWithGithub(GithubAuthDto dto)
        + ResponseEntity~AuthTokens~ refresh(Map~String,String~ body)
        + ResponseEntity~Void~ logout(Map~String,Object~ body)
    }

    class GithubAuthController {
        - GithubAuthService githubAuthService
        + ResponseEntity~String~ getAuthorizeUrl()
        + ResponseEntity~AuthTokens~ callback(String code, String state)
        + ResponseEntity~AuthTokens~ loginWithGithub(GithubAuthDto dto)
    }

    class UserController {
        - UserService userService
        + ResponseEntity~UserResponseDto~ getMyProfile()
        + ResponseEntity~UserResponseDto~ getByGithubId(String githubId)
        + ResponseEntity~Void~ deleteMyAccount()
    }

    AuthController --> GithubAuthService : uses
    AuthController --> AuthService : uses
    GithubAuthController --> GithubAuthService : uses
    UserController --> UserService : uses

    %% =========================
    %% 기타 관계
    %% =========================
    AuthService --> AuthTokens : returns
    AuthController --> AuthTokens : returns
    GithubAuthController --> AuthTokens : returns

```
<img width="852" height="623" alt="image" src="https://github.com/user-attachments/assets/47cc41aa-e614-4474-9bde-6de8bdcd3d7d" />



#### Entity Class

| Class Name        | UserEntity                         |         |            |
| ----------------- | ---------------------------------- | ------- | ---------- |
| Class Description | GitHub 계정 기반 사용자 정보를 저장하고 관리하는 엔티티 |         |            |
| 구분        | Name        | Type    | Visibility | Description                                   |
| --------- | ----------- | ------- | ---------- | --------------------------------------------- |
| Attribute | userId      | Long    | Private    | PK, 자동 증가(`IDENTITY`), ERD: `user_id`         |
| Attribute | githubId    | String  | Private    | GitHub 로그인 ID, 고유값, ERD: `github_id`          |
| Attribute | isAdmin     | boolean | Private    | 관리자 여부, ERD: `is_admin`                       |
| Attribute | createdAt   | Instant | Private    | 생성 시간, 최초 생성 시 자동 세팅, ERD: `created_at`       |
| Attribute | deletedAt   | Instant | Private    | 소프트 삭제 시간, 삭제되지 않은 경우 null, ERD: `deleted_at` |
| Attribute | commitCount | int     | Private    | 커밋 횟수, ERD: `commit_count`                    |
| Attribute | issueCount  | int     | Private    | 이슈 개수, ERD: `issue_count`                     |
| Attribute | prCount     | int     | Private    | PR 개수, ERD: `pr_count`                        |
| 구분       | Name       | Description                                   |
| -------- | ---------- | --------------------------------------------- |
| Callback | onCreate() | `@PrePersist` — createdAt 자동 세팅 및 통계 필드 0 초기화 |
| 구분     | Name                                                      | Return Type | Description                      |
| ------ | --------------------------------------------------------- | ----------- | -------------------------------- |
| Method | changeAdmin(boolean isAdmin)                              | void        | 사용자의 관리자 여부 변경                   |
| Method | softDelete()                                              | void        | 현재 시간을 deletedAt에 기록하여 소프트 삭제 처리 |
| Method | isDeleted()                                               | boolean     | deletedAt이 null이 아니면 탈퇴한 사용자로 판단 |
| Method | updateStats(int commitCount, int issueCount, int prCount) | void        | GitHub 통계 일괄 업데이트                |



#### DTO Class

| Class Name        | AuthTokens                             |        |            |
| ----------------- | ----------------------------------------- | ------ | ---------- |
| Class Description | 인증 후 발급되는 Access Token / Refresh Token 묶음 DTO |        |            |
| 구분        | Name         | Type   | Visibility | Description                        |
| --------- | ------------ | ------ | ---------- | ---------------------------------- |
| Attribute | accessToken  | String | Private    | 클라이언트 요청에 사용되는 JWT Access Token    |
| Attribute | refreshToken | String | Private    | Access Token 갱신용 JWT Refresh Token |


| Class Name        | GithubAuthDto                             |        |            |
| ----------------- | ----------------------------------------- | ------ | ---------- |
| Class Description | 깃허브 OAuth 인증 시 전달되는 인증 코드 및 상태 정보를 담는 DTO |        |            |
| 구분        | Name        | Type   | Visibility | Description                          |
| --------- | ----------- | ------ | ---------- | ------------------------------------ |
| Attribute | code        | String | Private    | GitHub 인증 과정에서 받은 authorization code |
| Attribute | state       | String | Private    | CSRF 방지용 state 값                     |
| Attribute | accessToken | String | Private    | GitHub에서 발급한 OAuth Access Token      |



| Class Name        | GithubProfileDto              |         |            |
| ----------------- | ----------------------------- | ------- | ---------- |
| Class Description | GitHub 사용자 프로필 정보를 담는 DTO |         |            |
| 구분        | Name      | Type   | Visibility | Description                |
| --------- | --------- | ------ | ---------- | -------------------------- |
| Attribute | id        | Long   | Private    | GitHub numeric id (고유 번호)  |
| Attribute | login     | String | Private    | GitHub username (로그인 ID)   |
| Attribute | avatarUrl | String | Private    | GitHub 프로필 이미지 URL         |
| Attribute | bio       | String | Private    | GitHub 프로필 소개 문구           |
| Attribute | email     | String | Private    | GitHub 이메일 (비공개 시 null 가능) |



| Class Name        | UserLoginDto                           |        |            |
| ----------------- | ------------------------------------- | ------ | ---------- |
| Class Description | 일반 이메일/비밀번호 기반 로그인 요청 DTO |        |            |
| 구분        | Name     | Type   | Visibility | Description               |
| --------- | -------- | ------ | ---------- | ------------------------- |
| Attribute | email    | String | Private    | 사용자 로그인 이메일               |
| Attribute | password | String | Private    | 사용자 비밀번호(평문, 서버에서 암호화 처리) |

| Class Name        | UserRegisterDto                           |        |            |
| ----------------- | ------------------------------------- | ------ | ---------- |
| Class Description | 일반 이메일/비밀번호 기반 로그인 요청 DTO |        |            |
| 구분        | Name     | Type   | Visibility | Description            |
| --------- | -------- | ------ | ---------- | ---------------------- |
| Attribute | email    | String | Private    | 회원가입 이메일(로그인 ID)       |
| Attribute | password | String | Private    | 회원 비밀번호(저장 전 해시 처리 예정) |
| Attribute | nickname | String | Private    | 서비스 내에서 사용할 닉네임        |
| Attribute | bio      | String | Private    | 한 줄 소개 / 자기소개          |


| Class Name        | UserResponseDto                           |        |            |
| ----------------- | ------------------------------------- | ------ | ---------- |
| Class Description | 클라이언트로 반환하는 사용자 정보 응답 DTO |        |            |
| 구분        | Name        | Type    | Visibility | Description              |
| --------- | ----------- | ------- | ---------- | ------------------------ |
| Attribute | userId      | Long    | Private    | 사용자 PK                   |
| Attribute | githubId    | String  | Private    | 사용자 GitHub ID (연동 계정)    |
| Attribute | admin       | boolean | Private    | 관리자 여부                   |
| Attribute | commitCount | int     | Private    | 누적 커밋 수                  |
| Attribute | issueCount  | int     | Private    | 누적 이슈 개수                 |
| Attribute | prCount     | int     | Private    | 누적 PR 개수                 |
| Attribute | createdAt   | Instant | Private    | 계정 생성 시각                 |
| Attribute | deletedAt   | Instant | Private    | 계정 삭제(탈퇴) 시각, 미탈퇴 시 null |
| 구분     | Name                  | Return Type     | Description                              |
| ------ | --------------------- | --------------- | ---------------------------------------- |
| Method | from(UserEntity user) | UserResponseDto | UserEntity를 기반으로 응답 DTO로 변환하는 정적 팩토리 메서드 |

| Class Name        | UserUpdateDto                           |        |            |
| ----------------- | ------------------------------------- | ------ | ---------- |
| Class Description | 마이페이지 등에서 사용자 프로필 수정 요청에 사용하는 DTO |        |            |
| 구분        | Name       | Type   | Visibility | Description     |
| --------- | ---------- | ------ | ---------- | --------------- |
| Attribute | nickname   | String | Private    | 변경할 닉네임         |
| Attribute | profileImg | String | Private    | 변경할 프로필 이미지 URL |
| Attribute | bio        | String | Private    | 변경할 자기소개/한 줄 소개 |



#### Repository Class

| Class Name        | UserRepository                                           |                      |            |
| ----------------- | -------------------------------------------------------- | -------------------- | ---------- |
| Class Description | UserEntity에 대한 CRUD 및 사용자 검색용 JPA Repository |                      |            |
| 구분     | Name                              | Return Type          | Description        |
| ------ | --------------------------------- | -------------------- | ------------------ |
| Method | findByGithubId(String githubId)   | Optional<UserEntity> | github_id로 사용자 조회  |
| Method | existsByGithubId(String githubId) | boolean              | github_id 존재 여부 확인 |


#### Security Class

| Class Name        | JwtTokenProvider                          |        |            |
| ----------------- | ----------------------------------------- | ------ | ---------- |
| Class Description | JWT Access/Refresh 토큰 생성·검증·파싱 담당         |        |            |
| 구분        | Name                     | Type | Visibility | Description      |
| --------- | ------------------------ | ---- | ---------- | ---------------- |
| Attribute | key                      | Key  | Private    | 서명 검증용 Key 객체    |
| Attribute | accessTokenValidityInMs  | long | Private    | 액세스토큰 유효 시간(ms)  |
| Attribute | refreshTokenValidityInMs | long | Private    | 리프레시토큰 유효 시간(ms) |
| 구분     | Name                                          | Return Type    | Description                            |
| ------ | --------------------------------------------- | -------------- | ---------------------------------------- |
| Method | generateAccessToken(Long userId, String role) | String         | Access Token 생성                          |
| Method | generateRefreshToken(Long userId)             | String         | Refresh Token 생성                         |
| Method | validateToken(String token)                   | boolean        | JWT 서명 및 만료 검증                           |
| Method | getUserIdFromToken(String token)              | Long           | JWT Payload에서 userId(subject) 추출         |
| Method | getAuthentication(String token)               | Authentication | SecurityContext에 넣을 Authentication 객체 생성 |



| Class Name        | JwtAuthenticationFilter                                              |                  |            |
| ----------------- | -------------------------------------------------------------------- | ---------------- | ---------- |
| 구분        | Name          | Type             | Visibility    | Description   |
| --------- | ------------- | ---------------- | ------------- | ------------- |
| Attribute | tokenProvider | JwtTokenProvider | Private/Final | JWT 생성·검증 제공자 |
| 구분     | Name                                 | Return Type | Description                                 |
| ------ | ------------------------------------ | ----------- | ------------------------------------------- |
| Method | doFilterInternal(...)                | void        | JWT 검증 후 SecurityContext에 Authentication 저장 |
| Method | resolveToken(HttpServletRequest req) | String      | Authorization 헤더에서 Bearer Token 추출          |




| Class Name        | JwtAuthenticationEntryPoint                                     |                        |            |
| ----------------- | -------------------------------------------------------- | ---------------------- | ---------- |
| 구분                    | Name                            | Type | Visibility |
| --------------------- | ------------------------------- | ---- | ---------- |
| **Class Name**        | JwtAuthenticationEntryPoint     |      |            |
| **Class Description** | 인증 실패(401 Unauthorized) 시 처리 담당 |      |            |
| 구분     | Name          | Return Type | Description       |
| ------ | ------------- | ----------- | ----------------- |
| Method | commence(...) | void        | 인증 실패 시 401 응답 전송 |


| Class Name        | JwtAccessDeniedHandler                                           |                             |            |
| ----------------- | --------------------------------------------------------- | --------------------------- | ---------- |
| 구분                    | Name                         | Type | Visibility |
| --------------------- | ---------------------------- | ---- | ---------- |
| **Class Name**        | JwtAccessDeniedHandler       |      |            |
| **Class Description** | 인가 실패(403 Forbidden) 시 처리 담당 |      |            |
| 구분     | Name        | Return Type | Description       |
| ------ | ----------- | ----------- | ----------------- |
| Method | handle(...) | void        | 권한 부족 시 403 응답 전송 |



| Class Name        | CustomUserDetailsService            |      |            |
| ----------------- | -------------------------------------- | ---- | ---------- |
| 구분                    | Name                                       | Type | Visibility |
| --------------------- | ------------------------------------------ | ---- | ---------- |
| **Class Name**        | CustomUserDetailsService                   |      |            |
| **Class Description** | GitHub ID 기반 사용자 조회(UserDetailsService 구현) |      |            |
| 구분        | Name           | Type           | Visibility    | Description        |
| --------- | -------------- | -------------- | ------------- | ------------------ |
| Attribute | userRepository | UserRepository | Private/Final | 사용자 조회용 Repository |
| 구분     | Name                                | Return Type | Description                             |
| ------ | ----------------------------------- | ----------- | --------------------------------------- |
| Method | loadUserByUsername(String githubId) | UserDetails | github_id로 유저 조회 후 CustomUserDetails 생성 |


| Class Name        | CustomUserDetails                |      | ---------- |
| ----------------- | ------------------------------------- | ---- | ---------- |
| 구분                    | Name                                             | Type | Visibility |
| --------------------- | ------------------------------------------------ | ---- | ---------- |
| **Class Name**        | CustomUserDetails                                |      |            |
| **Class Description** | UserEntity를 Spring Security의 UserDetails로 변환한 객체 |      |            |
| 구분        | Name                  | Type                                   | Visibility | Description             |
| --------- | --------------------- | -------------------------------------- | ---------- | ----------------------- |
| Attribute | userId                | Long                                   | Private    | 사용자 PK                  |
| Attribute | githubId              | String                                 | Private    | GitHub ID (username 대체) |
| Attribute | admin                 | boolean                                | Private    | 관리자 여부                  |
| Attribute | authorities           | Collection<? extends GrantedAuthority> | Private    | 역할/권한                   |
| Attribute | accountNonLocked      | boolean                                | Private    | 계정 잠김 여부                |
| Attribute | accountNonExpired     | boolean                                | Private    | 계정 만료 여부                |
| Attribute | credentialsNonExpired | boolean                                | Private    | 자격 만료 여부                |
| Attribute | enabled               | boolean                                | Private    | 활성화 여부(탈퇴 user=false)   |
| 구분     | Name                      | Return Type       | Description          |
| ------ | ------------------------- | ----------------- | -------------------- |
| Method | from(UserEntity user)     | CustomUserDetails | 엔티티 → UserDetails 변환 |
| Method | getAuthorities()          | Collection        | 권한 반환                |
| Method | getUsername()             | String            | GitHub ID 반환         |
| Method | getPassword()             | String            | (OAuth만 사용 → null)   |
| Method | isAccountNonLocked()      | boolean           | 잠김 여부                |
| Method | isAccountNonExpired()     | boolean           | 만료 여부                |
| Method | isCredentialsNonExpired() | boolean           | 자격증명 만료 여부           |
| Method | isEnabled()               | boolean           | 계정 활성 여부             |

| Class Name        | SecurityConfig                                      |                        |            |
| ----------------- | -------------------------------------------------------- | ---------------------- | ---------- |
| 구분                    | Name                               | Type | Visibility |
| --------------------- | ---------------------------------- | ---- | ---------- |
| **Class Name**        | SecurityConfig                     |      |            |
| **Class Description** | Spring Security 설정(필터, 권한, CORS 등) |      |            |
| 구분        | Name                     | Type                        | Visibility    | Description  |
| --------- | ------------------------ | --------------------------- | ------------- | ------------ |
| Attribute | jwtTokenProvider         | JwtTokenProvider            | Private/Final | JWT Provider |
| Attribute | authenticationEntryPoint | JwtAuthenticationEntryPoint | Private/Final | 401 에러 처리    |
| Attribute | accessDeniedHandler      | JwtAccessDeniedHandler      | Private/Final | 403 에러 처리    |
| 구분     | Name                           | Return Type             | Description            |
| ------ | ------------------------------ | ----------------------- | ---------------------- |
| Method | corsConfigurationSource()      | CorsConfigurationSource | CORS 설정 생성             |
| Method | passwordEncoder()              | PasswordEncoder         | BCrypt PasswordEncoder |
| Method | filterChain(HttpSecurity http) | SecurityFilterChain     | 전체 Security 설정 로직      |

| Class Name        | SecurityUtil                                    |                        |            |
| ----------------- | -------------------------------------------------------- | ---------------------- | ---------- |
| 구분                    | Name                                          | Type | Visibility |
| --------------------- | --------------------------------------------- | ---- | ---------- |
| **Class Name**        | SecurityUtil                                  |      |            |
| **Class Description** | SecurityContext에서 현재 로그인한 userId를 가져오는 유틸 클래스 |      |            |
| 구분     | Name               | Return Type | Description                            |
| ------ | ------------------ | ----------- | -------------------------------------- |
| Method | getCurrentUserId() | Long        | SecurityContext의 principal에서 userId 추출 |


#### Service Class

| Class Name        | AuthService                                                        |            |            |
| ----------------- | ------------------------------------------------------------------ | ---------- | ---------- |
| Class Description | GitHub 로그인, 로그아웃, 토큰 재발급 등 인증 관련 핵심 로직 담당                          |            |            |
| 구분        | Name             | Type             | Visibility      | Description         |
| --------- | ---------------- | ---------------- | --------------- | ------------------- |
| Attribute | userRepository   | UserRepository   | Private / Final | 사용자 조회용 JPA 리포지토리   |
| Attribute | jwtTokenProvider | JwtTokenProvider | Private / Final | JWT 생성 및 검증 담당 컴포넌트 |
| 구분     | Name                                | Return Type | Description                                                                      |
| ------ | ----------------------------------- | ----------- | -------------------------------------------------------------------------------- |
| Method | issueTokensForUser(UserEntity user) | AuthTokens  | GitHub OAuth 등을 통해 확보된 UserEntity 기반으로 역할(is_admin) 확인 후 Access/Refresh 토큰 세트 발급 |
| Method | refresh(String refreshToken)        | AuthTokens  | 전달받은 Refresh Token을 검증 후, 유저 상태를 확인하고 새 Access/Refresh Token 재발급                 |
| Method | logout(Long userId)                 | void        | 현재 구조에서는 stateless JWT 이므로 별도 처리 없이 로그아웃 훅 제공(추후 블랙리스트/저장소 도입 시 확장 가능)           |


| Class Name        | GithubAuthService                                                           |            |            |
| ----------------- | --------------------------------------------------------------------------- | ---------- | ---------- |
| Class Description | 깃허브 OAuth 인증 절차 및 GitHub 사용자 정보 연동 로직 수행                                    |            |            |
| 구분        | Name           | Type           | Visibility      | Description                               |
| --------- | -------------- | -------------- | --------------- | ----------------------------------------- |
| Attribute | clientId       | String         | Private         | GitHub OAuth Client ID (환경설정에서 주입)        |
| Attribute | clientSecret   | String         | Private         | GitHub OAuth Client Secret (환경설정에서 주입)    |
| Attribute | redirectUri    | String         | Private         | GitHub OAuth Redirect URI                 |
| Attribute | userRepository | UserRepository | Private / Final | GitHub 로그인(github_id) 기준 사용자 조회/저장용 리포지토리 |
| Attribute | authService    | AuthService    | Private / Final | 인증 토큰 발급 로직(AuthTokens 생성) 담당 서비스         |
| Attribute | restTemplate   | RestTemplate   | Private / Final | GitHub API 호출용 HTTP 클라이언트                 |
| 구분     | Name                                          | Return Type | Description                                                                                    |
| ------ | --------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------------- |
| Method | buildAuthorizeUrl()                           | String      | 프론트에서 GitHub 로그인 버튼 클릭 시 사용할 `https://github.com/login/oauth/authorize` URL 생성                 |
| Method | exchangeCodeForAccessToken(String code)       | String      | GitHub가 넘겨준 인가 코드(code)를 이용해 Access Token으로 교환                                                 |
| Method | fetchGithubLogin(String accessToken)          | String      | GitHub API(`/user`) 호출로 프로필 조회 후 `login` 값을 github_id로 사용                                      |
| Method | loginWithGithub(GithubAuthDto dto)            | AuthTokens  | ① accessToken 없으면 code로 교환 → ② GitHub login 조회 → ③ 기존 유저 조회 or 신규 생성 → ④ AuthService 통해 JWT 발급 |
| Method | createUserFromGithubLogin(String githubLogin) | UserEntity  | GitHub로 처음 로그인한 사용자를 ERD 규칙에 맞게 생성 후 저장 (is_admin=false, 통계 0, createdAt=now 등)                |

| Class Name        | UserService                                        |                 |            |
| ----------------- | -------------------------------------------------- | --------------- | ---------- |
| Class Description | 사용자 정보 조회, 탈퇴(소프트 삭제) 등 일반 사용자 관리 로직 담당            |                 |            |
| 구분        | Name           | Type           | Visibility      | Description          |
| --------- | -------------- | -------------- | --------------- | -------------------- |
| Attribute | userRepository | UserRepository | Private / Final | 사용자 조회/저장용 JPA 리포지토리 |
| 구분     | Name                           | Return Type     | Description                                                     |
| ------ | ------------------------------ | --------------- | --------------------------------------------------------------- |
| Method | getMyProfile()                 | UserResponseDto | SecurityContext의 userId를 기준으로 내 프로필과 GitHub 통계 정보를 조회하여 DTO로 반환 |
| Method | getByGithubId(String githubId) | UserResponseDto | github_id 기준 사용자 정보를 조회하여 DTO로 반환(관리자/내부용)                      |
| Method | deleteMyAccount()              | void            | 현재 로그인한 사용자를 조회 후 soft delete(`user.softDelete()`) 수행           |


#### Controller Class

| Class Name        | AuthController                                                  |                            |            |
| ----------------- | --------------------------------------------------------------- | -------------------------- | ---------- |
| Class Description | GitHub 로그인, 로그아웃, 토큰 재발급 요청을 처리하는 컨트롤러                          |                            |            |
| 구분        | Name              | Type              | Visibility      | Description                   |
| --------- | ----------------- | ----------------- | --------------- | ----------------------------- |
| Attribute | githubAuthService | GithubAuthService | Private / Final | GitHub OAuth 및 로그인 처리 서비스     |
| Attribute | authService       | AuthService       | Private / Final | 토큰 재발급, 로그아웃 등 인증 비즈니스 로직 서비스 |
| 구분     | Name                                      | Return Type                | Description                                                                                 |
| ------ | ----------------------------------------- | -------------------------- | ------------------------------------------------------------------------------------------- |
| Method | getGithubAuthorizeUrl()                   | ResponseEntity<String>     | 프론트에서 GitHub 로그인 버튼 클릭 시, GitHub 인증 페이지로 이동할 authorize URL 반환 (`GET /github/authorize-url`) |
| Method | githubCallback(String code, String state) | ResponseEntity<AuthTokens> | GitHub에서 콜백으로 넘겨준 code/state로 GitHub 인증 및 JWT 발급 수행 (`GET /github/callback`)                |
| Method | loginWithGithub(GithubAuthDto dto)        | ResponseEntity<AuthTokens> | SPA 환경 등에서 code를 body로 받아 GitHub 로그인 처리 (`POST /github/login`)                              |
| Method | refresh(Map<String,String> body)          | ResponseEntity<AuthTokens> | 리프레시 토큰을 이용해 Access/Refresh 토큰 재발급 (`POST /refresh`)                                        |
| Method | logout(Map<String,Object> body)           | ResponseEntity<Void>       | 로그아웃 요청 처리, 필요 시 userId 기반 후처리 가능 (`POST /logout`)                                          |

| Class Name        | GithubAuthController                                                  |                            |            |
| ----------------- | --------------------------------------------------------------- | -------------------------- | ---------- |
| Class Description | GitHub OAuth 로그인 전용 엔드포인트를 제공하는 컨트롤러                          |                            |            |
| 구분        | Name              | Type              | Visibility      | Description                  |
| --------- | ----------------- | ----------------- | --------------- | ---------------------------- |
| Attribute | githubAuthService | GithubAuthService | Private / Final | GitHub OAuth 인증 및 로그인 처리 서비스 |
| 구분     | Name                                | Return Type                | Description                                                                |
| ------ | ----------------------------------- | -------------------------- | -------------------------------------------------------------------------- |
| Method | getAuthorizeUrl()                   | ResponseEntity<String>     | GitHub 로그인 버튼 클릭 시 사용할 authorize URL 반환 (`GET /authorize-url`)             |
| Method | callback(String code, String state) | ResponseEntity<AuthTokens> | GitHub OAuth 콜백 처리, code/state로 로그인 후 JWT 토큰 반환 (`GET /callback`)          |
| Method | loginWithGithub(GithubAuthDto dto)  | ResponseEntity<AuthTokens> | 프론트에서 이미 code → accessToken 교환 완료 후 accessToken만 보내는 경우 처리 (`POST /login`) |


| Class Name        | UserController                                 |                                 |            |
| ----------------- | ---------------------------------------------- | ------------------------------- | ---------- |
| Class Description | 현재 사용자 정보 조회, 계정 탈퇴 요청을 처리하는 컨트롤러              |                                 |            |
| 구분        | Name        | Type        | Visibility      | Description                    |
| --------- | ----------- | ----------- | --------------- | ------------------------------ |
| Attribute | userService | UserService | Private / Final | 사용자 정보 조회 및 계정 삭제 로직을 처리하는 서비스 |
| 구분     | Name                           | Return Type                     | Description                                                       |
| ------ | ------------------------------ | ------------------------------- | ----------------------------------------------------------------- |
| Method | getMyProfile()                 | ResponseEntity<UserResponseDto> | 현재 로그인한 사용자의 프로필 정보 조회 (`GET /me`)                                |
| Method | getByGithubId(String githubId) | ResponseEntity<UserResponseDto> | github_id 기준 특정 사용자 정보 조회 (관리자용 예시) (`GET /by-github/{githubId}`) |
| Method | deleteMyAccount()              | ResponseEntity<Void>            | 현재 로그인한 사용자의 소프트 삭제(탈퇴) 처리 (`DELETE /me`)                         |

## 4. Sequence diagram
## 유저
### 1. GitHub OAuth 회원가입

```mermaid
sequenceDiagram
    autonumber
    participant U as User(브라우저)
    participant FE as Frontend(SPA)
    participant AC as AuthController
    participant GAS as GithubAuthService
    participant GH as GitHub OAuth
    participant GAPI as GitHub API
    participant AS as AuthService
    participant UR as UserRepository
    participant JTP as JwtTokenProvider

    U->>FE: "GitHub로 로그인" 버튼 클릭
    FE->>AC: GET /api/auth/github/authorize-url
    AC->>GAS: buildAuthorizeUrl()
    GAS-->>AC: authorizeUrl
    AC-->>FE: 200 OK (authorizeUrl)
    FE-->>U: GitHub 로그인 페이지로 리다이렉트

    U->>GH: GitHub 로그인 및 권한 허용
    GH-->>AC: GET /api/auth/github/callback?code&state
    AC->>GAS: loginWithGithub(GithubAuthDto{code,state})

    alt dto.accessToken 없음
        GAS->>GAS: exchangeCodeForAccessToken(code)
        GAS->>GH: POST /login/oauth/access_token
        GH-->>GAS: access_token
    end

    GAS->>GAPI: GET /user (Authorization: Bearer access_token)
    GAPI-->>GAS: { login, ... }

    GAS->>UR: findByGithubId(login)
    UR-->>GAS: Optional.empty (최초 로그인)

    GAS->>GAS: createUserFromGithubLogin(login)
    GAS->>UR: save(UserEntity)
    UR-->>GAS: saved UserEntity

    GAS->>AS: issueTokensForUser(user)
    AS->>JTP: generateAccessToken(user.userId, role)
    JTP-->>AS: accessToken
    AS->>JTP: generateRefreshToken(user.userId)
    JTP-->>AS: refreshToken
    AS-->>GAS: AuthTokens
    GAS-->>AC: AuthTokens
    AC-->>FE: 200 OK (AuthTokens)
    FE-->>U: 토큰 저장(localStorage 등) 후 첫 로그인 완료 화면


```

사용자가 웹 서비스에서 “GitHub로 로그인” 버튼을 클릭하면, 프론트엔드는 먼저 백엔드의 GET /api/auth/github/authorize-url 엔드포인트를 호출해 GitHub 인증 페이지로 이동할 수 있는 authorize URL을 요청한다. AuthController는 내부적으로 GithubAuthService.buildAuthorizeUrl()을 호출하여 GitHub OAuth 인증 URL을 생성해 프론트엔드에 전달한다. 프론트엔드는 해당 URL로 리다이렉트시켜 사용자를 GitHub 로그인 화면으로 보내고, 사용자는 GitHub 계정으로 로그인 및 권한 허용을 진행한다.

GitHub 로그인에 성공하면 GitHub는 등록된 redirect URI로 code와 state를 포함하여 백엔드로 콜백 요청을 보낸다. 이때 AuthController.githubCallback()이 호출되며, 컨트롤러는 전달받은 code/state 값을 GithubAuthDto에 담아 GithubAuthService.loginWithGithub()에 넘긴다.

GithubAuthService는 우선 DTO에 accessToken이 없는 경우 GitHub 토큰 발급 엔드포인트(https://github.com/login/oauth/access_token)에 client_id, client_secret, code, redirect_uri를 담아 POST 요청을 보내 액세스토큰을 받아온다. 이어서 이 액세스 토큰을 이용하여 GitHub API의 /user 엔드포인트를 호출해 사용자의 GitHub 프로필 정보를 조회하고, 이 중 login 값을 가져와 서비스에서 사용하는 github_id로 활용한다.

그 다음 UserRepository.findByGithubId()를 호출하여 해당 github_id가 이미 존재하는지 조회한다. 최초 로그인이라면 해당 값이 없기 때문에, GithubAuthService는 createUserFromGithubLogin()을 호출하여 새로운 UserEntity를 생성한다. 이때 관리자 여부는 기본적으로 false이며, commit/issue/pr 통계는 모두 0으로 초기화되고 created_at 값이 현재 시각으로 설정된다. 생성된 엔티티는 DB에 저장된다.

사용자 엔터티가 준비되면, GithubAuthService는 AuthService.issueTokensForUser()를 호출해 Access Token과 Refresh Token을 발급받는다. AuthService는 JWT 생성기 JwtTokenProvider를 사용하여, userId와 역할(is_admin 여부)을 포함한 Access Token과 Refresh Token을 각각 생성한다. 생성된 토큰 세트(AuthTokens)는 다시 컨트롤러를 통해 프론트엔드로 반환되며, 프론트는 이 토큰을 저장하여 최초 회원가입 및 로그인 과정을 마친다.

### 2. 로그인 (GitHub OAuth 재로그인)
```mermaid
sequenceDiagram
    autonumber
    participant U as User(브라우저)
    participant FE as Frontend(SPA)
    participant AC as AuthController
    participant GAS as GithubAuthService
    participant GH as GitHub OAuth
    participant GAPI as GitHub API
    participant AS as AuthService
    participant UR as UserRepository
    participant JTP as JwtTokenProvider

    U->>FE: "GitHub로 로그인" 버튼 클릭
    FE->>AC: GET /api/auth/github/authorize-url
    AC->>GAS: buildAuthorizeUrl()
    GAS-->>AC: authorizeUrl
    AC-->>FE: 200 OK (authorizeUrl)
    FE-->>U: GitHub 로그인 페이지로 리다이렉트

    U->>GH: GitHub 로그인/권한 허용
    GH-->>AC: GET /api/auth/github/callback?code&state
    AC->>GAS: loginWithGithub(GithubAuthDto{code,state})

    alt dto.accessToken 없음
        GAS->>GAS: exchangeCodeForAccessToken(code)
        GAS->>GH: POST /login/oauth/access_token
        GH-->>GAS: access_token
    end

    GAS->>GAPI: GET /user (Authorization: Bearer access_token)
    GAPI-->>GAS: { login, ... }

    GAS->>UR: findByGithubId(login)
    UR-->>GAS: 기존 UserEntity (이미 가입)

    GAS->>AS: issueTokensForUser(user)
    AS->>JTP: generateAccessToken(user.userId, role)
    JTP-->>AS: accessToken
    AS->>JTP: generateRefreshToken(user.userId)
    JTP-->>AS: refreshToken
    AS-->>GAS: AuthTokens
    GAS-->>AC: AuthTokens
    AC-->>FE: 200 OK (AuthTokens)
    FE-->>U: 토큰 갱신 후 로그인 완료 화면


```

재로그인 흐름은 회원가입과 거의 동일하게 시작된다. 사용자는 “GitHub로 로그인” 버튼을 클릭하고, 프론트엔드는 백엔드에서 authorize URL을 받아 GitHub 인증 페이지로 이동시킨다. GitHub에서 code/state를 전달하며 콜백 요청을 보내면, 백엔드는 code를 accessToken으로 교환하여 GitHub 계정 정보를 다시 읽어온다.

가장 큰 차이는 이 시점 이후이다. GithubAuthService.loginWithGithub()은 GitHub에서 넘어온 login 값을 기준으로 UserRepository.findByGithubId()를 조회하고, 이번에는 DB에 이미 저장된 기존 사용자 엔터티가 존재하므로 새롭게 생성하지 않는다. 이후 기존 사용자 정보로 AuthService.issueTokensForUser()를 호출해 JWT 토큰 세트를 새로 발급받는다. 프론트는 새로운 Access Token과 Refresh Token을 저장하여 로그인 상태가 갱신된다.

즉, 재로그인 과정에서는 회원가입이 발생하지 않고, 이미 등록된 사용자의 인증만 수행하는 방식으로 작동한다.
