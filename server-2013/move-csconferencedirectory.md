---
title: Move-CsConferenceDirectory
TOCTitle: Move-CsConferenceDirectory
ms:assetid: c43207fa-06dd-4360-ae32-b2f17f7100d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412968(v=OCS.15)
ms:contentKeyID: 49304961
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsConferenceDirectory

 

_**마지막으로 수정된 항목:** 2015-05-28_

기존 전화 회의 디렉터리를 다른 풀로 이동합니다. 전화 회의 디렉터리는 전화 접속 회의 사용자가 전화 회의 정보를 찾는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> -TargetPool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 3인 전화 회의 디렉터리를 atl-cs-002.litwareinc.com 풀로 이동합니다.

    Move-CsConferenceDirectory -Identity 3 -TargetPool atl-cs-002.litwareinc.com

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 그러나 이 예제에는 대상 풀을 현재 사용할 수 없는 경우에도 이동을 수행하도록 Force 매개 변수가 포함되어 있습니다.

    Move-CsConferenceDirectory -Identity 3 -TargetPool atl-cs-002.litwareinc.com -Force

## 예제 3

예제 3에서는 모든 기존 전화 회의 디렉터리를 대상 풀 atl-cs-002.litwareinc.com으로 이동합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsConferenceDirectory** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 전화 회의 디렉터리 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 디렉터리를 대상 풀로 이동하는 **Move-CsConferenceDirectory** cmdlet에 파이프됩니다.

    Get-CsConferenceDirectory | Move-CsConferenceDirectory -TargetPool atl-cs-002.litwareinc.com 

## 자세한 정보

전화 접속 회의 URI(Uniform Resource Identifier)를 만들면 이러한 URI에 고유한 SIP 주소가 할당됩니다. 그러나 SIP를 인식하지 않는 장치는 SIP 주소를 해석하기 어렵습니다. 예를 들어 PSTN(공중 전화망) 전화의 경우 SIP 주소를 해석할 수 없습니다. 따라서 Lync Server에서는 이러한 장치에서 전화 접속 회의를 찾아 연결하도록 도와줄 수 있는 방법으로 전화 회의 디렉터리를 사용합니다. 이를 위해 각 전화 접속 회의 URI와 연결되어 있고 SIP URI가 아닌 정수 값으로 식별된 SIP 전화 회의 디렉터리를 만듭니다. 이렇게 하면 PSTN 전화와 기타 장치가 전화 회의에 연결할 때 SIP URI 대신 이러한 번호를 사용할 수 있습니다. 디렉터리 번호는 사용자가 전화 접속 회의에 연결할 때 입력하는 PSTN 전화 회의 ID에 포함됩니다.

경우에 따라 전화 회의 디렉터리를 다른 풀로 이동해야 할 수 있습니다. 예를 들어 특정 풀을 해제하여 모든 기존 전화 회의 디렉터리를 새 위치로 이동해야 하는 경우가 있습니다. **Move-CsConferenceDirectory** cmdlet을 사용하면 전화 회의 디렉터리를 다른 풀로 이동할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Move-CsConferenceDirectory** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsConferenceDirectory"}

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
<td><p>이동할 전화 회의 디렉터리의 숫자 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPool</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이동할 전화 회의 디렉터리가 있는 풀의 FQDN(정규화된 도메인 이름)입니다(예: -Identity atl-cs-002.litwareinc.com).</p></td>
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
<td><p>이 매개 변수가 있으면 대상 풀을 현재 사용할 수 없는 경우에도 전화 회의 디렉터리가 이동됩니다. 기본적으로 <strong>Move-CsConferenceDirectory</strong> cmdlet은 대상 풀에 연결할 수 없는 경우 디렉터리를 이동하지 않습니다.</p>
<p><strong>Move-CsConferenceDirectory</strong> cmdlet을 Force 매개 변수와 함께 실행하기 전에 Dbimpexp.exe를 사용하여 레거시 데이터를 수동으로 내보낸 다음 이 데이터를 대상 등록자 풀에 가져와야 합니다. Dbimpexp.exe는 Lync Server 설치 미디어의 루트 폴더에 있습니다.</p></td>
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

없음. **Move-CsConferenceDirectory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

