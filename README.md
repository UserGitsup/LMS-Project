# 🎓 RE-MERGE LMS
> Java Spring 기반 학사 관리 시스템 — 4인 팀 프로젝트

![Java](https://img.shields.io/badge/Java_17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/Spring_Framework-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![JSP](https://img.shields.io/badge/JSP-007396?style=for-the-badge&logo=java&logoColor=white)

---

## 📌 프로젝트 개요

| 항목 | 내용 |
|------|------|
| **프로젝트명** | RE-MERGE LMS |
| **개발 기간** | 2026.04 ~ 2026.05 |
| **팀 구성** | 4인 팀 |
| **역할** | 강의 목록 개설 / 학점 계산 / 강의별 세부 페이지 (교수·학생·관리자) |

> 단과대학 학사 행정 전반을 디지털화한 LMS입니다. 교수, 학생, 관리자 각각의 역할에 맞는 독립적인 인터페이스를 제공하며, 수강 신청부터 학점 산출까지 전 과정을 구성하였습니다.

---

## ✨ 담당 기능

### 📚 강의 목록 개설
- 관리자가 학기별 강의를 등록하고 수강 인원·학점·시간표를 설정
- 강의 상태(개설/마감/폐강) 관리 기능

### 🧮 학점 계산
- 출석·과제·중간·기말 비율 기반 최종 학점 자동 산출
- 성적 분포 조회 및 학점 통계 시각화

### 🖥️ 역할별 강의 세부 페이지
| 역할 | 제공 기능 |
|------|-----------|
| **교수** | 수강생 명단 조회, 성적 입력/수정, 공지사항 등록, 출석 입력 |
| **학생** | 강의 자료 열람, 본인 성적 확인, 출석 현황 조회 |
| **관리자** | 강의 전체 현황 모니터링, 게시판 관리 |

---

## 🛠 Tech Stack

| 분류 | 기술 |
|------|------|
| **Language** | Java 17 |
| **Backend** | Spring Framework |
| **Frontend** | JSP, JavaScript (Fetch API) |
| **Database** | MariaDB 11.7.2 |
| **Build** | Maven |

---

## 🏗️ 아키텍처

```
RE-MERGE-LMS/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/remerge/lms/
│   │   │       ├── config/         # Spring 설정 (Mail, MVC, NaverLogin 등)
│   │   │       ├── controller/     # 요청 처리 및 뷰 반환
│   │   │       ├── dao/            # MariaDB 기반 DB 접근 계층
│   │   │       ├── dto/            # 계층 간 데이터 전달 객체
│   │   │       ├── exception/      # 커스텀 예외 클래스
│   │   │       ├── handler/        # 전역 예외 처리 핸들러
│   │   │       ├── interceptor/    # 로그인 인증 등 요청 인터셉터
│   │   │       ├── service/        # 비즈니스 로직 처리
│   │   │       └── sitemesh/       # Sitemesh 레이아웃 데코레이터
│   │   └── webapp/
│   │       ├── WEB-INF/views/      # JSP 뷰
│   │       └── resources/          # CSS, JS, 이미지
├── docs/
│   ├── requirements-analysis.pdf
│   ├── LMS_Wireframe.pdf
│   └── erd.png
└── pom.xml
```

---

## 🏆 성과
 
- `Course` 관련 Controller · Service · DAO · DTO · JSP 전 계층 단독 구현
- 교수 / 학생 / 관리자 **3가지 역할**에 맞는 강의 세부 페이지를 각각 설계 및 구현
- 강의 목록 개설부터 학점 산출까지 **강의 도메인 전체 플로우** 담당
---
 
## 🔥 트러블슈팅
 
### Sitemesh 중첩 레이아웃 적용 문제
 
**상황**
-역할별 강의 세부 페이지를 구현할 때, 공통 레이아웃(Sitemesh decorator) 안에 강의 전용 서브 레이아웃을 중첩 적용해야 했습니다. 그러나 내부 decorator가 렌더링되지 않거나 외부 레이아웃과 충돌하는 문제가 발생했습니다.
 
**원인**
-Sitemesh는 기본적으로 단일 decorator 적용을 전제로 동작하며, 중첩 decorator를 사용하려면 내부 페이지가 별도의 decorator 체인을 명시적으로 타도록 설정해야 합니다. 설정 누락으로 인해 내부 decorator가 무시되고 있었습니다.
 
**해결**
-`sitemesh.xml` 및 decorator 설정을 수정하여 중첩 decorator 체인이 올바르게 동작하도록 구성하였고, 역할별 페이지마다 적절한 decorator가 순서대로 적용되는 것을 확인했습니다.

---

## 📂 프로젝트 문서

| 구분 | 문서명 | 링크 |
|:---|:---|:---|
| **기획** | 요구사항 분석서 | [requirements-analysis.pdf](./docs/requirements-analysis.pdf) |
| **설계** | UI/UX 화면 설계 및 기능 분석 | [LMS_Wireframe.pdf](./docs/LMS_Wireframe.pdf) |
| **DB** | ERD 설계도 | [erd.png](./docs/erd.png) |

---

## 🔀 Git 협업 규칙

### Commit Convention

| 태그 | 설명 | 예시 |
|------|------|------|
| `feat` | 새로운 기능 추가 | `feat: 로그인 기능 구현` |
| `fix` | 버그 수정 | `fix: 회원가입 유효성 검사 수정` |
| `edit` | 기존 코드 수정 및 로직 변경 | `edit: 대시보드 조회 로직 최적화` |
| `style` | UI/UX 디자인 및 CSS 수정 | `style: 사이드바 디자인 변경` |
| `docs` | 문서 수정 (README, 설계서 등) | `docs: 설계서 링크 업데이트` |
| `chore` | 빌드 설정 및 라이브러리 관리 | `chore: pom.xml 의존성 추가` |

### Workflow
1. **Branch** — 본인 이름 브랜치에서 작업
2. **Push** — 기능 구현 완료 후 원격 브랜치에 push
3. **Merge** — PR 생성 후 `main` 브랜치에 병합

---

## 👥 구성

| 이름 | 역할 |
|------|------|
| **UserGitsup** | 강의 목록 개설, 학점 계산, 역할별 세부 페이지 |
