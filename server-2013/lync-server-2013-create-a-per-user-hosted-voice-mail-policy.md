---
title: Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 만들기
TOCTitle: Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 만들기
ms:assetid: 39018a7c-e0c3-46a2-be4e-05604ec67a50
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425867(v=OCS.15)
ms:contentKeyID: 49303329
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 만들기

 

_**마지막으로 수정된 항목:** 2012-09-24_

*사용자별* 정책은 개별 사용자, 그룹 및 연락처 개체에만 적용할 수 있습니다. 사용자별 정책을 배포하려면 하나 이상의 사용자, 그룹 또는 연락처 개체에 해당 정책을 명시적으로 할당해야 합니다. 자세한 내용은 [Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 할당](lync-server-2013-assign-a-per-user-hosted-voice-mail-policy.md)을 참조하십시오.

사용자별 호스팅된 음성 메일 정책을 사용하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet 관련 내용을 참조하십시오.

  - [New-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostedVoicemailPolicy)

  - [set-cshostedvoicemailpolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostedVoicemailPolicy)

  - [Get-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostedVoicemailPolicy)

## 사용자별 호스팅된 음성 메일 정책을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsHostedVoicemailPolicy cmdlet을 실행하여 정책을 만듭니다. 예를 들어 다음을 실행합니다.
    
        New-CsHostedVoicemailPolicy -Identity ExRedmond -Destination ExUM.fabrikam.com -Description "Hosted voice mail policy for Redmond users." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
    
    위의 예제에서는 사용자별 범위가 포함된 호스팅된 음성 메일 정책을 만들고 다음 매개 변수를 설정합니다.
    
      - **Identity**는 정책의 고유한 식별자를 지정합니다(범위 포함). 사용자별 범위가 포함된 정책의 경우 이 매개 변수 값은 ExRedmond와 같은 단순 문자열로 지정됩니다.
    
      - **Destination**은 호스팅된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름)을 지정합니다. 이 매개 변수는 선택 사항이지만 호스팅된 음성 메일에 대해 사용자를 활성화하려는 경우 사용자에게 할당된 정책에 Destination 값이 없으면 활성화가 실패합니다.
    
      - **Description**은 옵션 매개 변수로, 정책에 대한 설명 정보를 제공합니다.
    
      - **Organization**은 Lync Server 2013 사용자가 있는 Exchange 테넌트의 쉼표로 구분된 목록을 지정합니다. 각 테넌트는 호스트된 Exchange UM 서비스에 있는 해당 테넌트의 FQDN으로 지정해야 합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 사용자별 호스팅된 음성 메일 정책 할당](lync-server-2013-assign-a-per-user-hosted-voice-mail-policy.md)

