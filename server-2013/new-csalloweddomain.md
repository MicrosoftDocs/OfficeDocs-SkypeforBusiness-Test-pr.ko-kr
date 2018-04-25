---
title: New-CsAllowedDomain
TOCTitle: New-CsAllowedDomain
ms:assetid: 7e040cf8-8e6f-4293-b7c4-1be76053d43d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398628(v=OCS.15)
ms:contentKeyID: 49304166
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAllowedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션에 대해 승인된 도메인 목록에 도메인을 추가합니다. 도메인이 허용 목록에 추가되어 페더레이션이 승인되었다는 것은 사용자가 페더레이션 도메인의 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있음을 의미합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAllowedDomain -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    New-CsAllowedDomain -Domain <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Comment <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MarkForMonitoring <$true | $false>] [-ProxyFqdn <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 도메인 fabrikam.com이 허용 도메인 목록에 추가됩니다. 이 작업을 수행하기 위해 Identity 매개 변수와 함께 **New-CsAllowedDomain** cmdlet을 호출합니다. Identity에는 허용 목록에 추가할 도메인 이름이 할당됩니다. fabrikam.com이 허용 목록 또는 차단 목록에 이미 있는 경우에는 명령이 실패합니다.

    New-CsAllowedDomain -Identity "fabrikam.com"

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우 두 개의 추가 매개 변수가 Identity와 함께 포함됩니다. ProxyFqdn은 fabrikam.com에 대한 프록시 서버의 FQDN을 지정하는 데 사용되고, MarkForMonitoring은 모니터링 서버가 모니터링하는 항목 목록에 이 페더레이션 연결을 추가하는 데 사용됩니다.

    New-CsAllowedDomain -Identity "fabrikam.com" -ProxyFqdn "proxyserver.fabrikam.com" -MarkForMonitoring $True -Comment "Contact: Ken Myer (kenmyer@fabrikam.com)"

## 예제 3

예제 3에서는 InMemory 매개 변수를 사용하여 초기에 메모리에만 존재하는 새 허용 도메인을 만드는 방법을 보여 줍니다. 메모리에만 나타나는 이 도메인의 속성 값을 수정한 후에는 **Set-CsAllowedDomain** cmdlet을 호출하여 해당 도메인을 허용 목록에 추가할 수 있습니다.

이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsAllowedDomain** cmdlet 및 InMemory 매개 변수를 사용하여 ID가 fabrikam.com인 허용 도메인을 만듭니다. 이 가상 도메인은 변수 $x에 저장됩니다.

두 번째, 세 번째 및 네 번째 줄은 각각 ProxyFqdn, MarkForMonitoring 및 Comment 속성 값을 수정하는 데 사용됩니다. 모든 속성 값이 수정된 후 마지막 명령은 **Set-CsAllowedDomain** cmdlet을 사용하여 허용 도메인 목록에 가상 도메인을 추가합니다. **Set-CsAllowedDomain** cmdlet을 호출할 때까지 fabrikam.com은 메모리에만 존재합니다. 예제의 마지막 줄 전에 **Get-CsAllowedDomain** cmdlet을 실행하면 fabrikam.com이 허용 도메인 목록에 표시되지 않습니다. Fabrikam.com은 **Set-CsAllowedDomain** cmdlet을 호출해야 허용 목록에 표시됩니다.

    $x = New-CsAllowedDomain -Identity "fabrikam.com" -InMemory
    $x.ProxyFqdn = "proxyserver.fabrikam.com" 
    $x.MarkForMonitoring = $True 
    $x.Comment = "Contact: Ken Myer (kenmyer@fabrikam.com)"
    Set-CsAllowedDomain -Instance $x

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과의 직접 페더레이션을 설정하려면 몇 가지 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 Lync Server 액세스 에지 서비스를 실행하는 서버를 설정해야 합니다. 또한 상대방 조직에서 사용자와의 페더레이션을 설정해야 합니다. 두 당사자 중 하나라도 관계에 동의하지 않으면 페더레이션을 설정할 수 없습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록인 허용 목록과 차단 목록을 관리해야 할 수도 있습니다. 허용 목록은 페더레이션하기로 선택한 조직을 나타냅니다. 도메인이 허용 목록에 표시되면 구성 설정에 따라 사용자가 해당 페더레이션 도메인의 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

새 페더레이션 관계를 생성하려면 **New-CsAllowedDomain** cmdlet을 사용하여 도메인을 허용 도메인 목록에 추가할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAllowedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAllowedDomain"}

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
<td><p><em>Domain</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>허용 목록에 추가할 도메인의 FQDN(예: fabrikam.com)입니다. Identity 또는 Domain 매개 변수(둘 중 하나만)를 사용하여 도메인 이름을 지정할 수 있습니다. Identity를 사용하면 Domain 속성이 Identity에 할당된 값으로 설정되고, Domain을 사용하면 Identity 속성이 Domain에 할당된 값으로 설정됩니다.</p>
<p>도메인은 고유해야 합니다. 지정된 도메인이 차단 또는 허용 목록에 이미 있는 경우에는 명령이 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>허용 목록에 추가할 도메인의 FQDN(정규화된 도메인 이름)입니다(예: fabrikam.com). Identity 또는 Domain 매개 변수(둘 중 하나만)를 사용하여 도메인 이름을 지정할 수 있습니다. Identity를 사용하면 Domain 속성이 Identity에 할당된 값으로 설정되고, Domain을 사용하면 Identity 속성이 Domain에 할당된 값으로 설정됩니다.</p>
<p>ID는 고유해야 합니다. 지정된 도메인이 차단 또는 허용 목록에 이미 있는 경우에는 명령이 실패합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Comment</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>선택적 문자열 값은 허용 목록에 추가되는 도메인에 대한 추가 정보를 제공합니다. 예를 들어, 페더레이션 도메인에 대한 대화 상대 정보를 제공하는 설명을 추가할 수 있습니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MarkForMonitoring</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모니터링 서버에서 사용자 도메인과 원격 도메인 간의 페더레이션 연결을 모니터링할지 여부를 나타냅니다. 기본적으로 MarkForMonitoring은 False로 설정되므로 연결이 모니터링되지 않습니다.</p>
<p>모니터링 서버를 배포하지 않은 경우 이 속성이 무시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>허용 목록에 추가할 도메인에 배포된 SIP 프록시 서버의 FQDN(정규화된 도메인 이름)입니다(예: proxy-server.fabrikam.com). 이 속성은 선택 사항입니다. 이 매개 변수를 지정하지 않으면 DNS SRV 검색 프로시저를 통해 SIP 프록시 서버의 위치가 결정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsAllowedDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsAllowedDomain](get-csalloweddomain.md)  
[Remove-CsAllowedDomain](remove-csalloweddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)  
[Set-CsAllowedDomain](set-csalloweddomain.md)

