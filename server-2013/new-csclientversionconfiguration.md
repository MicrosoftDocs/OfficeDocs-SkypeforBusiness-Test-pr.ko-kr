---
title: New-CsClientVersionConfiguration
TOCTitle: New-CsClientVersionConfiguration
ms:assetid: e7aac850-9e29-4d18-8929-74a89e9355cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399029(v=OCS.15)
ms:contentKeyID: 49305366
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientVersionConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

클라이언트 버전 구성 설정의 새 컬렉션을 만듭니다. 클라이언트 버전 구성 설정은 Lync Server에서 시스템에 로그온하는 각 클라이언트 응용 프로그램의 버전 번호를 확인할지 여부를 결정합니다. 클라이언트 버전 필터링을 설정한 경우에는 해당 클라이언트 버전 정책에 구성된 설정에 따라 클라이언트 응용 프로그램에서 시스템에 액세스할 수 있는지 여부가 결정됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대한 클라이언트 버전 구성 설정의 새 컬렉션을 만듭니다. 이 명령에서는 Enabled 매개 변수를 False로 설정합니다. 이는 Redmond 사이트에 대해 클라이언트 필터링을 사용하지 않음을 의미합니다.

    New-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False

## 예제 2

예제 2에서는 클라이언트 버전 구성 설정의 새 컬렉션을 메모리에 만들고 수정한 다음 이러한 가상 설정을 Redmond 사이트에 적용되는 실제 설정 컬렉션으로 전환하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsClientVersionConfiguration** cmdlet 및 InMemory 매개 변수를 사용하여 메모리에만 나타나는 ID가 site:Redmond인 설정 컬렉션을 만듭니다. 이 컬렉션은 $x라는 변수에 저장되고 메모리에만 존재합니다. 따라서 Windows PowerShell 세션을 종료하거나 $x 변수를 삭제하면 이러한 클라이언트 버전 구성 설정이 사라지고 Redmond 사이트에 적용되지 않습니다.

두 번째 명령에서는 가상 설정의 DefaultAction 속성 값을 Block으로 설정합니다. 그런 다음 세 번째 명령에서 **Set-CsClientVersionConfiguration** cmdlet을 사용하여 가상 설정을 Redmond 사이트에 적용되는 실제 클라이언트 버전 구성 설정 컬렉션으로 변환합니다.

    $x = New-CsClientVersionConfiguration -Identity site:Redmond -InMemory
    $x.DefaultAction = "Block" 
    Set-CsClientVersionConfiguration -Instance $x

## 자세한 정보

Lync Server에서는 사용자가 시스템에 로그온하는 데 사용할 수 있는 클라이언트 소프트웨어 및 해당 소프트웨어의 버전 번호를 지정할 때 관리자에게 많은 선택권을 제공합니다. 예를 들어 사용자가 Lync를 사용하여 Lync Server에 로그온해야 하는 기술적인 이유는 없습니다. 기술적인 면에서는 Microsoft Office Communicator 2007 R2를 사용하여 로그온할 수도 있습니다.

그러나 사용자가 Office Communicator 2007 R2를 사용하여 로그온하지 않도록 하는 것이 좋은 몇 가지 비기술적인 이유가 있을 수 있습니다. 예를 들어 Office Communicator 2007 R2는 Lync에서 제공하는 일부 기능을 지원하지 않으므로 Office Communicator 2007 R2를 사용하여 로그온한 사용자에게는 Lync를 사용하여 로그온한 사용자와 다른 환경이 제공됩니다. 이것은 사용자에게 문제가 될 수 있으며 다양한 클라이언트 응용 프로그램을 지원해야 하는 지원 센터 직원에게도 문제가 될 수 있습니다.

조직에 문제가 된다면 클라이언트 버전 필터링을 사용하여 Lync Server에 로그온하는 데 사용할 수 있는 클라이언트 응용 프로그램을 지정하면 됩니다. Lync Server를 설치하면 전체 클라이언트 버전 구성 설정 집합이 설치되고 사용하도록 설정됩니다. 이러한 설정은 클라이언트 버전 필터링을 사용할지 여부를 결정하는 데 사용됩니다.

**New-CsClientVersionConfiguration** cmdlet을 사용하면 전역 설정 외에도 사이트 범위에서 클라이언트 버전 구성 설정을 만들 수 있습니다. 클라이언트 버전 구성 설정이 사이트 범위에서 적용되면 이러한 설정이 전역 설정보다 우선합니다. 예를 들어 전역 범위에서 클라이언트 버전 필터링을 사용할 때 Redmond 사이트에 대해 클라이언트 버전 필터링을 사용하지 않는 별도의 설정 컬렉션을 만들면 Redmond 사이트의 계정을 가진 모든 사용자에 대해 클라이언트 버전 필터링이 사용되지 않도록 설정됩니다.

하지만 익명 사용자는 전역 정책을 통해서만 영향을 받습니다. 이는 익명 사용자가 사이트와 연결되어 있지 않기 때문입니다.

클라이언트 버전 구성은 보안 기능이 아닙니다. 이 기술은 클라이언트 응용 프로그램의 자체 보고를 기반으로 하며, 응용 프로그램이 실제 해당 응용 프로그램인지, 이 응용 프로그램의 버전 번호가 올바른지 등을 확인하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsClientVersionConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientVersionConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>클라이언트 버전 구성 설정의 새 컬렉션에 할당할 고유 식별자를 나타냅니다. 사이트 범위에서만 새 컬렉션을 생성할 수 있기 때문에 ID의 접두사는 항상 &quot;site:&quot;이며 그 뒤에 사이트 이름이 옵니다(예: &quot;site:Redmond&quot;). ID가 site:Redmond인 설정 컬렉션이 이미 있는 경우에는 위 명령이 실패합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction</p></td>
<td><p>사용자가 해당 클라이언트 버전 정책에서 버전 번호를 찾을 수 없는 클라이언트 응용 프로그램에서 로그온하려는 경우에 수행할 작업을 나타냅니다. DefaultAction은 다음 값 중 하나로 설정해야 합니다.</p>
<p>Allow. 클라이언트 응용 프로그램의 로그온이 허용됩니다.</p>
<p>AllowWithUrl. 클라이언트 응용 프로그램의 로그온이 허용됩니다. 또한 사용자에게 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL이 포함된 메시지 상자가 표시됩니다. 이 웹 페이지의 URL을 DefaultUrl 속성 값으로 지정해야 합니다.</p>
<p>Block. 클라이언트 응용 프로그램의 로그온이 차단됩니다.</p>
<p>BlockWithUrl. 클라이언트 응용 프로그램의 로그온이 차단됩니다. 그러나 사용자에게 표시되는 &quot;액세스 거부&quot; 메시지 상자에 해당 사용자가 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL이 포함됩니다. 이 웹 페이지의 URL을 DefaultUrl 속성 값으로 지정해야 합니다.</p>
<p>Enabled 속성이 False로 설정된 경우에는 이 속성이 무시됩니다. 즉, Enabled 속성을 False로 설정하면 어떤 종류의 클라이언트 버전 필터링도 수행되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultURL</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 승인된 클라이언트 응용 프로그램을 다운로드할 수 있는 웹 페이지의 URL을 지정합니다. URL을 지정하고 DefaultAction을 BlockWithUrl로 설정하면 사용자가 지원되지 않는 클라이언트 응용 프로그램에서 로그온하려고 할 때마다 나타나는 &quot;액세스 거부&quot; 메시지 상자에 이 URL이 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>클라이언트 버전 필터링의 사용 여부를 나타냅니다. Enabled 속성이 True이면 서버에서 로그온하려는 각 클라이언트 응용 프로그램의 버전 번호를 확인한 다음 해당 클라이언트 버전 정책에 따라 액세스를 허용하거나 거부합니다. Enabled 속성이 False이면 로그온할 수 있는 모든 클라이언트 응용 프로그램의 로그온이 허용됩니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsClientVersionConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

