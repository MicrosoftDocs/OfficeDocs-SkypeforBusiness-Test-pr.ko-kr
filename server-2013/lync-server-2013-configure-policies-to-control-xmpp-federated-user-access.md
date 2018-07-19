---
title: 'Lync Server 2013: XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성'
TOCTitle: XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성
ms:assetid: 0fe0ff75-e52a-4e3e-923a-64f6412ac4e4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ552446(v=OCS.15)
ms:contentKeyID: 49302829
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 설명서는 준비 단계인 설명서이므로 변경될 수 있습니다. 빈 항목은 자리 표시자로 포함되어 있습니다.

XMPP(Extensible Messaging and Presence Protocol) 페더레이션 파트너 지원을 위한 정책을 구성하면 해당 정책은 XMPP 페더레이션 도메인 사용자에게는 적용되지만 SIP(Session Initiation Protocol) IM(인스턴트 메시징) 서비스 공급자(예: Windows Live) 또는 SIP 페더레이션 도메인 사용자에게는 적용되지 않습니다. 사용자가 대화 상대를 추가하고 통신하도록 허용할 각 XMPP 페더레이션 도메인에 대해 **XMPP 페더레이션 파트너**를 구성합니다. XMPP 페더레이션 파트너 정책은 단일 범위에서만 사용 가능하며, 글로벌 정책으로 정의되지는 않지만 글로벌 정책으로 작동합니다. XMPP 페더레이션 파트너에 대해 글로벌, 사이트 또는 사용자 정책을 정의하려면 먼저 필요한 범위에 대해 외부 액세스 정책을 만들고 구성하여 정책 범위를 구성합니다. 외부 액세스 및 페더레이션용으로 구성할 수 있는 정책의 유형에 대한 자세한 내용은 [Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md)를 참조하십시오.


> [!NOTE]
> 모든 <STRONG>페더레이션 및 외부 액세스</STRONG> 정책은 인밴드 프로비전을 통해 적용됩니다. 사용자에게 적용되거나, 사이트에 속하거나, 범위가 글로벌인 정책은 로그인 중에 클라이언트에게 전달됩니다. 조직에 대해 XMPP 페더레이션을 사용하도록 설정하지 않았더라도 XMPP 페더레이션 파트너 액세스를 제어하는 정책을 구성할 수 있습니다. 그러나 구성하는 정책은 조직에 대해 XMPP 파트너 페더레이션을 배포하고 사용하도록 설정하고 구성하는 경우에만 적용됩니다. XMPP 파트너 페더레이션을 배포 및 구성하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md">Lync Server 2013에서 SIP 페더레이션, XMPP 페더레이션 및 공용 메신저 구성</A>을 참조하십시오. 또한 XMPP 페더레이션 파트너를 제어하기 위해 외부 액세스 정책에서 사용자 정책을 지정하는 경우 해당 정책은 Lync Server 2013에 대해 사용하도록 설정되며 정책을 사용하도록 구성되는 사용자에게만 적용됩니다.



## XMPP 페더레이션 파트너에 대한 글로벌 정책을 편집하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭하고 **외부 액세스 정책** 을 클릭합니다.

4.  **외부 액세스 정책** 페이지에서 글로벌 정책에 대해 다음을 수행합니다.

5.  글로벌 정책을 클릭하고 **편집** 을 클릭한 다음 자세한 정보 표시를 클릭합니다.

6.  원하는 경우 글로벌 정책의 설명을 입력합니다.

7.  **페더레이션 사용자와의 통신 사용** 을 선택합니다.

8.  Select **Enable communications with XMPP federated users(XMPP 페더레이션 사용자와의 통신 사용)** 을 선택합니다.

9.  글로벌 정책에 대한 변경 내용을 저장하려면 **커밋** 을 클릭합니다.

## XMPP 페더레이션 파트너에 대한 사이트 또는 사용자 정책을 만들려면

1.  **새로 만들기** 를 클릭하고 **사이트 정책** 또는 **사용자 정책** 을 클릭합니다. **사이트 선택** 의 목록에서 적절한 사이트를 클릭하고 **확인** 을 클릭합니다.

2.  원하는 경우 사이트 정책의 설명을 입력합니다.

3.  사이트 또는 사용자 정책에서 **페더레이션 사용자와의 통신 사용** 을 선택합니다.

4.  Select **Enable communications with XMPP federated users(XMPP 페더레이션 사용자와의 통신 사용)** 을 선택합니다.

5.  **커밋** 을 클릭하여 변경 내용을 사이트 또는 사용자 정책에 저장합니다.

## XMPP 페더레이션 파트너에 대한 기존 정책을 편집하려면

1.  기존 정책을 변경하려면 목록에서 적절한 정책을 선택하고 **편집** , **자세한 정보 표시** 를 차례로 클릭합니다.

2.  원하는 경우 정책의 설명을 변경하거나 업데이트합니다.

3.  **페더레이션 사용자와의 통신 사용** 을 선택하거나 선택을 취소합니다.

4.  **XMPP 페더레이션 사용자와의 통신 사용** 을 선택하거나 선택을 취소합니다.

5.  정책에 대한 변경 내용을 저장하려면 **커밋** 을 클릭합니다.

## Windows PowerShell을 사용하여 XMPP 페더레이션 파트너에 대한 기존 정책을 편집하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    아래에는 페더레이션 사용자 액세스를 위한 글로벌 정책을 True(사용)로 설정하고 XMPP 도메인 액세스를 True(사용)로 설정하는 명령의 예가 나와 있습니다.
    
        Set-CsExternalAccessPolicy -Identity global -EnableFederationAccess $true -EnableXmppAccess $true

## Windows PowerShell을 사용하여 XMPP 페더레이션 파트너에 대한 사이트 또는 사용자 정책을 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        New-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false>
    
    아래에는 페더레이션 사용자 액세스를 위한 Redmond 사이트용 사이트 정책을 사용하도록 설정하고 XMPP 도메인 액세스를 사용하도록 설정하는 명령의 예가 나와 있습니다.
    
        New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true

## Windows PowerShell을 사용하여 XMPP 페더레이션 파트너에 대한 기존 정책을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy>
    
    아래에는 사용자 정책을 삭제하는 명령의 예가 나와 있습니다.
    
        Remove-CsExternalAccessPolicy -Identity EAPUserPolicySetXMPP

4.  아래에는 글로벌 정책을 기본값으로 다시 설정하는 명령의 예가 나와 있습니다.
    
        Remove-CsExternalAccessPolicy -Identity global

## 참고 항목

#### 작업

[Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)  
[Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  

#### 기타 리소스

[Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
[Set-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExternalAccessPolicy)  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)  
[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)

