# 🚀 Clubing 🏫
Clubing은 아주대학교 학생들이 동아리 활동을 한눈에 관리할 수 있도록 설계된 웹 플랫폼입니다.  
프론트엔드(React/Vite)와 AWS에 배포된 백엔드를 연동하여, 일정 관리·실시간 알림·가입 신청·모집 공고 등을 제공합니다.

---

## 🗂 목차

1. [📋 프로젝트 개요](#프로젝트-개요)  
2. [🎯 문제 인식 & 목표](#문제-인식--목표)  
3. [🔑 주요 기능](#주요-기능)  
4. [🛠️ 기술 스택](#기술-스택)  
5. [🏗️ 시스템 아키텍처](#시스템-아키텍처)  
6. [🌐 배포 환경](#배포-환경)  
7. [👥 기여자](#기여자)  
8. [📜 라이선스](#라이선스)

---

## 📋 프로젝트 개요

- **👩‍🎓 학생(User)**  
  - 동아리 모집 공고, 일정, 공지사항을 한곳에서 확인  
  - 가입 신청 후 실시간 알림을 받아 활동 참여  

- **👨‍🏫 동아리 운영자(Admin)**  
  - 모집 공고 작성 및 마감 관리  
  - 회원 가입 요청 승인/거절  
  - 일정 및 공지사항 등록·수정·삭제  

Clubing을 통해 학생과 운영자 모두가 번거로운 연락 없이 실시간으로 동아리 정보를 공유하고, 효율적인 운영이 가능합니다.

---

## 🎯 문제 인식 & 목표

1. **문제 인식**  
   - 동아리 정보가 학교 커뮤니티와 SNS에 분산되어 있어 원하는 정보를 찾기 어려움  
   - 운영자는 가입 승인, 일정 공지, 멤버 관리 등 반복 작업으로 시간 소모  

2. **목표**  
   - **학생**:  
     - 간단한 검색 & 클릭으로 동아리 조회 → 가입 신청 → 일정 확인  
     - 참여 장벽 최소화  
   - **운영자**:  
     - 통합 대시보드에서 모집 공고·일정·멤버 관리  
     - 업무 효율 극대화  

3. **해결 방안**  
   - React 기반 프론트엔드로 직관적이고 사용성 높은 UI 제공  
   - AWS에 배포된 API와 Vercel 자동배포 프론트엔드 연동  
   - SSE(Server-Sent Events) 기반 실시간 알림으로 즉시 정보 전달  

---

## 🔑 주요 기능

1. **🏠 동아리 목록 조회 (홈)**
   - 📂 카테고리별 필터링  
   - 🔍 키워드·제목 검색  
   - ▶️ 동아리 카드 클릭 시 상세 페이지 이동  
   <img width="664" alt="동아리 목록" src="https://github.com/user-attachments/assets/593dd301-b4ee-439e-9333-1db7844fec59" />

2. **✍️ 가입 신청 & 승인/거절**
   - 👩‍🎓 학생: 동아리 상세 페이지에서 가입 신청  
   - 👨‍🏫 운영자: 대시보드에서 신청자 리스트 확인 후 승인/거절  
   - 🔔 승인/거절 시 학생에게 실시간 알림(SSE)  
   <img width="824" alt="가입 신청" src="https://github.com/user-attachments/assets/1ea7e678-627f-4c1f-bb28-83c870809e2f" />

3. **🗓️ 일정 관리**
   - `react-calendar` 기반 달력 UI  
   - ➕ 일정 등록, ✏️ 수정, 🗑️ 삭제 기능  
   - 📣 일정 등록 시 SSE 알림 전송  
   <img width="476" alt="일정 관리" src="https://github.com/user-attachments/assets/680ad1eb-0c65-4d6c-adac-9246f1d6bde2" />

4. **📢 모집 공고 관리**
   - 📝 운영자: 상시/기간별 모집 공고 작성  
   - ⏳ 공고 마감 시 자동 상태 변경  
   - 🏠 홈 화면에 활성 공고 노출  

5. **📰 공지사항 & 👥 멤버 관리**
   - 📝 운영자: 공지사항 작성/삭제  
   - 👩‍🎓 학생: 공지사항 확인  
   - 👨‍🏫 운영자: 가입 멤버 목록 조회, 신청자 목록 관리  
   <img width="480" alt="공지사항" src="https://github.com/user-attachments/assets/f75e30e6-f510-4eca-b58a-264f268e9b2f" />  
   <img width="454" alt="멤버 관리" src="https://github.com/user-attachments/assets/6a6e3f0a-28e9-4934-9185-c43f366a8ed4" />

---

## 🛠️ 기술 스택

### Frontend
- **Framework & Bundler**: React (Vite 기반)  
- **컴포넌트 상태 관리**: Redux  
- **API 호출**: Axios  
- **입력폼 UX 개선**: react-input-mask  
- **실시간 알림**: SSE (EventSource)  
- **라우팅**: react-router-dom  
- **스타일링**: CSS Modules, Tailwind CSS 일부  
- **배포**: Vercel (GitHub → Vercel 자동 CI/CD)  
- **환경 변수 관리**: dotenv  

### Backend
- **Framework**: Spring Boot (AWS EC2 배포)  
- **데이터베이스**: MySQL (Amazon RDS)  
- **캐시/세션**: Redis (ElastiCache)  
- **인증·보안**:  
  - JWT 기반 인증  
  - CORS 설정  
  - TLS(HTTPS) 오류 대응 (Let’s Encrypt + Certbot)  
- **메일·알림 시스템**:  
  - AWS SES (이메일)  
  - Coolsms (SMS)  
  - 비동기 전송으로 응답 지연 최소화  
- **테스트 & 품질**:  
  - JUnit 기반 통합 테스트 (약 70% 커버리지)  
  - Redis 분산락 → Race Condition 방지  
- **모니터링**: Prometheus (메트릭 수집) → Grafana (대시보드 시각화)  

---

## 🏗️ 시스템 아키텍처

아래 다이어그램은 Clubing이 구성된 전체 시스템 흐름을 보여줍니다:  
<img width="718" alt="시스템 전체 구조" src="https://github.com/user-attachments/assets/c3032625-3f92-4479-a4a1-afbe29b6f384" />

### 📊 ERD  
<img width="653" alt="ERD 다이어그램" src="https://github.com/user-attachments/assets/c97fadcc-26c2-4652-92f0-6673ac211251" />

### 🖥️ 시스템 구조  
<img width="207" alt="서브시스템 모델" src="https://github.com/user-attachments/assets/68fd1a24-efcf-43dc-a205-6df589dca2c7" />

---

## 🌐 배포 환경

- **Frontend (Vercel)**  
  - 저장소: `main` 브랜치에 커밋 시 자동 빌드 및 배포  
  - HTTPS: Vercel 기본 SSL 적용

- **Backend (AWS EC2)**  
  - OS: Ubuntu 20.04  
  - Web Server: Nginx (Reverse Proxy)  
  - Application: Spring Boot JAR (포트 8080)  
  - 데이터베이스: MySQL (Amazon RDS)  
  - 캐시/세션: Redis (ElastiCache)  
  - TLS 인증서: Let’s Encrypt (Certbot)  
  - CI/CD: GitHub Actions → EC2 배포 스크립트 (push → 빌드 → 서비스 재시작)  
  - 모니터링: Prometheus (메트릭 수집) → Grafana (대시보드 시각화)

---

## 👥 기여자

- **강경서** – Frontend 리드  
  - React(Vite) 컴포넌트 설계 및 구현  
  - Vercel 배포 설정 및 환경 변수 관리  

- **이한식** – Backend 리드  
  - Spring Boot API 개발 및 AWS EC2 인프라 구성  
  - MySQL, Redis 연동 및 JWT/CORS 설정   

---

## 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다. 자세한 내용은 [LICENSE](./LICENSE) 파일을 참고하세요.

























