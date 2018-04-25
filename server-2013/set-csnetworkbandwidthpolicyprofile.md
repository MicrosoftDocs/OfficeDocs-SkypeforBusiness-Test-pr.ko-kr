---
title: Set-CsNetworkBandwidthPolicyProfile
TOCTitle: Set-CsNetworkBandwidthPolicyProfile
ms:assetid: 519916b9-d5a0-476e-a516-9b8a3058daf2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398338(v=OCS.15)
ms:contentKeyID: 49303620
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkBandwidthPolicyProfile

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 네트워크 대역폭 정책 프로필을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkBandwidthPolicyProfile [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제는 ID가 LowBWProfile인 대역폭 정책 프로필의 설명을 수정합니다. 이 작업을 수행하기 위해 **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 수정할 프로필 이름을 지정하는 Identity 및 프로필에 대한 새 설명을 지정하는 Description의 두 매개 변수와 함께 호출합니다.

    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile -Description "Policy for links of less than 10MB"

## 예제 2

예제 2는 ID가 LowBWLimit인 대역폭 정책 프로필에 대한 비디오 전송의 전체 제한 및 세션 제한을 수정합니다. 수정할 프로필의 ID를 지정한 후 VideoBWLimit 매개 변수를 사용하여 전체 비디오 제한을 2500으로 설정합니다. 그런 다음 VideoBWSessionLimit 매개 변수를 사용하여 개별 세션 제한을 300으로 설정합니다. 이 명령은 비디오 프로필을 추가하거나 LowBWLimit 대역폭 정책 프로필의 기존 비디오 프로필을 업데이트합니다. 기존 오디오 프로필은 영향을 받지 않습니다.

    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -VideoBWLimit 2500 -VideoBWSessionLimit 300

## 예제 3

이 예제에서는 새 대역폭 정책을 만들어 ID가 LowBWLimit인 대역폭 정책 프로필에 할당합니다. 이 예제의 첫째 줄은 **New-CsNetworkBWPolicy** cmdlet에 대한 호출입니다. 이 cmdlet은 새 프로필을 만듭니다. 이 경우에는 제한이 5000kbps(-BWLimit 5000)이고 세션 제한이 200kbps(-BWSessionLimit 200)인 비디오 프로필(-BWPolicyModality video)입니다. 이 새 프로필 개체는 $bp 변수에 저장됩니다. 이 예제의 다음 줄은 **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 LowBWLimit 프로필을 수정합니다(-Identity LowBWLimit). BWPolicy 매개 변수에는 $bp 값을 사용합니다. 이는 이 프로필의 기존 정책을 $bp 변수에 저장된 새로 만든 정책으로 대체합니다.

    $bp = New-CsNetworkBWPolicy -BWLimit 5000 -BWSessionLimit 200 -BWPolicyModality video
    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bp

## 예제 4

예제 4는 LowBWProfile 프로필의 기존 정책 집합에 새 오디오 대역폭 정책을 추가합니다. 첫째 줄에서는 **Get-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 ID가 LowBWProfile인 프로필을 검색합니다. 해당 프로필을 $a 변수에 저장합니다. 다음 줄에서는 **New-CsNetworkBWPolicy** cmdlet을 호출하여 새 대역폭 정책을 만듭니다. 이 정책은 제한이 2000kbps(-BWLimit 2000)이고 세션 제한이 300kbps(-BWSessionLimit 300)인 오디오 정책(-BWPolicyModality audio)입니다. 이 새 정책은 $ap 변수에 저장됩니다.

셋째 줄에서는 첫째 줄에서 검색한 프로필($a 변수에 저장됨)에 새 오디오 정책($ap에 저장됨)을 추가합니다. 이를 수행하기 위해 프로필에서 BWPolicy 속성의 Add 메서드를 호출하고 $ap 값을 전달합니다 이는 "$ap에 저장된 새 정책을 LowBWProfile 프로필의 BWPolicy($a에 저장됨)에 추가하는 것"으로 해석할 수 있습니다.

마지막으로 **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 LowBWProfile 프로필을 업데이트합니다. Instance 매개 변수를 사용하고 수정된 프로필이 포함된 $a 값을 전달합니다.

    $a = Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile
    $ap = New-CsNetworkBWPolicy -BWLimit 2000 -BWSessionLimit 300 -BWPolicyModality audio
    $a.BWPolicy.Add($ap)
    Set-CsNetworkBandwidthPolicyProfile -Instance $a

## 예제 5

예제 5는 기능 면에서 예제 4와 동일합니다. LowBWProfile 프로필의 기존 정책 목록에 새 오디오 정책을 추가합니다. 이 메서드에 필요한 줄 수가 더 적지만 확실한 것은 아닙니다. 이 예제를 여기에 포함한 이유는 동일한 작업을 여러 가지 방법으로 수행할 수 있음을 보여 주기 위함입니다.

첫째 줄에서는 새 오디오 대역폭 정책을 만들고 대역폭 제한(2000) 및 세션 제한(300)을 설정하고 새 개체를 $ap 변수에 저장합니다. 다음으로, **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 ID가 LowBWProfile인 프로필을 수정합니다. BWPolicy 매개 변수를 사용하여 프로필 내 정책 목록을 수정합니다. 이 매개 변수에 전달한 @{add=$ap} 값을 보십시오. 이는 Windows PowerShell에서 목록에 무언가를 추가할 수 있는 방법입니다. 맨 앞에 @ 기호를 입력한 다음 중괄호({})를 입력합니다. 이 중괄호 안에 목록에 대해 수행할 작업을 지정합니다. 이 경우에는 목록에 추가하는 작업입니다. 제거 또는 대체 작업을 수행할 수도 있습니다. add 작업 뒤에 등호를 입력한 후 목록에 추가할 개체를 입력합니다. 이 경우에는 $ap 변수에 저장한 새 정책입니다.

    $ap = New-CsNetworkBWPolicy -BWLimit 2000 -BWSessionLimit 300 -BWPolicyModality audio
    Set-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile -BWPolicy @{add=$ap}

## 자세한 정보

CAC(통화 허용 제어)의 일부로 특정 형식의 대역폭 제한을 정의하기 위해 대역폭 정책이 사용됩니다. Lync Server에서는 오디오 및 비디오 형식에만 대역폭 제한을 할당할 수 있습니다. 이 cmdlet은 이러한 정책의 컨테이너 프로필을 수정합니다.

중요: 프로필에 여러 정책이 포함된 경우(예: 오디오 정책 하나와 비디오 정책 하나) AudioBWLimit, AudioBWSessionLimit, VideoBWLimit 또는 VideoBWSessionLimit 속성을 사용하여 프로필을 수정하면 프로필의 모든 기존 정책이 제거되고 새 값으로 대체됩니다. 프로필에 비디오를 제한하는 정책이 포함되어 있고 AudioBWLimit 매개 변수만 설정한 경우 비디오 정책이 제거되고 오디오 정책이 생성됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkBandwidthPolicyProfile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkBandwidthPolicyProfile"}

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
<td><p><em>AudioBWLimit</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>모든 오디오 연결에 할당할 최대 대역폭 크기입니다. 단일 오디오 세션이 오디오 대역폭 제한을 초과할 경우 해당 세션은 시작되지 않습니다.</p>
<p>kbps 단위로 표현됩니다. 예를 들어 1000 값은 1000kbps를 나타냅니다.</p>
<p>이 매개 변수에 값을 지정하는 경우 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: AudioBWSessionLimit 매개 변수에 값을 지정하고 AudioBWLimit에 값을 지정하지 않으면 AudioBWLimit의 기본값은 0이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBWSessionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>오디오 세션별로 할당할 최대 대역폭 크기입니다. kbps 단위로 표현됩니다. 값은 40 이상이어야 합니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: AudioBWLimit 매개 변수에 값을 지정하고 AudioBWSessionLimit에 값을 지정하지 않으면 AudioBWSessionLimit의 기본값은 175가 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>대역폭 정책 프로필이 포함된 개체 목록입니다. 이 목록의 각 개체는 대역폭 형식(오디오 또는 비디오), 대역폭 제한 및 대역폭 세션 제한으로 구성됩니다.</p>
<p>이 매개 변수에 값을 지정하는 경우 AudioBWLimit, AudioBWSessionLimit, VideoBWLimit 또는 VideoBWSessionLimit 매개 변수에 값을 지정할 수 없습니다.</p>
<p>이 목록의 개체는 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType 유형이어야 합니다. 이러한 유형의 개체는 <strong>New-CsNetworkBWPolicy</strong> cmdlet을 호출하여 만들 수 있으며 결과 정책을 이 매개 변수의 값으로 할당하여 프로필에 추가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>대역폭 정책 프로필에 대한 설명입니다. 예를 들어 이 매개 변수를 사용하여 프로필의 예상 용도를 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 프롬프트를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>수정할 대역폭 정책 프로필을 고유하게 식별하는 문자열 값입니다. 이는 프로필의 BWPolicyProfileID 속성과 동일하며 이 값을 변경하려면 해당 속성의 값을 변경해야 합니다. &quot;잘라내서 붙여넣기&quot; 작업과 동일합니다. 프로필의 모든 속성이 그대로 유지되고 이름만 변경됩니다. 그러나 프로필이 네트워크 사이트에 할당된 경우 이 값을 변경할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>BW 정책 프로필 유형</p></td>
<td><p>프로필을 수정하는 데 사용할 설정이 포함된 대역폭 정책 프로필 개체(Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 유형의 개체)에 대한 참조입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 이 개체를 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoBWLimit</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>모든 비디오 연결에 할당할 최대 대역폭 크기입니다. 단일 비디오 세션이 비디오 대역폭 제한을 초과할 경우 해당 세션은 시작되지 않습니다.</p>
<p>kbps 단위로 표현됩니다. 예를 들어 1000 값은 1000kbps를 나타냅니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: VideoBWSessionLimit 매개 변수에 값을 지정하고 VideoBWLimit에 값을 지정하지 않으면 VideoBWLimit의 기본값은 0이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBWSessionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>비디오 세션별로 할당할 최대 대역폭 크기입니다. kbps 단위로 표현됩니다. 값은 100 이상이어야 합니다.</p>
<p>이 매개 변수에 값을 지정하는 경우 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: VideoBWLimit 매개 변수에 값을 지정하고 VideoBWSessionLimit에 값을 지정하지 않으면 VideoBWSessionLimit의 기본값은 700이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 개체입니다. 네트워크 대역폭 정책 프로필 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)

