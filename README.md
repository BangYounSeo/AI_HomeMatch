![header](https://capsule-render.vercel.app/api?type=transparent&height=100&section=header&text=Home'Scan&fontSize=48&fontColor=4B6BFB)
<br/>

## [프로젝트 소개]

Home'Scan은 복잡한 임대차 계약 과정을 보다 안전하고 체계적으로 관리하기 위해 개발된 **부동산 임대차 관리 플랫폼**입니다.  

AI 기반 계약서 및 등기부등본 분석으로 주요 조항과 잠재적 위험 요소를 점검할 수 있도록 지원하며, 매물 검증과 거주·퇴실 관리 기능을 제공합니다.  
또한, 챗봇을 통한 계약 조항 및 법률 정보 질의응답과 문서 보관·처리 동의 설정 기능을 포함해 통합 관리 환경을 구현했습니다.  
본 서비스는 법률적 판단을 대체하지 않으며, 사용자의 합리적인 **의사결정을 지원하는 보조 도구**로 설계되었습니다.

<br/>

## [기술 스택]

<table width="100%">
<tr>
<td width="50%" valign="top">

### Backend

![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge)
![Spring WebFlux](https://img.shields.io/badge/Spring_WebFlux-6DB33F?style=for-the-badge)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)
![JWT (jjwt)](https://img.shields.io/badge/JWT_(jjwt)-000000?style=for-the-badge)
![dotenv-java](https://img.shields.io/badge/dotenv--java-000000?style=for-the-badge)
![Apache PDFBox](https://img.shields.io/badge/Apache_PDFBox-D22128?style=for-the-badge)
![FastAPI 연동 — 등기부등본 AI 분석](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)

</td>

<td width="50%" valign="top">

### Frontend

![React 19](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![React Router DOM](https://img.shields.io/badge/React_Router_DOM-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Lucide React](https://img.shields.io/badge/Lucide_React-000000?style=for-the-badge)
![Recharts](https://img.shields.io/badge/Recharts-FF6384?style=for-the-badge)

</td>
</tr>

<tr>
<td valign="top">

### Database

![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)

</td>

<td valign="top">

### Server / Tool

![Apache Tomcat (Embedded)](https://img.shields.io/badge/Apache_Tomcat_(Embedded)-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)
![Git / Github](https://img.shields.io/badge/Git_/_Github-F05032?style=for-the-badge&logo=git&logoColor=white)

</td>
</tr>
</table>

<br/>

## [프로젝트 구성]

#### 프로젝트 유형 : 팀 프로젝트 / **개발 인원** : 5명 / **개발 기간** : 22일


#### (1) 프로젝트 전체 기능 개요

- **랜딩/인증**: 랜딩 페이지, 로그인, 회원가입
- **홈/매물**: 홈, 매물 리스트, 매물 상세
- **계약서**: 계약서 AI 점검(업로드·분석), 계약서 상세, 중개사 설명 vs 계약서 불일치
- **등기부등본**: 등기부등본 업로드·분석, 보관/삭제 설정
- **거주·퇴실**: 거주 중 관리, 퇴실·분쟁 예방
- **문서 동의**: 문서 보관·처리 동의 페이지, 마이페이지 내 동의 설정·철회
- **챗봇**: 플로팅 챗봇(거주·퇴실 주제별 안내 및 문서 기능 유도 등 사이트 가이드)
- **마이페이지**: 프로필, 데이터 출처·면책 안내, 문서 삭제/보관 설정, **문서 보관 및 처리 동의 설정**
- **관리자**: Admin 페이지


#### (2) 담당 역할
- **챗봇**: 플로팅 챗봇 UI, 주제별 대화·추천 질문, 스트리밍 응답, 문서 기능 연동 및 동의 유도
- **문서 보관 및 처리 동의 설정**: 동의 페이지·마이페이지 탭, 동의 API 연동, 계약서·등기부등본 등 문서 기능과의 연동

<br/>

## [담당 기능 상세 (챗봇, 문서 보관·처리 동의)]

#### (1) 챗봇
- 서비스 전역에서 사용할 수 있는 **플로팅 챗봇** UI 구성(열기/접기/최소화, 주제 선택)
- 주제별(계약서 점검, 등기부등본, 거주관리, 퇴실관리) 대화·추천 질문 및 **스트리밍 응답** 연동
- 계약서 점검·등기부등본 등 문서 관련 기능 사용 시 **문서 보관·처리 동의** 미완료 사용자는 동의 페이지로 유도
- 백엔드 `ChatbotController`(`/api/chatbot`) 및 `ChatbotService`, OpenAI 연동, 세션·메시지 저장(chat_sessions, chat_messages)과의 연동


#### (2) 문서 보관 및 처리 동의 설정
- **동의 페이지**(`DocumentConsentPage` · `/consents/document`): 문서 저장·분석 처리 동의 문구 노출, 체크 후 동의 저장, 쿼리(next, context, reason, preview, version, types) 지원
- **마이페이지 “문서 보관 및 처리 동의 설정” 탭**: 동의 상태 표시, 동의 내용 보기(새 창), **동의 철회** 처리
- **문서 기능과의 연동**: 계약서 점검(`ContractReviewUploadPage`), 등기부등본 분석(`DeedAnalysisPage`) 등에서 업로드/분석 전 동의 여부 확인, 미동의 시 동의 페이지로 리다이렉트 후 원래 기능으로 복귀
- **백엔드**: `UserConsentController` — `GET /api/consents/required`, `POST /api/consents/agree`, `GET /api/consents/me`, `POST /api/consents/withdraw` 및 서비스·DB(user_consents) 설계

<br/>

## [DB 설정 구조(보안 분리)]

DB 접속 정보는 보안 및 환경 분리를 위해 Git에 직접 포함하지 않습니다.

####  (1) 설정 방식
- `backend/.env` — Git 제외 권장
- `application.yml` — DB URL/계정은 환경 변수 참조 (`DB_URL`, `DB_USER`, `DB_PASSWORD`)
- BackendApplication에서 dotenv 및 시스템 환경 변수로 `spring.datasource.*` 주입

#### (2) 환경 변수 (주요 항목)
- `DB_URL` — 예: `jdbc:mariadb://localhost:3306/homematch`
- `DB_USER` — DB 사용자명
- `DB_PASSWORD` — DB 비밀번호
- `PORT` — 서버 포트 (기본 8080)
- (선택) `FASTAPI_BASE_URL` — 등기부등본 AI용 FastAPI 주소
- (선택) OpenAI API Key 등 — 백엔드에서 사용하는 경우

#### (3) 테이블 (담당 기능 관련)
- **user_consents**: 동의 유형(consent_type), 버전(version), 동의/철회 시각(agreed_at, withdrawn_at) 등
- **chat_sessions**, **chat_messages**: 챗봇 세션 및 메시지  

<br/>

전체 스키마는 `backend/create_tables.sql` 참고.

<br/>

## [실행 방법]

#### (1) 환경
- JDK 17 이상
- Node.js (npm)
- MariaDB

#### (2) DB 설정
- `backend/create_tables.sql`로 테이블 생성
- `backend/.env`에 `DB_URL`, `DB_USER`, `DB_PASSWORD` 설정 (또는 시스템 환경 변수)

#### (3) 실행_백엔드
- `backend` 폴더에서 `.\gradlew bootRun`
- API 서버: http://localhost:8080 (기본)

#### (4) 실행_프론트엔드
- `frontend` 폴더에서 `npm install` 후 `npm run dev`
- 브라우저: http://localhost:5173 (Vite 기본)

<br/>

## [주요 페이지(라우트)]
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

<br/>

## [프로젝트를 통해 얻은 점]
- 플로팅 챗봇 UI/UX 및 주제별 대화·스트리밍 응답 연동 경험
- 문서 처리 전 사용자 동의 수집·이력 관리·철회 플로우 설계 및 구현
- 동의 상태에 따른 문서 기능(계약서·등기부등본) 진입 제어 및 리다이렉트 연동
- JWT 기반 인증과 결합한 동의 API·DB 설계 경험

<br/>

## [참고]
- 문서 실제 보관·삭제는 마이페이지의 **문서 삭제/보관 설정** 탭에서 관리합니다.
- 동의 내용은 “문서 저장 및 분석 처리 동의” 문구로 제공되며, 버전·타입은 API/쿼리로 확장 가능합니다.
- 본 프로젝트는 학습 및 포트폴리오 목적의 팀 프로젝트이며, 실제 서비스 흐름을 고려한 구조로 구현되었습니다.

<br/>

**프로젝트 발표 자료(PPT)** : https://drive.google.com/file/d/1MBtbtSqTyN4Y7X5dN_6h8cx9JE4oOdB-/view?usp=drive_link
