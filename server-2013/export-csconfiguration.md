---
title: Export-CsConfiguration
TOCTitle: Export-CsConfiguration
ms:assetid: 7da7e133-e405-466c-a852-06a4fb678c59
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398627(v=OCS.15)
ms:contentKeyID: 49304164
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 토폴로지, 정책 및 구성 설정을 파일로 내보냅니다. 이 파일은 나중에 업그레이드, 하드웨어 오류 또는 기타 데이터 손실을 초래하는 문제가 발생한 후 이 정보를 중앙 관리 저장소로 복원하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Export-CsConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    Export-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 데이터를 중앙 관리 저장소에서 C:\\Config.zip 파일로 내보냅니다.

    Export-CsConfiguration -FileName "C:\Config.zip"

## 자세한 정보

Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터가 지정된 역할을 제대로 수행하려면 해당 컴퓨터에 현재 토폴로지, 현재 구성 설정 및 현재 정책의 복사본이 있어야 합니다. Lync Server는 이러한 정보가 해당 컴퓨터에 제대로 전달되도록 합니다.

**Export-CsConfiguration** cmdlet 및 **Import-CsConfiguration** cmdlet은 중앙 관리 저장소를 업그레이드하는 동안 Lync Server 토폴로지, 구성 설정 및 정책을 백업 및 복원하는 데 사용됩니다. **Export-CsConfiguration** cmdlet을 사용하여 데이터를 .ZIP 파일로 내보낸 다음 **Import-CsConfiguration** cmdlet을 사용하여 해당 .ZIP 파일을 읽고 토폴로지, 구성 설정 및 정책을 중앙 관리 저장소로 복원할 수 있습니다. 그런 다음 Lync Server의 복제 서비스는 복원된 정보를 Lync Server 서비스를 실행하는 다른 컴퓨터에 복제합니다.

구성 데이터 내보내기/가져오기 기능은 경계 네트워크(예: 에지 서버)에 있는 컴퓨터를 처음 구성할 때도 사용됩니다. 경계 네트워크의 컴퓨터를 구성할 때는 먼저 CsConfiguration cmdlet을 사용하여 수동 복제를 수행해야 합니다. 이를 수행하려면 **Export-CsConfiguration** cmdlet을 사용하여 구성 데이터를 내보낸 다음 경계 네트워크의 컴퓨터에 .ZIP 파일을 복사해야 합니다. 이렇게 하면 나중에 **Import-CsConfiguration** cmdlet 및 LocalStore 매개 변수를 사용하여 데이터를 가져올 수 있습니다. 이 작업을 한 번만 수행하면 자동으로 복제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Export-CsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsConfiguration"}

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
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p><strong>Export-CsConfiguration</strong> cmdlet을 실행할 때 생성되는 .ZIP 파일의 경로입니다(예: -FileName &quot;C:\Config.zip&quot;). <strong>Export-CsConfiguration</strong> cmdlet을 호출할 때 FileName 또는 AsBytes 매개 변수 중 하나를 포함해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>토폴로지 정보를 바이트 배열로 반환합니다. 나중에 <strong>Import-CsConfiguration</strong> cmdlet에서 사용하려면 반환된 데이터를 변수에 저장해야 합니다. 같은 명령에 AsBytes와 FileName을 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다. Force 매개 변수를 True로 설정하려면 다음 구문을 사용합니다.</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 로컬 컴퓨터에서 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Export-CsConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

AsBytes 매개 변수와 함께 호출한 경우 **Export-CsConfiguration** cmdlet은 바이트 배열 형식으로 구성 정보를 반환합니다.

## 참고 항목

#### 기타 리소스

[Import-CsConfiguration](import-csconfiguration.md)

