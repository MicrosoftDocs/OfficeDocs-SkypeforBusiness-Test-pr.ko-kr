---
title: Grant-CsExternalAccessPolicy
TOCTitle: Grant-CsExternalAccessPolicy
ms:assetid: 451fef34-3021-4261-8494-b36420b04c82
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425942(v=OCS.15)
ms:contentKeyID: 49303484
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsExternalAccessPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 외부 액세스 정책을 할당할 수 있습니다. 외부 액세스 정책은 사용자가 1) 페더레이션 조직의 SIP(Session Initiation Protocol) 계정을 가진 사용자와 통신할 수 있는지 여부, 2) MSN과 같은 공용 메신저 공급자의 SIP 계정을 가진 사용자와 통신할 수 있는지 여부 및 3) 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스할 수 있는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsExternalAccessPolicy -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-PolicyName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Active Directory 표시 이름이 Ken Myer인 사용자에게 외부 액세스 정책 RedmondAccessPolicy를 할당합니다.

    Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName RedmondAccessPolicy

## 예제 2

예제 2에 표시된 명령은 Redmond 시에서 일하는 모든 사용자에게 외부 액세스 정책 RedmondAccessPolicy를 할당합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsUser** 및 LdapFilter 매개 변수를 사용하여 Redmond에서 근무하는 모든 사용자의 컬렉션을 반환합니다. 필터 값 "l=Redmond"(여기서 l은 구/군/시를 나타내는 소문자 L)는 Redmond 시에서 근무하는 사용자에 대한 데이터만 반환하도록 제한합니다. 그런 다음 해당 컬렉션은 컬렉션의 각 사용자에게 RedmondAccessPolicy 정책을 할당하는 **Grant-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsExternalAccessPolicy -PolicyName RedmondAccessPolicy

## 예제 3

예제 3에서는 직위가 "영업 사원"인 모든 사용자에게 외부 액세스 정책 SalesAccessPolicy가 할당됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 모든 Sales Representatives 컬렉션을 반환합니다. 필터 값 "Title=Sales Representative"는 직위가 "Sales Representative"인 사용자에 대한 컬렉션만 반환하도록 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 사용자에게 SalesAccessPolicy를 할당하는 **Grant-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "Title=Sales Representative" | Grant-CsExternalAccessPolicy -PolicyName SalesAccessPolicy

## 예제 4

예제 4에 표시된 명령은 사용자별 정책이 명시적으로 할당된 모든 사용자에게 외부 액세스 정책 BasicAccessPolicy를 할당합니다. 즉, 사용자는 현재 사이트 정책 또는 전역 정책에 의해 관리되고 있습니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet 및 Filter 매개 변수를 사용하여 적절한 사용자 집합을 반환합니다. 필터 값 {ExternalAccessPolicy -eq $Null}은 ExternalAccessPolicy 속성이 null 값($Null)과 같은(-eq) 사용자 계정에 대한 데이터만 반환하도록 제한합니다. 정의에 따라 ExternalAccessPolicy는 사용자에게 사용자별 정책이 할당되지 않은 경우에만 null이 됩니다.

    Get-CsUser -Filter {ExternalAccessPolicy -eq $Null} | Grant-CsExternalAccessPolicy -PolicyName BasicAccessPolicy

## 예제 5

예제 5에서는 US OU(조직 구성 단위)에 계정이 있는 모든 사용자에게 외부 액세스 정책 USAccessPolicy를 할당합니다. 먼저 **Get-CsUser** cmdlet 및 OU 매개 변수를 호출합니다. 매개 변수 값 "ou=US,dc=litwareinc,dc=com"은 US OU에서 검색한 사용자 계정에 대한 데이터만 반환하도록 제한합니다. 반환된 컬렉션은 컬렉션의 각 사용자에게 USAccessPolicy 정책을 할당하는 **Grant-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "ou=US,dc=litwareinc,dc=com" | Grant-CsExternalAccessPolicy -PolicyName USAccessPolicy

## 예제 6

예제 6에서는 Lync Server를 사용할 수 있도록 설정된 사용자에게 이전에 할당된 사용자별 외부 액세스 정책의 할당을 취소합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsUser** cmdlet을 호출하여 Lync Server를 사용할 수 있도록 설정된 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 "-PolicyName $Null" 구문을 사용하여 이러한 사용자에게 이전에 할당된 모든 사용자별 외부 액세스 정책을 제거하는 **Grant-CsExternalAccessPolicy** cmdlet에 파이프됩니다.

    Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName $Null

## 자세한 정보

Lync Server를 설치하면 내부 사용자들만 서로 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 기본적으로 Active Directory 도메인 서비스에 SIP 계정이 있는 다른 사용자와만 통신할 수 있습니다. 또한 인터넷을 통해 Lync Server에 액세스할 수 없습니다. 대신 Lync Server에 로그온하려면 먼저 내부 네트워크에 로그온해야 합니다.

대부분의 사용자는 이것만으로 통신 요구 사항이 충족됩니다. 요구 사항이 충족되지 않는 경우 외부 액세스 정책을 사용하여 사용자가 통신하고 공동 작업할 수 있는 권한을 확장할 수 있습니다. 외부 액세스 정책은 사용자에게 다음 중 일부 또는 전부를 수행할 수 있는 권한을 부여하거나 해지할 수 있습니다.

1\. 페더레이션 조직의 SIP 계정을 가진 사용자와 통신합니다. 페더레이션을 사용하도록 설정하는 것만으로는 이러한 기능이 자동으로 제공되지 않습니다. 대신 페더레이션을 사용하도록 설정한 다음, 사용자에게 페더레이션 사용자와 통신할 권한을 제공하는 외부 액세스 정책을 할당해야 합니다.

2\. MSN과 같은 공용 메시지 서비스의 SIP 계정을 가진 사용자와 통신합니다.

3\. 내부 네트워크에 로그온하지 않고도 인터넷을 통해 Lync Server에 액세스 - 이 경우 사용자는 인터넷 카페 또는 기타 원격 위치에서 Lync를 사용하고 Lync Server에 로그온할 수 있습니다.

Lync Server를 설치하면 전역 외부 액세스 정책이 자동으로 만들어집니다. 이 전역 정책 외에도 **New-CsExternalAccessPolicy** cmdlet을 사용하여 사이트 또는 사용자별 범위에 구성된 추가 외부 액세스 정책을 만들 수 있습니다.

사이트 범위에 정책을 만들면 해당 정책이 해당 사이트에 자동으로 할당됩니다. 예를 들어 ID가 site:Redmond인 외부 액세스 정책은 레드몬드 사이트에 자동으로 할당됩니다. 반면 사용자별 범위에 생성된 정책은 사용자에게 자동으로 할당되지 않습니다. 대신 이러한 정책을 사용자 또는 사용자 그룹에 명시적으로 할당해야 합니다. 사용자별 정책 할당은 **Grant-CsExternalAccessPolicy** cmdlet의 작업입니다.

사용자별 정책은 항상 사이트 정책 및 전역 정책에 우선합니다. 예를 들어 페더레이션 사용자와의 통신을 허용하는 사용자별 정책을 만들고 해당 정책을 Ken Myer에게 할당하는 경우를 가정해 보겠습니다. 해당 정책이 적용되어 있는 한 Ken은 Ken의 사이트 정책 또는 전역 정책에서 허용하지 않더라도 페더레이션 사용자와 통신할 수 있습니다. 사용자별 정책 설정이 우선하기 때문입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsExternalAccessPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsExternalAccessPolicy"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>정책을 할당할 사용자 계정의 ID입니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>또한 사용자 ID를 지정할 때 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot;Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 정책을 할당할 때 연결할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 <strong>Grant-CsExternalAccessPolicy</strong> cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsExternalAccessPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PolicyName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondAccessPolicy인 정책의 PolicyName은 RedmondAccessPolicy와 같습니다.</p>
<p>사용자에게 이전에 할당된 사용자별 정책을 할당 취소하려면 PolicyName 매개 변수를 $Null로 설정합니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsExternalAccessPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsExternalAccessPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함한 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

