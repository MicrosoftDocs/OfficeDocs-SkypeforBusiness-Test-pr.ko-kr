---
title: Get-CsRgsWorkflow
TOCTitle: Get-CsRgsWorkflow
ms:assetid: 2ae2e10b-65ac-40f9-96a2-5adb01e8a69d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425766(v=OCS.15)
ms:contentKeyID: 49303139
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsWorkflow

 

_**마지막으로 수정된 항목:** 2015-03-09_

응답 그룹 워크플로에 대한 정보를 반환합니다. 워크플로는 응답 그룹 응용 프로그램이 전화 통화를 수신할 때 수행되는 작업을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsWorkflow [-Identity <RgsIdentity>] [-Name <String>] [-Owner <RgsIdentity>] [-ShowAll <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 워크플로에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsRgsWorkflow**를 호출합니다.

    Get-CsRgsWorkflow

## 예제 2

예제 2에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 응답 그룹 응용 프로그램 워크플로에 대한 정보를 반환합니다.

    Get-CsRgsWorkflow -Identity service:ApplicationServer:atl-cs-001.litwareinc.com

## 예제 3

예제 3의 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 각 응답 그룹 워크플로의 DefaultAction 속성에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 워크플로에 대한 정보를 반환합니다. 이 정보는 DefaultAction 속성에 저장된 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. DefaultAction 값을 확장하면 DefaultAction 속성에 저장되어 있는 포함된 개체의 개별 속성이 표시됩니다.

    Get-CsRgsWorkflow -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Select-Object -ExpandProperty DefaultAction

## 예제 4

예제 4에서는 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 European Sales Supports라는 단일 응답 그룹 워크플로에 대한 정보를 반환합니다.

    Get-CsRgsWorkflow -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "European Sales Support"

## 예제 5

예제 5에 표시된 명령은 영어(미국)를 기본 언어로 사용하는 모든 응답 그룹 워크플로에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsWorkflow**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 워크플로의 컬렉션을 반환합니다. 이 컬렉션은 Language 속성이 영어(미국)(en-US)와 같은 워크플로만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsWorkflow -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.Language -eq "en-Us"}

## 예제 6

예제 6에서는 ApplicationServer:atl-cs-001.litwareinc.com에서 CustomMusicOnHoldFile 속성이 Null 값으로 설정된 모든 워크플로를 반환합니다. 즉, 이 명령은 사용자 지정 음악이 할당되지 않은 워크플로에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsWorkflow**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 워크플로의 컬렉션을 반환합니다. 반환된 데이터는 CustomMusicOnHoldFile 속성이 Null 값과 같은 항목만 선택하는 **Where-Object**에 파이프됩니다.

    Get-CsRgsWorkflow service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.CustomMusicOnHoldFile -eq $Null}

## 자세한 정보

워크플로는 응답 그룹 응용 프로그램의 주요 요소입니다. 각 워크플로는 한 전화 번호에만 고유하게 연결됩니다. 누군가 그 번호로 전화를 걸면 워크플로에 따라 해당 전화의 처리 방법이 결정됩니다. 예를 들어 발신자에게 추가 정보를 입력하라는 일련의 IVR(대화형 음성 응답) 질문("하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 전화를 경로 지정할 수 있습니다. 또는 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치되고 발신자가 통화 대기 상태에 놓일 수 있습니다. 에이전트가 전화를 받을 수 있는 상태인지도 워크플로에서 지정합니다. 워크플로는 업무 시간(에이전트가 전화를 받을 수 있는 요일과 시간)과 휴일(에이전트가 전화를 받을 수 없는 요일)을 구성하는 데 사용됩니다.

**Get-CsRgsWorkflow** cmdlet을 사용하면 조직에서 사용하도록 구성된 워크플로에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsRgsWorkflow** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsWorkflow"}

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
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>응답 그룹 워크플로가 호스트되는 서비스의 ID 또는 워크플로 자체의 전체 ID를 나타냅니다. 서비스 ID(예: service: ApplicationServer:atl-cs-001.litwareinc.com)를 지정하면 해당 서비스에서 호스트되는 모든 응답 그룹 워크플로가 반환되고, 워크플로 ID를 지정하면 해당 응답 그룹 워크플로 하나만 반환됩니다. 워크플로 ID는 서비스 ID와 GUID(Globally Unique Identifier)로 구성됩니다(예: service:ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83).</p>
<p>서비스 ID를 지정한 다음 Name 매개 변수와 워크플로 이름을 포함하여 단일 응답 그룹 워크플로를 반환할 수도 있습니다. 이렇게 하면 특정 워크플로에 할당된 GUID를 몰라도 해당 워크플로를 검색할 수 있습니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsRgsWorkflow</strong>는 조직에서 사용하도록 구성된 모든 워크플로의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응답 그룹 워크플로를 만들 당시 해당 워크플로에 지정된 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>워크플로를 &quot;소유&quot;하는 풀의 정규화된 도메인 이름입니다. 워크플로의 풀 ID와 소유자 풀 ID는 보통 같습니다. 그러나 재해 복구 절차에서와 같이 워크플로를 일시적으로 이동해야 하는 경우에는 풀 ID가 변경됩니다. 이 경우에도 소유자 ID는 계속 원래 풀을 가리킵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 소유자 풀 ID와 풀 ID가 다른 워크플로를 비롯하여 모든 리소스 그룹 워크플로를 표시합니다. 기본적으로 Get-CsRgsWorkflow는 소유자 및 상위 풀이 동일한 워크플로에 대한 정보만 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsRgsWorkflow**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsRgsWorkflow**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsWorkflow](new-csrgsworkflow.md)  
[Remove-CsRgsWorkflow](remove-csrgsworkflow.md)  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)

