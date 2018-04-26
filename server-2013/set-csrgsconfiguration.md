---
title: Set-CsRgsConfiguration
TOCTitle: Set-CsRgsConfiguration
ms:assetid: 259cec4c-0152-4c8f-8aa6-51cefc1b55c9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425728(v=OCS.15)
ms:contentKeyID: 49303085
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

응답 그룹 응용 프로그램에 대한 구성 설정을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsConfiguration -Identity <RgsIdentity> [-AgentRingbackGracePeriod <Int16>] [-DefaultMusicOnHoldFile <AudioFile>] [-DisableCallContext <$true | $false>] <COMMON PARAMETERS>

    Set-CsRgsConfiguration -Instance <ServiceSettings> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 응답 그룹 응용 프로그램 구성 설정에 대한 AgentRingbackGracePeriod 속성을 수정합니다. 이 예제에서 AgentRingbackGracePeriod는 30초로 설정되어 있습니다.

    Set-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -AgentRingbackGracePeriod 30

## 예제 2

예제 2에서는 조직의 모든 응답 그룹 구성 설정에 대한 AgentRingbackGracePeriod를 수정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsService** cmdlet 및 ApplicationServer 매개 변수를 사용하여 응용 프로그램 서비스를 실행 중인 조직 내의 모든 컴퓨터에 대한 정보를 반환합니다. 반환된 컬렉션은 Applications 속성에 "urn:application:RGS" 응용 프로그램이 포함된 컴퓨터만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 이 값은 응답 그룹 응용 프로그램이 서버에서 실행 중임을 나타냅니다.

선택된 컴퓨터는 **ForEach-Object** cmdlet에 파이프됩니다. 그런 다음 **ForEach-Object**는 컬렉션의 각 컴퓨터에 대해 **Set-CsRgsConfiguration**을 사용하여 응답 그룹 구성 설정의 AgentRingbackGracePeriod 값을 30초로 설정합니다.

    Get-CsService -ApplicationServer | Where-Object {$_.Applications -contains "urn:application:RGS"} | ForEach-Object {Set-CsRgsConfiguration -Identity $_.Identity -AgentRingbackGracePeriod 30}

## 예제 3

예제 3에 표시된 명령은 오디오 파일(C:\\Media\\WhileYouWait.wav)을 가져와서 DefaultMusicOnHoldFile 속성에 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Import-CsRgsAudioFile**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 응답 그룹 응용 프로그램으로 오디오 파일을 가져옵니다. 이때 서비스 위치를 지정하는 Identity 매개 변수와 함께 FileName 매개 변수를 사용하여 가져올 파일의 파일 이름을 지정합니다.

오디오 파일을 가져올 때 Content 매개 변수를 사용하는 것도 중요합니다. 가져올 파일의 경로를 뒤에 입력하고 **Get-Content** cmdlet을 호출하여 파일을 가져오면 됩니다. **Get-Content**를 사용할 때는 인코딩 유형을 바이트로 설정하고 ReadCount를 0으로 설정해야 합니다. ReadCount를 0으로 설정하면 한 번의 작업으로 전체 파일을 읽을 수 있습니다. 가져온 파일은 변수 $x에 저장됩니다.

파일을 가져온 후에는 **Set-CsRgsConfiguration**을 호출하여 DefaultMusicOnHoldFile 속성을 $x에 저장된 오디오 파일로 설정합니다.

    $x = Import-CsRgsAudioFile -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -FileName "WhileYouWait.wav" -Content (Get-Content C:\Media\WhileYouWait.wav -Encoding byte -ReadCount 0)
    
    Set-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -DefaultMusicOnHoldFile $x

## 자세한 정보

응답 그룹 응용 프로그램에서는 지원 센터 또는 고객 지원과 같은 엔터티로 전화 통화를 자동으로 경로 지정하는 기능을 제공합니다. 발신자가 지정된 전화 번호로 전화를 걸면 이 전화를 적절한 응답 그룹 에이전트 집합으로 자동으로 경로 지정할 수 있습니다. 또는 IVR(대화형 음성 응답) 큐로 전화를 경로 지정할 수도 있습니다. 이 큐에서는 발신자에게 일련의 질문(예: "기존 주문과 관련하여 전화하셨습니까?")을 제공한 다음, 해당 답변에 따라 요청한 정보를 제공하거나 응답 그룹 에이전트로 통화를 경로 지정합니다.

**Set-CsRgsConfiguration** cmdlet을 사용하면 응답 그룹 응용 프로그램 인스턴스의 속성을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsConfiguration"}

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
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>응답 그룹 구성 설정을 호스트하는 서비스의 이름입니다(예: -Identity &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.ServiceSettings</p></td>
<td><p>수정할 응답 그룹 구성 설정에 대한 개체 참조입니다. 개체 참조는 일반적으로 <strong>Get-CsRgsConfiguration</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 다음 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 구성 설정에 대한 개체 참조를 반환하며 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-CsRgsConfiguration -Identity service:ApplicationServer:atl-cs-001.litwareinc.com</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>AgentRingbackGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int16</p></td>
<td><p>AgentRingbackGracePeriod는 에이전트가 통화를 거절한 경우 동일한 에이전트에게 통화가 다시 시도될 때까지 소요되는 시간(초)을 나타냅니다. 유예 기간은 30초에서 600초(10분)(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 60초입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultMusicOnHoldFile</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.AudioFile</p></td>
<td><p>기본적으로 발신자가 대기 상태에 놓일 때마다 재생되는 음악을 나타냅니다. 기본 음악은 응답 그룹 워크플로에서 고유의 대기 음악을 정의하지 않은 경우에만 재생됩니다.</p>
<p>DefaultMusicOnHoldFile 속성은 <strong>Import-CsRgsAudioFile</strong> cmdlet을 통해 만든 개체 참조를 사용하여 구성해야 합니다.</p>
<p>DefaultMusicOnHold가 Null 값(기본값)과 같고 워크플로에서 사용자 지정 대기 음악을 정의하지 않은 경우에는 발신자가 대기 중일 때마다 Lync Server를 설치할 때 자동으로 구성된 기본 대기 음악이 재생됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableCallContext</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False(기본값)로 설정된 경우 각 에이전트가 전화를 받을 때마다 통화 컨텍스트(발신자 대기 시간이나 워크플로 질문 및 응답 등의 정보)를 확인할 수 있습니다. 이 정보는 Lync 내에 표시됩니다. True로 설정된 경우에는 전화를 받을 때 에이전트에게 통화 컨텍스트 정보가 릴레이되지 않습니다.</p>
<p>이 경우 통화 컨텍스트는 IVR 큐에서만 사용됩니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.ServiceSettings object. **Set-CsRgsConfiguration**은 응답 그룹 응용 프로그램 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRgsConfiguration**은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.ServiceSettings 개체의 기존 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsConfiguration](get-csrgsconfiguration.md)  
[Move-CsRgsConfiguration](move-csrgsconfiguration.md)

