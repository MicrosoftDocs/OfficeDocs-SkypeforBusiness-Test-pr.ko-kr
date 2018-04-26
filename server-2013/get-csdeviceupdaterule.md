---
title: Get-CsDeviceUpdateRule
TOCTitle: Get-CsDeviceUpdateRule
ms:assetid: 14291802-a833-4f5f-8b4b-a465de6f7f2b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398215(v=OCS.15)
ms:contentKeyID: 49302890
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDeviceUpdateRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 장치 업데이트 규칙에 대한 정보를 반환합니다. 장치 업데이트 규칙은 펌웨어 업데이트를 Lync Server를 실행하는 장치와 연결하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDeviceUpdateRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDeviceUpdateRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 자세한 정보

Lync Server에서는 Lync Phone Edition을 실행하는 장치에 펌웨어 업데이트를 제공하는 한 가지 방법으로 장치 업데이트 규칙을 사용합니다. 관리자는 장치 업데이트 규칙 집합을 주기적으로 Lync Server에 업로드합니다. 그러면 이러한 규칙이 테스트 및 승인된 후 시스템에 연결된 적절한 장치에 자동으로 다운로드되어 적용됩니다. 장치는 기본적으로 장치를 켜고 Lync Server에 연결할 때마다 새 업데이트 규칙을 확인합니다. 또한 초기 로그온 후 24시간 간격으로 업데이트를 확인합니다.

장치 업데이트 규칙은 웹 서비스 서비스에 가져와 적용할 수 있습니다. **Get-CsDeviceUpdateRule** cmdlet은 사용자의 조직에서 사용하기 위해 가져온 장치 업데이트 규칙에 대한 정보를 반환합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDeviceUpdateRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDeviceUpdateRule"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>장치 업데이트 규칙이나 규칙 집합의 ID를 지정할 때 와일드 카드를 활용하는 데 사용됩니다. 예를 들어 WebServer:atl-cs-001.litwareinc.com에 대한 모든 장치 업데이트 규칙을 반환하려면 필터 값으로 &quot;service:WebServer:atl-cs-001.litwareinc.com*&quot;을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>장치 업데이트 규칙에 대한 고유한 식별자입니다. 장치 업데이트 규칙 ID는 규칙이 적용된 서비스 범위(예: service:WebServer:atl-cs-001.litwareinc.com) 및 규칙에 미리 할당된 GUID(Globally Unique Identifier)(예: d5ce3c10-2588-420a-82ac-dc2d9b1222ff9)의 두 부분으로 구성됩니다. 이를 기반으로, 지정된 장치 업데이트 규칙 ID는 &quot;service:WebServer:atl-cs-001.litwareinc.com /d5ce3c10-2588-420a-82ac-dc2d9b1222ff9&quot;와 유사합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 규칙을 지정할 때 와일드카드를 사용하려면 Filter 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 장치 업데이트 규칙 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDeviceUpdateRule** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDeviceUpdateRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule 개체의 인스턴스를 반환합니다.

## 예제

## 예제 1

예제 1의 명령은 사용자의 조직에 적용된 모든 장치 업데이트 규칙에 대한 정보를 반환합니다. **Get-CsDeviceUpdateRule** cmdlet을 추가 매개 변수 없이 호출하면 항상 장치 업데이트 규칙의 전체 컬렉션이 반환됩니다.

    Get-CsDeviceUpdateRule

## 예제 2

예제 2에 표시된 명령은 ID가 "WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"인 장치 업데이트 규칙에 대한 정보를 반환합니다.

    Get-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

## 예제 3

예제 3에서는 WebServer:atl-cs-001.litwareinc.com 서비스에 대해 구성된 모든 장치 업데이트 규칙에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수가 필터 값 "WebServer:atl-cs-001.litwareinc.com \*"과 함께 사용됩니다. 이 필터는 ID가 문자열 값 "service:WebServer:atl-cs-001.litwareinc.com"으로 시작하는 장치 업데이트 규칙에 대한 데이터만 반환하도록 제한합니다.

    Get-CsDeviceUpdateRule -Filter service:WebServer:atl-cs-001.litwareinc.com*

## 예제 4

예제 4에서는 Brand 속성이 "LG-Nortel"과 같은 모든 장치 업데이트 규칙을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateRule** cmdlet을 호출하여 조직의 모든 장치 업데이트 규칙 컬렉션을 반환합니다. 이 컬렉션은 Brand가 "LG-Nortel"과 같은 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "LG-Nortel"}

## 예제 5

예제 5에서는 승인되지 않은 모든 장치 업데이트 규칙의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateRules** cmdlet을 사용하여 모든 규칙의 컬렉션을 반환하고 이 컬렉션을 **Where-Object** cmdlet에 파이프합니다. 그리고 **Where-Object** cmdlet은 Approved 속성이 null 값과 같은 규칙만 선택합니다. Approved 속성이 null인 경우 이러한 규칙이 승인되지 않았음을 의미합니다.

    Get-CsDeviceUpdateRule | Where-Object {$_.ApprovedVersion -eq $Null}

## 예제 6

이 명령은 승인되고 LG-Nortel 장치와 관련 있는 규칙이어야 한다는 두 가지 기준을 충족하는 모든 장치 업데이트 규칙의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDeviceUpdateRule** cmdlet을 호출하여 조직의 모든 장치 업데이트 규칙 컬렉션을 반환합니다. 이 컬렉션은 Approved 속성이 null이 아니고(즉, 이 속성에 값이 있어야 함), Brand가 "LG-Nortel"과 같아야 한다는 두 조건에 대해 컬렉션을 필터링하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule | Where-Object {$_.ApprovedVersion -ne $Null -and $_.Brand -eq "LG-Nortel"}

## 참고 항목

#### 기타 리소스

[Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)  
[Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)  
[Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md)  
[Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)

