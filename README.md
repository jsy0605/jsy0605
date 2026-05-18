<div align="center">

## 제약된 환경에서 직접 문제를 찾고,<br/>하드웨어부터 알고리즘까지 스스로 해결하는 엔지니어 정성윤입니다.

### 정성윤 | Sungyoon Jeong

<br/>

**“ 펌웨어 설계부터 비전 알고리즘, 엔드투엔드(End-to-End) 통합 시스템 아키텍처까지 —<br/>디바이스와 소프트웨어가 유기적으로 연결되는 전 구간의 파이프라인을 독립적으로 구축합니다. ”**

<br/>

<img src="https://img.shields.io/badge/Embedded_SW-00599C?style=flat-square"/>&nbsp;
<img src="https://img.shields.io/badge/Robotics-0A0A0A?style=flat-square"/>&nbsp;
<img src="https://img.shields.io/badge/IoT-02569B?style=flat-square"/>&nbsp;
<img src="https://img.shields.io/badge/Edge_Vision-3776AB?style=flat-square"/>&nbsp;
<img src="https://img.shields.io/badge/Mobile_App-0175C2?style=flat-square"/>

</div>

---

## 🛠 Featured Projects

### AprilTag-FastSAM Hybrid Framework
> 연산 자원이 제한된 엣지 환경에서 고성능 제로샷 분할 모델을 실시간으로 운용하기 위한 연산 최적화 연구

- **주요 구현**: AprilTag의 포즈 추정 좌표를 FastSAM의 포인트 프롬프트로 실시간 자동 변환하는 파이프라인 설계
- **트러블슈팅**: 매 프레임 AI 추론으로 인한 병목을 해결하기 위해 초기 분할 후 **KCF Tracker**를 결합하는 하이브리드 구조 설계. 신뢰도 기반 조건부 재탐지 알고리즘으로 객체 드리프트 방지.
- **Environment**: Python, PyTorch, FastSAM, AprilTag, KCF Tracker, NVIDIA Jetson Orin Nano, JetPack 6.0
- **📈 Results**: FastSAM 단독 구동 대비 **처리 속도 45% 향상 (7.74 FPS 확보) · GPU 점유율 18% 절감**

### 실험 자동화 다관절 로봇 시스템
> 바이오 실험 자동화를 위한 UR 로봇 비전 정렬 및 피펫팅 제어 시스템 위탁 개발

- **주요 구현**: 마커 인식부터 데이터 가공, 최종 분주 제어 패킷 설계까지의 전 과정을 단독으로 설계 및 통합
- **트러블슈팅**: 카메라 좌표계와 엔드이펙터 물리 좌표계 간 **Hand-Eye 캘리브레이션**을 통해 마이크로 플레이트 well 정렬 오차 최소화. 딥러닝 OCR 기반으로 아날로그 피펫 용량을 판독하여 목표치에 맞추는 피드백 제어 알고리즘 구현.
- **Environment**: Python 3.12, UR Robot, VmbPy (Vimba SDK), AprilTag, OCR, Alvium 1800 U-511c
- **📈 Results**: 마커 인식부터 분주 패킷 설계까지 전 과정 단독 구현 완료 (위탁 기관 최종 보고서 제출)

### 네트워크 장애 대응형 ESP32 데이터로거
> 불안정한 네트워크 환경에서도 데이터 연속성을 보장하는 사물함 로드셀 라이프로그 수집 시스템

- **주요 구현**: 통신 단절 시 데이터 누락을 원천 차단하는 **Store-and-Forward 아키텍처** 설계
- **트러블슈팅**: `httpResponseCode`를 실시간 모니터링하여 장애 발생 시 데이터를 JSON 형태로 로컬 MicroSD 카드에 자동 버퍼링. 서버 복구 감지 시 통신 오버헤드를 줄이기 위해 **50개 단위 Batch POST** 방식으로 순차적 복구 전송 구현. ESP32 구동 안정성을 위해 부트 스트래핑 핀(GPIO 2번) 간섭을 원천 배제하는 하드웨어 설계 적용.
- **Environment**: C++, ESP32, HX711, MicroSD, REST API, NTP, Arduino IDE
- **📈 Results**: 인위적인 통신 단절 및 전원 차단 반복 테스트 환경에서 **데이터 유실률 0% 달성**

### Smart Doorbell Platform
> PIR 동작 감지, 실시간 영상/음성 스트리밍 및 원격 도어락 제어를 통합한 멀티 프로세스 IoT 보안 플랫폼 (팀장)

- **주요 구현**: 병렬 처리를 극대화하여 실시간성을 확보하는 **Multi-Process 아키텍처(C + Python Flask)** 설계 및 소켓 통신 기반 상태 동기화 구현
- **트러블슈팅**: 하드웨어 PWM 신호가 3.5mm 스피커 라인에 유발하는 화이트 노이즈를 핀 맵 변경 및 **SoftPWM** 방식으로 전환하여 제거. 카메라 모듈의 스트리밍(Picamera2)과 녹화(Libcamera-vid) 동시 점유 충돌을 **Mutex Lock** 메커니즘으로 제어.
- **Environment**: C, Python, Flask, Flutter / Dart, Raspberry Pi 4B, Firebase, Pthread, WiringPi
- **📈 Results**: SoftPWM 전환으로 오디오 노이즈 제거 완료 · 프로세스 간 Mutex 동기화 구조 완성

### Smart Fish Tank
> 센서 데이터 상시 수집 및 액추에이터 원격/자동 제어를 지원하는 자율 IoT 어항 관리 시스템

- **주요 구현**: 수온·탁도 실시간 모니터링 및 먹이 급여(서보모터), LED, 펌프 원격 제어 시스템 구축
- **기술적 포인트**: 카메라로 주기적으로 촬영된 이미지 데이터를 `glob`과 OpenCV 파이프라인을 통해 지능형 타임랩스 비디오 파일(`timelapse.mp4`, 2 FPS)로 변환하고 웹 스트림 형태로 자동 가공 제공
- **Environment**: Python, Flask, OpenCV, Raspberry Pi, Firebase Storage
- **📈 Results**: `cv2.VideoWriter` + `mp4v` 코덱 기반의 타임랩스 자동 생성 파이프라인 구축 및 자원 최적화

---

## 🔬 Research & Activities

**NCN LAB (차세대네트워크컴퓨팅 연구실)** **학부연구생 & 프로젝트 매니저(PM)** | *2024.03 – 2026.03 (24개월)*
- 산학 위탁 개발, 자율 로봇 시스템 R&D, IoT 플랫폼 구축 과제 총괄 주도
- 연구실 내 기술 문서화, 팀 일정 조율 및 최종 보고서 작성까지 PM 역할 병행
- **학술 성과**: 한국정보기술학회 종합학술대회 **3회 연속 동상 수상** 및 KCI 등재지 1건 포함 총 4건의 논문 게재

---
## 🌐 Other Projects
> 알고리즘 설계 및 데이터 시각화 관점으로 참여한 웹 플랫폼 프로젝트입니다. (학술대회 논문 게재 완료)

| 프로젝트 명 | 설명 | 사용 스택 | 성과 |
| :--- | :--- | :--- | :--- |
| **Eco Buddy** | 디지털 활동의 탄소 배출량을 실시간 정량화·시각화하는 트래킹 플랫폼 | React, JS, REST API, MIB / NetworkStats API | **2025 한국정보기술학회 하계 논문 게재** |
| **만남 배달부** | 콘텐츠 기반 + 협업 필터링 하이브리드 추천 알고리즘 기반 정서적 매칭 플랫폼 | React, JS, KoBERT, GPT API | **2025 한국정보기술학회 추계 논문 게재** |

---

## ⚙️ Tech Stack

### Languages
<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/C%20%2F%20C%2B%2B-00599C?style=flat-square&logo=c%2B%2B&logoColor=white"/>
  <img src="https://img.shields.io/badge/Dart-0175C2?style=flat-square&logo=dart&logoColor=white"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/>
</p>

### Embedded & Hardware
<p align="left">
  <img src="https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif&logoColor=white"/>
  <img src="https://img.shields.io/badge/Raspberry%20Pi-A22846?style=flat-square&logo=raspberrypi&logoColor=white"/>
  <img src="https://img.shields.io/badge/NVIDIA_Jetson_Orin_Nano-76B900?style=flat-square&logo=nvidia&logoColor=white"/>
  <img src="https://img.shields.io/badge/UR_Robot-0A0A0A?style=flat-square"/>
  <img src="https://img.shields.io/badge/Arduino-00979D?style=flat-square&logo=arduino&logoColor=white"/>
</p>

### Vision & AI
<p align="left">
  <img src="https://img.shields.io/badge/FastSAM-3776AB?style=flat-square"/>
  <img src="https://img.shields.io/badge/AprilTag-0A0A0A?style=flat-square"/>
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white"/>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/>
  <img src="https://img.shields.io/badge/KCF_Tracker-0A0A0A?style=flat-square"/>
  <img src="https://img.shields.io/badge/OCR-0A0A0A?style=flat-square"/>
</p>

### Frontend & App
<p align="left">
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white"/>
</p>

### Platform & Tools
<p align="left">
  <img src="https://img.shields.io/badge/Linux_/_Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black"/>
  <img src="https://img.shields.io/badge/REST_API-0A0A0A?style=flat-square"/>
  <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white"/>
</p>

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=[본인의깃허브ID]&show_icons=true&theme=gotham" alt="GitHub Stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=[본인의깃허브ID]&layout=compact&theme=gotham" alt="Top Languages" />
</p>

---
📧 **Contact** : jungsy0605@naver.com  
🔗 **Portfolio & Resume** : [여기에 포트폴리오 링크 입력]
