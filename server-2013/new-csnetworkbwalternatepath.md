---
title: New-CsNetworkBWAlternatePath
TOCTitle: New-CsNetworkBWAlternatePath
ms:assetid: 9017378e-4583-42bc-9572-aa8e9571cfe3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398732(v=OCS.15)
ms:contentKeyID: 49304366
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBWAlternatePath

 

_**마지막으로 수정된 항목:** 2015-03-09_

대역폭이 제한적인 연결에 대해 인터넷을 통해 대체 경로로 미디어를 경로 지정할 수 있는지 여부를 정의하는 새 설정을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkBWAlternatePath -AlternatePath <$true | $false> -BWPolicyModality <Audio | Video>

## 예제

## 예제 1

이 예제에서는 새 네트워크 대역폭 대체 경로를 만들고 새로 만들어진 지역에 이러한 설정을 할당합니다. 예제의 첫 번째 줄에서는 **New-CsNetworkBWAlternatePath** cmdlet을 호출하여 새 대체 경로를 만듭니다. 대체 경로에는 audio 또는 video로 설정해야 하는 BWPolicyModality(이 예제에서는 audio가 사용됨)와 True 또는 False여야 하는 AlternatePath(이 예제에서는 True가 사용됨), 두 개의 속성만 있습니다. 이 cmdlet의 결과(방금 만들어진 대체 경로에 대한 참조)를 변수 $a에 할당합니다.

이 예제의 두 번째 줄에서는 새 네트워크 지역을 만들면서 이렇게 새로 만들어진 대체 경로를 사용합니다. 이 작업을 수행하기 위해 **New-CsNetworkRegion** cmdlet을 호출하고 NorthAmerica라는 ID를 전달합니다. 필수 매개 변수 CentralSite에 대한 값을 할당한 다음(이 예제에서 이 지역에 대한 중앙 사이트의 이름은 Redmond-NA-MLS임) BWAlternatePaths 매개 변수를 지정하고 여기에 방금 만든 대체 경로 개체가 포함된 변수($a)를 전달합니다.

    $a = New-CsNetworkBWAlternatePath -BWPolicyModality "audio" -AlternatePath $true
    New-CsNetworkRegion -Identity NorthAmerica -CentralSite Redmond-NA-MLS -BWAlternatePaths $a

## 자세한 정보

Lync Server의 CAC(통화 허용 제어) 구성 내에는 두 가지 가능한 형식인 오디오와 비디오가 있습니다. 이러한 각 형식에 대해 대역폭 제한을 설정할 수 있습니다. 대역폭 제한으로 인해 통화를 수행할 수 없는 경우 해당 통화에서 인터넷을 통해 통화 연결이 가능한 대체 경로를 사용할 수 있습니다. 이 cmdlet을 사용하면 형식을 기반으로 인터넷을 통해 대체 경로로 통화를 경로 지정할 수 있는지 여부를 정의하는 설정을 만들 수 있습니다. 이 설정은 CAC 구성 내에서 지역별로 적용됩니다.

이 cmdlet은 새로 만들어진 설정을 바로 저장하지는 않고, 메모리에 설정을 만듭니다. 네트워크 내 지역에 이러한 설정을 적용하려면 이 cmdlet의 출력을 변수에 할당한 다음 이 변수를 **New-CsNetworkRegion** cmdlet 또는 **Set-CsNetworkRegion** cmdlet의 BWAlternatePaths 매개 변수 값으로 사용해야 합니다. **New-CsNetworkRegion** cmdlet 및 **Set-CsNetworkRegion** cmdlet의 AudioAlternatePath 및 VideoAlternatePath 매개 변수를 사용하면 **New-CsNetworkBWAlternatePath** cmdlet을 호출하여 새 개체를 만들 필요 없이 이러한 설정을 직접 적용할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkBWAlternatePath** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWAlternatePath"}

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
<td><p><em>AlternatePath</em></p></td>
<td><p>필수</p></td>
<td><p>부울</p></td>
<td><p>기본 경로에 충분한 대역폭이 없는 경우 BWPolicyModality 매개 변수에 지정된 형식의 미디어에서 수행된 통화를 대체 경로를 통해 경로 지정할 수 있도록 허용하려면 이 매개 변수를 True로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>필수</p></td>
<td><p>BW 정책 형식</p></td>
<td><p>대체 경로 설정을 적용할 형식입니다.</p>
<p>유효한 값: audio, video</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)

