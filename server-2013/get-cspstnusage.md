---
title: Get-CsPstnUsage
TOCTitle: Get-CsPstnUsage
ms:assetid: 9dc82b88-303b-4678-8298-0dbc769f6781
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412734(v=OCS.15)
ms:contentKeyID: 49304537
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPstnUsage

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 PSTN(공중 전화망) 사용 레코드에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPstnUsage [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 명령은 조직 내에서 사용할 수 있는 전역 PSTN 사용 목록을 반환합니다.

    Get-CsPstnUsage

## 예제 2

이 예제의 명령은 정의된 모든 PSTN 사용의 목록을 반환하며 출력의 각 줄에 하나의 사용이 나열됩니다. **Get-CsPstnUsage** cmdlet을 단독으로 호출하면 Identity 및 Usage 목록이 반환됩니다. Usage 목록에 4개 또는 5개 이상의 항목이 포함된 경우 출력된 목록은 다음과 같이 간략한 형태로 나타납니다.

Usage : {Internal, Local, Long Distance, International...}

이 예제의 명령을 사용하여 사용법 목록만 표시합니다. 결과는 다음과 비슷하게 출력됩니다.

Internal

Local

Long Distance

International

Restricted

    (Get-CsPstnUsage).Usage

## 예제 3

이 명령은 문자열 "tern"이 이름 안에 들어 있는 모든 PSTN 사용 이름을 반환합니다. 예를 들어, 이 명령은 "Internal" 및 "International"을 반환하지만 "Local" 또는 "Long Distance"는 반환하지 않습니다.

이 명령의 첫 번째 부분에서 **Get-CsPstnUsage** cmdlet이 괄호 안에 들어 있으므로 모든 PSTN 사용을 검색하는 작업이 가장 먼저 수행됩니다. .Usage 속성은 Identity가 아니라 PSTN 사용에 대한 사용 정보만 반환합니다. 그런 다음, 한 번에 하나씩 사용법 문자열을 확인하는 **ForEach-Object** cmdlet에 사용법 목록이 파이프됩니다. If 문은 현재 사용법 문자열을 문자열 "\*tern\*"과 비교하고(\*는 와일드카드) 해당 패턴과 일치하는 모든 경우를 표시합니다.

    (Get-CsPstnUsage).Usage | ForEach-Object {if ($_ -like "*tern*") {$_}}

## 자세한 정보

PSTN 사용법은 호출 권한 부여에 사용되는 문자열 값입니다. PSTN 사용법은 음성 정책을 경로에 연결합니다. **Get-CsPstnUsage** cmdlet은 조직 내에서 사용할 수 있는 모든 PSTN 사용 목록을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPstnUsage** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPstnUsage"}

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
<td><p>Filter 매개 변수를 사용하면 특정 문자열과 일치하는 ID를 가진 PSTN 사용만 검색할 수 있습니다. 그러나 PSTN 사용에 사용할 수 있는 유일한 ID가 Global이므로 이 매개 변수는 이 cmdlet에 유용하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이러한 설정이 적용되는 수준입니다. PSTN 사용법에 적용할 수 있는 유일한 ID는 Global입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>기본 중앙 관리 저장소가 아니라 로컬 데이터 저장소에서 PSTN 사용 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsPstnUsage** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PSTNUsages 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsPstnUsage](set-cspstnusage.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

