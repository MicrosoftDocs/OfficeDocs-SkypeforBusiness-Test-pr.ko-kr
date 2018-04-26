---
title: Remove-CsBlockedDomain
TOCTitle: Remove-CsBlockedDomain
ms:assetid: 34485703-9e1d-47f9-9834-c2ba37249cd1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425832(v=OCS.15)
ms:contentKeyID: 49303255
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsBlockedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션이 차단된 도메인 목록에서 도메인을 제거합니다. 정의에 따라 사용자는 Lync Server 응용 프로그램을 사용하여 차단된 도메인의 사용자와 통신할 수 없습니다. 예를 들어 사용자는 Lync를 사용하여 차단된 목록에 표시된 도메인의 SIP 계정을 가진 사용자와 메신저 대화를 교환할 수 없습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsBlockedDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 차단된 도메인 목록에서 fabrikam.com 도메인을 제거합니다. 이 작업을 수행하기 위해 ID가 "fabrikam.com"인 도메인을 지정하고 **Remove-CsBlockedDomain** cmdlet을 호출합니다.

    Remove-CsBlockedDomain -Identity fabrikam.com

## 예제 2

예제 2에서는 차단된 도메인 목록에서 ID에 문자열 값 "fabrikam"이 포함된 모든 도메인을 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsBlockedDomain** cmdlet 및 Filter 매개 변수를 사용하여 ID에 문자열 "fabrikam"이 포함된 모든 차단된 도메인의 컬렉션을 반환합니다(예: fabrikam.com, fabrikam.org 또는 us.fabrikam.net). 그런 다음 해당 컬렉션은 차단된 도메인 목록에서 컬렉션의 각 항목을 삭제하는 **Remove-CsBlockedDomain** cmdlet에 파이프됩니다.

    Get-CsBlockedDomain -Filter *fabrikam* | Remove-CsBlockedDomain 

## 예제 3

예제 3에 표시된 명령은 차단된 도메인 목록을 완전히 지웁니다. 이 작업을 수행하기 위해 먼저 매개 변수를 지정하지 않고 **Get-CsBlockedDomain** cmdlet을 호출하여 현재 차단된 도메인 목록에 있는 모든 도메인으로 구성된 컬렉션을 반환합니다. 그런 다음 해당 컬렉션은 차단된 도메인 목록에서 컬렉션의 각 항목을 제거하는 **Remove-CsBlockedDomain** cmdlet에 파이프됩니다. 그 결과 차단된 도메인 목록에 더 이상 도메인이 남지 않게 됩니다.

    Get-CsBlockedDomain | Remove-CsBlockedDomain 

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과 직접 페더레이션을 설정하려면 몇 가지 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 Lync Server 액세스 에지 서비스를 실행하는 서버를 설정해야 합니다. 또한 다른 조직이 사용자와의 페더레이션을 사용하도록 설정해야 합니다. 상대방이 페더레이션 관계에 동의하지 않으면 페더레이션이 설정되지 않습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록인 허용 목록과 차단 목록을 관리해야 할 수도 있습니다. 허용 목록은 페더레이션하기로 선택한 조직을 나타냅니다. 도메인이 허용 목록에 표시되면 구성 설정에 따라 사용자가 해당 페더레이션 도메인의 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

물론 메시지는 도메인이 차단 목록에 있는 동안에만 차단됩니다. 도메인이 이 목록에서 제거되면 해당 도메인과 페더레이션된 관계를 설정할 수 있습니다. 이전에 금지한 도메인과 페더레이션을 설정하려면 먼저 **Remove-CsBlockedDomain** cmdlet을 사용하여 차단된 도메인 목록에서 도메인을 제거하면 됩니다. 도메인은 허용 목록과 차단 목록에 동시에 표시될 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsBlockedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsBlockedDomain"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>차단 목록에서 제거할 도메인의 FQDN(정규화된 도메인 이름)(예: fabrikam.com). 도메인 ID를 지정할 때 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain 개체입니다. **Remove-CsBlockedDomain** cmdlet은 차단된 도메인 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsBlockedDomain](get-csblockeddomain.md)  
[New-CsBlockedDomain](new-csblockeddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)  
[Set-CsBlockedDomain](set-csblockeddomain.md)

