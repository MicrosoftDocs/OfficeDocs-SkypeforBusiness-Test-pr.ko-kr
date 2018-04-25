---
title: New-CsNetworkBWPolicy
TOCTitle: New-CsNetworkBWPolicy
ms:assetid: bbc91bd1-453c-4ae6-bb77-3b6be9429ed0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412916(v=OCS.15)
ms:contentKeyID: 49304858
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBWPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

대역폭 정책 프로필에 적용할 수 있는 대역폭 정책을 메모리에 만듭니다. Lync Server에서는 오디오 또는 비디오 대역폭에 정책이 적용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkBWPolicy -BWLimit <UInt32> -BWPolicyModality <Audio | Video> -BWSessionLimit <UInt32>

## 예제

## 예제 1

이 예제에서는 새 대역폭 정책을 만들어 $bwp 변수에 할당합니다. **New-CsNetworkBWPolicy** cmdlet의 모든 매개 변수는 필수 항목입니다. 이 예제에서는 2000kbps의 총 대역폭 제한(BWLimit) 및 300kbps의 대역폭 세션 제한(BWSessionLimit)을 지정하고 이러한 제한을 비디오 세션(-BWPolicyModality video)에 적용합니다.

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video

## 예제 2

예제 2에서는 예제 1을 확장하여 새 대역폭 정책을 정책 프로필에 할당합니다. 첫째 줄의 명령은 예제 1과 같이 비디오 대역폭 제한을 만듭니다. 그런 다음 둘째 줄에서 **New-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 해당 정책을 새 프로필에 추가합니다. 새 프로필은 LowBWLimit라는 ID를 받습니다. 마지막으로 BWPolicy 매개 변수를 사용하여 $bwp 값을 제공합니다. 이 변수에 첫째 줄에서 만든 새 대역폭 정책이 포함됩니다.

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video
    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bwp

## 자세한 정보

이 cmdlet은 새 대역폭 정책을 만듭니다. 대역폭 정책은 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Lync Server에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 대역폭 정책은 메모리에만 만들어지므로 출력이 변수에 할당된 다음 **New-CsNetworkBandwidthPolicyProfile** cmdlet 또는 **Set-CsNetworkBandwidthPolicyProfile** cmdlet의 BWPolicy 매개 변수 값으로 전달됩니다. 대역폭 정책은 단일 프로필에 대한 여러 정책을 저장할 수 있고 전역 네트워크 구성 CAC(통화 허용 제어)의 일부인 정책 프로필에 적용됩니다.

권장되는 오디오 및 비디오 정책 할당 방법은 **New-CsNetworkBandwidthPolicyProfile** 또는 **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하고 AudioBWLimit, AudioBWSessionLimit, VideoBWLimit 및 VideoBWSessionLimit 매개 변수 값을 지정하여 오디오 및 비디오 정책을 대역폭 정책 프로필에 직접 할당하는 것입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkBWPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWPolicy"}

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
<td><p><em>BWLimit</em></p></td>
<td><p>필수</p></td>
<td><p>System.UInt32</p></td>
<td><p>BWPolicyModality 매개 변수에 지정된 유형의 모든 동시 세션에 대한 최대 총 대역폭(kbps)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
<td><p>제한할 대역폭 유형을 결정합니다.</p>
<p>유효한 값: Audio, Video</p></td>
</tr>
<tr class="odd">
<td><p><em>BWSessionLimit</em></p></td>
<td><p>필수</p></td>
<td><p>System.UInt32</p></td>
<td><p>BWPolicyModality 매개 변수에 지정된 유형의 단일 세션에 허용되는 최대 대역폭(kbps)입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

