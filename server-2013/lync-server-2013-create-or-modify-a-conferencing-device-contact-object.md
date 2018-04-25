---
title: 회의 장치 대화 상대 개체 만들기 또는 수정
TOCTitle: 회의 장치 대화 상대 개체 만들기 또는 수정
ms:assetid: 62ed64be-379c-417d-9453-511881cf5604
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994035(v=OCS.15)
ms:contentKeyID: 52056856
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 장치 대화 상대 개체 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-10-02_

회의실 개체를 만들려면 먼저 장치를 나타내는 Active Directory 사용자 계정을 만듭니다. 그런 다음 **Enable-CsMeetingRoom** cmdlet을 사용하여 해당 계정이 회의 장치로 작동하도록 설정합니다. 기존 회의 장치의 속성을 변경해야 하는 경우에는 **Set-CsMeetingRoom** cmdleet을 사용합니다.

이러한 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




## 회의 장치 만들기

  - 새 회의 장치를 나타내는 Active Directory 사용자 계정을 만든 후에는 **Enable-CsMeetingRoom** cmdlet을 통해 해당 계정을 사용하도록 설정합니다. 이때 a) 회의 장치 ID, b) 회의실 계정을 포함할 등록자 풀, 그리고 c) 해당 계정에 할당할 SIP 주소를 포함해야 합니다. 예를 들면 다음과 같습니다.
    
        Enable-CsMeetingRoom -Identity "Redmond Conferencing device" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"

## 회의 장치 수정

  - 기존 회의 장치의 속성 값을 수정하려면 **Set-CsMeetingRoom** cmdlet을 사용합니다. 예를 들어 다음 명령은 회의 장치와 연결된 전화 번호(LineUri)를 업데이트합니다.
    
        Set-CsMeetingRoom -Identity "Redmond Conferencing device" -LineUri "tel:+12065551219"

자세한 내용은 [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet 및 [Set-CsMeetingRoom](set-csmeetingroom.md) cmdlet의 도움말 항목을 참고하세요.

