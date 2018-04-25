---
title: Set-CsCallParkOrbit
TOCTitle: Set-CsCallParkOrbit
ms:assetid: 9a159a9a-69a6-4e4d-8224-49aa42092ea8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398796(v=OCS.15)
ms:contentKeyID: 49304493
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCallParkOrbit

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직 내의 기존 통화 대기 파킹된 통화 번호 범위에 대한 속성을 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCallParkOrbit [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsCallParkOrbit [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CallParkService <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] [-Type <CallPark | GroupPickup>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 "Redmond CPO 1"이라는 통화 대기 파킹된 통화 번호의 번호 범위를 500-699로 변경합니다. 이 범위 내의 모든 값은 조직 내의 모든 통화 대기 파킹된 통화 번호 범위에서 고유해야 합니다.

    Set-CsCallParkOrbit -Identity "Redmond CPO 1" -NumberRangeStart 500 -NumberRangeEnd 699

## 예제 2

이 예제에서는 "Redmond CPO 2"라는 통화 대기 파킹된 통화 번호의 번호 범위를 \*7000-\*7100으로 변경합니다. 이 범위 내의 모든 값은 조직 내의 모든 통화 대기 파킹된 통화 번호 범위에서 고유해야 합니다. 앞의 예제와 달리 NumberRangeStart 및 NumberRangeEnd에 할당되는 값을 큰따옴표로 묶었습니다. 이러한 값이 \* 또는 \#(숫자가 아닌 값만 허용됨)으로 시작할 경우 값을 큰따옴표로 묶어야 합니다.

    Set-CsCallParkOrbit -Identity "Redmond CPO 2" -NumberRangeStart "*7000" -NumberRangeEnd "*7100"

## 자세한 정보

통화를 대기하면 수신된 전화 통화가 나중에 검색하기 위해 특정 범위 내의 번호에 할당됩니다. 통화 대기 파킹된 통화 번호는 이 목적을 위해 정의된 번호 집합입니다. **Set-CsCallParkOrbit** cmdlet을 사용하면 통화 대기 서비스의 ID 및 번호 범위를 변경할 수 있습니다. 번호의 새 범위는 조직 내에 정의된 모든 통화 대기 파킹된 통화 번호에서 고유해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsCallParkOrbit** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCallParkOrbit"}

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
<td><p><em>CallParkService</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>통화 대기 응용 프로그램을 호스트하는 응용 프로그램 서비스의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다. NumberRangeStart 및 NumberRangeEnd 매개 변수에 의해 지정된 범위 내의 숫자에 대기된 모든 통화는 이 서버나 풀에 경로 지정됩니다.</p>
<p></p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 통화 대기 파킹된 통화 번호 범위의 고유 식별자입니다. ID에 공백이 포함된 경우 이 값을 큰따옴표로 묶어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>DisplayCallParkOrbit</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 이 개체는 <strong>Get-CsCallParkOrbit</strong>을 호출하여 검색할 수 있는 DisplayCallParkOrbit 유형이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 통화 대기 파킹된 통화 번호에 대한 범위의 마지막 숫자입니다. 값은 NumberRangeStart보다 크거나 같아야 합니다. 또한 값은 NumberRangeStart의 값과 동일한 길이어야 합니다. 예를 들어 NumberRangeStart가 100으로 설정된 경우 NumberRangeEnd는 1001로 설정될 수 없습니다. 또한 NumberRangeStart가 * 또는 #으로 시작하면 NumberRangeEnd도 같은 문자로 시작해야 합니다.</p>
<p>유효한 값: 정규식 문자열([\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8})과 일치해야 합니다. 이는 값이 * 또는 # 문자로 시작하거나 숫자 1-9로 시작하는 문자열이어야 한다는 것을 의미합니다(첫 문자는 0일 수 없음). 첫 문자가 * 또는 #인 경우 다음 문자는 숫자 1-9여야 합니다(0일 수 없음). 이후 문자는 숫자 0-9가 최대 7자까지 올 수 있습니다(예: &quot;#6000&quot;, &quot;*92000&quot; 및 &quot;*95551212&quot;). 첫 문자가 * 또는 #이 아닌 경우 첫 문자는 숫자 1-9여야 하고(0일 수 없음) 그 뒤에는 숫자 0-9가 최대 8자까지 올 수 있습니다(예: 915551212;41212;300).</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 통화 대기 파킹된 통화 번호에 대한 범위의 첫 번째 숫자입니다. 값은 NumberRangeEnd보다 작거나 같아야 합니다. 또한 값은 NumberRangeEnd의 값과 동일한 길이어야 합니다.</p>
<p>유효한 값: 정규식 문자열([\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8})과 일치해야 합니다. 이는 값이 * 또는 # 문자로 시작하거나 숫자 1-9로 시작하는 문자열이어야 한다는 것을 의미합니다(첫 문자는 0일 수 없음). 첫 문자가 * 또는 #인 경우 다음 문자는 숫자 1-9여야 합니다(0일 수 없음). 이후 문자는 숫자 0-9가 최대 7자까지 올 수 있습니다(예: &quot;#6000&quot;, &quot;*92000&quot; 및 &quot;*95551212&quot;). * 또는 # 뒤에 오는 숫자는 100보다 커야 합니다. 첫 문자가 * 또는 #이 아닌 경우 첫 문자는 숫자 1-9여야 하고(0일 수 없음) 그 뒤에는 숫자 0-9가 최대 8자까지 올 수 있습니다(예: 915551212;41212;300).</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Core.OrbitType</p></td>
<td><p>통화 대기 파킹된 통화 번호의 유형을 지정합니다. Lync Server 2013에서는 다음의 두 가지 통화 대기 파킹된 통화 번호 유형을 사용할 수 있습니다.</p>
<p>CallPark. 표준 통화 대기 파킹된 통화 번호이며, 사용자가 통화를 대기시킨 다음 지정된 통화 대기 번호로 전화를 걸어 어떤 전화에서나 해당 통화를 재개할 수 있습니다. CallPark는 Type 매개 변수를 지정하지 않으면 사용되는 기본 파킹된 통화 번호 유형입니다.</p>
<p>GroupPickup. 그룹 통화를 사용하는 경우 통화 수신 그룹의 구성원에게 걸려온 수신 전화를 받을 수 있습니다. 통화 수신 그룹은 관리자가 구성합니다.</p>
<p>통화 대기 파킹된 통화 번호 유형을 지정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Type GroupPickup</p>
<p>이 매개 변수는 Lync Server 2013의 2013년 2월 릴리스에서 도입되었습니다.</p></td>
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

Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit 개체입니다. 통화 대기 파킹된 통화 번호 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

