---
title: Remove-CsRgsWorkflow
TOCTitle: Remove-CsRgsWorkflow
ms:assetid: 9626df55-e3ed-478a-a485-f2a9abcf493b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398765(v=OCS.15)
ms:contentKeyID: 49304443
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRgsWorkflow

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 워크플로를 삭제합니다. 워크플로는 응답 그룹 응용 프로그램이 전화 통화를 수신할 때 수행되는 작업을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRgsWorkflow -Instance <Workflow> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 모든 응답 그룹 워크플로를 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsWorkflow**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 워크플로의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 워크플로를 삭제하는 **Remove-CsRgsWorkflow**에 파이프됩니다.

    Get-CsRgsWorkflow -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com | Remove-CsRgsWorkflow

## 예제 2

예제 2에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 있는 "Help Desk Workflow"라는 단일 응답 그룹 워크플로를 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 Help Desk Workflow라는 워크플로를 반환합니다. 이 워크플로는 **Remove-CsRgsWorkflow**에 파이프되어 삭제됩니다.

    Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Workflow" | Remove-CsRgsWorkflow

## 예제 3

예제 3에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 영어(미국)로 된 모든 워크플로를 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 워크플로를 검색합니다. 이 컬렉션은 언어가 영어(미국)(en-us)와 같은 워크플로만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsRgsWorkflow** cmdlet에 파이프됩니다.

    Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.Language -eq "en-us"} | Remove-CsRgsWorkflow

## 예제 4

예제 4에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 CustomMusicOnHoldFile 속성에 대해 구성된 값이 있는 모든 응답 그룹 워크플로를 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 워크플로의 컬렉션을 반환합니다. 이 컬렉션은 CustomMusicOnHoldFile 속성이 Null 값과 같지 않은 워크플로만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 속성이 Null 값과 같지 않다는 것은 이 워크플로에 대해 사용자 지정 음악이 정의되어 있음을 의미합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsRgsWorkflow**에 파이프됩니다.

    Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.CustomMusicOnHoldFile -ne $Null} | Remove-CsRgsWorkflow

## 자세한 정보

워크플로는 응답 그룹 응용 프로그램의 주요 요소입니다. 각 워크플로는 한 전화 번호에만 고유하게 연결됩니다. 누군가 그 번호로 전화를 걸면 워크플로에 따라 해당 전화의 처리 방법이 결정됩니다. 예를 들어 발신자에게 추가 정보를 입력하라는 일련의 IVR(대화형 음성 응답) 질문("하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 전화를 경로 지정할 수 있습니다. 또는 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치되고 발신자가 통화 대기 상태에 놓일 수 있습니다. 에이전트가 전화를 받을 수 있는 상태인지도 워크플로에서 지정합니다. 워크플로는 업무 시간(에이전트가 전화를 받을 수 있는 요일과 시간)과 휴일(에이전트가 전화를 받을 수 없는 요일)을 유지 관리하는 데 사용됩니다.

새 워크플로는 **New-CsRgsWorkflow** cmdlet을 사용하여 만듭니다. 이러한 워크플로를 만든 후 나중에 **Remove-CsRgsWorkflow**를 사용하여 삭제할 수 있습니다. 그러나 삭제된 워크플로는 응답 그룹 응용 프로그램에서 완전히 제거되므로 주의해야 합니다. 워크플로를 일시적으로 사용하지 않으려면 **Remove-CsRgsWorkflow** 대신 **Set-CsRgsWorkflow** cmdlet을 사용하여 워크플로를 사용하지 않도록 설정합니다. 그러면 나중에 다시 사용하도록 설정할 수 있습니다.

활성 워크플로를 삭제하려고 하면 **Remove-CsRgsWorkflow**에서 워크플로를 삭제할지 확인하는 메시지를 표시합니다. 사용자가 이 프롬프트에 응답할 때까지 **Remove-CsRgsWorkflow**가 더 이상 작업을 수행하지 않습니다. 이 프롬프트를 무시하고 활성 워크플로를 자동으로 삭제하려면 Force 매개 변수를 사용합니다. 예를 들면 다음과 같습니다.

Get-CsRgsWorkflow –Identity "service:ApplicationServer:atl-cs-001.litwareinc.com " | Remove-CsRgsWorkflow –Force

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRgsWorkflow** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRgsWorkflow"}

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
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow</p></td>
<td><p>제거할 워크플로를 가리키는 개체 참조입니다. 워크플로 개체를 <strong>Remove-CsRgsWorkflow</strong>에 파이프할 때 Instance 매개 변수를 삭제할 수 있습니다.</p>
<p>Instance 매개 변수를 사용하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-CsRgsWorkflow –Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83</p>
<p>Remove-CsRgsWorkflow –Instance $x</p>
<p>Instance 매개 변수를 사용하는 경우 한 번에 하나의 워크플로만 제거할 수 있습니다. 이는 개체 참조($x)가 여러 워크플로 개체를 포함할 수 없음을 의미합니다.</p></td>
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
<td><p>워크플로를 강제로 제거합니다. 이 매개 변수가 있으면 현재 활성화되어 있는 경우에도 경고 없이 워크플로가 삭제됩니다. 이 매개 변수가 없으면 활성 워크플로를 삭제할지 확인하는 메시지가 표시됩니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow 개체**. Remove-CsRgsWorkflow**는 응답 그룹 워크플로 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsRgsWorkflow**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsWorkflow](get-csrgsworkflow.md)  
[New-CsRgsWorkflow](new-csrgsworkflow.md)  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)

