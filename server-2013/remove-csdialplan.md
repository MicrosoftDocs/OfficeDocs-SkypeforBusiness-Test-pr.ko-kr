---
title: Remove-CsDialPlan
TOCTitle: Remove-CsDialPlan
ms:assetid: 99845b82-1730-494a-8f47-2dec5ef177c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398791(v=OCS.15)
ms:contentKeyID: 49304484
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDialPlan

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 다이얼 플랜을 제거합니다. 또한 이 cmdlet을 사용하여 전역 다이얼 플랜을 제거할 수 있습니다. 그러나 전역 다이얼 플랜을 제거할 경우 다이얼 플랜은 실제로 제거되지 않으며, 그 대신 설정이 기본값으로 다시 설정됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDialPlan -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsDialPlan** cmdlet을 사용하여 ID가 RedmondDialPlan인 사용자별 다이얼 플랜을 삭제합니다. 다이얼 플랜을 삭제할 경우 현재 삭제된 플랜이 할당된 사용자에게 새 플랜을 할당할 필요는 없습니다. 대신에 이러한 사용자는 서비스 또는 사이트나 전역 플랜에 할당된 다이얼 플랜을 사용합니다.

    Remove-CsDialPlan -Identity RedmondDialPlan

## 예제 2

예제 2에서는 Redmond라는 단어가 설명에 포함된 모든 다이얼 플랜이 삭제됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDialPlan** cmdlet을 호출하여 조직에 사용하도록 구성된 모든 다이얼 플랜 컬렉션을 반환합니다. 그런 다음, Redmond라는 단어가 설명에 포함된 프로필에 대한 데이터만 반환하도록 제한하는 필터를 적용하기 위해 해당 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 이 작업이 수행된 후 필터링된 컬렉션은 컬렉션의 모든 다이얼 플랜을 제거하는 **Remove-CsDialPlan** cmdlet에 전달됩니다.

    Get-CsDialPlan | Where-Object {$_.Description -match "Redmond"} | Remove-CsDialPlan

## 자세한 정보

이 cmdlet은 기존 다이얼 플랜(위치 프로필이라고도 함)을 제거합니다. 다이얼 플랜은 Enterprise Voice 사용자가 전화 통화를 할 수 있는 데 필요한 정보를 제공합니다. 또한 전화 접속 회의를 위해 회의 길잡이 응용 프로그램에서 다이얼 플랜이 사용됩니다. 다이얼 플랜은 어떤 정규화 규칙이 적용되는지, 외부 통화를 위해 접두사를 사용해야 하는지 여부 등을 결정합니다.

참고: 다이얼 플랜을 제거하면 연관된 모든 정규화 규칙도 제거됩니다. 전역 다이얼 플랜이 제거될 경우 연관된 모든 정규화 규칙도 제거되지만 기본 전역 정규화 규칙이 만들어집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDialPlan** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDialPlan"}

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
<td><p>제거할 다이얼 플랜의 고유한 식별자입니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체입니다. **Remove-CsDialPlan** cmdlet은 다이얼 플랜 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialPlan](new-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)  
[Test-CsDialPlan](test-csdialplan.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

