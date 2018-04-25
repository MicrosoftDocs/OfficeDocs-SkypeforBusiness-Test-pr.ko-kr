---
title: Set-CsConferencingPolicy
TOCTitle: Set-CsConferencingPolicy
ms:assetid: 2ddcf4ea-ae6c-40fa-9499-4e3b1b140e68
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425788(v=OCS.15)
ms:contentKeyID: 49303171
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConferencingPolicy

 

_**마지막으로 수정된 항목:** 2015-04-21_

기존 전화 회의 정책을 수정합니다. 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정합니다. 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsConferencingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsConferencingPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowAnnotations <$true | $false>] [-AllowAnonymousParticipantsInMeetings <$true | $false>] [-AllowAnonymousUsersToDialOut <$true | $false>] [-AllowConferenceRecording <$true | $false>] [-AllowExternalUserControl <$true | $false>] [-AllowExternalUsersToRecordMeeting <$true | $false>] [-AllowExternalUsersToSaveContent <$true | $false>] [-AllowIPAudio <$true | $false>] [-AllowIPVideo <$true | $false>] [-AllowLargeMeetings <$true | $false>] [-AllowMultiView <$true | $false>] [-AllowNonEnterpriseVoiceUsersToDialOut <$true | $false>] [-AllowOfficeContent <$true | $false>] [-AllowParticipantControl <$true | $false>] [-AllowPolls <$true | $false>] [-AllowQandA <$true | $false>] [-AllowSharedNotes <$true | $false>] [-AllowUserToScheduleMeetingsWithAppSharing <$true | $false>] [-AppSharingBitRateKb <Int64>] [-AudioBitRateKb <UInt32>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisablePowerPointAnnotations <$true | $false>] [-EnableAppDesktopSharing <None | SingleApplication | Desktop>] [-EnableDataCollaboration <$true | $false>] [-EnableDialInConferencing <$true | $false>] [-EnableFileTransfer <$true | $false>] [-EnableMultiViewJoin <$true | $false>] [-EnableOnlineMeetingPromptForLyncResources <$true | $false>] [-EnableP2PFileTransfer <$true | $false>] [-EnableP2PRecording <$true | $false>] [-EnableP2PVideo <$true | $false>] [-FileTransferBitRateKb <Int64>] [-Force <SwitchParameter>] [-MaxMeetingSize <UInt32>] [-MaxVideoConferenceResolution <CIF | VGA>] [-TotalReceiveVideoBitRateKb <Int64>] [-VideoBitRateKb <Int64>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전화 회의 정책 SalesConferencingPolicy의 속성 값을 수정합니다. 특히 AllowConferenceRecording 속성의 값을 False로 설정합니다. 이 작업을 수행하기 위해 Identity 및 AllowConferenceRecording 매개 변수와 함께 **Set-CsConferencingPolicy** cmdlet을 호출합니다.

    Set-CsConferencingPolicy -Identity SalesConferencingPolicy -AllowConferenceRecording $False

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 전화 회의 정책에 대해 동일한 두 개의 속성 값 AllowAnonymousParticipantsInMeetings 및 EnableDialInConferencing을 수정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsConferencingPolicy** cmdlet을 사용하여 사용 가능한 모든 전화 회의 정책의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 정책에 대해 AllowAnonymousParticipantsInMeetings 및 EnableDialInConferencing 값을 둘 다 False로 설정하는 **Set-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsConferencingPolicy | Set-CsConferencingPolicy -AllowAnonymousParticipantsInMeetings $False -EnableDialInConferencing $False

## 예제 3

예제 3에 표시된 명령은 사이트 범위에서 구성된 모든 전화 회의 정책에 대해 MaxVideoConferenceResolution 속성을 수정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsConferencingPolicy** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "site:\*"는 사이트 범위에서 구성된 정책의 데이터만 반환되도록 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션에 있는 각 정책의 MaxVideoConferenceResolution 속성을 "CIF"로 설정하는 **Set-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsConferencingPolicy -Filter "site:*" | Set-CsConferencingPolicy  -MaxVideoConferenceResolution CIF

## 예제 4

예제 4에서는 최대 모임 크기가 100보다 큰(-gt) 모든 정책을 검색하고 연결된 속성(MaxMeetingSize)의 값을 100으로 변경합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsConferencingPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 전화 회의 정책 컬렉션을 반환합니다. 이 컬렉션은 MaxMeetingSize가 100보다 큰 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책에 대해 MaxMeetingSize 속성을 100으로 설정하는 **Set-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsConferencingPolicy | Where-Object {$_.MaxMeetingSize -gt 100} | Set-CsConferencingPolicy -MaxMeetingSize 100 

## 자세한 정보

전화 회의는 Lync Server의 중요한 부분입니다. 전화 회의 기능을 사용하면 사용자 그룹이 온라인으로 모여 슬라이드 및 비디오 보기, 응용 프로그램 공유, 파일 교환, 기타 통신 및 공동 작업 등을 수행할 수 있기 때문입니다.

관리자가 전화 회의 및 전화 회의 설정에 대한 제어를 유지 관리하는 기능도 중요합니다. 경우에 따라 보안 문제가 발생할 수 있습니다. 기본적으로 인증되지 않은 사용자를 비롯한 모든 사용자가 모임에 참가하고 모임 중에 배포된 슬라이드나 유인물을 저장할 수 있습니다. 대역폭 문제가 발생하는 경우도 있습니다. 예를 들어 동시 모임 수가 많은 경우, 각 모임에 수백 명의 참가자가 있는 경우 및 각 모임에서 화상 공급 및 파일 공유를 사용하는 경우에 네트워크에 문제가 발생할 수 있습니다. 또한 법적인 문제가 발생할 수 있습니다. 예를 들어 모임 참가자는 기본적으로 공유 콘텐츠에 주석을 추가할 수 있지만 이러한 주석은 모임을 보관할 때 저장되지 않습니다. 조직에서 모든 전자 통신의 기록을 보관해야 하는 경우 주석을 사용하지 않도록 설정할 수 있습니다.

물론 전화 회의 설정을 관리해야 하는 것도 중요한 사항입니다. 실제로 이러한 설정을 관리하는 것은 또 다른 문제입니다. Lync Server에서는 전화 회의 정책을 사용하여 전화 회의를 관리합니다. 이전 버전의 소프트웨어에서는 이러한 정책을 모임 정책이라고 했습니다. 앞서 언급한 것처럼 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정하며, 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 전화 회의 정책은 전역 범위, 사이트 범위 또는 사용자별 범위에서 구성할 수 있습니다. 따라서 각 사용자가 사용할 수 있는 기능을 관리자가 유동적으로 결정할 수 있습니다.

정책을 만들 때 정책 속성 값을 구성할 수 있습니다. 뿐만 아니라 언제든지 **Set-CsConferencingPolicy** cmdlet을 사용하여 기존 정책의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsConferencingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferencingPolicy"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AllowAnnotations</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>참가자가 모임 중에 공유되는 콘텐츠에 대해 화면 주석을 사용하도록 허용할지 여부를 나타냅니다. 또한 이 설정은 전화 회의에서 화이트보드가 허용되는지 여부를 결정합니다. 기본값은 True입니다.</p>
<p>주석은 다른 모임 콘텐츠와 함께 보관되지 않습니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 주석이 포함되지 않습니다. 그러나 주석이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowAnonymousParticipantsInMeetings</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>익명 사용자가 모임에 참가할 수 있는지 여부를 나타냅니다. False로 설정하면 인증된 사용자(즉, 사용자의 Active Directory 도메인 서비스 또는 페더레이션 파트너의 Active Directory에 로그온한 사용자)만 모임에 참가할 수 있습니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 익명 참가자가 허용되지 않습니다. 그러나 익명 참가자가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowAnonymousUsersToDialOut</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>익명 사용자(예: 인증되지 않은 사용자)가 전화 접속 전화를 사용하여 전화 회의에 참가할 수 있는지 여부를 나타냅니다. 전화 접속 전화를 사용하면 전화 회의 서버에서 사용자에게 전화를 겁니다. 사용자가 전화를 받으면 전화 회의에 참가하게 됩니다.</p>
<p>전화 접속 회의는 이 설정이 False로 설정된 경우에도 허용됩니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에서 익명 참가자가 전화를 걸어 회의에 참가하는 것이 허용되지 않습니다. 그러나 사용자는 익명 사용자가 전화를 걸어 참가할 수 있는 다른 전화 회의에 참가할 수 있습니다.</p>
<p>기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowConferenceRecording</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 모임을 기록할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p>
<p>이 설정은 전화 회의 참가 중인 모든 사용자에게 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowExternalUserControl</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 사용자(익명 사용자 또는 페더레이션 사용자)가 공유 응용 프로그램 또는 데스크톱을 제어할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p>
<p>이 설정은 전화 회의 및 피어 투 피어 통신 세션 둘 다에 대해 사용자 수준에서 적용됩니다. 즉, 세션의 일부 사용자는 공유 응용 프로그램 또는 데스크톱에 대한 제어 권한을 외부 사용자에게 부여할 수 있고 다른 사용자는 제어 권한을 부여할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowExternalUsersToRecordMeeting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 사용자(익명 사용자 또는 페더레이션 사용자)가 모임을 기록할 수 있는지 여부를 나타냅니다. 기본값은 False입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에서 외부 사용자의 전화 회의 기록이 허용되지 않습니다. 그러나 외부 사용자의 모임 기록이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p>
<p>이 설정은 AllowConferenceRecording 속성을 True로 설정한 경우에만 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowExternalUsersToSaveContent</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 사용자(즉, 현재 네트워크에 로그온하지 않은 사용자)가 유인물, 슬라이드 및 기타 모임 콘텐츠를 저장할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에서 외부 사용자의 콘텐츠 저장이 허용되지 않습니다. 그러나 외부 사용자의 콘텐츠 저장이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowIPAudio</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임에서 컴퓨터 오디오가 허용되는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 IP 오디오가 허용되지 않습니다. 그러나 IP 오디오가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowIPVideo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임에서 컴퓨터 비디오가 허용되는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 IP 비디오가 허용되지 않습니다. 그러나 IP 비디오가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowLargeMeetings</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 모든 온라인 모임이 &quot;대규모 모임&quot;으로 처리됩니다. 대규모 모임에서는 참가자에게 발송되는 알림의 수와 기본적으로 전송되는 모임 명단의 크기에 제한이 적용됩니다.</p>
<p>기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowMultiView</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 다중 뷰를 사용할 수 있는 전화 회의(클라이언트가 지정된 전화 회의 중에 여러 비디오 스트림을 수신할 수 있음)를 예약할 수 있습니다. 이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 다중 뷰를 포함할 수 없습니다. 그러나 다중 뷰가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowNonEnterpriseVoiceUsersToDialOut</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>Enterprise Voice에 대해 사용하도록 설정되지 않은 사용자가 전화 접속 전화를 사용하여 전화 회의에 참가할 수 있는지 여부를 나타냅니다. 전화 접속 전화를 사용하면 전화 회의 서버에서 사용자에게 전화를 겁니다. 사용자가 전화를 받으면 전화 회의에 참가하게 됩니다.</p>
<p>전화 접속 회의는 이 설정이 False로 설정된 경우에도 허용됩니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에서는 Enterprise Voice에 대해 사용하도록 설정되지 않은 사용자가 전화 걸기를 통해 회의에 참가할 수 없습니다. 그러나 사용자는 Enterprise Voice에 대해 사용하도록 설정되지 않은 사용자가 전화 걸기를 통해 참가할 수 있는 다른 전화 회의에는 참가할 수 있습니다.</p>
<p>기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowOfficeContent</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False로 설정하면 사용자가 전화 회의에서 Office 콘텐츠를 사용할 수 없게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowParticipantControl</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임 참가자가 모임 중에 공유되는 응용 프로그램 또는 바탕 화면을 제어할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 참가자 제어가 허용되지 않습니다. 그러나 참가자 제어가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPolls</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 모임 중에 온라인 설문 조사를 수행할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 폴링이 허용되지 않습니다. 그러나 폴링이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowQandA</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 자신이 구성한 모든 온라인 회의에 질문과 대답 관리자를 포함할 수 있습니다. False로 설정하면 사용자는 자신이 구성한 모든 회의에 질문과 대답 관리자를 포함할 수 없습니다.</p>
<p>이 설정은 회의를 구성한 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 회의에서 질문과 대답 관리자를 사용할 수 없습니다. 하지만 사용자는 폴링이 허용된 다른 회의에서 질문과 대답 관리자를 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowSharedNotes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 전화 회의에 연결된 열려 있는 모든 OneNote 전자 필기장이 전화 회의 참가자, 전화 회의 중에 공유되는 콘텐츠에 대한 세부 사항 등의 정보로 자동 업데이트됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowUserToScheduleMeetingsWithAppSharing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 응용 프로그램 공유를 포함하는 모임을 구성할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 응용 프로그램 공유가 허용되지 않습니다. 그러나 응용 프로그램 공유가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingBitRateKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>응용 프로그램 공유에 사용되는 비트 전송률(킬로비트)입니다. 기본값은 50000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBitRateKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>오디오 전송에 사용되는 비트 전송률(킬로비트)입니다. 오디오 비트 전송률은 20에서 200(포함) 사이의 정수일 수 있으며, 기본값은 200입니다.</p>
<p>이 설정은 전화 회의 및 피어 투 피어 통신 세션 둘 다에 대해 사용자 수준에서 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 전화 회의 정책에 대한 추가 텍스트를 제공할 수 있습니다. 예를 들어 Description에서 정책이 할당되어야 하는 사용자를 표시할 수도 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisablePowerPointAnnotations</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 사용자가 전화 회의에서 사용되는 PowerPoint 슬라이드에 주석을 추가할 수 없습니다. 그러나 AllowAnnotations 속성의 값에 따라 사용자가 다른 화이트보드 기능에 액세스할 수는 있습니다. 기본값은 False(PowerPoint 주석이 허용됨)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableAppDesktopSharing</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.EnableAppDesktopSharing</p></td>
<td><p>참가자가 모임 중에 응용 프로그램(또는 해당 데스크톱)을 공유할 수 있는지 여부를 나타냅니다. 허용되는 값은 다음과 같습니다.</p>
<p>Desktop. 사용자가 전체 데스크톱을 공유할 수 있습니다.</p>
<p>SingleApplication. 사용자가 단일 응용 프로그램을 공유할 수 있습니다.</p>
<p>없음. 사용자가 응용 프로그램이나 데스크톱을 공유할 수 없습니다.</p>
<p>이 설정은 사용자 수준에서 적용됩니다. 즉, 전화 회의에 참가한 일부 사용자는 자신의 데스크톱 또는 응용 프로그램을 공유할 수 있고, 같은 전화 회의의 다른 사용자는 그렇게 할 수 없습니다.</p>
<p>기본값은 Desktop입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDataCollaboration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 화이트보드 기능, 주석 등의 데이터 공동 작업 활동을 포함하는 모임을 구성할 수 있는지 여부를 나타냅니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 데이터 공동 작업이 허용되지 않습니다. 그러나 데이터 공동 작업이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDialInConferencing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 PSTN(공중 전화망) 전화로 전화를 걸어 모임에 참가할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 전화 접속 회의가 허용되지 않습니다. 그러나 전화 접속 회의가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableFileTransfer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임 중에 모든 모임 참가자에 대한 파일 전송이 허용되는지 여부를 나타냅니다. 기본값은 True입니다.</p>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. False로 설정하면 이 정책의 영향을 받는 사용자가 만든 전화 회의에 파일 전송이 허용되지 않습니다. 그러나 파일 전송이 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMultiViewJoin</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 클라이언트가 다중 뷰(클라이언트가 전화 회의 중에 여러 비디오 스트림을 수신할 수 있음)를 사용하여 전화 회의 참가를 시도합니다. 참가하려는 전화 회의에서 다중 뷰가 허용되지 않으면 이 매개 변수는 무시됩니다. 이 설정은 전화 회의 및 피어 투 피어 통신 세션 둘 다에 대해 사용자 수준에서 적용됩니다. 즉, 세션에서 일부 사용자는 여러 비디오 스트림을 수신하도록 허용되지만 동일한 전화 회의의 나머지 사용자에게는 여러 비디오 스트림 수신이 허용되지 않을 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableOnlineMeetingPromptForLyncResources</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 Outlook에서 모임을 예약할 때마다 방문자(예: 회의실)를 포함하라는 메시지가 나타납니다. 이는 온라인에서 개최하는 모임에 유용합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableP2PFileTransfer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모임 중에 모든 피어-투-피어 파일 전송(즉, 일부 참가자에게만 보내는 파일 전송)을 허용할지 여부를 나타냅니다. 기본값은 True($True)입니다.</p>
<p>이 설정은 사용자 수준에서 적용됩니다. 즉, 피어-투-피어 통신 세션의 한 사용자는 파일을 전송할 수 있고 다른 사용자는 파일을 전송할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableP2PRecording</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 피어-투-피어 전화 회의 세션을 기록할 수 있습니다. 기본값은 False입니다.</p>
<p>이 설정은 사용자 수준에서 적용됩니다. 즉, 피어-투-피어 통신 세션의 한 사용자는 세션을 기록할 수 있고 다른 사용자는 세션을 기록할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableP2PVideo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 피어-투-피어 비디오 회의 세션에 참가할 수 있습니다. 기본값은 False입니다.</p>
<p>이 설정은 사용자 수준에서 적용됩니다. 즉, 피어-투-피어 통신 세션의 한 사용자는 비디오를 사용할 수 있고 다른 사용자는 비디오를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FileTransferBitRateKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>파일 전송에 사용되는 비트 전송률(킬로비트)입니다. 기본값은 50000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 전화 회의 정책의 고유 식별자입니다. 전화 회의 정책은 전역, 사이트 또는 사용자별 범위에서 구성할 수 있습니다. 전역 정책을 수정하려면 -Identity global 구문을 사용합니다. 사이트 정책을 수정하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 또한 사용자별 정책을 수정하려면 -Identity SalesConferencingPolicy와 유사한 구문을 사용합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. ID를 지정하지 않으면 <strong>Set-CsConferencingPolicy</strong> cmdlet에서 자동으로 전역 전화 회의 정책을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>모임 정책</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxMeetingSize</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>모임에 참가할 수 있는 최대 사용자 수를 나타냅니다. 최대 참가자 수에 도달한 후에는 다른 사람이 모임에 참가하려고 시도할 때 모임 정원이 찼다는 공지와 함께 참가가 거부됩니다. 이 값에 지정된 참가자 수는 32비트 정수(1에서 4,294,967,295 사이 값)일 수 있지만 권장 크기는 2에서 250까지이며 기본값은 250입니다.</p>
<div class="alert">

> [!NOTE]
> Microsoft 테스트를 기반으로 공유 풀 배포의 최대값은 250입니다. 참가자가 250명 이상인 모임을 지원하는 방법에 대한 자세한 내용은 "대규모 모임을 위한 Microsoft Lync Server 2010 지원(<A href="http://go.microsoft.com/fwlink/?linkid=242073">http://go.microsoft.com/fwlink/?linkID=242073</A>)을 참고하세요.


</div>
<p>이 설정은 전화 회의를 주최하는 사용자에게 적용됩니다. 이 정책의 영향을 받는 사용자가 만든 전화 회의에는 지정된 수보다 많은 참가자가 허용되지 않습니다. 그러나 추가 참가자가 허용되는 다른 전화 회의에는 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxVideoConferenceResolution</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MaxVideoConferenceResolution</p></td>
<td><p>모임 비디오의 최대 해상도를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>CIF. CIF(Common Intermediate Format)의 해상도는 352 x 288픽셀입니다.</p>
<p>VGA. VGA의 해상도는 640 x 480픽셀입니다.</p>
<p>기본값은 VGA입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TotalReceiveVideoBitRateKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>전화 회의에서 사용되는 모든 비디오에 대해 허용되는 최대 비트 속도(초당 킬로바이트), 즉 모든 비디오 스트림의 비트 속도를 합한 값을 나타냅니다. 기본값은 초당 50000킬로비트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBitRateKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>비디오 전송에 사용되는 비트 전송률(킬로비트)입니다. 기본값은 50000입니다.</p>
<p>이 설정은 전화 회의 및 피어 투 피어 통신 세션 둘 다에 대해 사용자 수준에서 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy 개체입니다. **Set-CsConferencingPolicy** cmdlet은 모임 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsConferencingPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferencingPolicy](get-csconferencingpolicy.md)  
[Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)  
[Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)

