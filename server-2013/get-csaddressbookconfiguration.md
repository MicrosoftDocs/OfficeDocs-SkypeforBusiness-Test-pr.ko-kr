---
title: Get-CsAddressBookConfiguration
TOCTitle: Get-CsAddressBookConfiguration
ms:assetid: 07757a19-f819-4d65-82da-50bf2f157a9b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398132(v=OCS.15)
ms:contentKeyID: 49302707
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAddressBookConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

주소록 구성 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAddressBookConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAddressBookConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용 중인 모든 주소록 구성 설정에 대한 정보를 반환합니다. 이는 **Get-CsAddressBookConfiguration** cmdlet을 추가 매개 변수 없이 호출했을 때의 기본 동작입니다.

    Get-CsAddressBookConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 주소록 구성 설정의 정보를 반환합니다.

    Get-CsAddressBookConfiguration -Identity site:Redmond

## 예제 3

이 예제에서는 Filter 매개 변수와 필터 값 "site:\*"를 사용하여 사이트 범위에 적용된 모든 주소록 구성 설정에 대한 정보를 반환합니다. 입력한 필터 값은 ID가 문자열 값 "site:"으로 시작하는 모든 주소록 설정의 정보를 반환합니다.

    Get-CsAddressBookConfiguration -Filter site:*

## 예제 4

예제 4에서는 전화 번호를 구문 분석할 때 정규화 규칙을 사용하는 주소록 서버의 모든 주소록 설정 구성에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsAddressBookConfiguration** cmdlet을 사용하여 조직의 모든 주소록 설정 컬렉션을 반환합니다. 이 컬렉션은 UseNormalizationRules 속성이 True인 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAddressBookConfiguration | Where-Object {$_.UseNormalizationRules -eq $True}

## 자세한 정보

주소록 서버는 Active Directory 도메인 서비스와 Lync Server 간의 중계자입니다. 주소록 서버는 Lync Server에 저장된 사용자 정보와 Active Directory에 저장된 사용자 정보가 동기화되도록 합니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다.

그뿐만 아니라 주소록 서버는 Lync를 실행하는 컴퓨터로 다운로드되는 인덱스 파일을 주기적으로 생성합니다. 사용자가 연락처를 검색하면 이러한 인덱스 파일 또는 중앙 관리 저장소에 저장된 주소록 인덱스 파일이 검색됩니다.

주소록 서버는 주소록 구성 설정을 사용하여 관리됩니다. 이러한 설정은 주소록 파일이 사용자 데이터베이스와 동기화되는 빈도 및 주소록 인덱스 파일이 생성되는 빈도 등을 결정합니다. Lync Server를 설치하면 전체 주소록 설정 집합이 만들어집니다. 개별 사이트에 적용 가능한 사용자 지정 구성 설정을 만들 수도 있습니다. 이러한 설정(있는 경우)은 사이트에서 작동하는 모든 주소록 서버에 적용되며 항상 전역 설정보다 우선합니다.

**Get-CsAddressBookConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 주소록 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAddressBookConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAddressBookConfiguration"}

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
<td><p>와일드카드 문자는 주소록 설정 컬렉션(또는 여러 컬렉션)을 반환하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용합니다. Identity에 문자열 값 &quot;EMEA&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter *EMEA* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 주소록 설정 컬렉션의 고유 식별자입니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 Filter 매개 변수를 대신 포함하십시오.</p>
<p>이 매개 변수가 지정되지 않은 경우 <strong>Get-CsAddressBookConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 주소록 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 주소록 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAddressBookConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAddressBookConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)  
[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

