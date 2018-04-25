---
title: 위치 기반 라우팅 사용
TOCTitle: 위치 기반 라우팅 사용
ms:assetid: 029ede7e-0c4e-4ad2-af99-909ae674d6fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994014(v=OCS.15)
ms:contentKeyID: 52056777
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 위치 기반 라우팅 사용

 

_**마지막으로 수정된 항목:** 2015-03-09_

Enterprise Voice를 배포하고 네트워크 영역, 사이트 및 서브넷을 정의한 후에 위치 기반 라우팅을 설정할 수 있습니다. 위치 기반 라우팅은 다음 Enterprise Voice 요소에 대해 사용할 수 있도록 설정해야 합니다.

  - 네트워크 사이트

  - 트렁크 구성

  - 음성 정책

  - 라우팅 구성

## 네트워크 사이트에 대해 위치 기반 라우팅을 사용하도록 설정

Enterprise Voice를 배포하고 네트워크 사이트를 구성한 경우 위치 기반 라우팅을 구성할 수 있습니다. 먼저 해당 PSTN 사용법과 네트워크 사이트를 연결하기 위한 음성 라우팅 정책을 만듭니다. 음성 라우팅 정책에 PSTN 사용법을 할당할 때에는 위치 기반 라우팅 제한이 필요하지 않은 영역에 위치한 사이트나 PSTN 게이트웨이의 로컬 PSTN 게이트웨이를 사용하는 음성 경로에 연결된 PSTN 사용법만 사용해야 합니다. 음성 라우팅 정책을 만들려면 Lync ServerWindows PowerShell 명령 New-CsVoiceRoutingPolicy 또는 Lync Server 제어판을 사용합니다.

    New-CsVoiceRoutingPolicy -Identity <voice routing policy ID> -Name <voice routing policy name> -PstnUsages <usages>

자세한 내용은 [New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)를 참고하세요.

다음 표와 Windows PowerShell 명령은 이 시나리오에서 정의된 두 개의 음성 라우팅 정책과 관련 PSTN 사용법을 보여줍니다. 이 표에는 위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

    New-CsVoiceRoutingPolicy -Identity "DelhiVoiceRoutingPolicy" -Name "Delhi voice routing policy" -PstnUsages @{add="Delhi usage", "PBX Del usage", "PBX Hyd usage"}
    New-CsVoiceRoutingPolicy -Identity "HyderabadVoiceRoutingPolicy" -Name " Hyderabad voice routing policy" -PstnUsages @{add="Hyderabad usage", "PBX Del usage", "PBX Hyd usage"}


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>음성 라우팅 정책 1</th>
<th>음성 라우팅 정책 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>음성 정책 ID</p></td>
<td><p>델리 음성 라우팅 정책</p></td>
<td><p>히드라바드 음성 라우팅 정책</p></td>
</tr>
<tr class="even">
<td><p>PSTN 사용법</p></td>
<td><p>델리 사용법, PBX Del 사용법, PBX Hyd 사용법</p></td>
<td><p>히드라바드 사용법, PBX Hyd 사용법, PBX Del 사용법</p></td>
</tr>
</tbody>
</table>

  

다음으로 적용 가능한 네트워크 사이트에 대한 위치 기반 라우팅을 구성하고 여기에 음성 라우팅 정책을 연결합니다. 위치 기반 라우팅을 설정하려면 Lync ServerWindows PowerShell 명령 New-CsNetworkSite를 사용하고 라우팅 제한을 적용해야 하는 네트워크 사이트에 음성 라우팅 정책을 연결합니다.

    Set-CsNetworkSite -Identity <site ID> -EnableLocationBasedRouting <$true|$false> -VoiceRoutingPolicy <voice routing policy ID>

다음 표는 Lync ServerWindows PowerShell을 사용하여 이 시나리오에서 정의된 두 개의 서로 다른 네트워크 사이트(델리 및 히드라바드)에 대한 위치 기반 라우팅을 보여줍니다. 이 표에는위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

    Set-CsNetworkSite -Identity "Delhi" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "DelhiVoiceRoutingPolicy"
    Set-CsNetworkSite -Identity "Hyderabad" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "HyderabadVoiceRoutingPolicy"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>사이트 1(델리)</th>
<th>사이트 2(히드라바드)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>사이트 이름</p></td>
<td><p>사이트 1(델리)</p></td>
<td><p>사이트 2(히드라바드)</p></td>
</tr>
<tr class="even">
<td><p>EnableLocationBasedRouting</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p>음성 라우팅 정책</p></td>
<td><p>델리 음성 라우팅 정책</p></td>
<td><p>히드라바드 음성 라우팅 정책</p></td>
</tr>
<tr class="even">
<td><p>서브넷</p></td>
<td><p>서브넷 1(델리)</p></td>
<td><p>서브넷 2(히드라바드)</p></td>
</tr>
</tbody>
</table>



## 트렁크에 대해 위치 기반 라우팅을 사용할 수 있도록 설정

위치 기반 라우팅을 사용할 수 있도록 트렁크 구성을 설정하려면 먼저 각 트렁크 또는 각 네트워크 사이트에 대해 트렁크 설정을 만들어야 합니다. 트렁크 구성을 만들려면 Lync ServerWindows PowerShell 명령 New-CsTrunkConfiguration을 사용합니다. 여러 개의 트렁크가 지정된 시스템(예: 게이트웨이 또는 PBX)과 연결되어 있는 경우 위치 기반 라우팅 제한을 사용하도록 각 트렁크 구성을 수정해야 합니다.

    New-CsTrunkConfiguration -Identity < trunk configuration ID>

자세한 내용은 [New-CsTrunkConfiguration](new-cstrunkconfiguration.md)을 참고하세요.

다음 Windows PowerShell 명령은 이 시나리오에서 정의된 배포의 트렁크마다 하나의 트렁크 구성을 만드는 과정을 보여줍니다.

    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 1 DEL-GW>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 2 HYD-GW>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 3 DEL-PBX>"
    New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 4 HYD-PBX>"

트렁크당 하나의 트렁크 구성을 구성했으면 Lync ServerWindows PowerShell 명령 Set-CsTrunkConfiguration을 사용하여 라우팅 제한을 적용해야 하는 트렁크에 대해 위치 기반 라우팅을 사용하도록 설정할 수 있습니다. 통화의 경로를 PSTN 게이트웨이로 지정하는 트렁크에 대해 위치 기반 라우팅을 설정하고 게이트웨이가 있는 네트워크 사이트를 연결합니다.

    Set-CsTrunkConfiguration -Identity <trunk configuration ID> -EnableLocationRestriction $true -NetworkSiteID <site ID>

자세한 내용은 [New-CsTrunkConfiguration](new-cstrunkconfiguration.md)을 참고하세요.

이 예에서는 델리와 히드라바드의 PSTN 게이트웨이에 연결된 각 트렁크에 대해 위치 기반 라우팅이 설정되어 있습니다.

    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 1 DEL-GW -EnableLocationRestriction $true -NetworkSiteID "Delhi"
    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 2 HYD-GW -EnableLocationRestriction $true -NetworkSiteID "Hyderabad"

  

통화의 경로를 PSTN으로 지정하지 않는 트렁크의 경우 위치 기반 라우팅을 활성화하지 마세요. 하지만 이 경우에도 이 트렁크를 통해 연결되는 끝점에 도달하는 PSTN 통화에 대해 위치 기반 라우팅 제한을 적용해야 하므로 시스템이 있는 네트워크 사이트에 여전히 트렁크를 연결해야 합니다. 이 예에서는 델리와 히드라바드의 PBX 시스템에 연결된 각 트렁크에 대해 위치 기반 라우팅이 설정되어 있지 않습니다.

    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 3 DEL-PBX -EnableLocationRestriction $false -NetworkSiteID "Delhi"
    Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 4 HYD-PBX -EnableLocationRestriction $false -NetworkSiteID "Hyderabad"

  
통화의 경로를 PSTN으로 지정하지 않는 시스템(예: PBX)에 연결된 끝점에는 위치 기반 라우팅을 사용할 수 있는 사용자의 Lync 끝점과 비슷한 제한이 적용됩니다. 따라서 이 사용자는 사용자의 위치에 관계없이 Lync 사용자에게 전화를 걸고 받을 수 있습니다. 또한 시스템에 연결된 네트워크 사이트와 상관없이 통화의 경로를 PSTN 네트워크로 지정하지 않는 다른 시스템(예: 다른 PBX에 연결된 끝점)으로 전화를 걸고 받을 수 있습니다. PSTN 끝점이 사용되는 모든 인바운드 통화, 아웃바운드 통화, 통화 전송 및 통화 전달에는 위치 기반 라우팅이 적용됩니다. 이러한 통화는 해당 시스템에 대해 로컬로 정의된 PSTN 게이트웨이만 사용해야 합니다.

다음 표는 서로 다른 네트워크 사이트 2개에 속한 트렁크 4개(PSTN 게이트웨이에 연결된 트렁크 2개 및 PBX 시스템에 연결된 트렁크 2개)의 트렁크 구성을 보여줍니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>EnableLocationRestriction</th>
<th>NetworkSiteID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PstnGateway:Trunk 1 DEL-GW</p></td>
<td><p>True</p></td>
<td><p>사이트 1(델리)</p></td>
</tr>
<tr class="even">
<td><p>PstnGateway:Trunk 2 HYD-GW</p></td>
<td><p>True</p></td>
<td><p>사이트 2(히드라바드)</p></td>
</tr>
<tr class="odd">
<td><p>PstnGateway:Trunk 3 DEL-PBX</p></td>
<td><p>False</p></td>
<td><p>사이트 1(델리)</p></td>
</tr>
<tr class="even">
<td><p>PstnGateway:Trunk 4 HYD-PBX</p></td>
<td><p>False</p></td>
<td><p>사이트 2(히드라바드)</p></td>
</tr>
</tbody>
</table>



## 음성 정책에 대해 위치 기반 라우팅을 사용할 수 있도록 설정

특정 사용자에게 음설 기반 라우팅을 적용하려면 PSTN 유료 우회 방지를 방지하도록 해당 사용자의 음성 정책을 구성합니다. PSTN 유료 우회를 방지하여 위치 기반 라우팅을 사용하도록 설정하려면 Lync ServerWindows PowerShell 명령 New-CsVoicePolicy를 사용하여 새 음성 정책을 만들거나 기존 정책을 사용 중인 경우 Set-CsVoicePolicy를 만듭니다.

    Set-CsVoicePolicy -Identity <voice policy ID> -PreventPSTNTollBypass <$true|$false>

자세한 내용은 [New-CsVoicePolicy](new-csvoicepolicy.md)를 참고하세요.

다음 표와 Windows PowerShell 명령은 이 시나리오에서 정의된 델리와 히드라바드 음성 정책으로 PSTN 유료 우회 방지를 설정하는 과정을 보여줍니다. 이 표에는 위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

    Set-CsVoicePolicy -Identity "Delhi voice policy" -PreventPSTNTollBypass $true
    Set-CsVoicePolicy -Identity "Hyderabad voice policy" -PreventPSTNTollBypass $true


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>음성 정책 1</th>
<th>음성 정책 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>음성 정책 ID</p></td>
<td><p>델리 음성 정책</p></td>
<td><p>히드라바드 음성 정책</p></td>
</tr>
<tr class="even">
<td><p>PSTN 사용법</p></td>
<td><p>델리 사용법, PBX Del 사용법, PBX Hyd 사용법</p></td>
<td><p>히드라바드 사용법, PBX Hyd 사용법, PBX Del 사용법</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>



## 라우팅 구성에서 위치 기반 라우팅을 사용할 수 있도록 설정

마지막으로 라우팅 구성에 대해 전역적으로 위치 기반 라우팅을 사용하도록 설정합니다. 위치 기반 라우팅을 설정하려면 Lync ServerWindows PowerShell 명령을 사용합니다.

    Set-CsRoutingConfiguration -EnableLocationBasedRouting $true

자세한 내용은 [Set-CsRoutingConfiguration](set-csroutingconfiguration.md)을 참고하세요.


> [!NOTE]
> 위치 기반 라우팅은 전역 구성을 통해 설정해야 하지만 적용되는 규칙 집합은 이 설명서에 명시된 대로 구성된 사이트, 사용자 및 트렁크에 대해서만 적용됩니다.




## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 위치 기반 라우팅 구성](lync-server-2013-configuring-location-based-routing.md)

