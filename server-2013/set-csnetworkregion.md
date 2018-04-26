---
title: Set-CsNetworkRegion
TOCTitle: Set-CsNetworkRegion
ms:assetid: ffa1774b-ac60-4392-ad55-07bb887bf945
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413089(v=OCS.15)
ms:contentKeyID: 49305655
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 네트워크 지역을 수정합니다. 네트워크 지역은 엔터프라이즈 네트워크에서 네트워크 허브 또는 백본을 나타냅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkRegion [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AudioAlternatePath <$true | $false>] [-BWAlternatePaths <PSListModifier>] [-BypassID <String>] [-CentralSite <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-VideoAlternatePath <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 NorthAmerica라는 네트워크 지역을 수정합니다. Description 매개 변수에는 "North American Region" 값을 지정합니다. 이 명령은 NorthAmerica 지역에 Description이 있는 경우 이 값으로 해당 Description을 덮어쓰고, 설정된 Description이 없는 경우 Description을 설정합니다.

    Set-CsNetworkRegion -Identity NorthAmerica -Description "North American Region"

## 예제 2

이 예제에서는 EMEA라는 네트워크 지역을 수정하고 새 비디오 대체 경로 설정을 제공합니다. 이 작업을 수행하기 위해 **Set-CsNetworkRegion** cmdlet을 호출하고 Identity(EMEA)를 전달합니다. 그런 다음 VideoAlternatePath 매개 변수를 지정하고 $False 값을 전달합니다. VideoAlternatePath를 False로 설정하면 적절한 대역폭을 사용할 수 없는 경우 비디오 통화가 대체 경로로 경로 지정되지 않고 완료되지 않습니다.

    Set-CsNetworkRegion -Identity EMEA -VideoAlternatePath $False

## 예제 3

예제 3에서는 NorthAmerica 지역에 설정된 것과 동일한 대체 경로 설정 집합을 Asia 네트워크 지역에 할당합니다. 이 예제의 첫째 줄은 NorthAmerica 네트워크 지역의 인스턴스를 검색하여 $a 변수에 할당합니다. 둘째 줄은 먼저 $a 변수에 저장된 BWAlternatePaths 속성 또는 NorthAmerica 지역의 콘텐츠($a.BWAlternatePaths)를 검색합니다. 그러면 NorthAmerica 지역의 모든 대체 경로 설정 컬렉션이 반환됩니다.

이 설정 컬렉션을 foreach 함수에 파이프합니다. Foreach는 한 번에 하나씩 컬렉션의 항목을 확인하여 그 뒤의 중괄호에 있는 작업을 수행합니다. 이 경우에는 Identity가 Asia인 **Set-CsNetworkRegion** cmdlet을 호출하여 Asia 지역의 속성을 설정합니다. 다음 매개 변수는 BWAlternatePaths입니다. 이 매개 변수에 @{add=$\_} 값을 전달합니다. $\_ 변수는 컬렉션의 현재 항목(여기서는 현재 대체 경로)을 나타내고, 값의 @{add=} 부분은 이 항목을 Asia 지역의 BWAlternatePaths 컬렉션에 추가합니다.

    $a = Get-CsNetworkRegion -Identity NorthAmerica
    $a.BWAlternatePaths | foreach {Set-CsNetworkRegion -Identity Asia -BWAlternatePaths @{add=$_}}

## 자세한 정보

네트워크 지역은 여러 지역의 많은 네트워크 부분을 교차합니다. 모든 네트워크 지역은 중앙 사이트와 연결되어 있어야 합니다. 중앙 사이트는 CAC(통화 허용 제어) 대역폭 정책 서비스가 실행되는 데이터 센터 사이트입니다. 이 cmdlet을 사용하면 오디오 및 비디오 연결에 대체 경로가 허용되는지 여부를 결정하는 설정, 지역 내의 사이트를 미디어 우회 구성과 연결하는 설정 등을 포함하여 기존 네트워크 지역을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkRegion** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkRegion\\b"}

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
<td><p><em>AudioAlternatePath</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수는 기본 경로에 적절한 대역폭이 없는 경우 대체 경로를 통해 오디오 통화를 경로 지정할지 여부를 결정하며,</p>
<p>BWAlternatePaths 속성을 채웁니다. 이 매개 변수에 제공된 값은 Audio의 BWPolicyModality 값으로 대체 경로 요소의 AlternatePath 값에 저장됩니다.</p>
<p>이 매개 변수 값을 제공한 경우에는 BWAlternatePaths 매개 변수 값을 지정할 수 없습니다.</p>
<p>통화가 인터넷 통화인 경우 대역폭 설정에 관계없이 이 값은 True여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BWAlternatePaths</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>기본 경로를 따라 미디어 요청을 완료할 수 없는 경우(예: 해당 경로의 한도를 초과한 경우) 대체 연결 경로를 사용할 수 있는지 여부에 대한 정보가 포함된 개체 목록입니다. 대체 경로 개체의 유형은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType이어야 하며, <strong>New-CsNetworkBWAlternatePath</strong> cmdlet을 사용하여 이 유형의 개체를 만들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BypassID</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>GUID(Globally Unique Identifier)입니다. 이 GUID는 네트워크 지역을 CAC 또는 E9-1-1(Enhanced 9-1-1) 네트워크 구성 내의 미디어 우회 설정에 매핑하는 데 사용됩니다. <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet을 호출할 때 이 BypassID 값을 사용합니다.</p>
<p>이 매개 변수는 <strong>New-CsNetworkRegion</strong> cmdlet을 호출하여 지역을 만들 때 자동으로 생성될 수도 있습니다. 이 값은 변경하지 않는 것이 좋습니다. 그럼에도 불구하고 값을 지정하려면 GUID 형식(예: 3b24a047-dce6-48b2-9f20-9fbff17ed62a)을 사용해야 합니다. 이 경우 값을 수동으로 설정할지 확인하는 확인 메시지가 나타납니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CentralSite</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>대역폭 정책 서비스를 실행 중인 중앙 사이트입니다. CAC를 사용하려면 이 서비스를 활성화해야 합니다. 이 서비스는 프런트 엔드 서버 또는 Standard Edition 서버에서 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>영역을 설명하는 문자열입니다. 이 매개 변수를 사용하여 ID만으로 표시할 때보다 지역의 용도에 대해 자세한 설명을 제공할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>수정할 네트워크 지역의 고유 식별자입니다. ID는 해당 지역을 고유하게 식별하는 문자열 형식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>PS 개체</p></td>
<td><p>네트워크 지역 개체에 대한 참조입니다. 이 개체의 유형은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType이어야 하며, <strong>Get-CsNetworkRegion</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoAlternatePath</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수는 기본 경로에 적절한 대역폭이 없는 경우 대체 경로를 통해 비디오 통화를 경로 지정할지 여부를 결정하며,</p>
<p>BWAlternatePaths 속성을 채웁니다. 이 매개 변수에 제공된 값은 Video의 BWPolicyModality 값으로 대체 경로 요소의 AlternatePath 값에 저장됩니다.</p>
<p>이 매개 변수 값을 제공한 경우에는 BWAlternatePaths 매개 변수 값을 지정할 수 없습니다.</p>
<p>통화가 인터넷 통화인 경우 대역폭 설정에 관계없이 이 값은 True여야 합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 개체입니다. 네트워크 지역 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[New-CsNetworkBWAlternatePath](new-csnetworkbwalternatepath.md)

