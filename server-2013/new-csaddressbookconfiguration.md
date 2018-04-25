---
title: New-CsAddressBookConfiguration
TOCTitle: New-CsAddressBookConfiguration
ms:assetid: 5a92a2b0-c46e-44e3-b07c-fc9ff0d33b2b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398395(v=OCS.15)
ms:contentKeyID: 49303736
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

주소록 구성 설정의 새 컬렉션을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAddressBookConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableFileGeneration <$true | $false>] [-EnablePhotoSearch <$true | $false>] [-Force <SwitchParameter>] [-IgnoreGenericRules <$true | $false>] [-InMemory <SwitchParameter>] [-KeepDuration <UInt32>] [-MaxDeltaFileSizePercentage <UInt32>] [-MaxFileShareThreadCount <Int32>] [-RunTimeOfDay <DateTime>] [-SynchronizePollingInterval <TimeSpan>] [-UseNormalizationRules <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID site:Redmond를 사용하여 주소록 구성 설정의 새 컬렉션을 만듭니다. 새 컬렉션을 만들려면 Identity 매개 변수 및 기타 선택적 매개 변수(예: KeepDuration 및 SynchronizePollingInterval)와 함께 **New-CsAddressBookConfiguration** cmdlet을 호출해야 합니다.

    New-CsAddressBookConfiguration -Identity site:Redmond -KeepDuration 15 -SynchronizePollingInterval 00:10:00

## 예제 2

예제 2에서는 Paris 사이트에 대한 주소록 설정의 새 컬렉션을 만듭니다. 이 새 컬렉션에서는 Redmond 사이트에 대해 구성된 주소록 설정에서 복사한 두 값(KeepDuration 및 SynchronizePollingInterval)을 사용합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Get-CsAddressBookConfiguration** cmdlet을 사용하여 Redmond 사이트에 대해 구성된 모든 주소록 설정의 컬렉션을 반환합니다. 이 정보는 $x라는 변수에 저장됩니다.

두 번째 명령은 **New-CsAddressBookConfiguration** cmdlet을 사용하여 Pairs 사이트에 대한 주소록 설정을 만듭니다. 이 명령에는 site:Redmond에서 복사된 값을 포함하는 두 가지 선택적 매개 변수인 KeepDuration 및 SynchronizePollingInterval이 포함됩니다. 예를 들어 KeepDuration은 매개 변수 값 $x.KeepDuration을 사용하는데, 이 매개 변수 값은 Redmond 사이트에서 복사된 KeepDuration 정보를 나타냅니다.

    $x = Get-CsAddressBookConfiguration -Identity site:Redmond
    New-CsAddressBookConfiguration -Identity site:Paris -KeepDuration $x.KeepDuration -SynchronizePollingInterval $x.SynchronizePollingInterval

## 예제 3

예제 3에서는 InMemory 매개 변수를 사용하여 주소록 설정 컬렉션의 메모리 내 전용 인스턴스를 생성하고, 메모리에서 해당 설정을 수정한 다음, **Set-CsAddressBookConfiguration** cmdlet을 사용하여 ID site:Redmond로 실제 컬렉션을 생성하는 방법을 보여 줍니다. 이 모두를 수행하기 위해 첫 번째 명령은 주소록 설정 구성의 새로운 메모리 내 전용 인스턴스를 생성하여 해당 인스턴스를 변수 $x에 저장합니다. InMemory 매개 변수는 이러한 주소록 설정이 메모리에만 존재하도록 합니다. Lync Server 세션을 종료하거나 변수 $x를 삭제하면 설정이 사라지고 Redmond 사이트에 적용되지 않습니다.

두 번째 및 세 번째 명령에서는 이러한 가상 주소록 설정의 두 가지 속성을 수정합니다. 두 번째 명령은 KeepDuration 속성 값을 15일로 설정하고, 세 번째 명령은 SynchronizePollingInterval을 10분(00:10:00)으로 설정합니다. 그런 다음 네 번째 마지막 명령은 **Set-CsAddressBookConfiguration** cmdlet 및 Instance 매개 변수를 사용하여 가상 주소록 설정을 Redmond 사이트에서 구성된 설정의 실제 컬렉션으로 변환합니다.

    $x = New-CsAddressBookConfiguration -Identity site:Redmond -InMemory
    $x.KeepDuration = 15
    $x.SynchronizePollingInterval = "00:10:00"
    Set-CsAddressBookConfiguration -Instance $x

## 자세한 정보

주소록 서버는 AD DS와 Lync Server 사이의 중재자입니다. 주소록 서버를 사용하면 Lync Server에 저장된 사용자 정보와 AD DS에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다.

그뿐만 아니라 주소록 서버는 Lync를 실행하는 컴퓨터로 다운로드되는 인덱스 파일을 주기적으로 생성합니다. 사용자가 연락처를 검색하면 이러한 인덱스 파일 또는 중앙 관리 저장소에 저장된 주소록 인덱스 파일이 검색됩니다.

주소록 서버는 주소록 구성 설정을 사용하여 관리됩니다. 이러한 설정은 주소록 파일이 사용자 데이터베이스와 동기화되는 빈도 및 주소록 인덱스 파일이 생성되는 빈도 등을 결정합니다. Lync Server를 설치하면 전체 주소록 설정 집합이 만들어집니다. 개별 사이트에 적용할 수 있는 사용자 지정 구성 설정을 생성할 수도 있습니다. 이러한 설정(있는 경우)은 사이트에서 작동하는 모든 주소록 서버에 적용되며 항상 전역 설정보다 우선합니다.

사이트 수준 설정은 **New-CsAddressBookConfiguration** cmdlet을 사용하여 만듭니다. 사이트 범위에서만 설정을 생성할 수 있습니다. 전역 범위를 비롯하여 다른 범위에서 새 설정을 만들려고 하면 명령이 실패합니다. 해당 사이트에 이미 주소록 설정 컬렉션이 포함된 경우에도 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAddressBookConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAddressBookConfiguration"}

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
<td><p>주소록 설정의 새 컬렉션에 할당할 고유 식별자입니다. 사이트 범위에서만 새 컬렉션을 생성할 수 있기 때문에 ID의 접두사는 항상 &quot;site:&quot;이며 그 뒤에 사이트 이름이 옵니다(예: &quot;site:Redmond&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableFileGeneration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 주소록 서버에서 클라이언트가 다운로드할 수 있는 주소록 인덱스 파일을 생성합니다. False로 설정하면 이러한 인덱스 파일이 생성되지 않습니다. 즉, 클라이언트 응용 프로그램에서 연락처를 검색할 때 주소록 웹 쿼리 서비스를 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePhotoSearch</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자 사진이 검색 결과에 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreGenericRules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>주소록 서버에서 전화 번호를 구문 분석할 때 사용되는 일반 정규화 규칙을 무시할지 여부를 나타냅니다. 일반 규칙은 Lync Server에서 기본 제공하는 규칙입니다. 일반 규칙은 변경할 수 없습니다. 그러나 이 속성의 값을 True로 설정하여 주소록 서버에서 이러한 규칙을 무시하고 대신 사용자가 만든 사용자 지정 규칙을 사용하도록 지시할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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
<td><p>Lync Server에 대해 새 사용자를 활성화하는 등 Active Directory를 변경할 경우 주소록 서버는 일반적으로 이러한 변경 내용을 업데이트된 정보로만 구성된 파일인 &quot;델타 파일&quot;에 기록합니다. 그러면 Lync는 전체 주소록 파일이 아니라 델타 파일을 다운로드할 수 있습니다. MaxDeltaFileSizePercentage 속성은 델타 파일이 전체 주소록 파일로 통합될 때까지 유지되는 델타 파일의 크기를 결정합니다. 기본적으로 델타 파일이 전체 주소록 파일의 20%를 초과하면 새 주소록 파일이 생성됩니다. 이때 Lync 클라이언트에서 델타 파일이 아니라 전체 파일을 다운로드합니다.</p>
<p>MaxDeltaFileSizePercentage는 1에서 100(포함) 사이의 백분율 값으로 입력해야 합니다.</p></td>
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

없음. **New-CsAddressBookConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WriteableConfig.Settings.AddressBook.AddressBookSettings 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)  
[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

