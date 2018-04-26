---
title: Get-CsNetworkSite
TOCTitle: Get-CsNetworkSite
ms:assetid: 9627869d-101f-4668-bee2-01fce1d84cbd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398766(v=OCS.15)
ms:contentKeyID: 49304444
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkSite

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 또는 E9-1-1(Enhanced 9-1-1)에 대해 정의된 하나 이상의 네트워크 사이트를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkSite [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

**Get-CsNetworkSite** cmdlet을 매개 변수 없이 호출하면 Lync Server 배포 내에 CAC 또는 E9-1-1에 대해 구성된 모든 네트워크 사이트가 반환됩니다.

    Get-CsNetworkSite

## 예제 2

이 명령은 Identity, 그리고 정의상 NetworkSiteID가 Redmond인 사이트를 검색합니다.

    Get-CsNetworkSite -Identity Redmond

## 예제 3

예제 3의 명령은 Filter 매개 변수를 포함하여 **Get-CsNetworkSite** cmdlet을 호출합니다. Filter 매개 변수의 값은 NA\*로, 이는 문자열 NA로 시작하고 그 뒤에 문자(문자 수는 관계없음)가 오는 ID를 가진 모든 사이트가 이 명령을 통해 검색됨을 의미합니다. 예를 들어 NARedmond, NAVancouver 및 NAChicago와 같은 사이트가 반환됩니다.

    Get-CsNetworkSite -Filter NA*

## 예제 4

예제 4에서는 두 개의 cmdlet, 즉 **Get-CsNetworkSite** cmdlet 및 **Where-Object** cmdlet을 사용하여 NorthAmerica 지역에 속하는 모든 사이트를 검색합니다. 명령은 먼저 **Get-CsNetworkSite** cmdlet을 매개 변수 없이 호출하여 모든 네트워크 사이트를 검색합니다. 그러면 이 사이트 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션을 필터링하면서 컬렉션에서 NetworkRegionID 속성이 NorthAmerica와 같은(-eq) 모든 사이트를 찾습니다.

    Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"}

## 자세한 정보

네트워크 사이트는 각 CAC 또는 E9-1-1 배포 영역 내에 구성된 사무실 또는 위치입니다. 이 cmdlet은 하나 이상의 기존 사이트에 대한 설정을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkSite** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkSite"}

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
<td><p>사이트 Identity와 Filter 값의 대조를 기반으로 여러 사이트를 검색할 수 있도록 하는 와일드카드 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 네트워크 사이트의 고유 식별자입니다. 사이트는 전역 범위에서만 만들어지므로 범위는 지정할 필요가 없습니다. 대신 사이트 ID만 지정하면 됩니다(네트워크 사이트에 대한 NetworkSiteID와 같은 값임).</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 사이트 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType 유형의 개체를 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkSite](new-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)

