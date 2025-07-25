# 네트워크 보안

## 1. Network Security란?

네트워크 보안은 통신 당사자 간의 기밀성을 유지하는 것을 목표로 하며, 이를 위해 데이터를 암호화하고 복호화하여 해석할 수 있어야 합니다. 또한, 통신 상대방의 신원을 검증하기 위한 인증 과정이 필요합니다. 메시지가 전송 중 변조되지 않았음을 보장하는 무결성도 필수적이며, 이를 통해 데이터가 도중에 변경되거나 손상되지 않았음을 확인할 수 있습니다. 마지막으로, 허용된 사용자가 언제든 네트워크 자원에 접근할 수 있는 가용성 역시 중요한 요소입니다.

## 2. 방화벽 (Firewall)

방화벽은 네트워크 관리자가 네트워크에 대한 트래픽 출입을 관리함으로써 외부 세계와 관리 네트워크 내 자원 사이의 접근을 제어합니다.

- **방화벽 종류**: 전통적인 패킷 필터와 응용 게이트웨이 등이 있습니다.
- **구조**: 이중 네트워크 호스트 구조, 호스트 게이트웨이 구조, 스크린드 서브넷 구조 등이 있습니다.

## 3. 보안 키 종류

- **대칭 키 암호화 (Symmetric Key Cryptography)**: 동일한 키로 암호화와 복호화를 수행하는 방식으로, 대표적으로 DES 암호화가 있습니다.
- **공개 키 암호화 (Public Key Cryptography)**: 서로 다른 두 개의 키를 사용하는 방식으로, 암호화 시에는 공개 키(Public Key)를 사용하고 복호화 시에는 개인 키(Private Key)를 사용합니다. 대표적으로 RSA가 있습니다.
  - **RSA**: 두 개의 소수 p, q를 선택하고, N = p * q, Z = (p-1)(q-1)을 계산합니다. 1 < e < N이고 Z와 서로소인 e를 선택하며, (d * e) mod Z = 1을 만족하는 d를 구합니다. 이후 공개 키는 (N, e), 개인 키는 (N, d)로 설정됩니다. 암호화는 m^e mod N, 복호화는 c^d mod N으로 진행됩니다.

## 4. 각 계층별 보안 프로토콜

- **어플리케이션 계층**: PGP  
- **전송 계층**: SSL  
- **네트워크 계층**: IPsec  
- **데이터 링크 계층**: WEP
