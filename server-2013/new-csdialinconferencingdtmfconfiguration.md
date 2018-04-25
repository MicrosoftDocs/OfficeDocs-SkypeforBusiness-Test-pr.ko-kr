---
title: New-CsDialInConferencingDtmfConfiguration
TOCTitle: New-CsDialInConferencingDtmfConfiguration
ms:assetid: 2e373bab-fc4c-4b8b-96e7-fc23ac3bcf47
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425792(v=OCS.15)
ms:contentKeyID: 49303178
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDialInConferencingDtmfConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의에 사용되는 DTMF(Dual-Tone Multifrequency) 신호 설정의 새 컬렉션을 만듭니다. DTMF를 사용하면 전화 회의에 전화 접속한 사용자가 전화기의 키패드를 사용하여 음소거 설정 및 해제 또는 전화 회의 잠금 설정 및 해제와 같은 전화 회의 설정을 제어할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDialInConferencingDtmfConfiguration -Identity <XdsIdentity> [-AdmitAll <String>] [-AudienceMuteCommand <String>] [-CommandCharacter <String>] [-Confirm [<SwitchParameter>]] [-EnableDisableAnnouncementsCommand <String>] [-Force <SwitchParameter>] [-HelpCommand <String>] [-InMemory <SwitchParameter>] [-LockUnlockConferenceCommand <String>] [-MuteUnmuteCommand <String>] [-OperatorLineUri <String>] [-PrivateRollCallCommand <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트의 새로운 DTMF 구성 설정 집합을 만듭니다. 이 예제에서는 MuteUnmuteCommand 속성을 4로 설정하고 AudienceMuteCommand 속성을 6으로 설정합니다.

    New-CSDialInConferencingDtmfConfiguration -Identity site:Redmond -MuteUnmuteCommand 4 -AudienceMuteCommand 6

## 예제 2

예제 2에서는 Redmond 사이트의 새로운 DTMF 구성 설정 집합을 만듭니다. 이 예제에서는 AdmitAll 매개 변수를 사용하고 매개 변수 값을 Null로 설정하여 AdmitAll 속성을 사용하지 않도록 설정합니다.

    New-CSDialInConferencingDtmfConfiguration -Identity site:Redmond -AdmitAll $Null

## 예제 3

예제 3에서는 InMemory 매개 변수를 사용하여 메모리에만 나타나는 DTMF 구성 설정 컬렉션 인스턴스를 만들고 해당 설정을 수정한 다음 **Set-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 실제 컬렉션을 만듭니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 메모리에만 나타나는 새로운 DTMF 구성 설정 컬렉션 인스턴스를 만들고, 이 인스턴스를 $x라는 변수에 저장합니다. 이러한 설정은 메모리에만 존재합니다. Windows PowerShell을 닫거나 변수 $x를 삭제하면 이 설정이 사라지고 Redmond 사이트에 적용되지 않습니다.

다음 세 가지 명령은 이 "가상" DTMF 설정 컬렉션의 속성을 수정합니다. 두 번째, 세 번째, 네 번째 명령은 각각 AdmitAll, MuteUnmuteCommand 및 AudienceMuteCommand에 새 값을 할당합니다. 그런 다음 마지막 명령은 **Set-CSDialInConferencingDtmfConfiguration** cmdlet 및 Instance 매개 변수를 사용하여 $x에 저장된 가상 설정을 Redmond 사이트에 대해 구성된 실제 설정 컬렉션으로 변환합니다.

    $x = New-CSDialInConferencingDtmfConfiguration -Identity site:Redmond -InMemory
    $x.AdmitAll = $Null
    $x.MuteUnmuteCommand = 4 
    $x.AudienceMuteCommand = 6
    Set-CSDialInConferencingDtmfConfiguration -Instance $x

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 접속하여 전화 회의에 참가할 수 있습니다. 전화 접속 사용자는 비디오를 보거나 다른 전화 회의 참석자와 메신저 대화를 교환할 수 없지만 모임의 오디오 부분에는 전적으로 참여할 수 있습니다.

또한 전화 회의에 참가하는 것 외에 전화기의 키패드를 사용하여 해당 전화 회의의 선택된 부분을 관리할 수도 있습니다. 사용자가 관리할 수 있는 특정 전화 회의 설정과 관리할 수 없는 특정 전화 회의 설정은 사용자가 발표자인지 여부에 따라 다릅니다. 예를 들어 기본적으로 사용자는 키패드에서 6번 키를 눌러 음소거를 설정하거나 해제할 수 있습니다. 참가자는 모임에 참가한 다른 모든 사람의 이름을 개인적으로 재생할 수 있고, 발표자는 모든 모임 참가자에 대해 음소거를 설정 및 해제하고 누군가 전화 회의에 참가하거나 전화 회의에서 나갈 때 재생되는 알림을 설정하거나 해제하는 등의 작업을 수행할 수 있습니다.

전화기의 키패드를 사용하여 이와 같은 선택을 수행할 수 있는 기능을 DTMF(Dual-Tone Multi-Frequency) 신호라고 합니다. 특정 전화 번호로 전화를 걸었는데 "영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르십시오."라는 안내에 따라 작업을 수행해야 하는 경우 DTMF 신호를 사용한 것입니다.

Lync Server를 설치하면 전역 DTMF 설정 컬렉션이 만들어집니다. 이러한 전역 설정 외에도 **New-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 사이트별로 사용자 지정 설정을 만들 수 있습니다. 예를 들어 Redmond 사이트에 대한 설정(및 Redmond 사이트에만 적용되는 설정)의 새 컬렉션을 만들 때 6번 키 대신 4번 키를 음소거/음소거 해제 키로 사용하도록 만들 수 있습니다. 사이트 범위에서 구성하는 모든 설정은 전역 범위에서 구성하는 설정보다 우선합니다. 따라서 전역 설정에서는 음소거/음소거 해제 키로 6번 키를 사용하더라도 Redmond 사이트의 사용자는 4번 키를 음소거/음소거 해제 키로 사용하게 됩니다.

DTMF 설정 컬렉션과 전역 컬렉션은 사이트별로 하나씩만 지정할 수 있습니다. 예를 들어 ID가 site:Redmond인 컬렉션이 이미 있는 경우

New- CSDialInConferencingDtmfConfiguration –Identity site:Redmond 명령을 실행하려고 하면

site:Redmond 컬렉션이 이미 존재하므로 이 명령은 실패합니다. Redmond 사이트에 대한 설정을 수정하려면 **Set-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하거나 기존 컬렉션을 제거한 다음 site:Redmond라는 ID를 사용하는 새 컬렉션을 만듭니다.

DTMF 명령의 값을 구성할 때는 두 가지 사항에 주의해야 합니다. 먼저, 0-9의 숫자 키 및 별표(\*)만 사용할 수 있고, 키패드에 있는 다른 키(예: \# 키)는 사용할 수 없습니다. 단, CommandCharacter 키에는 예외적으로 \* 키 또는 \# 키가 허용됩니다. 둘째, 명령에는 고유한 키를 할당해야 합니다. 예를 들어 4번 키를 음소거를 설정 및 해제하거나 전화 회의 잠금을 설정 및 해제하는 데 동시에 사용할 수 없습니다. 이는 명령에 할당된 키를 수정할 때 두 가지 서로 다른 명령에 사용되는 키를 바꿔야 할 수도 있음을 의미합니다. 예를 들어 EnableDisableAnnouncementsCommand(기본값: 9)에 4번 키를 할당하려는 경우 동일한 명령에서 AudienceMuteCommand에 9번 키를 할당해야 합니다.

명령을 사용하지 않도록 설정하려면 값을 Null($Null)로 설정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDialInConferencingDtmfConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDialInConferencingDtmfConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>DTMT 구성 설정의 새 컬렉션에 할당할 고유 식별자입니다. 사이트 범위에서만 새 컬렉션을 생성할 수 있기 때문에 ID의 접두사는 항상 &quot;site:&quot;이며 그 뒤에 사이트 이름이 옵니다(예: &quot;site:Redmond&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>AdmitAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>대기실의 모든 사용자가 즉시 전화 회의에 참가하도록 허용하기 위해 눌러야 하는 키를 지정합니다. 기본값은 8입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudienceMuteCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>발표자가 전화 회의에서 다른 모든 사람의 말소리를 음소거하거나 음소거 해제(즉, 발표자를 제외한 모든 사람의 말소리를 음소거하거나 음소거 해제)할 때 누를 수 있는 키를 나타냅니다. 기본 키는 4입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CommandCharacter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>명령의 시작 부분에 입력할 키를 지정합니다. 기본 키는 별표(*)입니다. 다른 값은 #만 허용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDisableAnnouncementsCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>누군가 전화 회의에 참가하거나 전화 회의를 나갈 때마다 알림을 사용하거나 사용하지 않도록 설정하기 위해 눌러야 하는 키를 지정합니다. 기본 키는 9입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HelpCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모든 DTMF 명령의 설명을 개인적으로 재생하기 위해 눌러야 하는 키를 지정합니다. 기본 키는 1입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LockUnlockConferenceCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의를 잠그거나 잠금을 해제하기 위해 눌러야 할 키를 지정합니다. 전화 회의를 잠그면 잠금이 해제될 때까지 새 참가자가 해당 전화 회의에 참가할 수 없게 됩니다. 기본 키는 7입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MuteUnmuteCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>자신의 음성을 음소거하거나 음소거 해제할 때 누를 키를 나타냅니다. 같은 키를 사용하여 음소거와 음소거 해제 간에 전환할 수 있습니다. 기본 키는 6입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OperatorLineUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 전화기 키패드에서 *0을 누를 때마다 전화 접속 회의 자동 전화 교환이 PSTN 사용자를 연결하는 전화 번호입니다. *0을 누르면 전화 접속 회의 사용자가 교환 서비스로 연결됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateRollCallCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>각 전화 회의 참가자의 이름을 개인적으로 재생하기 위해 눌러야 하는 키를 지정합니다. 기본 키는 3입니다.</p></td>
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

없음. **New-CsDialInConferencingDtmfConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)  
[Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)  
[Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

