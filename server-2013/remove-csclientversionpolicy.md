---
title: Remove-CsClientVersionPolicy
TOCTitle: Remove-CsClientVersionPolicy
ms:assetid: 2fd9ca4c-8b4f-41f0-b051-5b486376008c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425801(v=OCS.15)
ms:contentKeyID: 49303199
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClientVersionPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 클라이언트 버전 정책을 제거합니다. 클라이언트 버전 정책을 사용하면 Lync Server 시스템에 로그온할 수 있는 클라이언트(예: Microsoft Office Communicator 2007 R2)를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsClientVersionPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대한 클라이언트 버전 정책을 삭제합니다.

    Remove-CsClientVersionPolicy -Identity site:Redmond

## 예제 2

예제 2에서는 사용자별 범위에서 구성된 모든 클라이언트 버전 정책을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsClientVersionPolicy** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "tag:\*"는 사용자 범위에서 구성된 정책의 데이터만 반환되도록 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsClientVersionPolicy** cmdlet에 파이프됩니다.

    Get-CsClientVersionPolicy -Filter tag:* | Remove-CsClientVersionPolicy

## 자세한 정보

클라이언트 버전 정책은 클라이언트 버전 규칙 컬렉션을 나타내고, 클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 지정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 SIP 헤더에 포함된 버전 정보에서 클라이언트 버전 규칙 컬렉션을 검사하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 예를 들어 로그온을 허용 또는 차단하거나 로그온을 허용하되 클라이언트 응용 프로그램을 최신 버전으로 자동 업그레이드(예: Communicator 2007 R2에서 Lync 2013으로 업그레이드)하도록 Lync Server에 지시하는 규칙이 있을 수 있습니다.

전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 적용할 수 있는 클라이언트 버전 정책을 통해 시스템에 액세스하는 데 사용할 수 있는 클라이언트 응용 프로그램을 유동적으로 결정할 수 있습니다. 예를 들어 Communicator 2007 R2는 Lync 2013와 동일한 요소 및 기능을 지원하지 않기 때문에 사용자가 Communicator 2007 R2를 사용하여 Lync Server에 로그온하지 못하도록 할 수 있습니다. 그러나 하드웨어 또는 소프트웨어 충돌로 인해 Lync 2013로 업그레이드할 수 없는 사용자 그룹이 있을 수도 있습니다. 이 경우 해당 사용자가 Communicator 2007 R2 내에서 로그온하도록 하는 별도의 규칙과 별도의 클라이언트 버전 정책을 만들 수 있습니다.

**New-CsClientVersionPolicy** cmdlet을 사용하여 새 정책을 만들 수 있습니다. 이러한 사용자 지정 정책은 나중에 **Remove-CsClientVersionPolicy** cmdlet을 실행하여 제거할 수 있습니다. 클라이언트 버전 정책을 제거하면 이전에 해당 정책으로 제어된 사용자가 자동으로 관리 계층의 다음 정책을 상속받습니다. 예를 들어 사용자별 정책을 삭제하면 사용자가 자동으로 적절한 서비스 정책으로 제어됩니다. 서비스 정책이 없으면 사용자가 적절한 사이트 정책으로 제어됩니다. 사이트 정책이 없으면 사용자가 전역 정책으로 제어됩니다.

항상 한 개의 전역 정책이 있으므로 클라이언트 버전 정책에 의해 관리되지 않는 사용자는 없습니다. 전역 정책에 대해 **Remove-CsClientVersionPolicy** cmdlet을 실행할 수도 있지만 실제로 정책이 삭제되지는 않습니다. 대신, 모든 정책 규칙이 기본값으로 다시 설정됩니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsClientVersionPolicy** cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientVersionPolicy\\b"}

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
<td><p>삭제할 정책의 고유 식별자입니다. 사이트 범위에서 구성된 정책을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 정책을 제거하려면 -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 등록자 서비스는 클라이언트 버전 정책을 호스트할 수 있는 유일한 서비스입니다.</p>
<p>사용자별 범위에서 정책을 제거할 수도 있습니다. 사용자별 정책을 제거하려면 -Identity &quot;SalesDepartmentPolicy&quot;와 유사한 구문을 사용합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy 개체입니다. **Remove-CsClientVersionPolicy** cmdlet은 클라이언트 버전 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsClientVersionPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)  
[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

