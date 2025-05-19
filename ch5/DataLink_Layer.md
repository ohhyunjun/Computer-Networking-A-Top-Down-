1. 네트워크계층
  = 인접한 두 노드사이의 데이터 그램을 전송하는 역할을 한다. 단위는 frame이다.
  = 링크계층의 서비스 종류: 
    - Flow Control = 인접한 송신 노드와 수신 노드간의 간격 조정(송신측이 대역폭 조절).
    - Error Dectection = 에러는 신호감쇠 혹은 노이즈등으로 생기며, 수신측은 오류의 존재를 감지한다(CRC...). 
    - Error Correction = 수신측이 재전송 요청없이 비트 오류를 식별 및 수정한다.(여기선 배우지 않음.)
    - Half-duplex and full-duplex = Half의 경우는 링크 양쪽의 끝의 노드가 저송 할 수 있지만 동시에 전송은 불가. full은 가능.

2. EDC(Error Detection and Correction bits) = 주로 데이터 비트 뒤에 EDC가 추가되어 보내진다.
   - Parity Checking = 1을 기준으로 데이터에 1의 양이 짝수라면 데이터 비트 뒤에 0을 붙이고  
