---
title: New-CsStaticRoutingConfiguration
TOCTitle: New-CsStaticRoutingConfiguration
ms:assetid: 30d1736f-990f-46e8-931f-9247cd988244
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425811(v=OCS.15)
ms:contentKeyID: 49303215
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsStaticRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

고정 경로 프록시 구성 설정의 새 컬렉션을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsStaticRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 service:Registrar:atl-cs-001.litwareinc.com인 새 고정 경로 구성 컬렉션을 만듭니다. Route 매개 변수가 명령에 포함되어 있지 않으므로 새 컬렉션에는 고정 경로가 할당되지 않습니다.

    New-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" 

## 예제 2

예제 2에 표시된 명령은 TCP를 전송으로 사용하는 새 SIP 프록시 경로를 만듭니다. 새 경로는 새 고정 경로 지정 구성 컬렉션에 추가됩니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsStaticRoute** cmdlet을 사용하여 IP 주소가 192.168.1.100인 다음 홉 서버를 가리키는 새 경로를 만듭니다. 변수 $x에 저장된 새 경로도 포트 8025와 MatchUri "\*.litwareinc.com"을 사용합니다.

그런 다음 ID가 service:Registrar:atl-cs-001.litwareinc.com인 새 컬렉션을 만들기 위해 **New-CsStaticRoutingConfiguration** cmdlet을 호출하여 변수 $x에 저장된 경로를 새 컬렉션의 Route 속성에 할당합니다.

    $x = New-CsStaticRoute -TCPRoute -Destination "192.168.0.100" -Port 8025 -MatchUri "*.litwareinc.com"
    
    New-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" -Route $x

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버에서 알고리즘을 사용하여 메시지가 전달되어야 하는 다음 위치(다음 홉)를 확인합니다. 고정 경로의 경우 메시지 경로는 시스템 관리자에 의해 미리 결정됩니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 설치하면 전역 고정 경로 컬렉션이 자동으로 만들어집니다. 그뿐만 아니라 **New-CsStaticRoutingConfiguration** cmdlet을 사용하여 추가 컬렉션과 사이트 범위 또는 서비스 범위(등록자 서비스에만 해당)을 만들 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsStaticRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsStaticRoutingConfiguration"}

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
<td><p>만들려는 새 고정 경로 지정 컬렉션의 고유 식별자입니다. 새 컬렉션은 서비스 범위에서만 만들 수 있고 등록자 서비스에만 할당할 수 있습니다. 따라서 새 컬렉션의 ID는 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 유사해야 합니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Route</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>컬렉션 내에서 유지 관리되는 개별 고정 경로입니다. 컬렉션에 추가할 경로는 다른 컬렉션에서 복사하거나 <strong>New-CsStaticRoute</strong> cmdlet을 사용하여 만들어야 합니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p></td>
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

없음. **New-CsStaticRoutingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsStaticRoutingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)  
[New-CsStaticRoute](new-csstaticroute.md)  
[Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

