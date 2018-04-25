---
title: New-CsNetworkRegion
TOCTitle: New-CsNetworkRegion
ms:assetid: 33a8efed-23d3-4a03-bede-80f649eaa7b9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425829(v=OCS.15)
ms:contentKeyID: 49303252
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 네트워크 영역을 만듭니다. 네트워크 영역은 엔터프라이즈 네트워크의 네트워크 허브 또는 백본을 나타냅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkRegion -NetworkRegionID <String> <COMMON PARAMETERS>

    New-CsNetworkRegion -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -CentralSite <String> [-AudioAlternatePath <$true | $false>] [-BWAlternatePaths <PSListModifier>] [-BypassID <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-VideoAlternatePath <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 NorthAmerica라는 새 네트워크 영역을 만듭니다. 영역 이름이 Identity 매개 변수의 값으로 지정됩니다. 선택적 Description 매개 변수의 값도 지정되며, 이 영역이 "All North American Locations"로 구성되어 있다고 설명합니다. 마지막으로, CentralSite 매개 변수는 Redmond-NA-MLS 영역에 대한 중앙 사이트의 이름 값을 받습니다.

    New-CsNetworkRegion -Identity NorthAmerica -Description "All North American Locations" -CentralSite Redmond-NA-MLS

## 예제 2

이 예제에서는 오디오 대체 경로 설정이 포함된 새 네트워크 영역을 EMEA라는 이름으로 만듭니다. 이 작업을 수행하기 위해 EMEA라는 Identity를 전달하여 **New-CsNetworkRegion** cmdlet을 호출합니다. 필수 매개 변수인 CentralSite의 값을 할당한 다음(이 예제에서 이 영역의 중앙 사이트 이름은 Dublin-EU-Site임), AudioAlternatePath 매개 변수를 지정하고 값 $False를 전달합니다. AudioAlternatePath를 False로 설정하면 적절한 대역폭을 사용할 수 없는 경우 오디오 통화가 대체 경로로 경로 지정되지 않고 완료되지 않습니다.

    New-CsNetworkRegion -Identity EMEA -CentralSite Dublin-EU-Site -AudioAlternatePath $False

## 예제 3

이 예제에서는 예제 2에서 만든 것과 동일한 네트워크 영역을 만들지만, 이 경우 AudioAlternatePath 매개 변수 대신 BWAlternatePaths 매개 변수를 사용하여 대체 경로 설정을 정의합니다. 예제의 첫 번째 줄에서는 **New-CsNetworkBWAlternatePath** cmdlet을 호출하여 새 대체 경로를 만듭니다. 대체 경로에는 audio 또는 video로 설정해야 하는 BWPolicyModality(이 예제에서는 audio)와 True 또는 False여야 하는 AlternatePath(이 예제에서는 False), 두 개의 속성만 있습니다. 방금 만든 대체 경로 개체에 대한 참조인 이 cmdlet의 출력을 $a 변수에 할당합니다.

이 예제의 둘째 줄에서 새 네트워크 영역을 만들 때 새로 만든 대체 경로를 사용합니다. 이 작업을 수행하기 위해 EMEA라는 Identity를 전달하여 **New-CsNetworkRegion** cmdlet을 호출합니다. 필수 매개 변수인 CentralSite의 값을 할당한 다음(이 예제에서 이 영역의 중앙 사이트 이름은 Dublin-EU-Site임), BWAlternatePaths 매개 변수를 지정하고 방금 만든 대체 경로 개체가 포함된 변수($a)를 전달합니다.

    $a = New-CsNetworkBWAlternatePath -BWPolicyModality "audio" -AlternatePath $False
    New-CsNetworkRegion -Identity EMEA -CentralSite Dublin-EU-Site -BWAlternatePaths $a

## 자세한 정보

네트워크 영역은 여러 지역의 많은 네트워크 부분을 교차합니다. 모든 네트워크 영역은 중앙 사이트와 연결되어 있어야 합니다. 중앙 사이트는 CAC(통화 허용 제어) 대역폭 정책 서비스가 실행되는 데이터 센터 사이트입니다. 이 cmdlet을 사용하여 새 네트워크 영역을 만들 수 있습니다. 이 cmdlet의 매개 변수를 사용하면 인터넷을 통한 대체 경로가 오디오 및 비디오 연결에 허용되는지 여부를 결정하고 바이패스 ID를 자동으로 생성할 수 있는 설정을 제공할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkRegion** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkRegion"}

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
<td><p><em>CentralSite</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>대역폭 정책 서비스를 실행 중인 중앙 사이트입니다. CAC를 사용하려면 이 서비스를 활성화해야 합니다. 이 서비스는 프런트 엔드 서버 또는 Standard Edition 서버에서 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>새로 만든 네트워크 영역의 고유 식별자입니다. 영역은 전역 범위에서만 만들어지므로 이 식별자에서 범위를 지정할 필요가 없습니다. 대신 해당 영역을 식별하는 고유 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 값은 Identity와 같습니다. Identity와 NetworkRegionID를 모두 지정할 수 없습니다. 한 매개 변수에 대해 입력한 값이 자동으로 둘 다에 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioAlternatePath</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 기본 경로에 적절한 대역폭이 없는 경우 대체 경로를 통해 오디오 통화를 경로 지정할지 여부를 결정하며,</p>
<p>BWAlternatePaths 속성을 채웁니다. 이 매개 변수에 제공된 값은 Audio의 BWPolicyModality 값으로 대체 경로 요소의 AlternatePath 값에 저장됩니다.</p>
<p>이 매개 변수 값을 제공한 경우에는 BWAlternatePaths 매개 변수 값을 지정할 수 없습니다.</p>
<p>기본값: True. 인터넷으로 오프로드를 해제해야 하는 경우에만 이 매개 변수를 False로 설정합니다. 통화가 인터넷 통화인 경우 대역폭 설정에 관계없이 이 값은 True여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWAlternatePaths</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>기본 경로에서 미디어 요청을 완료할 수 없는 경우(예: 해당 경로의 제한을 초과한 경우) 대체 인터넷 연결 경로를 사용할 수 있는지 여부에 대한 정보가 포함된 개체 목록입니다. 대체 경로 개체를 만들려면 <strong>New-CsNetworkBWAlternatePath</strong> cmdlet을 호출해야 합니다.</p>
<p>이 매개 변수의 값을 지정하는 경우 AudioAlternatePath 또는 VideoAlternatePath 매개 변수에는 값을 지정할 수 없습니다.</p>
<p>오디오 및 비디오의 대체 경로는 기본적으로 활성화되어 있습니다(AlternatePath = True).</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>GUID(Globally Unique Identifier)입니다. 이 GUID는 네트워크 지역을 CAC 또는 E9-1-1(Enhanced 9-1-1) 네트워크 구성 내의 미디어 우회 설정에 매핑하는 데 사용됩니다. <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet을 호출할 때 이 BypassID 값을 사용합니다.</p>
<p>이 매개 변수의 값을 지정하지 않으면 값이 자동으로 생성됩니다. 값을 지정하는 경우 GUID 형식을 사용해야 합니다(예: 3b24a047-dce6-48b2-9f20-9fbff17ed62a). 자동 생성하는 것이 좋습니다. 이 매개 변수의 값을 지정하면 자동으로 값을 생성하는 대신 이 값을 지정할 것인지 확인하는 확인 메시지가 표시됩니다.</p></td>
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
<td><p>영역을 설명하는 문자열입니다. 이 매개 변수를 사용하여 ID만으로 표시할 때보다 지역의 용도에 대해 자세한 설명을 제공할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다. 예를 들어 BypassID 매개 변수에 값을 제공하는 경우 확인 메시지가 표시되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoAlternatePath</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 기본 경로에 적절한 대역폭이 없는 경우 대체 경로를 통해 비디오 통화를 경로 지정할지 여부를 결정하며,</p>
<p>BWAlternatePaths 속성을 채웁니다. 이 매개 변수에 제공된 값은 Video의 BWPolicyModality 값으로 대체 경로 요소의 AlternatePath 값에 저장됩니다.</p>
<p>이 매개 변수 값을 제공한 경우에는 BWAlternatePaths 매개 변수 값을 지정할 수 없습니다.</p>
<p>기본값: True. 인터넷으로 오프로드를 해제해야 하는 경우에만 이 매개 변수를 False로 설정합니다. 통화가 인터넷 통화인 경우 대역폭 설정에 관계없이 이 값은 True여야 합니다.</p></td>
</tr>
<tr class="even">
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[New-CsNetworkBWAlternatePath](new-csnetworkbwalternatepath.md)

