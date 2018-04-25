---
title: 에지 서버 Cmdlet
TOCTitle: 에지 서버 Cmdlet
ms:assetid: 1a5427f4-a0d1-4652-8135-91333158ffc8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg415635(v=OCS.15)
ms:contentKeyID: 49302965
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 에지 서버 Cmdlet

 

_**마지막으로 수정된 항목:** 2013-10-07_

에지 서버는 내부 네트워크에 로그온하지 않은 사용자도 Microsoft Lync Server 2013의 기능을 사용할 수 있도록 합니다. 예를 들어 내부 네트워크를 통해서가 아니라 인터넷을 통해 Lync Server 2013에 로그온한 인증된 원격 사용자가 있는 경우 Lync Server 액세스 에지 서비스를 실행하는 에지 서버를 설정해야 합니다. 또한 다른 조직과 페더레이션을 설정하려는 경우나 사용자에게 Yahoo\!, AOL, MSN 등의 공용 메신저 서비스에 계정이 있는 사람들과 통신하는 권한을 제공하려는 경우 에지 서버가 필요합니다.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속해서 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



## 에지 서버 Cmdlet

다음은 에지 서버 관리에 직접적으로 관련된 cmdlet 목록입니다.

**에지 서버**

  -   
    [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)

  -   
    [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

  -   
    [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)

  -   
    [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)

  -   
    [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  -   
    [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

  -   
    [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

  -   
    [Set-CsEdgeServer](set-csedgeserver.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150)

