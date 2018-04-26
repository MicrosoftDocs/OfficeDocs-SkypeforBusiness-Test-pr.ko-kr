---
title: Remove-CsDialInConferencingDtmfConfiguration
TOCTitle: Remove-CsDialInConferencingDtmfConfiguration
ms:assetid: 3cd6313c-fd0a-4fb2-bacd-b1bdf2a59430
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425894(v=OCS.15)
ms:contentKeyID: 49303377
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDialInConferencingDtmfConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의에 사용되는 DTMF(Dual-Tone Multifrequency) 신호 설정의 기존 컬렉션을 제거합니다. DTMF를 사용하면 전화 회의에 전화 접속한 사용자가 전화기의 키패드를 사용하여 음소거 설정 및 해제 또는 전화 회의 잠금 설정 및 해제와 같은 전화 회의 설정을 제어할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDialInConferencingDtmfConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Identity site:Redmond가 포함된 DTMF 구성 설정 컬렉션을 삭제합니다.

    Remove-CSDialInConferencingDtmfConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 구성된 모든 DTMF 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CSDialInConferencingDtmfConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 DTMF 설정의 컬렉션을 반환합니다. 필터 값 "site:\*"는 문자열 값 "site:"으로 시작하는 Identity를 가진 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 항목을 제거하는 **Remove-CSDialInConferencingConfiguration** cmdlet에 파이프됩니다.

    Get-CSDialInConferencingDtmfConfiguration -Filter "site:*" | Remove-CSDialInConferencingDtmfConfiguration

## 예제 3

예제 3에서는 **Remove-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 PrivateRollCallCommand 속성이 null 값과 같은(private roll call 명령이 비활성화된) 모든 DTMF 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 DTMF 설정의 컬렉션을 반환합니다. 이 컬렉션은 PrivateRollCallCommand가 null 값과 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CSDialInConferencingDtmfConfiguration**에 파이프됩니다.

    Get-CSDialInConferencingDtmfConfiguration | Where-Object {$_.PrivateRollCallCommand -eq $Null} | Remove-CSDialInConferencingDtmfConfiguration

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 접속하여 전화 회의에 참가할 수 있습니다. 전화 접속 사용자는 비디오를 보거나 다른 전화 회의 참석자와 메신저 대화를 교환할 수 없지만 모임의 오디오 부분에는 전적으로 참여할 수 있습니다.

또한 전화 회의에 참가하는 것 외에 전화기의 키패드를 사용하여 해당 전화 회의의 선택된 부분을 관리할 수도 있습니다. 사용자가 관리할 수 있는 특정 전화 회의 설정과 관리할 수 없는 특정 전화 회의 설정은 사용자가 발표자인지 여부에 따라 다릅니다. 예를 들어 기본적으로 사용자는 키패드에서 6번 키를 눌러 음소거를 설정하거나 해제할 수 있습니다. 참가자는 모임에 참가한 다른 모든 사람의 이름을 개인적으로 재생할 수 있고, 발표자는 모든 모임 참가자에 대해 음소거를 설정 및 해제하고 누군가 전화 회의에 참가하거나 전화 회의에서 나갈 때 재생되는 알림을 설정/해제하는 등의 작업을 수행할 수 있습니다.

전화기의 키패드를 사용하여 이와 같은 선택을 수행할 수 있는 기능을 DTMF(Dual-Tone Multifrequency) 신호라고 합니다. 특정 전화 번호로 전화를 걸었는데 "영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르십시오."라는 안내에 따라 작업을 수행해야 하는 경우 DTMF 신호를 사용한 것입니다.

Lync Server를 설치하면 전역 DTMF 설정 컬렉션이 만들어집니다. 이러한 전역 설정 외에도 **New-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 사이트별로 사용자 지정 설정을 만들 수 있습니다. 사이트 범위에서 생성한 설정은 나중에 **Remove-CSDialInConferencingDtmfConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 사이트 범위에서 적용된 DTMF 설정을 제거하면 영향을 받는 사이트의 사용자는 전역 DTMF 구성 설정의 영향을 받는 범위에서 자동으로 실패합니다.

**Remove-CSDialInConferencingDtmfConfiguration** cmdlet을 전역 설정에 대해 실행할 수도 있습니다. 그러나 전역 DTMF 설정은 제거할 수 없기 때문에 이 작업을 수행해도 전역 설정이 제거되지 않습니다. 대신, 전역 설정의 속성이 기본값으로 다시 설정됩니다. 예를 들어 4번 키를 음소거/음소거 해제 키로 사용하도록 전역 설정을 수정한 경우를 가정해 보겠습니다. 이제 전역 설정에 대해 **Remove-CSDialInConferencingDtmfConfiguration** cmdlet을 실행하면 음소거/음소거 해제 키 값이 기본값 6으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDialInConferencingDtmfConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDialInConferencingDtmfConfiguration"}

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
<td><p>제거할 DTMF 설정 컬렉션의 고유한 식별자입니다. 전역 설정을 &quot;제거&quot;하려면 -Identity global 구문을 사용합니다. 앞에서 언급한 대로 전역 설정을 실제로 제거할 수는 없습니다. 작업을 수행하면 속성이 기본값으로 다시 설정될 뿐입니다. 사이트 범위에서 구성된 컬렉션을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체입니다. **Remove-CsDialInConferencingDtmfConfiguration** cmdlet은 전화 접속 회의 DTMF 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신, **Remove-CSDialInConferencingDtmfConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)  
[New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)  
[Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

