<div align="center">

# 안녕하세요, 채민주입니다 👋

**호기심으로 세상을 묻고, 기술로 답을 찾는 클라우드 엔지니어 지망생**

조선대학교 정보보안전공 (2027.02 졸업 예정)

<!-- 공개해도 괜찮다면 아래 줄의 주석을 풀어 주세요 -->
<!-- 📫 chaeminju78@gmail.com -->

</div>

잘 만든 AI 모델이 사람에게 빠르고 안전하게 닿도록, 그 아래의 인프라를 만드는 일을 하고 싶습니다.
모델 선정부터 엣지 기기(Jetson) 배포, AWS 3-Tier 설계, 자동 배포·롤백 파이프라인 운영까지 한 흐름으로 직접 다뤄 왔고,
정보보안 전공자로서 배포 과정까지 보안 점검 대상으로 봅니다.

<br>

## 🛠 Tech Stack

**자신 있는 기술**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_Streams-DC382D?style=flat-square&logo=redis&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**사용할 줄 아는 기술**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![llama.cpp](https://img.shields.io/badge/llama.cpp-000000?style=flat-square&logoColor=white)
![TensorRT](https://img.shields.io/badge/TensorRT-76B900?style=flat-square&logo=nvidia&logoColor=white)
![Jetson](https://img.shields.io/badge/NVIDIA_Jetson-76B900?style=flat-square&logo=nvidia&logoColor=white)
![Naver Cloud](https://img.shields.io/badge/Naver_Cloud_(NCA)-03C75A?style=flat-square&logo=naver&logoColor=white)
![GCP Vertex AI](https://img.shields.io/badge/GCP_Vertex_AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Gemini API](https://img.shields.io/badge/Gemini_API-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)

<br>

## 🚀 Projects

### 😂 LOLog: 웃긴 대화를 4컷만화와 쇼츠로 남기는 앱
`팀 3명` · `2026.11.02 ~ 2026.11.27` · [서비스 페이지](https://lolog.java21.net) · [LOLog-2026](https://github.com/LOLog-2026)

일상 대화를 녹음해 두면 AI가 기록할 만한 이야기를 찾아 카드로 모으고, 고른 카드를 4컷만화와 쇼츠 영상으로 만들어 주는 서비스입니다.
저는 **AI와 인프라**를 맡았습니다. Android APK v0.2.2까지 배포했습니다.

- **온프레미스 AI 파이프라인**: 대화를 외부 AI 서비스로 보내지 않도록 Jetson 3대에 LLM(llama.cpp + Qwen3.5-4B), 이미지 생성(FLUX.2 klein), TTS(Qwen3-TTS)를 나눠 올리고, 메인 서버의 Redis Streams 큐를 각 워커가 SSH 터널로 꺼내 처리하는 구조
- **배포와 운영**: 여러 학생이 함께 쓰는 학교 서버에서 포트 3개만 열고 내부 API(`/internal`)는 외부에서 차단, 로그인 요청 횟수 제한. main에 머지하면 테스트 → GHCR 이미지 → 서버 배포, 헬스체크에 실패하면 이전 버전으로 자동 롤백
- **실험으로 결정**: 립싱크를 16회 반복 개선해 처음 보는 카드의 적용률을 47~61%에서 96%로 올림 / 얼굴 조각 크기를 비교해 장당 42초 걸리던 그림 수정을 12초로 줄임 / 폰 음성 인식에 음량 보정을 넣어 빈 결과 9개 → 0개

<br>

### 🏠 한채: 한옥 마을 콘셉트 블로그 서비스
`개인` · `2026.10.01 ~ 2026.10.22` · [서비스 페이지](https://hanchae.java21.net) · [blog-code](https://github.com/blog-minju-2026/blog-code)

각자의 블로그를 '한 채의 집'처럼 짓고 기록을 쌓으며 이웃집을 방문하는 블로그 서비스입니다.
기획, 명세, DB 설계, 백엔드, 화면, 배포까지 혼자 맡아 3주 만에 완성하고 학교 서버에서 v1.11.0까지 운영했습니다.

- **명세 우선 개발**: AI 코딩 도구의 구현 범위를 통제하려고 GitHub Spec Kit으로 명세를 작업 235개로 나누고, 테스트 파일 19개로 작업마다 검증
- **자동 배포**: Docker와 GitHub Actions로 머지하면 서버에 자동 배포되는 파이프라인, Nginx 설정, 매일 도는 정리 작업 자동화 구성
- **보안 점검**: 공개된 GitHub Actions 로그에 개인정보가 찍히는 문제를 찾아 수정하고, 이후 배포 파이프라인도 점검 대상에 포함
- 커밋 78개, PR 22개

<br>

### 🚗 Paragon: 차량 공기저항 계수 예측 서비스 (UC San Diego Qualcomm Institute)
`팀 5명` · `2026.06.28 ~ 2026.07.26` · `미국` · [Qulcomm_Institute_team_a](https://github.com/parag0hz/Qulcomm_Institute_team_a) · [Live demo](https://qulcomm-institute-team-a.onrender.com/)

차량 3D 포인트 클라우드만으로 공기저항 계수(Cd)를 몇 초 만에 예측하고, 그 결과를 LLM이 쉬운 말로 설명해 주는 웹 서비스입니다.
며칠에서 몇 주가 걸리는 CFD 시뮬레이션 전에 후보 디자인을 빠르게 걸러 내는 용도입니다.
여러 대학 학생 5명이 모인 팀에서 저는 **기획, 발표, 인프라**를 맡았습니다.

- **수상**: 프로그램 내 팀 해커톤 ML Empowerment Build Challenge 2.0 **3위**, 프로그램 **Achievement Award**
- **프로토타입**: 팀 개발 초기에 PRD의 데이터 분포를 재현한 합성 데이터로 FastAPI + React(three.js) 데모를 먼저 만들어 Render에 배포하고, 화면 흐름을 팀과 맞춤 ([QI_practice](https://github.com/chaeminju/QI_practice))
- **팀 결과**: DrivAerNet++(CFD로 계산한 세단 7,713대)로 학습한 PointNet이 설계 파라미터 기반 모델보다 정확

  | 모델 | 입력 | R² | 순위 맞힘 |
  |---|---|---|---|
  | **PointNet** | 3D 포인트 2,048개 | **0.878** | **89.1%** |
  | LightGBM | 설계 파라미터 23개 | 0.557 | 78.0% |

- **영어 발표**: 미국 현지 멘토와 영어로 피드백을 주고받으며 아이디어를 다듬고, 최종 발표를 영어로 맡아 기술을 사업 관점에서 설명

<br>

### 👵 낙상 감지 및 알림 서비스 (산학프로젝트 "잘 지켜봐조")
`팀 5명` · `2026.03.02 ~ 2026.06.19` · [26-1IAP](https://github.com/HYoMo-nim/26-1IAP)

혼자 사는 어르신의 낙상 같은 이상행동을 가정용 카메라로 감지해 알려 주는 서비스입니다.
저는 **자세 추정 모델 비교·선정과 엣지 기기 배포**를 맡았습니다.

- **모델 선정**: 정확도 하나가 아니라 정확도, 실제 기기 속도, 변환 가능성 세 가지 기준으로 MoveNet, YOLOv8 계열, YOLO26n-pose 비교
- **결과**: YOLO26n-pose를 TensorRT로 변환해 기존 후보(YOLOv8n-pose) 대비 성능 향상

  | 모델 (TensorRT) | mAP | FPS (Jetson Nano) |
  |---|---|---|
  | YOLOv8n-pose | 0.381 | 154 |
  | **YOLO26n-pose** | **0.460** | **191** |

- **엣지-클라우드 구조**: 원본 영상 대신 관절 좌표만 30프레임 단위로 AWS EC2에 HTTPS 전송(X-API-Key 인증)해 개인정보와 전송량을 함께 절감
- 3D 변환 모델은 VideoPose3D와 PoseFormerV2를 비교해 VideoPose3D 선택

<br>

### 🛡 SafeScan: 악성 문서 탐지 웹 서비스 (오픈소스SW 프로젝트)
`팀 4명` · `2025.09.01 ~ 2025.12.12` · [Virus_Detector](https://github.com/kkicktthebbal/Virus_Detector)

문서로 위장한 악성파일을 업로드하면 매크로, PDF 스크립트, 실행 파일 패킹 여부 등을 분석하고, 그 결과를 Gemini가 쉬운 말로 설명해 주는 서비스입니다.
저는 **클라우드 아키텍트**로 AWS 배포 아키텍처를 설계하고 구축했습니다.

- **3-Tier 설계**: CloudFront + S3(화면), External/Internal ALB + Auto Scaling(서버), RDS(DB). 악성 의심 파일을 다루는 서비스라 WAS와 DB는 외부에서 직접 닿지 않도록 Internal ALB 뒤에 배치
- **트러블슈팅**: Internal ALB unhealthy 문제를 요청 경로(보안 그룹 → 리스너 → 대상 그룹 → 서버) 순서로 추적해 포트 불일치와 WAS 미배포 두 원인 해결
- **인계 문서**: 팀원 누구나 인프라를 이어받을 수 있도록 구성과 운영 방법을 문서로 정리

<!-- 아키텍처 그림(virus-detector-architecture.png)을 이 저장소에 올리고 아래 주석을 풀면 그림이 보여요 -->
<!-- <img src="./assets/safescan-architecture.png" width="700"> -->

<br>

## 📚 Research

**Mean-Teacher 기반 한국어 AI 생성 글 탐지** · 제19회 융합·스마트미디어시스템(CSMS) 워크샵, 2025 (공동저자)
- KoELECTRA와 Mean-Teacher 준지도학습으로, 정답 라벨이 충분하지 않은 한국어 데이터에서도 LLM이 쓴 글을 더 잘 가려내는 방법 제안
- 모델 구현, 실험, 결과 분석 담당 / 단독 모델 대비 F1, ROC-AUC 향상

<br>

## 🏆 Awards & Certificates

| 연도 | 내용 |
|---|---|
| 2026 | Qualcomm Institute AI Entrepreneurship Program **ML Empowerment Build Challenge 2.0 3위, Achievement Award** |
| 2025 | 호남권 LLM 해커톤 **우수상** (HyperCLOVA X 대화형 챗봇, NCP 환경 구성) |
| 2025 | SW중심대학 오픈소스 아이디어 경진대회 **동상** (팀장/PM) |
| - | **NCA** (Naver Cloud Platform Certified Associate) |

<br>

## 🎓 Education & Activities

- **AI부트캠프사업단 AI응용프로젝트 과정** (조선대학교, 2026.10.01 ~ 2026.11.30)
  명세 우선 개발 방식(GitHub Spec Kit)으로 '한채'를 단독 기획·개발·배포
- **Qualcomm Institute AI Entrepreneurship Program** (UC San Diego, 미국, 2026.06.28 ~ 2026.07.26)
  GCP·Vertex AI 기반 ML과 MLOps 수강, 5인 팀에서 기획·발표·인프라 담당, 최종 발표 영어로 진행
- **SW멤버십 AWS 클라우드 멘토링** (조선대학교 SW중심대학사업단 × 으뜸정보기술, 2025.08.18 ~ 2025.09.12)
  S3 정적 호스팅 → EC2+RDS 2-Tier → Multi-AZ 3-Tier → ALB·Auto Scaling → Docker 배포까지 단계별 구축,
  Auto Scaling 인스턴스 무한 생성 문제를 상태 검사 실패와 최대 인스턴스 수 미설정 두 원인으로 찾아 해결
