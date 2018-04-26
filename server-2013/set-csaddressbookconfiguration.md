---
title: Set-CsAddressBookConfiguration
TOCTitle: Set-CsAddressBookConfiguration
ms:assetid: a700328b-c738-447a-a03c-319852b42240
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412784(v=OCS.15)
ms:contentKeyID: 49304647
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

주소록 구성 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAddressBookConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsAddressBookConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableFileGeneration <$true | $false>] [-EnablePhotoSearch <$true | $false>] [-Force <SwitchParameter>] [-IgnoreGenericRules <$true | $false>] [-KeepDuration <UInt32>] [-MaxDeltaFileSizePercentage <UInt32>] [-MaxFileShareThreadCount <Int32>] [-RunTimeOfDay <DateTime>] [-SynchronizePollingInterval <TimeSpan>] [-UseNormalizationRules <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제는 RunTimeOfDay 속성(주소록 동기화 발생 시간을 결정하는 속성)을 23:00(24시간제 형식의 오후 11시)으로 설정합니다. Identity 매개 변수를 사용하여 ID가 site:Redmond인 주소록 서버 구성 설정만 변경하도록 제한합니다.

    Set-CsAddressBookConfiguration -identity site:Redmond -RunTimeOfDay 23:00

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 주소록 설정 컬렉션의 RunTimeOfDay 속성을 오후 11시(23:00)로 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAddressBookConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 모든 사이트별 설정의 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환되는 데이터를 사이트 범위에서 구성된 컬렉션으로 제한합니다. 그러면 이 정보가 **Set-CsAddressBookConfiguration** cmdlet에 파이프되어 컬렉션의 각 항목에 대한 RunTimeOfDay 속성 값이 수정됩니다.

    Get-CsAddressBookConfiguration -Filter site:* | Set-CsAddressBookConfiguration -RunTimeOfDay 23:00

## 예제 3

예제 3에서는 KeepDuration이 30일 미만인 주소록 설정 컬렉션의 KeepDuration 속성을 수정합니다. 이 작업을 수행하기 위해 **Get-CsAddressBookConfiguration** cmdlet을 추가 매개 변수 없이 사용하여 조직에서 사용하도록 구성된 모든 주소록 설정 컬렉션을 반환합니다. 이 컬렉션은 KeepDuration 속성이 30일 미만인 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그러면 이 필터링된 컬렉션이 **Set-CsAddressBookConfiguration** cmdlet에 파이프되어 컬렉션의 각 항목에 대한 KeepDuration 속성 값이 30일로 변경됩니다.

    Get-CsAddressBookConfiguration | Where-Object {$_.KeepDuration -lt 30} | Set-CsAddressBookConfiguration -KeepDuration 30

## 자세한 정보

주소록 서버는 AD DS와 Lync Server 사이의 중재자입니다. 주소록 서버를 사용하면 Lync Server에 저장된 사용자 정보와 AD DS에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다.

그뿐만 아니라 주소록 서버는 Lync를 실행하는 컴퓨터로 다운로드되는 인덱스 파일을 주기적으로 생성합니다. 사용자가 연락처를 검색하면 이러한 인덱스 파일 또는 중앙 관리 저장소에 저장된 주소록 인덱스 파일이 검색됩니다.

주소록 서버는 주소록 구성 설정을 사용하여 관리됩니다. 이러한 설정은 주소록 파일이 사용자 데이터베이스와 동기화되는 빈도 및 주소록 인덱스 파일이 생성되는 빈도 등을 결정합니다. Lync Server를 설치하면 전체 주소록 설정 집합이 만들어집니다. 개별 사이트에 적용할 수 있는 사용자 지정 구성 설정을 생성할 수도 있습니다. 이러한 설정(있는 경우)은 사이트에서 작동하는 모든 주소록 서버에 적용되며 항상 전역 설정보다 우선합니다.

**Set-CsAddressBookConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 주소록 구성 설정 컬렉션을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAddressBookConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAddressBookConfiguration"}

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
<td><p><em>EnableFileGeneration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 주소록 서버에서 클라이언트가 다운로드할 수 있는 주소록 인덱스 파일을 생성합니다. False로 설정하면 이러한 인덱스 파일이 생성되지 않습니다. 즉, 클라이언트 응용 프로그램에서 연락처를 검색할 때 주소록 웹 쿼리 서비스를 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePhotoSearch</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자 사진이 검색 결과에 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>주소록 설정 컬렉션에 할당할 고유 식별자입니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. Identity를 지정할 때 와일드카드 문자를 사용할 수 없습니다.</p>
<p>이 매개 변수를 생략하면 <strong>Set-CsAddressBookConfiguration</strong> cmdlet이 전역 설정을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreGenericRules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>주소록 서버에서 전화 번호를 구문 분석할 때 사용되는 일반 정규화 규칙을 무시할지 여부를 나타냅니다. 일반 규칙은 Lync Server에서 기본 제공하는 규칙입니다. 일반 규칙은 변경할 수 없습니다. 그러나 이 속성의 값을 True로 설정하여 주소록 서버에서 이러한 규칙을 무시하고 대신 사용자가 만든 사용자 지정 규칙을 사용하도록 지시할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>AddressBookSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepDuration</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>주소록 서버에서 변경 파일을 유지하는 시간(일)을 지정합니다. KeepDuration 속성 값보다 오래된 변경 파일은 삭제됩니다. KeepDuration은 1에서 90(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 30일입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxDeltaFileSizePercentage</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>Active Directory를 변경(예: Lync Server에 대해 새 사용자를 사용하도록 설정)할 때 주소록 서버에서는 일반적으로 이러한 변경 사항을 업데이트된 정보로만 구성된 파일인 &quot;델타 파일&quot;에 기록합니다. 따라서 Lync는 전체 주소록 파일이 아니라 델타 파일을 다운로드할 수 있습니다. MaxDeltaFileSizePercentage 속성은 델타 파일이 전체 주소록 파일로 통합될 때까지 유지되는 델타 파일의 크기를 결정합니다. 기본적으로 델타 파일이 전체 주소록 파일의 20%를 초과하면 새 주소록 파일이 생성됩니다. 이때 Lync 클라이언트에서 델타 파일이 아니라 전체 파일을 다운로드합니다.</p>
<p>MaxDeltaFileSizePercentage는 1-100(포함) 사이의 백분율 값으로 입력해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxFileShareThreadCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>서비스 파일 공유에 연결하는 데 문제가 있을 경우 주소록 서버에서 사용될 수 있는 최대 시스템 리소스 수를 지정합니다. 기본값은 300입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RunTimeOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>서버에서 새 주소록 파일을 생성하는 시간을 나타냅니다. RunTimeOfDay 속성은 00:00:00이 자정을 나타내고 23:59:00이 오후 11시 59분을 나타내는 24시간제(시간:분:초) 형식을 기반으로 합니다.</p>
<p>기본값은 01:30:00(오후 1시 30분)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SynchronizePollingInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>주소록 서버가 정보를 사용자 데이터베이스에 저장된 정보와 동기화하는 빈도를 나타냅니다. SynchronizePollingInterval은 5초(00:00:05)에서 3시간(03:00:00) 사이의 값으로 설정할 수 있습니다. 기본값은 5분(00:05:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseNormalizationRules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>주소록 서버가 전화 번호를 검색할 때 전화 정규화 규칙을 사용해야 할지를 나타냅니다. False로 설정하면 전화 번호가 있는 그대로 검색되며, 이러한 번호를 표시할 때 정규화 규칙의 적용 여부는 클라이언트 응용 프로그램에 따라 다릅니다.</p>
<p>기본값은 True입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings 개체입니다. **Set-CsAddressBookConfiguration** cmdlet은 주소록 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsAddressBookConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)  
[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)  
[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

