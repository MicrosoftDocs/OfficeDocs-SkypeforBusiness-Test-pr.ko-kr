---
title: Get-CsNetworkBandwidthPolicyProfile
TOCTitle: Get-CsNetworkBandwidthPolicyProfile
ms:assetid: 31784852-0cf4-4114-bf92-5eef6f346c47
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425815(v=OCS.15)
ms:contentKeyID: 49303222
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkBandwidthPolicyProfile

 

_**마지막으로 수정된 항목:** 2015-03-09_

네트워크 대역폭 정책 프로필을 한 개 이상 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkBandwidthPolicyProfile [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

매개 변수를 지정하지 않고 **Get-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하면 Lync Server 배포에 정의된 모든 대역폭 정책 프로필을 검색합니다.

    Get-CsNetworkBandwidthPolicyProfile

## 예제 2

이 예제에서는 ID가 LowBWProfile인 대역폭 정책 프로필을 검색합니다. ID는 고유하므로 이 명령은 프로필을 한 개 이하로 반환합니다.

    Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 와일드카드 문자열을 기준으로 검색할 프로필을 한 개 이상 지정합니다. 문자열 \*50MB\*를 사용했는데, 이는 Identity 값에 50MB 문자열이 포함된 모든 대역폭 정책 프로필을 검색하도록 지정합니다. 예를 들어 이 문자열을 사용하면 ID가 "BW profile for 50MB links", "50MB audio limit" 및 "video limits of 50MB"와 같은 프로필이 검색됩니다.

    Get-CsNetworkBandwidthPolicyProfile -Filter *50MB*

## 자세한 정보

대역폭 정책은 CAC(통화 허용 제어)의 일부로서 특정 형식의 대역폭 제한을 정의하는 데 사용됩니다. Lync Server에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 이 cmdlet은 이러한 정책의 컨테이너 프로필을 한 개 이상 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkBandwidthPolicyProfile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkBandwidthPolicyProfile"}

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
<td><p>ID 값이 와일드카드 패턴과 일치하는 대역폭 정책 프로필을 검색하는 데 사용되는 와일드카드를 포함하는 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 대역폭 정책 프로필을 고유하게 식별하는 문자열 값입니다. ID를 지정하면 프로필이 한 개 이하만 검색됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 대역폭 정책 프로필을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 형식의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

