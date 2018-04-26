---
title: Lync Server 2013의 페더레이션 및 외부 액세스 Cmdlet
TOCTitle: Lync Server 2013의 페더레이션 및 외부 액세스 Cmdlet
ms:assetid: 4a384a57-257f-47a6-98d9-54cea2c647b7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg415651(v=OCS.15)
ms:contentKeyID: 49303540
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 페더레이션 및 외부 액세스 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-06-26_

페더레이션 및 외부 액세스는 두 가지 중요한 기능을 제공합니다. 페더레이션은 사용자가 조직 외부 사람들과 통신할 수 있도록 하며, 외부 액세스는 사용자가 내부 네트워크 바깥에서 Microsoft Lync Server 2013에 연결할 수 있도록 합니다. Lync Server 2013에서 페더레이션 및 외부 액세스를 관리하는 데 사용할 수 있는 cmdlet을 통해 사용자가 통신할 수 있는/없는 사람과, 내부 네트워크에 로그온하지 않고도 Lync Server에 연결할 수 있는지 여부를 확인할 수 있습니다.

## 페더레이션 및 외부 액세스 Cmdlet

페더레이션 및 외부 액세스에 적용되는 대부분의 관리 작업은 Lync Server 제어판에서 수행할 수 있습니다. 이와 동일한 작업을 Lync Server 관리 셸 또는 스크립트 내에서 cmdlet을 사용하여 수행할 수도 있습니다. 스크립트를 사용하는 경우 특정 작업을 자동화할 수 있습니다. 다음 목록에는 페더레이션 및 외부 액세스 관리와 직접적으로 관련된 cmdlet이 나와 있습니다.

  -   
    [Get-CsAllowedDomain](get-csalloweddomain.md)

  -   
    [New-CsAllowedDomain](new-csalloweddomain.md)

  -   
    [Remove-CsAllowedDomain](remove-csalloweddomain.md)

  -   
    [Set-CsAllowedDomain](set-csalloweddomain.md)

  -   
    [Get-CsBlockedDomain](get-csblockeddomain.md)

  -   
    [New-CsBlockedDomain](new-csblockeddomain.md)

  -   
    [Remove-CsBlockedDomain](remove-csblockeddomain.md)

  -   
    [Set-CsBlockedDomain](set-csblockeddomain.md)

  -   
    [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)

  -   
    [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)

  -   
    [New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)

  -   
    [Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)

  -   
    [Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

  - [Get-CsFIPSConfiguration](get-csfipsconfiguration.md)

  - [New-CsFIPSConfiguration](new-csfipsconfiguration.md)

  - [Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)

  - [Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

  -   
    [Disable-CsHostingProvider](disable-cshostingprovider.md)

  -   
    [Enable-CsHostingProvider](enable-cshostingprovider.md)

  -   
    [Get-CsHostingProvider](get-cshostingprovider.md)

  -   
    [New-CsHostingProvider](new-cshostingprovider.md)

  -   
    [Remove-CsHostingProvider](remove-cshostingprovider.md)

  -   
    [Set-CsHostingProvider](set-cshostingprovider.md)

  -   
    [Disable-CsPublicProvider](disable-cspublicprovider.md)

  -   
    [Enable-CsPublicProvider](enable-cspublicprovider.md)

  -   
    [Get-CsPublicProvider](get-cspublicprovider.md)

  -   
    [New-CsPublicProvider](new-cspublicprovider.md)

  -   
    [Remove-CsPublicProvider](remove-cspublicprovider.md)

  -   
    [Set-CsPublicProvider](set-cspublicprovider.md)

  -   
    [Test-CsFederatedPartner](test-csfederatedpartner.md)

  - [Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)

  - [New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)

  - [Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)

  - [Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

  - [Get-CsXmppGatewayConfiguration](get-csxmppgatewayconfiguration.md)

  - [Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)

  - [Test-CsXmppIM](test-csxmppim.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

