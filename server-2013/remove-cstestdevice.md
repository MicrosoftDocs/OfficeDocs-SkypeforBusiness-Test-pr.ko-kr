---
title: Remove-CsTestDevice
TOCTitle: Remove-CsTestDevice
ms:assetid: 995111e0-2ab2-49a1-83f0-fc873f5b5426
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398790(v=OCS.15)
ms:contentKeyID: 49304482
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTestDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 장치 업데이트 관리 테스트 장치를 제거합니다. 관리자는 테스트 장치를 통해 펌웨어 업데이트를 조직의 모든 장치에 배포하기 전에 테스트할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsTestDevice -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트의 모든 테스트 장치를 제거합니다. 장치 컬렉션과 개별 테스트 장치가 모두 제거됩니다.

    Remove-CsTestDevice -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 조직에서 사용하도록 구성된 모든 테스트 장치를 제거합니다. 이 작업을 수행하기 위해 **Get-CsTestDevice** cmdlet을 사용하여 모든 테스트 장치 컬렉션을 반환한 다음 이러한 항목을 모두 **Remove-CsTestDevice** cmdlet에 파이프합니다. 전역 테스트 장치 컬렉션은 제거할 수 없지만 이 명령은 전역 수준에 구성된 모든 개별 테스트 장치를 삭제합니다.

    Get-CsTestDevice | Remove-CsTestDevice

## 예제 3

예제 3에서는 사이트 범위에 구성된 모든 테스트 장치가 제거됩니다. 이 작업을 수행하기 위해 **Get-CsTestDevice** cmdlet 및 Filter 매개 변수를 사용하여 ID가 문자열 값 "site:"으로 시작하는 모든 테스트 장치를 반환합니다. 이 필터링된 컬렉션은 컬렉션의 모든 항목을 삭제하는 **Remove-CsTestDevice** cmdlet에 파이프됩니다.

    Get-CsTestDevice -Filter "site:" | Remove-CsTestDevice

## 예제 4

예제 4의 명령은 모든 LG-Nortel 전화 테스트 장치를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsTestDevice** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 테스트 장치를 반환합니다. 그런 다음 이 정보는 -match 연산자를 사용하여 Name 속성의 아무 위치에나 문자열 값 "LG-Nortel"이 포함된 장치를 찾는 **Where-Object**에 파이프됩니다. 이 조건을 충족하는 모든 테스트 장치는 **Remove-CsTestDevice** cmdlet을 사용하여 삭제됩니다.

    Get-CsTestDevice | Where-Object {$_.Name -match "LG-Nortel Phone"} | Remove-CsTestDevice

## 자세한 정보

관리자는 특정 Lync Phone Edition 호환 전화 또는 기타 장치를 테스트 장치로 식별하여 펌웨어 업데이트를 조직의 모든 관련 장치에 적용하기 전에 이러한 업데이트를 확인 및 승인할 수 있습니다. 장치 업데이트 규칙을 Lync Server로 가져올 때 이러한 규칙은 "대기 중"으로 표시됩니다. 이는 대상 장치에서 이러한 규칙에 해당하는 업데이트를 자동으로 다운로드 및 설치하지 않음을 의미합니다.

대신 이러한 대기 중인 규칙은 관련 테스트 장치에서 다운로드하여 설치합니다. 테스트 장치의 기본 개념이 바로 이것입니다. 즉, 새 장치 업데이트 규칙은 테스트 장치에 자동으로 적용되므로 관리자는 펌웨어 업데이트가 예상대로 작동하는지 여부를 확인할 수 있습니다. 예상대로 작동할 경우 관리자는 규칙을 승인된 것으로 표시할 수 있습니다. 그러면 승인된 규칙은 조직의 모든 관련 장치에 다운로드 및 설치됩니다.

테스트 장치는 Lync Server를 실행하는 하드웨어 장치입니다. 이러한 장치는 **New-CsTestDevice** cmdlet을 사용하여 만듭니다. 만들어진 장치는 나중에 **Remove-CsTestDevice** cmdlet을 실행하여 제거할 수 있습니다. 테스트 장치로서 장치를 제거해도 실제 장치 자체에는 아무런 영향도 주지 않습니다. 예를 들어 Lync Server에 액세스하는 데 Lync Phone Edition 호환 전화를 계속 사용할 수 있습니다. 유일한 차이점은 더 이상 테스트 장치가 아니므로 대기 중 상태인 장치 업데이트 규칙을 더 이상 다운로드하지 않는다는 것입니다. 대신 해당 장치는 규칙이 승인될 때까지 기다린 후 다운로드하여 설치합니다.

**Remove-CsTestDevice** cmdlet을 사용하여 전역 또는 사이트 범위에 구성된 개별 테스트 장치를 제거할 수 있습니다. 또한 이 cmdlet을 사용하여 지정된 범위에 대해 구성된 모든 테스트 장치를 제거할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsTestDevice** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTestDevice"}

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
<td><p>제거할 테스트 장치의 Identity를 나타냅니다. 특정 장치를 제거하려면 범위(예: site:Redmond)와 장치 이름을 모두 포함합니다(예: -Identity &quot;site:Redmond/UCPhoneTest&quot;). 특정 사이트에서 모든 장치를 제거하려면 -Identity &quot;site:Redmond&quot; 형태의 구문을 사용합니다.</p>
<p>전역 범위에서도 테스트 장치를 제거할 수 있습니다. 전역 테스트 장치 컬렉션 자체는 제거할 수 없지만 다음 명령을 사용하여 전역 컬렉션에 저장된 모든 장치를 삭제할 수 있습니다.</p>
<p>Remove-CsTestDevice –Identity global</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체입니다. **Remove-CsTestDevice** cmdlet은 테스트 장치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsTestDevice**cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTestDevice](get-cstestdevice.md)  
[New-CsTestDevice](new-cstestdevice.md)  
[Set-CsTestDevice](set-cstestdevice.md)

