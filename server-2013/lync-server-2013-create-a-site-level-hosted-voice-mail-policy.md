---
title: Lync Server 2013에서 사이트 수준 호스팅된 음성 메일 정책 만들기
TOCTitle: Lync Server 2013에서 사이트 수준 호스팅된 음성 메일 정책 만들기
ms:assetid: 145892c8-a6ca-45fb-9e83-786f709dd775
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398216(v=OCS.15)
ms:contentKeyID: 49302893
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사이트 수준 호스팅된 음성 메일 정책 만들기

 

_**마지막으로 수정된 항목:** 2012-09-24_

*사이트* 정책은 정책이 정의된 사이트가 홈으로 지정된 모든 사용자에게 영향을 줄 수 있습니다. 사용자가 호스팅된 Exchange UM에 액세스할 수 있도록 구성되어 있는데 사용자별 정책이 할당되지 않은 경우에는 사이트 정책이 적용됩니다. 사이트 정책을 배포하지 않은 경우에는 글로벌 정책이 적용됩니다.

사이트 정책을 구성하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet을 참조하십시오.

  - [New-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostedVoicemailPolicy)

  - [set-cshostedvoicemailpolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostedVoicemailPolicy)

  - [Get-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostedVoicemailPolicy)

## 사이트 호스팅된 음성 메일 정책을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsHostedVoicemailPolicy cmdlet을 실행하여 정책을 만듭니다. 예를 들어 다음을 실행합니다.
    
        New-CsHostedVoicemailPolicy -Identity site:Redmond -Destination ExUM.fabrikam.com -Description "Hosted voice mail policy for the Redmond site." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
    
    이 예제에서는 사이트 범위를 포함하는 호스팅된 음성 메일 정책을 만들고 다음 매개 변수를 설정합니다.
    
      - **Identity**는 정책의 고유한 식별자를 지정합니다(범위 포함). 사이트 범위가 포함된 정책의 경우 Identity 매개 변수는 `site:`*\<이름\>* 형식으로 지정해야 합니다(예: `site:Redmond`).
    
      - **Destination**은 호스팅된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름)을 지정합니다. 이 매개 변수는 선택 사항이지만 호스팅된 음성 메일에 대해 사용자를 활성화하려는 경우 사용자에게 할당된 정책에 Destination 값이 없으면 활성화가 실패합니다.
    
      - **Description**은 옵션 매개 변수로, 정책에 대한 설명 정보를 제공합니다.
    
      - **Organization**은 Lync Server 2013 사용자가 있는 Exchange 테넌트의 쉼표로 구분된 목록을 지정합니다. 각 테넌트는 호스트된 Exchange UM 서비스에 있는 해당 테넌트의 FQDN으로 지정해야 합니다.

