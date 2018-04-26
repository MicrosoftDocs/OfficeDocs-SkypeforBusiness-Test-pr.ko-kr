---
title: Reset-CsDeviceUpdateRule
TOCTitle: Reset-CsDeviceUpdateRule
ms:assetid: 0de47bcf-da8f-4dae-b293-3adac3c1acdb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398181(v=OCS.15)
ms:contentKeyID: 49302808
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Reset-CsDeviceUpdateRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

시스템으로 가져온 장치 업데이트 규칙을 거부합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Reset-CsDeviceUpdateRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Reset-CsDeviceUpdateRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 WebServer:atl-cs-001.litwareinc.com 서비스에 있는 장치 업데이트 규칙 d5ce3c10-2588-420a-82ac-dc2d9b1222ff9를 다시 설정합니다.

    Reset-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

## 예제 2

예제 2에서는 WebServer:atl-cs-001.litwareinc.com 서비스에 대해 구성된 모든 장치 업데이트 규칙을 다시 설정합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수와 함께 **Get-CsDeviceUpdateRule** cmdlet을 호출합니다. 필터 값 "WebServer:atl-cs-001.litwareinc.com\*"는 ID가 "WebServer:atl-cs-001.litwareinc.com" 문자로 시작하는 규칙만 반환되도록 합니다. 정의상, 이러한 규칙은 WebServer:atl-cs-001.litwareinc.com 서비스에 할당된 모든 장치 업데이트 규칙입니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 규칙을 다시 설정하는 **Reset-CsDeviceUpdateRule** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule -Filter service:WebServer:atl-cs-001.litwareinc.com*  | Reset-CsDeviceUpdateRule

## 예제 3

예제 3에 표시된 명령은 LG-Nortel 브랜드에 대한 모든 장치 업데이트 규칙을 다시 설정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsDeviceUpdateRule** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 장치 업데이트 규칙 컬렉션을 반환합니다. 이 컬렉션은 Brand 속성이 LG-Nortel과 같은 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 필터링된 컬렉션의 모든 규칙을 다시 설정하는 **Reset-CsDeviceUpdateRule** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "LG-Nortel"} | Reset-CsDeviceUpdateRule

## 자세한 정보

Lync Server에서는 Lync Phone Edition을 실행하는 장치에 펌웨어 업데이트를 제공하는 한 가지 방법으로 장치 업데이트 규칙을 사용합니다. 관리자는 주기적으로 Lync Server에 장치 업데이트 규칙 집합을 업로드하면 됩니다. 이러한 규칙을 테스트하고 승인한 후에는 규칙이 자동으로 다운로드되어 해당 장치(시스템에 연결된 경우)에 적용됩니다. 장치는 기본적으로 장치를 켜고 Lync Server에 연결할 때마다 새 업데이트 규칙을 확인합니다. 또한 초기 로그온 후 24시간 간격으로 업데이트를 확인합니다.

시스템에 추가된 새 장치 업데이트 규칙은 각각 "보류 중"으로 표시됩니다. 따라서 적절한 테스트 장치가 업데이트를 다운로드 및 설치하지만 일반 클라이언트 장치는 다운로드 및 설치하지 않습니다. 이렇게 하면 이 업데이트를 전체적으로 배포하기 전에 업데이트를 테스트하고 부정적인 영향이 있는지 확인할 수 있습니다. 업데이트가 테스트를 통과하고 조직에서 사용하기에 적절하다고 판단되는 즉시 **Approve-CsDeviceUpdateRule** cmdlet을 사용하여 업데이트를 승인할 수 있습니다.

반면, 관리자가 지정된 업데이트를 조직에서 사용하지 않도록 결정할 수도 있습니다. 예를 들어 업데이트로 인해 사내 소프트웨어와 충돌이 발생할 수 있습니다. 이 경우 관리자는 **Reset-CsDeviceUpdateRule** cmdlet을 사용하여 업데이트를 거부할 수 있습니다. 거부하면 업데이트 규칙의 PendingVersion이 null 값으로 설정됩니다. 이 경우 시스템에 로그온한 테스트 장치가 업데이트를 제거하고 승인된 버전의 업데이트를 다시 설치합니다. 그러나 승인된 업데이트가 없는 경우에는 이러한 테스트 장치 이외의 다른 장치에서 업데이트를 설치하지 못합니다. 따라서 일반 사용자에게 아무 영향을 주지 않습니다.

**Reset-CsDeviceUpdateRule** cmdlet은 보류 중인 상태의 장치 업데이트 규칙에만 사용할 수 있습니다. 규칙이 이미 승인된 경우 **Restore-CsDeviceUpdateRule** cmdlet을 사용하여 장치 업데이트 배포를 롤백해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Reset-CsDeviceUpdateRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Reset-CsDeviceUpdateRule"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>다시 설정되는 장치 업데이트 규칙의 고유 식별자입니다. 장치 업데이트 규칙의 ID는 장치 업데이트 규칙이 할당된 서비스(예: service:WebServer:atl-cs-001.litwareinc.com)와 GUID(Globally Unique Identifier)로 구성됩니다. 따라서 Redmond 사이트에 대해 구성된 장치 업데이트 규칙의 ID는 &quot;service:WebServer:atl-cs-oo1.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9&quot;와 유사합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>DeviceUpdate.Rule</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule 개체입니다. **Reset-CsDeviceUpdateRule** cmdlet은 장치 업데이트 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신, **Reset-CsDeviceUpdateRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule 개체의 인스턴스를 다시 설정합니다.

## 참고 항목

#### 기타 리소스

[Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)  
[Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)  
[Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)  
[Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)

