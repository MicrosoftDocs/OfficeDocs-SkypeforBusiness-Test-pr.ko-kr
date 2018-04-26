---
title: Remove-CsServerApplication
TOCTitle: Remove-CsServerApplication
ms:assetid: 55325d8c-9c67-4e88-868d-ce62bc11322e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398366(v=OCS.15)
ms:contentKeyID: 49303668
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsServerApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 서버 응용 프로그램을 제거합니다. 서버 응용 프로그램은 Lync Server에서 호스트되는 응용 프로그램입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsServerApplication -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Identity가 service: EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor인 서버 응용 프로그램을 제거합니다. ID는 고유하므로 이 명령은 둘 이상의 응용 프로그램을 삭제하지 않습니다.

    Remove-CsServerApplication -Identity "service:EdgeServer:atl-edge-001.litwareinc.com/EdgeMonitor"

## 예제 2

예제 2에서는 중요하지 않은 모든 서버 응용 프로그램을 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsServerApplication** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 서버 응용 프로그램의 컬렉션을 반환합니다. 이 컬렉션은 Critical 속성이 False와 같은 모든 응용 프로그램을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsServerApplication** cmdlet에 파이프됩니다.

    Get-CsServerApplication | Where-Object {$_.Critical -eq $False} | Remove-CsServerApplication

## 예제 3

예제 3에서는 EdgeServer:atl-cs-001.litwareinc.com 서비스에서 사용하도록 구성된 모든 서버 응용 프로그램을 삭제합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 지정하고 **Get-CsServerApplication** cmdlet을 사용합니다. 필터 값에는 "service:EdgeServer:atl-cs-001.litwareinc.com/\*"를 사용하여 ID가 "service:EdgeServer:atl-cs-001.litwareinc.com/"으로 시작하는 모든 응용 프로그램을 반환합니다. 그런 다음 해당 컬렉션은 EdgeServer:atl-cs-001.litwareinc.com에서 각 응용 프로그램을 삭제하는 **Remove-CsServerApplication** cmdlet에 파이프됩니다.

    Get-CsServerApplication -Filter "service:EdgeServer:atl-cs-001.litwareinc.com/*" | Remove-CsServerApplication

## 자세한 정보

서버 응용 프로그램은 Lync Server에서 실행되는 개별 프로그램입니다. **Remove-CsServerApplication** cmdlet을 사용하면 관리자가 Lync Server의 일부로 실행되는 응용 프로그램을 제거할 수 있습니다. 서버 응용 프로그램을 삭제하는 것은 응용 프로그램을 제거하는 것과는 다릅니다. **Remove-CsServerApplication** cmdler을 실행하면 응용 프로그램이 더 이상 Lync Server에서 실행되지 않습니다. 그러나 소프트웨어 자체가 제거되는 것은 아니며 **New-CsServerApplication** cmdlet을 실행하여 응용 프로그램을 다시 활성화할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsServerApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsServerApplication }

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
<td><p>제거할 서버 응용 프로그램에 대한 고유한 식별자입니다. 서버 응용 프로그램 ID는 응용 프로그램이 호스트되는 서비스와 응용 프로그램 이름으로 구성됩니다. 예를 들어 QoEAgent라는 서버 응용 프로그램의 ID는 service:Registrar:atl-cs-001.litwareinc.com/QoEAgent와 유사할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application 개체입니다. **Remove-CsServerApplication** cmdlet은 서버 응용 프로그램 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsServerApplication** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsServerApplication](get-csserverapplication.md)  
[New-CsServerApplication](new-csserverapplication.md)  
[Set-CsServerApplication](set-csserverapplication.md)

