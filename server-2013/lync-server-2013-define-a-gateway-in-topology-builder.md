---
title: 'Lync Server 2013: 토폴로지 작성기에서 게이트웨이 정의'
TOCTitle: 토폴로지 작성기에서 게이트웨이 정의
ms:assetid: 456e5a96-d9f6-42a6-862c-a69464391628
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425945(v=OCS.15)
ms:contentKeyID: 49303488
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 토폴로지 작성기에서 게이트웨이 정의

 

_**마지막으로 수정된 항목:** 2012-10-04_

다음 단계에 따라 토폴로지 작성기를 사용해서 Enterprise Voice가 설정된 사용자에 대해 PSTN(공중 전화망) 연결 기능을 제공하기 위해 중재 서버와 연결할 수 있는 *peer* 를 정의합니다. 중재 서버에 대한 피어는 PSTN 게이트웨이, IP-PBX 또는 SIP 트렁크를 구성하여 연결하는 ITSP(인터넷 전화 통신 서비스 공급자)에 대한 SBC(세션 경계 컨트롤러)일 수 있습니다.


> [!NOTE]
> 이 항목에서는 배포 설명서의 <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Lync Server 2013에서 프런트 엔드 풀 또는 Standard Edition 서버 정의 및 구성</A> 및 <A href="lync-server-2013-publish-the-topology.md">Lync Server 2013에서 토폴로지 게시</A>에 설명된 대로 사용자가 함께 배치된 또는 독립 실행형 중재 서버를 포함하는 하나 이상의 중앙 사이트에서 최소한 하나 이상의 내부 프런트 엔드 풀 또는 Standard Edition 서버를 설정했다고 가정합니다. 이 항목에서는 또한 사용자의 인프라가 <A href="lync-server-2013-software-prerequisites-for-enterprise-voice.md">Lync Server 2013의 Enterprise Voice에 대한 소프트웨어 필수 구성 요소</A> 및 <A href="lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md">Lync Server 2013의 Enterprise Voice에 대한 보안 및 구성 필수 구성 요소</A>에 설명된 필수 구성 요소를 충족하는 것으로 확인되었다고 가정합니다.



## 중재 서버의 피어를 정의하려면

1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

2.  Lync Server 2013, 사이트 이름, 공유 구성 요소 아래에서 **PSTN 게이트웨이** 노드를 마우스 오른쪽 단추로 클릭한 후 **새 PSTN 게이트웨이** 를 클릭합니다.
    
    ![토폴로지 작성기 Lync Server 2013](images/Gg425945.d898c3c1-8798-4b74-8f02-b994ef3db4c1(OCS.15).png "토폴로지 작성기 Lync Server 2013")

3.  **Define New IP/PSTN Gateway** 에서 피어의 FQDN(정규화된 도메인 이름) 또는 IP 주소를 입력하고 **다음** 을 클릭합니다.
    
    ![IP/PSTN 게이트웨이](images/Gg425945.8017ba5e-41bc-48d4-97d9-fd306cd322b8(OCS.15).png "IP/PSTN 게이트웨이")
    

    > [!NOTE]
    > TLS(전송 계층 보안)을 전송 유형으로 지정하는 경우 중재 서버의 IP 주소 대신 FQDN을 지정해야 합니다.



4.  새 PSTN 게이트웨이의 IP 주소에 대한 수신 노드(IPv4 또는 IPv6)를 정의하고 **다음** 을 클릭합니다.
    
    ![IP 주소](images/Gg425945.c7fc0d12-adc8-45a7-aca1-b376e1d2fcec(OCS.15).png "IP 주소")

5.  PSTN 게이트웨이에 대한 *루트 트렁크* 를 정의합니다. 트렁크는 중재 서버와 튜플로 고유하게 식별된 게이트웨이 사이의 논리적 연결입니다.
    
    { 중재 서버 FQDN, 중재 서버 수신 대기 포트(TLS 또는 TCP) : 게이트웨이 IP 및 FQDN, 게이트웨이 수신 대기 포트}
    
      - 토폴로지 작성기에서 PSTN 게이트웨이를 정의할 때는 PSTN 게이트웨이를 토폴로지에 성공적으로 추가하도록 루트 트렁크를 정의해야 합니다.
    
      - 연결된 PSTN 게이트웨이를 제거할 때까지는 루트 트렁크를 제거할 수 없습니다.
    
    ![게이트웨이 정의: 루트 트렁크](images/Gg425945.3b030757-eb35-4616-bb6b-74ee67507e3d(OCS.15).png "게이트웨이 정의: 루트 트렁크")

6.  **IP/PSTN 게이트웨이의 수신 대기 포트** 에서 게이트웨이, PBX 또는 SBC가 PSTN 게이트웨이의 루트 트렁크와 연결되는 중재 서버의 SIP 메시지에 대해 사용할 수신 대기 포트를 입력합니다. 기본적으로 TCP(Transmission Control Protocol)의 경우 포트 5066, PSTN 게이트웨이, PBX 또는 SBC의 TLS(전송 계층 보안)의 경우 포트 5067이 사용됩니다. 분기 사이트의 SBA(Survivable Branch Appliance)에서 기본 포트는 TCP의 경우 5081, TLS의 경우 5082입니다.

7.  **SIP 전송 프로토콜** 에서 피어가 사용하는 전송 유형을 클릭하고 **확인** 을 클릭합니다.
    

    > [!NOTE]
    > 보안상의 이유로 TLS를 사용할 수 있는 중재 서버에 피어를 배포하는 것이 좋습니다.



8.  **연관된 중재 서버**에서 이 PSTN 게이트웨이의 루트 트렁크와 연결할 중재 서버 풀을 선택합니다.

9.  **연관된 중재 서버 포트** 에서 중재 서버가 게이트웨이의 SIP 메시지에 대해 사용할 수신 대기 포트를 입력합니다.
    

    > [!NOTE]
    > Lync Server 2013의 다중 트렁크 지원을 포함하는 다중 SIP 신호 포트는 여러 PSTN 게이트웨이와의 통신에 사용할 수 있도록 중재 서버에 정의할 수 있습니다. 트렁크를 정의할 때 <STRONG>연관된 중재 서버 포트</STRONG> 는 중재 서버에서 허용되는 각 프로토콜에 대한 수신 대기 포트 범위 내에 있어야 합니다. 이 포트 범위는 Lync Server 2013 및 중재 풀 아래에 정의됩니다. 원하는 중재 서버 풀을 마우스 오른쪽 단추로 클릭하고 <STRONG>속성 편집</STRONG> 을 선택합니다. <STRONG>수신 대기 포트</STRONG> 필드에서 포트 범위를 지정합니다.



10. **마침** 을 클릭합니다.


> [!IMPORTANT]
> 이 단계를 마치기 전에 정의한 피어가 실행 중이고 사용자가 지정한 FQDN 또는 IP 주소를 사용 중인지 확인합니다.



다음으로, 토폴로지에 피어를 추가하려면 배포 설명서의 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md)에 설명된 절차를 따릅니다. Lync Server를 실행하는 서버에 파일을 설치할 때 해당 데이터를 사용할 수 있도록 토폴로지 작성기를 사용하여 토폴로지를 작성하거나 수정할 때마다 토폴로지를 게시해야 합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 토폴로지 작성기에서 트렁크 수정](lync-server-2013-modify-a-trunk-in-topology-builder.md)

