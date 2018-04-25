---
title: New-CsSipDomain
TOCTitle: New-CsSipDomain
ms:assetid: 385f0f23-397b-4d8d-b9b7-ec942cda4a99
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425857(v=OCS.15)
ms:contentKeyID: 49303317
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용할 새 SIP 도메인을 만듭니다. SIP 도메인은 SIP 트래픽을 보내고 받을 권한이 있는 도메인이며 사용자에게 SIP 주소를 할당할 때 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IsDefault <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 fabrikam.com인 새 SIP 도메인을 만듭니다.

    New-CsSipDomain -Identity fabrikam.com

## 예제 2

예제 2에서는 fabrikam.com이라는 새 SIP 도메인을 만들고 새 도메인을 기본 SIP 도메인으로 설정합니다. 또한 이 명령은 fabrikam.com을 기본 도메인으로 지정하여 이전에 기본 SIP 도메인으로 사용된 도메인의 "수준을 내립니다". 이것은 한 개의 기본 SIP 도메인만 포함할 수 있기 때문입니다.

    New-CsSipDomain -Identity fabrikam.com -IsDefault $True

## 자세한 정보

사용자의 SIP 주소를 구성하고 사용자가 Lync 2013과 같은 SIP 관련 소프트웨어를 사용하도록 지원하려면 사용자 ID(예: Ken.Myer)와 SIP 도메인(예: litwareinc.com) 정보가 필요합니다. SIP 주소를 생성하는 데 사용되는 SIP 도메인은 Active Directory 포리스트 내에 있으며 SIP 트래픽을 보내고 받을 권한이 있는 도메인이어야 합니다. 예를 들어 litwareinc.com, fabrikam.com 및 contoso.com이라는 도메인이 있지만 litwareinc.com만 SIP 도메인인 것으로 식별된 경우 sip:Ken.Myer@fabrikam.com 또는 sip:Ken.Myer@contoso.com과 같은 SIP 주소를 사용하려면 최소한 fabrikam.com 및 contoso.com이 유효한 SIP 도메인으로 구성되어 있어야 합니다. 이렇게 하려면 **New-CsSipDomain** cmdlet을 실행하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipDomain"}

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
<td><p>새 SIP 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -Identity fabrikam.com).</p></td>
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
<td><p><em>IsDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>도메인이 기본 SIP 도메인(도메인 이름이 명시적으로 지정되지 않은 경우 Lync Server에서 사용하는 도메인)인지 여부를 나타냅니다. True로 설정하면 새 도메인이 새 기본 도메인이 됩니다.</p>
<p>IsDefault의 기본값은 False입니다. 새 도메인을 기본 도메인으로 설정하지 않으려는 경우 매개 변수를 생략하면 됩니다.</p>
<p>기본 SIP 도메인을 변경하는 경우에는 RTCCAA 및 RTCCAS 서비스를 다시 시작해야 합니다.</p></td>
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

없음. **New-CsSipDomain** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**New-CsSipDomain** cmdlet은 Microsoft.Rtc.Management.Xds.SipDomain object 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsSipDomain](get-cssipdomain.md)  
[Remove-CsSipDomain](remove-cssipdomain.md)  
[Set-CsSipDomain](set-cssipdomain.md)

