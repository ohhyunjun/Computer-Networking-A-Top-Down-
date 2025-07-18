# 데이터 링크 계층 (Data Link Layer)

데이터 링크 계층은 네트워크에서 중요한 역할을 담당하며, 노드와 이웃 노드 간의 데이터 전송을 관리합니다.

## 주요 정의 및 역할
- **정의**: 노드와 이웃 노드 사이의 경로를 관리하며, 데이터 단위는 **프레임(frame)**입니다.
- **주요 역할**:
  - 송수신 역할 수행
  - **흐름 제어 (Flow Control)**: 송신과 수신 속도를 조절
  - **신뢰성 전송**: 데이터가 손실 없이 전달되도록 보장
  - **오류 검출 (Error Detection)**: 전송 중 발생한 오류 감지
  - **오류 정정 (Error Correction)**: 오류 수정

## 세부 기능
### 1. 흐름 제어 (Flow Control)
- **설명**: 인접한 두 노드 간에 적용되며, 송신 측이 과도한 데이터를 전송하지 않도록 조절합니다.
- **동작 방식**: 수신 측 버퍼가 가득 차면 송신 측에 신호를 보내 속도를 줄이도록 합니다.

### 2. 오류 검출 및 정정
- **오류 검출**: 신호 감쇠나 잡음으로 발생한 오류를 수신 측에서 확인합니다.
  - 대표적인 방법: **CRC (Cyclic Redundancy Check)**
- **오류 정정**: 검출된 오류를 수정합니다.
  - 예: 해밍 코드(Hamming Code)

### 3. 듀플렉스 모드 (Duplex Modes)
- **Half-duplex (반이중)**: 링크 양 끝이 데이터를 전송할 수 있지만, 동시에 전송은 불가능합니다.
- **Full-duplex (전이중)**: 링크 양 끝이 동시에 데이터를 전송할 수 있습니다.

---

# EDC (Error Detection and Correction Bits)

EDC는 데이터 전송의 신뢰성을 높이기 위해 사용되는 비트입니다.

## 정의
- **EDC란?**: 오류 감지 및 수정 비트를 의미하며, 데이터(D)에 추가되어 전송됩니다.
- **특징**: 100% 신뢰성을 보장하지는 않습니다.

## 오류 검출 및 정정 방법
### 1. Single Bit Parity
- **설명**: 데이터 전송 중 오류를 확인하기 위해 추가된 비트입니다.
- **작동 방식**:
  - 1의 개수가 짝수(짝수 패리티) 또는 홀수(홀수 패리티)가 되도록 설정.
  - **예시**: 데이터 `0111000110101011`에 패리티 비트 `0` 추가 시 1의 개수는 9(홀수). 수신 측에서 확인 후 오류 여부 판단.

### 2. Two-Dimensional Bit Parity
- **설명**: 데이터를 2차원 격자 형태로 구성하고, 행과 열에 패리티 비트를 추가해 검출 능력을 강화합니다.

### 3. Checksum
- **설명**: 데이터를 합산해 체크섬 값을 생성하고, 수신 측에서 동일한 계산으로 오류를 확인합니다.

### 4. CRC (Cyclic Redundancy Check)
- **설명**: 데이터를 다항식으로 간주하고, 생성 다항식으로 나눈 나머지를 체크값으로 사용합니다.
- **동작 방식**:
  - 송신 측: 데이터에 CRC 값을 붙여 **코드워드** 전송.
  - 수신 측: 동일한 다항식으로 나누어 나머지가 0이면 오류 없음, 0이 아니면 오류 발생.
- **참고**: ![Image](https://github.com/user-attachments/assets/d49c97fc-e33f-4edb-815c-d06f1a602cdc)
![Image](https://github.com/user-attachments/assets/33bf17e6-5236-46e8-8919-d3dfc3b59628)
![Image](https://github.com/user-attachments/assets/f6af69a2-7fbe-402c-b63d-2a1811e4a7eb)
---

# 다중 접속 프로토콜 (Multiple Access Protocols)

다중 접속 프로토콜은 여러 호스트가 제한된 채널을 공유하도록 관리합니다.

## MAC 프로토콜 개요
- **정의**: 공평한 채널 공유를 보장하는 프로토콜.
- **주요 유형**:
  1. **Channel Partitioning (채널 분할)**: 시간, 주파수, 코드 단위로 채널을 나눔.
  2. **Random Access (랜덤 액세스)**: 충돌을 허용하고 복구 메커니즘 사용.
  3. **Taking Turns (턴 기반)**: 토큰이나 폴링으로 충돌 방지.

## 구체적인 프로토콜
### 1. FDMA (Frequency Division Multiple Access)
- **설명**: 주파수 대역을 여러 채널로 나누어 노드에 할당 (1세대 기술).
- **관련 개념**:
  - **FDD (Frequency Division Duplex)**: 주파수를 업링크와 다운링크로 분리.
  - **TDD (Time Division Duplex)**: 시간을 나눠 업링크와 다운링크로 사용.
- **참고**:![Image](https://github.com/user-attachments/assets/4dd2921a-1fbb-4f2b-9e42-6bb64d8c9496)

### 2. TDMA (Time Division Multiple Access)
- **설명**: 시간을 프레임 단위로 나누고, 시간 슬롯을 노드에 할당 (2세대 기술).
- **참고**:![Image](https://github.com/user-attachments/assets/2d027d8e-dcff-4bd7-863b-b5efd8b8c970)

### 3. CDMA (Code Division Multiple Access)
- **설명**: 고유한 칩 시퀀스를 사용해 신호를 인코딩 (3세대 기술).
- **동작 방식**:
  - **인코딩**: 원본 데이터 × 칩 시퀀스.
  - **디코딩**: 수신 신호와 칩 시퀀스의 내적 계산으로 데이터 복원.
- **특징**: 여러 노드가 동시에 전송해도 간섭 최소화.
- **참고**: ![Image](https://github.com/user-attachments/assets/49903a1c-5ac3-4cf4-ad0d-a05f348cebad)
  ![Image](https://github.com/user-attachments/assets/814cdfde-5ae2-409b-aeda-2fafb2c8e029)

### 4. Random Access Protocols
- **설명**: 노드가 전체 채널 속도(R)로 전송하며, 충돌 가능성이 있음.
- **세부 프로토콜**:
  - **Slotted ALOHA**:
    - 시간을 슬롯으로 나누고, 슬롯 시작 시 전송.
    - 충돌 시 확률 \(p\)로 재전송.
    - **효율**: 최대 37%.
    - **참고**: ![Image](https://github.com/user-attachments/assets/6e7eed36-1938-4882-a838-8755b1efc8c4)
  - **Pure ALOHA**:
    - 시간 제약 없이 전송, 충돌 확률 높음.
    - **참고**: ![Image](https://github.com/user-attachments/assets/158615c3-d7d4-4898-8210-d4089b842abc)
  - **CSMA (Carrier Sense Multiple Access)**:
    - 전송 전 채널 확인 후 유휴 시 전송.
    - **CSMA/CD (Collision Detection)**: 유선랜에서 사용되며, 회선상태가 비어있는 상태로 감지되면 즉각 데이터를 전송한다. 충돌이 발생할 경우 네티워크 상의 다른 컴퓨터에게 이 사실을 알리고 충돌 발생 사실을 전달 받은 컴퓨터들은 임의의 시간동안 대기를 한 후 다시 재전송을 시도한다.
      - ex) CSMA/CD에서 5번의 충돌 후에 노드가 K=4를 선택할 확률은?, K=4는 10Mbps 이더넷에서 몇 초의 지연시간에 해당하는가?
        -: 5번의 충돌 -> 2^5=32(0~31까지) 즉 확률은 1/32, 지연시간의 경우 4*512*0.1*10^-6(bit time)/10*10^6(bps)
    - **CSMA/CA (Collision Avoidance)**: 무선에서 사용하는 방식으로 회피하기 어렵기 때문에 충돌이 일어나지 않게 해당되지 않는 노드들은 기다리는 방식이다. 송신측이 RTS로 핼로페킷을 보내면 수신자가 CTS로 응답페킷을 보낸다. 그 사이 다른 노드들이 수신을 방해하지 않도록 대기하여 기다린다.
---

# 추가 정보

## 주요 개념
- **MAC 주소**: 48비트 고유 식별자 (LAN/물리 주소).
- **ARP (Address Resolution Protocol)**: IP 주소를 MAC 주소로 매핑.
- **RARP (Reverse Address Resolution Protocol)**: MAC 주소를 IP 주소로 매핑.
- **비컨 프레임 (Beacon Frame)**: 무선 네트워크 동기화 및 존재 알림.

---
