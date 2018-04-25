---
title: Set-CsArchivingServer
TOCTitle: Set-CsArchivingServer
ms:assetid: d4e51c14-34a6-4134-bb71-87bc2f11092d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398923(v=OCS.15)
ms:contentKeyID: 49305157
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsArchivingServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 보관 서버에 대한 새 데이터베이스 위치를 지정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsArchivingServer [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingDatabase <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ArchivingServer:atl-cs-001.litwareinc.com이라는 보관 서버의 보관 데이터베이스 위치를 변경합니다. 이 예제에서 새 데이터베이스는 ArchivingDatabase:atl-sql-001.litwareinc.com에 있습니다.

    Set-CsArchivingServer -Identity "ArchivingServer:atl-cs-001.litwareinc.com" -ArchivingDatabase "ArchivingDatabase:atl-sql-001.litwareinc.com"

## 자세한 정보

보관 서버를 사용하면 조직에서 실행되는 메신저 대화 세션의 전체 대화 내용을 저장할 수 있습니다. 이는 조직에서 메신저 대화 세션의 복사본을 유지하는 데 유용하게 사용될 수 있습니다. 특히, 모든 전자 통신 기록을 유지해야 하는 조직에서는 의무적으로 이러한 메신저 대화 세션의 복사본을 유지해야 합니다.

보관 서버는 각 메신저 대화 세션의 실행 시간 및 참가자에 대한 정보와 함께 각 세션의 대화 내용을 SQL Server 데이터베이스에 기록합니다. 이 데이터베이스의 위치는 보관 서버를 설치할 때 지정해야 합니다. 대부분의 경우 데이터베이스 위치를 변경할 필요가 없지만 하드웨어 오류 등의 문제가 발생하는 경우 **Set-CsArchivingServer** cmdlet을 사용하여 보관 서버의 새 데이터베이스를 지정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsArchivingServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsArchivingServer"}

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
<td><p><em>ArchivingDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 보관 데이터베이스의 서비스 위치입니다(예: -ArchivingDatabase ArchivingDatabase:atl-sql-001.litwareinc.com). 데이터베이스 위치를 지정할 때 SQL Server 경로 대신 이 서비스 위치를 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 보관 서버 인스턴스의 서비스 위치입니다(예: -Identity ArchivingServer:atl-cs-001.litwareinc.com). 다음 명령을 실행하여 모든 보관 서버의 서비스 위치를 검색할 수 있습니다.</p>
<p>Get-CsService –ArchivingServer | Select-Object Identity</p>
<p>이제 보관 서버를 지정할 때 접두사 &quot;ArchivingServer:&quot;를 사용하지 않아도 됩니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p></p></td>
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

없음. **Set-CsArchivingServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsArchivingServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayArchivingServer 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

