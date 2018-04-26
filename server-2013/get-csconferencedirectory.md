---
title: Get-CsConferenceDirectory
TOCTitle: Get-CsConferenceDirectory
ms:assetid: 2b7927ab-c6b3-42ce-9c27-9825cd47fd77
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425771(v=OCS.15)
ms:contentKeyID: 49303167
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferenceDirectory

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 전화 회의 디렉터리에 대한 정보를 반환합니다. 전화 회의 디렉터리는 전화 접속 회의 사용자가 전화 회의 정보를 찾는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsConferenceDirectory [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDirectory [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 전화 회의 디렉터리에 대한 정보를 반환합니다.

    Get-CsConferenceDirectory

## 예제 2

예제 2에서는 Identity가 2인 전화 회의 디렉터리에 대한 정보를 반환합니다. Identity가 고유해야 하므로 이 명령은 둘 이상의 전화 회의 디렉터리를 반환하지 않습니다.

    Get-CsConferenceDirectory -Identity 2

## 예제 3

예제 3에서는 UserServer:atl-cs-001.litwareinc.com 서비스에 포함된 모든 전화 회의 디렉터리를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsConferenceDirectory** cmdlet을 호출하여 조직에서 찾은 모든 전화 회의 디렉터리 컬렉션을 반환합니다. 이 컬렉션은 ServiceID가 문자열 값 "UserServer:atl-cs-001.litwareinc.com"과 일치하는 디렉터리만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"}

## 자세한 정보

전화 접속 회의 URI(Uniform Resource Identifier)를 만들면 이러한 URI에 고유한 SIP 주소가 할당됩니다. 그러나 SIP 주소는 SIP를 인식하지 않는 장치에서 변환하기 어렵습니다. 예를 들어 PSTN(공중 전화망) 전화는 SIP 주소를 변환할 수 없습니다. 따라서 Lync Server에서는 이러한 장치에서 전화 접속 회의를 찾아 연결하도록 도와줄 수 있는 방법으로 전화 회의 디렉터리를 사용합니다. 이를 위해 각 전화 접속 회의 URI와 연결되어 있고 SIP URI가 아닌 정수 값으로 식별된 SIP 전화 회의 디렉터리를 만듭니다. 이렇게 하면 PSTN 전화와 기타 장치가 전화 회의에 연결할 때 SIP URI 대신 이러한 번호를 사용할 수 있습니다. 실제로 디렉터리 번호는 사용자가 전화 접속 회의에 연결할 때 입력하는 PSTN 전화 회의 ID에 포함됩니다.

**Get-CsConferenceDirectory** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 전화 회의 디렉터리에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsConferenceDirectory** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDirectory"}

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
<td><p>와일드카드를 사용하여 검색할 전화 회의 디렉터리의 ID를 지정할 수 있습니다. 디렉터리 ID가 숫자이기 때문에 이 매개 변수는 최소한의 값으로 구성될 수 있습니다. 그러나 -Filter &quot;3*&quot; 구문은 Identity가 숫자 3으로 시작하는 모든 전화 회의 디렉터리를 반환합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 전화 회의 디렉터리의 숫자 식별자(예: 7)입니다. 이 매개 변수를 생략하면 <strong>Get-CsConferenceDirectory</strong> cmdlet에서 조직에서 사용 중인 모든 전화 회의 디렉터리에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 전화 회의 디렉터리 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsConferenceDirectory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsConferenceDirectory** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

