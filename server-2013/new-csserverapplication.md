---
title: New-CsServerApplication
TOCTitle: New-CsServerApplication
ms:assetid: 045e6e65-8ad6-49af-8bfb-aa9045fa4dd8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398096(v=OCS.15)
ms:contentKeyID: 49302659
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsServerApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 서버 응용 프로그램을 만듭니다. 서버 응용 프로그램은 Lync Server에서 호스트되는 응용 프로그램입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsServerApplication -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsServerApplication -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Uri <String> [-Confirm [<SwitchParameter>]] [-Critical <$true | $false>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Priority <Int32>] [-Script <String>] [-ScriptName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor인 새 서버 응용 프로그램을 만듭니다. Identity를 지정할 뿐 아니라 Uri 및 Critical 매개 변수도 포함됩니다. 두 매개 변수는 응용 프로그램 URI를 지정하고 응용 프로그램이 중요하게 간주되지 않음을 나타내는 데 사용됩니다.

    New-CsServerApplication -Identity "EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor" -Uri http://www.litwareinc.com/edgemonitor -Critical $False

## 예제 2

예제 2에 표시된 명령은 초기에 메모리에만 있는 새 서버 응용 프로그램을 만드는 방법을 보여 줍니다. 이 작업을 위해 첫 번째 명령은 두 매개 변수와 함께 **New-CsServerApplication** cmdlet을 호출합니다. Identity는 응용 프로그램의 Identity를 지정하고 InMemory는 새 응용 프로그램이 메모리에만 만들어져야 함을 나타냅니다. 결과 서버 응용 프로그램 개체는 변수 $x에 저장됩니다.

이 가상 서버 응용 프로그램이 만들어진 후 각각 Uri 및 Critical 속성 값을 수정하기 위해 명령 2와 3이 사용됩니다. 마지막으로, 명령 4는 가상 서버 응용 프로그램을 실제 서버 응용 프로그램으로 변환하는 데 사용됩니다. 이 마지막 명령은 필수입니다. **Set-CsServerApplication** cmdlet을 호출하지 않으면 EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor에 대해 응용 프로그램이 구성되지 않으며, Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 응용 프로그램이 사라집니다.

    $x = New-CsServerApplication -Identity "EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor" -InMemory
    $x.Uri = "http://www.litwareinc.com/edgemonitor"
    $x.Critical = $False
    Set-CsServerApplication -Instance $x

## 자세한 정보

서버 응용 프로그램은 Lync Server에서 실행되는 개별 프로그램입니다. **New-CsServerApplication** cmdlet을 통해 관리자는 새 서버 응용 프로그램을 구성할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsServerApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsServerApplication"}

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
<td><p>만들려는 서버 응용 프로그램의 고유 식별자입니다. 서버 응용 프로그램 ID는 응용 프로그램이 호스트되는 서비스와 응용 프로그램 이름으로 구성됩니다. 예를 들어 QoEAgent라는 서버 응용 프로그램의 ID는 service:Registrar:atl-cs-001.litwareinc.com/QoEAgent와 유사할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>서비스 이름입니다. Identity 매개 변수를 사용하는 경우 새 서비스를 만들 때 Name 매개 변수를 포함할 필요가 없습니다. Name 속성은 응용 프로그램 Identity의 이름 부분을 사용하여 채워집니다. 예를 들어 ID가 service:Registrar:atl-cs-001.litwareinc.com/TestService인 새 응용 프로그램을 만드는 경우 응용 프로그램 이름은 자동으로 TestService로 지정됩니다. Name 매개 변수는 Parent 매개 변수를 사용하는 경우에만 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 서버 응용 프로그램을 호스트할 서비스를 지정합니다. Identity 매개 변수를 사용하는 경우 Parent 또는 Name 매개 변수를 사용할 필요가 없습니다. 응용 프로그램 ID는 Parent 속성 값과 Name 속성 값의 조합으로 구성되기 때문입니다. 그러나 Parent 및 Name 매개 변수를 대신 사용하는 경우 Identity를 생략할 수 있습니다. 이 경우 Parent 매개 변수는 -Parent &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 유사해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Uri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램의 고유 URI(Uniform Resource Identifier)입니다. 예를 들어 QoEAgent 응용 프로그램의 URI는 http://www.microsoft.com/LCS/QoEAgent입니다.</p></td>
</tr>
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
<td><p>True로 설정하면 해당 응용 프로그램을 시작할 수 있을 때까지 Lync Server가 시작되지 않습니다. False로 설정하면 해당 응용 프로그램을 시작할 수 있는지 여부에 관계없이 Lync Server가 시작됩니다. 이 매개 변수를 지정하지 않으면 Critical 속성이 True로 설정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>응용 프로그램을 사용하려면 이 값을 True로 설정하고, 응용 프로그램을 사용하지 않으려면 이 값을 False로 설정합니다. 이 매개 변수를 지정하지 않으면 Enabled 속성이 False로 설정되고 새 응용 프로그램이 사용할 수 없도록 설정됩니다.</p></td>
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
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>서버 응용 프로그램의 실행 순서를 나타냅니다. 우선 순위가 0인 응용 프로그램이 맨 먼저 시작되고, 우선 순위가 1인 응용 프로그램이 두 번째로 시작됩니다. 서버 응용 프로그램을 호스트하는 각 서비스에는 고유의 우선 순위 집합이 있습니다. 예를 들어 등록자 서비스는 해당 우선 순위가 0, 1, 2인 응용 프로그램 세 개를 호스트할 수 있습니다. 마찬가지로 에지 서버 서비스에는 응용 프로그램 네 개가 있을 수 있는데, 이러한 응용 프로그램의 우선 순위는 0, 1, 2, 3이 됩니다.</p>
<p>우선 순위를 지정하지 않으면 응용 프로그램이 우선 순위 목록의 맨 아래에 자동으로 추가됩니다. 응용 프로그램을 추가하거나 제거하면 그에 따라 다른 응용 프로그램의 우선 순위가 조정됩니다. 예를 들어 우선 순위가 0인 응용 프로그램을 삭제하면 이전에 우선 순위가 1인 응용 프로그램의 우선 순위가 자동으로 0으로 설정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Script</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서버 응용 프로그램을 스크립트와 연결할 수 있습니다. 서버 응용 프로그램에 스크립트를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Script &quot;Update.ps1&quot;</p>
<p>스크립트를 제거하려면 Script 속성을 null 값으로 설정하면 됩니다.</p>
<p>-Script $Null</p>
<p>각 서버 응용 프로그램은 스크립트 하나에만 연결할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ScriptName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램에서 사용하는 MSPL(Microsoft SIP Processing Language) 스크립트의 경로입니다(해당되는 경우). MSPL은 SIP 메시지 필터링 및 경로 지정에 사용되는 스크립팅 언어입니다.</p></td>
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

없음. **New-CsServerApplication** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsServerApplication** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsServerApplication](get-csserverapplication.md)  
[Remove-CsServerApplication](remove-csserverapplication.md)  
[Set-CsServerApplication](set-csserverapplication.md)

