---
title: Set-CsUserServer
TOCTitle: Set-CsUserServer
ms:assetid: f4dd845a-5c78-4455-93eb-722b603ff154
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413026(v=OCS.15)
ms:contentKeyID: 49305537
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 User Services 풀을 수정하는 데 사용됩니다. User Services 풀은 현재 상태 정보를 제공하고 전화 회의를 관리하도록 지원합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUserServer [-Identity <XdsGlobalRelativeIdentity>] [-ConfDirManagementWcfTcpPort <UInt16>] [-ConferenceServer <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-McuFactorySipPort <UInt16>] [-UserDatabase <String>] [-UserPinManagementWcfHttpPort <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 UserServer:atl-cs-001.litwareinc.com인 단일 User Services 풀의 McuFactorySipPort를 변경합니다. 이 예제에서는 포트가 445로 변경됩니다.

    Set-CsUserServer -Identity "UserServer:atl-cs-001.litwareinc.com" -McuFactorySipPort 445

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 이번에는 조직의 모든 User Services 풀에 대한 McuFactorySipPort가 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 UserServer 매개 변수를 사용하여 현재 사용 중인 모든 User Services 풀의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 풀을 가져와 McuFactorySipPort를 445로 설정하는 **ForEach-Object** cmdlet에 파이프됩니다. **Set-CsUserServer** cmdlet은 파이프라인된 데이터 자체를 수신할 수 없으므로 데이터가 **ForEach-Object** cmdlet에 파이프되어야 합니다.

    Get-CsService -UserServer | ForEach-Object {Set-CsUserServer -Identity $_.Identity -McuFactorySipPort 445}

## 자세한 정보

User Services는 다양한 핵심 Lync Server 역할을 수행하는 범용 구성 요소입니다. 예를 들어 User Services는 현재 상태 정보를 제공하고, 전화 회의 센터 및 전화 회의 예약 센터를 통해 전화 회의 관리를 지원하고, 사용자 권한 부여 및 사용자 수준 경로 지정을 처리하고, 백 엔드 데이터베이스의 기본 인터페이스 역할을 합니다. User Services는 또한 사용자 계정 프로비저닝을 지원합니다.

따라서 관리자는 User Services 풀이 어떻게 구성되었는지 정확히 알아야 하며 필요할 경우 이러한 구성을 수정해야 합니다. 다음 명령을 사용하여 User Services 풀에 대한 정보를 검색할 수 있습니다.

Get-CsService -UserServer

마찬가지로 **Set-CsUserServer** cmdlet을 사용하여 이러한 풀에 대한 변경 작업을 수행할 수 있습니다. **Set-CsUserServer** cmdlet을 통해 관리자가 풀과 연결된 사용자 데이터베이스 및/또는 전화 회의 서버를 변경할 수 있습니다. 또한 이 cmdlet을 사용하여 회의 예약 센터에 연결하는 데 사용되는 포트를 수정할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUserServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserServer"}

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
<td><p><em>ConfDirManagementWcfTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>전화 회의 디렉터리를 관리하는 데 사용되는 WCF(Windows Communication Foundation) 포트입니다. 기본값은 9001입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConferenceServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>User Services 풀과 연결된 전화 회의 서버의 서비스 ID입니다(예: -ConferenceServer &quot;ConferenceServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 User Services 풀의 고유 식별자입니다(예: -Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot;).</p>
<p>이제 사용자 서버를 지정할 때 접두사 &quot;UserServer:&quot;를 사용하지 않아도 됩니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>McuFactorySipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>회의 예약 센터(McuFactory)에 연결하는 데 사용되는 포트입니다. 회의 예약 센터는 MCU(Media Control Unit)를 할당하여 전화 회의에 특정 미디어 유형(예: 오디오)을 추가합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>User Services 풀과 연결된 사용자 데이터베이스의 서비스 ID입니다 (예: -UserDatabase &quot;UserDatabase:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>UserPinManagementWcfHttpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자 PIN을 관리할 때 WCF(Windows Communication Foundation)에서 사용하는 포트입니다. 기본값은 443입니다.</p></td>
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

없음. **Set-CsUserServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsUserServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayUserServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

