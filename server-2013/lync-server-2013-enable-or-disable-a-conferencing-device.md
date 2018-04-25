---
title: 회의 장치를 사용하거나 사용하지 않도록 설정
TOCTitle: 회의 장치를 사용하거나 사용하지 않도록 설정
ms:assetid: d5140e38-d015-4706-9bde-cf2fa748c36b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994070(v=OCS.15)
ms:contentKeyID: 52056962
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 장치를 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-02-20_

**Enable-CsMeetingRoom** cmdlet과 **Disable-CsMeetingRoom** cmdlet을 사용하여 회의 장치를 사용 및 사용하지 않도록 설정합니다. 이러한 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




## 회의 장치를 사용하도록 설정

  - 회의 장치를 사용하도록 설정하려면 **Enable-CsMeetingRoom** cmdlet을 사용합니다. 회의 장치를 사용하도록 설정할 때는 a) 회의 장치 ID, b) 회의실 계정을 포함할 등록자 풀, 그리고 c) 해당 계정에 할당할 SIP 주소를 포함해야 합니다.
    
        Enable-CsMeetingRoom -Identity "Redmond Conferencing device" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"

## 회의 장치를 사용하지 않도록 설정

  - 회의 장치를 사용하지 않도록 설정하려면 **Disable-CsMeetingRoom** cmdlet을 사용합니다. 사용하지 않도록 설정할 회의 장치의 ID를 지정해야 합니다.
    
        Disable-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"

자세한 내용은 [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet 및 [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet의 도움말 항목을 참조하십시오.

