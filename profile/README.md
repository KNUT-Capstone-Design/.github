# 스미싱 예방 교육 및 탐지 시스템

한국교통대학교 컴퓨터소프트웨어학과 캡스톤디자인 프로젝트입니다.  
스미싱 예방 교육과 의심 메시지·URL·QR 코드·이미지 판별 기능을 결합한 웹 기반 보안 서비스입니다.

## 팀원 소개

| 이름 | 역할 |
|---|---|
| 이영수 | 미정 |
| 민승호 | 미정 |
| 임찬우 | 미정 |
| 김흥원 | 미정 |

## 주요 기능

- 네이버, 구글, 쿠팡 사칭 가짜 로그인 페이지 판별
- 쿠팡·청첩장·택배 사칭 APK 설치 유도 메시지 탐지
- 대출, 공공기관 사칭, 주식 리딩, 단체예약·술 구매 유도 URL 위험도 분석
- QR 코드 속 URL 추출 및 위험도 검사
- 조작 사진 판별
- 스미싱 사례 기반 예방 교육 및 퀴즈

## 기술 스택

### Frontend

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

### Backend

![Next.js API Routes](https://img.shields.io/badge/Next.js_API_Routes-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white)

### DevOps & Collaboration

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

### AI / 분석 기능 (예정)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)

## 개발 목표

웹에서 의심 메시지, URL, QR 코드, 이미지를 간단히 검사하고 위험 요인과 예방법을 함께 제공하는 경량형 스미싱 예방 시스템을 구현합니다.

## 개발 일정 및 데드라인 계획

현재 5주차이며, 14주차까지 약 9주 동안 개발을 진행합니다.

| 기간 | 주요 작업 | 산출물 / 데드라인 |
|---|---|---|
| 5~6주차 | 아이디어 구체화, 요구사항 분석, 역할 분담 | 프로젝트 기획서, 기능 명세서 |
| 7주차 | 화면 설계 및 DB 설계, 기술 스택 선정 | 화면 흐름도, DB 설계서 |
| 8주차 | 웹 페이지 기본 구조 및 회원/메인 화면 구현 | 기본 웹 UI |
| 9주차 | URL·문자 메시지 경량 탐지 기능 구현 | URL/문자 위험도 분석 기능 |
| 10주차 | QR 코드 분석 및 APK 설치 유도 탐지 기능 구현 | QR URL 추출 및 탐지 기능 |
| 11주차 | 가짜 로그인 페이지·조작 이미지 판별 기능 구현 | 이미지/사칭 판별 기능 |
| 12주차 | 예방 교육 콘텐츠 및 퀴즈 기능 구현 | 교육 페이지, 퀴즈 기능 |
| 13주차 | 기능 통합, 테스트 및 오류 수정 | 통합 테스트 결과 |
| 14주차 | 최종 발표 자료, 시연 영상 및 결과 보고서 작성 | 최종 발표 및 프로젝트 제출 |

## 리스크 관리 계획

| 리스크 | 영향 | 대응 방안 |
|---|---|---|
| 역할 분담 지연 | 개발 일정이 늦어질 수 있음 | 6주차까지 담당 기능을 확정하고 진행 상황을 주 1회 공유 |
| 탐지 정확도 부족 | 잘못된 판별 결과가 나올 수 있음 | 초기에는 규칙 기반 경량 탐지를 적용하고, 결과를 ‘위험도’와 ‘참고용’으로 안내 |
| 학습 데이터 부족 | AI 기반 이미지·문자 판별 구현이 어려움 | 공개 데이터셋 및 직접 수집한 예시 데이터를 활용하고, 부족한 기능은 규칙 기반으로 대체 |
| 기능 범위 과다 | 모든 기능을 완성하지 못할 수 있음 | URL·문자 탐지를 핵심 기능으로 우선 구현하고, 이미지 판별은 보조 기능으로 개발 |
| 팀원 간 일정 조율 어려움 | 회의·개발 진행이 지연될 수 있음 | GitHub, Notion, 카카오톡 등을 활용해 작업 내용과 일정을 공유 |
| 보안 및 개인정보 문제 | 사용자 데이터 유출 가능성 | 실제 개인정보는 저장하지 않고, 업로드 파일과 검사 기록은 최소한으로 관리 |
| 배포 및 시연 환경 오류 | 발표 시 서비스가 실행되지 않을 수 있음 | 발표 전 로컬 환경과 배포 환경에서 모두 테스트하고, 시연 영상 또는 화면 녹화를 백업으로 준비 |