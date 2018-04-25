---
title: New-CsDialInConferencingConfiguration
TOCTitle: New-CsDialInConferencingConfiguration
ms:assetid: ac0b6e22-3883-4884-aa94-18f4029c7f1e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412816(v=OCS.15)
ms:contentKeyID: 49304696
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDialInConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의 구성 설정의 새 컬렉션을 만듭니다. 이러한 설정은 전화 접속 회의에 입장 또는 퇴장할 때 Lync Server에서 응답하는 방법을 결정합니다. 이 정보는 참가자가 회의에 입장할 때 자신의 이름을 기록해야 하는지 여부와 시스템에서 입장 또는 퇴장을 알리는 방법(또는 알리는지 여부)에 관계없이 반환됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDialInConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableNameRecording <$true | $false>] [-EntryExitAnnouncementsEnabledByDefault <$true | $false>] [-EntryExitAnnouncementsType <UseNames | ToneOnly>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 적용되는 전화 접속 회의 구성 설정의 새 컬렉션을 만듭니다. 또한 선택적 매개 변수 EnableNameRecording을 포함하여 EnableNameRecording 속성을 False로 설정합니다.

    New-CSDialInConferencingConfiguration -Identity site:Redmond -EnableNameRecording $False

## 예제 2

예제 2에서는 처음에는 메모리에만 존재하는 전화 접속 회의 구성 설정의 새 컬렉션을 만들기 위해 InMemory 매개 변수를 사용합니다. 이 작업을 수행하기 위해 먼저 **New-CSDialInConferencingConfiguration** cmdlet을 호출하고 InMemory 매개 변수를 지정하여 변수 $x에 저장되는 가상 설정 컬렉션을 만듭니다. 이 컬렉션의 ID에는 site:Redmond를 지정합니다. 가상 컬렉션을 만든 다음 두 번째 줄에서 EnableNameRecording 속성의 값을 수정합니다. 마지막으로 예제의 세 번째 줄에서는 **Set-CSDialInConferencingConfiguration** cmdlet을 호출하여 $x에 저장된 가상 구성 설정을 Redmond 사이트에 적용되는 실제 설정의 컬렉션으로 변환합니다.

    $x = New-CSDialInConferencingConfiguration -Identity site:Redmond -InMemory
    $x.EnableNameRecording = $False
    Set-CSDialInConferencingConfiguration -Instance $x

## 자세한 정보

사용자가 전화 접속 회의에 입장(또는 퇴장)할 때 Lync Server는 다양한 방식으로 응답할 수 있습니다. 예를 들어 전화 회의에 입장하기 전에 참가자에게 자신의 이름을 기록하도록 요청할 수 있습니다. 마찬가지로 관리자는 전화 접속 참가자가 전화 회의에 퇴장 또는 입장할 때 Lync Server에서 다른 사람에게 이를 알리도록 할지 여부를 결정할 수 있습니다.

이러한 회의 "참가 동작"은 전화 접속 회의 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위 또는 사이트 범위에 구성할 수 있습니다. 사이트 범위에서 구성된 설정이 전역 범위에서 구성된 설정보다 우선합니다. Lync Server를 처음 설치하면 전역 범위의 전화 접속 구성 설정 한 개만 사용할 수 있지만 **New-CSDialInConferencingConfiguration** cmdlet을 사용하여 사이트 범위에 새 설정을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDialInConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDialInConferencingConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Xds ID</p></td>
<td><p>만들 전화 접속 회의 구성 설정의 ID를 지정합니다. 이러한 설정은 사이트 범위에서만 만들어질 수 있으므로 접두사 &quot;site:&quot; 뒤에 사이트 이름이 오는 -Identity site:Redmond와 유사한 구문을 사용합니다.</p>
<p>전화 접속 회의 구성 설정은 사이트당 한 개만 사용할 수 있습니다. 샘플 명령은 ID가 site:Redmond인 설정의 컬렉션이 이미 존재하는 경우 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableNameRecording</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>회의에 입장하기 전에 사용자에게 이름을 기록하도록 요청할지 여부를 지정합니다. 이름 기록을 요구하려면 True($True)로 설정하고, 이름 기록을 건너뛰려면 False($False)로 설정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EntryExitAnnouncementsEnabledByDefault</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 참가자가 회의에 입장 또는 퇴장할 때마다 알림이 재생됩니다. False(기본값)로 설정하면 입장 및 퇴장 알림이 재생되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EntryExitAnnouncementsType</em></p></td>
<td><p>선택</p></td>
<td><p>입장/퇴장 알림 유형</p></td>
<td><p>참가자가 회의에 입장 또는 퇴장할 때마다 시스템에서 수행하는 작업을 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>UseNames. 참가자가 회의에 입장 또는 퇴장할 때마다 이름을 호명합니다(예: &quot;Ken Myer님이 회의에서 퇴장하셨습니다&quot;).</p>
<p>ToneOnly. 참가자가 회의에 입장 또는 퇴장할 때마다 신호음이 재생됩니다.</p>
<p>기본값은 UseNames입니다. EntryExitAnnouncementsEnabledByDefault 속성이 True로 설정된 경우에만 알림이 재생됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsDialInConferencingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

