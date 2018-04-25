---
title: Set-CsRgsWorkflow
TOCTitle: Set-CsRgsWorkflow
ms:assetid: 36cffa89-e5bb-48fd-bd6e-da67066fd273
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425845(v=OCS.15)
ms:contentKeyID: 49303291
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsWorkflow

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 워크플로를 수정합니다. 워크플로는 응답 그룹 응용 프로그램이 전화 통화를 수신할 때 수행되는 작업을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsWorkflow -Instance <Workflow> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 기존 업무 시간 집합을 검색한 다음 해당 업무 시간을 Help Desk라는 워크플로에 할당합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsRgsHoursOfBusiness**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 US Business Hours라는 업무 시간 컬렉션을 검색합니다. 이러한 업무 시간은 $businessHours라는 변수에 저장됩니다.

업무 시간을 검색한 후에는 **Get-CsRgsWorkflow** cmdlet을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk 워크플로를 검색합니다. 이 개체는 $y라는 변수에 저장됩니다.

예제의 세 번째 명령은 BusinessHoursID를 검색된 컬렉션($businessHours.Identity)의 ID로 설정하여 Help Desk 워크플로의 BusinessHoursId 속성을 검색된 업무 시간 컬렉션으로 설정합니다. 마지막 명령은 **Set-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 실제 Help Desk 워크플로에 새 업무 시간을 기록합니다. 이전 단계의 모든 변경 내용은 메모리에만 적용되었기 때문에 이 마지막 단계가 중요합니다. 실제로 이러한 변경 내용을 Help Desk 워크플로에 저장하려면 **Set-CsRgsWorkflow**를 호출하여 워크플로의 가상 복사본이 포함된 개체 참조($y)에 cmdlet을 전달해야 합니다.

    $businessHours = Get-CsRgsHoursOfBusiness service:ApplicationServer:atl-cs-001.litwareinc.com -Name "US Business Hours"
    $y = Get-CsRgsWorkflow Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $y.BusinessHoursId = $businessHours.Identity
    Set-CsRgsWorkflow -Instance $y

## 예제 2

예제 2에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk 워크플로에 새 설명을 할당합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 지정된 워크플로(-Name "Help Desk")를 검색하고 검색된 개체를 $x라는 변수에 저장합니다. 그런 다음 두 번째 명령이 새 설명("Workflow for the Redmond Help Desk")을 Help Desk 워크플로의 가상 복사본에 추가합니다. 설명이 변경된 후 세 번째 명령은 **Set-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에 있는 실제 Help Desk 워크플로에 이러한 변경 내용을 다시 기록합니다.

    $x = Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.Description = "Workflow for the Redmond Help Desk" 
    Set-CsRgsWorkflow -Instance $x

## 예제 3

예제 3에 표시된 명령은 새 응답 그룹 오디오 파일을 가져온 다음 이 오디오 파일을 기존 워크플로에 할당합니다. 이렇게 하기 위해 예제의 첫 번째 명령은 새 오디오 파일을 가져옵니다. 이 작업을 수행하기 위해 **Get-Content** cmdlet을 호출하여 오디오 파일(C:\\MediaFiles\\Hold.wav)을 바이트 단위로 읽습니다. 오디오 파일을 정확하게 읽으려면 ReadCount 매개 변수(0으로 설정) 및 Encoding 매개 변수(Byte로 설정)를 포함해야 합니다. 오디오 파일을 읽은 후에는 데이터가 **New-CsRgsAudioFile**에 파이프되어 ApplicationServer:atl-cs-001.litwareinc.com에 새 파일이 만들어집니다. HelpDeskHoldMusic.wav라는 이 파일에 대한 개체 참조는 $musicFile이라는 변수에 저장됩니다.

오디오 파일이 만들어진 후 두 번째 명령은 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk 워크플로를 검색하여 반환된 개체를 $y라는 변수에 저장합니다. 그런 다음 세 번째 명령은 이 워크플로의 CustomMusicOnHoldFile 속성에 $musicFile(새로 만든 오디오 파일을 포함하는 변수) 값을 할당합니다.

$musicFile이 CustomMusicOnHoldFile에 할당된 후 마지막 명령은 **Set-CsRgsWorkflow** cmdlet을 사용하여 Help Desk 워크플로에 이러한 변경 내용을 다시 기록합니다.

    $musicFile = Get-Content -ReadCount 0 -Encoding Byte C:\MediaFiles\Hold.wav | Import-CsRgsAudioFile -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -FileName "HelpDeskHoldMusic.wav"
    $y = Get-CsRgsWorkflow -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $y.CustomMusicOnHoldFile = $musicFile
    Set-CsRgsWorkflow -Instance $y

## 자세한 정보

워크플로는 응답 그룹 응용 프로그램의 주요 요소입니다. 각 워크플로는 한 전화 번호에만 고유하게 연결됩니다. 누군가 그 번호로 전화를 걸면 워크플로에 따라 해당 전화의 처리 방법이 결정됩니다. 예를 들어 발신자에게 추가 정보를 입력하라는 일련의 IVR(대화형 음성 응답) 질문(예: "하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 전화를 경로 지정할 수 있습니다. 또는 전화를 큐에 두고 에이전트가 전화를 받을 수 있을 때까지 발신자가 대기하게 할 수도 있습니다. 에이전트가 전화를 받을 수 있는 상태인지도 워크플로에서 지정합니다. 워크플로는 업무 시간(에이전트가 전화를 받을 수 있는 요일과 시간)과 휴일(에이전트가 전화를 받을 수 없는 요일)을 구성하는 데 사용됩니다.

**Set-CsRgsWorkflow** cmdlet은 기존 워크플로의 속성을 수정하는 방법을 제공합니다. 예를 들어 워크플로의 전화 번호, 워크플로에 연결된 에이전트 그룹 또는 워크플로가 트리거될 때(즉, 누군가 워크플로에 연결된 전화 번호로 전화를 걸 때)마다 수행할 기본 작업을 변경할 수 있습니다.

**Set-CsRgsWorkflow**는 워크플로 자체를 직접 수정하지 않습니다. 대신 워크플로를 변경하려면 먼저 **Get-CsRgsWorkflow**를 사용하여 해당 워크플로에 대한 개체 참조를 만들어야 합니다. 즉, 원하는 워크플로를 검색한 다음 반환된 개체를 변수에 저장하면 됩니다. 개체 참조를 만든 후에는 메모리에 있는 개체의 속성을 수정한 다음 **Set-CsRgsWorkflow**를 사용하여 이러한 변경 내용을 "실제" 응답 그룹 응용 프로그램 워크플로에 다시 기록합니다. **Set-CsRgsWorkflow**를 호출하지 않으면 변경 내용이 메모리에만 존재하고 Windows PowerShell을 닫거나 개체 참조 변수를 삭제하는 즉시 사라집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsWorkflow** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsWorkflow"}

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
<td><p>수정할 응답 그룹 응용 프로그램 워크플로에 대한 개체 참조입니다. 일반적으로 개체 참조는 <strong>Get-CsRgsWorkflow</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 이 명령은 Help Desk 워크플로에 대한 개체 참조를 반환하여 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com -Name &quot;Help Desk&quot;</p>
<p>Instance 매개 변수는 위치 매개 변수입니다. 따라서 워크플로에 대한 개체 참조가 명령에 사용된 첫 번째 매개 변수 값인 경우 생략할 수 있습니다. 이는 다음 두 명령이 기능적으로 동일함을 의미합니다.</p>
<p>Set-CsRgsWorkflow –Instance $x</p>
<p>Set-CsRgsWorkflow $x</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow object. **Set-CsRgsWorkflow**는 응답 그룹 워크플로 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRgsWorkflow**는 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsWorkflow](get-csrgsworkflow.md)  
[New-CsRgsWorkflow](new-csrgsworkflow.md)  
[Remove-CsRgsWorkflow](remove-csrgsworkflow.md)

