---
title: Import-CsLegacyConfiguration
TOCTitle: Import-CsLegacyConfiguration
ms:assetid: bd688c08-abb8-4c78-8e1b-b330412d4422
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412923(v=OCS.15)
ms:contentKeyID: 49304878
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsLegacyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Import-CsLegacyConfiguration** cmdlet을 사용하여 Microsoft Office Communications Server 2007 R2 또는 Microsoft Office Communications Server 2007에서 Lync Server로 여러 구성 설정을 가져올 수 있습니다. 이는 Lync Server 및 Office Communications Server 2007 R2 또는 Office Communications Server 2007의 이전 설치 간에 상호 운용성을 제공하는 데 도움이 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsLegacyConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplaceExisting <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 설치된 Lync Server와 Communications Server 2007 또는 Communications Server 2007 R2의 음성 정책 및 기타 설정을 병합합니다.

    Import-CsLegacyConfiguration

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 ReplaceExisting 매개 변수를 포함합니다. 이 매개 변수는 가져온 데이터를 사용하여 이름 충돌을 해결하도록 cmdlet에 지시합니다. 예를 들어 LocalRoute라는 음성 경로를 가져오려고 하는데, 이 이름의 음성 경로가 Lync Server 설치에 이미 있는 경우를 가정해 보겠습니다. ReplaceExisting 매개 변수를 포함했기 때문에 Lync Server 경로가 가져올 음성 경로로 대체됩니다.

    Import-CsLegacyConfiguration -ReplaceExisting

## 자세한 정보

**Import-CsLegacyConfiguration** cmdlet은 **Merge-CsLegacyTopology** cmdlet과 함께 사용되어 이전 버전의 Office Communications Server(Office Communications Server 2007 R2 또는 Office Communications Server 2007)에서 Lync Server로 마이그레이션할 수 있게 해 줍니다. **Import-CsLegacyConfiguration** cmdlet은 음성 정책, 위치 프로필(예: 다이얼 플랜), 음성 경로, 음성 정규화 규칙, 모임 정책, 외부 액세스 정책, 보관 정책, 현재 상태 정책, Communicator Web Access URL 설정 및 전화 접속 회의 액세스 번호를 가져오는 데 사용됩니다.

**Import-CsLegacyConfiguration** cmdlet을 실행하려면 먼저 WMI(Windows Management Instrumentation) 이전 버전과의 호환성 인터페이스 패키지를 설치해야 합니다. 이 응용 프로그램은 OCSWMIBC.msi를 실행하여 설치할 수 있습니다. 호환성 인터페이스 패키지를 설치한 후에는 **Merge-CsLegacyTopology** cmdlet을 실행해야 합니다. **Merge-CsLegacyTopology** cmdlet이 완료되면 토폴로지 작성기를 사용하여 병합된 토폴로지를 게시해야 합니다. 병합된 토폴로지를 게시하면 **Import-CsLegacyConfiguration** cmdlet을 호출할 수 있습니다. **Import-CsLegacyConfiguration** cmdlet은 WMI를 사용하여 이전 버전의 Office Communications Server에서 레거시 데이터를 읽습니다. 그런 다음 **Import-CsLegacyConfiguration** cmdlet은 검색된 데이터를 가져와 Lync Server에 해당하는 개체를 만듭니다. 예를 들어 현재 설치된 Lync Server에서 찾은 각 음성 정책에 해당하는 음성 정책이 새로 설치하는 Office Communications Server에서 만들어집니다.

**Import-CsLegacyConfiguration** cmdlet은 Office Communications Server 항목인 음성 정책, 위치 프로필, 음성 경로, 음성 정규화 규칙, 모임 정책, 외부 액세스 정책, 보관 정책, 현재 상태 정책, Communicator Web Access URL 설정 및 전화 접속 회의 액세스 번호를 변경할 때마다 다시 실행됩니다. 기본적으로 **Import-CsLegacyConfiguration** cmdlet을 다시 실행하면 Office Communications Server 토폴로지에 추가된 새 항목만 가져오게 됩니다. 수정된 개체를 가져오려면 다음 두 가지를 수행해야 합니다. 첫째, Lync Server 구성 복사본에서 해당 항목(예: 음성 정책)에 대해 변경 사항이 없는지 확인합니다. 둘째, **Import-CsLegacyConfiguration** cmdlet을 ReplaceExisting 매개 변수와 함께 실행합니다. 이렇게 하면 **Import-CsLegacyConfiguration** cmdlet이 수정된 개체를 가져오고 현재 Lync Server에 있는 해당 개체를 덮어씁니다. Communications Server 2007 R2 토폴로지에서 개체를 삭제해도 Lync Server에서 해당 항목이 삭제되지 않습니다. Lync Server에서 해당 항목을 수동으로 제거해야 합니다.

**Move-CsLegacyUser** cmdlet은 **Import-CsLegacyConfiguration** cmdlet을 사용하여 가져온 정보에 의존합니다. 따라서 **Move-CsLegacyUser** cmdlet을 실행하면 계속하기 전에 **Import-CsLegacyConfiguration** cmdlet을 실행해야 함을 알려 주는 오류 메시지가 수신될 수 있습니다. 이 경우 **Import-CsLegacyConfiguration** cmdlet을 다시 실행해야 레거시 사용자를 이동할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 다음 그룹의 구성원은 **Import-CsLegacyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsLegacyConfiguration"}

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
<td><p><em>ReplaceExisting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 이전에 가져온 정책 또는 설정 중 cmdlet이 마지막으로 실행된 이후로 변경된 정책 또는 설정을 <strong>Import-CsLegacyConfiguration</strong> cmdlet이 덮어쓰도록 지시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다 (예: -Report &quot;C:\Logs\ImportConfiguration.html&quot;).</p></td>
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

없음. **Import-CsLegacyConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Import-CsLegacyConfiguration** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)  
[Move-CsLegacyUser](move-cslegacyuser.md)

