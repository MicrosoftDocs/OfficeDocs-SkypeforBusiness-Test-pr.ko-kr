---
title: Set-CsSite
TOCTitle: Set-CsSite
ms:assetid: f4165fdb-5828-4e81-b489-7e263b27e36b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413023(v=OCS.15)
ms:contentKeyID: 49305521
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsSite

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 사이트의 속성을 수정합니다. 사이트는 Lync Server 풀의 컬렉션을 나타내며 일반적으로 지리적인 지역에 걸쳐 설계됩니다. Lync Server에는 데이터 센터 사이트와 원격 사이트(지점)의 두 가지 사이트가 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsSite [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-DefaultPersistentChatPool <String>] [-Description <String>] [-DisplayName <String>] [-FederationRoute <String>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]] [-XmppFederationRoute <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity Redmond)의 Description 속성을 수정합니다.

    Set-CsSite -Identity Redmond -Description "Full-time employees in Redmond, WA."

## 예제 2

예제 2에서는 Redmond 사이트의 표시 이름을 "US Headquarters"로 변경합니다.

    Set-CsSite -Identity Redmond -DisplayName "US Headquarters"

## 예제 3

예제 3에 표시된 명령은 Description이 없는 모든 사이트를 찾은 다음 이러한 각 사이트에 일반 설명 "Litwareinc.com"을 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSite** cmdlet을 매개 변수 없이 호출하여 모든 Lync Server 사이트의 컬렉션을 반환합니다. 반환된 컬렉션은 Description 속성이 Null 값($Null)과 같은(-eq) 사이트만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 사이트는 **ForEach-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션의 각 항목을 받고 **Set-CsSite** cmdlet을 사용하여 Description 속성 값을 수정합니다.

    Get-CsSite | Where-Object {$_.Description -eq $Null} | ForEach-Object {Set-CsSite $_.Identity -Description "Litwareinc.com"}

## 자세한 정보

Lync Server 2010에는 Lync Server 토폴로지의 새로운 개념인 사이트가 도입되었습니다. 사이트는 일반적으로 지리 및 네트워크 대역폭에 따라 조직된 Lync Server 풀 및 서버의 컬렉션이며 Active Directory 사이트 또는 Microsoft Exchange Server 사이트와 혼동해서는 안 됩니다. 예를 들어 Redmond의 모든 컴퓨터가 고속, 저지연 연결을 지원하는 동일한 로컬 영역 네트워크에 있는 경우 이러한 컴퓨터를 통칭하는 Redmond 사이트를 지정할 수 있습니다. Dublin에 있는 컴퓨터가 로컬 영역 네트워크에 있고 고속, 저지연 연결을 공유하는 경우 별도의 Dublin 사이트도 만들 수 있습니다. 사이트는 또한 Lync Server 관리에서 중요한 역할을 합니다. 많은 정책 및 설정을 사이트 범위에 구성할 수 있으며, 이렇게 하면 Redmond의 사용자에게 특정 다이얼 플랜 집합을 적용하고 Dublin의 사용자에게는 다른 다이얼 플랜 집합을 적용하는 등의 작업을 쉽게 수행할 수 있습니다.

사이트는 토폴로지 작성기를 사용하여 만들며 사이트 인프라에 대한 변경 작업(예: 새 풀 추가)도 Topology Builder를 사용하여 수행해야 합니다. 그러나 **Set-CsSite** cmdlet을 사용하여 조직에 있는 모든 사이트의 표시 이름, 설명 및 페더레이션 경로를 변경할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsSite** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsSite"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultPersistentChatPool</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사이트에 대한 기본 영구 채팅 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 사이트 개체에 다른 정보를 추가하는 데 사용됩니다. 예를 들어 Description은 사이트의 대화 상대 정보를 포함할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사이트의 알아보기 쉬운 이름입니다(예: -DisplayName &quot;North America and South America&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>FederationRoute</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>내부 네트워크와 인터넷 사이에 브리지를 제공하는 데 사용되는 에지 서버의 서비스 위치입니다(예: -FederationRoute &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 사이트의 이름입니다(예: -Identity &quot;Redmond&quot;). ID를 지정할 때는 &quot;site:Redmond&quot;와 같은 형식을 사용하지 마십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>XmppFederationRoute</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>XMPP(Extensible Messaging and Presence Protocol) 페더레이션에 사용되는 에지 서버의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-XmppFederationRoute EdgeServer:atl-xmpp-001.litwareinc.com</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsSite** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsSite** cmdlet은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsSite](get-cssite.md)

