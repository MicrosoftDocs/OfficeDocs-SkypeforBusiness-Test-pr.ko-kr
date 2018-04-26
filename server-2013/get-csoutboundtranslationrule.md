---
title: Get-CsOutboundTranslationRule
TOCTitle: Get-CsOutboundTranslationRule
ms:assetid: 0564df17-dcca-44e1-9341-15521e0fa14b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398104(v=OCS.15)
ms:contentKeyID: 49302675
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOutboundTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

아웃바운드 변환 규칙을 하나 이상 검색합니다. 아웃바운드 변환 규칙은 전화 번호를 PBX(Private Branch Exchange) 시스템 및 PSTN(공중 전화망) 게이트웨이와의 상호 작용을 위한 로컬 전화 번호 형식으로 변환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsOutboundTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsOutboundTranslationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 Lync Server 배포에 대한 모든 아웃바운드 변환 규칙을 검색합니다.

    Get-CsOutboundTranslationRule

## 예제 2

이 예제에서는 ID가 site:Redmond/Prefix Redmond인 단일 아웃바운드 변환 규칙을 검색합니다.

    Get-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"

## 예제 3

이 예제에서는 모든 사이트 수준 아웃바운드 변환 규칙을 검색합니다. 이 명령은 site:\* 필터를 사용하여 **Get-CsOutboundTranslationRule** cmdlet을 호출하여 ID 값이 site: 문자열로 시작하는 모든 규칙의 컬렉션을 반환합니다.

    Get-CsOutboundTranslationRule -Filter site:*

## 자세한 정보

기존 아웃바운드 변환 규칙을 검색하려면 이 cmdlet을 호출합니다. Lync Server는 E.164 형식으로 전화 번호를 정규화합니다. 그러나 이 형식을 사용할 수 없는 PBX(Private Branch Exchange) 시스템이 많습니다. 아웃바운드 변환 규칙은 이 번호를 중재 서버 또는 게이트웨이로 전송하기 전에 로컬 전화 번호 형식으로 변환합니다.

각 아웃바운드 변환 규칙은 트렁크 구성과 연결됩니다. 둘 이상의 아웃바운드 변환 규칙을 각 트렁크 구성과 연결할 수 있습니다. 따라서 각 규칙의 ID는 범위와 각 범위 내에서 고유한 이름으로 구성됩니다(범위/이름 형식, 예: site:Redmond/OBR1). 규칙은 동일한 범위의 트렁크 구성과 자동으로 연결됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsOutboundTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsOutboundTranslationRule"}

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
<td><p>ID를 기준으로 와일드카드 검색을 수행하여 지정된 와일드카드 문자열과 ID가 일치하는 아웃바운드 변환 규칙으로 결과를 좁힙니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 아웃바운드 변환 규칙에 대한 고유한 식별자입니다. ID는 범위와 각 범위 내에서 고유한 이름이 뒤에 나오는 형식으로 구성됩니다(예: site:Redmond/OutboundRule1). ID에 값을 지정하면 아웃바운드 변환 규칙이 한 개 이하로 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 아웃바운드 변환 규칙을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 유형의 개체를 한 개 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)

