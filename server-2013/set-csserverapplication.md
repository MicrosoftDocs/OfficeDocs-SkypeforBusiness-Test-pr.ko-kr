---
title: Set-CsServerApplication
TOCTitle: Set-CsServerApplication
ms:assetid: b0f75629-b6c3-4958-b466-6c8a2f104819
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412850(v=OCS.15)
ms:contentKeyID: 49304752
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsServerApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 서버 응용 프로그램의 속성 값을 수정합니다. 서버 응용 프로그램은 Lync Server에서 호스트하는 응용 프로그램입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsServerApplication [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsServerApplication [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Critical <$true | $false>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-Priority <Int32>] [-Script <String>] [-ScriptName <String>] [-Uri <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 Registrar:atl-cs-001.litwareinc.com/ExumRouting인 서버 응용 프로그램을 사용하도록 설정합니다. ID는 고유해야 하므로 이 명령은 단일 서버 응용 프로그램만 사용하도록 설정합니다.

    Set-CsServerApplication -Identity "Registrar:atl-cs-001.litwareinc.com/ExumRouting" -Enabled $True

## 예제 2

예제 2에서는 현재 사용하지 않도록 설정된 모든 서버 응용 프로그램을 사용하도록 설정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsServerApplication** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 서버 응용 프로그램의 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 응용 프로그램만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 가져와서 Enabled 속성을 True로 설정하는 **Set-CsServerApplication** cmdlet에 파이프됩니다.

    Get-CsServerApplication | Where-Object {$_.Enabled -eq $False} | Set-CsServerApplication -Enabled $True

## 자세한 정보

서버 응용 프로그램은 Lync Server에서 실행되는 개별 프로그램을 의미합니다. **Set-CsServerApplication** cmdlet을 사용하면 관리자가 Lync Server의 일부로 실행되는 응용 프로그램 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsServerApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsServerApplication"}

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
<td><p><em>Critical</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 해당 응용 프로그램을 시작할 수 있을 때까지 Lync Server가 시작되지 않습니다. False로 설정하면 해당 응용 프로그램을 시작할 수 있는지 여부에 관계없이 Lync Server가 시작됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>응용 프로그램을 사용하려면 이 값을 True로 설정하고, 응용 프로그램을 사용하지 않으려면 이 값을 False로 설정합니다.</p></td>
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
<td><p>수정할 서버 응용 프로그램의 고유 식별자입니다. 서버 응용 프로그램 ID는 응용 프로그램이 호스트되는 서비스와 응용 프로그램 이름으로 구성됩니다. 예를 들어 QoEAgent라는 서버 응용 프로그램의 ID는 Registrar:atl-cs-001.litwareinc.com/QoEAgent와 유사할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>ServerApplication.Application 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>서버 응용 프로그램의 실행 순서를 나타냅니다. 우선 순위가 0인 응용 프로그램이 맨 먼저 시작되고, 우선 순위가 1인 응용 프로그램이 두 번째로 시작됩니다. 서버 응용 프로그램을 호스트하는 각 서비스에는 고유의 우선 순위 집합이 있습니다. 예를 들어 등록자 서비스는 해당 우선 순위가 0, 1, 2인 응용 프로그램 세 개를 호스트할 수 있습니다. 마찬가지로 에지 서버 서비스에는 응용 프로그램 네 개가 있을 수 있는데, 이러한 응용 프로그램의 우선 순위는 0, 1, 2, 3이 됩니다.</p>
<p>우선 순위를 지정하지 않으면 응용 프로그램이 우선 순위 목록의 맨 아래에 자동으로 추가됩니다. 응용 프로그램을 추가하거나 제거하면 그에 따라 다른 응용 프로그램의 우선 순위가 조정됩니다. 예를 들어 우선 순위가 0인 응용 프로그램을 삭제하면 이전에 우선 순위가 1인 응용 프로그램의 우선 순위가 자동으로 0으로 설정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Script</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서버 응용 프로그램을 스크립트와 연결할 수 있습니다. 서버 응용 프로그램에 스크립트를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Script &quot;Update.ps1&quot;</p>
<p>스크립트를 제거하려면 Script 속성을 null 값으로 설정하면 됩니다.</p>
<p>-Script $Null</p>
<p>각 서버 응용 프로그램은 스크립트 하나에만 연결할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ScriptName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램에서 사용하는 MSPL(Microsoft SIP Processing Language) 스크립트의 경로입니다. MSPL은 SIP 메시지를 필터링 및 경로 지정하는 데 사용되는 스크립팅 언어입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Uri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램의 고유한 URI(Uniform Resource Identifier)입니다. 예를 들어 QoEAgent 응용 프로그램의 URI는 http://www.microsoft.com/LCS/QoEAgent입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application 개체입니다. **Set-CsServerApplication** cmdlet은 서버 응용 프로그램 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsServerApplication** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.application 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsServerApplication](get-csserverapplication.md)  
[New-CsServerApplication](new-csserverapplication.md)  
[Remove-CsServerApplication](remove-csserverapplication.md)

