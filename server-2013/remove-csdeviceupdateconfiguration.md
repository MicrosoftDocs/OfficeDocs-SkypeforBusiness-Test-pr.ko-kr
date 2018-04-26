---
title: Remove-CsDeviceUpdateConfiguration
TOCTitle: Remove-CsDeviceUpdateConfiguration
ms:assetid: 4335eb24-61a6-4e76-8242-edfd861d7d0b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425933(v=OCS.15)
ms:contentKeyID: 49303463
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDeviceUpdateConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 장치 업데이트 구성 설정을 제거합니다. 이러한 설정은 관리자가 전화기 및 Lync Phone Edition을 실행하는 기타 장치에 펌웨어 업데이트를 배포하는 데 사용할 수 있는 Lync Server 구성 요소인 장치 업데이트 웹 서비스를 관리하도록 도와줍니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDeviceUpdateConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsDeviceUpdateConfiguration** cmdlet을 사용하여 전역 장치 업데이트 구성 설정을 "제거"합니다. 전역 설정은 제거할 수 없으므로 명령은 실제로는 아무것도 삭제하지 않으며 대신 전역 장치 업데이트 구성 설정의 모든 속성을 해당 기본값으로 다시 설정합니다.

    Remove-CsDeviceUpdateConfiguration -Identity global

## 예제 2

예제 2에 표시된 명령은 ID가 site:Redmond인 장치 업데이트 구성 설정을 제거합니다. 이러한 설정은 사이트 범위에서 구성되었으므로 삭제되며 Redmond 사이트에는 더 이상 자체 장치 업데이트 구성 설정이 없게 됩니다.

    Remove-CsDeviceUpdateConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에 구성된 모든 장치 업데이트 구성 설정을 제거합니다. 이 작업을 수행하기 위해 **Get-CsDeviceUpdateConfiguration** cmdlet과 -Filter 매개 변수를 사용하여 ID가 문자열 값 "site:"으로 시작하는 모든 설정을 반환합니다. 이렇게 하면 사이트 범위에 구성된 모든 설정이 반환됩니다. 해당 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsDeviceUpdateConfiguration** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration 

## 예제 4

예제 4에서는 MaxLogFileSize 속성이 1024000바이트보다 큰 모든 장치 업데이트 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDeviceUpdateConfiguration** cmdlet을 호출하여 모든 장치 업데이트 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 MaxLogFileSize 속성이 1024000바이트보다 큰 구성 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsDeviceUpdateConfiguration** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -lt 1024000} | Remove-CsDeviceUpdateConfiguration

## 자세한 정보

장치 업데이트 웹 서비스를 사용하면 관리자가 Lync Phone Edition을 실행하는 장치에 펌웨어 업데이트를 배포할 수 있습니다. 관리자는 주기적으로 Lync Server에 장치 업데이트 규칙 집합을 업로드하면 됩니다. 이러한 규칙을 테스트하고 승인한 후에는 규칙이 해당 장치(시스템에 연결된 경우)에 적용됩니다. 장치는 장치를 켤 때 업데이트를 확인한 다음 사용자가 로그온하면 다시 확인합니다. 이후에는 24시간마다 업데이트를 확인합니다.

Lync Server는 장치 업데이트 구성 설정을 사용하여 장치 업데이트 웹 서비스를 관리합니다. 이러한 구성 설정은 전역 범위 또는 사이트 범위에 적용됩니다. 기본적으로 설정은 전역 범위에서만 발견되지만 **New-CsDeviceUpdateConfiguration** cmdlet을 사용하여 사용자 지정된 설정을 사이트 범위에 할당할 수 있습니다.

또한 **Remove-CsDeviceUpdateConfiguration** cmdlet을 사용하여 사이트 범위에 할당된 설정을 삭제할 수 있습니다. 이 cmdlet을 사이트를 대상으로 실행하면 해당 사이트에 할당된 장치 업데이트 구성 설정이 제거됩니다. 전역 설정을 대상으로 **Remove-CsDeviceUpdateConfiguration** cmdlet을 실행할 수도 있습니다. 이 경우 전역 설정이 제거되지 않습니다. 전역 장치 업데이트 구성 설정은 제거할 수 없습니다. 대신 전역 속성은 해당 기본값으로 다시 설정됩니다. 예를 들어 전역 속성인 MaxLogCacheLimit를 1,024,000바이트로 설정했다고 가정해 보겠습니다. 전역 설정을 대상으로 **Remove-CsDeviceUpdateConfiguration** cmdlet을 실행하더라도 전역 설정이 제거되지는 않지만 수정된 속성이 있으면 해당 기본값으로 다시 설정됩니다. 즉, MaxLogCacheLimit가 512,000바이트로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDeviceUpdateConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDeviceUpdateConfiguration"}

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
<td><p>제거할 장치 업데이트 구성 설정의 ID를 지정합니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration 개체입니다. **Remove-CsDeviceUpdateConfiguration** cmdlet은 장치 업데이트 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsDeviceUpdateConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)  
[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

