# Computer Network

- 컴퓨터 네트워크는 여러 컴퓨터와 장치들을 서로 연결하여 데이터를 주고받는 기술을 의미합니다.
  - 이를 통해 인터넷, 로컬 네트워크, 클라우드 서비스 등이 가능해집니다.
  - 네트워크를 구성하는 장치에는 컴퓨터, 노트북, 스마트폰, 라우터, 스위치, 서버 등이 포함됩니다.

# 현대 컴퓨터 네트워크에서 데이터 전달 방법

- 현대 컴퓨터 네트워크에서 데이터는 패킷(Packet)이라고 불리는 작은 조각으로 나누어져 전송됩니다.
  - 데이터를 전송할 때 송신자는 데이터를 패킷으로 나누고, 각 패킷은 목적지 주소, 송신자 주소, 오류 검출 정보 등을 포함하여 전송됩니다.
    - 이러한 패킷들은 네트워크 장치들(라우터, 스위치 등)을 거쳐 목적지로 전달되며, 목적지에서 다시 원래의 데이터로 복원됩니다.

# 라우터와 스위치

### 라우터(Router)

- 여러 개의 네트워크를 연결하여 데이터를 전달하는 장치입니다.
- 각 네트워크는 서로 다른 IP 주소 대역을 가지고 있는 경우가 많기 때문에 라우터는 패킷이 목적지로 가는 경로를 결정하여 데이터를 전송합니다.
- 라우터는 인터넷과 같이 여러 네트워크를 연결하는데 주로 사용됩니다.

### 스위치(Switch)

- 스위치는 컴퓨터들이 연결되어 있는 로컬 네트워크에서 데이터를 전달하는 장치입니다.
- 스위치는 패킷의 목적지 주소를 보고 해당 패킷을 정확한 포트로 전송함으로써 효율적으로 데이터를 전달합니다.

# 프로토콜과 프로토콜 스택

### 프로토콜(Protocol)

- 프로토콜은 네트워크 장치들 간에 데이터를 주고받는 데 사용되는 규칙과 규약을 정의한 것입니다.
- 프로토콜을 데이터 전송 방식, 오류 처리, 보안 등 다양한 기능을 정의하여 데이터의 신뢰성과 안정성을 보장합니다.

### 프로토콜 스택(Protocol Stack)

- 프로토콜 스택은 네트워크 계층을 계층적으로 구조화하여 프로토콜들이 상호작용하도록 합니다.
- 일반적으로 OSI 7 Layer 또는 TCP/IP 모델과 같이 계층 구조를 사용합니다. 각 계층은 하위 계층과 상위 계층과의 인터페이스를 통해 데이터를 주고받으며, 이를 통해 복잡한 네트워크를 보다 쉽게 관리할 수 있습니다.

# OSI 7 Layer

- OSI 7 Layer는 컴퓨터 네트워크에서 데이터를 전송하는 데 사용되는 프로토콜들을 7개의 계층으로 분리하여 정의한 모델입니다.
- 각 계층은 다른 계층들과만 상호작용하며, 상위 계층은 하위 계층의 서비스를 이용합니다.
  - 물리 계층(Physical Layer): 데이터 전송을 위한 하드웨어적인 인터페이스를 제공합니다.
  - 데이터 링크 계층(Data Link Layer): 물리적인 주소를 사용하여 네트워크 장치들이 통신할 수 있도록 합니다.
  - 네트워크 계층(Network Layer): IP 주소를 사용하여 다른 네트워크로 데이터를 전송합니다.
  - 전송 계층(Transport Layer): 데이터를 신뢰성 있게 전송하고 오류를 처리합니다.
  - 세션 계층(Session Layer): 데이터 통신을 위한 세션을 설정, 유지, 종료합니다.
  - 표현 계층(Presentation Layer): 데이터를 표현하고 암호화, 복호화를 처리합니다.
  - 응용 계층(Application Layer): 사용자와 네트워크 간의 인터페이스를 제공하며, 최종 사용자에게 서비스를 제공합니다.

# TCP/IP

- TCP/IP는 현대 인터넷에서 가장 널리 사용되는 프로토콜 스택입니다.
- 4개의 계층으로 구성되어 있습니다.

  - 네트워크 액세스 계층 (Network Access Layer):
    네트워크 액세스 계층은 물리적인 연결을 다룹니다. 이 계층에서는 데이터를 전기 신호로 변환하여 네트워크 매체(유선 또는 무선)를 통해 전송합니다. 이더넷, Wi-Fi, PPP(Poin-to-Point Protocol) 등과 같은 프로토콜이 이 계층에서 사용됩니다. 네트워크 액세스 계층은 물리적인 주소로서 MAC(Media Access Control) 주소를 사용하여 장치들을 구분합니다.
  - 인터넷 계층 (Internet Layer):
    인터넷 계층은 IP(Internet Protocol) 주소를 사용하여 데이터를 전송하고 라우팅을 수행합니다. IP 주소는 각 장치에 할당되어 네트워크 상에서 고유한 주소를 가집니다. 이 계층에서는 데이터를 패킷(Packet) 형태로 분할하고, 각 패킷에 출발지와 목적지 IP 주소를 부여하여 네트워크를 통해 전송합니다.

  * 전송 계층 (Transport Layer):

  전송 계층은 데이터를 신뢰성 있게 전송하기 위해 TCP(Transmission Control Protocol)와 UDP(User Datagram Protocol) 프로토콜을 사용합니다. TCP는 신뢰성 있는 연결 기반의 데이터 전송을 제공합니다. 데이터를 세그먼트(Segment) 단위로 분할하고, 패킷이 제대로 전달되었는지 확인하고 재전송하는 기능을 수행합니다. 반면에 UDP는 비연결성 기반의 프로토콜로, 데이터를 데이터그램(Datagram) 단위로 전송하지만 데이터의 신뢰성은 보장하지 않습니다.

  - 응용 계층 (Application Layer):

  응용 계층은 최종 사용자에게 서비스를 제공하는 계층입니다. 웹 브라우저, 이메일 클라이언트, 파일 전송 프로그램 등의 응용 소프트웨어가 이 계층에서 동작합니다. 응용 계층에서는 사용자와 컴퓨터 네트워크 간의 인터페이스를 제공하며, HTTP(Hypertext Transfer Protocol), FTP(File Transfer Protocol), SMTP(Simple Mail Transfer Protocol) 등과 같은 프로토콜들이 사용됩니다. 응용 계층에서는 사용자의 요청에 따라 데이터를 다른 계층으로 전달하거나 받은 데이터를 응용 프로그램으로 제공합니다.
  -> TCP/IP의 이러한 계층 구조를 통해 데이터는 하위 계층에서 상위 계층으로 전달되면서 신속하고 안전하게 통신됩니다.
  -> 각 계층은 독립적으로 동작하며, 계층 간의 인터페이스를 통해 데이터가 원활하게 전송될 수 있습니다.