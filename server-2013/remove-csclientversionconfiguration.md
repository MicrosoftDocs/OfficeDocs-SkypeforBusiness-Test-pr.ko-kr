---
title: Remove-CsClientVersionConfiguration
TOCTitle: Remove-CsClientVersionConfiguration
ms:assetid: 42065d1d-a0ef-4fa4-826b-d65b14b343c9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425925(v=OCS.15)
ms:contentKeyID: 49303447
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClientVersionConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 클라이언트 버전 구성 설정의 컬렉션을 제거합니다. 클라이언트 버전 구성 설정은 Lync Server에서 시스템에 로그온하는 각 클라이언트 응용 프로그램의 버전 번호를 확인할지 여부를 결정합니다. 클라이언트 버전 필터링을 설정한 경우에는 해당 클라이언트 버전 정책에 구성된 설정에 따라 클라이언트 응용 프로그램에서 시스템에 액세스할 수 있는지 여부가 결정됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "site:Redmond"인 클라이언트 버전 구성 설정을 삭제합니다.

    Remove-CsClientVersionConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에 적용된 모든 클라이언트 버전 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수를 지정하고 **Get-CsClientVersionConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 클라이언트 버전 구성 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsClientVersionConfiguration** cmdlet에 파이프됩니다.

    Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

## 예제 3

예제 3에서는 현재 사용하지 않도록 설정된 모든 클라이언트 버전 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsClientVersionConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 클라이언트 버전 구성 설정의 컬렉션을 반환합니다. 이 데이터가 반환되면 컬렉션은 Enabled 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsClientVersionConfiguration** cmdlet에 파이프됩니다.

    Get-CsClientVersionConfiguration | Where-Object {$_.Enabled -eq $False} | Remove-CsClientVersionConfiguration

## 자세한 정보

Lync Server에서는 사용자가 시스템에 로그온하는 데 사용하는 클라이언트 소프트웨어와 해당 소프트웨어의 버전 번호를 지정할 수 있는 상당한 재량권을 관리자에게 제공하고 있습니다. 예를 들어 사용자가 Lync Server를 사용하여 Lync에 로그온해야 하는 기술적인 이유는 없습니다. 기술적인 면에서는 Microsoft Office Communicator 2007 R2를 사용하여 로그온할 수도 있습니다.

그러나 사용자가 Office Communicator 2007 R2를 사용하여 로그온하지 않도록 하는 것이 좋은 몇 가지 비기술적인 이유가 있을 수 있습니다. 예를 들어 Office Communicator 2007 R2는 Lync에서 제공하는 일부 기능을 지원하지 않으므로 Office Communicator 2007 R2를 사용하여 로그온한 사용자에게는 Lync를 사용하여 로그온한 사용자와 다른 환경이 제공됩니다. 이것은 사용자에게 문제가 될 수 있으며 다양한 클라이언트 응용 프로그램을 지원해야 하는 지원 센터 직원에게도 문제가 될 수 있습니다.

이러한 점이 조직에 문제가 되는 경우 클라이언트 버전 필터링을 사용하여 Lync Server에 로그온하는 데 사용할 수 있는 클라이언트 응용 프로그램을 지정할 수 있습니다. Lync Server를 설치하면 전체 클라이언트 버전 구성 설정 집합이 설치되고 사용하도록 설정됩니다. 이러한 전역 설정 외에 사이트 범위에 클라이언트 버전 구성 설정을 적용할 수 있습니다.

만든 사이트 설정은 나중에 **Remove-CsClientVersionConfiguration** cmdlet을 사용하여 삭제할 수 있습니다. 전역 설정에 대해 **Remove-CsClientVersionConfiguration** cmdlet을 실행할 수도 있습니다. 이 경우 전역 설정이 제거되지 않습니다. 대신 전역 속성이 해당 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsClientVersionConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientVersionConfiguration"}

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
<td><p>제거할 클라이언트 버전 구성 설정의 컬렉션에 대한 고유한 식별자입니다. 전역 컬렉션을 제거하려면 -Identity global 구문을 사용합니다. 전역 설정은 실제로 제거되지는 않으며 전역 속성이 해당 기본값으로 다시 설정됩니다. 사이트 컬렉션을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체입니다. **Remove-CsClientVersionConfiguration** cmdlet은 클라이언트 버전 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

