---
title: 'Lync Server 2013: (선택 사항) 회의 참가/나가기 알림 활성화/비활성화'
TOCTitle: (선택 사항) 회의 참가/나가기 알림 활성화/비활성화
ms:assetid: c9529568-e66c-48d8-aef2-9072f9c336ff
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398834(v=OCS.15)
ms:contentKeyID: 49305019
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (선택 사항) Lync Server 2013에서 회의 참가/나가기 알림 활성화/비활성화

 

_**마지막으로 수정된 항목:** 2012-09-30_

사용자가 전화 접속 회의에 참가하거나 회의에서 나갈 때 회의 알림 응용 프로그램에서 신호음을 재생하거나 사용자 이름을 말해 입장이나 퇴장을 알릴 수 있습니다. cmdlet를 실행하여 알림 작동 방식을 변경할 수 있습니다. 이 단계는 선택 사항입니다.

## 회의 입장 및 퇴장 알림 동작을 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 **Cs-ServerAdministrator** 또는 **CsAdministrator** 역할의 구성원으로 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령 프롬프트에서 다음을 실행합니다.
    
        Get-CsDialinConferencingConfiguration
    
    이 cmdlet는 참가자가 회의에 참가할 때 사용자 이름을 기록해야 하는지 여부 및 참가자가 전화 접속 회의에 참가하거나 회의에서 나갈 때 Lync Server에서 응답하는 방식에 대한 정보를 검색합니다.

4.  명령 프롬프트에서 다음을 실행합니다.
    
        Set-CsDialinConferencingConfiguration -Identity <identity of dial-in conferencing settings to be modified>
        [-EnableNameRecording <$true | $false>]
        [-EntryExitAnnouncementsEnabledByDefault <$true | $false>]
        [-EntryExitAnnouncementsType <UseNames | ToneOnly]
    
    **EnableNameRecording**   회의에 입장하기 전에 사용자에게 이름을 기록하도록 요청할지 여부를 결정합니다. 기본값은 "$true"이며, 익명의 사용자가 회의에 참가할 경우 이름을 얘기하라는 메시지가 표시됩니다. 인증된 참가자는 표시 이름이 대신 사용되므로 이름을 기록하지 않아도 됩니다.
    
    **EntryExitAnnouncementsEnabledByDefault**   알림이 기본적으로 설정되어 있는지 해제되어 있는지 여부를 나타냅니다. 기본값은 "$false"이며, 참가자가 회의에 참가하거나 회의에서 나갈 때 기본적으로 알림이 표시되지 않습니다. 모임 예약 시 모임 이끌이가 이 설정을 덮어쓸 수 있습니다.
    
    **EntryExitAnnouncementsType**   참가자가 알림을 사용하도록 설정된 회의에 참가하거나 이 회의에서 나갈 때마다 수행되는 동작을 나타냅니다. 기본값은 "UseNames"이며 알림이 설정된 경우 "Ken Myer 님이 회의에 참가하셨습니다." 등과 같은 알림이 제공됩니다.
    
    이러한 설정은 전역 범위나 사이트 범위에서 구성할 수 있습니다. 사이트 범위에서 구성된 설정이 전역 범위에서 구성된 설정보다 우선합니다.
    
    예를 들면 다음과 같습니다.
    
        Set-CsDialinConferencingConfiguration -Identity site:Redmond
        -EnableNameRecording $false
        -EntryExitAnnouncementsEnabledByDefault $true
        -EntryExitAnnouncementsType ToneOnly
    
    이 예에서는 레드몬드에 대해 사이트 범위에서 설정이 구성되었습니다. 알림이 설정되었지만 참가자가 회의에 참가할 때 이름을 얘기하라는 메시지가 표시되지 않습니다. 참가자가 회의에 참가하거나 회의에서 나갈 때 신호음이 재생됩니다.

