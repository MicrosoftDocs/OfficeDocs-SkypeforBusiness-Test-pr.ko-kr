---
title: New-CsCallParkOrbit
TOCTitle: New-CsCallParkOrbit
ms:assetid: d65a000f-905d-4512-b082-066748719f4c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398936(v=OCS.15)
ms:contentKeyID: 49305175
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsCallParkOrbit

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직 내에서 통화 대기를 위해 할당되는 명명된 번호 범위를 새로 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> -CallParkService <String> -NumberRangeEnd <String> -NumberRangeStart <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Type <CallPark | GroupPickup>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 서비스 ID가 ApplicationServer:pool0.litwareinc.com인 응용 프로그램 서버에서 "Redmond CPO 1"이라는 새 통화 대기 파킹된 통화 번호를 만듭니다. 이 통화 대기 파킹된 통화 번호에 사용할 수 있는 번호 범위는 100-199입니다.

    New-CsCallParkOrbit -Identity "Redmond CPO 1" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService ApplicationServer:pool0.litwareinc.com

## 예제 2

이 예제에서는 FQDN이 pool0.litwareinc.com인 통화 대기 응용 프로그램 서버에서 "Redmond CPO 2"라는 새 통화 대기 파킹된 통화 번호를 만듭니다. 이 통화 대기 파킹된 통화 번호에 사용할 수 있는 범위는 \*1000-\*1999입니다.

    New-CsCallParkOrbit -Identity "Redmond CPO 2" -NumberRangeStart "*1000" -NumberRangeEnd "*1999" -CallParkService pool0.litwareinc.com

## 예제 3

이 예제에서는 서비스 ID가 ApplicationServer:redmond.litwareinc.com인 통화 대기 응용 프로그램 서버에서 "Redmond CPO 3"이라는 새 통화 대기 파킹된 통화 번호 범위를 만듭니다. 이 통화 대기 파킹된 통화 번호에 사용할 수 있는 범위는 \#1000-\#1999입니다.

    New-CsCallParkOrbit -Identity "Redmond CPO 3" -NumberRangeStart "#1000" -NumberRangeEnd "#1999"  -CallParkService ApplicationServer:redmond.litwareinc.com

## 자세한 정보

통화를 대기하면 수신된 전화 통화가 나중에 검색하기 위해 특정 번호에 할당됩니다. 통화 대기 파킹된 통화 번호 범위는 이러한 목적으로 특정 통화 대기 서버에 할당된 통화 대기 위치 집합입니다. **New-CsCallParkOrbit** cmdlet은 통화 대기 파킹된 통화 번호 범위에 대한 번호를 정의하고 특정 서비스에 적용합니다. 지정된 범위 내의 대기된 통화는 지정된 통화 대기 서비스에서 대기됩니다. 여러 통화 대기 파킹된 통화 번호를 만들 수 있지만 각 통화 대기 파킹된 통화 번호에는 전역적으로 고유한 이름과 고유한 번호 범위가 있어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsCallParkOrbit** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCallParkOrbit"}

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
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>통화 대기 응용 프로그램을 호스트하는 응용 프로그램 서비스의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다. NumberRangeStart 및 NumberRangeEnd 매개 변수에 의해 지정된 범위 내의 숫자에 대기된 모든 통화는 이 서버나 풀에 경로 지정됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>통화 대기 파킹된 통화 번호 범위의 이름입니다. 이 이름은 Lync Server 배포 내에서 고유해야 합니다. 이 문자열은 임의의 값일 수 있지만 특정 통화 대기 파킹된 통화 번호 범위를 쉽게 식별할 수 있어야 합니다. 모든 통화 대기 파킹된 통화 번호 범위는 전역 범위를 사용하여 만듭니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 통화 대기 파킹된 통화 번호에 대한 범위의 마지막 숫자입니다. 값은 NumberRangeStart보다 크거나 같아야 합니다. 또한 값은 NumberRangeStart의 값과 동일한 길이어야 합니다. 예를 들어 NumberRangeStart가 100으로 설정된 경우 NumberRangeEnd는 1001로 설정될 수 없습니다. 또한 NumberRangeStart가 * 또는 #으로 시작하면 NumberRangeEnd도 같은 문자로 시작해야 합니다.</p>
<p>유효한 값: 정규식 문자열([\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8})과 일치해야 합니다. 이는 값이 * 또는 # 문자로 시작하거나 숫자 1-9로 시작하는 문자열이어야 한다는 것을 의미합니다(첫 문자는 0일 수 없음). 첫 문자가 * 또는 #인 경우 다음 문자는 숫자 1-9여야 합니다(0일 수 없음). 이후 문자는 숫자 0-9가 최대 7자까지 올 수 있습니다(예: #6000, *92000 및 *95551212). 첫 문자가 * 또는 #이 아닌 경우 첫 문자는 숫자 1-9여야 하고(0일 수 없음) 그 뒤에는 숫자 0-9가 최대 8자까지 올 수 있습니다(예: 915551212;41212;300)</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 통화 대기 파킹된 통화 번호에 대한 범위의 첫 번째 숫자입니다. 값은 NumberRangeEnd보다 작거나 같아야 합니다. 또한 값은 NumberRangeEnd의 값과 동일한 길이어야 합니다.</p>
<p>유효한 값: 정규식 문자열([\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8})과 일치해야 합니다. 이는 값이 * 또는 # 문자로 시작하거나 숫자 1-9로 시작하는 문자열이어야 한다는 것을 의미합니다(첫 문자는 0일 수 없음). 첫 문자가 * 또는 #인 경우 다음 문자는 숫자 1-9여야 합니다(0일 수 없음). 이후 문자는 숫자 0-9가 최대 7자까지 올 수 있습니다(예: #6000, *92000 및 *95551212). * 또는 # 뒤에 오는 번호는 100보다 커야 합니다. 또한 첫 문자가 * 또는 #이 아닌 경우 첫 문자는 숫자 1-9여야 하고(0일 수 없음) 그 뒤에는 숫자 0-9가 최대 8자까지 올 수 있습니다(예: 915551212;41212;300).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Core.OrbitType</p></td>
<td><p>작성 중인 통화 대기 파킹된 통화 번호의 유형을 지정합니다. Lync Server 2013에서는 다음의 두 가지 통화 대기 파킹된 통화 번호 유형을 사용할 수 있습니다.</p>
<p>CallPark. 표준 통화 대기 파킹된 통화 번호이며, 사용자가 통화를 대기시킨 다음 지정된 통화 대기 번호로 전화를 걸어 어떤 전화에서나 해당 통화를 재개할 수 있습니다. CallPark는 Type 매개 변수를 지정하지 않으면 사용되는 기본 파킹된 통화 번호 유형입니다.</p>
<p>GroupPickup. 그룹 통화를 사용하는 경우 통화 수신 그룹의 구성원에게 걸려 온 수신 전화를 받을 수 있습니다. 통화 수신 그룹은 관리자가 구성합니다.</p>
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

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

