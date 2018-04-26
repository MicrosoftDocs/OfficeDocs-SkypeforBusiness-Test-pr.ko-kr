---
title: Get-CsVoiceRoute
TOCTitle: Get-CsVoiceRoute
ms:assetid: 422abb2d-bff3-4b9a-b18c-d8202b01f69b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425926(v=OCS.15)
ms:contentKeyID: 49303448
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 음성 경로에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceRoute [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

조직 내에 정의된 모든 음성 경로의 속성을 검색합니다.

    Get-CsVoiceRoute

## 예제 2

Route1 음성 경로의 속성을 검색합니다.

    Get-CsVoiceRoute -Identity Route1

## 예제 3

이 명령은 문자열 "test"가 해당 값의 아무 곳에나 포함된 ID가 있는 음성 경로 설정을 표시합니다. ID의 끝 부분에 있는 문자열 test만 찾으려면 값 \*test를 사용합니다. 마찬가지로 ID의 시작 부분에 있는 문자열 test만 찾으려면 값 test\*를 지정합니다.

    Get-CsVoiceRoute -Filter *test*

## 예제 4

이 명령은 PSTN 게이트웨이가 할당되지 않은 모든 음성 경로를 검색합니다. 먼저 **Get-CsVoiceRoute** cmdlet을 사용하여 모든 음성 경로를 검색합니다. 그런 다음, 이러한 음성 경로는 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 Get 작업 결과의 범위를 좁힙니다. 이 경우 각 음성 경로($\_가 나타내는)에서 PstnGatewayList 속성의 Count 속성을 확인합니다. PSTN 게이트웨이의 개수가 0인 경우 목록은 비어 있고 경로에 정의된 게이트웨이가 없는 것입니다.

    Get-CsVoiceRoute | Where-Object {$_.PstnGatewayList.Count -eq 0}

## 자세한 정보

이 cmdlet을 사용하여 하나 이상의 기존 음성 경로를 검색합니다. 음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다.

이 cmdlet을 사용하여 경로에 연결된 PSTN 게이트웨이(있을 경우), 경로에 연결된 PSTN 사용법, 경로가 적용되는 전화 번호를 식별하는 패턴(정규식 형태), 호출자 ID 설정 등과 같은 음성 경로에 대한 정보를 검색할 수 있습니다. PSTN 사용법은 음성 경로를 음성 정책에 연결합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsVoiceRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceRoute"}

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
<td><p>이 매개 변수는 이 매개 변수에 전달된 와일드카드 값에 기초하여 Get 작업의 결과를 필터링합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>음성 경로를 고유하게 식별하는 문자열입니다. ID가 제공되지 않은 경우 조직에 대한 모든 음성 경로가 반환됩니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 경로를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)

