---
title: Import-CsLegacyConferenceDirectory
TOCTitle: Import-CsLegacyConferenceDirectory
ms:assetid: 5ecb9bf9-cbce-48a6-966c-ecbdac59cb3a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398418(v=OCS.15)
ms:contentKeyID: 49303781
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsLegacyConferenceDirectory

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Import-CsLegacyConferenceDirectory** cmdlet은 Microsoft Office Communications Server 2007 R2의 전화 회의 디렉터리를 Lync Server로 가져오는 데 사용됩니다. 이를 통해 Lync Server와 Office Communications Server 2007 R2 간에 상호 운용성을 유지할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsLegacyConferenceDirectory [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Communications Server 2007 R2의 전화 회의 디렉터리를 Lync Server로 가져옵니다.

    Import-CsLegacyConferenceDirectory

## 자세한 정보

**Import-CsLegacyConferenceDirectory** cmdlet은 **Merge-CsLegacyTopology** cmdlet과 함께 Office Communications Server 2007 R2에서 Lync Server로 마이그레이션하는 데 사용됩니다. **Import-CsLegacyConfiguration** cmdlet은 Communications Server 2007 R2의 전화 회의 디렉터리를 Lync Server로 가져옵니다.

**Import-CsLegacyConferenceDirectory** cmdlet을 실행하려면 먼저 WMI(Windows Management Instrumentation) 이전 버전과의 호환성 인터페이스 패키지를 설치해야 합니다. Lync Server 설치 DVD의 설치(Setup) 폴더에 있는 OCSWMIBC.msi 파일을 실행하면 이 응용 프로그램이 설치됩니다. 이전 버전과의 호환성 인터페이스 패키지를 설치한 후에는 **Merge-CsLegacyTopology** cmdlet을 실행해야 합니다.

**Merge-CsLegacyTopology** cmdlet 실행이 완료되면 **Import-CsLegacyConferenceDirectory** cmdlet을 호출할 수 있습니다. **Import-CsLegacyConferenceDirectory** cmdlet은 먼저 WMI를 사용하여 Communications Server 2007 R2에서 데이터를 읽은 다음 검색된 데이터를 가져와 Lync Server에서 해당 개체를 만듭니다. Communications Server 2007 R2의 각 전화 회의 디렉터리에 해당하는 디렉터리가 새로 설치한 Lync Server에 만들어집니다.

**Import-CsLegacyConferenceDirectory** cmdlet은 Communications Server 2007 R2 환경에서 전화 회의 디렉터리를 추가, 삭제 또는 이동할 때마다 다시 실행해야 합니다. 또한 **Import-CsLegacyConferenceDirectory** cmdlet은 **Merge-CsLegacyTopology** cmdlet을 실행할 때마다 실행해야 합니다. 그러면 전화 회의 디렉터리와 토폴로지가 동기화된 상태로 유지됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsLegacyConferenceDirectory** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsLegacyConferenceDirectory"}

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
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\ImportDirectories.html&quot;).</p></td>
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

없음. **Import-CsLegacyConferenceDirectory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Import-CsLegacyConferenceDirectory** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)  
[Move-CsLegacyUser](move-cslegacyuser.md)

