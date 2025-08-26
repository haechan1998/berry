# BedRequest 숙박 프로젝트  

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=180&section=header&text=BedRequest&fontSize=50&fontAlignY=35" />

---
<br>

## 📘 프로젝트 소개
> 숙박 예약 플랫폼을 벤치마킹하여 **사용자 친화적인 UI/UX**와 **안정적인 백엔드 로직**을 구현한 프로젝트입니다.  
Spring Boot 기반으로 제작되었으며, **회원 인증/보안, 예약 관리, 개인화 기능**을 중점적으로 맡아 개발했습니다.  

---
<br>

## 📅 개발 기간 및 팀 규모
#### 개발기간 : <2025/07/00 - 2025/08/18>
#### 인원 : 6명

---
<br>

## ⚙️ 기술 스택  

### Backend  
<div>
 <img src="https://img.shields.io/badge/springboot%203.5.13-6DB33F?style=for-the-badge&logo=springboot&logoColor=white">
 <img src="https://img.shields.io/badge/Spring%20Boot%20Data%20Jpa-6DB33F?style=for-the-badge&logoColor=white">
</div>
<div><img src="https://img.shields.io/badge/java%2017-007396?style=for-the-badge&logo=OpenJDK&logoColor=white"></div>
<div><img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white"></div>



### Database & Frontend  
<div><img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"></div>
<div>
 <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
 <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=HTML5&logoColor=white">
 <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
</div>
<div><img src="https://img.shields.io/badge/Thymeleaf-005F0F?style=for-the-badge&logo=Thymeleaf&logoColor=white"></div>

### Library & API  
- flatpickr  
- OAuth 2.0 (소셜 로그인)  
- Google SMTP (이메일 인증)  
- CoolSMS (휴대폰 본인인증)

### Collaboration Tool
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">

---
<br>

## 프로젝트 ERD  
<a href="https://www.erdcloud.com/d/eKKqYtQ4ji3fNK6b9"><img src="https://github.com/user-attachments/assets/8ffc8df7-039f-410b-9e5e-9d8f8df3cfe9"></a>  

---
<br>

## 개인 역할 & 기여  

### 회원 인증/보안
- **웹 로그인 및 소셜 로그인(OAuth 2.0)** 구현  
- **Spring Security** 설정 및 로그인/로그아웃 핸들러 커스텀  
- **모바일 본인인증 (CoolSMS), 이메일 인증(Google SMTP)** 적용  
- **비밀번호 재설정, 변경, 회원 탈퇴** 기능 구현  

### 데이터베이스 설계
- **유저(User), 북마크(Bookmark), 알림(Notification)** 테이블 설계 및 ERD 모델링  

### 마이페이지
- 회원정보 수정 기능 개발  
- 북마크 기능 백엔드 설계 및 연동  
- 예약 내역 리스트 & 상세 조회 구현

### UI/UX 기능
- **메인 페이지 배너 슬라이드** 구현 (자동재생/정지/이전·다음 버튼 포함)
- **로그인 / 회원가입 페이지 프론트엔드** 구현
- **마이페이지 프론트엔드** 구현

---
<br>

## 프로젝트 진행 중 어려웠던 점 및 해결
### 1. 소셜 로그인 로그아웃 처리 문제

* **문제**: **OAuth** 기반 소셜 로그인 구현 시, Kakao는 로그아웃 URL을 제공했지만 Google/Naver는 별도의 로그아웃 API가 없어 로그아웃 처리를 일관성 있게 구현하기 어려웠음.

* **해결방법**: 각 플랫폼별 **세션/토큰** 관리 방식을 분석하여 플랫폼 별 Access Token을 이용해 별도의 로그아웃 로직을 직접 구현. **공통 로직과 개별 플랫폼 특화 로직**을 분리하여 안정적인 로그아웃 기능 제공.

* **배운 점**: 외부 API 제공 방식이 다를 수 있음을 경험했고, 서비스 로직을 유연하게 설계하는 방법을 배움.

<br>

### 2. User PK 충돌 문제

* **문제**: 패키지 전역에서 **@ControllerAdvice**를 활용해 User PK를 제공했으나, 회원 정보 수정 과정에서 **email**(Security Config에서 parameterId로 사용)이 변경되면 **기존 세션과 충돌 발생**.

* **해결방법**: 회원 정보 수정 완료 후 **기존 세션을 강제로 제거**하는 로직을 추가하여 충돌을 방지.

* **배운 점**: 전역 상태 관리의 위험성을 인식했고, 세션/보안 로직을 설계할 때 **데이터 변경과 세션 동기화**를 고려해야 함을 배움.
 

