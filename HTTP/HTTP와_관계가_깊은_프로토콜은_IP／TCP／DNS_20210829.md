[목록](https://github.com/JungInBaek/TIL/blob/main/README.md)

# 1-4. HTTP와 관계가 깊은 프로토콜은 IP/TCP/DNS

## 1-4-1. 배송을 담당하는 IP
IP(Internet Protocol)는 네트워크 계층에 해당된다. IP의 역할은 개개의 패킷을 상대방에게 전달하는 것이다. 상대방에게 전달하기까지 여러 가지 요소가 필요하다. 그 중에서도 IP 주소와 MAC 주소(Media Access Control Address)라는 요소가 중요하다.

IP 주소는 각 노드에 부여된 주소를 가리키고 MAC 주소는 각 네트워크 카드에 할당된 고유의 주소이다. IP 주소는 MAC 주소와 결부된다. IP 주소는 변경 가능하지만 기본적으로 MAC 주소는 변경할 수 없다.

### 통신은 ARP를 이용하여 MAC 주소에서 한다.
IP 통신은 MAC 주소에 의존해서 통신을 한다. 통신 상대가 같은 랜선 내에 있을 경우는 적어 여러 대의 컴퓨터와 네트워크 기기를 중계해서 상대방에게 도착한다. 그렇게 중계하는 동안 다음으로 중계할 곳의 MAC 주소를 사용하여 목적지를 찾아가는 것이다. 이 때, ARP(Address Resolution Protocol)이라는 프로토콜이 사용된다.

## 1-4-2. 신뢰성을 담당하는 TCP
TCP(Transfer Control Protocol)는 트랜스포트 계층에 해당하는데, 신뢰성 있는 바이트 스트림 서비스를 제공한다. 바이트 스트림 서비스란 용량이 큰 데이터를 보내기 쉽게 TCP 세그먼트라고 불리는 단위 패킷으로 작게 분해하여 관리하는 것을 말하고, 신뢰성 있는 서비스는 상대방에게 보내는 서비스를 의미한다. 결국 TCP는 대용량의 데이터를 보내기 쉽게 작게 분해하여 상대에게 보내고, 정확하게 도착했는지 확인하는 역할을 담당하고 있다.

### 상대에게 데이터를 확실하게 보내는 것이 일이다
상대에게 확실하게 데이터를 보내기 위해서 TCP는 "쓰리웨이 핸드셰이킹(three way handshaking)"이라는 방법을 사용하고 있다.

송신 측에서는 최초 'SYN' 플래그로 상대에게 접속함과 동시에 패킷을 보내고, 수신 측에서는 'SYN/ACK' 플래그로 송신 측에 접속함과 동시에 패킷을 수신한 사실을 전한다. 마지막으로 송신측이 'ACK' 플래그를 보내 패킷 교환이 완료되었음을 전한다. 이 과정에서 통신이 도중에 끊기면 TCP는 그와 동시에 같은 수순으로 패킷을 재전송한다.