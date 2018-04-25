---
title: 'Lync Server 2013: 분기 사이트에 대한 PSTN 게이트웨이 정의'
TOCTitle: 분기 사이트에 대한 PSTN 게이트웨이 정의
ms:assetid: 87be2fe2-1d56-4062-b430-439d4536414c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398689(v=OCS.15)
ms:contentKeyID: 49304284
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 분기 사이트에 대한 PSTN 게이트웨이 정의

 

_**마지막으로 수정된 항목:** 2012-09-21_

하나 이상의 프런트 엔드 풀 또는 Standard Edition 서버를 포함하는 중앙 사이트에서 이 절차를 수행합니다.


> [!IMPORTANT]
> 절차를 수행하기 전에 다음 조건을 충족해야 합니다. 
> <UL>
> <LI>
> <P>Lync Server 2013통신 소프트웨어를 중앙 사이트에 설치해야 합니다.</P>
> <LI>
> <P>중재 서버를 중앙 사이트에 배포해야 합니다.</P></LI></UL>



## PSTN 게이트웨이를 정의하려면

1.  **시작** , **모든 프로그램** , **Microsoft Lync Server** 를 차례로 클릭한 다음 **Lync Server 토폴로지 작성기** 를 클릭합니다.

2.  콘솔 트리에서 중앙 사이트, **지점 사이트** 를 차례로 확장한 다음 PSTN(공중 전화망) 게이트웨이를 정의할 분기 사이트의 이름을 확장한 후 **공유 구성 요소** 를 확장합니다.

3.  **PSTN 게이트웨이** 를 마우스 오른쪽 단추로 클릭한 다음 **새 IP/PSTN 게이트웨이** 를 클릭합니다.

4.  **새 IP/PSTN 게이트웨이 정의** 대화 상자에서 **게이트웨이 FQDN 또는 IP 주소** 를 클릭한 다음 분기 사이트에 배포할 게이트웨이의 FQDN(정규화된 도메인 이름) 또는 IP 주소를 입력합니다.

5.  **IP/PSTN 게이트웨이용 수신 대기 포트** 를 클릭한 다음 기본값을 수락합니다.

6.  **SIP 전송 프로토콜** 목록에서 게이트웨이가 사용하는 전송 프로토콜을 클릭한 다음 **확인** 을 클릭합니다.
    

    > [!NOTE]
    > 보안을 위해 TLS(전송 계층 보안)를 지원하는 PSTN 게이트웨이를 사용하는 것이 좋습니다.




> [!TIP]
> PSTN 게이트웨이의 속성을 수정하려면 <STRONG>Set-CsPstnGateway</STRONG> cmdlet을 사용합니다. 자세한 내용은 Lync Server 관리 셸 도움말의 <A href="set-cspstngateway.md">Set-CsPstnGateway</A>를 참조하십시오.



분기 사이트 복구의 **다음 단계** : [Lync Server 2013에서 분기 사이트 복원을 위한 사용자 구성](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

## 참고 항목

#### 개념

[Lync Server 2013의 PSTN 게이트웨이 배포 옵션](lync-server-2013-pstn-gateway-deployment-options.md)

