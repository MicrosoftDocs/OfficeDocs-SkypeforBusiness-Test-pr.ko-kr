---
title: Get-CsServerApplication
TOCTitle: Get-CsServerApplication
ms:assetid: 46769cc2-9e61-4437-b74a-24f3cf118f39
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425948(v=OCS.15)
ms:contentKeyID: 49303498
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsServerApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 서버 응용 프로그램에 대한 정보를 반환합니다. 서버 응용 프로그램은 Lync Server에서 호스트되는 응용 프로그램입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsServerApplication [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsServerApplication [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 실행 중인 모든 서버 응용 프로그램에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsServerApplication** cmdlet을 매개 변수 없이 호출합니다.

    Get-CsServerApplication

## 예제 2

예제 2에서는 EdgeServer:atl-edge-001.litwareinc.com 서비스에서 실행 중인 모든 서버 응용 프로그램을 반환합니다.

    Get-CsServerApplication -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

## 예제 3

예제 3에서는 Identity가 Registrar:atl-cs-001.litwareinc.com/ExumRouting인 단일 서버 응용 프로그램에 대한 정보를 반환합니다.

    Get-CsServerApplication -Identity "service:Registrar:atl-cs-001.litwareinc.com/ExumRouting"

## 예제 4

예제 4에서는 atl-cs-001.litwareinc.com 풀에서 사용하도록 구성된 모든 서버 응용 프로그램을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 "service:\*:atl-cs-001.litwareinc.com\*"를 사용합니다. 이 필터 값은 반환되는 데이터를 ID가 "service:" 문자로 시작하고 ":atl-cs-001.litwareinc.com" 문자를 포함하는 응용 프로그램으로 제한합니다.

    Get-CsServerApplication -Filter "service:*:atl-cs-001.litwareinc.com*"

## 예제 5

예제 5에서는 현재 사용할 수 없는 모든 서버 응용 프로그램에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsServerApplication** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 서버 응용 프로그램의 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 응용 프로그램만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsServerApplication | Where-Object {$_.Enabled -eq $False}

## 예제 6

예제 6은 예제 5에 표시된 명령의 변형입니다. 예제 6에서는 중요로 표시되고 현재 비활성화된 모든 서버 응용 프로그램에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsServerApplication** cmdlet을 매개 변수 없이 호출하여 사용하도록 구성된 모든 서버 응용 프로그램의 컬렉션을 반환합니다. 이 컬렉션은 Critical 속성이 True와 같고 Enabled 속성이 False와 같은 응용 프로그램만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 두 조건을 모두 충족하는 개체만 반환하도록 -and 연산자를 사용합니다.

    Get-CsServerApplication | Where-Object {$_.Critical -eq $True -and $_.Enabled -eq $False}

## 예제 7

예제 7에서는 해당 Uri에 문자열 값 "routing"이 포함되어 있는 모든 서버 응용 프로그램에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsServerApplication** cmdlet을 사용하여 현재 사용 중인 모든 서버 응용 프로그램을 검색합니다. 결과 컬렉션은 Uri 속성에 문자열 값 "routing"이 포함된 응용 프로그램만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsServerApplication | Where-Object {$_.Uri -like "*routing*"}

## 예제 8

예제 8에서는 스크립트가 할당된 모든 서버 응용 프로그램에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsServerApplication** cmdlet을 매개 변수 없이 호출하여 현재 사용 중인 모든 서버 응용 프로그램의 컬렉션을 검색합니다. 그런 다음 전체 서버 응용 프로그램 컬렉션은 ScriptName 속성이 null 값과 다른 응용 프로그램만 선택하는 **Where-Object** cmdlet에 파이프됩니다. ScriptName 속성이 null 값과 다르다는 것은 해당 응용 프로그램에 스크립트가 할당되었다는 의미입니다.

    Get-CsServerApplication | Where-Object {$_.ScriptName -ne $Null}

## 자세한 정보

서버 응용 프로그램은 Lync Server에서 실행되는 개별 프로그램입니다. **Get-CsServerApplication** cmdlet을 통해 관리자는 Lync Server의 일부로 실행 중인 모든 응용 프로그램에 대한 설정을 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsServerApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsServerApplication"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서버 응용 프로그램 또는 서버 응용 프로그램의 집합을 반환할 때 와일드카드를 활용하는 데 사용됩니다. 예를 들어 ID에 문자열 값 &quot;IIMFilter&quot;가 포함된 모든 서버 응용 프로그램을 반환하도록 하려면 -Filter &quot;*IIMFilter*&quot;를 지정하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 서버 응용 프로그램의 고유한 식별자입니다. 서버 응용 프로그램 ID는 응용 프로그램이 호스트되는 서비스와 응용 프로그램 이름으로 구성됩니다. 예를 들어 QoEAgent라는 서버 응용 프로그램의 ID는 service: Registrar:atl-cs-001.litwareinc.com/QoEAgent와 유사할 수 있습니다.</p>
<p>지정한 서비스에서 실행 중인 모든 응용 프로그램의 컬렉션을 검색하려면 다음과 같이 응용 프로그램 이름을 비워 두면 됩니다.</p>
<p>-Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;</p>
<p>이 매개 변수를 생략하면 <strong>Get-CsServerApplication</strong> cmdlet을 호출할 때 모든 서버 응용 프로그램이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 서버 응용 프로그램 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsServerApplication** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsServerApplication** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ServerApplication.Application 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsServerApplication](new-csserverapplication.md)  
[Remove-CsServerApplication](remove-csserverapplication.md)  
[Set-CsServerApplication](set-csserverapplication.md)

