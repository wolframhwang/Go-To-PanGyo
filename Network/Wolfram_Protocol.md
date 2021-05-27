# 통신 프로토콜

> 통신 프로토콜(Protocol)의 정의

- 서로 다른 시스템에 존재하는 개체(Entity)간의 원활한 통신을 위한 소프트웨어적, 하드웨어적 약속이나 규칙 및 규약을 말한다.
    - 시스템 : 컴퓨터, Terminal을 말한다.
    - 개체 : 사용자 프로그램, 파일 전송 프로그램, 데이터 베이스 등을 말한다.

> 통신 프로토콜의 기본 구성 요소

- 구문(Syntax) : 데이터 형식, 부호화, 신호 레벨(Signal Level)등의 요소를 말한다.
- 의미(Semantics): 전송 제어 및 오류 처리를 위한 정보 등을 규정한다.
- 시간(Timing) : 두 개체 간의 통신 속도를 조정하거나 메세지의 전송 및 순서에 대한 특성을 가리킨다.

> 통신 프로토콜의 주요 기능

- 단편화와 재결합(Fragmentation and Reassembly)
    - 많은 양의 데이터 블록은 효율적인 전송이 되도록 작은 단위의 블록(패킷)을 단편화하여 전송하며, 수신된 작은 단위의 블록은 다시 원래의 데이터가 될때 재결합 되어야만 한다.
    - 효과적으로 오류를 제어할수 있고 응답시간이 빠르다.
    - 재결합시 프레임에 순서 번호를 부여하는 등 부수적인 데이터의 증가와 처리시간이 길어져서 비효율 적이다.
- 캡슐화(Encapsulation)
    - 데이터의 플래그(Flag), 주소(Address), 제어정보(Control Block)등 정보 데이터와 그것을 오류없이 전송하기 위한 구조적인 묶음을 말한다. Ex) HDLC, BASIC, DDCMP, TCP
- 캡슐의 주요 제어 정보
    - 주소(Address), 에러 검출 코드(Error Detecting Code), 프로토콜 제어(Protocol Control)
- 연결 제어(Connection Control)
    - 회선 접속 -> 링크 확립 -> 데이터 전송 -> 링크 해제 -> 회선 절단에서 링크 확립과 링크 해제 단계를 제어하는 기능을 연결 제어 기능이라고 한다.
- 흐름 제어(Flow Control)
    - 두 개체 사이에 데이터의 개수나 속도를 조절하는 기능이다.
- 오류 제어(Error Control)
    - 수신된 오류를 검출하고 재전송을 요구하는 기능이다. Ex) ARQ, Hamming Code, Parity
- 동기화(Synchronization)
    - 데이터 전송은 직렬 전송으로 이루어진다. 따라서 송신측의 정보를 수신측에서 정확하게 수신하기 위해서는 직렬 입력 파형으로부터 비트와 문자를 정확하게 시간에 맞춰서 수신을 해야만 한다.
    - 송신측과 수신측이 같은 시간으로 동작하게 하는 기능을 말한다.
- 순서 제어(Sequencing)
    - 연결 제어의 순서적 절차 기능으로 데이터 조각(패킷)에 순서를 부여하여 전송하거나 수신된 데이터 조각을 순서에 맞게 조립하는 기능이다.
- 주소 지정(Addressing)
    - 데이터를 목적지까지 전송할수 있도록 데이터에 목적지 위치(주소)를 추가하고 관리하는 기능이다. Ex) IP주소, Subnet mask, NIC주소, ARP, RARP등등…
- 다중화(Multiplexing)
    - 여러개의 회선에서 데이터를 받아 한개의 고속 회선으로 송신하거나 반대로 고속 회선에서 데이터를 입력받아서 여러개의 회선으로 분할하는 기능이다. Ex) FDM , TDM, CDM
- 경로 선택(Routing)
    - 송, 수신 간에 중간 서브넷(부 네트워크, 중간 노드)을 거쳐서 최적의 경로를 선택하게 하는 기술이다.
    - 서브넷 자원의 이용을 최대화하여 평균 패킷 전송 시간을 최소화 하는 기능이다.

> 통신 프로토콜의 종류

- X.25
    - 패킷 교환망에 광범위하게 사용되는 네트워크 프로토콜로서 CCITT에 의해 표준으로 채택되었다. 패킷형으로 동작하는 데이터 단말장치(DTE)와 데이터 회선 종단장치(DCE)간의 인터페이스로, 사용자 단말 장치와 패킷 교환망(PSDN)간의 데이터 교환 절차를 정의하고 있다.
        - 공중 패킷 교환망에 대한 ITU-T의 권고안 이다.
        - 물리 계층, 데이터 링크 계층, 패킷 계층들에 대한 기능으로 구성된다.
        - 연결형 네트워크 프로토콜이다.
        - 흐름 및 오류 제어 기능을 제공한다.
- OSI(Open Systems Interconnection) : 개방형 시스템간 상호 접속
    - 국제 표준화 기구인 ISO에서 개발된 OSI는 통신 네트워크 간에 어떻게 데이터를 전송할 것인가에 대한 표준 규약 또는 참조 모델이다.
    - OSI참조모델은 통신의 종단에서 이루어지는 기능을 7계층으로 정의했다.
        - Application
        - Presentation
        - Session
        - Transport
        - Network
        - Data Link
        - Physical
    - 통신 제어 프로그램(Communication Control Program)이란?
        - 데이터 전송 회선과 통신 제어 장치를 이용해서 컴퓨터와 단말기 간, 단말기와 단말기 간, 컴퓨터와 컴퓨터 간의 정보를 송 수신 하기위한 프로그램을 통칭하여 통신제어 프로그램 혹은 통신 소프트웨어라고 한다.
        - 다음의 세가지 기능이 있어야 통신 제어프로그램이라고 할수 있다.
            - 데이터 송, 수신 기능 
                - 두 노드 간에 정보를 교환을 위해서는 사전에 송, 수신측 간 통신 제어 프로그램의 명령이나 응답에 관한 신호의 제어 및 전달 방식을 약속해야 한다. 이러한 약속을 프로토콜 이라고 하며, 통신 소프트웨어가 지원한다.
            - 통신 하드웨어 제어 기능
                - 통신에 필요한 하드웨어와의 신호 및 데이터 송,수신을 행하는 모든 통신 제어를 소프트웨어가 제공한다.
            - User Interface 제어 기능
                - 이용자가 통신 시스템을 쉽게 지시하고 통신 기능을 원만하게 수행할수 있도록 하는 기본 명령을 소프트웨어가 제공한다.

> REFERENCE : 이기적 정보 처리기사, https://blog.naver.com/adamdoha/222134105596
