---
title: New-CsNetworkBandwidthPolicyProfile
TOCTitle: New-CsNetworkBandwidthPolicyProfile
ms:assetid: 84940891-37a6-45fc-972d-05b95aa71ba9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398675(v=OCS.15)
ms:contentKeyID: 49304252
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBandwidthPolicyProfile

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 네트워크 대역폭 정책 프로필을 만듭니다. 이 cmdlet은 프로필 내의 대역폭 정책을 설정하는 데 사용할 수도 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 LowBWLimits라는 새 대역폭 정책 프로필을 만듭니다. 이 새 프로필에는 오디오 정책과 비디오 정책, 두 개의 정책이 할당됩니다(Lync Server에서 이 두 정책만 사용 가능). AudioBWLimit 매개 변수로 전체 오디오 연결에 대해 제한을 할당(이 경우 2000kbps)하고, AudioBWSessionLimit 매개 변수로 개별 오디오 세션에 대한 제한 200kbps를 할당하여 프로필에 오디오 정책을 추가합니다. 동일한 작업으로 비디오 세션 제한을 만듭니다. 단, VideoBWLimit 및 VideoBWSessionLimit 매개 변수를 사용합니다.

    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimits -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400 -VideoBWSessionLimit 500

## 자세한 정보

대역폭 정책은 CAC(통화 허용 제어)의 일부로 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Lync Server에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 이 cmdlet은 이러한 정책에 대한 컨테이너 프로필을 만듭니다. 이 cmdlet을 호출할 때 오디오 및 비디오 대역폭 제한을 지정하여 컨테이너 내에 개별 정책을 정의합니다.

대역폭 정책 프로필은 **New-CsNetworkSite** cmdlet 또는 **Set-CsNetworkSite** cmdlet을 호출하여 네트워크 사이트에 적용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkBandwidthPolicyProfile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBandwidthPolicyProfile"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>정책을 고유하게 식별하는 문자열 값입니다. 모든 대역폭 정책 프로필은 전역 범위에서 만들어집니다. 따라서 범위는 내포되어 있으므로 새 대역폭 정책 프로필을 만들 때 고유한 이름만 지정하면 됩니다. 프로필의 BWPolicyProfileID 속성도 이 값으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBWLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모든 오디오 연결에 대해 할당할 최대 대역폭 크기입니다. 하나의 오디오 세션으로 인해 오디오 대역폭 제한이 초과될 경우 해당 세션은 시작이 허용되지 않습니다.</p>
<p>단위는 kbps입니다. 예를 들어 1000 값은 1000kbps를 나타냅니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: AudioBWSessionLimit 매개 변수에 값을 지정하고 AudioBWLimit에 값을 지정하지 않으면 AudioBWLimit의 기본값은 0이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioBWSessionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 세션별로 할당할 최대 대역폭 크기입니다. 단위는 kbps입니다. 값은 40 이상이어야 합니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: AudioBWLimit 매개 변수에 값을 지정하고 AudioBWSessionLimit에 값을 지정하지 않으면 AudioBWSessionLimit의 기본값은 175가 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>대역폭 정책 프로필이 포함된 개체의 목록입니다. 목록의 각 개체는 대역폭 형식(오디오 또는 비디오), 대역폭 제한 및 대역폭 세션 제한으로 구성됩니다.</p>
<p>이 매개 변수에 값을 지정하면 AudioBWLimit, AudioBWSessionLimit, VideoBWLimit 또는 VideoBWSessionLimit 매개 변수에 값을 지정할 수 없습니다.</p>
<p><strong>New-CsNetworkBWPolicy</strong> cmdlet을 호출하면 목록의 개체를 만들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>대역폭 정책 프로필에 대한 설명입니다. 예를 들어 이 매개 변수를 사용하여 프로필의 용도를 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoBWLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모든 비디오 연결에 대해 할당할 최대 대역폭 크기입니다. 하나의 비디오 세션으로 인해 비디오 대역폭 제한이 초과될 경우 해당 세션은 시작이 허용되지 않습니다.</p>
<p>단위는 kbps입니다. 예를 들어 1000 값은 1000kbps를 나타냅니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: VideoBWSessionLimit 매개 변수에 값을 지정하고 VideoBWLimit에 값을 지정하지 않으면 VideoBWLimit의 기본값은 0이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBWSessionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>비디오 세션별로 할당할 최대 대역폭 크기입니다. 단위는 kbps입니다. 값은 100 이상이어야 합니다.</p>
<p>이 매개 변수에 값을 지정하면 BWPolicy 매개 변수에 값을 지정할 수 없습니다.</p>
<p>기본값: VideoBWLimit 매개 변수에 값을 지정하고 VideoBWSessionLimit에 값을 지정하지 않으면 VideoBWSessionLimit의 기본값은 700이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)

