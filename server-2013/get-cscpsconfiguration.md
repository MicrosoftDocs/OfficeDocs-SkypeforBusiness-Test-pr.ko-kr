---
title: Get-CsCpsConfiguration
TOCTitle: Get-CsCpsConfiguration
ms:assetid: d81ee8fe-d02b-4f60-a4d5-6aa84f65d156
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398948(v=OCS.15)
ms:contentKeyID: 49305195
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCpsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

통화 대기 서비스에 대한 정보를 반환합니다. 통화 대기는 사용자가 수신 전화 통화를 "대기"시킬 수 있는 서비스입니다. 통화를 대기시키면 통화가 지정된 범위, 즉 파킹된 통화 번호의 번호로 전송되고 즉시 대기 상태로 전환됩니다. 원래 전화를 받았던 사람뿐만 아니라 모든 사람이 올바른 번호를 입력하여 시스템에서 전화를 통해 대화를 다시 시작할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCpsConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 정의된 모든 통화 대기 서비스 구성의 컬렉션을 검색합니다.

    Get-CsCpsConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond1인 통화 대기 서비스 구성만 검색합니다.

    Get-CsCpsConfiguration -Identity site:Redmond1

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 통화 대기 서비스 구성을 반환하기 위해 Filter 매개 변수를 사용합니다. 와일드카드 문자열 site:\*는 문자열 값 site:으로 시작하는 ID를 가진 설정만 반환하도록 **Get-CsCpsConfiguration** cmdlet에 지시합니다.

    Get-CsCpsConfiguration -Filter site:*

## 예제 4

예제 3과 같이 이 예제에서는 Filter 매개 변수를 사용하여 정의된 모든 통화 대기 서비스 구성의 하위 집합을 검색합니다. 이 경우에는 Redmond1, Redmond2 및 RemoteComputer와 같은 문자 re로 시작하는 이름을 가진 모든 사이트에 대한 통화 대기 구성을 반환하는 문자열 \*:re\*를 필터링합니다.

    Get-CsCpsConfiguration -Filter *:re*

## 예제 5

예제 5에서는 전화 건 사람이 통화 대기 중일 때 음악을 재생하지 않는 모든 통화 대기 서비스 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsCpsConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 통화 대기 서비스 설정을 검색합니다. 이 컬렉션은 반환되는 데이터를 EnableMusicOnHold 속성이 False와 같은(-eq) 항목으로 제한하는 필터가 적용되는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsCpsConfiguration | Where-Object {$_.EnableMusicOnHold -eq $False}

## 자세한 정보

이 cmdlet은 하나 이상의 통화 대기 서비스 구성을 검색하는 데 사용됩니다. 통화 대기 서비스 구성은 통화가 대기된 후 통화에 수행되는 작업을 지정합니다. 예를 들어 대기된 통화를 일정 기간 동안 받지 않을 경우 관리자 또는 응답 그룹과 같은 누군가에게 자동으로 전달할 수 있습니다. 통화를 잊지 않게 하려면 일정 기간 후에 벨이 울리도록 통화를 구성할 수도 있습니다. 또한 통화를 대기하는 동안 전화를 건 사람에게 음악이 들리도록 통화 대기 서비스를 구성할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsCpsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCpsConfiguration"}

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
<td><p>와일드카드 검색을 수행하여 와일드카드 문자열과 일치하는 ID 값을 가진 구성만 검색하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 통화 대기 서비스 구성의 고유 식별자입니다. 이 식별자는 Global 또는 site:&lt;sitename&gt;입니다. 여기서 &lt;sitename&gt;은 구성이 적용되는 사이트의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 통화 대기 서비스 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 유형의 개체를 하나 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

