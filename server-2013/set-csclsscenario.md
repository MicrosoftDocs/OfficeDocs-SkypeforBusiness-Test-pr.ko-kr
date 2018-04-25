---
title: Set-CsClsScenario
TOCTitle: Set-CsClsScenario
ms:assetid: 00de6571-a1ad-4f69-a21e-8a9ae115882f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204622(v=OCS.15)
ms:contentKeyID: 49302609
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClsScenario

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 로깅 구성 시나리오를 수정할 수 있습니다. 시나리오는 관리자가 추적을 위해 사용하거나 사용하지 않도록 설정할 수 있는 특정 Lync Server 2013 구성 요소 또는 상황(예: 메신저 대화 및 현재 상태)을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsClsScenario [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClsScenario [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Provider <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 새 중앙 로깅 시나리오 공급자를 만든 다음 이 공급자를 Redmond 사이트에 구성된 WAC 시나리오에 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsClsProvider** cmdlet을 사용하여 WebInfrastructure라는 새 공급자를 만듭니다. 이 새 공급자는 변수 $provider에 저장됩니다. 그 다음 예제의 두 번째 명령은 새 공급자를 시나리오 site:Redmond/WAC에 추가합니다. 이 명령은 @{Add=$provider} 구문을 사용하기 때문에 새 공급자는 이미 구성되어 있는 다른 공급자와 함께 WAC 시나리오에 추가됩니다.

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Add=$provider}

## 예제 2

예제 2의 명령은 예제 1에 나와 있는 명령의 변형입니다. 하지만 예제 2에서는 새 공급자가 WAC 시나리오에 구성되어 있는 일부 또는 전체 기존 공급자를 대체합니다. 이를 위해 @{Replace=$provider} 구문을 사용합니다.

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Replace=$provider}

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 중앙 로깅 구성 설정의 컬렉션에 새 시나리오를 추가하는 방법으로 사용자 지정 시나리오를 만들 수 있습니다. 그런 후에 **Set-CsClsScenario** cmdlet을 사용하여 원하는 시나리오를 수정할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClsScenario"}

Lync Server 제어판: **Set-CsClsScenario** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 시나리오의 고유 식별자입니다. 시나리오는 구성되는 범위(시나리오가 포함된 중앙 로깅 구성 설정 컬렉션) 및 시나리오 이름의 두 부분으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/AddressBook&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Provider</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>시나리오에 대한 로깅 공급자입니다. 새 공급자는 <strong>New-CsClsProvider</strong> cmdlet을 사용하여 작성해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>$provider = New-CsClsProvider -Name &quot;UserServices&quot; -Type &quot;WPP&quot; -Level &quot;Info&quot; -Flags &quot;All&quot;</p></td>
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

**Set-CsClsScenario** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsClsScenario** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario\#Decorated 개체의 기존 인스턴스를 수정합니다.

