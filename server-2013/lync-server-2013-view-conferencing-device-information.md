---
title: 회의 장치 정보 보기
TOCTitle: 회의 장치 정보 보기
ms:assetid: 838bdbf8-8b68-4eb6-8fa3-45bfd5b0b1cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994043(v=OCS.15)
ms:contentKeyID: 52056897
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 장치 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-20_

Windows PowerShell 및 **Get-CsMeetingRoom** cmdlet을 사용하여 조직에서 사용하도록 구성된 회의 장치에 대한 정보를 확인할 수 있습니다. **Get-CsMeetingRoom** cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행합니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



매개 변수를 포함하지 않고 **Get-CsMeetingRoom** cmdlet을 사용하는 경우에는 모든 회의 장치에 대한 정보가 반환됩니다. 선택적 매개 변수를 포함하면 다른 방식으로 정보를 필터링할 수 있습니다. 자세한 내용은 [Get-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingRoom)의 매개 변수 섹션을 참조하십시오.


## 모든 회의 장치에 대한 정보 보기

  - 모든 회의 장치에 대한 세부 정보를 확인하려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsMeetingRoom
    
    이 cmdlet은 각 회의 장치에 대해 다음과 같은 정보를 반환합니다. 이 예에는 해당 cmdlet 실행 시 표시되는 정보 중 일부만 표시되어 있습니다.
    
        ContactOptionFlags                : 64
        OwnerUrn                          : urn:device:roomsystem
        OriginatorSid                     :
        SamAccountName                    : room12129
        UserPrincipalName                 : room1219@litwareinc.com
        FirstName                         : 
        LastName                          :
        WindowsEmailAddress               :
        Sid                               : S-1-5-21-2831376166-2963252556-2165051629-1257
        LineServerURI                     :
        AudioVideoDisabled                : False
        IPPBXSoftPhoneRoutingEnabled      : False
        RemoteCallControlTelephonyEnabled : False
        PrivateLine                       :
        AcpInfo                           : {}
        HostedVoiceMail                   :
        DisplayName                       : Room 1219

## 특정 회의 장치에 대한 정보 보기

  - 특정 회의 장치에 대한 정보를 보려면 Identity 매개 변수와 회의 장치 ID(일반적으로 Active Directory 표시 이름)를 순서대로 포함합니다. 예를 들면 다음과 같습니다.
    
        Get-CsMeetingRoom -Identity "Room 1219"

자세한 내용은 [Get-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingRoom) cmdlet의 도움말 항목을 참조하십시오.

