---
title: Set-CsClientVersionConfiguration
TOCTitle: Set-CsClientVersionConfiguration
ms:assetid: 7cd2e86f-2d31-4db2-9d0f-f1418fd4aba2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398623(v=OCS.15)
ms:contentKeyID: 49304159
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientVersionConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

클라이언트 버전 구성 설정의 지정된 컬렉션을 수정합니다. 클라이언트 버전 구성 설정은 Lync Server에서 시스템에 로그온하는 각 클라이언트 응용 프로그램의 버전 번호를 확인할지 여부를 결정합니다. 클라이언트 버전 필터링을 설정한 경우에는 해당 클라이언트 버전 정책에 구성된 설정에 따라 클라이언트 응용 프로그램에서 시스템에 액세스할 수 있는지 여부가 결정됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientVersionConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsClientVersionConfiguration** cmdlet을 사용하여 ID가 "site:Redmond"인 설정 컬렉션을 수정합니다. 이 경우 Enabled 매개 변수를 False로 설정하여 클라이언트 버전 구성 설정을 비활성화합니다.

    Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False

## 예제 2

예제 2에서는 조직에서 현재 사용되고 있는 모든 클라이언트 버전 구성 설정에 대한 DefaultUrl 속성을 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 추가 매개 변수 없이 **Get-CsClientVersionConfiguration** cmdlet을 호출하여 모든 클라이언트 버전 구성 설정을 반환합니다. 이 정보는 각 구성 컬렉션의 DefaultUrl 값을 https://litwareinc.com/csclients로 설정하는 **Set-CsClientVersionConfiguration** cmdlet에 파이프됩니다.

    Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"

## 예제 3

예제 3에서는 DefaultAction이 현재 Block으로 설정된 모든 클라이언트 버전 구성 설정을 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsClientVersionConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 클라이언트 버전 구성 설정 컬렉션을 반환합니다. 이 정보는 DefaultAction 속성이 "Block"과 같은 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대해 다음 두 작업을 수행하는 **Set-CsClientVersionConfiguration** cmdlet에 파이프됩니다. 1) DefaultAction을 BlockWithUrl로 설정, 2) DefaultUrl을 https://litwareinc.com/csclients로 설정

    Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block"} | Set-CsClientVersionConfiguration -DefaultAction "BlockWithUrl" -DefaultURL "https://litwareinc.com/csclients"

## 자세한 정보

Lync Server에서는 사용자가 시스템에 로그온하는 데 사용할 수 있는 클라이언트 소프트웨어 및 해당 소프트웨어의 버전 번호를 지정할 때 관리자에게 많은 선택권을 제공합니다. 예를 들어 사용자가 Lync를 사용하여 Lync Server에 로그온해야 하는 기술적인 이유는 없습니다. 기술적인 면에서는 Microsoft Office Communicator 2007 R2를 사용하여 로그온할 수도 있습니다.

그러나 사용자가 Office Communicator 2007 R2를 사용하여 로그온하지 않도록 하는 것이 좋은 몇 가지 비기술적인 이유가 있을 수 있습니다. 예를 들어 Office Communicator 2007 R2는 Lync에서 제공하는 일부 기능을 지원하지 않으므로 Office Communicator 2007 R2를 사용하여 로그온한 사용자에게는 Lync를 사용하여 로그온한 사용자와 다른 환경이 제공됩니다. 이 경우 사용자뿐만 아니라 여러 클라이언트 응용 프로그램에 대한 지원을 제공해야 하는 지원 센터 담당자도 곤란한 상황에 처할 수 있습니다.

이러한 점이 조직에 문제가 되는 경우 클라이언트 버전 필터링을 사용하여 Lync Server에 로그온하는 데 사용할 수 있는 클라이언트 응용 프로그램을 지정할 수 있습니다. Lync Server를 설치하면 전체 클라이언트 버전 구성 설정 집합이 설치되고 사용하도록 설정됩니다. 이러한 설정은 클라이언트 버전 필터링을 사용할지 여부를 결정하는 데 사용됩니다. 이러한 전역 설정 외에 사이트 범위에 클라이언트 버전 구성 설정을 적용할 수 있습니다. 이 경우 사이트 설정이 전역 설정보다 우선합니다.

**Set-CsClientVersionConfiguration** cmdlet을 사용하면 클라이언트 버전 구성 설정의 기존 컬렉션을 수정할 수 있습니다.

클라이언트 버전 구성은 보안 기능이 아닙니다. 이 기술은 클라이언트 응용 프로그램의 자체 보고를 기반으로 하며, 응용 프로그램이 실제 해당 응용 프로그램인지, 이 응용 프로그램의 버전 번호가 올바른지 등을 확인하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsClientVersionConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientVersionConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction</p></td>
<td><p>사용자가 해당 클라이언트 버전 정책에서 버전 번호를 찾을 수 없는 클라이언트 응용 프로그램에서 로그온하려는 경우에 수행할 작업을 나타냅니다. DefaultAction은 다음 값 중 하나로 설정해야 합니다.</p>
<p>Allow. 클라이언트 응용 프로그램의 로그온이 허용됩니다.</p>
<p>AllowWithUrl. 클라이언트 응용 프로그램의 로그온이 허용됩니다. 또한 사용자가 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL이 포함된 메시지 상자가 표시됩니다. 이 웹 페이지의 URL은 DefaultUrl 속성 값으로 지정해야 합니다.</p>
<p>Block. 클라이언트 응용 프로그램의 로그온이 차단됩니다.</p>
<p>BlockWithUrl. 클라이언트 응용 프로그램의 로그온이 차단됩니다. 그러나 사용자에게 표시되는 &quot;액세스 거부&quot; 메시지 상자에 해당 사용자가 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL이 포함됩니다. 이 웹 페이지의 URL은 DefaultUrl 속성 값으로 지정해야 합니다.</p>
<p>Enabled 속성이 False로 설정된 경우에는 이 속성이 무시됩니다. 즉, Enabled 속성을 False로 설정하면 어떤 종류의 클라이언트 버전 필터링도 수행되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL을 지정합니다. URL을 지정하고 DefaultAction을 BlockWithURL로 설정하면 사용자가 지원되지 않는 클라이언트 응용 프로그램에서 로그온하려고 할 때마다 나타나는 &quot;액세스 거부&quot; 메시지 상자에 이 URL이 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>클라이언트 버전 필터링의 사용 여부를 나타냅니다. Enabled 속성이 True인 경우 서버는 로그온을 시도하는 각 클라이언트 응용 프로그램의 버전 번호를 확인합니다. 그런 다음 서버는 해당 클라이언트 버전 정책에 따라 액세스를 허용하거나 거부합니다. Enabled 속성이 False이면 로그온할 수 있는 모든 클라이언트 응용 프로그램의 로그온이 허용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 클라이언트 버전 구성 설정의 고유 식별자를 나타냅니다. 전역 설정을 수정하려면 -Identity global과 같은 구문을 사용합니다. 사이트 범위에 할당된 설정을 수정하려면 &quot;site:Redmond&quot;와 같은 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsClientVersionConfiguration</strong> cmdlet이 전역 설정을 자동으로 구성합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>ClientVersionPolicy 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체입니다. **Set-CsClientVersionConfiguration** cmdlet은 클라이언트 버전 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsClientVersionConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)

