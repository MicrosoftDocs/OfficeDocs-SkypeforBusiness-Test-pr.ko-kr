---
title: Remove-CsSipDomain
TOCTitle: Remove-CsSipDomain
ms:assetid: cccd344f-7744-46c5-b1e1-ca4e8a29772c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398865(v=OCS.15)
ms:contentKeyID: 49305058
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsSipDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 이전에 구성된 SIP 도메인을 제거합니다. SIP 도메인은 SIP 트래픽을 보내고 받을 권한이 있는 도메인이며 사용자에게 SIP 주소를 할당할 때 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsSipDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 지원되는 도메인 이름 목록에서 ID가 fabrikam.com인 SIP 도메인을 제거합니다. fabrikam.com이 조직에서 현재 사용 중인 유일한 SIP 도메인인 경우에는 이 명령이 실패합니다. 토폴로지는 SIP 도메인을 하나 이상 포함해야 하기 때문입니다.

    Remove-CsSipDomain -Identity fabrikam.com

## 예제 2

예제 2에 표시된 명령은 기본 도메인을 제외하고 조직의 모든 SIP 도메인을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSipDomain** cmdlet을 호출하여 모든 SIP 도메인 컬렉션을 반환합니다. 이 컬렉션은 IsDefault 속성이 True와 같지 않은 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그러면 기본 도메인이 필터링된 후 나머지 도메인이 **Remove-CsSipDomain** cmdlet에 파이프되어 삭제됩니다.

    Get-CsSipDomain | Where-Object {$_.IsDefault -ne $True} | Remove-CsSipDomain

## 자세한 정보

사용자의 SIP 주소를 구성하고 사용자가 Lync 2013과 같은 SIP 관련 소프트웨어를 사용하도록 지원하려면 사용자 ID(예: Ken.Myer)와 SIP 도메인(예: litwareinc.com) 정보가 필요합니다. SIP 주소를 생성하는 데 사용되는 SIP 도메인은 Active Directory 포리스트 내에 있으며 SIP 트래픽을 보내고 받을 권한이 있는 도메인이어야 합니다. 예를 들어 litwareinc.com, fabrikam.com 및 contoso.com이라는 도메인이 있지만 litwareinc.com만 SIP 도메인인 것으로 식별된 경우 sip:Ken.Myer@fabrikam.com 또는 sip:Ken.Myer@contoso.com과 같은 SIP 주소를 사용하려면 최소한 fabrikam.com 및 contoso.com이 유효한 SIP 도메인으로 구성되어 있어야 합니다. 이렇게 하려면 **New-CsSipDomain** cmdlet을 실행하면 됩니다.

SIP 도메인에 권한을 부여한 후 **Remove-CsSipDomain** cmdlet을 사용하여 "권한을 취소"할 수 있습니다. 이 cmdlet은 지정된 도메인을 승인된 SIP 도메인 목록에서 제거합니다. 그러나 기본 도메인은 제거할 수 없습니다. 기본 도메인을 제거해야 하는 경우 먼저 다른 SIP 도메인을 기본 도메인으로 구성해야 합니다. SIP 도메인이 하나만 있는 경우에는 해당 도메인이 기본 도메인으로 자동으로 구성되며 제거할 수 없습니다.

또한 하나 이상의 SIP 주소가 할당된 SIP 도메인은 제거할 수 없습니다. 예를 들어 Ken Myer의 SIP 주소가 "sip:kenmyer@contoso.com"인 경우 SIP 도메인 Contoso.com을 제거할 수 없습니다. 현재 사용 중인 SIP 도메인을 제거하려면 먼저 SIP 주소에 해당 도메인이 있는 모든 사용자에게 새 SIP 주소를 할당해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsSipDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsSipDomain"}

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
<td><p>제거할 SIP 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -Identity fabrikam.com).</p></td>
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

Microsoft.Rtc.Management.Xds.SipDomain 개체입니다. **Remove-CsSipDomain** cmdlet은 SIP 도메인 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsSipDomain** cmdlet은 Microsoft.Rtc.Management.Xds.SipDomain 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsSipDomain](get-cssipdomain.md)  
[New-CsSipDomain](new-cssipdomain.md)  
[Set-CsSipDomain](set-cssipdomain.md)

