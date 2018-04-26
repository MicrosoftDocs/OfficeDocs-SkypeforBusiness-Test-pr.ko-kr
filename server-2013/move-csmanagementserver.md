---
title: Move-CsManagementServer
TOCTitle: Move-CsManagementServer
ms:assetid: bcead113-fbd2-4fcf-ae01-6a312511ceef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412921(v=OCS.15)
ms:contentKeyID: 49304860
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsManagementServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

한 풀에 있는 중앙 관리 서버를 다른 풀로 이동합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsManagementServer [-ConfigurationFileName <String>] [-LisConfigurationFileName <String>] [-TargetFqdn <Fqdn>] <COMMON PARAMETERS>

    Move-CsManagementServer [-TargetFqdn <Fqdn>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 기존 풀에서 새 풀로 중앙 관리 서버를 이동합니다. 이 실시간 마이그레이션을 수행하려면, 즉 온라인 상태이고 액세스 가능한 중앙 관리 서버를 이동하려면 서버를 이동할 풀에 있는 컴퓨터에서 명령을 실행해야 합니다.

    Move-CsManagementServer

## 예제 2

예제 2에서는 재해 복구 시나리오, 즉 기존 관리 서버가 오프라인 상태이거나 액세스할 수 없는 시나리오에서 중앙 관리 서버를 이동합니다. 이 유형의 마이그레이션을 수행하려면 서버를 이동할 풀에 있는 컴퓨터에서 위 명령을 실행해야 합니다. 또한 ConfigurationFileName 매개 변수를 포함하여 이전에 저장한 구성 백업 파일을 가져오고, LisConfigurationFileName매개 변수를 포함하여 이전에 저장한 E9-1-1 백업 파일을 가져오며(E9-11을 사용하는 경우), Force 매개 변수를 포함하여 기존 서버에 연결할 수 없는 경우에도 중앙 관리 서버를 강제로 전송해야 합니다.

    Move-CsManagementServer -ConfigurationFileName "C:\CsConfiguration.zip" -LisConfigurationFileName "C:\CsLisConfiguration.zip" -Force

## 자세한 정보

**Move-CsManagementServer** cmdlet을 통해 관리자는 한 풀에 있는 중앙 관리 서버(및 중앙 관리 저장소)를 다른 풀로 이동할 수 있습니다. 중앙 관리 서버를 이동할 때마다 항상 서비스가 중단되고 데이터가 손실될 가능성이 있기 때문에 다음과 같은 경우가 아니면 전송하지 않는 것이 좋습니다.

1\. 기존 관리 풀을 해제해야 하는 경우. 이 경우 먼저 중앙 관리 서버를 전송한 다음 관리 풀을 해제해야 합니다.

2\. 재해 복구 시나리오가 발생하여 기존 중앙 관리 서버에 더 이상 액세스할 수 없는 경우

중앙 관리 서버를 이동하기 전에 다음을 수행해야 합니다.

1\. 새 중앙 관리 저장소가 생성되었는지 확인합니다. 이 작업을 수행하기 위해 **Install-CsDatabase** cmdlet을 실행하고 CentralManagementDatabase 매개 변수를 사용합니다.

2\. 중앙 관리 서버를 Standard Edition 서버로 이동하는 경우 로컬 설치를 사용하여 Standard Edition 서버 준비 옵션을 실행했는지 확인합니다. 이러한 사전 준비는 Windows PowerShell이 새 중앙 관리 저장소에 원격으로 액세스하도록 허용하는 방화벽 규칙을 추가하는 데 필요합니다.

3\. **Move-CsManagementServer** cmdlet을 실행할 컴퓨터에 중앙 관리 서버를 수용할 만큼 사용 가능한 디스크 공간이 충분한지 확인합니다.

4\. **Move-CsManagementServer** cmdlet을 실행할 컴퓨터에 프런트 엔드 서버 서비스가 설치되었는지 확인합니다. 이 서비스가 설치되어 실행되고 있지 않은 경우 이동이 실패하게 됩니다.

5\. **Move-CsManagementServer** cmdlet을 실행할 컴퓨터에서 **Enable-CsTopology** cmdlet을 올바르게 실행할 수 있는지 확인합니다. 해당 컴퓨터에서 **Enable-CsTopology** cmdlet을 실행할 수 없는 경우 이동이 실패하고 중앙 관리 저장소가 더 이상 작동하지 않게 됩니다.

이러한 단계를 완료했으면 중앙 관리 서버를 풀 A에서 풀 B로 이동하기 위해 풀 B에 있는 컴퓨터에 로그온한 다음 **Move-CsManagementServer** cmdlet을 추가 매개 변수 없이 호출하기만 하면 됩니다.

Move-CsManagementServer

그러면 **Move-CsManagementServer** cmdlet에서 토폴로지를 참조하여 중앙 관리 서버의 이전 위치(풀 A)를 확인한 다음 중앙 관리 서버 및 중앙 관리 저장소를 현재 풀(풀 B)로 전송합니다.

이동이 성공하면 **Move-CsManagementServer** cmdlet이 컴퓨터 목록을 화면에 표시하게 됩니다. 이동을 완료하려면 이러한 각 컴퓨터에서 로컬 설치를 실행해야 합니다. 풀 A의 컴퓨터에서 여전히 비활성 버전의 중앙 관리 서비스를 실행하므로 로컬 설치를 실행하여 해당 서비스를 삭제합니다. 풀 B에서는 중앙 관리 서버가 이동된 컴퓨터에서만 중앙 관리 서비스가 실행되고 다른 컴퓨터에서는 실행되지 않습니다. 따라서 이러한 컴퓨터에서 로컬 설치를 실행하면 중앙 관리 서비스가 설치됩니다.

재해 복구 시나리오에서 중앙 관리 서버를 전송하려면 **Export-CsConfiguration** cmdlet 및 **Export-CsLisConfiguration** cmdlet을 사용하여 Lync Server 구성과 E9-1-1(Enhanced 9-1-1) 구성의 백업 파일을 각각 만들어야 합니다. 일반적으로 재해는 경고 없이 발생하므로 이러한 cmdlet을 정기적으로 실행하여 구성 설정 백업 파일을 만들어야 합니다. **Move-CsManagementServer** cmdlet을 호출할 때는 이러한 백업 파일을 읽기 위해 ConfigurationFileName 및 LisConfigurationFileName 매개 변수를 모두 포함해야 합니다.

또한 오프라인 상태이거나 액세스할 수 없는 중앙 관리 서버를 이동할 때마다 Force 매개 변수를 포함해야 합니다. **Move-CsManagementServer** cmdlet을 호출하면 이 cmdlet에서 이동 작업을 수행하기 전에 일시적으로 중앙 관리 저장소를 읽기 전용으로 설정하여 데이터 손실을 방지합니다. 그러나 재해 복구 시나리오에서는 중앙 관리 저장소를 읽기 전용으로 표시할 수 없습니다. Force 매개 변수가 읽기 전용으로 구성되지 않은 경우에도 중앙 관리 저장소를 이동하도록 cmdlet에 지시하기 때문입니다.

**Move-CsManagementServer** cmdlet이 실패할 경우 중앙 관리 서버가 더 이상 작동하지 않는 상황이 발생할 수 있습니다. 중앙 관리 서버를 복원하려면 **Move-CsManagementServer** cmdlet을 실패하게 한 문제를 해결한 다음 cmdlet을 다시 실행해야 합니다. 이러한 다시 실행 작업은 새 풀 또는 기존 풀에서 수행할 수 있습니다. 기존 풀에서 **Move-CsManagementServer** cmdlet을 실행하면 이동이 효과적으로 취소되고 원래 구성으로 돌아갑니다.

**Move-CsManagementServer** cmdlet은 로컬로 실행해야 하며 원격 관리 세션에서 호출할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Move-CsManagementServer** cmdlet을 로컬로 실행할 수 있습니다. 또한 이 cmdlet을 실행 중인 컴퓨터의 로컬 관리자여야 합니다.

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
<td><p><em>ConfigurationFileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Export-CsConfiguration</strong> cmdlet을 실행하여 만드는 Lync Server 구성 백업 파일의 전체 경로입니다. 이 매개 변수는 재해 복구 시나리오에서만 사용해야 합니다.</p></td>
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
<td><p>기존 저장소가 오프라인 상태인 경우에도 중앙 관리 서버를 강제로 이동합니다. 이 매개 변수는 재해 복구 시나리오에서 필요합니다. 중앙 관리 서버를 강제 이동할 때마다 일부 데이터가 손실될 수 있습니다.</p>
<p>이전에 시도한 <strong>Move-CsManagementServer</strong> cmdlet 호출이 실패한 경우에도 Force 매개 변수를 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LisConfigurationFileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Export-CsLisConfiguration</strong> cmdlet을 실행하여 만드는 E9-1-1 백업 파일의 전체 경로입니다. 이 매개 변수는 재해 복구 시나리오에서만 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\MoveManagementServer.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리 서버를 이동할 풀의 정규화된 도메인 이름입니다</p></td>
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

없음. **Move-CsManagementServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Move-CsManagementServer** cmdlet은 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Set-CsManagementServer](set-csmanagementserver.md)

