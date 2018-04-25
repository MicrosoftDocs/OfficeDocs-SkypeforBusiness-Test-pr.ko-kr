---
title: New-CsRgsWorkflow
TOCTitle: New-CsRgsWorkflow
ms:assetid: 1a2ac5b7-cb1d-4a83-801f-f27671e71743
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398246(v=OCS.15)
ms:contentKeyID: 49302961
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsWorkflow

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 워크플로를 만듭니다. 워크플로는 응답 그룹 응용 프로그램이 전화 통화를 수신할 때 수행되는 작업을 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsWorkflow -Name <String> -Parent <RgsIdentity> -PrimaryUri <Uri> [-Active <$true | $false>] [-Anonymous <$true | $false>] [-BusinessHoursID <RgsIdentity>] [-Confirm [<SwitchParameter>]] [-CustomMusicOnHoldFile <AudioFile>] [-DefaultAction <CallAction>] [-Description <String>] [-DisplayNumber <String>] [-EnabledForFederation <$true | $false>] [-Force <SwitchParameter>] [-HolidayAction <CallAction>] [-HolidaySetIDList <Collection>] [-InMemory <SwitchParameter>] [-Language <String>] [-LineUri <Uri>] [-Managed <$true | $false>] [-ManagersByUri <Collection>] [-NonBusinessHoursAction <CallAction>] [-TimeZone <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 새 워크플로를 만듭니다. 이 워크플로에는 Help Desk라는 이름이 지정되고 sip:helpdesk@litwareinc.com이라는 기본 URI가 할당됩니다.

    New-CsRgsWorkflow -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -PrimaryUri "sip:helpdesk@litwareinc.com" 

## 예제 2

예제 2에 표시된 명령은 새 워크플로 프롬프트 및 통화 작업을 만들어 새 응답 그룹 워크플로에 할당합니다. 첫 번째 명령은 **New-CsRgsPrompt** cmdlet을 사용하여 "Welcome to the help desk"라는 텍스트 음성 변환 프롬프트를 만듭니다. 이 새 프롬프트는 $prompt 변수에 저장됩니다.

두 번째 명령은 **Get-CsRgsQueue** cmdlet을 사용하여 Help Desk라는 기존 응답 그룹 큐의 ID를 검색합니다. 반환된 ID는 $queue 변수에 저장됩니다.

세 번째 명령은 새 프롬프트($prompt)와 검색된 큐($queue) 둘 다를 참조하는 새 통화 작업($callAction 변수에 저장됨)을 만듭니다. 끝으로, 이 예제의 마지막 명령은 Help Desk라는 새 워크플로를 만듭니다. 이 명령은 PrimaryUri를 sip:helpdesk@litwareinc.com으로 설정하고 DefaultAction 속성 값을 이전 단계에서 만든 통화 작업으로 설정합니다.

    $prompt = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to the help desk."
    $queue = (Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk").Identity
    $callAction = New-CsRgsCallAction -Prompt $prompt -Action TransferToQueue -QueueId $queue
    New-CsRgsWorkflow -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -PrimaryUri "sip:helpdesk@litwareinc.com" -DefaultAction $callAction

## 자세한 정보

워크플로는 응답 그룹 응용 프로그램의 주요 요소입니다. 각 워크플로는 한 전화 번호에만 고유하게 연결됩니다. 누군가 그 번호로 전화를 걸면 워크플로에 따라 해당 전화의 처리 방법이 결정됩니다. 예를 들어 발신자에게 추가 정보를 입력하라는 일련의 IVR(대화형 음성 응답) 질문("하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 전화를 경로 지정할 수 있습니다. 또는 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치되고 발신자가 통화 대기 상태에 놓일 수 있습니다. 에이전트가 통화에 응답할 수 있는지 여부도 워크플로를 통해 지정할 수 있습니다. 워크플로는 업무 시간(에이전트가 전화를 받을 수 있는 요일과 시간)과 휴일(에이전트가 전화를 받을 수 없는 요일)을 구성하기 위해 사용됩니다.

새 워크플로는 **New-CsRgsWorkflow** cmdlet을 사용하여 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRgsWorkflow** cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsWorkflow"}

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
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>워크플로에 할당할 고유 이름입니다. Parent 속성과 Name 속성을 조합하면 워크플로 GUID(Globally Unique Identifier)를 참조하지 않고도 워크플로를 고유하게 식별할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>새 워크플로를 호스트할 서비스입니다 (예: -Parent &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>PrimaryUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.Uri</p></td>
<td><p>워크플로의 SIP 주소입니다(예: -PrimaryUri &quot;sip:helpdesk@litwareinc.com&quot;). PrimaryUri는 &quot;sip:&quot; 접두사로 시작해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Active</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 워크플로가 활성 상태이고 전화 통화에 워크플로를 사용할 수 있음을 의미합니다. False(기본값)로 설정된 경우에는 전화 통화에 워크플로를 사용할 수 없습니다.</p>
<p>Active 속성을 True로 설정하면 워크플로를 만들기 전에 유효성 검사가 실행됩니다. 예를 들어 DefaultAction이 지정되어 있지 않은 경우 워크플로가 만들어지지 않습니다. 반면, Active를 False로 설정하거나 구성하지 않으면 유효성 검사가 실행되지 않으며 DefaultAction이 지정되어 있지 않은 경우에도 워크플로가 만들어집니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Anonymous</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 개별 응답 그룹 에이전트가 통화에 응답할 때마다 해당 에이전트의 ID가 마스킹되고, False(기본값)로 설정된 경우 발신자가 에이전트 ID를 확인할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BusinessHoursID</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>워크플로 에이전트가 통화에 응답할 수 있는 요일 및 시간입니다. 업무 시간 ID는 <strong>Get-CsRgsHoursOfBusiness</strong> cmdlet을 사용하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomMusicOnHoldFile</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.AudioFile</p></td>
<td><p>발신자가 통화 대기 중일 때 재생할 사용자 지정 음악을 나타냅니다. 이 매개 변수를 정의하지 않으면 발신자가 통화 대기 중일 때 기본 음악이 재생됩니다. 사용자 지정 음악은 <strong>Import-CsRgsAudioFile</strong> cmdlet을 사용하여 가져와야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>업무 시간 중에 워크플로가 열린 경우 수행할 작업을 나타냅니다. DefaultAction은 <strong>New-CsRgsCallAction</strong> cmdlet을 사용하여 정의해야 하며, 통화를 큐 또는 질문으로 전달해야 합니다. 워크플로가 활성화된 경우에는 DefaultAction 매개 변수가 필수지만 비활성화된 경우에는 생략할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 응답 그룹 워크플로에 대한 추가 정보를 추가하는 데 사용됩니다. 예를 들어 Description은 워크플로 소유자의 연락처 정보를 포함할 수 있습니다. 이 설명은 워크플로의 Lync 대화 상대 카드에 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync 표시되는 워크플로의 전화 번호입니다. DisplayNumber 형식은 원하는 대로 설정할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-DisplayNumber &quot;555-1219&quot;</p>
<p>-DisplayNumber &quot;1-(425)-555-1219&quot;</p>
<p>-DisplayNumber &quot;1.425.555.1219&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>EnabledForFederation</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>페더레이션 도메인의 사용자가 워크플로를 사용할 수 있는지 여부를 나타냅니다. False로 설정된 경우 조직 내부의 사용자만 워크플로에 액세스할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HolidayAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>휴일에 전화를 받은 경우에 수행할 작업입니다. HolidayAction은 <strong>New-CsRgsCallAction</strong> cmdlet을 사용하여 정의해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HolidaySetIDList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.ObjectModel.Collection</p></td>
<td><p>워크플로 에이전트가 통화에 응답할 수 없는 날짜를 나타냅니다. 휴일 집합 ID는 <strong>Get-CsRgsHolidaySet</strong> cmdlet을 사용하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Language</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>워크플로 텍스트 음성 변환 프롬프트를 읽는 데 사용되는 언어입니다. 운영 체제에서 아래 목록에 표시된 지원되는 언어 중 하나를 사용하는 경우 언어 매개 변수는 선택 사항입니다. 지원되는 음성 언어는 운영 체제에서 사용할 수 있는 언어의 하위 집합을 나타냅니다.</p>
<p>운영 체제에서 지원되는 언어를 사용하지 않는 경우 Language는 필수 매개 변수가 되며 지원되는 언어에 대한 언어 코드를 지정해야 합니다. 이 경우 Language 매개 변수를 포함하지 않고 <strong>New-CsRgsWorkflow</strong> cmdlet을 실행하면 명령이 실패합니다.</p>
<p>예를 들어 운영 체제가 페로어로 실행되는 경우를 가정해 보겠습니다. 이 언어는 Windows 운영 체제에서 지원되지만 응답 그룹 응용 프로그램에서는 지원되지 않습니다. 따라서 새 워크플로를 만들 때 Language 매개 변수와 지원되는 언어를 포함해야 합니다.</p>
<p>언어를 지정하지 않으면 워크플로에서 운영 체제 언어를 사용하기 때문에 이는 필수 조건입니다. 페로어는 응답 그룹 응용 프로그램에서 지원하는 경우에만 워크플로에 사용할 수 있습니다.</p>
<p>다음 언어 코드 중 하나를 사용하여 언어를 지정해야 합니다.</p>
<p>ca-ES – 카탈로니아어(스페인)</p>
<p>da-DK – 덴마크어(덴마크)</p>
<p>de-DE – 독일어(독일)</p>
<p>en-AU – 영어(오스트레일리아)</p>
<p>en-CA – 영어(캐나다)</p>
<p>en-GB – 영어(영국)</p>
<p>en-IN – 영어(인도)</p>
<p>en-US – 영어(미국)</p>
<p>es-ES – 스페인어(스페인)</p>
<p>es-MX – 스페인어(멕시코)</p>
<p>fi-FI – 핀란드어(핀란드)</p>
<p>fr-CA – 프랑스어(캐나다)</p>
<p>fr-FR – 프랑스어(프랑스)</p>
<p>it-IT – 이탈리아어(이탈리아)</p>
<p>ja-JP – 일본어(일본)</p>
<p>ko-KR – 한국어(대한민국)</p>
<p>nb-NO – 노르웨이어, 복말(노르웨이)</p>
<p>nl-NL – 네덜란드어(네덜란드)</p>
<p>pl-PL – 폴란드어(폴란드)</p>
<p>pt-BR – 포르투갈어(브라질)</p>
<p>pt-PT – 포르투갈어(포르투갈)</p>
<p>ru-RU – 러시아어(러시아)</p>
<p>sv-SE – 스웨덴어(스웨덴)</p>
<p>zh-CN - 중국어(중국)</p>
<p>zh-HK – 중국어(홍콩 특별 행정구)</p>
<p>zh-TW – 중국어(대만)</p>
<p>예: -Language &quot;nl-NL&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>LineUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Uri</p></td>
<td><p>워크플로의 전화 번호입니다. URI(Uniform Resource Identifier) 행은 TEL: 접두사, 더하기 기호, 국가 번호, 지역 번호, 전화 번호(공백, 마침표, 하이픈 등 없이 숫자만 사용)를 순서대로 나열하는 형식으로 지정해야 합니다(예: -LineUri &quot;TEL:+14255551219&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Managed</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하는 경우 한 명 이상의 사용자가 워크플로를 관리함을 나타냅니다. ManagedByUri 매개 변수를 사용하여 해당 사용자를 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ManagersByUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.ObjectModel.Collection</p></td>
<td><p>워크플로를 관리할 사용자의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-ManagedByUri &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>관리자를 여러 명 지정하려면 관리자 SIP 주소를 쉼표로 구분합니다.</p>
<p>-ManagedByUri &quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>NonBusinessHoursAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>워크플로 업무 시간 이외에 전화를 받은 경우에 수행할 작업입니다. NonBusinessHoursAction은 <strong>New-CsRgsCallAction</strong> cmdlet을 사용하여 정의해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TimeZone</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>휴일 및 업무 시간을 결정할 때 사용되는 표준 시간대 정보입니다(예: -TimeZone &quot;태평양 표준시&quot;).</p></td>
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

없음. **New-CsRgsWorkflow** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsWorkflow** cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.Workflow 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsWorkflow](get-csrgsworkflow.md)  
[Remove-CsRgsWorkflow](remove-csrgsworkflow.md)  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)

