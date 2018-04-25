---
title: New-CsClientVersionPolicy
TOCTitle: New-CsClientVersionPolicy
ms:assetid: 8c95493a-ce18-49eb-937f-7348743fcbb4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398709(v=OCS.15)
ms:contentKeyID: 49304325
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientVersionPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 클라이언트 버전 정책을 생성합니다. 클라이언트 버전 정책을 사용하면 Lync Server 시스템에 로그온할 수 있는 클라이언트 버전(예: Microsoft Office Communicator 2007 R2)을 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsClientVersionPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Rules <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 새 클라이언트 버전 정책을 만듭니다. 필수 매개 변수인 Identity 이외에는 매개 변수가 지정되지 않았기 때문에 새 정책에는 클라이언트 버전 정책에 대한 모든 기본값이 포함됩니다.

    New-CsClientVersionPolicy -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 조직의 각 사이트에 대한 새 클라이언트 버전 정책을 만듭니다. 이 작업을 수행하기 위해 명령은 먼저 추가 매개 변수 없이 **Get-CsSite** cmdlet을 호출하여 토폴로지에 있는 모든 사이트의 컬렉션을 반환합니다. 이 사이트 컬렉션은 각 사이트의 Identity 속성을 추출하는 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 ID는 컬렉션의 각 사이트에 대해 새 클라이언트 버전 정책을 만드는 **ForEach-Object** cmdlet에 파이프됩니다.

    Get-CsSite | Select-Object Identity | ForEach-Object {New-CsClientVersionPolicy -Identity ("site:" + $_.Identity)}

## 자세한 정보

클라이언트 버전 정책은 클라이언트 버전 규칙 컬렉션을 나타내고, 클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 지정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 SIP 헤더에 포함된 버전 정보에서 클라이언트 버전 규칙 컬렉션을 검사하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 예를 들어 로그온을 허용 또는 차단하거나 로그온을 허용하되 클라이언트 응용 프로그램을 최신 버전으로 자동 업그레이드(예: Communicator 2007 R2에서 Lync 2013으로 업그레이드)하도록 Lync Server에 지시하는 규칙이 있을 수 있습니다.

전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 적용할 수 있는 클라이언트 버전 정책을 통해 시스템에 액세스하는 데 사용할 수 있는 클라이언트 응용 프로그램을 유동적으로 결정할 수 있습니다. 예를 들어 Communicator 2007 R2는 Lync와 동일한 기능을 지원하지 않으므로 이 클라이언트 응용 프로그램을 사용하여 Lync Server에 로그온하지 못하도록 할 수 있습니다. 그러나 하드웨어 또는 소프트웨어 충돌로 인해 Lync Server로 업그레이드할 수 없는 사용자 그룹이 있을 수도 있습니다. 이 경우 해당 사용자가 Communicator 2007 R2 내에서 로그온하도록 하는 별도의 규칙과 별도의 클라이언트 버전 정책을 만들 수 있습니다.

하지만 익명 사용자는 전역 정책을 통해서만 영향을 받습니다. 이는 익명 사용자의 경우 사이트나 서비스에 연결되어 있지 않아 사용자별 정책을 할당할 수 없기 때문입니다.

새 클라이언트 버전 정책은 **New-CsClientVersionPolicy** cmdlet을 사용하여 만듭니다. 이러한 새 정책은 사이트 범위, 서비스 범위(등록자 서비스만) 또는 사용자별 범위에서 생성할 수 있습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsClientVersionPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientVersionPolicy\\b"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>만들려는 정책의 고유 식별자입니다. 사이트 범위의 정책을 만들려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 정책을 생성하려면 -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 등록자 서비스는 클라이언트 버전 정책을 호스트할 수 있는 유일한 서비스입니다.</p>
<p>사용자별 범위에서 정책을 만들 수도 있습니다. 사용자별 정책을 만들려면 -Identity &quot;SalesDepartmentPolicy&quot;와 유사한 구문을 사용합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책에 대한 설명 텍스트를 제공할 수 있습니다. 예를 들어, 정책을 할당해야 하는 사용자에 대한 정보를 포함할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Rules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>클라이언트 버전 정책 규칙의 컬렉션입니다. <strong>New-CsClientVersionPolicyRule</strong> cmdlet 및 <strong>Remove-CsClientVersionPolicyRule</strong> cmdlet을 사용하여 정책에서 규칙을 추가 및 제거할 수 있습니다. 새 정책을 만들 때 규칙을 추가하려면 규칙을 만든 후 값을 변수(예: $x)에 저장합니다. 그런 다음 새 정책을 생성할 때 다음과 같은 구문을 사용할 수 있습니다.</p>
<p>New-CsClientVersionPolicy -Identity &quot;RedmondClientVersionPolicy&quot; -Rules @{Add=$x}</p></td>
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

없음. **Get-CsClientVersionPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsClientVersionPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)  
[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

