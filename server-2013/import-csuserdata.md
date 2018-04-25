---
title: Import-CsUserData
TOCTitle: Import-CsUserData
ms:assetid: f39ef951-ee5b-4200-b6fb-68a4d4d6e86f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205373(v=OCS.15)
ms:contentKeyID: 49305515
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsUserData

 

_**마지막으로 수정된 항목:** 2015-03-09_

이전에 Export-CsUserData cmdlet을 사용하여 내보낸 사용자 데이터를 가져옵니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Import-CsUserData -PoolFqdn <Fqdn> <COMMON PARAMETERS>

    Import-CsUserData -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -FileName <String> [-ConfDirectoryFilter <String>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-LegacyFormat <SwitchParameter>] [-RoutingGroupFilter <String>] [-UserFilter <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Logs\\ExportedUserData.zip 파일의 사용자 데이터를 atl-cs-001.litwareinc.com 풀로 가져옵니다.

    Import-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

## 자세한 정보

Import-CsUserData cmdlet은 이전에 저장한 사용자 데이터 및/또는 전화 회의 디렉터리 데이터를 Lync Server로 가져오는 데 사용됩니다. 이 데이터는 [Export-CsUserData](export-csuserdata.md) cmdlet을 사용하여 내보낸 상태여야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsUserData"}

**Lync Server 제어판:** **Import-CsUserData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>내보낸 사용자 데이터를 포함하는 입력 파일의 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-InputFile &quot;C:\Data\ExportedUsers.xml&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>데이터를 가져올 사용자 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;UserDatabase:atl-sql-001.litwareinc.com&quot;</p>
<p>Identity 매개 변수와 PoolFqdn 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>가져올 사용자 데이터에 대한 등록자 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>–PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ConfDirectoryFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정하는 경우 지정된 전화 회의 디렉터리에 대한 전화 회의 디렉터리 정보를 가져올 수 있습니다. 예를 들어 ID가 13인 전화 회의 디렉터리에서 데이터를 가져오려면 다음 구문을 사용합니다.</p>
<p>-ConfDirectoryFilter 13</p>
<p>다음 명령을 사용하면 전화 회의 디렉터리 ID를 반환할 수 있습니다.</p>
<p>Get-CsConferenceDirectory</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Import-CsUserData</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet은 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LegacyFormat</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>가져올 데이터를 이전 버전 Lync Server 또는 Office Communications Server를 사용하여 내보냈음을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RoutingGroupFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>같은 라우팅 그룹에 속하는 사용자에 대해서만 데이터를 가져오도록 제한할 수 있습니다. 라우팅 그룹은 Lync Server에서 사용자가 등록되어 있는 프런트 엔드 서버를 결정하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자의 사용자 데이터를 가져올 수 있습니다. 지정한 사용자에 대한 데이터만 변환하려면 UserFilter 매개 변수를 해당 사용자의 SIP 주소로 설정합니다. 이때 sip: 매개 변수는 생략합니다. 예를 들면 다음과 같습니다.</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p>
<p>이 매개 변수를 사용하면 한 번에 한 사용자의 데이터를 가져올 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Import-CsUserData**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Convert-CsUserData](convert-csuserdata.md)  
[Export-CsUserData](export-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)  
[Update-CsUserData](update-csuserdata.md)

