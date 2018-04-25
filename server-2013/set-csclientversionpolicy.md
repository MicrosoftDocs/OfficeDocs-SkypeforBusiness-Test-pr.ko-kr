---
title: Set-CsClientVersionPolicy
TOCTitle: Set-CsClientVersionPolicy
ms:assetid: cf7c1a6c-b8a9-4609-97f4-6c8ef9e45be7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398876(v=OCS.15)
ms:contentKeyID: 49305085
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientVersionPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 클라이언트 버전 정책을 수정합니다. 클라이언트 버전 정책을 사용하면 Lync Server 시스템에 로그온할 수 있는 클라이언트(예: Microsoft Office Communicator 2007 R2)를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsClientVersionPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientVersionPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Rules <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 한 클라이언트 버전 정책의 모든 클라이언트 버전 규칙을 다른 정책에 복사합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Set-CsClientVersionPolicy** cmdlet을 사용하여 site:Redmond 정책의 모든 규칙을 제거합니다. 이때 Rules 속성 값을 null로 설정합니다. 규칙이 삭제되면 두 번째 명령에서 **Get-CsClientVersionPolicy** cmdlet을 사용하여 site:Dublin 정책에 대해 구성된 모든 클라이언트 버전 정책 규칙을 검색합니다. 이러한 규칙은 $x라는 변수에 저장됩니다.

마지막 명령에서는 **Set-CsClientVersionPolicy** cmdlet을 다시 호출합니다. 그리고 이번에는 Redmond 정책의 Rules 속성을 $x로 설정합니다. 이렇게 하면 site:Dublin 정책의 모든 규칙을 복사하여 site:Redmond 정책에 효과적으로 추가할 수 있습니다.

    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $Null
    
    $x = Get-CsClientVersionPolicy -Identity site:Dublin | Select-Object -ExpandProperty Rules
    
    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $x

## 자세한 정보

클라이언트 버전 정책은 클라이언트 버전 규칙 컬렉션을 나타내고, 클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 지정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 SIP 헤더에 포함된 버전 정보에서 클라이언트 버전 규칙 컬렉션을 검사하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 예를 들어 로그온을 허용 또는 차단하거나 로그온을 허용하되 클라이언트 응용 프로그램을 최신 버전으로 자동 업그레이드(예: Communicator 2007 R2에서 Lync 2013으로 업그레이드)하도록 Lync Server에 지시하는 규칙이 있을 수 있습니다.

전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 적용할 수 있는 클라이언트 버전 정책을 통해 시스템에 액세스하는 데 사용할 수 있는 클라이언트 응용 프로그램을 유동적으로 결정할 수 있습니다. 예를 들어 Lync Server가 Lync와 동일한 요소 및 기능을 지원하지 않기 때문에 사용자가 Communicator 2007 R2을 사용하여 이러한 이전 버전의 클라이언트 응용 프로그램에 로그온하지 못하게 하려는 경우가 있습니다. 그러나 하드웨어 또는 소프트웨어 충돌로 인해 Lync로 업그레이드할 수 없는 사용자 그룹이 있을 수도 있습니다. 이 경우 해당 사용자가 Communicator 2007 R2 내에서 로그온하도록 하는 별도의 규칙과 별도의 클라이언트 버전 정책을 만들 수 있습니다.

클라이언트 버전 정책은 언제든지 수정할 수 있습니다. 클라이언트 버전 정책을 수정한다는 것은 일반적으로 새 규칙을 추가하거나 기존 규칙을 삭제하거나 기존 규칙의 속성을 수정(예: 규칙 동작을 Allow에서 Block으로 변경)하는 작업을 의미합니다. 이러한 변경 작업은 **Set-CsClientVersionPolicy** cmdlet을 사용하여 수행할 수 있습니다. 그러나 이러한 수정 작업은 **CsClientVersionPolicyRule** cmdlet을 사용하여 수행하는 것이 더 간편합니다.

반면, **Set-CsClientVersionPolicy** cmdlet을 사용하면 하나의 전체 클라이언트 버전 정책 집합을 다른 정책 집합으로 쉽게 복사할 수 있는 장점이 있습니다. 자세한 내용은 이 도움말 항목의 예제 섹션을 참조하십시오.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsClientVersionPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientVersionPolicy\\b"}

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
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책에 대한 설명 정보를 제공하는 데 사용됩니다. 예를 들어 정책을 할당해야 하는 정책을 설명하는 정보를 제공할 수 있습니다.</p></td>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 정책의 고유 식별자입니다. 전역 정책을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 정책을 수정하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 정책을 수정하려면 -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 등록자 서비스는 클라이언트 버전 정책을 호스트할 수 있는 유일한 서비스입니다.</p>
<p>사용자별 정책도 이 cmdlet을 사용하여 수정할 수 있습니다. 또한 사용자별 정책을 수정하려면 -Identity &quot;SalesDepartmentPolicy&quot;와 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsClientVersionPolicy</strong> cmdlet이 전역 정책을 수정합니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>클라이언트 버전 정책 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Rules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>정책에 할당된 개별 클라이언트 정책 규칙 컬렉션입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy 개체입니다. **Remove-CsClientVersionPolicy** cmdlet은 클라이언트 버전 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsClientVersionPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

