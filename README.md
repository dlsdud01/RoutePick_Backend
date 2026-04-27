<div align="center">

# 🧭 RoutePick

### *여행지를 고르면, 최적의 경로를 알려드립니다*

> 사용자 설문 기반 **AI 여행 일정 생성 + Google Maps 경로 최적화** 웹 서비스

<br/>

[![Backend](https://img.shields.io/badge/Backend-Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)](https://github.com/tjoeunProject/Backend)
[![Frontend](https://img.shields.io/badge/Frontend-React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://github.com/tjoeunProject/Frontend)
[![AI](https://img.shields.io/badge/AI-Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/tjoeunProject/Backend)
[![Deploy](https://img.shields.io/badge/Deploy-AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white)](https://github.com/tjoeunProject/Backend)

</div>

---

## 📌 프로젝트 소개

여행지를 하나하나 검색하고 동선을 직접 짜야 하는 번거로움을 줄이기 위해 만든 서비스입니다.

> 사용자 설문 입력 → POI 데이터 수집 → AI 일정 생성 → Google Maps 경로 시각화

사용자는 간단한 입력만으로 여행 일정을 추천받고, 최적의 이동 경로를 지도에서 바로 확인할 수 있습니다.

---

## 👩‍💻 내 담당 역할

> ※ 이 레포지토리는 팀 프로젝트 원본을 **포크하여 본인의 담당 역할 기록용으로 재구성**한 것입니다.
> React 프론트엔드 및 Python AI 로직은 팀원이 담당했습니다.
> 원본 팀 레포 → [tjoeunProject/Backend](https://github.com/tjoeunProject/Backend)

| 영역 | 담당 내용 |
|------|-----------|
| **DB 설계** | Oracle ERD 설계, 테이블 정의 및 관계 설정 |
| **Spring Boot 서버** | STS 환경 구축, REST API 설계, JPA 기반 CRUD 구현 |
| **인증** | Spring Security + JWT Access/Refresh Token 인증 구조 적용 |
| **AI 연동** | Python FastAPI 기반 경로 최적화 서버 ↔ Spring Boot 간 데이터 파이프라인 연결 참여 |
| **AWS 배포** | EC2(Spring Boot), RDS(Oracle), S3, Lambda, Docker 기반 배포 구성 |

---

## ✨ 주요 기능

### 🗺️ AI 기반 여행 일정 생성
사용자가 여행 지역과 선호 키워드를 입력하면, Google Maps API + Gemini AI 기반으로 POI 데이터를 수집하고 일정을 자동 생성합니다.

### 📍 경로 최적화
k-means 알고리즘을 활용해 근거리 우선으로 여행지를 배치하고 최적 경로를 지도에 시각화합니다.

### 🔐 인증
Spring Security + JWT (Access / Refresh Token) 기반 인증을 적용했습니다.

### 💾 일정 저장 및 조회
생성된 여행 일정을 저장하고, 마이페이지에서 조회·관리할 수 있습니다.

---

## 🏗️ 아키텍처

```
┌─────────────────────────────────────────────┐
│              React App (S3 호스팅)            │
└──────────────────┬──────────────────────────┘
                   │ REST API
     ┌─────────────▼──────────────┐
     │   Spring Boot (EC2)         │
     │   - JWT 인증                │
     │   - 여행 일정 CRUD          │
     │   - AI 서비스 연동          │
     └──────┬──────────┬──────────┘
            │          │
 ┌──────────▼──┐  ┌────▼────────────────────┐
 │  Oracle DB  │  │  Python AI Service       │
 │  (RDS)      │  │  (Lambda + API Gateway)  │
 └─────────────┘  └──────────────────────────┘

  외부 API: Google Maps API / Gemini / SerpAPI
```

---

## 🛠️ 기술 스택

### Backend *(담당)*

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white)

### Frontend *(팀원 담당)*

![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

### AI / External API *(팀원 담당 + 연동 참여)*

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-4285F4?style=flat-square&logo=google&logoColor=white)
![Google Maps](https://img.shields.io/badge/Google_Maps-4285F4?style=flat-square&logo=googlemaps&logoColor=white)

### Infra / Deploy *(담당)*

![AWS EC2](https://img.shields.io/badge/EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white)
![AWS RDS](https://img.shields.io/badge/RDS-527FFF?style=flat-square&logo=amazonrds&logoColor=white)
![AWS S3](https://img.shields.io/badge/S3-569A31?style=flat-square&logo=amazons3&logoColor=white)
![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?style=flat-square&logo=awslambda&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## 📊 DB 설계 (ERD 주요 테이블)

```
tb_user          사용자 계정 (이메일, 닉네임, 권한)
tb_schedule      여행 일정 (제목, 지역, 시작·종료일, 생성일시)
tb_place         장소 (이름, 위도, 경도, 카테고리, 평점)
tb_schedule_place  일정-장소 매핑 (방문 순서 포함)
tb_review        장소 리뷰 (내용, 평점, 작성자)
```

---

## 🚀 배포 구조

| 서비스 | 배포 방식 |
|--------|-----------|
| React 프론트엔드 | **S3** 정적 호스팅 |
| Spring Boot API | JAR 빌드 → **EC2** 실행 |
| Python AI 서비스 | **Lambda** + API Gateway |
| DB | **RDS** (Oracle) |
| 도메인 | Route 53 (`routepick.store`) *(현재 비용 문제로 비활성화)* |

---

## 📁 프로젝트 구조

```
Backend/
├── sts/                  # Spring Boot 메인 서버
│   ├── config/           # Security, JWT 설정
│   ├── controller/       # API 엔드포인트
│   ├── service/          # 비즈니스 로직
│   ├── repository/       # Oracle DB 연동 (JPA)
│   └── entity/           # 도메인 모델 (user, schedule, place ...)
└── python/               # Python AI 서비스
    ├── app.py            # FastAPI 진입점
    └── requirements.txt
```

---

## 🔧 트러블슈팅

### 1. EC2 ↔ RDS 연결 실패

**문제** : EC2에서 Spring Boot 서버 실행 후 Oracle RDS 연결이 되지 않는 오류 발생

**원인** : RDS 보안 그룹 인바운드 규칙에 EC2의 IP 대역이 허용되지 않은 것을 CloudWatch 및 서버 로그에서 확인
```
Communications link failure / Connection refused
```

**해결** : RDS 보안 그룹에 EC2 보안 그룹을 인바운드 소스로 추가하여 해결

---

### 2. FastAPI ↔ Spring Boot 데이터 파이프라인 연결 오류

**문제** : Spring Boot에서 Python FastAPI 서버로 경로 최적화 요청 시 응답 파싱 실패

**원인** : FastAPI의 응답 JSON 구조와 Spring Boot에서 기대하는 DTO 구조가 불일치

**해결** : FastAPI 응답 필드명과 Spring Boot DTO 필드를 맞추고, 응답 역직렬화 구조를 정리하여 해결

---

### 3. CORS 설정 오류 (배포 환경)

**문제** : 로컬에서는 정상 동작했으나 S3(프론트) + EC2(백엔드) 배포 환경에서 CORS 오류 발생

**원인** : Spring Boot CORS 설정에 S3 도메인이 허용 Origin으로 등록되지 않음

**해결** : `WebMvcConfigurer`의 `addCorsMappings`에 S3 배포 도메인 추가

---

## 🔁 원본 레포지토리 안내

> 이 레포지토리는 팀 프로젝트 원본을 **포크하여 본인의 담당 역할 기록용으로 재구성**한 것입니다.
> 실제 코드와 전체 협업 내역은 아래 원본 팀 레포지토리에서 확인하실 수 있습니다.

| 구분 | 링크 |
|------|------|
| 🖥️ **백엔드 원본** (Spring Boot + Python AI) | https://github.com/tjoeunProject/Backend |
| 📱 **프론트엔드 원본** (React) | https://github.com/tjoeunProject/Frontend |

---

<div align="center">

[![Backend Repo](https://img.shields.io/badge/팀_Backend_Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/tjoeunProject/Backend)
[![Frontend Repo](https://img.shields.io/badge/팀_Frontend_Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/tjoeunProject/Frontend)
[![Portfolio](https://img.shields.io/badge/포트폴리오-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/dlsdud01/portfolio)

</div>
