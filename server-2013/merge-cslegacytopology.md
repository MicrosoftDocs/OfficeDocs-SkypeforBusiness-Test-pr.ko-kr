---
title: Merge-CsLegacyTopology
TOCTitle: Merge-CsLegacyTopology
ms:assetid: 396d6c84-7b38-41ae-9273-665f76cdd9ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425870(v=OCS.15)
ms:contentKeyID: 49303343
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Merge-CsLegacyTopology

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Merge-CsLegacyTopology** cmdlet을 사용하여 Microsoft Office Communications Server 2007 R2 또는 Microsoft Office Communications Server 2007에서 Lync Server로 토폴로지 정보를 마이그레이션할 수 있습니다. 이를 통해 Lync Server와 이전 버전 소프트웨어 간의 상호 운용성을 유지할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Merge-CsLegacyTopology -TopologyXmlFileName <String> <COMMON PARAMETERS>

    Merge-CsLegacyTopology -Reserved <PSObject> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-UserInputFileName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Communications Server 2007 R2 또는 Communications Server 2007의 토폴로지 정보 및 신뢰할 수 있는 서비스 항목을 Lync Server와 병합합니다. 필수 매개 변수인 TopologyXmlFileName은 **Merge-CsLegacyTopology** cmdlet을 실행할 때 생성되는 출력 파일의 경로를 지정하는 데 사용됩니다.

    Merge-CsLegacyTopology -TopologyXmlFileName C:\New_Topology.xml

## 예제 2

예제 2는 예제 1에 사용된 명령의 변형입니다. 그러나 예제 2에서는 에지 서버 정보를 토폴로지에 병합하기 위해 UserInputFileName 매개 변수를 포함합니다. 매개 변수 값 C:\\EdgeServers.xml은 Office Communications Server에 대한 에지 서버 정보가 포함된 사용자 지정 XML 파일을 가리킵니다.

    Merge-CsLegacyTopology -TopologyXmlFileName C:\New_Topology.xml -UserInputFileName C:\EdgeServers.xml

## 자세한 정보

**Merge-CsLegacyTopology** cmdlet은 이전 버전의 Office Communications Server( Office Communications Server 2007 R2 또는 Office Communications Server 2007)에서 Lync Server로 마이그레이션할 때 처음 사용하는 도구입니다. **Merge-CsLegacyTopology** cmdlet은 도메인, User Services, 등록자, 중재 서버 및 에지 서버 구성 요소에 대한 신뢰할 수 있는 서비스 항목 및 토폴로지 정보를 마이그레이션하는 데 사용됩니다. 또한 이 cmdlet은 회의 길잡이 응용 프로그램, Communicator Web Access 및 전화 회의 디렉터리의 트러스트된 서비스 항목을 마이그레이션합니다. 트러스트된 서비스 항목이란 Lync Server에서 신뢰하는 서버를 나타내는 Active Directory 기록입니다. 토폴로지 정보를 병합하면 Lync Server에 속한 사용자가 Communications Server 2007 또는 Communications Server 2007 R2에 속한 사용자와 통신할 수 있습니다.

**Merge-CsLegacyTopology** cmdlet을 실행하려면 먼저 WMI(Windows Management Instrumentation) Backward Compatibility 인터페이스 패키지를 설치해야 합니다. 설치 DVD의 설치(Setup) 폴더에 있는 OCSWMIBC.msi 파일을 실행하면 이 응용 프로그램이 설치됩니다. Compatibility 인터페이스 패키지를 설치한 후에는 **Merge-CsLegacyTopology** cmdlet을 호출할 수 있습니다. **Merge-CsLegacyTopology** cmdlet은 WMI를 사용하여 이전 버전의 Office Communications Server에서 레거시 데이터를 읽습니다. 그런 다음 이렇게 검색한 데이터를 사용하여 Lync Server에서 해당하는 개체를 만듭니다. 예를 들어 Office Communications Server에 있는 각 SIP 도메인에 대해 Lync Server에서 해당 SIP 도메인을 새로 만듭니다.

**Merge-CsLegacyTopology** cmdlet을 실행한 후에는 **Import-CsLegacyConfiguration** cmdlet 및 **Import-CsLegacyConferenceDirectory** cmdlet을 실행해야 합니다.

**Merge-CsLegacyTopology** cmdlet은 Communications Server 2007 또는 Communications Server 2007 R2 토폴로지를 가져오기 위해 마이그레이션 시작 시 한 번, 이전 Office Communications Server 환경이 해제된 경우 마이그레이션 종료 시 한 번, 이렇게 적어도 두 번 이상 실행해야 합니다. 또한 레거시 Office Communications Server 환경을 변경할 때마다 이 cmdlet을 실행해야 합니다. 예를 들어 Office Communications Server에서 중재 서버를 추가하거나 풀을 해제한 경우 수정된 토폴로지를 가져오려면 **Merge-CsLegacyTopology** cmdlet을 다시 실행해야 합니다.

**Import-CsLegacyConfiguration** cmdlet 및 **Import-CsLegacyConferenceDirectory** cmdlet은 **Merge-CsLegacyTopology** cmdlet에 의해 구성된 값에 따라 달라집니다. 즉, 방금 발생한 문제의 가능한 한 가지 해결 방법으로 **Import-CsLegacyConfiguration** cmdlet 또는 **Import-CsLegacyConferenceDirectory** cmdlet에서 **Merge-CsLegacyTopology** cmdlet을 실행하도록 지시하는 오류 메시지가 나타날 수 있습니다. **Merge-CsLegacyTopology** cmdlet을 다시 실행하지 않으면 추가 오류가 발생할 수 있습니다. 특히 항목이 Office Communications Server 환경에서 제거되었는데도 Lync Server에서 여전히 사용 중인 경우 오류가 발생합니다.

이전 Office Communications Server의 에지 서버를 병합하려면 먼저 에지 서버가 포함된 사용자 지정 XML 파일을 만들어야 합니다. 에지 서버 설정은 Active Directory에 저장되지 않아 **Merge-CsLegacyTopology** cmdlet에서 검색할 수 없기 때문입니다. 이 XML 파일을 만든 후에는(이 파일을 만드는 방법은 Lync Server 배포 가이드 참조) **Merge-CsLegacyTopology** cmdlet을 실행할 때 이 파일의 경로와 UserInputFileName 매개 변수를 포함해야 합니다. 그러지 않으면 병합된 토폴로지에 에지 서버가 포함되지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Merge-CsLegacyTopology** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Merge-CsLegacyTopology"}

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
<td><p><em>Reserved</em></p></td>
<td><p>필수</p></td>
<td><p>PS topology object</p></td>
<td><p>토폴로지 XML 파일 대신 토폴로지 개체를 사용하여 토폴로지를 병합하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TopologyXmlFileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p><strong>Merge-CsLegacyTopology</strong> cmdlet이 실행될 때 출력 파일이 생성되는 경로입니다. 이 파일은 Report 매개 변수로 지정하는 파일과는 다릅니다. 후자는 오류 정보를 기록하는 데 사용되는 반면, 토폴로지 XML 파일은 새로 만든 Lync Server 토폴로지를 포함합니다. 이 파일은 나중에 새 토폴로지를 게시하는 데 사용할 수 있습니다.</p>
<p>지정된 파일이 이미 존재하는 경우 <strong>Merge-CsLegacyTopology</strong> cmdlet을 실행할 때 덮어씁니다.</p></td>
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
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다. (예: -Report &quot;C:\Logs\MergeTopology.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>UserInputFileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이전 버전의 Office Communications Server에서 에지 서버 데이터를 가져오는 데 사용되는 XML 파일의 경로입니다. 이 XML 파일( Lync Server 배포 가이드에 설명된 지침에 따라 만들어야 함)은 에지 서버 설정이 Active Directory 도메인 서비스에 저장되지 않기 때문에 필요합니다. 에지 서버 정보를 가져올 필요가 없는 경우 이 매개 변수를 생략해도 됩니다.</p>
<p>이 매개 변수를 사용하지 않으면 Communications Server 2007 R2 또는 Communications Server 2007 R2 및 Lync Server을 실행하는 환경에서 원격 및 외부 액세스 기능(페더레이션 포함)이 제대로 작동하지 않을 수 있습니다.</p></td>
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

없음. **Merge-CsLegacyTopology** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Merge-CsLegacyTopology** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)  
[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)  
[Move-CsLegacyUser](move-cslegacyuser.md)

