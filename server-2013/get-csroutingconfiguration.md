---
title: Get-CsRoutingConfiguration
TOCTitle: Get-CsRoutingConfiguration
ms:assetid: 37a1cbc9-b8b2-423c-8ebb-7947fdcad24e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425851(v=OCS.15)
ms:contentKeyID: 49303311
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 배포 내에 정의된 모든 음성 경로의 목록을 포함하는 경로 지정 구성 개체를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsRoutingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 경로 지정 구성을 검색합니다. 개별 음성 경로를 검색하려면 **Get-CsVoiceRoute** cmdlet을 사용합니다.

    Get-CsRoutingConfiguration

## 자세한 정보

음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet을 사용하여 Lync Server 배포 내에 정의된 모든 음성 경로의 목록을 보유하는 전역 인스턴스를 검색합니다. 개별 음성 경로를 검색하거나 목록이 아닌 개별 개체로 검색하려면 **Get-CsVoiceRoute** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRoutingConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 개체의 인스턴스가 하나만 있을 수 있으므로 이 매개 변수는 아무 효과도 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 경로 지정 구성의 범위입니다. 가능한 값은 Global뿐입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 경로 지정 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsRoutingConfiguration** cmdlet은 Microsoft.Rtc.Management.Writable.Policy.Voice.PSTNRoutingSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

