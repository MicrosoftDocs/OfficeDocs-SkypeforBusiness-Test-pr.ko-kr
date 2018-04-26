---
title: New-CsConferenceDirectory
TOCTitle: New-CsConferenceDirectory
ms:assetid: fd5a4369-10cd-4337-94df-51bcaee4fde9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413080(v=OCS.15)
ms:contentKeyID: 49305639
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsConferenceDirectory

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용할 새 전화 회의 디렉터리를 만듭니다. 전화 회의 디렉터리는 전화 접속 회의 사용자가 전화 회의 정보를 찾는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsConferenceDirectory -HomePool <String> -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

ID가 42인 새 전화 회의 디렉터리를 만듭니다. 이 디렉터리는 atl-cs-001.litwareinc.com 풀에 호스트됩니다.

    New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"

## 자세한 정보

전화 접속 회의 URI(Uniform Resource Identifier)를 만들면 이러한 URI에 고유한 SIP 주소가 할당됩니다. 그러나 SIP를 인식하지 않는 장치는 SIP 주소를 해석하기 어렵습니다. 예를 들어 PSTN(공중 전화망) 전화의 경우 SIP 주소를 해석할 수 없습니다. 따라서 Lync Server에서는 이러한 장치에서 전화 접속 회의를 찾아 연결하도록 도와줄 수 있는 방법으로 전화 회의 디렉터리를 사용합니다. 이를 위해 각 전화 접속 회의 URI와 연결되어 있고 SIP URI가 아닌 정수 값으로 식별된 SIP 전화 회의 디렉터리를 만듭니다. 이렇게 하면 PSTN 전화와 기타 장치가 전화 회의에 연결할 때 SIP URI 대신 이러한 번호를 사용할 수 있습니다. 실제로 디렉터리 번호는 사용자가 전화 접속 회의에 연결할 때 입력하는 PSTN 전화 회의 ID에 포함됩니다.

새 전화 회의 디렉터리는 **New-CsConferenceDirectory** cmdlet을 호출하여 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsConferenceDirectory** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsConferenceDirectory"}

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
<td><p><em>HomePool</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 전화 회의 디렉터리를 호스트할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다(예: -Identity atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>새 전화 회의 디렉터리의 고유 식별자(숫자)입니다. ID는 0에서 9999 사이의 정수 값일 수 있지만 고유해야 합니다. 예를 들어 ID가 575인 디렉터리가 두 개 있을 수 없습니다. 새 디렉터리를 만들 때 숫자의 순서는 따르지 않아도 됩니다. 예를 들어 ID가 999인 디렉터리를 먼저 만들고 그 뒤에 ID가 2인 디렉터리와 ID가 438인 디렉터리 등을 차례로 만들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

없음. **New-CsConferenceDirectory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

