---
title: 신뢰할 수 있는 응용 프로그램 정보 보기
TOCTitle: 신뢰할 수 있는 응용 프로그램 정보 보기
ms:assetid: 7b916323-96fb-4308-bc95-c178de41a3d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688103(v=OCS.15)
ms:contentKeyID: 49885831
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 신뢰할 수 있는 응용 프로그램 정보 보기

 

_**마지막으로 수정된 항목:** 2015-03-30_

다음 절차에 따라 Lync Server 관리 셸에서 Lync Server 2013 관리 셸 신뢰할 수 있는 응용 프로그램 정보를 볼 수 있습니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램 정보 보기

Lync Server 관리 셸 및 **Get-CsTrustedApplication** cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램에 대한 정보를 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 신뢰할 수 있는 응용 프로그램을 보려면

  - 신뢰할 수 있는 모든 응용 프로그램을 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsConferenceDisclaimer
    
    이 명령은 신뢰할 수 있는 각 응용 프로그램에 대해 다음과 비슷한 정보를 반환합니다.
    
        Identity               : CN={5dedf4b0-a590-49b3-80cf-f16f914bbef9},CN=Application Contacts,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        RegistrarPool          : 487279971
        HomeServer             : CN=Lc Services,CN=Microsoft,CN=co1:2,CN=Pools,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        OwnerUrn               : urn:application:helpdesk
        SipAddress             : sip:RtcApplication-dbf5142f-2bb2-4c4f-9531-b7fea45c5000@litware.com
        DisplayName            :
        DisplayNumber          :
        LineURI                :
        PrimaryLanguage        : 0
        SecondaryLanguages     : {}
        EnterpriseVoiceEnabled : True
        ExUmEnabled            : False
        Enabled                : True

자세한 내용은 [Get-CsTrustedApplication](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrustedApplication)을 참조하십시오.

