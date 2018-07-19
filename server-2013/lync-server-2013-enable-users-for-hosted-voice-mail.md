---
title: Lync Server 2013에서 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정
TOCTitle: 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정
ms:assetid: fa559f8f-ef99-43a1-b580-9e998b95efb8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413062(v=OCS.15)
ms:contentKeyID: 49305592
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정

 

_**마지막으로 수정된 항목:** 2012-09-24_

다음 절차를 사용하여 Lync Server 2013 사용자가 호스팅된 Exchange UM(통합 메시징) 서비스에서 음성 사서함을 사용하도록 설정할 수 있습니다.

자세한 내용은 계획 설명서에서 [Lync Server 2013의 호스팅된 Exchange 사용자 관리](lync-server-2013-hosted-exchange-user-management.md)을 참고하세요.

[Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUser) cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.


> [!IMPORTANT]
> Lync Server 2013 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정하려면 해당 사용자 계정에 적용할 호스팅된 음성 사서함 정책을 배포해야 합니다. 자세한 내용은 <A href="lync-server-2013-hosted-voice-mail-policies.md">Lync Server 2013의 호스팅된 음성 메일 정책</A>을 참조하십시오.



## 사용자가 호스팅된 음성 메일을 사용할 수 있도록 설정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsUser cmdlet를 실행하여 호스팅된 음성 메일에 대한 사용자 계정을 구성합니다. 예를 들어 다음을 실행합니다.
    
        Set-CsUser -HostedVoiceMail $True -Identity "contoso\kenmyer"
    
    위의 예는 다음 매개 변수를 설정합니다.
    
      - **HostedVoiceMail**은 사용자의 음성 사서함 통화를 호스팅된 Exchange UM으로 라우팅할 수 있도록 해줍니다. 또한 Microsoft Lync 2013에 신호를 보내 "음성 사서함 호출" 표시기를 켭니다.
    
      - **Identity**는 수정할 사용자 계정을 지정합니다. Identity 값은 다음 형식 중 하나를 사용하여 지정할 수 있습니다.
        
          - 사용자의 SIP 주소
        
          - 사용자의 Active Directory 사용자 계정 이름
        
          - 사용자의 도메인\\로그온 이름(예: contoso\\kenmyer)
        
          - 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer). Identity 값으로 표시 이름을 사용하는 경우 별표(\*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 Identity 값이 "\* Smith"일 경우 표시 이름이 "Smith" 문자열 값으로 끝나는 모든 사용자를 반환합니다.
        

        > [!NOTE]
        > SAM 계정 이름은 포리스트에서 고유하지 않아도 되므로 사용자의 Active Directory SAM 계정 이름을 Identity 값으로 사용할 수 없습니다.


