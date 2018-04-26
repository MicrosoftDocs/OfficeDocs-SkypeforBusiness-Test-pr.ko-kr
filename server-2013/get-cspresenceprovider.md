---
title: Get-CsPresenceProvider
TOCTitle: Get-CsPresenceProvider
ms:assetid: 15f7a7d0-d6d6-491e-a2e3-04fd2d6528d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204705(v=OCS.15)
ms:contentKeyID: 49302920
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPresenceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 현재 상태 공급자에 대한 정보를 반환합니다. 현재 상태 공급자는 사용자 서비스 구성 설정 컬렉션의 PresenceProviders 속성을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPresenceProvider [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPresenceProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 현재 상태 공급자에 대한 정보를 반환합니다.

    Get-CsPresenceProvider

## 예제 2

예제 2에서는 단일 현재 상태 공급자, 즉 ID가 global/fabrikam.com인 공급자에 대한 정보를 반환합니다.

    Get-CsPresenceProvider -Identity "global/fabrikam.com"

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 현재 상태 공급자에 대한 정보를 반환합니다. 이를 위해 Filter 매개 변수와 필터 값 "site:\*"를 사용합니다. 해당 필터 값은 반환되는 데이터를 ID가 문자열 값 "site:"으로 시작하는 현재 상태 공급자로 제한합니다.

    Get-CsPresenceProvider -Filter "site:*"

## 예제 4

예제 4에서는 Fqdn 속성에 문자열 값 "fabrikam.com"이 포함된 모든 현재 상태 공급자를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPresenceProvider** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 현재 상태 공급자의 컬렉션을 반환합니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 Fqdn 속성에 문자열 값 "fabrikam.com"이 포함된(-match) 공급자만 선택합니다.

    Get-CsPresenceProvider | Where-Object {$_.Fqdn -match "fabrikam.com"}

## 자세한 정보

**CsPresenceProvider** cmdlet은 사용자 서비스구성 설정에 포함된 PresenceProviders 속성을 관리하는 데 사용됩니다. 이 설정의 가장 중요한 용도는 권한이 부여된 현재 상태 공급자 컬렉션을 포함하는 현재 상태 정보를 유지 관리하는 것입니다. 해당 컬렉션은 PresenceProviders 속성에 저장됩니다. Get-CsPresenceProvider cmdlet을 사용하면 조직에서 사용하도록 권한이 부여된 현재 상태 공급자에 대한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPresenceProvider"}

**Lync Server 제어판:** **Get-CsPresenceProvider** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 하나 이상의 현재 상태 공급자 ID를 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 서비스 범위에서 구성된 모든 현재 상태 공급자를 반환하려면 다음 필터 값을 사용합니다.</p>
<p>-Filter &quot;service:*&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>현재 상태 공급자의 고유 식별자입니다. 현재 상태 공급자의 ID는 두 부분, 즉 service:UserServer:atl-cs-001.litwareinc.com과 같은 공급자가 적용된 범위(상위 항목)와 공급자의 정규화된 도메인 이름으로 구성됩니다. 예를 들어 단일 현재 상태 공급자를 검색하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;global/fabrikam.com&quot;</p>
<p>특정 상위 항목에 대한 모든 현재 상태 공급자를 반환하려면 범위만 지정하면 됩니다. 예를 들어 다음 구문은 전역 범위에 대해 구성된 모든 현재 상태 공급자를 반환합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 모두 포함하지 않으면 <strong>Get-CsPresenceProvider</strong> cmdlet은 모든 공급자에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 허용 도메인을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPresenceProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsPresenceProvider](new-cspresenceprovider.md)  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)  
[Set-CsPresenceProvider](set-cspresenceprovider.md)

