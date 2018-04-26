---
title: Set-CsBlockedDomain
TOCTitle: Set-CsBlockedDomain
ms:assetid: 03f9443c-4c99-4338-bbf0-7b2f40a30ea5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398090(v=OCS.15)
ms:contentKeyID: 49302654
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsBlockedDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션이 차단된 도메인 목록에 포함된 하나 이상의 도메인에 대한 Comment 속성을 수정합니다. 정의상, 사용자는 Lync Server 응용 프로그램을 사용하여 차단된 도메인의 사용자와 통신할 수 없습니다. 예를 들어 사용자는 Lync를 사용하여 차단 목록에 표시된 도메인의 SIP 계정을 가진 사용자와 메신저 대화를 교환할 수 없습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsBlockedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsBlockedDomain [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Comment <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "fabrikam.com"인 차단된 도메인의 설명을 수정합니다. 이 예제에서 Comment 매개 변수는 매개 변수 값 "Block this domain pending legal review."와 함께 포함됩니다.

    Set-CsBlockedDomain -Identity fabrikam.com -Comment "Block this domain pending legal review."

## 예제 2

예제 2에서 Comment 속성은 차단된 도메인 목록에 포함된 모든 도메인에 대해 업데이트됩니다. 이 작업을 수행하기 위해 먼저 차단된 도메인 목록에 현재 있는 모든 도메인의 컬렉션을 반환하는 **Get-CsBlockedDomain** cmdlet을 호출합니다. 이 컬렉션은 컬렉션의 각 도메인에 대한 Comment 속성을 수정하는 **Set-CsBlockedDomain** cmdlet에 파이프됩니다.

    Get-CsBlockedDomain | Set-CsBlockedDomain -Comment "Block this domain pending legal review."

## 예제 3

예제 3에서는 Comment 속성에 대한 값이 구성되지 않은 차단 목록의 각 도메인에 새 설명("Block this domain pending legal review.")을 추가합니다. 이 작업을 수행하기 위해 먼저 **Get-CsBlockedDomain** cmdlet을 사용하여 차단 목록에 현재 있는 모든 도메인의 컬렉션을 반환합니다. 이 컬렉션은 Comment 속성이 null 값과 같은 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 필터링된 컬렉션에 있는 각 도메인의 Comment 속성에 동일한 설명을 할당하는 **Set-CsBlockedDomain** cmdlet에 파이프됩니다.

    Get-CsBlockedDomain | Where-Object {$_.Comment -eq $Null} | Set-CsBlockedDomain -Comment "Block this domain pending legal review."

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync Server와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

다른 조직과 직접 페더레이션을 설정하려면 여러 작업을 수행해야 합니다. 먼저 페더레이션을 허용하도록 액세스 에지 서버를 설정해야 합니다. 또한 다른 조직이 사용자 조직과 페더레이션을 설정해야 합니다. 한 당사자라도 관계에 동의하지 않으면 페더레이션을 설정할 수 없습니다.

페더레이션 관계를 설정하려면 두 개의 페더레이션 관련 목록인 허용 목록과 차단 목록을 관리해야 합니다. 허용 목록은 페더레이션하도록 선택한 대상 조직을 나타냅니다. 도메인이 허용 목록에 나타나는 경우 구성 설정에 따라 사용자는 해당 페더레이션 도메인에 계정이 있는 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반대로 차단 목록은 페더레이션이 명시적으로 금지된 도메인을 나타냅니다. 예를 들어 차단된 도메인에서 전송된 메시지는 Lync Server에서 자동으로 거부합니다.

차단된 도메인에서 유일하게 수정할 수 있는 속성인 Comment 속성은 차단 목록에 있는 도메인에 대한 추가 정보(예: 도메인 차단 이유, 차단 목록에서 도메인을 제거할 수 있는 시기, 차단 목록에서 도메인을 제거하려는 경우 문의할 사람 등)를 저장하는 데 사용됩니다. 차단된 도메인 목록에 있는 도메인의 Comment 속성을 변경해야 하는 경우 **Set-CsBlockedDomain** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsBlockedDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsBlockedDomain"}

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
<td><p>수정할 도메인에 대한 추가 정보를 제공하는 데 사용됩니다. 예를 들어 도메인이 차단 목록에 포함된 이유를 나타내는 Comment를 추가할 수 있습니다.</p></td>
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
<td><p>Comment 속성을 수정할 차단된 도메인의 FQDN(정규화된 도메인 이름)입니다.예: fabrikam.com</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>BlockedDomain 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain 개체입니다. **Set-CsBlockedDomain** cmdlet은 차단된 도메인 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsBlockedDomain** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsBlockedDomain](get-csblockeddomain.md)  
[New-CsBlockedDomain](new-csblockeddomain.md)  
[Remove-CsBlockedDomain](remove-csblockeddomain.md)  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

