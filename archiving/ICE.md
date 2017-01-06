ICE (RFC 5245)
==============

-	stun과 turn을 활용하여 offer/answer model의 프로토콜에 적용할 수 있다.
-	ice는 offer/answer 모델에 의해 생성되는 udp 기반 미디어 스트림을 위한 nat traversal기술이다. -
-	stun + turn을 이용하여 sip client가 최적의 rtp통신(가급적 p2p)를 하도록 해야 함.  
-	turn은 worst case에만 사용하도록!  
-	그래서, 초기 invite message를 전송하기 전에 가능한 모든 정보들을 수집하여 결정해야함.  

#### 용어

-	server reflexive address : NAT장비가 부여한 client의 public address

STUN
----

-	**"자신의 public ip와 port를 확인하는 과정 + NAT Type을 확인"**
-	client-server 프로토콜.

-	stun client는 서버로 binding request 메세지를 보내고,

-	서버는 그 응답으로 binding response 메세지를 보낸다.

-	Sturn server는 nat type을 알아내기 위해서는 2개의 public ip주소와 2개의 소스 포트를 가지고 있어야 한다. 보통 3478, 3479... 이를 통해 4가지의 test를 통해서 type을 알아낸다.

-	client는 자신의 public ip를 알 수 없으므로, server는 client의 public 주소를 알려준다.

-	server는 layer3/4 ip주소와 포트 넘버 <=> stun 패킷의 페이로드 내의 ip주소,port넘버와 비교한 후에 자신의 db에다가 두 주소를 바인딩한다.

TURN
----

#### 용어

-	relayed transport address : turn server의 ip, port  

---

#### 정리

-	**"미디어 스트림을 relay하는 relay server"**
-	**Client가 firewall 뒤에 있거나, symmetric nat환경인 경우 p2p로 연결할 수 없기에, turn 서버를 이용하여 rtp packet을 relay한다.**
-	nat 상황에 놓인 호스트가 릴레이 서버를 활용하여 상호 통신하도록 함.  
-	client는 nat 장비 뒤, server는 공인망에 위치한다.  
-	turn client -> turn server로 turn message를 보낸다.  
	message에는 turn client의 사설망 내의 ip(host transport address), port를 담아서 보낸다.  
-	turn server는 turn message 내의 host transport address와

-	**turn server는 public ip를 가지기 때문에, peer들이 firewall, proxy뒤에 있어도 접근할 수 있다.**
	------------------------------------------------------------------------------------------------

**참고**  
- https://voipmagazine.wordpress.com/tag/server-reflexive-address/ - http://www.nexpert.net/424  
- stun을 이용한 nat type discovery http://www.netmanias.com/ko/post/blog/5856/nat-network-protocol-stun/rfc-5780-nat-behavior-discovery-using-stun
