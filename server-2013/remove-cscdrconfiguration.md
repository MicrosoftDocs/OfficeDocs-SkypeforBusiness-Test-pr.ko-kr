---
title: Remove-CsCdrConfiguration
TOCTitle: Remove-CsCdrConfiguration
ms:assetid: 64352746-a03c-434a-9baf-4d9cd630e9da
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398451(v=OCS.15)
ms:contentKeyID: 49303837
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCdrConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 CDR(통화 정보 기록) 설정의 컬렉션을 제거합니다. CDR을 사용하여 피어-투-피어 메신저 대화 세션, VoIP(Voice over Internet Protocol) 전화 통화, 전화 회의 통화 등의 사용 현황을 추적할 수 있습니다. 이러한 사용 내역 데이터에는 누가 누구에게 전화를 걸었는지, 언제 전화를 걸었는지 및 얼마나 오래 통화했는지에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsCdrConfiguration** cmdlet을 사용하여 Redmond 사이트에 할당된 CDR 설정을 제거합니다. Identity 매개 변수를 사용하면 지정된 사이트에 할당된 설정만 제거됩니다.

    Remove-CsCdrConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 할당된 모든 CDR 설정을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsCdrConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 해당하는 CDR 설정을 검색하고 문자열 값 "site:\*"를 사용하여 ID가 문자 "site:"으로 시작하는 설정만 반환되도록 합니다. 필터링된 컬렉션은 컬렉션의 모든 항목을 삭제하는 **Remove-CsCdrConfiguration** cmdlet에 파이프됩니다.

    Get-CsCdrConfiguration -Filter site:* | Remove-CsCdrConfiguration

## 예제 3

예제 3에서는 KeepCallDetailForDays 속성이 30일보다 작은 모든 CDR 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 추가 매개 변수 없이 **Get-CsCdrConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 CDR 설정의 컬렉션을 반환합니다. 이 컬렉션은 KeepCallDetailForDays 속성이 30일보다 작은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsCdrConfiguration** cmdlet에 파이프됩니다.

    Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30} | Remove-CsCdrConfiguration

## 자세한 정보

CDR(통화 정보 기록)을 사용하면 VoIP(Voice over Internet Protocol) 전화 통화, 메신저 대화, 파일 전송, A/V(오디오/비디오) 회의 및 응용 프로그램 공유 세션과 같은 Lync Server 기능의 사용 내역을 추적할 수 있습니다. CDR은 모니터링 서비스를 배포한 경우에만 사용할 수 있으며, 사용 정보를 보관하고 예를 들어 통화에 참여한 사람, 통화 시간, 파일 전송 여부 등에 대한 정보를 기록합니다. 그러나 통화 자체를 녹음하지는 않습니다.

CDR은 또한 통화 오류 정보를 추적하며 피어-투-피어 세션과 전화 회의 통화에 대한 자세한 진단 데이터를 제공합니다.

관리자는 조직에서 CDR을 사용할지 여부를 결정할 수 있습니다. 모니터링 서비스가 배포된 경우 CDR을 사용하거나 사용하지 않도록 쉽게 설정할 수 있습니다. 뿐만 아니라 이 결정을 전체적으로 적용하여 조직 전체에서 CDR을 활성화 또는 비활성화하거나, 사이트 단위로 적용할 수 있습니다. 예를 들어 Redmond 사이트에서는 CDR을 사용하고 Paris 사이트에서는 CDR을 사용하지 않을 수 있습니다.

**New-CsCdrConfiguration** cmdlet을 사용하여 만든 사이트 관련 설정은 나중에 **Remove-CsCdrConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 사이트별 설정을 제거하면 영향받는 사이트의 CDR이 자동으로 전역 CDR 구성 설정에 따라 제어됩니다.

전역 CDR 설정에 대해 **Remove-CsCdrConfiguration** cmdlet을 실행할 수도 있습니다. 그러나 전역 설정은 제거할 수 없으므로 대신 기본값으로 다시 설정됩니다. 예를 들어 전역 설정에서 KeepCallDetailForDays 속성의 값을 90으로 설정한 후에 전역 설정에 대해 **Remove-CsCdrConfiguration** cmdlet을 실행하면 속성이 기본값인 60으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsCdrConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCdrConfiguration"}

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
<td><p>제거할 CDR 구성 설정의 고유 식별자입니다. 전역 설정을 &quot;제거&quot;하려면 -Identity global 구문을 사용합니다. 앞서 말했듯이 전역 설정은 실제로 제거할 수 없습니다. 속성을 기본값으로 다시 설정할 수만 있습니다. 사이트 범위에서 설정을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. **Remove-CsCdrConfiguration** cmdlet은 CDR 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

