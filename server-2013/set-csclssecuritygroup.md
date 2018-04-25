---
title: Set-CsClsSecurityGroup
TOCTitle: Set-CsClsSecurityGroup
ms:assetid: 14e7d927-8d3e-4b36-867c-d4742101e751
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204700(v=OCS.15)
ms:contentKeyID: 49302897
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClsSecurityGroup

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 로깅 구성 보안 그룹을 수정합니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsClsSecurityGroup [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClsSecurityGroup [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AccessLevel <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 global/HelpDesk인 중앙 로깅 보안 그룹을 수정합니다. 이 예제에서 AccessLevel 속성은 Tier3으로 설정됩니다.

    Set-CsClsSecurityGroup -Identity "global/HelpDesk" -AccessLevel "Tier3"

## 예제 2

예제 2에서는 전역 범위에서 구성된 모든 중앙 로깅 보안 그룹에 대해 액세스 수준을 수정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 Filter 매개 변수를 포함하여 **Get-CsClsSecurityGroup** cmdlet을 호출합니다. 필터 값 "global/\*"는 반환되는 데이터를 전역 범위에서 구성된 보안 그룹으로 제한합니다. 이러한 그룹은 **Set-CsClsSecurityGroup** cmdlet에 파이프되며, 이 cmdlet은 각 그룹의 AccessLevel 속성을 Tier3으로 설정합니다.

    Get-CsClsSecurityGroup -Filter "global/*" | Set-CsClsSecurityGroup-AccessLevel "Tier3"

## 예제 3

예제 3에서는 단일 명령을 사용하여 기존 액세스 수준을 공유하는 모든 중앙 로깅 보안 그룹의 액세스 수준을 변경하는 방법을 보여줍니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsClsSecurityGroup** cmdlet을 호출하여 모든 중앙 로깅 보안 그룹의 컬렉션을 반환합니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 AccessLevel이 GlobalAccess인(-eq) 그룹만 선택합니다. 이렇게 선택된 그룹은 **Set-CsClsSecurityGroup** cmdlet에 파이프되며, 이 cmdlet은 각 그룹을 가져와 AccessLevel을 Tier3으로 변경합니다.

    Get-CsClsSecurityGroup | Where-Object {$_.AccessLevel -eq "GlobalAccess"} | Set-CsClsSecurityGroup -AccessLevel "Tier3"

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

Office 365 버전 Lync Server에서는 로그 파일에 기록되는 개인 식별이 가능한 정보에 액세스할 수 있는 사용자를 결정하는 데 보안 그룹이 사용됩니다. 보안 그룹은 [New-CsClsSecurityGroup](new-csclssecuritygroup.md) cmdlet을 사용하여 작성된 다음 중앙 로깅 구성 설정의 컬렉션에 추가됩니다. 이러한 그룹을 만든 후에는 **Set-CsClsSecurityGroup** cmdlet을 사용하여 해당 속성 값을 수정할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClsSecurityGroup"}

**Lync Server 제어판:** **Set-CsClsSecurityGroup** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AccessLevel</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>그룹에 할당되는 액세스 수준을 지정하는 문자열 값입니다. 액세스 수준은 관리자가 할당하며 보안 그룹을 분류하는 데 사용됩니다. 예를 들면 다음과 같습니다.</p>
<p>-AccessLevel &quot;Tier3&quot;</p>
<p>여러 그룹에서 동일한 액세스 수준을 공유할 수 있습니다. 현재 의미 있는 값은 &quot;Tier3&quot;, &quot;Tier2&quot;, &quot;Product&quot;, &quot;Ops&quot; 및 &quot;Pii&quot;뿐입니다.</p></td>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 중앙 로깅 보안 그룹의 고유 식별자입니다. 보안 그룹 ID는 그룹이 만들어진 범위 뒤에 그룹 이름이 붙는 형식으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 HelpDesk 그룹을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global/HelpDesk&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

**Set-CsClsSecurityGroup** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsClsSecurityGroup** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup\#Decorated 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsSecurityGroup](get-csclssecuritygroup.md)  
[New-CsClsSecurityGroup](new-csclssecuritygroup.md)  
[Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)

