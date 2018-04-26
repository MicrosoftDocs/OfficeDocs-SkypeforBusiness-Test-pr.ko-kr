---
title: Remove-CsAddressBookConfiguration
TOCTitle: Remove-CsAddressBookConfiguration
ms:assetid: d634abc2-988a-48f9-ad11-903759516082
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398934(v=OCS.15)
ms:contentKeyID: 49305171
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 주소록 구성 설정 컬렉션을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsAddressBookConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 **Remove-CsAddressBookConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 주소록 구성 설정을 삭제합니다. Identity 매개 변수를 사용하면 지정된 주소록 설정만 제거할 수 있습니다.

    Remove-CsAddressBookConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 주소록 설정 컬렉션이 제거됩니다. 이 작업을 수행하기 위해 **Get-CsAddressBookConfiguration** cmdlet을 사용하여 사이트 범위에서 구성된 모든 주소록 설정 컬렉션을 검색합니다. 이 작업은 Filter 매개 변수와 필터 값 "site:\*"를 사용하여 수행합니다. 검색된 컬렉션은 해당 컬렉션의 모든 항목을 제거하는 **Remove-CsAddressBookConfiguration** cmdlet에 파이프됩니다.

    Get-CsAddressBookConfiguration -Filter site:* | Remove-CsAddressBookConfiguration

## 예제 3

예제 3에서는 변경 파일 보관 기간이 30일 미만인 모든 주소록 설정을 제거합니다. 이 작업을 수행하기 위해 **Get-CsAddressBookConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 주소록 설정 컬렉션을 반환합니다. 이 컬렉션은 KeepDuration 속성이 30일 미만인 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 여기서 30.이라는 구문에 주의하십시오. 일 수 뒤에 마침표를 포함해야 합니다. 마지막으로 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsAddressBookConfiguration** cmdlet에 파이프됩니다.

    Get-CsAddressBookConfiguration | Where-Object {$_.KeepDuration -lt 30.} | Remove-CsAddressBookConfiguration

## 자세한 정보

주소록 서버는 AD DS와 Lync Server 사이의 중재자입니다. 주소록 서버를 사용하면 Lync Server에 저장된 사용자 정보와 AD DS에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다.

그뿐만 아니라 주소록 서버는 Lync Server를 실행하는 컴퓨터로 다운로드되는 인덱스 파일을 주기적으로 생성합니다. 사용자가 연락처를 검색하면 이러한 인덱스 파일 또는 중앙 관리 저장소에 저장된 주소록 인덱스 파일이 검색됩니다.

주소록 서버는 주소록 구성 설정을 사용하여 관리됩니다. 이러한 설정은 주소록 파일이 사용자 데이터베이스와 동기화되는 빈도 및 주소록 인덱스 파일이 생성되는 빈도 등을 결정합니다. Lync Server를 설치하면 전체 주소록 설정 집합이 만들어집니다. 그리고 개별 사이트에 적용할 수 있는 사용자 지정 구성 설정을 만들 수도 있습니다. 이러한 설정(있는 경우)은 사이트에서 작동하는 모든 주소록 서버에 적용되며 항상 전역 설정보다 우선합니다.

**New-CsAddressBookConfiguration** cmdlet을 사용하여 사이트 수준 주소록 구성 설정을 만들 수 있습니다. 나중에 사이트 범위에서 구성한 주소록 설정을 제거하려면 **Remove-CsAddressBookConfiguration** cmdlet을 사용합니다. 전역 설정에 대해 **Remove-CsAddressBookConfiguration** cmdlet을 실행할 수도 있지만 실제로 전역 설정을 제거할 수는 없습니다. 대신 전역 설정에 대해 **Remove-CsAddressBookConfiguration** cmdlet을 실행하면 모든 전역 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsAddressBookConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAddressBookConfiguration"}

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
<td><p>제거할 주소록 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 제거하려면 -Identity global 구문을 사용하고, 전역 설정을 &quot;제거&quot;하면 모든 속성을 기본값으로 간단히 재설정할 수 있습니다. 사이트 컬렉션을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용하십시오. 정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings 개체입니다. **Remove-CsAddressBookConfiguration** cmdlet은 주소록 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsAddressBookConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)  
[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

