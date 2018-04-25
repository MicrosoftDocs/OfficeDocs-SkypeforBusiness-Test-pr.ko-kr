---
title: 'Lync Server 2013: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의'
TOCTitle: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의
ms:assetid: 1f49cfbe-30b3-4600-af15-47cb2f58d18a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398280(v=OCS.15)
ms:contentKeyID: 49303015
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의

 

_**마지막으로 수정된 항목:** 2012-10-07_

SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 토폴로지에 추가할 때 정의하지 않은 경우 중앙 사이트에서 이 절차를 수행합니다.

## SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 정의하려면

1.  **시작** , **모든 프로그램** , **Microsoft Lync Server 2013**, **Lync Server토폴로지 작성기**를 차례로 클릭합니다.

2.  콘솔 트리에서 중앙 사이트, **분기 사이트** 를 차례로 확장하고 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 배포하려는 분기 사이트의 이름을 확장합니다.

3.  **SBA(Survivable Branch Appliance)**를 마우스 오른쪽 단추로 클릭하고 **새 SBA(Survivable Branch Appliance)**를 클릭합니다.
    

    > [!IMPORTANT]
    > <STRONG>SBA(Survivable Branch Appliance)</STRONG>에서 지속 가능 분기 서버 및 SBA(Survivable Branch Appliance)를 정의합니다.



4.  **SBA(Survivable Branch Appliance)정의** 대화 상자에서 **FQDN**을 클릭하고, 이 분기 사이트에서 배포할 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 FQDN(정규화된 도메인 이름)을 입력한 후에 **다음**을 클릭합니다.
    

    > [!IMPORTANT]
    > SBA(Survivable Branch Appliance)를 정의하는 경우 <STRONG>FQDN</STRONG> 에 입력하는 이름은 <STRONG>servicePrincipalName</STRONG> 특성에 할당한 SBA(Survivable Branch Appliance) FQDN과 같아야 합니다. 자세한 내용은 <A href="lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md">Lync Server 2013에서 Active Directory에 SBA(Survivable Branch Appliance) 추가</A>를 참조하십시오.



5.  **프런트 엔드 풀** 을 클릭하고, 중앙 사이트에서 이 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 연결할 프런트 엔드 서버(사용자 서비스 풀)를 클릭한 후에 **다음** 을 클릭합니다.

6.  **에지 서버** 를 클릭하고 분기 사이트의 원격 사용자가 PSTN에 연결할 수 있도록 이 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 연결할 에지 풀을 클릭한 후에 **다음** 을 클릭합니다.

7.  **게이트웨이 FQDN 또는 IP 주소** 를 클릭하고, 인바운드 및 아웃바운드 PSTN 통화 라우팅을 위해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 연결된 게이트웨이 피어의 FQDN 또는 IP 주소를 입력합니다.
    

    > [!IMPORTANT]
    > SBA(Survivable Branch Appliance)를 정의하는 경우 이 게이트웨이는 SBA(Survivable Branch Appliance) 내의 중재 서버가 PSTN 연결을 위해 연결하는 게이트웨이입니다.



8.  **IP/PSTN 게이트웨이의 수신 대기 포트** 를 클릭하고 기본 포트를 적용합니다.

9.  **SIP 전송 프로토콜** 에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 사용할 전송 프로토콜을 클릭하고 **마침** 을 클릭합니다.
    

    > [!NOTE]
    > 보안상의 이유로, TLS(전송 계층 보안)를 사용하는 것이 좋습니다. SBA(Survivable Branch Appliance)를 정의하는 경우에는 사용 중인 SBA(Survivable Branch Appliance)가 TLS 프로토콜을 지원하는지 SBA(Survivable Branch Appliance) 공급업체 설명서를 확인하십시오.



10. 콘솔 트리에서 새 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 마우스 오른쪽 단추로 클릭하고 **토폴로지** 를 클릭한 후에 **게시** 를 클릭합니다.

**다음 단계** : [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 분기 사이트 작업](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)

