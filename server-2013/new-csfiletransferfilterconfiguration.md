---
title: New-CsFileTransferFilterConfiguration
TOCTitle: New-CsFileTransferFilterConfiguration
ms:assetid: 3d1050fb-5df9-4186-94b9-8ef8a9103958
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425897(v=OCS.15)
ms:contentKeyID: 49303379
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsFileTransferFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 파일 전송 필터 구성을 만듭니다. 파일 전송 필터 구성은 사용자가 Lync Server 클라이언트를 사용하여 특정 파일 형식(예: 파일 확장명이 .vbs 또는 .ps1인 파일)을 전송하지 못하게 차단하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsFileTransferFilterConfiguration -Identity <XdsIdentity> [-Action <BlockAll | Block>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Extensions <PSListModifier>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **New-CsFileTransferFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 새 메신저 대화 파일 전송 필터 구성을 만듭니다. 추가 매개 변수를 지정하지 않았으므로 기본값을 사용하여 구성이 만들어집니다.

    New-CsFileTransferFilterConfiguration -Identity site:Redmond

## 예제 2

이 명령에서는 **New-CsFileTransferFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 새 파일 전송 필터 구성을 만듭니다. Extensions 매개 변수를 지정했으므로 새 구성에는 모든 기본값과 추가 파일 확장명 .ps1이 포함됩니다. Extensions 매개 변수를 사용하고 목록 한정자 Add 뒤에 추가할 파일 확장명을 포함하면 새 확장명이 추가됩니다. 파일 확장명의 일부로 마침표를 포함해야 합니다. 여러 개의 파일 확장명을 추가하려면 해당 확장명을 쉼표로 구분합니다(@{Add=".ps1",".ps2",".ps3"}).

    New-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Add=".ps1"}

## 예제 3

예제 3에서는 **New-CsFileTransferFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 새 파일 전송 필터 구성을 만듭니다. 이 예제는 Add 한정자 대신 Replace 목록 한정자가 사용된 점을 제외하고 예제 2와 유사합니다. 즉, 전체 파일 확장명 집합이 지정한 두 개의 파일 확장명 .vbs와 .ps1로 바뀝니다. 이 경우 Redmond 사이트에서 .vbs 및 .ps1 파일만 차단됩니다.

    New-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Replace=".vbs",".ps1"}

## 예제 4

예제 4에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 상주하는 파일 전송 필터 구성을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsFileTransferFilterConfiguration** cmdlet 및 InMemory 매개 변수를 사용하여 ID가 site:Redmond인 새 파일 전송 필터 구성을 만듭니다. 이때 새 설정은 메모리에만 있으며, Redmond 사이트의 사용자는 여전히 전역 파일 전송 필터 설정으로 제어됩니다.

두 번째 명령은 이 메모리에만 나타나는 인스턴스의 Action 속성 값을 BlockAll로 설정합니다. 마지막으로, 예제의 세 번째 명령은 **Set-CsFileTransferFilterConfiguration** cmdlet을 사용하여 새 설정 컬렉션을 만들고 Redmond 사이트에 적용합니다.

이 작업을 다음 명령을 사용하여 한 단계로 수행할 수 있습니다.

    New-CsFileTransferFilterConfiguration -Identity site:Redmond -Action "BlockAll"
    $x = New-CsFileTransferFilterConfiguration -Identity site:Redmond -InMemory 
    $x.Action = "BlockAll"
    Set-CsFileTransferFilterConfiguration -Instance $x

## 자세한 정보

메신저 대화를 보낼 때 사용자는 파일을 첨부하여 다른 대화 참가자에게 보낼 수 있습니다. 특정 확장명(보통 잠재적으로 유해한 파일 형식의 확장명)을 가진 파일이 Lync Server 클라이언트를 사용하여 전송되지 않도록 Lync Server를 구성할 수 있습니다.

Lync Server를 설치하면 전역 범위에서 구성된 단일 파일 전송 필터 구성이 자동으로 만들어집니다. 기본적으로 전역 구성은 조직의 모든 사용자에게 적용됩니다. 또한 **New-CsFileTransferFilterConfiguration** cmdlet을 사용하여 개별 사이트에 대한 사용자 지정 파일 전송 필터 구성을 만들 수 있습니다. 지정된 사이트에 대한 구성이 있는 경우 이 파일 전송 설정은 해당 사이트의 모든 사용자에게 적용됩니다. 사이트에 대한 이러한 컬렉션이 없을 경우 전역 설정이 대신 적용됩니다.

전역 범위에서는 새 파일 전송 필터 구성을 만들 수 없습니다. 그러나 **Set-CsFileTransferFilterConfiguration** cmdlet을 사용하여 전역 설정을 수정할 수는 있습니다. 마찬가지로, 구성이 이미 있는 사이트에 대해서는 새 구성을 만들 수 없습니다. 만들려고 하면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdministrator 그룹의 구성원은 **New-CsFileTransferFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsFileTransferFilterConfiguration"}

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
<td><p>파일 전송 필터 구성에 지정할 고유 식별자입니다. 새 구성의 ID는 &quot;site:&quot; 접두사 뒤에 사이트 이름을 포함하여 구성됩니다. 예를 들어 Redmond 사이트에 대한 새 구성을 만들려면 -Identity site:Redmond 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Action</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileFilterAction</p></td>
<td><p>파일 전송이 설정된 경우 수행할 작업을 결정합니다. BlockAll로 설정하면 파일 확장명에 관계없이 모든 파일 전송이 금지됩니다. Block(기본값)으로 설정하면 파일 확장명이 Extensions 속성에 나열된 금지된 파일 형식 중 하나가 아닌 경우 파일 전송이 허용됩니다.</p>
<p>무제한 파일 전송을 허용하려면(즉, 파일 확장명에 관계없이 사용자가 모든 파일 형식을 교환할 수 있도록 하려면) 이 정책의 Enabled 속성을 False로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>파일 전송 필터링을 활성화하거나 비활성화합니다. 이 매개 변수를 True로 설정하면 Lync Server 클라이언트를 사용하여 지정된 확장명을 가진 파일(또는 Action 속성 값에 따라 모든 파일)을 전송할 수 없습니다. 이 매개 변수를 False로 설정하면 모든 파일을 전송할 수 있습니다.</p>
<p>기본값: True.</p></td>
</tr>
<tr class="odd">
<td><p><em>Extensions</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>차단할 파일 확장명 목록입니다. Lync Server 클라이언트를 사용하여 파일 확장명이 이 목록의 확장명 중 하나와 일치하는 파일을 전송하려고 하면 전송이 차단되고 파일이 전송되지 않습니다. Action이 BlockAll로 설정된 경우(모든 파일 전송이 차단됨) 또는 Enabled가 False로 설정된 경우(파일 전송이 차단되지 않음)에는 이 목록이 무시됩니다.</p>
<p>기본적으로 Extensions 속성에 포함되는 파일 확장명은 .ade, .adp, .app, .asp, .bas, .bat, .cer, .chm, .cmd, .com, .cpl, .crt, .csh, .exe, .fxp, .grp, .hlp, .hta, .inf, .ins, .isp, .its, .js, .jse, .ksh, .lnk, .mad, .maf, .mag, .mam, .maq, .mar., mas., .mat, .mau, .mav, .maw, .mda, .mdb. .mde, .mdt, .mdw, .mdz, .msc, .msi, .msp, .mst, .ocx, .ops, .pcd, .pif, .pl, .pnp, .prf, .prg, .pst, .reg, .scf, .scr, .sct, .shb, .shs, .tmp, .url, .vb, .vbe, .vbs, .vsd, .vsmacros, .vss, .vst, .vsw, .ws, .wsc. .wsf, .wsh입니다.</p></td>
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

**New-CsFileTransferFilterConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)  
[Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)  
[Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)

