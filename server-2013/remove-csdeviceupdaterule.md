---
title: Remove-CsDeviceUpdateRule
TOCTitle: Remove-CsDeviceUpdateRule
ms:assetid: 42b0bcd5-d567-4867-841e-0d35ac05c09f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425930(v=OCS.15)
ms:contentKeyID: 49303454
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDeviceUpdateRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 장치 업데이트 규칙을 제거합니다. 장치 업데이트 규칙은 펌웨어 업데이트를 Lync Phone Edition을 실행하는 장치와 연결하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDeviceUpdateRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9인 장치 업데이트 규칙을 삭제합니다. 규칙이 삭제된 후에는 해당 펌웨어 업데이트를 더 이상 사용할 수 없습니다.

    Remove-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

## 예제 2

예제 2에 표시된 명령은 조직에서 사용하도록 구성된 모든 장치 업데이트 규칙을 제거합니다. 현재 사용 중인 모든 장치 업데이트 규칙 컬렉션을 반환하기 위해 **Get-CsDeviceUpdateRule** cmdlet을 매개 변수 없이 호출합니다. 그런 다음 이 컬렉션은 컬렉션의 각 규칙을 삭제하는 **Remove-CsDeviceUpdateRule** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule | Remove-CsDeviceUpdateRule

## 예제 3

예제 3에서는 WebServer:atl-cs-001.litwareinc.com 서비스로 가져온 모든 장치 업데이트 규칙이 제거됩니다. 먼저 **Get-CsDeviceUpdateRule** cmdlet 및 Filter 매개 변수를 사용하여 ID가 문자열 값 "service:WebServer:atl-cs-001.litwareinc.com"으로 시작하는 모든 장치 업데이트 규칙을 검색합니다. 그런 다음 이 컬렉션은 컬렉션의 각 규칙을 삭제하는 **Remove-CsDeviceUpdateRule**에 파이프됩니다.

    Get-CsDeviceUpdateRule -Filter service:WebServer:atl-cs-001.litwareinc.com* | Remove-CsDeviceUpdateRule

## 예제 4

예제 4에서는 Brand가 "LG-Nortel"과 같은 모든 장치 업데이트 규칙을 삭제합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateRule** cmdlet을 매개 변수 없이 호출하여 조직에서 사용 중인 모든 장치 업데이트 규칙 컬렉션을 검색합니다. 이 컬렉션은 Brand가 "LG-Nortel"과 같은 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 규칙을 제거하는 **Remove-CsDeviceUpdateRule** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "LG-Nortel"} | Remove-CsDeviceUpdateRule

## 자세한 정보

Lync Server에서는 Lync Phone Edition을 실행하는 장치에 펌웨어 업데이트를 제공하는 한 가지 방법으로 장치 업데이트 규칙을 사용합니다. 관리자는 장치 업데이트 규칙 집합을 주기적으로 Lync Server에 업로드합니다. 그러면 이러한 규칙이 테스트 및 승인된 후 시스템에 연결된 적절한 장치에 자동으로 다운로드되어 적용됩니다. 장치는 기본적으로 장치를 켜고 Lync Server에 연결할 때마다 새 업데이트 규칙을 확인합니다. 또한 초기 로그온 후 24시간 간격으로 업데이트를 확인합니다.

관리자는 고유한 장치 업데이트 규칙을 만들 수 없습니다. 업데이트 규칙을 만들려면 Microsoft 웹 사이트에서 규칙 집합을 다운로드하여 가져와야 합니다. 따라서 시간이 경과함에 따라 오래된 규칙이나 조직에서 사용하지 않는 규칙을 수집하게 될 수 있습니다. 예를 들어 조직에서 LG-Nortel 전화를 더 이상 사용하지 않는 경우에는 해당 장치에 대한 펌웨어 업데이트가 더 이상 필요하지 않습니다. 불필요한 이러한 규칙으로 인해 문제가 발생하지는 않지만 관리 작업이 복잡해질 수 있습니다. **Get-CsDeviceUpdateRule** cmdlet을 실행하여 모든 장치 업데이트 규칙 컬렉션을 반환했는데 대부분의 규칙이 조직에 적용되지 않는다면 혼동을 줄 수 있습니다. 이러한 혼동을 줄이기 위해 **Remove-CsDeviceUpdateRule** cmdlet을 사용하여 가져온 장치 업데이트 규칙 또는 규칙 집합을 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDeviceUpdateRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDeviceUpdateRule"}

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
<td><p>장치 업데이트 규칙의 고유 식별자입니다. 장치 업데이트 규칙의 ID는 규칙이 적용된 서비스 범위(예: service:WebServer:atl-cs-001.litwareinc.com) 및 규칙에 미리 할당된 GUID(Globally Unique Identifier)(예: d5ce3c10-2588-420a-82ac-dc2d9b1222ff9)의 두 부분으로 구성됩니다. 이 구성에 따라 지정된 장치 업데이트 규칙의 ID는 &quot;service:WebServer:atl-cs-001.litwareinc.com /d5ce3c10-2588-420a-82ac-dc2d9b1222ff9&quot; 유사합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule 개체입니다. **Remove-CsDeviceUpdateRule** cmdlet은 장치 업데이트 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsDeviceUpdateRule** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.Rule 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)  
[Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)  
[Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md)  
[Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)

