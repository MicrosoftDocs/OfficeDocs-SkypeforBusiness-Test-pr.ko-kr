---
title: Get-CsNetworkInterSitePolicy
TOCTitle: Get-CsNetworkInterSitePolicy
ms:assetid: a4a64048-f8d7-483a-9565-0c6f3b0937b7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412769(v=OCS.15)
ms:contentKeyID: 49304607
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterSitePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에 직접 연결된 사이트 간 대역폭 제한을 정의하는 하나 이상의 네트워크 사이트 정책을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterSitePolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

**Get-CsNetworkInterSitePolicy** cmdlet을 매개 변수 없이 호출하면 직접 연결된 두 네트워크 사이트 간에 정의된 모든 네트워크 사이트 정책이 검색됩니다.

    Get-CsNetworkInterSitePolicy

## 예제 2

이 예제에서는 ID가 Reno\_Portland인 네트워크 사이트 정책을 검색합니다.

    Get-CsNetworkInterSitePolicy -Identity Reno_Portland

## 예제 3

예제 3에서는 Identity 값 내에 Reno 문자열이 있는 모든 네트워크 사이트 정책을 검색합니다. Filter 매개 변수에 전달된 값 내에 있는 와일드카드 문자(\*)는 "모든 문자 또는 문자 집합"을 의미합니다. 즉, \*Reno\* 문자열은 임의의 문자로 시작하고 다음에 Reno 문자열이 오고 다음에 임의 문자가 오는 Identity 값과 일치합니다.

    Get-CsNetworkInterSitePolicy -Filter *Reno*

## 예제 4

이 예제에서는 대역폭 정책 프로필이 할당되지 않은 모든 네트워크 사이트 정책을 검색합니다. 명령은 먼저 예제 1에서와 같이 모든 네트워크 사이트 정책 컬렉션을 검색하는 **Get-CsNetworkInterSitePolicy** cmdlet을 호출합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 대역폭 정책 프로필이 할당되지 않은 사이트 정책만 포함하도록 컬렉션 범위를 좁힙니다. 이를 위해 각 사이트 정책의 BWPolicyProfileID 속성이 Null($null)과 같은지(-eq) 비교하여 확인합니다.

    Get-CsNetworkInterSitePolicy | Where-Object {$_.BWPolicyProfileID -eq $null}

## 자세한 정보

네트워크 사이트에서 직접 연결을 공유하는 경우 이 두 사이트 간에 오디오 및 비디오 연결에 대한 대역폭 제한이 정의될 수 있습니다. 이 cmdlet은 직접 연결된 사이트에 대역폭 제한 정책을 적용하는 하나 이상의 네트워크 사이트 정책을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkInterSitePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterSitePolicy"}

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
<td><p>ID 값이 와일드카드 문자열과 일치하는 정책을 검색하는 와일드카드 문자가 포함된 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 네트워크 사이트 정책의 고유 식별자입니다. 네트워크 사이트 정책은 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 여기에는 해당 정책을 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 사이트 간 정책 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 유형의 개체를 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

