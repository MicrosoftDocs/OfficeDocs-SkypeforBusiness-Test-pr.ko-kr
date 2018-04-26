---
title: 'Lync Server 2013: 조직에 대한 외부 액세스 정책 관리'
TOCTitle: 조직에 대한 외부 액세스 정책 관리
ms:assetid: 5571811e-34c8-443a-b94c-1ab5d4275581
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520995(v=OCS.15)
ms:contentKeyID: 49303675
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 외부 액세스 정책 관리

 

_**마지막으로 수정된 항목:** 2013-10-07_

에지 서버를 하나 이상 배포한 후에는 조직에 대해 지원할 유형의 외부 액세스를 사용하도록 설정해야 합니다.

조직에서 외부 사용자 액세스를 이미 지원하도록 설정한 경우에도 기본적으로 원격 사용자 액세스, 페더레이션 사용자 액세스를 비롯한 외부 사용자 액세스를 지원하는 정책은 구성되지 않습니다. 외부 사용자 액세스 사용을 제어하려면 하나 이상의 정책을 구성하고 각 정책에 대해 지원되는 외부 사용자 액세스 유형을 지정해야 합니다. 다음 정책 범위를 만들고 구성할 수 있습니다. 기본적으로 글로벌 정책이 만들어지지만 삭제할 수는 없습니다.

  - **글로벌 정책**   글로벌 정책은 에지 서버를 배포할 때 작성됩니다. 기본적으로 글로벌 정책에서는 외부 사용자 액세스 옵션이 사용하도록 설정되지 않습니다. 글로벌 수준에서 외부 사용자 액세스를 지원하려면 외부 사용자 액세스 옵션 유형을 하나 이상 지원하도록 글로벌 정책을 구성합니다. 글로벌 정책은 조직의 모든 사용자에게 적용되지만, 사이트 정책과 사용자 정책이 글로벌 정책을 다시 정의합니다. 삭제한 글로벌 정책은 제거되는 것이 아니라 기본 설정으로 다시 설정됩니다.

  - **사이트 정책**   하나 이상의 사이트 정책을 만들고 구성하여 특정 사이트에 대한 외부 사용자 액세스 지원을 제한할 수 있습니다. 사이트 정책의 구성은 사이트 정책에 포함되는 특정 사이트에 한해 글로벌 정책을 다시 정의합니다. 예를 들어 글로벌 정책에서 원격 사용자 액세스를 사용하도록 설정하는 경우 특정 사이트에 대해서는 원격 사용자 액세스를 사용하지 않도록 설정하는 사이트 정책을 지정할 수 있습니다. 기본적으로 사이트 정책은 해당 사이트의 모든 사용자에게 적용되지만, 사용자에게 사용자 정책을 지정하여 사이트 정책 설정을 다시 정의할 수 있습니다.

  - **사용자 정책**   하나 이상의 사용자 정책을 만들고 구성하여 특정 사용자에 대한 원격 사용자 액세스 지원을 제한할 수 있습니다. 사용자 정책의 구성은 사용자 정책이 지정된 특정 사용자에 한해 글로벌 정책 및 사이트 정책을 다시 정의합니다. 예를 들어 글로벌 정책 및 사이트 정책에서 원격 사용자 액세스를 사용하도록 설정하는 경우 원격 사용자 액세스를 사용하지 않도록 설정하는 사용자 정책을 지정한 다음 특정 사용자에게 해당 사용자 정책을 지정할 수 있습니다. 사용자 정책을 만드는 경우에는 한 명 이상의 사용자에게 정책을 적용해야 정책이 효력을 발휘합니다.


> [!IMPORTANT]
> 한 정책 수준에서 적용되는 Lync Server 정책 설정은 다른 정책 수준에서 적용되는 설정을 재정의할 수 있습니다. Lync Server 정책 우선 순위에 따르면 사용자 정책(최대 영향력)이 사이트 정책을 재정의한 후 사이트 정책이 글로벌 정책(최소 영향력)을 재정의합니다. 즉, 정책 설정이 해당 정책의 영향을 받는 개체에 가까울수록 개체에 미치는 영향력도 커집니다.



이러한 옵션에는 다음과 같은 유형의 외부 액세스가 포함됩니다.

  - **페더레이션 사용자와의 통신 사용**    페더레이션 파트너 도메인에 대한 사용자 액세스를 지원하려면 이 옵션을 사용하도록 설정합니다. 이 설정은 사용자가 다른 Microsoft Office 365와 같은 호스트된 공급자는 물론 다른 SIP 페더레이션 도메인과 통신할 수 있는 기능을 구성합니다. 이 설정을 선택하면 XMPP 페더레이션 도메인과의 통신을 허용하는 옵션을 선택할 수 있습니다.
    
    **페더레이션 사용자와의 통신 사용** 을 처음 선택할 경우에는 옵션으로 **XMPP 페더레이션 파트너와의 통신 사용** 을 선택할 수 있습니다. XMPP 페더레이션은 XMPP(Extensible Messaging and Presence Protocol)를 사용하는 조직과의 페더레이션입니다.
    

    > [!NOTE]
    > XMPP 페더레이션을 사용하도록 설정한 경우 <STRONG>XMPP 페더레이션</STRONG> 도 토폴로지 작성기의 에지 풀 구성 섹션에 배포하도록 선택해야 합니다. XMPP 페더레이션을 구성하면 에지 서버에 XMPP 프록시가 배포되고 프런트 엔드 서버에 XMPP 게이트웨이가 배포됩니다.



  - **원격 사용자와의 통신 사용**    방화벽 외부에 있는 조직 사용자(예: 재택 근무자, 출장 중인 사용자)가 인터넷을 통해 Lync Server에 연결할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다.

  - **공용 사용자와의 통신 사용**    내부 사용자가 공용 IM 공급자 연락처(예: Windows Live, Yahoo\! 및 AOL(America Online)에서 제공된 연락처)와 통신할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다.
    

    > [!IMPORTANT]
    > <UL>
    > <LI>
    > <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
    > <LI>
    > <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
    > <LI>
    > <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>




> [!NOTE]
> 외부 사용자 액세스 지원을 사용하도록 설정하는 것 외에도, 조직에서 외부 사용자 액세스 사용을 제어하는 정책을 구성해야 사용자들이 외부 사용자 액세스 유형을 사용할 수 있습니다. 외부 사용자 액세스에 대한 정책 만들기, 구성 및 적용에 대한 자세한 내용은 <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함</A>을 참조하십시오.



**Windows PowerShell cmdlet을 사용하여 외부 액세스 정책을 보려면**

  - Lync Server 관리 셸 및 **Get-CsExternalAccessPolicy** cmdlet을 사용하여 외부 액세스 정책을 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.
    
    모든 외부 액세스 정책에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsExternalAccessPolicy
    
    이 명령은 다음과 비슷한 정보를 반환합니다.
    
        Identity                          : Global
        Description                       :
        EnableFederationAccess            : False
        EnableXmppAccess                  : False
        EnablePublicCloudAccess           : False
        EnablePublicCloudAudioVideoAccess : False
        EnableOutsideAccess               : False

## 이 단원의 내용

  - [Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md)

  - [Lync Server 2013에서 XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md)

  - [Lync Server 2013에서 원격 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-remote-user-access.md)

  - [Lync Server 2013에서 공용 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-public-user-access.md)

  - [Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)

  - [Lync Server 2013에서 외부 사용자 액세스 정책 다시 설정 또는 삭제](lync-server-2013-resetting-or-deleting-external-user-access-policies.md)

