---
title: Set-CsDialInConferencingDtmfConfiguration
TOCTitle: Set-CsDialInConferencingDtmfConfiguration
ms:assetid: cc22353e-6c14-49b1-bf23-f952c100bfd8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398860(v=OCS.15)
ms:contentKeyID: 49305055
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDialInConferencingDtmfConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의에 사용되는 DTMF(Dual-Tone Multifrequency) 신호 설정을 수정합니다. DTMF를 사용하면 전화 회의에 전화 접속한 사용자가 전화기의 키패드를 사용하여 음소거 설정 및 해제 또는 전화 회의 잠금 설정 및 해제와 같은 전화 회의 설정을 제어할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDialInConferencingDtmfConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDialInConferencingDtmfConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AdmitAll <String>] [-AudienceMuteCommand <String>] [-CommandCharacter <String>] [-Confirm [<SwitchParameter>]] [-EnableDisableAnnouncementsCommand <String>] [-Force <SwitchParameter>] [-HelpCommand <String>] [-LockUnlockConferenceCommand <String>] [-MuteUnmuteCommand <String>] [-OperatorLineUri <String>] [-PrivateRollCallCommand <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 알림을 사용하거나 사용하지 않도록 설정하는 명령에 할당된 키(기본값: 9) 및 전역 DTMF 설정에 대해 음소거를 설정 및 해제하는 명령에 할당된 키패드 키(기본값: 4)를 스왑합니다. 이 작업을 수행하기 위해 매개 변수 값 4가 지정된 EnableDisableAnnoucementsCommand와 값 9가 지정된 AudienceMuteCommand의 두 가지 매개 변수를 사용합니다. ID를 지정하지 않았으므로 이러한 변경 내용은 전역 DTMF 설정에 영향을 줍니다.

    Set-CsDialInConferencingDtmfConfiguration -Identity global -EnableDisableAnnouncementsCommand 4 -AudienceMuteCommand 9

## 예제 2

예제 2에 표시된 명령은 첫 번째 예제에 표시된 명령의 변형입니다. 그러나 이 예제의 경우 변경 내용은 ID가 site:Redmond인 DTMF 설정에만 영향을 줍니다.

    Set-CsDialInConferencingDtmfConfiguration -Identity site:Redmond -EnableDisableAnnouncementsCommand 4 -AudienceMuteCommand 9

## 예제 3

예제 3에 표시된 명령은 Redmond 사이트에 대해 전화 회의에 참가한 모든 사람의 목록을 재생하는 롤콜(roll call) 명령을 비활성화합니다. 이 명령을 비활성화하기 위해 매개 변수 값이 $Null로 설정된 PrivateRollCallCommand 매개 변수가 포함됩니다. 즉, 명령에 아무 키패드 키도 연결되지 않으므로 사용자가 명령을 사용할 수 없게 됩니다.

    Set-CsDialInConferencingDtmfConfiguration -Identity "site:Redmond" -PrivateRollCallCommand $Null

## 예제 4

예제 4는 예제 3의 변형입니다. 이 예제에서는 사이트 범위에서 구성된 모든 DTMF 설정에 대해 롤콜(roll call) 명령을 비활성화합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDialInConferencingDtmfConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에 구성된 모든 설정 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환된 데이터를 문자 "site:"으로 시작하는 ID를 가진 설정으로 제한합니다. 필터링된 컬렉션은 PrivateRollCallCommand 속성 값을 Null($Null)로 설정하는 **Set-CsDialInConferencingDtmfConfiguration** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingDtmfConfiguration -Filter "site:*" | Set-CsDialInConferencingDtmfConfiguration -PrivateRollCallCommand $Null

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 접속하여 전화 회의에 참가할 수 있습니다. 전화 접속 사용자는 비디오를 보거나 다른 전화 회의 참석자와 메신저 대화를 교환할 수 없지만 모임의 오디오 부분에는 전적으로 참여할 수 있습니다.

또한 전화 회의에 참가하는 것 외에 전화기의 키패드를 사용하여 해당 전화 회의의 선택된 부분을 관리할 수도 있습니다. 사용자가 관리할 수 있는 특정 전화 회의 설정과 관리할 수 없는 특정 전화 회의 설정은 사용자가 발표자인지 여부에 따라 다릅니다. 예를 들어 기본적으로 사용자는 키패드에서 6번 키를 눌러 음소거를 설정하거나 해제할 수 있습니다. 참가자는 모임에 참가한 다른 모든 사람의 이름을 개인적으로 재생할 수 있고, 발표자는 모든 모임 참가자에 대해 음소거를 설정 및 해제하고 누군가 전화 회의에 참가하거나 전화 회의에서 나갈 때 재생되는 알림을 설정하거나 해제하는 등의 작업을 수행할 수 있습니다.

전화기의 키패드를 사용하여 이와 같은 선택을 수행할 수 있는 기능을 DTMF(Dual-Tone Multifrequency) 신호라고 합니다. 특정 전화 번호로 전화를 걸었는데 "영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르십시오."라는 안내에 따라 작업을 수행해야 하는 경우 DTMF 신호를 사용한 것입니다.

**Set-CsDialInConferencingDtmfConfiguration** cmdlet을 사용하면 Lync Server 전화 접속 회의에서 지원되는 명령을 트리거하는 데 사용되는 키를 수정할 수 있습니다.

DTMF 명령을 수정할 때 두 가지 사항에 유의해야 합니다. 첫째, 0부터 9까지의 숫자 키만 사용할 수 있습니다. 키패드에 있는 다른 키(예: \# 키)는 허용되지 않습니다. 이러한 규칙에는 한 가지 예외가 있습니다. CommandCharacter 매개 변수에는 별표 키(\*) 또는 파운드 키(\#)만 사용할 수 있습니다. CommandCharacter 매개 변수에는 숫자 값을 할당할 수 없습니다. 그러나 다른 모든 명령 매개 변수는 숫자 값만 허용합니다.

둘째, 명령에는 고유한 키를 할당해야 합니다. 예를 들어 4번 키를 음소거를 설정 및 해제하거나 전화 회의 잠금을 설정 및 해제하는 데 동시에 사용할 수 없습니다. 따라서 명령에 할당된 키를 수정할 때는 두 가지 명령에 사용되는 키를 스왑하는 것이 좋습니다. 예를 들어 EnableDisableAnnouncementsCommand(기본값: 9)에 4번 키를 할당하려는 경우 동일한 명령에서 AudienceMuteCommand에 9번 키를 할당하는 것이 좋습니다.

명령을 사용하지 않도록 설정하려면 값을 Null($Null)로 설정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDialInConferencingDtmfConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDialInConferencingDtmfConfiguration"}

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
<td><p><em>AdmitAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>대기실의 모든 사용자가 즉시 전화 회의에 참가하도록 허용하기 위해 눌러야 하는 키를 지정합니다. 기본값은 8입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudienceMuteCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>발표자가 전화 회의의 모든 참가자들을 음소거하기 위해 누를 수 있는 키를 지정합니다. 즉, 발표자를 제외한 모든 사람이 음소거됩니다. 기본 키는 4입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CommandCharacter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>명령의 시작 부분에 입력할 키를 지정합니다. 기본 키는 별표(*)입니다. 허용되는 유일한 다른 값은 파운드 키(#)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDisableAnnouncementsCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>누군가 전화 회의에 참가하거나 전화 회의를 나갈 때마다 알림을 사용하거나 사용하지 않도록 설정하기 위해 눌러야 하는 키를 지정합니다. 기본 키는 9입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HelpCommand</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모든 DTMF 명령의 설명을 개인적으로 재생하기 위해 눌러야 하는 키를 지정합니다. 기본 키는 1입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 DTMF 설정의 컬렉션에 대한 고유 식별자를 지정합니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p>
<p>이 매개 변수가 지정되지 않으면 <strong>Set-CsDialInConferencingDtmfConfiguration</strong> cmdlet이 전역 DTMF 설정을 수정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>전화 접속 회의 DTMF 구성 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체입니다. **Set-CsDialInConferencingDtmfConfiguration** cmdlet은 전화 접속 회의 DTMF 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsDialInConferencingDtmfConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)  
[New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)  
[Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)

