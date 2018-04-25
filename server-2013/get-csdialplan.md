---
title: Get-CsDialPlan
TOCTitle: Get-CsDialPlan
ms:assetid: f77df510-ea43-4352-84c1-13f69eda252e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413043(v=OCS.15)
ms:contentKeyID: 49305571
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDialPlan

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 다이얼 플랜에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDialPlan [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDialPlan [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 **Get-CsDialPlan** cmdlet을 추가 매개 변수 없이 호출하여 조직에서 사용하도록 구성된 모든 다이얼 플랜의 컬렉션을 반환합니다.

    Get-CsDialPlan

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 ID가 RedmondDialPlan인 사용자별 다이얼 플랜을 가진 다이얼 플랜에 대한 데이터만 검색하도록 제한합니다. ID가 고유해야 하므로 이 명령은 지정한 다이얼 플랜만 반환합니다.

    Get-CsDialPlan -Identity RedmondDialPlan

## 예제 3

예제 3은 사용자별 다이얼 플랜을 검색하는 대신 사이트에 할당된 다이얼 플랜을 검색하는 점을 제외하고 예제 2와 동일합니다. 이 작업을 수행하기 위해 site: 값 다음에 검색할 사이트의 사이트 이름(이 경우 Redmond)을 지정합니다.

    Get-CsDialPlan -Identity site:Redmond

## 예제 4

이 예제에서는 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 다이얼 플랜의 컬렉션을 반환합니다. (사용자별 또는 태그 범위에서 구성된 설정은 사용자 및 그룹에 직접 할당할 수 있습니다.) 와일드카드 문자열 tag:\*는 다이얼 플랜을 사용자별 다이얼 플랜으로 식별하는 문자열 값 tag:로 시작하는 ID를 가진 다이얼 플랜만 반환하도록 cmdlet에 지시합니다.

    Get-CsDialPlan -Filter tag:*

## 예제 5

이 예제에서는 조직에서 사용하도록 구성된 다이얼 플랜에 사용되는 정규화 규칙을 표시합니다. NormalizationRules 속성이 개체 배열로 구성되므로 일반적으로 전체 정규화 규칙 집합이 화면에 표시되지 않습니다. 이러한 규칙을 모두 표시하기 위해 이 샘플 명령은 먼저 **Get-CsDialPlan** cmdlet을 사용하여 모든 다이얼 플랜의 컬렉션을 검색합니다. 이 컬렉션은 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 **Select-Object** cmdlet의 ExpandProperty 매개 변수를 사용하여 NormalizationRules 속성에서 발견된 값이 "확장"됩니다. 값을 확장한다는 것은 **Get-CsVoiceNormalizationRule** cmdlet을 호출한 경우에 표시되는 출력처럼 모든 정규화 규칙이 화면에 개별적으로 표시된다는 의미입니다.

    Get-CsDialPlan | Select-Object -ExpandProperty NormalizationRules

## 예제 6

예제 6에서는 **Get-CsDialPlan** cmdlet 및 **Where-Object** cmdlet을 사용하여 Redmond라는 단어가 설명에 포함된 모든 다이얼 플랜의 컬렉션을 검색합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDialPlan** cmdlet을 사용하여 모든 다이얼 플랜을 검색합니다. 그런 다음, 해당 컬렉션은 반환되는 데이터를 Redmond라는 단어가 설명의 아무 곳에나 포함된 프로필로 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDialPlan | Where-Object {$_.Description -match "Redmond"}

## 자세한 정보

이 cmdlet은 조직에 있는 하나 이상의 다이얼 플랜(위치 프로필이라고도 함)에 대한 정보를 반환합니다. 다이얼 플랜은 Enterprise Voice 사용자가 전화 통화를 할 수 있는 데 필요한 정보를 제공합니다. 또한 전화 접속 회의를 위해 회의 길잡이 응용 프로그램에서 다이얼 플랜이 사용됩니다. 다이얼 플랜은 어떤 정규화 규칙이 적용되는지, 외부 통화를 위해 접두사를 사용해야 하는지 여부 등을 결정합니다.

참고: **Get-CsDialPlan** cmdlet을 사용하여 다이얼 플랜의 정규화 규칙에 대한 특정 정보를 검색할 수 있지만 해당 정보가 유일하게 필요한 다이얼 플랜 정보인 경우 **Get-CsVoiceNormalizationRule** cmdlet을 사용할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDialPlan** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDialPlan"}

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
<td><p>지정된 와일드카드 문자열과 일치하는 ID를 가진 다이얼 플랜만 포함하도록 결과의 범위를 좁힐 수 있는 와일드카드 검색을 수행합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 다이얼 플랜을 식별하기 위해 범위 및 이름(사용자별 범위의 경우)을 지정하는 고유 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 다이얼 플랜 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialPlan](new-csdialplan.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)  
[Test-CsDialPlan](test-csdialplan.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

