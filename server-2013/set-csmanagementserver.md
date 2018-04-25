---
title: Set-CsManagementServer
TOCTitle: Set-CsManagementServer
ms:assetid: 6607580d-f111-4dff-961a-71525bf2e482
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398465(v=OCS.15)
ms:contentKeyID: 49303860
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsManagementServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server  중앙 관리 서비스에서 사용하는 복제 포트를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsManagementServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplicationServicePort <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 Identity가 ManagementServer:atl-cs-001.litwareinc.com인 중앙 관리 서비스에 연결하여 복제 서비스 포트를 포트 5076으로 설정합니다.

    Set-CsManagementServer -Identity "ManagementServer:atl-cs-001.litwareinc.com" -ReplicationServicePort 5076

## 자세한 정보

중앙 관리 서비스는 중앙 관리 저장소 및 Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터 간의 데이터 복제를 담당합니다. 중앙 관리 서비스는 단일 프런트 엔드 풀(또는 Standard Edition 서버)에서 실행되며 Lync Server 인프라 전반에서 복제를 용이하게 합니다.

**Set-CsManagementServer** cmdlet을 사용하면 중앙 관리 서비스가 복제에 사용하는 포트를 지정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsManagementServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsManagementServer"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>중앙 관리 서비스의 고유 식별자입니다. 예를 들면 다음과 같습니다. -Identity &quot;ManagementServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>이제 접두사 &quot;ManagementServer:&quot;를 중앙 관리 서버를 지정할 때 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicationServicePort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>중앙 관리 서비스에서 사용하는 복제 포트의 포트 번호입니다.</p></td>
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

없음. **Set-CsManagementServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsManagementServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayManagementServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)  
[Move-CsManagementServer](move-csmanagementserver.md)

