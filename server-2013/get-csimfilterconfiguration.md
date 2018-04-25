---
title: Get-CsImFilterConfiguration
TOCTitle: Get-CsImFilterConfiguration
ms:assetid: de9b24a1-8d17-4da1-89c2-db5b532674eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398980(v=OCS.15)
ms:contentKeyID: 49305271
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsImFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직 내에 구성된 메신저 링크 필터를 반환합니다. 이러한 필터는 사용자가 특정 접두사를 사용하는 하이퍼링크(예: http 또는 telnet 접두사가 있는 링크)가 포함된 메신저 대화를 보내지 못하도록 하는 데 사용됩니다. 설정에 따라 이는 이러한 스키마 중 하나로 시작되는 URI(Uniform Resource Identifier)가 클릭할 수 없는 하이퍼링크로 변환되거나 모두 제거됨을 의미합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsImFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsImFilterConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 메신저 하이퍼링크 필터 컬렉션을 반환합니다. 이는 매개 변수 없이 **Get-CsImFilterConfiguration** cmdlet을 호출할 때마다 실행되는 동작입니다.

    Get-CsImFilterConfiguration

## 예제 2

예제 2에서는 단일 메신저 필터에 대한 설정(여기서는 ID가 site:Redmond인 설정)을 반환합니다. ID는 고유해야 하므로 이 명령은 두 개 이상의 구성을 반환할 수 없습니다.

    Get-CsImFilterConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사이트 수준에서 구성된 모든 메신저 필터 컬렉션을 반환합니다. 와일드카드 문자열 site:\*는 ID가 문자열 값 site:으로 시작하는 메신저 필터 구성만 반환하도록 **Get-CsImFilterConfiguration** cmdlet에 지시합니다.

    Get-CsImFilterConfiguration -Filter site:*

## 예제 4

예제 4에서는 화면에 표시되는 전역 메신저 필터 구성의 Prefixes 속성 값을 "확장"합니다. 즉, 속성 및 해당 값을 보다 친숙하고 읽기 쉬운 형식으로 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsImFilterConfiguration** cmdlet을 사용하여 전역 메신저 필터 구성을 검색합니다. 이때 **Get-CsImFilterConfiguration** cmdlet을 괄호로 묶어 호출해야 합니다. 이렇게 하면 Windows PowerShell에서 괄호로 묶인 명령을 먼저 수행한 후 다음 명령을 계속 수행합니다. 구성 검색이 완료되면 Prefixes 속성 값이 한 줄씩 접두사와 함께 표시됩니다.

    (Get-CsImFilterConfiguration -Identity Global).Prefixes

## 자세한 정보

메신저 대화를 보낼 때 사용자가 대화의 다른 참가자를 특정 웹 사이트 또는 공유로 연결하는 URI를 해당 메시지 텍스트 내에 포함할 수 있는데, 특정 접두사가 있는 하이퍼링크가 차단되거나 비활성화되도록 Lync Server를 구성할 수 있습니다. 즉, 참가자가 단순히 링크를 클릭하여 URI가 참조하는 사이트로 이동할 수 없고 수동으로 링크를 복사하여 브라우저에 붙여 넣어야 합니다.

**Get-CsImFilterConfiguration** cmdlet은 메신저 대화에서 URI 필터링에 대한 모든 설정을 검색합니다. 매개 변수 없이 호출되는 **Get-CsImFilterConfiguration** cmdlet은 전역적으로 적용되거나 모든 사이트에 적용되는 모든 URI 메신저 필터 설정을 반환합니다. 또한 특정 사이트의 설정 또는 전역 설정을 표시하도록 ID를 지정할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsImFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsImFilterConfiguration"}

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
<td><p>지정된 ID 패턴과 일치하는 구성에 대한 와일드카드 검색을 수행합니다. 예를 들어 ID가 site*로 시작하는 모든 설정, 즉 모든 사이트별 설정을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 설정의 고유 식별자입니다. 이 값은 global 또는 site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 이러한 설정을 적용할 사이트의 이름(예: site:Redmond)입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 메신저 필터 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsImFilterConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)

