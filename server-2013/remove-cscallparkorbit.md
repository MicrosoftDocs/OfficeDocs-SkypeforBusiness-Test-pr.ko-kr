---
title: Remove-CsCallParkOrbit
TOCTitle: Remove-CsCallParkOrbit
ms:assetid: b8e7c236-f8de-45bd-966b-60c815b37aed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412901(v=OCS.15)
ms:contentKeyID: 49304833
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCallParkOrbit

 

_**마지막으로 수정된 항목:** 2015-03-09_

특정 통화 대기 파킹된 통화 번호 범위를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 **Remove-CsCallParkOrbit** cmdlet을 사용하여 이름이 Redmond CPO 1인 통화 대기 파킹된 통화 번호 범위를 삭제합니다.

    Remove-CsCallParkOrbit -Identity "Redmond CPO 1"

## 예제 2

이 예제의 명령은 조직에 정의된 모든 통화 대기 파킹된 통화 번호 범위를 제거합니다. 이 명령은 먼저 **Get-CsCallParkOrbit** cmdlet을 매개 변수 없이 호출하여 정의된 모든 통화 대기 파킹된 통화 번호 범위를 검색합니다. 그런 다음 각 통화 대기 파킹된 통화 번호를 제거하는 **Remove-CsCallParkOrbit** cmdlet에 통화 대기 파킹된 통화 번호 범위 컬렉션을 파이프합니다.

    Get-CsCallParkOrbit | Remove-CsCallParkOrbit

## 예제 3

이 명령은 "Redmond 501", "CP Redmond 1" 및 "ARedmond"와 같이 ID에 문자열 "Redmond"가 포함된 모든 통화 대기 파킹된 통화 번호 범위를 제거합니다. 먼저 이 명령은 Filter 매개 변수와 함께 **Get-CsCallParkOrbit** cmdlet을 호출하여 ID에 문자열 Redmond가 포함된 모든 통화 대기 파킹된 통화 번호 범위를 검색합니다. 이 컬렉션은 컬렉션의 모든 항목을 제거하는 **Remove-CsCallParkOrbit** cmdlet에 파이프됩니다.

    Get-CsCallParkOrbit -Filter *Redmond* | Remove-CsCallParkOrbit

## 자세한 정보

**Remove-CsCallParkOrbit** cmdlet은 필수 항목인 Identity 매개 변수에 전달된 이름을 가진 통화 대기 파킹된 통화 번호 범위를 삭제합니다. 조직 내의 각 통화 대기 파킹된 통화 번호에는 고유한 번호 범위가 있어야 합니다. 통화 대기 파킹된 통화 번호를 제거하면 해당 통화 대기 파킹된 통화 번호에 있던 범위가 비워집니다. 그런 다음, 비워진 번호를 새로 정의한 통화 대기 파킹된 통화 번호에서 사용할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsCallParkOrbit** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCallParkOrbit"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>통화 대기 파킹된 통화 번호 범위의 이름입니다. 이 이름은 통화 대기 파킹된 통화 번호 범위를 정의할 때 관리자가 할당합니다.</p></td>
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

Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit 개체입니다. 통화 대기 파킹된 통화 번호 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

