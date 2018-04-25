---
title: Get-CsSipDomain
TOCTitle: Get-CsSipDomain
ms:assetid: 8a8def42-7b14-40c3-be5a-57905069b405
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398701(v=OCS.15)
ms:contentKeyID: 49304308
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsSipDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 SIP 도메인에 대한 정보를 반환합니다. SIP 도메인은 SIP 트래픽을 보내고 받을 권한이 있는 도메인이며 사용자에게 SIP 주소를 할당할 때 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsSipDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsSipDomain [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에서는 매개 변수 없이 **Get-CsSipDomain** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 SIP 도메인에 대한 정보가 반환됩니다.

    Get-CsSipDomain

## 예제 2

예제 2에 표시된 명령은 ID가 fabrikam.com인 모든 SIP 도메인에 대한 정보를 반환합니다. SIP 도메인 ID는 고유해야 하므로 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsSipDomain -Identity fabrikam.com

## 예제 3

예제 3에서는 **Get-CsSipDomain** cmdlet 및 Filter 매개 변수를 사용하여 ID가 "f" 문자로 시작하는 모든 SIP 도메인에 대한 정보를 반환합니다. 예를 들어 fabrikam.com, fabrikam.org, fabrikam-users.com 등이 여기에 해당합니다.

    Get-CsSipDomain -Filter "f*"

## 예제 4

예제 4에 표시된 명령은 기본 SIP 도메인에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsSipDomain** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 SIP 도메인 컬렉션을 반환합니다. 이 컬렉션은 IsDefault 속성이 True와 같은 도메인 하나를 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsSipDomain | Where-Object {$_.IsDefault -eq $True}

## 자세한 정보

사용자의 SIP 주소를 구성하고 사용자가 Lync 2013과 같은 SIP 관련 소프트웨어를 사용하도록 지원하려면 사용자 ID(예: Ken.Myer)와 SIP 도메인(예: litwareinc.com) 정보가 필요합니다. SIP 주소를 생성하는 데 사용되는 SIP 도메인은 Active Directory 포리스트 내에 있으며 SIP 트래픽을 보내고 받을 권한이 있는 도메인이어야 합니다. 예를 들어 litwareinc.com, fabrikam.com 및 contoso.com이라는 도메인이 있지만 litwareinc.com만 SIP 도메인인 것으로 식별된 경우 sip:Ken.Myer@fabrikam.com 또는 sip:Ken.Myer@contoso.com과 같은 SIP 주소를 사용하려면 최소한 fabrikam.com 및 contoso.com이 유효한 SIP 도메인으로 구성되어 있어야 합니다. 이렇게 하려면 **New-CsSipDomain** cmdlet을 실행하면 됩니다.

**Get-CsSipDomain** cmdlet을 사용하면 조직에서 사용할 권한이 있는 SIP 도메인에 대한 정보를 가져올 수 있습니다. **Get-CsSipDomain** cmdlet은 또한 조직의 기본 SIP 도메인을 식별합니다. 이는 SIP 도메인이 지정되지 않은 경우 Lync Server에서 기본적으로 사용하는 도메인입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsSipDomain** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsSipDomain"}

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
<td><p>반환할 SIP 도메인의 ID를 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 &quot;*.org&quot; 필터 값은 ID가 &quot;.org&quot; 문자열 값으로 끝나는 모든 권한 있는 SIP 도메인의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 SIP 도메인의 FQDN(정규화된 도메인 이름)입니다(예: fabrikam.com). 이 매개 변수 및 Filter 매개 변수가 둘 다 지정되지 않은 경우 조직에서 사용할 권한이 있는 모든 SIP 도메인이 반환됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsSipDomain** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**Get-CsSipDomain** cmdlet은 Microsoft.Rtc.Management.Xds.SipDomain 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsSipDomain](new-cssipdomain.md)  
[Remove-CsSipDomain](remove-cssipdomain.md)  
[Set-CsSipDomain](set-cssipdomain.md)

