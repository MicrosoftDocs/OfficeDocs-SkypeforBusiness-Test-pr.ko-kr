---
title: Get-CsBlockedDomain
TOCTitle: Get-CsBlockedDomain
ms:assetid: 5fa2c2a3-b5e4-430c-970a-0c506a6924b5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398424(v=OCS.15)
ms:contentKeyID: 49303786
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsBlockedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션이 차단된 도메인 목록에 포함된 도메인에 대한 정보를 반환합니다. 사용자는 Lync Server 응용 프로그램을 사용하여 차단된 도메인의 사용자와 통신할 수 없도록 정의되어 있습니다. 예를 들어 사용자는 차단된 목록에 포함된 도메인의 SIP(Session Initiation Protocol) 계정을 소유한 사용자와 Lync를 사용하여 메신저 대화를 교환할 수 없습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsBlockedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsBlockedDomain [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 차단된 도메인 목록에 포함된 모든 도메인의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsBlockedDomain** cmdlet을 호출합니다.

    Get-CsBlockedDomain

## 예제 2

예제 2에서는 차단된 도메인 중 ID "fabrikam.com"을 사용하는 도메인만 반환합니다. 차단 목록의 도메인은 고유한 ID를 가져야 하므로 이 명령은 대부분 단일 항목을 반환합니다.

    Get-CsBlockedDomain -Identity fabrikam.com

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 문자열 값 ".net"으로 끝나는 ID를 가진 모든 차단된 도메인의 컬렉션을 반환합니다. 이 샘플 명령은 northwindtraders.net, contoso.net, fabrikam.net 등의 도메인을 반환합니다.

    Get-CsBlockedDomain -Filter *.net

## 예제 4

예제 4에서는 Comment 속성에 값이 없는 모든 도메인의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsBlockedDomain** cmdlet을 사용하여 차단 목록에 있는 모든 도메인의 컬렉션을 반환합니다. 이 컬렉션은 Comment 속성이 null 값과 같은 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsBlockedDomain | Where-Object {$_.Comment -eq $Null}

## 예제 5

예제 5에서는 Comment 속성에 문자열 값 "Ken Myer"가 포함된 모든 차단된 도메인을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsBlockedDomain** cmdlet을 호출하여 차단된 도메인 목록에 있는 모든 도메인의 컬렉션을 반환합니다. 이 컬렉션은 Comment 속성에 문자열 값 "Ken Myer"가 포함된 도메인을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsBlockedDomain | Where-Object {$_.Comment -match "Ken Myer"}

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과 직접 페더레이션을 설정하려면 여러 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 Lync Server 액세스 에지 서비스를 구성해야 합니다. 또한 다른 조직이 사용자 조직과 페더레이션을 설정해야 합니다. 한 당사자라도 관계에 동의하지 않으면 페더레이션을 설정할 수 없습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록인 허용 목록과 차단 목록을 관리해야 합니다. 허용 목록은 페더레이션하도록 선택한 대상 조직을 나타냅니다. 도메인이 허용 목록에 나타나는 경우 구성 설정에 따라 사용자는 해당 페더레이션 도메인에 계정이 있는 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

**Get-CsBlockedDomain** cmdlet을 사용하면 차단된 도메인 목록에 나타나는 도메인에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsBlockedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsBlockedDomain"}

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
<td><p>차단된 도메인 목록에서 하나 이상의 도메인을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. ID가 &quot;r&quot; 문자로 시작하는 모든 도메인을 반환하려면 -Filter r* 구문을 사용합니다. ID가 &quot;.net&quot;으로 끝나는 모든 도메인을 반환하려면 -Filter &quot;*.net&quot; 구문을 사용합니다. ID가 &quot;f&quot; 문자 또는 &quot;g&quot; 문자로 시작하는 모든 도메인을 반환하려면 -Filter [fg]* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 도메인의 이름입니다. 도메인은 FQDN(정규화된 도메인 이름)별로 차단 목록에 나열되므로, 지정된 도메인의 ID는 fabrikam.com 또는 contoso.net과 유사합니다. 도메인 ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하여 지정된 도메인(또는 도메인 집합)을 반환하려면 대신 Filter 매개 변수를 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 차단된 도메인 목록의 모든 도메인이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 차단된 도메인 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsBlockedDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsBlockedDomain](new-csblockeddomain.md)  
[Remove-CsBlockedDomain](remove-csblockeddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)  
[Set-CsBlockedDomain](set-csblockeddomain.md)

