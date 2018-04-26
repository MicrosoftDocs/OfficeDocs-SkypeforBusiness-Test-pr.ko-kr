---
title: Get-CsUserServicesConfiguration
TOCTitle: Get-CsUserServicesConfiguration
ms:assetid: 07884f7a-d9f7-4a3f-a5ef-7f4ba71c2769
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398133(v=OCS.15)
ms:contentKeyID: 49302710
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserServicesConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 User Services 구성 설정에 대한 정보를 반환합니다. User Services 서비스는 현재 상태 정보를 유지 관리하고 전화 회의를 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUserServicesConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsUserServicesConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 User Services 구성 설정의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsUserServicesConfiguration** cmdlet을 추가 매개 변수 없이 호출합니다.

    Get-CsUserServicesConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 User Services 구성 설정 컬렉션만 반환합니다. ID는 고유해야 하므로 이 명령은 항목을 한 개 이하만 반환할 수 있습니다.

    Get-CsUserServicesConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 서비스 수준에 적용된 모든 User Services 구성 설정의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsUserServicesConfiguration** cmdlet을 -Filter 매개 변수와 함께 호출합니다. 필터 값 "service:\*"는 반환되는 데이터를 ID가 "service:" 문자로 시작하는 설정으로 제한합니다. 정의에 따라 서비스 범위에 구성된 설정이 반환됩니다.

    Get-CsUserServicesConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 사용자가 250개 이상의 연락처를 가질 수 있도록 허용하는 모든 User Services 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUserServicesConfiguration** cmdlet을 추가 매개 변수 없이 호출하여 현재 사용 중인 모든 User Services 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 MaxContacts 속성이 250보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 250}

## 예제 5

예제 5에서는 익명 사용자 유예 기간이 10분보다 긴 User Services 구성 설정에 대한 정보를 보고합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUserServicesConfiguration** cmdlet을 추가 매개 변수 없이 호출하여 조직에서 사용 중인 모든 User Services 구성 설정의 컬렉션을 반환합니다. 반환된 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 여기서는 AnonymousUserGracePeriod 속성이 10분(00시간: 10분: 00초)보다 큰 설정만 선택합니다.

    Get-CsUserServicesConfiguration | Where-Object {$_.AnonymousUserGracePeriod -gt "00:10:00"}

## 자세한 정보

Lync Server는 User Services 서비스를 사용하여 사용자의 현재 상태 정보를 유지 관리하고 모임 및 전화 회의를 관리합니다. 그런 다음 **CsUserServicesConfiguration** cmdlet을 사용하여 전역, 사이트 및 서비스 범위에서 User Services 설정을 관리합니다. User Services 구성 설정을 호스트할 수 있는 서비스는 User Services 자체뿐입니다. 이러한 설정은 사용자가 가질 수 있는 연락처 수, 사용자가 한 번에 예약할 수 있는 모임 수, 전화 회의가 활성 상태로 남아 있을 수 있는 시간 등을 결정합니다.

**Get-CsUserServicesConfiguration** cmdlet을 통해 관리자는 현재 사용 중인 모든 User Services 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins그룹의 구성원은 **Get-CsUserServicesConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserServicesConfiguration"}

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
<td><p>User Services 구성 설정의 컬렉션을 하나 이상 검색할 때 와일드카드를 활용하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용하고, 서비스 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;service:*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 User Services 구성 설정에 대한 고유한 식별자입니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 반환하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 반환하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p>
<p>이 매개 변수가 생략된 경우 <strong>Get-CsUserServicesConfiguration</strong> cmdlet은 현재 조직에서 사용 중인 모든 User Services 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 User Services 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUserServicesConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUserServicesConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)  
[Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)  
[Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

