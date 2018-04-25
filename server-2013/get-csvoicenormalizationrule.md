---
title: Get-CsVoiceNormalizationRule
TOCTitle: Get-CsVoiceNormalizationRule
ms:assetid: 59fe1370-1cec-4cf9-8f65-029a7c2454d1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398393(v=OCS.15)
ms:contentKeyID: 49303730
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceNormalizationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 음성 정규화 규칙에 대한 정보를 반환합니다. 음성 정규화 규칙은 전화 걸기 요구 사항(예: 외부 회선에 액세스하기 위해 9번 걸기)을 Lync Server에서 사용하는 E.164 전화 번호 형식으로 변환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceNormalizationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 조직에 대한 모든 음성 정규화 규칙을 검색합니다.

    Get-CsVoiceNormalizationRule

## 예제 2

예제 2에서는 모든 사이트에 지정된 모든 음성 정규화 규칙을 검색합니다.

    Get-CsVoiceNormalizationRule -Filter site*

## 예제 3

예제 3에서는 범위에 문자 s가 포함된 모든 음성 정규화 규칙을 검색합니다. 예를 들어, 이 명령은 모든 사이트 및 서비스 수준 규칙과 범위 이름에 s가 포함된 사용자별 규칙(예: RedmondEastUsers)을 반환합니다.

    Get-CsVoiceNormalizationRule -Filter *s*

## 예제 4

예제 2 및 3에 사용된 Filter 매개 변수는 ID의 범위 부분에서만 일치합니다. 이 예제에서는 이름 부분에서 일치를 수행하여 이름에 문자열 "seattle"이 포함된 모든 규칙을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsVoiceNormalizationRule** cmdlet을 호출하여 조직의 모든 정규화 규칙을 검색합니다. 그런 다음 컬렉션에서 Name 속성이 문자열 "seattle"과 일치하는 모든 항목을 찾기 위해 **Where-Object** cmdlet에 이 컬렉션을 파이프합니다.

    Get-CsVoiceNormalizationRule | Where-Object {$_.Name -match "seattle"}

## 자세한 정보

이 cmdlet은 명명된 음성 정규화 규칙이나 음성 정규화 규칙의 컬렉션을 반환합니다. 이러한 규칙은 전화 권한 부여 및 통화 경로 지정의 필수 부분입니다. 이러한 규칙은 번호를 내부 Lync Server 형식에서 표준(E.164) 형식으로 변환하기 위한 요구 사항을 정의합니다. 정규식을 이해하면 변환될 숫자 패턴을 정의하는 데 도움이 됩니다.

이 cmdlet에 의해 액세스되는 동일한 규칙은 **Get-CsDialPlan** cmdlet을 호출하여 반환되는 NormalizationRules 속성을 통해 액세스할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsVoiceNormalizationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceNormalizationRule"}

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
<td><p>와일드카드 문자열을 사용하여 ID에 기초한 정규화 규칙 컬렉션을 반환합니다. Filter는 이름이 아니라 ID의 범위 부분에서만 작동합니다. 예를 들어, 필터 값 *lob*는 전역 범위(문자 lob를 포함하는 범위)의 모든 규칙을 반환하지만 ID가 site:Redmond/lobby인 규칙은 반환하지 않습니다. 여기서 lob는 범위가 아니라 ID의 이름 부분에만 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>규칙에 대한 고유한 식별자입니다. 이 매개 변수에 값이 지정된 경우 범위/이름 형식이어야 합니다. 예를 들어, site:Redmond/Rule1이 될 수 있으며 여기서 site:Redmond는 범위이고 Rule1은 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 정규화 규칙을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsVoiceNormalizationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Get-CsDialPlan](get-csdialplan.md)

