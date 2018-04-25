---
title: Export-CsUserData
TOCTitle: Export-CsUserData
ms:assetid: 52c411e1-76da-48b8-b1e3-ddc7c7f86e3d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204897(v=OCS.15)
ms:contentKeyID: 49303638
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsUserData

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server로 가져올 수 있는 형식으로 사용자 데이터를 내보냅니다. 데이터는 XML 문서 쌍을 포함하는 .ZIP 파일로 내보내기됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Export-CsUserData -PoolFqdn <Fqdn> <COMMON PARAMETERS>

    Export-CsUserData -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -FileName <String> [-ConfDirectoryFilter <String>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-LegacyFormat <SwitchParameter>] [-UserFilter <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀의 사용자 데이터를 C:\\Logs\\ExportedUserData.zip 파일로 내보냅니다.

    Export-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

## 자세한 정보

관리자는 **Export-CsUserData** cmdlet을 사용하여 Lync Server 풀에 대한 사용자 데이터 및/또는 전화 회의 디렉터리를 내보낼 수 있습니다. Lync Server 2013 또는 Microsoft Lync Server 2010에서 사용되는 사용자 데이터 형식으로 저장 가능한 이 데이터는 [Import-CsUserData](import-csuserdata.md) cmdlet을 사용하여 가져올 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsUserData"}

**Lync Server 제어판:** **Export-CsUserData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><strong>Export-CsUserData</strong> cmdlet이 만드는 .ZIP 파일(내보내는 사용자 데이터가 포함됨)의 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-FileName &quot;C:\Logs\ExportedData.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>내보내려는 사용자 데이터를 포함하는 사용자 데이터베이스가 설치된 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>다음 명령을 실행하여 사용자 데이터베이스 풀의 정규화된 도메인 이름을 검색할 수 있습니다.</p>
<p>Get-CsService –UserDatabase</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>내보낼 사용자 데이터를 포함하는 등록자 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ConfDirectoryFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정하는 경우 지정된 전화 회의 디렉터리에 대한 전화 회의 디렉터리 정보를 내보낼 수 있습니다. 예를 들어 ID가 13인 전화 회의 디렉터리에서 데이터를 내보내려면 다음 구문을 사용합니다.</p>
<p>-ConfDirectoryFilter 13</p>
<p>다음 명령을 사용하면 전화 회의 디렉터리 ID를 반환할 수 있습니다.</p>
<p>Get-CsConferenceDirectory</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Export-CsUserData</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용하게 됩니다.</p></td>
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
<td><p>이 매개 변수를 지정하면 Microsoft Lync Server 2010에서 사용되는 형식으로 데이터가 저장됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자에 대한 데이터를 내보낼 수 있습니다. 특정 사용자를 표시하려면 다음과 같이 sip: 접두사를 포함하지 않고 해당 사용자의 SIP 주소를 지정합니다.</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Export-CsUserData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Export-CsUserData** cmdlet은 새 .ZIP 파일을 만듭니다.

## 참고 항목

#### 기타 리소스

[Convert-CsUserData](convert-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)  
[Update-CsUserData](update-csuserdata.md)

