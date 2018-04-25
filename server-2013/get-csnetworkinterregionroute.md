---
title: Get-CsNetworkInterRegionRoute
TOCTitle: Get-CsNetworkInterRegionRoute
ms:assetid: 31c38d92-1cef-40fe-bd04-26e5b373703e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425817(v=OCS.15)
ms:contentKeyID: 49303227
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterRegionRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에서 네트워크 영역을 연결하는 경로를 하나 이상 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterRegionRoute [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 Identity가 NA\_APAC\_Route인 경로를 검색합니다.

    Get-CsNetworkInterRegionRoute -Identity NA_APAC_Route

## 예제 2

예제 2에서는 Filter 매개 변수를 사용하여 Identity 내에 APAC 문자열이 포함된 모든 경로를 검색합니다.

    Get-CsNetworkInterRegionRoute -Filter *APAC*

## 예제 3

이 예제에서는 네트워크 영역 링크 NA\_EMEA를 사용하는 모든 영역 경로를 검색합니다. 먼저 **Get-CsNetworkInterRegionRoute** cmdlet을 호출합니다. 이 cmdlet을 매개 변수 없이 호출하면 CAC 구성으로 정의된 모든 경로가 검색됩니다. 이 경로 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션을 가져오고 NetworkRegionLinks 목록에 NA\_EMEA 값이 포함된 컬렉션 내 모든 항목을 검색합니다.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionLinks -eq "NA_EMEA"}

## 예제 4

예제 4에서는 NorthAmerica 영역이 포함된 모든 영역 경로를 검색합니다. 명령의 처음 부분은 **Get-CsNetworkInterRegionRoute** cmdlet을 호출합니다. 이 cmdlet을 매개 변수 없이 호출하면 모든 영역 경로가 검색됩니다. 그런 다음 이 경로 컬렉션이 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 경로의 지역 중 하나로 NorthAmerica가 정의되어 있는 경로로 컬렉션의 범위를 좁힙니다. 이 작업을 수행하기 위해 경로의 NetworkRegionID1 값이 NorthAmerica와 같은지(-eq) 또는(-or) NetworkRegionID2 값이 NorthAmerica와 같은지 확인됩니다.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"}

## 자세한 정보

CAC 구성 내의 모든 영역에는 다른 모든 영역에 액세스할 수 있는 방법이 있어야 합니다. 영역 링크는 영역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 한 영역에서 다른 영역으로 연결이 통과하게 되는 링크된 경로를 결정합니다. 이 cmdlet은 이러한 경로 연결에 대한 정보를 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsNetworkInterRegionRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterRegionRoute"}

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
<td><p>이 매개 변수의 값으로 전달된 와일드카드 문자열에 Identity 값을 일치시켜 경로를 검색할 수 있도록 하는 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 네트워크 영역 경로의 고유 식별자입니다. 네트워크 영역 경로는 전역 범위에서만 만들어지므로 이 식별자에서는 범위를 지정할 필요가 없습니다. 대신 여기에는 특정 경로를 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 지역 간 경로 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 유형의 개체를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)

