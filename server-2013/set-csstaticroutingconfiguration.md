---
title: Set-CsStaticRoutingConfiguration
TOCTitle: Set-CsStaticRoutingConfiguration
ms:assetid: 8f3e923e-f1e1-4a22-8252-5ef24fbc3cb3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398724(v=OCS.15)
ms:contentKeyID: 49304360
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsStaticRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

고정 경로 구성 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsStaticRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsStaticRoutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전역 고정 경로 지정 컬렉션에서 경로를 복사한 다음 해당 경로를 두 번째 고정 경로 컬렉션(ID가 service:Registrar:atl-cs-001.litwareinc.com인 컬렉션)에 할당합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 전역 컬렉션에 연결하여 MatchUri가 litwareinc.com이고 MatchOnlyPhoneUri가 True와 같은 경로에 대한 개체 참조를 반환합니다.

이 작업을 수행하기 위해 명령은 **Get-CsStaticRoutingConfiguration** cmdlet을 호출하여 전역 고정 경로 구성 컬렉션에서 정보를 반환합니다. 이 데이터는 ExpandProperty 매개 변수를 사용하여 Route 속성 값을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 컬렉션에 할당된 개별 경로를 나타내는 이러한 확장 값은 MatchUri 속성이 litwareinc.com과 같고 MatchOnlyPhoneUri 속성이 True와 같은 경로 하나를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 반환된 경로는 변수 $x에 저장됩니다.

경로가 검색된 후 예제의 두 번째 명령은 해당 경로를 service: Registrar:atl-cs-001.litwareinc.com 컬렉션에 추가합니다. 이 작업을 수행하기 위해 Route 매개 변수와 함께 **Set-CsStaticRoutingConfiguration** cmdlet을 호출합니다. 매개 변수 값 @{Add=$x}는 변수 $x에 저장된 경로를 Route 속성에서 유지 관리되는 경로 컬렉션에 추가하도록 **Set-CsStaticRoutingConfiguration** cmdlet에 지시합니다.

    $x = Get-CsStaticRoutingConfiguration -Identity global | Select-Object -ExpandProperty Route | Where-Object {$_.MatchUri -eq "litwareinc.com" -and $_.MatchOnlyPhoneUri -eq $True}
    
    Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route @{Add=$x}

## 예제 2

예제 2에 표시된 명령은 고정 경로 컬렉션에서 경로를 삭제합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 ID가 service:Registrar:atl-cs-001.litwareinc.com인 컬렉션에 연결하여 MatchUri가 litwareinc.com이고 MatchOnlyPhoneUri가 True와 같은 경로에 대한 개체 참조를 반환합니다. 이 작업을 수행하기 위해 명령은 **Get-CsStaticRoutingConfiguration** cmdlet을 호출하여 service:Registrar:atl-cs-001.litwareinc.com 컬렉션에서 정보를 반환합니다. 이 데이터는 ExpandProperty 매개 변수를 사용하여 Route 속성 값을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 컬렉션에 할당된 개별 경로를 나타내는 이러한 확장 값은 MatchUri 속성이 litwareinc.com과 같고 MatchOnlyPhoneUri 속성이 True와 같은 경로 하나를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 반환된 경로는 변수 $x에 저장됩니다.

경로가 검색된 후 두 번째 명령은 컬렉션에서 해당 명령을 삭제합니다. 이 작업을 수행하기 위해 Route 매개 변수와 함께 **Set-CsStaticRoutingConfiguration** cmdlet을 호출합니다. 매개 변수 값 @{Remove=$x}는 변수 $x에 지정된 경로를 삭제하도록 **Set-CsStaticRoutingConfiguration** cmdlet에 지시합니다.

    $x = Get-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com | Select-Object -ExpandProperty Route | Where-Object {$_.MatchUri -eq "litwareinc.com" -and $_.MatchOnlyPhoneUri -eq $True}
    
    Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route @{Remove=$x}

## 예제 3

예제 3에서는 정적 경로 지정 구성 컬렉션에 할당된 모든 경로를 제거하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 Route 매개 변수를 포함하고 매개 변수 값을 null로 설정합니다. 명령이 완료되면 컬렉션은 계속 존재하지만 컬렉션에 할당된 경로는 더 이상 존재하지 않습니다.

    Set-CsStaticRoutingConfiguration -Identity service:Registrar:atl-cs-001.litwareinc.com -Route $Null

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버에서 알고리즘을 사용하여 메시지가 전달되어야 하는 다음 위치(다음 홉)를 확인합니다. 고정 경로의 경우 메시지 경로는 시스템 관리자에 의해 미리 결정됩니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 설치하면 전역 고정 경로 컬렉션이 자동으로 만들어집니다. 컬렉션이 만들어지지만 이 컬렉션에 경로는 할당되지 않습니다. 또한 이 소프트웨어를 통해 서비스 범위에 적용되는 추가 컬렉션을 만들 수 있습니다. 이러한 새 컬렉션은 등록자 서비스에만 할당할 수 있습니다. **Set-CsStaticRoutingConfiguration** cmdlet을 사용하여 기존 정적 경로 컬렉션의 속성 값을 수정할 수 있습니다. 즉, cmdlet을 사용하여 새 경로를 컬렉션에 추가하거나 기존 경로를 컬렉션에서 삭제할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsStaticRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsStaticRoutingConfiguration"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 정적 경로 지정 구성 컬렉션의 고유한 식별자입니다. 전역 컬렉션을 수정하려면 -Identity global 구문을 사용합니다. 서비스 범위에 적용된 컬렉션을 수정하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsStaticRoutingConfiguration</strong> cmdlet이 전역 컬렉션을 자동으로 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>RoutingSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Route</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>컬렉션 내에서 유지 관리되는 개별 고정 경로입니다. 컬렉션에 추가할 경로는 다른 컬렉션에서 복사하거나 <strong>New-CsStaticRoute</strong> cmdlet을 사용하여 만들어야 합니다. 컬렉션에서 경로를 삭제하려면 먼저 해당 경로에 대한 개체 참조를 생성해야 합니다. 자세한 내용은 도움말 항목의 예제 섹션을 참조하십시오.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체입니다. **Set-CsStaticRoutingConfiguration** cmdlet은 고정 경로 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsStaticRoutingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)  
[New-CsStaticRoute](new-csstaticroute.md)  
[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)  
[Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

