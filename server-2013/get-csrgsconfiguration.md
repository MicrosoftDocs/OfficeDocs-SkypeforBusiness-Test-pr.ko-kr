---
title: Get-CsRgsConfiguration
TOCTitle: Get-CsRgsConfiguration
ms:assetid: a3667917-cfbf-47c1-8b48-e936594b5357
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412762(v=OCS.15)
ms:contentKeyID: 49304591
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

응답 그룹 응용 프로그램의 구성 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsConfiguration -Identity <RgsIdentity>

## 예제

## 예제 1

예제 1에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 대한 응답 그룹 구성 설정을 반환합니다. 서비스당 하나의 설정 컬렉션만 있을 수 있기 때문에 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"

## 예제 2

예제 2에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 응답 그룹 구성 설정에 대한 단일 속성(DisableCallContext) 값을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsConfiguration**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 응답 그룹 구성 설정에 대한 모든 속성 값을 검색합니다. 이 명령은 괄호로 묶여 있는데, 이는 작업을 수행하기 전에 Windows PowerShell에서 모든 속성 값을 반환하도록 하기 위한 것입니다.

모든 속성 값을 반환된 후에는 표준 "점 표기법"을 사용하여 DisableCallContext 속성 값만 표시합니다. 표준 점 표기법은 개체, 마침표(점), 표시할 속성 이름을 차례로 나열하여 구성합니다. 예를 들어 AgentRingbackGracePeriod 속성 값만 표시하려면 다음 명령을 사용하면 됩니다.

(Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com").AgentRingbackGracePeriod

    (Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com").DisableCallContext

## 예제 3

예제 3에 표시된 명령은 응용 프로그램 서비스를 실행하고 응답 그룹 응용 프로그램의 인스턴스를 호스트하는 모든 컴퓨터에서 응답 그룹 구성 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsService** cmdlet 및 ApplicationServer 매개 변수를 사용하여 응용 프로그램 서비스를 실행 중인 조직 내의 모든 서버에 대한 정보를 반환합니다. 이 컬렉션은 Applications 속성에 "urn:application:RGS" 응용 프로그램이 포함된 서버만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 이 값은 응답 그룹 응용 프로그램이 서버에서 실행 중임을 나타냅니다.

선택된 서버는 **ForEach-Object** cmdlet에 파이프됩니다. 그런 다음 **ForEach-Object**는 컬렉션의 각 서버에 대해 **Get-CsRgsConfiguration**을 사용하여 응답 그룹 구성 정보를 반환합니다.

    Get-CsService -ApplicationServer | Where-Object {$_.Applications -contains "urn:application:RGS"} | ForEach-Object {Get-CsRgsConfiguration -Identity $_.Identity}

## 자세한 정보

응답 그룹 응용 프로그램에서는 지원 센터 또는 고객 지원과 같은 엔터티로 전화 통화를 자동으로 경로 지정하는 기능을 제공합니다. 발신자가 지정된 전화 번호로 전화를 걸면 이 전화를 적절한 응답 그룹 에이전트 집합으로 바로 경로 지정할 수 있습니다. 또는 먼저 IVR(대화형 음성 응답) 큐로 전화를 경로 지정할 수도 있습니다. 이 큐에서는 발신자에게 일련의 질문(예: "기존 주문과 관련하여 전화하셨습니까?")을 제공한 다음, 해당 답변에 따라 적절한 응답 그룹 큐로 경로 지정합니다.

**Get-CsRgsConfiguration** cmdlet을 사용하면 응답 그룹 응용 프로그램이 구성된 방식에 대한 정보를 가져올 수 있습니다. 기본적으로 이 cmdlet은 한 번에 하나의 응답 그룹 응용 프로그램 인스턴스에서만 정보를 반환합니다. 예를 들어 ApplicationServer:atl-cs-001.litwareinc.com과 ApplicationServer:dublin-cs-001.litwareinc.com에 하나씩 별도의 응답 그룹 응용 프로그램을 설치한 경우 각 응답 그룹 인스턴스에 대한 정보를 가져오려면 **Get-CsRgsConfiguration**을 별도로 호출해야 합니다. 이 항목의 예제 섹션에서는 이러한 문제를 해결하는 방법을 보여 줍니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsRgsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsConfiguration"}

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
<td><p>응답 그룹 구성 설정을 호스트하는 서비스의 이름입니다(예: -Identity &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;). 이 매개 변수를 포함하지 않으면 <strong>Get-CsRgsConfiguration</strong>에서 ID를 제공하라는 메시지를 표시합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsRgsConfiguration**은 응답 그룹 구성 설정의 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

**Get-CsRgsConfiguration**은 Microsoft.Rtc.Rgs.Management.WritableSettings.ServiceSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Move-CsRgsConfiguration](move-csrgsconfiguration.md)  
[Set-CsRgsConfiguration](set-csrgsconfiguration.md)

