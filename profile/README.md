# 스미싱 예방 교육 및 탐지 시스템

**의심스러운 링크를 확인하고, 위험한 이유와 대응 방법까지 배우는 스미싱 예방 서비스**

한국교통대학교 컴퓨터소프트웨어학과 캡스톤디자인 프로젝트입니다.  
사용자가 제출한 URL·문자 메시지·QR 이미지를 분석하고, 판단 근거와 예방 교육을 함께 제공합니다.

[기능 명세](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/01_Feature_Specification.md) · [사용자 흐름](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/02_User_Flow.md) · [시스템 구조](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/03_System_Architecture.md) · [API 명세](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/05_API_Specification.md) · [UI 설계](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/06_UI_Design.md)

> 현재 MVP 설계 및 개발 준비 단계입니다. 아래 내용은 구현 목표이며, 동작 중인 서비스나 검증된 탐지 성능을 의미하지 않습니다. 기술 세부사항은 팀 검토를 거쳐 조정합니다.

## 어떤 서비스인가요?

택배 안내, 청첩장, 공공기관 알림처럼 보이는 메시지를 받았을 때 링크를 열기 전에 확인할 수 있는 서비스를 만듭니다. 분석 결과에서는 위험도와 함께 의심스러운 부분, 확인 방법, 이후 행동을 설명합니다.

검사에서 끝나지 않고 관련 스미싱 사례와 퀴즈로 이어져, 사용자가 비슷한 상황을 스스로 판단할 수 있도록 돕는 것이 목표입니다.

## 차별점과 서비스 모델

이 프로젝트는 위험 여부만 보여주는 검사 도구가 아니라 **판정 근거 → 즉시 대응 → 관련 사례 학습 → 퀴즈**로 이어지는 예방 교육 흐름을 함께 제공합니다. 기본 검사와 공개 교육은 회원가입 없이 무료로 제공해 누구나 빠르게 이용할 수 있도록 설계합니다.

후속 단계에서는 학교·기업·공공기관이 구성원을 초대하고 교육을 배정하며 이수 현황과 익명화된 학습 통계를 확인하는 **기관용 보안 교육 SaaS**를 핵심 사업 모델로 검토합니다. 검사 API 제공과 기관별 맞춤 콘텐츠·운영 지원도 확장 후보입니다. 실제 요금제, 결제와 청구 기능은 MVP에 포함하지 않습니다.

## 이번에 만드는 기능

- **URL 검사:** 주소와 도메인 특징, 다운로드 유도 등 위험 신호를 분석합니다.
- **문자 검사:** 위험 문구와 패턴을 찾고, 포함된 URL을 함께 검사합니다.
- **QR 검사:** 이미지에서 주소를 추출해 검사합니다. 추출된 링크는 자동으로 열지 않습니다.
- **결과 안내:** 위험 등급·점수·판단 근거·권장 행동을 한 화면에 제공합니다.
- **예방 교육:** 대표 유형 7개 이상의 사례와 예방·대응 방법을 제공합니다.
- **퀴즈:** 로그인 없이 10문제를 풀고 최종 제출 후 정답과 해설을 확인합니다.

이용 흐름은 **검사 유형 선택 → 자료 입력 → 분석 → 결과 확인 → 대응 방법·관련 교육**입니다.

### 분석 결과는 이렇게 다룹니다

초기에는 설명 가능한 규칙 기반 분석을 사용합니다. 점수에 따라 안전·주의·위험을 표시하고, 확인된 중대한 위험 신호는 별도 근거와 함께 반영합니다. 점수는 악성일 확률이 아니며 배점과 기준은 평가 데이터를 통해 검증할 예정입니다.

일부 분석이 실패하면 검사하지 못한 범위를 표시합니다. URL이 아닌 QR 데이터에는 안전 점수를 매기지 않고 ‘URL 분석 대상 아님’을 안내합니다. 위험 신호가 발견되지 않았더라도 대상의 안전을 보장하지 않습니다.

## 개발 범위

**MVP에 집중하는 기능:** URL·문자·QR 검사, 공통 결과 화면, 예방 교육, 퀴즈.

**2차 개발 후보:** 개인 회원과 학습 기록, 기관 초대·교육 배정·이수 관리, 익명 통계, 문자 캡처 OCR, 결과 저장·공유, 사용자 피드백, 관리자 기능.

**도전 기능:** 가짜 로그인 페이지의 동적 분석, 조작 이미지 판별, 개인 검사 이력. 자체 AI 모델 학습은 현재 MVP 범위에 포함하지 않습니다.

외부 평판 조회는 선택 기능으로 두고, 내부 규칙 분석만으로도 기본 검사가 가능하도록 설계합니다.

## 기술 구성

- **Frontend — 제안:** Next.js, React, TypeScript, Tailwind CSS
- **Backend — 제안:** Python, FastAPI, OpenCV 기반 QR 분석
- **Database — 사용 결정:** 사용자 OCI 서버에서 Docker PostgreSQL 운영
- **배포 — 제안:** FE는 Vercel, BE는 OCI의 Docker 컨테이너
- **협업:** GitHub 저장소, Issues, Pull Requests, Markdown 설계 문서

FE는 입력과 결과 화면을 담당하고, BE는 분석·점수 계산·교육 조회·퀴즈 채점을 담당합니다. PostgreSQL은 교육 사례, 예방수칙, 퀴즈 문제·선택지·정답·해설을 저장합니다. 탐지 규칙은 BE 저장소에서 버전 관리합니다.

DB를 사용하는 구조로 결정했으며 실제 서버 설치와 운영 검증은 별도 개발 작업입니다.

## 데이터 처리 원칙

- 검사한 문자·URL·QR 이미지와 개인 검사 이력을 DB에 저장하지 않습니다.
- QR 임시 이미지는 정상 처리 후 즉시 삭제하고, 실패 시에도 업로드 후 10분 이내 정리하는 정책으로 설계합니다.
- 퀴즈는 서버에서 채점하지만 개인 답안과 점수 기록은 저장하지 않습니다.
- 2차 개인 기록은 사용자가 명시적으로 선택한 비식별 결과 요약만 저장하며 기관에는 검사 원문을 제공하지 않습니다.
- MVP 분석 서버는 의심 사이트에 직접 접속하거나 파일을 실행하지 않습니다.
- 원문과 민감한 정보는 로그·이슈·PR에 올리지 않습니다.

## 팀원과 담당 업무

- **이영수 · PM / Full-Stack / DevOps:** 일정·문서 관리, 시스템 구조, FE·BE 통합, OCI·Docker·PostgreSQL 배포
- **민승호 · Frontend:** Next.js 화면 구현, 입력 검증, API 연동, 반응형 UI
- **임찬우 · Detection / Data:** URL·문자 탐지 규칙, 위험 점수 기준, 테스트 데이터와 탐지 성능 평가
- **김흥원 · Backend:** FastAPI, 분석 API, QR 처리, DB 연동, 교육 조회와 퀴즈 채점

팀원 모두 자신의 기능 테스트, 코드 리뷰, 통합 시연과 발표 준비에 참여합니다.

## 저장소 안내

- [Frontend](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-FE): 화면과 사용자 상호작용, API 연동
- [Backend](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-BE): 분석 로직, API, DB 및 배포 구성
- [Docs](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs): 요구사항, 사용자 흐름, 시스템·DB·API 설계
- [.github](https://github.com/KNUT-Capstone-Design/.github): 조직 소개와 공통 협업 안내

## 개발 순서

1. MVP·기술 구조·API 계약을 팀에서 검토합니다.
2. 화면 설계, 테스트 기준, 담당 작업과 일정을 정합니다.
3. URL 입력부터 실제 분석 결과 표시까지 먼저 연결합니다.
4. 문자·QR 검사, DB 기반 교육·퀴즈로 확장합니다.
5. 배포 환경에서 통합 테스트와 탐지 성능 평가를 진행합니다.
6. 시연 영상과 최종 발표 자료를 준비합니다.

주차별 일정과 마감일은 팀 합의 후 Docs 저장소에서 관리합니다.

## 설계 문서

- [01 · 기능 명세서](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/01_Feature_Specification.md)
- [02 · 사용자 흐름](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/02_User_Flow.md)
- [03 · 시스템 아키텍처](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/03_System_Architecture.md)
- [04 · DB 설계서](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/04_Database_Design.md)
- [05 · API 명세서](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/05_API_Specification.md)
- [06 · UI 설계서](https://github.com/KNUT-Capstone-Design/KNUT-Capstone-Design-docs/blob/main/docs/06_UI_Design.md)

기능 범위와 계약의 상세 기준은 설계 문서를 따릅니다. 팀 작업 방식은 [협업 가이드](https://github.com/KNUT-Capstone-Design/.github/blob/main/CONTRIBUTING.md)를 참고합니다.
