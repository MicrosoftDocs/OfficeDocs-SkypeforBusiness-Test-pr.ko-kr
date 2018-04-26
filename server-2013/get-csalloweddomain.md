---
title: Get-CsAllowedDomain
TOCTitle: Get-CsAllowedDomain
ms:assetid: 0b693788-2270-4bf3-b899-f5cf4321351b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398164(v=OCS.15)
ms:contentKeyID: 49302766
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAllowedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션이 승인된 도메인 목록에 포함된 도메인에 대한 정보를 반환합니다. 도메인이 허용 목록에 추가되어 페더레이션이 승인된 후에는 사용자가 해당 도메인의 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAllowedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsAllowedDomain [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 페더레이션이 승인된 도메인 목록에 포함된 모든 도메인 컬렉션을 반환합니다. 추가 매개 변수 없이 **Get-CsAllowedDomain** cmdlet을 호출하면 항상 승인된 도메인의 전체 컬렉션이 반환됩니다.

    Get-CsAllowedDomain

## 예제 2

예제 2에서는 ID가 "fabrikam.com"인 허용 도메인에 대한 정보를 반환합니다. ID가 고유해야 하므로 이 명령은 둘 이상의 항목을 반환하지 않습니다.

    Get-CsAllowedDomain -Identity fabrikam.com

## 예제 3

예제 3에 표시된 명령은 Identity에 문자열 값 "fabrikam"이 포함된 모든 허용 도메인 컬렉션을 반환합니다. 이를 위해 명령에 Filter 매개 변수와 필터 값 "\*fabrikam\*"가 사용됩니다. 이 필터 값은 Identity(이 속성만 필터링할 수 있음)에 문자열 값 "fabrikam"이 포함된 도메인만 반환하도록 **Get-CsAllowedDomain** cmdlet에 지시합니다. 이 명령은 fabrikam.com, fabrikam.net, africa.fabrikam.org 등의 도메인을 모두 반환합니다.

    Get-CsAllowedDomain -Filter *fabrikam*

## 예제 4

예제 4에서는 **Get-CsAllowedDomain** cmdlet 및 **Where-Object** cmdlet을 사용하여 ProxyFqdn 속성 값이 입력되지 않은 경우 모든 도메인 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 추가 매개 변수 없이 **Get-CsAllowedDomain** cmdlet을 호출하여 모든 허용 도메인의 컬렉션을 반환합니다. 이 컬렉션은 ProxyFqdn 속성이 Null 값(ProxyFqdn에 대해 입력된 값이 없음을 의미함)과 같은 허용 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다. ProxyFqdn 속성에 대해 구성된 값이 있는 모든 도메인을 찾으려면 대신 다음 구문을 사용합니다.

Where-Object {$\_.ProxyFqdn -ne $Null}

    Get-CsAllowedDomain | Where-Object {$_.ProxyFqdn -eq $Null}

## 예제 5

예제 5에서는 모니터링 서버에서 상태를 확인한 모든 허용 도메인을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsAllowedDomain** cmdlet을 사용하여 허용 도메인 목록에 있는 모든 도메인의 컬렉션을 반환합니다. 이 컬렉션은 MarkForMonitoring 속성이 True인 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAllowedDomain | Where-Object {$_.MarkForMonitoring -eq $True}

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과의 직접 페더레이션을 설정하려면 몇 가지 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 액세스 에지 서버를 설정해야 합니다. 또한 상대방 조직에서 사용자와의 페더레이션을 설정해야 합니다. 두 당사자 중 하나라도 관계에 동의하지 않으면 페더레이션을 설정할 수 없습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록인 허용 목록과 차단 목록을 관리해야 할 수도 있습니다. 허용 목록(EnablePartnerDiscovery를 사용하지 않는 경우에 필요함)은 페더레이션하도록 선택한 조직을 나타냅니다. 도메인이 허용 목록에 표시되면 구성 설정에 따라 사용자가 해당 페더레이션 도메인의 계정을 가진 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

**Get-CsAllowedDomain** cmdlet을 통해 허용된 도메인 목록에 있는 모든 도메인에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAllowedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAllowedDomain"}

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
<td><p>허용 도메인 목록에서 하나 이상의 도메인을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. ID가 &quot;r&quot; 문자로 시작하는 모든 도메인을 반환하려면 -Filter r* 구문을 사용합니다. ID가 &quot;.net&quot;으로 끝나는 모든 도메인을 반환하려면 -Filter &quot;*.net&quot; 구문을 사용합니다. ID가 &quot;r&quot; 문자 또는 &quot;g&quot; 문자로 시작하는 모든 도메인을 반환하려면 -Filter [rg]* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 도메인의 이름입니다. 도메인이 FQDN(정규화된 도메인 이름)으로 허용 목록에 나열되므로 지정된 도메인의 ID는 fabrikam.com 또는 contoso.net과 유사합니다. 도메인 ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하여 지정된 도메인(또는 도메인 집합)을 반환하려면 대신 Filter 매개 변수를 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 허용 도메인 목록에 있는 모든 도메인이 반환됩니다.</p></td>
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

없음. **Get-CsAllowedDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsAllowedDomain](new-csalloweddomain.md)  
[Remove-CsAllowedDomain](remove-csalloweddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)  
[Set-CsAllowedDomain](set-csalloweddomain.md)

