---
title: Get-CsNetworkRegionLink
TOCTitle: Get-CsNetworkRegionLink
ms:assetid: dc5cb988-13e2-4af4-8b36-0aaa58ebf1c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398972(v=OCS.15)
ms:contentKeyID: 49305241
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkRegionLink

 

_**마지막으로 수정된 항목:** 2015-03-09_

네트워크 지역 간에 CAC(통화 허용 제어)용으로 구성된 하나 이상의 링크를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegionLink [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 Lync Server 배포 내에 정의된 모든 네트워크 지역 링크를 검색합니다.

    Get-CsNetworkRegionLink

## 예제 2

예제 2에서는 ID가 NA\_EMEA인 단일 네트워크 지역 링크에 대한 정보를 검색합니다.

    Get-CsNetworkRegionLink -Identity NA_EMEA

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 링크 이름(ID)에 문자열 EMEA가 포함된 모든 네트워크 지역 링크를 검색합니다. 이 경우 문자열 EMEA 앞뒤로 \* 문자를 각각 하나씩 포함해야 합니다. 이는 문자열 EMEA는 ID에 포함되어 있기만 하면 되고 그 앞이나 뒤에 임의의 문자가 올 수 있음을 의미합니다. 따라서 NA\_EMEA, EMEA\_APAC 및 EMEA2\_SA와 같은 이름의 링크가 검색됩니다.

    Get-CsNetworkRegionLink -Filter *EMEA*

## 예제 4

이 예제에서는 연결된 두 지역 중 하나의 링크 이름에 EMEA가 포함된 모든 네트워크 지역 링크를 검색합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsNetworkRegionLink** cmdlet을 호출하여 모든 지역 링크를 검색합니다. 이 링크 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션의 각 구성원을 하나씩 검사하여 NetworkRegionID1 및 NetworkRegionID2 속성 값을 확인합니다. 이 두 속성 중 하나가 EMEA와 같은 경우, 즉 NetworkRegionID1이 EMEA와 같은(-eq) 경우 또는(-or) NetworkRegionID2가 EMEA와 같은(-eq) 경우 컬렉션의 해당 항목을 유지하고 표시합니다.

    Get-CsNetworkRegionLink | Where-Object {$_.NetworkRegionID1 -eq "EMEA" -or $_.NetworkRegionID2 -eq "EMEA"}

## 자세한 정보

네트워크 내의 지역은 실제 WAN 연결을 통해 연결됩니다. 이 cmdlet은 Lync Server 배포의 네트워크 구성 설정 내에 정의된 하나 이상의 지역 링크를 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins그룹의 구성원은 **Get-CsNetworkRegionLink** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegionLink"}

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
<td><p>와일드카드 문자열과 일치하는 ID 값을 기준으로 네트워크 링크를 검색하는 데 사용되는 와일드카드 문자열을 적용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 네트워크 지역 링크의 고유 식별자입니다. 네트워크 지역 링크는 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 이 식별자는 해당 링크를 식별하는 고유 이름 문자열을 포함합니다. 이 값은 NetworkRegionLinkID와 같습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 지역 링크 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 유형의 개체를 하나 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)

