---
title: 'Lync Server 2013: 토폴로지 작성기에서 추가 트렁크 정의'
TOCTitle: 토폴로지 작성기에서 추가 트렁크 정의
ms:assetid: e68b8377-50a2-452a-bf5c-910929e34236
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721915(v=OCS.15)
ms:contentKeyID: 49886028
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 토폴로지 작성기에서 추가 트렁크 정의

 

_**마지막으로 수정된 항목:** 2012-10-04_

다음 단계에 따라 토폴로지 작성기를 사용하여 *피어* 와 중재 서버를 연결할 수 있는 추가 트렁크를 정의하십시오. 사용자는 피어를 통해 PSTN(공중 전화망)에 연결하여 Enterprise Voice를 사용할 수 있습니다. 피어는 ITSP(인터넷 전화 통신 서비스 공급자)의 SBC(세션 경계 컨트롤러), IP-PBX 또는 PSTN 게이트웨이일 수 있습니다. 트렁크는 중재 서버와 피어 사이에서 이 연결을 정의합니다. 중재 서버마다 여러 트렁크를 정의할 수 있습니다. 하나의 중재 서버를 여러 피어와 연결할 수 있습니다

트렁크는 튜플로 고유하게 식별되는 게이트웨이와 중재 서버 간의 논리적 연결입니다.

{ 중재 서버 FQDN, 중재 서버 수신 대기 포트(TLS 또는 TCP) : 게이트웨이 IP 및 FQDN, 게이트웨이 수신 대기 포트}


> [!NOTE]
> 이 항목에서는 배포 설명서의 <A href="lync-server-2013-define-a-gateway-in-topology-builder.md">Lync Server 2013의 토폴로지 작성기에서 게이트웨이 정의</A>에 설명된 대로 하나 이상의 배치되었거나 독립 실행형인 중재 서버 또는 풀로 PSTB 게이트웨이 및 루트 트렁크를 설정했다고 가정합니다.




> [!NOTE]
> 이 항목에서는 배포 설명서의 <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Lync Server 2013에서 프런트 엔드 풀 또는 Standard Edition 서버 정의 및 구성</A> 및 <A href="lync-server-2013-publish-the-topology.md">Lync Server 2013에서 토폴로지 게시</A>에 설명된 대로 하나 이상의 중앙 사이트에 하나 이상의 프런트 엔드 풀 또는 Standard Edition 서버를 설정했다고 가정합니다.



## 중재 서버와 게이트웨이 피어 사이에 추가 트렁크를 정의하려면

1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

2.  Lync Server 2013, 해당 사이트 이름, **공유 구성 요소** 에서 **트렁크** 노드를 마우스 오른쪽 단추로 클릭하고 **새 트렁크(New Trunk)** 를 클릭합니다.
    
    ![Lync Server 토폴로지 작성기 파일 구조 화면](images/JJ721915.90d5b349-aa1e-407a-87ed-fa112f478560(OCS.15).png "Lync Server 토폴로지 작성기 파일 구조 화면")

3.  **새 트렁크 정의(Define New Trunk)** 에서 트렁크를 고유하게 식별할 이름을 지정합니다. 두 트렁크에 동일한 이름을 사용할 수 없습니다.
    

    > [!NOTE]
    > TLS(전송 계층 보안)을 전송 유형으로 지정하는 경우 중재 서버의 IP 주소 대신 FQDN을 지정해야 합니다.



4.  **연결된 PSTN 게이트웨이(Associated PSTN gateway)** 에서 이 트렁크와 연결할 PSTN 게이트웨이 피어를 선택합니다.
    
    ![트렁크의 PSTN 게이트웨이 피어에 대한 속성 설정](images/JJ721915.7c3fe8ee-8f4c-4413-8462-8347228e61bb(OCS.15).png "트렁크의 PSTN 게이트웨이 피어에 대한 속성 설정")

5.  **PSTN 게이트웨이용 수신 대기 포트(Listening Port for PSTN gateway)** 에서 피어(PSTN 게이트웨이, IP-PBX 또는 SBC)가 이 트렁크와 연결되어야 할 중재 서버로부터 SIP 메시지를 받을 수신 대기 포트를 입력합니다. 기본 피어 포트는 TCP(Transmission Control Protocol)의 경우 5066이고 TLS(전송 계층 보안)의 경우 5067이며, 기본 SBA(Survivable Branch Appliance) 포트는 TCP의 경우 5081이고 TLS의 경우 5082입니다.

6.  **SIP 전송 프로토콜** 아래에서 피어에서 사용할 전송 유형을 클릭합니다.
    

    > [!NOTE]
    > 보안상의 이유로 TLS를 사용할 수 있는 중재 서버에 피어를 배포하는 것이 좋습니다.



7.  **연결된 중재 서버(Associated Mediation Server)** 에서 이 피어의 루트 트렁크와 연결할 중재 서버 풀을 선택합니다.

8.  **연결된 중재 서버 포트(Associated Mediation Server port)** 에서 중재 서버가 피어로부터 SIP 메시지를 받을 수신 대기 포트를 입력합니다.
    

    > [!NOTE]
    > Lync Server 2013에서 여러 트렁크가 지원될 경우 트렁크 이름이 서로 다른 두 트렁크를 동일한 <STRONG>연결된 중재 서버 포트(Associated 중재 서버 port)</STRONG> 와 <STRONG>IP/PSTN 게이트웨이용 수신 대기 포트</STRONG> 로 구성할 수는 없습니다.

    

    > [!NOTE]
    > Lync Server 2013에서 여러 트렁크가 지원되는 경우 여러 피어와의 통신을 위해 중재 서버에 여러 SIP 신호 처리 포트를 정의할 수 있습니다. 트렁크를 정의하는 경우 <STRONG>연결된 중재 서버 포트(Associated Mediation Server)</STRONG> 번호는 중재 서버에서 허용하는 해당 프로토콜에 대한 수신 대기 포트 범위에 속해야 합니다. 이 포트 범위는 Lync Server 2013과 중재 서버 풀 아래에 정의됩니다. 관련 중재 서버 풀을 마우스 오른쪽 단추로 클릭하고 <STRONG>속성 편집</STRONG> 을 선택합니다. <STRONG>수신 대기 포트</STRONG> 필드에 포트 범위를 지정합니다.



9.  **확인** 을 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 토폴로지 작성기에서 트렁크 수정](lync-server-2013-modify-a-trunk-in-topology-builder.md)

