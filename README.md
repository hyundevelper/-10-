# Firebase 프로젝트

# Firebase

>> Firebase의 주요 기능
1. Authentication (인증)
    * 이메일/비밀번호, 구글, 페이스북, 애플 등 다양한 방식의 사용자 인증을 지원.
2. Cloud Firestore / Realtime Database
    * 실시간 데이터 동기화가 가능한 NoSQL 데이터베이스.
    * 클라우드 기반으로 확장성과 반응성이 뛰어남.
3. Cloud Functions
    * 서버 없이 백엔드 로직을 작성할 수 있는 FaaS(Function as a Service).
    * 예: 사용자 등록 시 이메일 자동 전송.
4. Cloud Storage
    * 이미지, 동영상 등 대용량 파일 저장용 스토리지 제공.
5. Hosting
    * 정적 웹사이트를 빠르게 배포할 수 있는 호스팅 서비스.
6. Analytics
    * Firebase와 Google Analytics를 연동해 사용자 행동 데이터 수집 가능.
7. Crashlytics
    * 앱의 충돌(Crash)을 추적하고 문제를 실시간으로 파악 가능.
8. Push Notification (Cloud Messaging)
    * 사용자에게 알림을 전송할 수 있는 기능.

✅ Firebase의 장점
* 서버 관리 불필요 (서버리스)
* 확장성 우수
* 빠른 개발 및 배포 가능
* Google 생태계와의 연동 용이

🔍 사용 예시
* 실시간 채팅 앱
* 사용자 인증이 필요한 앱
* 빠르게 MVP를 만들고 싶은 스타트업


# NTP (Network Time Protocol)

>> NTP의 핵심 개념
* 목적: 인터넷이나 로컬 네트워크를 통해 클라이언트 장치가 정확한 표준 시간(UTC 등) 을 신뢰할 수 있는 타임 서버로부터 받아서 시스템 시간을 맞춤.
* 표준 프로토콜: NTP는 UDP 포트 123을 사용하며, Stratum 계층 구조로 시간 소스를 계층화함.

>> NTP 구조: Stratum 계층
* Stratum 0: 원자시계, GPS 시계 등 실제 정확한 시간 소스 (직접 연결 불가).
* Stratum 1: Stratum 0에 직접 연결된 서버. 가장 정확한 NTP 서버.
* Stratum 2: Stratum 1에서 시간 데이터를 받아 클라이언트에게 제공.
* ...
* Stratum 15: 네트워크에서 최하위 레벨의 시간 정확도.

>> 동작 방식
1. 클라이언트가 NTP 서버에 시간 요청.
2. 서버는 요청 시점의 타임스탬프와 함께 응답.
3. 클라이언트는 왕복 시간(RTT)을 고려해 시간 오차를 계산하고, 자체 시계를 조정.

✅ NTP의 특징
* 정확도: 공용 인터넷에서는 수 밀리초(millisecond), LAN에서는 수 마이크로초(microsecond) 단위의 정확도.
* 자동 조정: 서서히 시간 보정 (갑자기 시간을 바꾸지 않음).
* 보안: NTPv4에서는 인증 기능 지원 (하지만 기본적으로는 보안에 취약할 수 있음).

📌 사용 예
* 서버 클러스터의 로그 시간 일치
* 금융 시스템의 정확한 타임스탬핑
* IoT 기기의 동기화
* CCTV, 보안 시스템의 시간 정렬


#  IoT 프로젝트

>> 실습 목표
* ESP32에서 센서 데이터 읽기 (ex: 온도/습도)
* Firebase Realtime Database에 데이터 업로드
* Firebase에서 실시간으로 데이터 확인

>> 준비물
항목	설명
ESP32	Wi-Fi 기능이 있는 마이크로컨트롤러
DHT11/DHT22	온도/습도 센서 (옵션)
Jumper Wires	배선용 점퍼선
Firebase 계정	https://firebase.google.com
Arduino IDE	ESP32 보드 설정 및 코드 업로드용
Firebase Arduino 라이브러리	Firebase_ESP_Client 추천

🛠️ 단계별 실습
1. Firebase 프로젝트 생성
1. Firebase 콘솔에 접속해 새 프로젝트 생성
2. Realtime Database 활성화 (테스트 모드 OK)
3. Database URL 확인 (예: https://your-project.firebaseio.com)
4. 서비스 계정 > Database Secrets 또는 Web API 키 확보

2. Arduino IDE 설정
1. ESP32 보드 매니저 URL 추가 
2. ESP32 보드 설치: Tools > Board > ESP32 Dev Module 선택
3. Firebase 라이브러리 설치: 라이브러리 매니저에서 Firebase ESP Client 설치

3. 회로 연결 (옵션: DHT 센서 사용 시)
* VCC → 3.3V
* GND → GND
* DATA → D5 (또는 원하는 핀)

