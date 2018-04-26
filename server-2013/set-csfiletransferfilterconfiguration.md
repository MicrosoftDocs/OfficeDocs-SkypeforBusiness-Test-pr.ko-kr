---
title: Set-CsFileTransferFilterConfiguration
TOCTitle: Set-CsFileTransferFilterConfiguration
ms:assetid: 2697d3a0-d920-4a1d-9adc-7a8c754d8977
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425736(v=OCS.15)
ms:contentKeyID: 49303095
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsFileTransferFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

파일 전송 필터 구성 설정 컬렉션을 수정합니다. 파일 전송 필터 설정은 사용자가 Lync Server 클라이언트를 사용하여 특정 파일 형식(예: 파일 확장명이 .vbs 또는 .ps1인 파일)을 전송하지 못하게 차단하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsFileTransferFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsFileTransferFilterConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Action <BlockAll | Block>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Extensions <PSListModifier>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(즉, ID가 site:Redmond인 파일 전송 필터링 구성)에 대한 파일 전송 필터링을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 Enabled 매개 변수를 명령에 포함하고 $False로 설정합니다.

    Set-CsFileTransferFilterConfiguration -Identity site:Redmond -Enabled $False

## 예제 2

예제 2에 표시된 명령은 Redmond 사이트에서 금지되는 파일 확장명 목록에 새 파일 확장명(Windows PowerShell 스크립트용 파일 확장명인 .ps1)을 추가합니다. **Set-CsFileTransferFilterConfiguration** cmdlet은 새 파일 확장명을 추가하기 위해 Extensions 매개 변수 및 Add 목록 한정자를 사용합니다. 이 한정자는 지정된 파일 확장명(.ps1)을 금지된 확장명 목록에 추가합니다. 단일 명령을 사용하여 여러 확장명을 추가하려면 쉼표를 사용하여 파일 확장명을 구분하면 됩니다(예: @{Add=".ps1",".ps2",".ps3"}). 단일 파일 확장명을 지정할 때는 마침표를 포함해야 합니다.

    Set-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Add=".ps1"}

## 예제 3

예제 3에서는 현재 조직에서 사용 중인 모든 파일 전송 필터 구성에 대한 Extensions 목록에 .ps1 파일 확장명을 추가합니다. 이를 위해 먼저 현재 사용 중인 모든 파일 전송 필터 구성 컬렉션을 반환하기 위해 **Get-CsFileTransferFilterConfiguration** cmdlet이 추가 매개 변수 없이 호출됩니다. 해당 컬렉션은 컬렉션의 각 항목에 .ps1 파일 확장명을 추가하는 **Set-CsFileTransferFilterConfiguration** cmdlet에 파이프됩니다.

    Get-CsFileTransferFilterConfiguration | Set-CsFileTransferFilterConfiguration -Extensions @{Add=".ps1"}

## 예제 4

예제 4에서는 Redmond 사이트의 파일 전송 필터 구성에 의해 차단되는 확장명 목록에서 파일 확장명 .ps1이 제거됩니다. 이 예제는 Add 목록 한정자를 호출하여 목록에 확장명을 추가하는 대신 Remove 목록 한정자를 호출하여 해당 목록에서 특정 확장명을 제거한다는 점을 제외하고 예제 3과 동일합니다.

    Set-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Remove=".ps1"}

## 예제 5

예제 5는 예제 4와 동일한 작업을 수행합니다. Redmond 사이트에 대한 파일 전송 필터 확장명 목록에서 .ps1 확장명을 제거합니다. 그러나 이 경우 먼저 site:Redmond에 대한 파일 전송 필터 구성을 검색하고 출력을 변수 $a에 할당합니다. 이제 $a에는 Redmond 사이트에 대한 구성이 포함됩니다. 다음으로, site:Redmond의 Extensions 속성인 $a의 Extensions 속성을 검색합니다($a.Extensions). 이 속성은 파일 확장명 목록을 포함합니다. Extensions 속성 다음에는 Remove 메서드에 대한 호출이 옵니다($a.Extensions.Remove). Remove 메서드에 값 .ps1을 전달합니다. 이렇게 하면 해당 확장명이 Extensions 속성 목록에서 제거됩니다. 그러나 변수 $a의 메모리에 저장된 구성에서만 확장명이 제거된 것입니다. 데이터베이스를 변경하려면 **Set-CsFileTransferFilterConfiguration** cmdlet을 호출하고 Instance 매개 변수에 $a를 전달해야 합니다.

    $a = Get-CsFileTransferFilterConfiguration -Identity site:Redmond
    $a.Extensions.Remove(".ps1")
    Set-CsFileTransferFilterConfiguration -Instance $a

## 자세한 정보

메신저 대화를 보낼 때 사용자는 파일을 첨부하여 다른 대화 참가자에게 보낼 수 있습니다. 특정 확장명(보통 잠재적으로 유해한 파일 형식의 확장명)을 가진 파일이 클라이언트에서 전송되지 않도록 Lync Server를 구성할 수 있습니다.

사용자가 Lync Server 클라이언트를 사용하여 파일을 전송할 수 있는지 여부는 전역 또는 (선택적으로) 사이트 범위에 적용된 파일 전송 필터 구성 설정에 따라 달라집니다. **Set-CsFileTransferFilterConfiguration** cmdlet을 사용하면 기존의 파일 전송 필터 구성을 수정할 수 있습니다. 확장명을 추가 또는 제거하거나 완전히 새 목록을 만들어 차단할 확장명 목록을 수정할 수 있습니다. 또한 이 cmdlet을 사용하여 파일 전송 필터링을 사용하도록 설정할지 여부와 Extensions 목록에 있는 항목과 일치하는 확장명을 가진 파일만 차단할지 또는 모든 파일을 차단할지 등의 차단 수준을 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsFileTransferFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsFileTransferFilterConfiguration"}

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
<td><p><em>Action</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileFilterAction</p></td>
<td><p>이 파일 전송 필터 구성이 설정된 경우 수행할 작업을 결정합니다. BlockAll로 설정한 경우 파일 확장명에 관계없이 모든 파일 전송이 금지됩니다. Block(기본값)으로 설정한 경우 Extensions 속성에 나열된 금지된 파일 형식 중 하나가 아닌 경우에 한해 파일 전송이 허용됩니다.</p>
<p>무제한 파일 전송을 허용하려면(즉, 파일 확장명에 관계없이 사용자가 모든 파일 형식을 교환할 수 있도록 하려면) 이 정책의 Enabled 속성을 False로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>파일 전송 필터링을 사용하거나 사용하지 않도록 설정합니다. 이 매개 변수가 True로 설정된 경우 Action 속성 값에 따라 지정된 확장명을 가진 파일 또는 모든 파일을 클라이언트에서 전송할 수 없습니다. 이 매개 변수가 False로 설정된 경우 모든 파일을 전송할 수 있습니다.</p>
<p>기본값: True.</p></td>
</tr>
<tr class="even">
<td><p><em>Extensions</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>차단할 파일 확장명 목록입니다. Lync Server 클라이언트를 사용하여 파일 확장명이 이 목록의 확장명 중 하나와 일치하는 파일을 전송하려고 하면 전송이 차단되고 파일이 전송되지 않습니다. Action이 BlockAll로 설정된 경우(모든 파일 전송이 차단됨) 또는 Enabled가 False로 설정된 경우(파일 전송이 차단되지 않음)에는 이 목록이 무시됩니다.</p>
<p>기본적으로 Extensions 속성 Default에 포함된 파일 확장명은 .ade, .adp, .app, .asp, .bas, .bat, .cer, .chm, .cmd, .com, .cpl, .crt, .csh, .exe, .fxp, .grp, .hlp, .hta, .inf, .ins, .isp, .its, .js, .jse, .ksh, .lnk, .mad, .maf, .mag, .mam, .maq, .mar., mas., .mat, .mau, .mav, .maw, .mda, .mdb, .mde, .mdt, .mdw, .mdz, .msc, .msi, .msp, .mst, .ocx, .ops, .pcd, .pif, .pl, .pnp, .prf, .prg, .pst, .reg, .scf, .scr, .sct, .shb, .shs, .tmp, .url, .vb, .vbe, .vbs, .vsd, .vsmacros, .vss, .vst, .vsw, .ws, .wsc, .wsf, .wsh입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 프롬프트를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 파일 전송 구성의 고유 식별자입니다. 이 값은 global 또는 site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 설정을 적용할 사이트의 이름입니다(예: site:Redmond).</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Set-CsFileTransferFilterConfiguration</strong> cmdlet이 기본적으로 전역 설정을 업데이트하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>파일 전송 필터 구성</p></td>
<td><p>개별 매개 변수 값을 설정하지 않고 cmdlet에 개체 참조를 전달할 수 있습니다. 이 개체는 FileTransferFilterConfiguration 유형이어야 하며 <strong>Get-CsFileTransferFilterConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체입니다. 파일 전송 필터 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값 또는 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)  
[Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)  
[Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)

