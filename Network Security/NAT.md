# NAT(Network Address Translation)

IP패킷에 있는 출발지 및 목적지의 IP주소와 TCP/UDP 포트 숫자 등을 바꿔 재기록하면서 네트워크 트래픽을 주고 받게 하는 기술이다.

## 용도

* **IP주소 절약**<br>
    NAT기술을 이용하면, 하나의 공인 IP주소를 사용하여 여러 대의 호스트가 인터넷에 접속할 수 있다.

    집에 인터넷 회선을 개통하고 인터넷 공유기를 설치해서 여러 PC를 연결하여 사용한다. 이러한 방법이 가능한 이유는 인터넷 공유기에 NAT기능이 탑재되어 있기 때문이다. 
* **보안**<br>
    NAT 동작의 특성상 IP를 숨길 수 있는 기능이 있다.

    라우터 외부로 트래칙이 나갈 때는 사설IP가 공인 IP 주소로 바뀌므로 공격자가 라우터 안 쪽에 있는 사설 IP를 모르기 때문에 최종 목적지로의 공격이 어려워진다.


## 종류

* **Static NAT(1:1 NAT)**<br>

    공인 IP주소와 사설 IP 주소가 1:1로 매칭이 되는 방식<br>

    출발지와 목적지의 IP를 미리 매핑해 고정해놓은 NAT를 정적 NAT라고 한다.

    <img src='..\images\SNAT.png' width=500 align=center>

<br>

* **Dynamic NAT(1:N, N:1, N:M)**<br>

    여러 개의 내부 IP주소와 여러개의 외부 IP주소를 동적으로 매핑시키는 방법<br>

    공인 주소 여러 개는 공인 주소 pool에 담겨 있고 사설 주소가 이를 요청했을 경우 pool에 있는 공인 주소를 그때마다 꺼내어 동적으로 맵핑해 준다.
    정적 NAT는 출발지와 목적지 매칭 관계가
    
    <img src='..\images\DNAT.png' width=500 align=center>

* **PAT(Port Address Translation)**<br>

    공인 IP 주소 1개에 사설 IP 주소 여러 개가 매칭이 되는 방식.

    변환된 IP주소로는 사내망 호스트들을 구분할 수 없기 때문에 포트번호를 부여하여 구분한다.

    PAT는 공인IP(L3)뿐만 아니라 포트(L4)까지 함께 패킷에 사용되기 떄문에, 공인 포트번호에 맵핑된 호스트의 사설 IP를 찾아, 올바른 호스트에게 패킷을 전달할 수 있다.

     <img src='..\images\PNAT.png' width=500 align=center>
