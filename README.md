# Home'Scan

## 프로젝트 소개

Home'Scan은 복잡한 주거 문제를 스마트하게 해결하는 **부동산 임대차 관리 플랫폼**입니다.
계약부터 입주, 퇴실까지 전 과정을 지원하며, AI 기반 계약서 분석, 등기부등본 분석, 매물 검증, 거주·퇴실 관리 기능을 제공합니다.
사용자는 계약서·등기부등본 업로드 및 AI 분석, 챗봇 어시스턴트를 통해 계약 조항·법률 정보 질의응답, 문서 보관·처리 동의 설정 등을 활용할 수 있습니다.

## 기술 스택

### Backend
- Spring Boot 3.2.1
- Spring Security (JWT 인증)
- Spring Data JPA
- Spring WebFlux (OpenAI API 호출)
- MariaDB
- JWT (jjwt)
- dotenv-java (환경 변수)
- Apache PDFBox (PDF 처리)
- (선택) FastAPI 연동 — 등기부등본 AI 분석

### Frontend
- React 19
- TypeScript
- Vite
- React Router DOM
- Tailwind CSS
- Lucide React
- Recharts

### Database
- MariaDB

### Server/Tool
- Apache Tomcat (Embedded)
- Gradle
- Git / Github

## 프로젝트 구성

### 프로젝트 유형
팀 프로젝트

### 개발 인원
5명

### 개발 기간
며칠이여

### 담당 역할 (본인 구현 기능)
- **챗봇**: 플로팅 챗봇 UI, 주제별 대화·추천 질문, 스트리밍 응답, 문서 기능 연동 및 동의 유도
- **문서 보관 및 처리 동의 설정**: 동의 페이지·마이페이지 탭, 동의 API 연동, 계약서·등기부등본 등 문서 기능과의 연동

## 프로젝트 전체 기능 개요

- **랜딩/인증**: 랜딩 페이지, 로그인, 회원가입
- **홈/매물**: 홈, 매물 리스트, 매물 상세
- **계약서**: 계약서 AI 점검(업로드·분석), 계약서 상세, 중개사 설명 vs 계약서 불일치
- **등기부등본**: 등기부등본 업로드·분석, 보관/삭제 설정
- **거주·퇴실**: 거주 중 관리, 퇴실·분쟁 예방
- **문서 동의**: 문서 보관·처리 동의 페이지, 마이페이지 내 동의 설정·철회
- **챗봇**: 플로팅 챗봇(계약서·등기부등본·거주·퇴실 주제별 안내 및 문서 기능 유도)
- **마이페이지**: 프로필, 데이터 출처·면책 안내, 문서 삭제/보관 설정, **문서 보관 및 처리 동의 설정**
- **관리자**: Admin 페이지

## 담당 기능 상세 (챗봇, 문서 보관·처리 동의)

### 챗봇
- 서비스 전역에서 사용할 수 있는 **플로팅 챗봇** UI 구성(열기/접기/최소화, 주제 선택)
- 주제별(계약서 점검, 등기부등본, 거주관리, 퇴실관리) 대화·추천 질문 및 **스트리밍 응답** 연동
- 계약서 점검·등기부등본 등 문서 관련 기능 사용 시 **문서 보관·처리 동의** 미완료 사용자는 동의 페이지로 유도
- 백엔드 `ChatbotController`(`/api/chatbot`) 및 `ChatbotService`, OpenAI 연동, 세션·메시지 저장(chat_sessions, chat_messages)과의 연동

### 문서 보관 및 처리 동의 설정
- **동의 페이지**(`DocumentConsentPage` · `/consents/document`): 문서 저장·분석 처리 동의 문구 노출, 체크 후 동의 저장, 쿼리(next, context, reason, preview, version, types) 지원
- **마이페이지 “문서 보관 및 처리 동의 설정” 탭**: 동의 상태 표시, 동의 내용 보기(새 창), **동의 철회** 처리
- **문서 기능과의 연동**: 계약서 점검(`ContractReviewUploadPage`), 등기부등본 분석(`DeedAnalysisPage`) 등에서 업로드/분석 전 동의 여부 확인, 미동의 시 동의 페이지로 리다이렉트 후 원래 기능으로 복귀
- **백엔드**: `UserConsentController` — `GET /api/consents/required`, `POST /api/consents/agree`, `GET /api/consents/me`, `POST /api/consents/withdraw` 및 서비스·DB(user_consents) 설계

## DB 설정 구조(보안 분리)

DB 접속 정보는 보안 및 환경 분리를 위해 Git에 직접 포함하지 않습니다.

### 설정 방식
- `backend/.env` — Git 제외 권장
- `application.yml` — DB URL/계정은 환경 변수 참조 (`DB_URL`, `DB_USER`, `DB_PASSWORD`)
- BackendApplication에서 dotenv 및 시스템 환경 변수로 `spring.datasource.*` 주입

### 환경 변수 (주요 항목)
- `DB_URL` — 예: `jdbc:mariadb://localhost:3306/homematch`
- `DB_USER` — DB 사용자명
- `DB_PASSWORD` — DB 비밀번호
- `PORT` — 서버 포트 (기본 8080)
- (선택) `FASTAPI_BASE_URL` — 등기부등본 AI용 FastAPI 주소
- (선택) OpenAI API Key 등 — 백엔드에서 사용하는 경우

### 테이블 (담당 기능 관련)
- **user_consents**: 동의 유형(consent_type), 버전(version), 동의/철회 시각(agreed_at, withdrawn_at) 등
- **chat_sessions**, **chat_messages**: 챗봇 세션 및 메시지

전체 스키마는 `backend/create_tables.sql` 참고.

## 실행 방법

### 환경
- JDK 17 이상
- Node.js (npm)
- MariaDB
- (선택) Python 3 — 등기부등본 FastAPI 분석 서비스 사용 시

### DB 설정
- `backend/create_tables.sql`로 테이블 생성
- `backend/.env`에 `DB_URL`, `DB_USER`, `DB_PASSWORD` 설정 (또는 시스템 환경 변수)

### 실행

**백엔드**
- `backend` 폴더에서 `.\gradlew bootRun`
- API 서버: http://localhost:8080 (기본)

**프론트엔드**
- `frontend` 폴더에서 `npm install` 후 `npm run dev`
- 브라우저: http://localhost:5173 (Vite 기본)

**등기부등본 AI (선택)**
- FastAPI 서비스 실행 시 `FASTAPI_BASE_URL` 설정 후 사용

## 주요 페이지(라우트)
- `/` — 랜딩
- `/login`, `/signup` — 로그인/회원가입
- `/home` — 홈(로그인 후 메인)
- `/properties`, `/properties/:id` — 매물 리스트/상세
- `/contract/review`, `/contract/review/upload`, `/contract/review/detail` — 계약서 점검
- `/contract/deed` — 등기부등본 분석
- `/consents/document` — 문서 보관·처리 동의
- `/residency` — 거주 중 관리
- `/moveout` — 퇴실·분쟁 예방
- `/mypage` — 마이페이지(프로필, 문서 삭제/보관, **문서 보관 및 처리 동의 설정** 등)
- `/admin` — 관리자

(챗봇은 플로팅 컴포넌트로 전역 노출)

## 프로젝트를 통해 얻은 점 (담당 기능 기준)
- 플로팅 챗봇 UI/UX 및 주제별 대화·스트리밍 응답 연동 경험
- 문서 처리 전 사용자 동의 수집·이력 관리·철회 플로우 설계 및 구현
- 동의 상태에 따른 문서 기능(계약서·등기부등본) 진입 제어 및 리다이렉트 연동
- JWT 기반 인증과 결합한 동의 API·DB 설계 경험

## 참고
- 문서 실제 보관·삭제는 마이페이지의 **문서 삭제/보관 설정** 탭에서 관리합니다.
- 동의 내용은 “문서 저장 및 분석 처리 동의” 문구로 제공되며, 버전·타입은 API/쿼리로 확장 가능합니다.
- 본 프로젝트는 학습 및 포트폴리오 목적의 팀 프로젝트이며, 실제 서비스 흐름을 고려한 구조로 구현되었습니다.
