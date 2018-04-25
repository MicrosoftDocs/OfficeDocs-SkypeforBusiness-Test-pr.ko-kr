---
title: Export-CsArchivingData
TOCTitle: Export-CsArchivingData
ms:assetid: 644bf86e-0e7e-4607-bedf-d491b1c16745
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398452(v=OCS.15)
ms:contentKeyID: 49303845
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsArchivingData

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server  보관 데이터베이스에 저장된 레코드를 내보내는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Export-CsArchivingData -DBInstance <String> -Identity <XdsIdentity> <COMMON PARAMETERS>

    Export-CsArchivingData -Identity <XdsIdentity> <COMMON PARAMETERS>

    Export-CsArchivingData -DBInstance <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -OutputFolder <String> -StartDate <DateTime> [-Confirm [<SwitchParameter>]] [-EndDate <DateTime>] [-ExcludeWebConfArchive <SwitchParameter>] [-Force <SwitchParameter>] [-IncludeTrustedApplication <SwitchParameter>] [-Purge <SwitchParameter>] [-UserUri <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-sql-001.litwareinc.com 서버에 있는 보관 데이터베이스에서 레코드를 추출하여 결과 EML 파일을 C:\\ArchivingExports 폴더에 저장합니다. 시작 날짜를 2012년 6월 1일(-StartDate 6/1/2012)로 지정하여 2012년 5월 31일 이후 데이터베이스에 기록된 항목만 내보냅니다.

    Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports"

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형이며 이 경우에는 사용자 Ken Myer에 관련된 레코드만 내보냅니다. 단일 사용자에 대한 레코드로 내보내기를 제한하기 위해 적절한 SIP 주소가 뒤에 오도록 UserUri 매개 변수를 포함합니다.

    Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports" -UserUri "kenmyer@litwareinc.com"

## 예제 3

예제 3은 예제 1에 표시된 명령의 다른 변형입니다. 예제 3에서는 데이터베이스에서 2012년 6월에 해당하는 항목만 내보냅니다. 이 기간으로 내보내기를 제한하기 위해 EndDate 매개 변수와 StartDate 매개 변수를 함께 사용합니다. 시작 날짜를 2012년 6월 1일로 지정하고 종료 날짜를 2012년 6월 30일로 지정하여 내보내기를 2012년 6월에 기록된 항목으로 제한합니다.

    Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -EndDate 6/30/2012 -OutputFolder "C:\ArchivingExports"

## 자세한 정보

많은 조직에서 내부 사용자들이 수행한 모든 메신저 대화 세션의 대화 내용을 보관하는 것이 유용하다고 판단하고 있으며, 법률상으로 이러한 보관이 의무화된 조직도 있습니다. 예를 들어 금융업계에는 법률 규정에 따라 모든 전자 통신의 복사본을 유지해야 하는 조직이 많습니다.

이유와 관계없이 Lync Server에서는 메신저 대화 및 전화 회의 세션 보관과 관련된 유연한 기능을 제공합니다. 보관 서버를 배포한 경우 여러 가지 **CsArchivingConfiguration** cmdlet을 사용하여 메신저 대화 보관을 설정 및 해제하고 보관 데이터베이스를 관리할 수 있습니다. 또한 보관이 실패한 경우 메신저 대화를 일시 중지할 수 있으므로 모든 전자 통신 레코드를 보관하는 데 도움이 됩니다.

보관을 활성화한 경우 사용자의 전자 통신 기록은 보관 데이터베이스에 저장됩니다. 이러한 모든 레코드(또는 이러한 레코드의 선택된 하위 집합)를 보려면 **Export-CsArchivingData** cmdlet을 사용하여 데이터베이스에서 이러한 레코드를 추출하고 Outlook EML(Express Electronic Mail) 파일(.EML 파일 확장명)로 저장할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCComponentUniversalServices 그룹의 구성원은 **Export-CsArchivingData** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsArchivingData"}

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
<td><p><em>DBInstance</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>보관 데이터가 기록되는 SQL Server 데이터베이스 인스턴스에 대한 경로입니다(예: &quot;atl-sql-001\Archinst&quot;).</p>
<p>이 매개 변수는 Microsoft Lync Server 2010에서만 사용됩니다. Lync Server 2013에서 <strong>Export-CsArchivingData</strong> cmdlet을 사용하는 경우에는 Identity 매개 변수를 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>내보낼 보관 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;ArchivingDatabase:atl-sql-001.litwareinc.com&quot;</p>
<p>풀 이름만 사용하여 데이터베이스를 지정할 수도 있습니다.</p>
<p>-Identity &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>다음 명령을 사용하면 보관 데이터베이스의 서비스 ID를 검색할 수 있습니다.</p>
<p>Get-CsService –ArchivingDatabase | Select-Object Identity</p></td>
</tr>
<tr class="odd">
<td><p><em>OutputFolder</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>내보낸 데이터를 저장할 폴더의 전체 경로입니다(예: C:\ArchivingExports). 이 폴더가 존재하지 않으면 <strong>Export-CsArchivingData</strong> cmdlet이 해당 폴더를 만듭니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StartDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>내보낼 레코드의 가장 이른 작업 날짜입니다. 예를 들어 시작 날짜를 2010년 6월 1일로 설정하면 이 날짜보다 이전(예: 2010년 5월 31일)에 데이터베이스에 기록된 항목은 내보내기에서 제외됩니다.</p>
<p>StartDate 및 EndDate 속성에 값을 할당할 대는 국가 및 언어 옵션 설정에 지정된 날짜-시간 형식을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EndDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>내보낼 레코드의 가장 늦은 작업 날짜입니다. 예를 들어 종료 날짜를 2010년 6월 1일로 설정하면 이 날짜보다 이후(예: 2010년 6월 2일)에 데이터베이스에 기록된 항목은 내보내기에서 제외됩니다. 종료 날짜가 시작 날짜보다 이전인 경우 오류 메시지가 수신되지는 않지만 내보내기가 실패합니다(예를 들어 종료 날짜가 2010년 1월 1일이고 시작 날짜가 2010년 6월 1일인 경우).</p>
<p>StartDate 및 EndDate 속성에 값을 할당할 대는 국가 및 언어 옵션 설정에 지정된 날짜-시간 형식을 사용합니다.</p>
<p>종료 날짜를 지정하지 않으면 현재 날짜가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeWebConfArchive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>메신저 대화 레코드만 내보내도록 <strong>Export-CsArchivingData</strong> cmdlet에 지시합니다. 기본적으로 이 cmdlet은 메신저 대화 레코드와 전화 회의 레코드를 둘 다 내보냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>IncludeTrustedApplication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함할 경우 <strong>Export-CsArchivingData</strong> cmdlet이 레코드를 내보낼 때 신뢰할 수 있는 응용 프로그램에서 기록한 데이터를 포함하도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Purge</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Purge 매개 변수는 성공적으로 내보낸 레코드를 보관 데이터베이스에서 삭제합니다. 이 매개 변수를 포함하지 않으면 내보낸 레코드가 데이터베이스에 유지됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자에 대한 보관 데이터 내보내기를 사용하도록 설정하는 데 사용됩니다. 이 작업은 UserUri 매개 변수를 사용하고 사용자에 대한 SIP 주소를 지정하여 수행됩니다. UserUri 매개 변수는 한 번에 하나의 URI만 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DBInstance</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>보관 데이터가 기록되는 SQL Server 데이터베이스 인스턴스에 대한 경로입니다(예: &quot;atl-sql-001\Archinst&quot;).</p>
<p>이 매개 변수는 Microsoft Lync Server 2010에서만 사용됩니다. Lync Server 2013에서 <strong>Export-CsArchivingData</strong> cmdlet을 사용하는 경우에는 Identity 매개 변수를 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>내보낼 보관 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;ArchivingDatabase:atl-sql-001.litwareinc.com&quot;</p>
<p>풀 이름만 사용하여 데이터베이스를 지정할 수도 있습니다.</p>
<p>-Identity &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>다음 명령을 사용하면 보관 데이터베이스의 서비스 ID를 검색할 수 있습니다.</p>
<p>Get-CsService –ArchivingDatabase | Select-Object Identity</p></td>
</tr>
<tr class="odd">
<td><p><em>OutputFolder</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>내보낸 데이터를 저장할 폴더의 전체 경로입니다(예: C:\ArchivingExports). 이 폴더가 존재하지 않으면 <strong>Export-CsArchivingData</strong> cmdlet이 해당 폴더를 만듭니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StartDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>내보낼 레코드의 가장 이른 작업 날짜입니다. 예를 들어 시작 날짜를 2010년 6월 1일로 설정하면 이 날짜보다 이전(예: 2010년 5월 31일)에 데이터베이스에 기록된 항목은 내보내기에서 제외됩니다.</p>
<p>StartDate 및 EndDate 속성에 값을 할당할 대는 국가 및 언어 옵션 설정에 지정된 날짜-시간 형식을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EndDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>내보낼 레코드의 가장 늦은 작업 날짜입니다. 예를 들어 종료 날짜를 2010년 6월 1일로 설정하면 이 날짜보다 이후(예: 2010년 6월 2일)에 데이터베이스에 기록된 항목은 내보내기에서 제외됩니다. 종료 날짜가 시작 날짜보다 이전인 경우 오류 메시지가 수신되지는 않지만 내보내기가 실패합니다(예를 들어 종료 날짜가 2010년 1월 1일이고 시작 날짜가 2010년 6월 1일인 경우).</p>
<p>StartDate 및 EndDate 속성에 값을 할당할 대는 국가 및 언어 옵션 설정에 지정된 날짜-시간 형식을 사용합니다.</p>
<p>종료 날짜를 지정하지 않으면 현재 날짜가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeWebConfArchive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>메신저 대화 레코드만 내보내도록 <strong>Export-CsArchivingData</strong> cmdlet에 지시합니다. 기본적으로 이 cmdlet은 메신저 대화 레코드와 전화 회의 레코드를 둘 다 내보냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>IncludeTrustedApplication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함할 경우 <strong>Export-CsArchivingData</strong> cmdlet이 레코드를 내보낼 때 신뢰할 수 있는 응용 프로그램에서 기록한 데이터를 포함하도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Purge</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Purge 매개 변수는 성공적으로 내보낸 레코드를 보관 데이터베이스에서 삭제합니다. 이 매개 변수를 포함하지 않으면 내보낸 레코드가 데이터베이스에 유지됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>단일 사용자에 대한 보관 데이터 내보내기를 사용하도록 설정하는 데 사용됩니다. 이 작업은 UserUri 매개 변수를 사용하고 사용자에 대한 SIP 주소를 지정하여 수행됩니다. UserUri 매개 변수는 한 번에 하나의 URI만 허용합니다.</p></td>
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

없음. **Export-CsArchivingData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Export-CsArchivingData** cmdlet은 보관 데이터베이스 레코드를 EML 형식으로 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

