---
title: Debug-CsUnifiedContactStore
TOCTitle: Debug-CsUnifiedContactStore
ms:assetid: 8e92d262-604d-41b1-9530-947765025a79
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994054(v=OCS.15)
ms:contentKeyID: 52056889
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Debug-CsUnifiedContactStore

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹의 대화 상대가 통합 연락처 저장소에 저장되는지 여부를 확인합니다.

이 cmdlet은 Lync Server 2013용 누적 업데이트(2013년 2월)에 도입되었습니다.

## 구문

    Debug-CsUnifiedContactStore -Identity <UserIdParameter> [-ContactDataExportFileName <String>] <COMMON PARAMETERS>

    Debug-CsUnifiedContactStore -PoolFqdn <Fqdn> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 계정이 atl-cs-001.litwareinc.com 풀에 있는 모든 사용자의 통합 연락처 저장소 상태를 확인합니다.

    Debug-CsUnifiedContactStore -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 SIP 주소가 "kenmyer@litwareinc.com"인 단일 사용자의 통합 연락처 저장소 상태를 확인합니다.

    Debug-CsUnifiedContactStore -Identity "kenmyer@litwareinc.com"

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 사용하면 Microsoft Lync 2013, Outlook 2013, Outlook Web App 등의 여러 응용 프로그램에서 대화 상대 목록에 액세스할 수 있습니다. 대화 상대 정보가 단일 위치( Microsoft Exchange Server 2013)에 저장되므로 이러한 액세스가 가능합니다.

관리자는 **Debug-CsUnifiedContactStore** cmdlet을 사용하여 특정 사용자 또는 특정 사용자 집합(계정이 특정 풀에 있는 모든 사용자)의 대화 상대 목록이 통합 연락처 저장소에 저장되는지 여부를 확인할 수 있습니다. 특정 사용자 계정에 대해 **Debug-CsUnifiedContactStore** cmdlet을 실행하면 해당 cmdlet은 통합 연락처 저장소용으로 사용자 대화 상대가 이동되었는지 여부, 대화 상대 이동 시도 횟수, 그리고 Lync Server에서 마지막으로 대화 상대 목록 마이그레이션을 시도한 날짜와 시간을 표시합니다. **Debug-CsUnifiedContactStore** cmdlet을 풀에 대해 실행하면 다음과 같은 데이터가 반환됩니다.

FrontEnd: atl-cs-001.litwareinc.com  
UcsDisabledCount: 44  
UcsAllowedCount: 129  
UcsMigratingCount: 11  
UcsMigratedCount:  
FailedUserData:

**Debug-CsUnifiedContactStore** cmdlet 및 ContactDataExportFileName 매개 변수를 사용하여 특정 사용자의 대화 상대 정보를 XML 파일로 내보낼 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsUnifiedContactStore"}

**Lync Server 제어판:** **Debug-CsUnifiedContactStore** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>통합 연락처 저장소 상태를 확인 중인 개별 사용자의 SIP 주소입니다. 사용자는 명령당 한 명만 지정할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;kenmyer@litwareinc.com&quot;</p>
<p>SIP 주소를 지정할 때 필요에 따라 sip: 접두사를 포함할 수 있습니다. 예를 들어 다음 구문도 사용 가능합니다.</p>
<p>-Identity &quot;sip:kenmyer@litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>통합 연락처 저장소 상태를 확인 중인 등록자 풀의 정규화된 도메인 이름입니다. 지정된 풀에 있는 모든 사용자 계정을 확인합니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ContactDataExportFileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>통합 연락처 저장소에서 내보낸 지정한 사용자의 대화 상대가 포함되는 XML 파일의 파일 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-ContactDataExportFileName &quot;C:\Exports\KenMyer.xml&quot;</p>
<p>대화 상대를 내보내려는 사용자의 SIP 주소와 Identity 매개 변수를 포함해야 합니다. 사용자가 통합 연락처 저장소를 사용하도록 설정되지 않은 경우에는 명령이 종료되며 대화 상대 내보내기가 수행되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Debug-CsUnifiedContactStore** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**Debug-CsUnifiedContactStore** cmdlet은 Microsoft.Rtc.Management.Presence.Cmdlets.GetUcsFrontEndData 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)

