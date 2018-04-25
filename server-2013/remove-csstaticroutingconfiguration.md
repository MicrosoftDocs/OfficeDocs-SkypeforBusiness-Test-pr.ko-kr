---
title: Remove-CsStaticRoutingConfiguration
TOCTitle: Remove-CsStaticRoutingConfiguration
ms:assetid: 844e849e-a2f6-42fd-a49c-1ab234a07a65
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398668(v=OCS.15)
ms:contentKeyID: 49304247
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsStaticRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 고정 경로 구성 설정 컬렉션을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsStaticRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 service:Registrar:atl-cs-001.litwareinc.com인 고정 경로 구성 컬렉션을 제거합니다.

    Remove-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 서비스 범위에 적용된 모든 고정 경로 구성 컬렉션이 제거됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsStaticRoutingConfiguration** cmdlet 및 Filter 매개 변수를 사용합니다. 필터 값 "service:\*"는 ID가 문자열 값 "service:"으로 시작하는 컬렉션만 반환되도록 합니다. 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsStaticRoutingConfiguration** cmdlet에 파이프됩니다.

    Get-CsStaticRoutingConfiguration -Filter "service:*" | Remove-CsStaticRoutingConfiguration

## 예제 3

예제 3에서는 실제 경로에 할당되지 않은 모든 고정 경로 구성 컬렉션을 삭제하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 **Get-CsStaticRoutingConfiguration** cmdlet을 호출하여 조직에서 사용되는 모든 고정 경로 컬렉션에 대한 정보를 반환합니다. 이 컬렉션은 경로의 수(Route.Count)가 0과 같은 컬렉션만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 필터링된 정보는 하나 이상의 경로에 할당되지 않은 각 컬렉션을 삭제하는 **Remove-CsStaticRoutingConfiguration** cmdlet에 파이프됩니다.

    Get-CsStaticRoutingConfiguration | Where-Object {$_.Route.Count -eq 0} | Remove-CsStaticRoutingConfiguration

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버에서 알고리즘을 사용하여 메시지가 전달되어야 하는 다음 위치(다음 홉)를 확인합니다. 고정 경로의 경우 메시지 경로는 시스템 관리자에 의해 미리 결정됩니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 설치하면 전역 고정 경로 컬렉션이 자동으로 만들어집니다. 컬렉션이 만들어지지만 이 컬렉션에 경로는 할당되지 않습니다. 또한 이 소프트웨어를 통해 서비스 범위에 적용되는 추가 컬렉션을 만들 수 있습니다. 이러한 새 컬렉션은 등록자 서비스에만 할당할 수 있습니다. 나중에 원하는 경우 **Remove-CsStaticRoutingConfiguration** cmdlet을 사용하여 서비스 범위에 적용된 컬렉션을 삭제할 수 있습니다.

또한 전역 컬렉션에 대해 **Remove-CsStaticRoutingConfiguration** cmdlet을 실행할 수도 있습니다. 단, Lync Server에서는 전역 컬렉션을 제거하도록 허용하지 않으므로 이 경우 전역 컬렉션이 제거되지 않습니다. 대신 전역 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. 이는 전역 컬렉션에 할당된 모든 경로가 삭제됨을 의미합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsStaticRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsStaticRoutingConfiguration"}

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
<td><p>제거할 고정 경로 구성 컬렉션의 고유 식별자입니다. 사이트 범위에 구성된 컬렉션을 제거하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 같은 구문을 사용합니다.</p>
<p><strong>Remove-CsStaticRoutingConfiguration</strong> cmdlet은 전역 컬렉션에 대해서도 실행할 수 있습니다. 이렇게 하려면 -Identity global 구문을 사용합니다. 단, 전역 컬렉션은 실제로 제거되지 않습니다. 대신 해당 컬렉션의 속성이 기본값으로 다시 설정됩니다. 즉, Route 속성의 모든 항목이 삭제됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체입니다. **Remove-CsStaticRoutingConfiguration** cmdlet은 고정 경로 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsStaticRoutingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)  
[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

