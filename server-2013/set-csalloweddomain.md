---
title: Set-CsAllowedDomain
TOCTitle: Set-CsAllowedDomain
ms:assetid: d5b25b66-2b11-40ef-9ea4-efcae0b610e6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398931(v=OCS.15)
ms:contentKeyID: 49305154
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAllowedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션이 승인된 도메인 목록에 포함된 도메인의 속성 값을 수정합니다. 도메인이 허용 목록에 추가되어 페더레이션이 승인되었다는 것은 사용자가 페더레이션 도메인의 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있음을 의미합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAllowedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsAllowedDomain [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Comment <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MarkForMonitoring <$true | $false>] [-ProxyFqdn <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "fabrikam.com"인 허용된 도메인의 Comment 속성을 수정합니다. 이 작업을 수행하기 위해 Comment 매개 변수와 적절한 매개 변수 값 "Contact: Ken Myer (kenmyer@fabrikam.com)"를 포함합니다.

    Set-CsAllowedDomain -Identity fabrikam.com -Comment "Contact: Ken Myer (kenmyer@fabrikam.com)"

## 예제 2

예제 2에서는 ID에 문자열 값 "fabrikam"이 포함된 모든 허용된 도메인의 Comment 및 MarkForMonitoring 속성을 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAllowedDomain** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "\*fabrikam\*"는 ID에 문자열 값 "fabrikam"이 포함된 모든 도메인을 반환하도록 **Get-CsAllowedDomain** cmdlet에 지시합니다. 예를 들어 이 명령은 fabrikam.com, us.fabrikam.net 및 fabrikam-users.org와 같은 도메인을 반환합니다. 필터링된 컬렉션은 컬렉션의 각 항목에 대한 MarkForMonitoring 속성을 True($True)로 설정하는 **Set-CsAllowedDomain** cmdlet에 파이프됩니다.

    Get-CsAllowedDomain -Filter *fabrikam* | Set-CsAllowedDomain -Comment "Contact: Ken Myer (kenmyer@fabrikam.com)" -MarkForMonitoring $True

## 예제 3

예제 3에 표시된 명령은 모니터링 서버에서 현재 모니터링하지 않는 허용 목록의 모든 도메인을 수정합니다. 즉, MarkForMonitoring 속성이 False로 설정된 모든 도메인이 여기에 해당합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsAllowedDomain** cmdlet을 호출하여 허용 목록의 모든 도메인 컬렉션을 검색합니다. 이 컬렉션은 MarkForMonitoring이 False와 같은 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 도메인에 대한 MarkForMonitoring 속성을 True로 설정하는 **Set-CsAllowedDomain** cmdlet에 파이프됩니다.

    Get-CsAllowedDomain | Where-Object {$_.MarkForMonitoring -eq $False} | Set-CsAllowedDomain -MarkForMonitoring $True

## 예제 4

예제 4에서는 현재 Comment 속성 값이 없는 허용 목록의 각 도메인에 일반적인 설명("Need contact information.")을 추가합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAllowedDomain** cmdlet을 호출하여 허용 목록의 모든 도메인 컬렉션을 검색합니다. 이 컬렉션은 Comment 속성이 null 값과 같은 도메인을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대한 Comment 속성을 수정하는 **Set-CsAllowedDomain** cmdlet에 파이프됩니다.

    Get-CsAllowedDomain | Where-Object {$_.Comment -eq $Null} | Set-CsAllowedDomain -Comment "Need contact information."

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과의 직접 페더레이션을 설정하려면 몇 가지 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 Lync Server 액세스 에지 서비스를 실행하는 서버를 설정해야 합니다. 또한 상대방 조직에서 사용자와의 페더레이션을 설정해야 합니다. 두 당사자 중 하나라도 관계에 동의하지 않으면 페더레이션을 설정할 수 없습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록을 관리하는 것도 중요합니다. 허용 목록은 페더레이션하도록 선택한 조직을 나타냅니다. 도메인이 허용 목록에 표시되면 구성 설정에 따라 사용자가 해당 페더레이션 도메인의 계정을 가진 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

**Set-CsAllowedDomain** cmdlet을 사용하면 허용된 도메인 목록에 있는 도메인의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAllowedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAllowedDomain"}

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
<td><p><em>Comment</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>수정할 도메인에 대한 추가 정보를 제공하는 선택적 문자열 값입니다. 예를 들어 페더레이션 도메인의 대화 상대 정보를 제공하는 Comment를 추가할 수 있습니다.</p></td>
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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>속성 값을 수정할 허용된 도메인의 FQDN(정규화된 도메인 이름)입니다(예:</p>
<p>-Identity fabrikam.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>차단된 도메인 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MarkForMonitoring</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>모니터링 서버에서 사용자 도메인과 원격 도메인 간의 페더레이션 연결을 모니터링할지 여부를 나타냅니다. 기본적으로 MarkForMonitoring은 False로 설정되며, 이는 연결을 모니터링하지 않음을 의미합니다.</p>
<p>모니터링 서버를 배포하지 않은 경우에는 이 속성이 무시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>허용 목록에 추가되는 도메인에 배포된 SIP 프록시 서버의 정규화된 도메인 이름(예: proxy-server.fabrikam.com)입니다. 이 속성은 선택 사항입니다. 이 매개 변수를 지정하지 않으면 DNS SRV 검색 프로시저를 통해 SIP 프록시 서버의 위치가 결정됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain 개체입니다. **Set-CsAllowedDomain** cmdlet은 허용 도메인 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsAllowedDomain** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowedDomain 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAllowedDomain](get-csalloweddomain.md)  
[New-CsAllowedDomain](new-csalloweddomain.md)  
[Remove-CsAllowedDomain](remove-csalloweddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

