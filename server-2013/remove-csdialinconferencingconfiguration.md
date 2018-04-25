---
title: Remove-CsDialInConferencingConfiguration
TOCTitle: Remove-CsDialInConferencingConfiguration
ms:assetid: 0c7f2a69-eeed-41bf-8ba7-5cc36dfdfa3c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398174(v=OCS.15)
ms:contentKeyID: 49302784
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDialInConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의 구성 설정 컬렉션을 하나 이상 제거합니다. 이러한 설정은 전화 접속 회의에 입장 또는 퇴장할 때 Lync Server에서 응답하는 방법을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDialInConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 전화 접속 회의 구성 설정을 삭제합니다.

    Remove-CSDialInConferencingConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 전화 접속 회의 설정이 삭제됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CSDialInConferencingConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 전화 접속 회의 설정의 컬렉션을 반환합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"로 시작하는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CSDialInConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CSDialInConferencingConfiguration -Filter "site:*" | Remove-CSDialInConferencingConfiguration

## 예제 3

예제 3에서는 이름 기록을 사용하지 않는 모든 전화 접속 회의 구성 설정이 삭제됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CSDialInConferencingConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 전화 접속 회의 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnableNameRecording 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CSDialInConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CSDialInConferencingConfiguration | Where-Object {$_.EnableNameRecording -eq $False} | Remove-CSDialInConferencingConfiguration

## 자세한 정보

사용자가 전화 접속 회의에 입장(또는 퇴장)할 때 Lync Server는 다양한 방식으로 응답할 수 있습니다. 예를 들어 전화 회의에 입장하기 전에 참가자에게 자신의 이름을 기록하도록 요청할 수 있습니다. 마찬가지로 관리자는 전화 접속 참가자가 전화 회의에 퇴장 또는 입장할 때 Lync Server에서 다른 사람에게 이를 알리도록 할지 여부를 결정할 수 있습니다.

이러한 전화 회의 "참가 동작"은 전화 접속 회의 구성 설정을 사용하여 관리됩니다. 이러한 설정은 전역 범위 또는 사이트 범위에서 구성할 수 있습니다. 사이트 범위에서 구성된 설정이 전역 범위에서 구성된 설정보다 우선합니다. Lync Server를 설치하면 전역 전화 접속 회의 구성 설정 컬렉션이 자동으로 만들어집니다. 사이트(또는 사이트 집합)에 대해 다른 설정을 지정하려는 경우 **New-CSDialInConferencingConfiguration** cmdlet을 사용하여 해당 컬렉션을 만들 수 있습니다.

**Remove-CSDialInConferencingConfiguration** cmdlet은 사이트 범위에서 구성된 모든 전화 접속 회의 설정을 삭제합니다. 이러한 사이트별 설정이 삭제되면 영향을 받는 사이트에 포함된 사용자의 전화 접속 회의 동작이 전역 설정으로 제어됩니다.

전역 전화 접속 회의 설정에 대해 **Remove-CSDialInConferencingConfiguration** cmdlet을 실행할 수도 있습니다. 전역 설정은 제거할 수 없으므로 이 경우에는 전역 설정이 제거되지 않습니다. 대신, 해당 설정 컬렉션 내의 모든 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDialInConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDialInConferencingConfiguration"}

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
<td><p>제거할 전화 접속 회의 구성 설정의 ID를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체입니다. **Remove-CSDialInConferencingConfiguration** cmdlet은 전화 접속 회의 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신, **Remove-CSDialInConferencingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)  
[New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

