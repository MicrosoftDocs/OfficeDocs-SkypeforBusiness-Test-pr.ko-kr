---
title: Get-CsCallParkOrbit
TOCTitle: Get-CsCallParkOrbit
ms:assetid: 73bbb09a-7966-4af1-aff3-001f5cc56df1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398554(v=OCS.15)
ms:contentKeyID: 49304034
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCallParkOrbit

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에 대한 통화 대기 파킹된 통화 번호 범위 설정을 가져옵니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsCallParkOrbit [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsCallParkOrbit [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Type <CallPark | GroupPickup>]

## 예제

## 예제 1

이 예제에서는 추가 매개 변수를 지정하지 않고 **Get-CsCallParkOrbit** cmdlet을 호출합니다. 이와 같이 호출하면 **Get-CsCallParkOrbit** cmdlet은 조직에서 사용하도록 구성된 모든 통화 대기 파킹된 통화 번호 범위의 컬렉션을 반환합니다.

    Get-CsCallParkOrbit

## 예제 2

예제 2에서는 **Get-CsCallParkOrbit** cmdlet을 사용하여 이름이 "Redmond CPO 1"인 통화 대기 파킹된 통화 번호 범위에 대한 정보를 반환합니다.

    Get-CsCallParkOrbit -Identity "Redmond CPO 1"

## 예제 3

이 예제의 명령은 문자열 "Redmond"가 ID에 있는 모든 통화 대기 파킹된 통화 번호 범위를 반환합니다. 예를 들어, 이 명령은 "Redmond 501", "CP Redmond 1", "ARedmond" 등과 같은 ID를 가진 통화 대기 파킹된 통화 번호를 반환합니다. 이 명령에서는 검색할 항목을 지정하기 위해 와일드카드 문자(\*)가 있는 Filter 매개 변수를 사용합니다. 이 검색은 대/소문자를 구분하지 않습니다.

    Get-CsCallParkOrbit -Filter *Redmond*

## 예제 4

이 명령은 ID가 ApplicationServer:pool0.litwareinc.com인 통화 대기 서비스에 할당된 모든 통화 대기 파킹된 통화 번호 범위를 반환합니다. **Get-CsCallParkOrbit** cmdlet은 모든 통화 대기 파킹된 통화 번호 범위의 컬렉션을 검색한 다음, 해당 컬렉션을 **Where-Object** cmdlet에 파이프합니다. **Where-Object** cmdlet에 대한 이 호출은 CallParkServiceId 속성에 ApplicationServer:pool0.litwareinc.com 값이 있는 해당 컬렉션의 모든 통화 대기 파킹된 통화 번호를 찾습니다. CallParkServiceId 매개 변수 이름 끝에 toString 메서드를 추가해야 합니다. CallParkServiceId는 WritableServiceId 유형입니다. 이 값을 제공된 문자열과 비교하려면 먼저 toString 메서드를 호출하여 문자열로 변환해야 합니다.

    Get-CsCallParkOrbit | Where-Object {$_.CallParkServiceId.toString() -eq "ApplicationServer:pool0.litwareinc.com"}

## 예제 5

이 예제의 명령은 번호 범위가 \* 접두사로 시작하는 모든 통화 대기 파킹된 통화 번호 범위를 반환합니다. **Get-CsCallParkOrbit** cmdlet이 모든 통화 대기 파킹된 통화 번호 범위의 컬렉션을 검색한 후에 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 \*로 시작하는 통화 대기 위치를 가진 통화 대기 파킹된 통화 번호 범위로 컬렉션의 범위를 좁힙니다. 이를 수행하기 위해 NumberRangeStart 개체의 StartsWith 속성에서 문자열 "\*"를 확인합니다.

    Get-CsCallParkOrbit | Where-Object {$_.NumberRangeStart.StartsWith("*")}

## 예제 6

이 예제의 명령은 범위의 번호에 접두사가 할당되지 않은 모든 통화 대기 파킹된 통화 번호 범위를 반환합니다. 접두사는 번호 앞에 오는 값 \* 또는 \#입니다. 이 명령에서 반환된 모든 통화 대기 파킹된 통화 번호는 다른 문자를 포함하지 않고 번호만으로 이루어진 범위를 가집니다. **Get-CsCallParkOrbit** cmdlet이 모든 통화 대기 파킹된 통화 번호 범위의 컬렉션을 검색한 후에 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet에 대한 호출을 살펴보면 $\_.NumberRangeStart\[0\]) 조건을 볼 수 있습니다. 이 조건은 범위의 시작 부분에 있는 번호의 첫 문자를 반환합니다. 범위의 시작 번호에 접두사가 없으면 끝 부분도 마찬가지이므로 범위의 시작 부분만 확인하면 됩니다. 이 문자는 숫자인지 확인하기 위해 IsDigit 함수에 전달됩니다. 숫자인 경우 해당 컬렉션 항목에 대한 통화 대기 파킹된 통화 번호 정보가 반환됩니다.

    Get-CsCallParkOrbit | Where-Object {[Char]::IsDigit($_.NumberRangeStart[0])}

## 자세한 정보

이 cmdlet은 조직에 정의된 통화 대기 파킹된 통화 번호의 설정을 검색합니다. Identity 매개 변수에 지정된 단일 통화 대기 파킹된 통화 번호 범위를 검색하거나 **Get-CsCallParkOrbit** cmdlet을 매개 변수 없이 호출하여 조직에 정의된 모든 통화 대기 파킹된 통화 번호 범위를 검색할 수 있습니다. 통화 대기 파킹된 통화 번호는 사용자가 통화를 대기시킬 수 있는 번호의 범위 및 이러한 번호 범위와 연관된 서버를 지정하는 설정으로 구성됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsCallParkOrbit** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCallParkOrbit"}

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
<td><p>이 매개 변수에는 와일드카드 문자열이 사용되며 해당 문자열과 일치하는 ID를 가진 모든 통화 대기 파킹된 통화 번호 범위가 반환됩니다. 예를 들어, Filter 값 Redmond*는 문자열 Redmond로 이름이 시작하는 모든 통화 대기 파킹된 통화 번호 범위(예: Redmond 1, Redmond 2 및 RedmondCPO)를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>통화 대기 파킹된 통화 번호 범위의 고유 이름입니다. 이 이름은 통화 대기 파킹된 통화 번호 범위를 정의할 때 관리자가 할당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 통화 대기 파킹된 통화 번호 정보를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Core.OrbitType</p></td>
<td><p>검색할 통화 대기 파킹된 통화 번호 유형을 지정합니다. Lync Server 2013에서는 다음의 두 가지 통화 대기 파킹된 통화 번호 유형을 사용할 수 있습니다.</p>
<p>CallPark. 표준 통화 대기 파킹된 통화 번호이며, 사용자가 통화를 대기시킨 다음 지정된 통화 대기 번호로 전화를 걸어 어떤 전화에서나 해당 통화를 재개할 수 있습니다.</p>
<p>GroupPickup. 그룹 통화를 사용하는 경우 통화 수신 그룹의 구성원에게 걸려온 수신 전화를 받을 수 있습니다. 통화 수신 그룹은 관리자가 구성합니다.</p>
<p>지정된 유형의 통화 대기 파킹된 통화 번호를 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Type GroupPickup</p>
<p>유형에 관계없이 모든 통화 대기 파킹된 통화 번호를 반환하려면 Type 매개 변수만 생략하면 됩니다.</p>
<p>이 매개 변수는 Lync Server 2013의 2013년 2월 릴리스에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbits 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)

