---
title: New-CsNetworkSubnet
TOCTitle: New-CsNetworkSubnet
ms:assetid: 15af44bd-d798-435c-9c27-df47ab475023
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398226(v=OCS.15)
ms:contentKeyID: 49302910
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 네트워크 서브넷을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkSubnet -SubnetID <String> <COMMON PARAMETERS>

    New-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -MaskBits <Int32> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-NetworkSiteID <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 172.11.15.0/24 서브넷을 나타내는 새 서브넷 개체를 만드는 방법을 보여 줍니다. 서브넷의 Identity는 172.11.15.0으로 설정됩니다. 이 값은 SubnetID로 자동으로 할당됩니다. 서브넷에 마스크 비트가 정의되어 있어야 합니다. 이렇게 하려면 MaskBits 매개 변수에 값(이 경우 24)을 지정합니다. 마지막으로, 사이트 ID Vancouver가 NetworkSiteID 매개 변수에 전달되어 이 서브넷을 해당 사이트와 연결합니다.

    New-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 24 -NetworkSiteID Vancouver

## 예제 2

예제 2에서는 CSV 파일을 읽어 일련의 서브넷을 만듭니다. 이 예제의 CSV 파일은 다음과 유사합니다.

Identity, Mask, SiteID

172.11.12.0, 24, Redmond

172.11.13.0, 24, Chicago

172.11.14.0, 25, Vancouver

172.11.15.0, 31, Paris

...

이 예제에서는 먼저 CSV 파일의 경로를 전달하여 **Import-CSV** cmdlet을 호출합니다. 이 cmdlet은 해당 파일의 내용을 메모리로 읽어옵니다. 이러한 파일 내용은 foreach 함수에 파이프됩니다. foreach 함수는 한 번에 한 줄씩 내용을 반복합니다. 예제 파일에서 볼 수 있듯이, 첫째 줄은 나머지 내용을 정의하는 제목 목록입니다. foreach 함수는 이러한 제목을 사용하여 쉼표로 구분된 값을 이름으로 액세스합니다.

foreach 문 내에서 **New-CsNetworkSubnet** cmdlet이 호출됩니다. foreach는 파일 내용의 각 줄을 반복하므로 해당 줄이 **New-CsNetworkSubnet** cmdlet 매개 변수의 값으로 전달됩니다. 예를 들어 foreach 문을 처음 수행할 때 **New-CsNetworkSubnet** cmdlet은 Identity가 172.11.12.0인 서브넷을 만듭니다. 이 값은 쉼표로 구분된 값의 첫째 줄에서 Identity 위치에 있는 값입니다. $\_은 foreach 루프의 현재 값을 나타냅니다. 그런 다음 Mask 값(24)이 MaskBits 매개 변수에 전달되고 파일의 SiteID 값(Redmond)이 NetworkSiteID 매개 변수에 전달됩니다.

이 프로세스는 파일의 모든 줄을 읽고 해당 값이 새 서브넷을 만드는 데 사용될 때까지 계속됩니다.

    Import-CSV C:\subnet.csv | foreach {New-CsNetworkSubnet -Identity $_.Identity -MaskBits $_.Mask -NetworkSiteID $_.SiteID}

## 자세한 정보

각 서브넷은 해당 서브넷에 속한 호스트의 지리적 위치를 확인할 수 있도록 네트워크 사이트에 연결되어야 합니다. 이 cmdlet을 사용하여 새 서브넷을 만들고, 이와 동시에 선택적으로 네트워크 사이트에 할당할 수 있습니다.

CAC(통화 허용 제어)를 구현하는 대부분의 Lync Server 배포에는 일반적으로 많은 서브넷이 있습니다. 따라서 **Import-CSV** cmdlet과 함께 **New-CsNetworkSubnet** cmdlet을 호출하는 것이 좋습니다. 두 cmdlet을 함께 사용하면 CSV(쉼표로 구분된 값) 파일에서 서브넷 설정을 읽어와서 여러 개의 서브넷을 동시에 만들 수 있습니다. 자세한 내용은 이 cmdlet에 대한 예제 섹션을 참고하세요.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkSubnet"}

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
<td><p>만들 서브넷의 고유 서브넷 ID입니다. 이 ID는 IP 주소(예: 174.11.12.0)여야 하며 서브넷으로 정의된 IP 주소 범위의 첫 번째 주소여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaskBits</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>만들 서브넷에 적용할 비트마스크입니다.</p>
<p>유효한 값: 1 ~ 32</p></td>
</tr>
<tr class="odd">
<td><p><em>SubnetID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수 값은 Identity와 같습니다. Identity 또는 SubnetID 중 한 개만 지정해야 하며 둘 다 지정할 수 없습니다. 한 매개 변수에 값을 지정하면 다른 매개 변수에 해당 값이 자동으로 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>만들 서브넷에 대한 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 서브넷이 속해 있는 사이트의 사이트 ID입니다. <strong>Get-CsNetworkSite</strong> cmdlet을 호출하여 배포에 사용할 사이트 ID를 검색할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkSite](get-csnetworksite.md)

