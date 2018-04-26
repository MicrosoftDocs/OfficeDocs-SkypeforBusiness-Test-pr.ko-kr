---
title: Get-CsNetworkRegion
TOCTitle: Get-CsNetworkRegion
ms:assetid: 5c9eef10-16c1-45f7-ae7b-2bee0965b421
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398406(v=OCS.15)
ms:contentKeyID: 49303760
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 네트워크 지역을 검색합니다. 네트워크 지역은 엔터프라이즈 네트워크에서 네트워크 허브 또는 백본을 나타냅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegion [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에 대해 정의된 모든 네트워크 지역을 검색합니다.

    Get-CsNetworkRegion

## 예제 2

예제 2에서는 Identity NorthAmerica를 사용하는 네트워크 지역을 검색합니다. ID는 고유하기 때문에 이 명령은 하나의 네트워크 지역만 검색합니다.

    Get-CsNetworkRegion -Identity NorthAmerica

## 예제 3

이 예제에서는 문자열 "America"로 끝나는 ID를 사용하는 모든 네트워크 지역을 검색합니다. 이 명령은 NorthAmerica, SouthAmerica 및 CentralAmerica 등의 ID를 사용하는 지역을 검색합니다.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

## 예제 4

이 예제에서는 중앙 사이트 Redmond와 연결된 모든 네트워크 지역을 검색합니다. 명령은 먼저 매개 변수 없이 **Get-CsNetworkRegion** cmdlet을 호출하여 Lync Server 배포에 대해 정의된 모든 네트워크 지역의 컬렉션을 검색합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 이 컬렉션을 필터링하여 CentralSite 값이 site:Redmond와 같은(-eq) 항목(네트워크 지역)만 반환합니다.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

## 자세한 정보

네트워크 지역은 여러 지역의 많은 네트워크 부분을 교차합니다. 모든 네트워크 지역은 중앙 사이트와 연결되어 있어야 합니다. 이 cmdlet을 사용하면 연결된 중앙 사이트를 비롯한 하나 이상의 네트워크 지역에 대한 정보, 오디오 및 비디오 연결에 대체 경로가 허용되는지 여부를 결정하는 설정 및 지역 내의 사이트를 미디어 우회 구성과 연결하는 설정을 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkRegion** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegion"}

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
<td><p>이 매개 변수를 사용하면 조직에 대해 구성된 모든 네트워크 지역의 ID에 대해 와일드카드 검색을 수행할 수 있습니다. 즉, 와일드카드 문자를 사용하여 ID의 일부를 필터링할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 네트워크 지역의 고유한 식별자입니다. ID는 해당 지역을 고유하게 식별하는 문자열 형식입니다. ID는 NetworkRegionID와 동일합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 지역 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 유형의 개체 중 하나 이상을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)

