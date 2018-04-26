---
title: 회의 Cmdlet
TOCTitle: 회의 Cmdlet
ms:assetid: 7ff94637-6319-4c45-9230-be34e8d81ede
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398641(v=OCS.15)
ms:contentKeyID: 49304187
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-10-09_

Microsoft Lync Server 2013에서 사용자는 두 가지 서로 다른 방법 즉, Lync 2013과 같은 회의 응용 프로그램을 사용하거나 전화기로 전화를 걸어 회의에 참가할 수 있습니다. 전화 접속 사용자는 슬라이드를 보거나 인스턴트 메시지를 교환하는 등의 작업을 할 수 없지만 회의의 오디오 부분에는 완벽하게 참가할 수 있습니다.

## 회의 Cmdlet

**CsDialInConferencing** cmdlet은 사용자가 회의에 참가하기 위해 전화를 걸 수 있는 전화 번호를 지정하는 것에서부터 사용자가 회의에 참가한 후 키패드 명령을 사용(예: 전화를 음소거 또는 음소거 해제하기 위해 6을 누르는 것)할 수 있는 것에 이르기까지 모든 것을 포함하는 전화 접속 회의 속성을 구성하는 데 사용됩니다. 회의의 다른 대부분의 기능(예: 사용자가 회의를 녹음/녹화하는 것, 사용자가 회의 도중 응용 프로그램을 공유하는 것 등)은 **CsConferencingPolicy** cmdlet을 사용하여 관리합니다.

**[전화 접속 회의 Cmdlet](lync-server-2013-dial-in-conferencing-cmdlets.md)**

  -   
    [Get-CsConferenceDirectory](get-csconferencedirectory.md)

  -   
    [Move-CsConferenceDirectory](move-csconferencedirectory.md)

  -   
    [New-CsConferenceDirectory](new-csconferencedirectory.md)

  -   
    [Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

  -   
    [Test-CsDialInConferencing](test-csdialinconferencing.md)

  -   
    [Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)

  -   
    [New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)

  -   
    [Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)

  -   
    [Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

  -   
    [Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)

  -   
    [New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)

  -   
    [Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)

  -   
    [Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

  -   
    [Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)

  -   
    [New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)

  -   
    [Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)

  -   
    [Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

  -   
    [Get-CsDialInConferencingLanguageList](get-csdialinconferencinglanguagelist.md)

**[웹 회의 Cmdlet](lync-server-2013-web-conferencing-cmdlets.md)**

  -   
    [Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)

  -   
    [Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

  -   
    [Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

  -   
    [Set-CsConferenceServer](set-csconferenceserver.md)

  -   
    [Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)

  -   
    [New-CsConferencingConfiguration](new-csconferencingconfiguration.md)

  -   
    [Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)

  -   
    [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

  -   
    [Get-CsConferencingPolicy](get-csconferencingpolicy.md)

  -   
    [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)

  -   
    [New-CsConferencingPolicy](new-csconferencingpolicy.md)

  -   
    [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)

  -   
    [Set-CsConferencingPolicy](set-csconferencingpolicy.md)

  -   
    [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)

  -   
    [New-CsMeetingConfiguration](new-csmeetingconfiguration.md)

  -   
    [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)

  -   
    [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

  - [Disable-CsMeetingRoom](disable-csmeetingroom.md)

  - [Enable-CsMeetingRoom](enable-csmeetingroom.md)

  - [Get-CsMeetingRoom](get-csmeetingroom.md)

  - [Move-CsMeetingRoom](move-csmeetingroom.md)

  - [Set-CsMeetingRoom](set-csmeetingroom.md)

  -   
    [Test-CsASConference](test-csasconference.md)

  -   
    [Test-CsAVConference](test-csavconference.md)

  -   
    [Test-CsDataConference](test-csdataconference.md)

  -   
    [Test-CsWebApp](test-cswebapp.md)

  -   
    [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

  -   
    [Test-CsWebScheduler](test-cswebscheduler.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

