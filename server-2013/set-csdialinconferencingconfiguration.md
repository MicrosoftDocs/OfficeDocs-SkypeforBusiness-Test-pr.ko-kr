---
title: Set-CsDialInConferencingConfiguration
TOCTitle: Set-CsDialInConferencingConfiguration
ms:assetid: 3300343f-c075-4b4f-aaa4-091dbf1fcd90
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425825(v=OCS.15)
ms:contentKeyID: 49303245
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDialInConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 전화 접속 회의에 입장 또는 퇴장할 때 Lync Server에서 응답하는 방법을 지정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDialInConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDialInConferencingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableNameRecording <$true | $false>] [-EntryExitAnnouncementsEnabledByDefault <$true | $false>] [-EntryExitAnnouncementsType <UseNames | ToneOnly>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트의 전화 접속 구성 설정의 EntryExitAnnoucements 속성을 수정합니다. 이 경우에는 EntryExitAnnouncementsType 속성을 ToneOnly로 설정합니다.

    Set-CsDialInConferencingConfiguration -Identity site:Redmond -EntryExitAnnouncementsType "ToneOnly"

## 예제 2

예제 2에서는 조직에서 사용 중인 모든 전화 접속 회의 구성 설정을 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingConfiguration** cmdlet을 사용하여 모든 전화 접속 회의 설정의 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 컬렉션에 있는 각 항목의 EnableNameRecording 속성을 True($True)로 설정하는 **Set-CsDialInConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingConfiguration | Set-CsDialInConferencingConfiguration -EnableNameRecording $True

## 예제 3

예제 3에서는 사이트 범위에 구성된 모든 전화 접속 회의 설정을 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에 구성된 모든 설정의 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환되는 데이터를 ID가 문자열 값 "site:\*"로 시작하는 설정으로 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션에 있는 각 항목의 EnableNameRecording 속성과 EntryExitAnnouncementsType 속성을 수정하는 **Set-CsDialInConferencingConfiguration** cmdlet에 파이프됩니다. 명령 실행이 완료되면 사이트 범위에 구성된 모든 전화 접속 회의 설정의 EnableNameRecording 속성은 True로 설정되고 EntryExitAnnoucements 속성은 "UseNames"로 설정됩니다.

    Get-CsDialInConferencingConfiguration -Filter "site:*" | Set-CsDialInConferencingConfiguration -EnableNameRecording $True -EntryExitAnnouncementsType "UseNames"

## 자세한 정보

사용자가 전화 접속 회의에 입장(또는 퇴장)할 때 Lync Server는 다양한 방식으로 응답할 수 있습니다. 예를 들어 전화 회의에 입장하기 전에 참가자에게 자신의 이름을 기록하도록 요청할 수 있습니다. 마찬가지로 관리자는 전화 접속 참가자가 전화 회의에 퇴장 또는 입장할 때 Lync Server에서 다른 사람에게 이를 알리도록 할지 여부를 결정할 수 있습니다.

이러한 전화 회의 "참가 동작"은 전화 접속 회의 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위 또는 사이트 범위에 구성할 수 있습니다. Lync Server을 처음 설치하면 전역 범위의 전화 접속 구성 설정 한 개만 사용할 수 있지만 **New-CsDialInConferencingConfiguration** cmdlet을 사용하면 사이트 범위에 새 설정을 만들 수 있습니다. 또한 **Set-CsDialInConferencingConfiguration** cmdlet을 사용하여 전역 또는 사이트 범위의 이러한 구성 설정을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDialInConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDialInConferencingConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableNameRecording</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>전화 회의에 입장하기 전에 사용자에게 이름을 기록하도록 요청할지 여부를 지정합니다. 이름 기록을 사용하도록 설정하려면 True로 설정하고, 이름 기록을 건너뛰려면 False로 설정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EntryExitAnnouncementsEnabledByDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 참가자가 전화 회의에 입장 또는 퇴장할 때마다 알림이 재생됩니다. False(기본값)로 설정하면 입장 및 퇴장 알림이 재생되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EntryExitAnnouncementsType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.EntryExitAnnouncementsType</p></td>
<td><p>참가자가 전화 회의에 입장 또는 퇴장할 때마다 시스템에서 수행하는 작업을 나타냅니다. EntryExitAnnoucementsEnabledByDefault가 True로 설정된 경우에만 알림을 만들 수 있습니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>UseNames. 참가자가 전화 회의에 입장 또는 퇴장할 때마다 이름을 호명합니다(예: &quot;Ken Myer님이 전화 회의에서 퇴장하셨습니다&quot;).</p>
<p>ToneOnly. 참가자가 전화 회의에 입장 또는 퇴장할 때마다 신호음이 재생됩니다.</p>
<p>기본값은 UseNames입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 전화 접속 회의 구성 설정의 ID를 지정합니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체입니다. **Set-CSDialInConferencingConfiguration** cmdlet은 전화 접속 회의 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CSDialInConferencingConfiguration** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)  
[New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)

