---
title: Debug-CsIntraPoolReplication
TOCTitle: Debug-CsIntraPoolReplication
ms:assetid: 9882f703-07c7-46fe-b525-7efd1326503c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205103(v=OCS.15)
ms:contentKeyID: 49304473
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Debug-CsIntraPoolReplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

주 프런트 엔드 서버에서 지정한 사용자에 대해 저장된 데이터를 복제본 프런트 엔드 서버에서 같은 사용자에 대해 저장된 데이터와 비교하여 풀의 동기 복제를 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Debug-CsIntraPoolReplication -UserUri <UserIdParameter> <COMMON PARAMETERS>

    Debug-CsIntraPoolReplication -ConferenceDirectory <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 SIP 주소가 "sip:kenmyer@litwareinc.com"인 사용자를 사용하여 프런트 엔드 서버에서 복제를 확인합니다.

    Debug-CsIntraPoolReplication -UserUri "sip:kenmyer@litwareinc.com"

## 예제 2

예제 2에서는 Redmond OU에 사용자 계정이 있는 모든 사용자를 사용하여 복제를 확인합니다. 이를 위해 명령은 먼저 OU 매개 변수를 포함하여 Get-CsUser를 호출합니다. 매개 변수 값 "OU=Redmond,dc=litwareinc,dc=com"은 반환되는 데이터를 Redmond OU에 있는 사용자 계정으로 제한합니다. 해당 계정은 ForEach-Object cmdlet에 파이프되며, 이 cmdlet은 Debug-CsIntraPoolReplication cmdlet을 사용하여 OU에 있는 각 계정의 복제 상태를 확인합니다.

    Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | ForEach-Object {Debug-CsIntraPoolReplication $_.Identity}

## 예제 3

예제 3에 표시된 명령은 사용자 SIP 주소 쌍을 사용하여 복제 상태를 확인합니다. 이 작업을 수행하기 위해 따옴표로 묶이고 쉼표로 분리된 두 개의 SIP 주소를 ForEach-Object cmdlet에 파이프합니다. 이 cmdlet은 각 SIP 주소에 대해 Debug-CsIntraPoolReplication cmdlet을 실행합니다.

    "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com" | ForEach-Object {Debug-CsIntraPoolReplication -UserUri $_}

## 예제 4

예제 4에서는 ID가 13인 전화 회의 디렉터리에 대해 복제를 확인합니다.

    Debug-CsIntraPoolReplication -ConferenceDirectory 13

## 예제 5

예제 5에서는 지정된 등록자 풀에 있는 모든 사용자에 대해 복제를 확인하는 방법을 보여 줍니다. 이를 위해 명령은 먼저 Filter 매개 변수를 포함하여 Get-CsUser를 호출합니다. 필터 값 {RegistrarPool –eq "atl-cs-001.litwareinc.com"}은 반환되는 데이터를 등록자 풀 atl-cs-001.litwareinc.com에 있는 사용자 계정으로 제한합니다. 해당 계정은 Debug-CsIntraPoolReplication cmdlet에 파이프되며, 이 cmdlet은 풀의 각 사용자에 대해 복제를 확인합니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Debug-CsIntraPoolReplication UserUri {$_.Identity}

## 자세한 정보

관리자는 Debug-CsIntraPoolReplication cmdlet을 사용하여 주 프런트 엔드 서버와 해당 복제본 프런트 엔드 서버 간에 복제가 수행되고 있는지를 확인할 수 있습니다. 이 작업을 수행하려면 지정된 사용자의 데이터가 프런트 엔드 서버와 모든 복제본 서버에서 동일한지를 확인하거나, 전화 회의 디렉터리의 데이터가 프런트 엔드 서버와 모든 복제본 서버에서 동일한지를 확인하는 두 가지 방법 중 하나를 사용합니다. 이 두 작업 중 하나를 수행하기 위해 Debug-CsIntraPoolReplication은 먼저 주 프런트 엔드 서버에 연결한 다음 사용자 또는 전화 회의 디렉터리 데이터가 포함된 XML 파일을 생성합니다. 이 cmdlet은 그런 다음 복제본 서버에 연결하여 이와 비슷한 XML 파일을 생성한 후 XML 파일에서 선택한 콘텐츠가 동일한지 확인합니다.

Debug-CsIntraPoolReplication cmdlet은 하나 이상의 사용자 계정이나 전화 회의 디렉터리 하나를 가져온 후 주 프런트 엔드 서버 및 모든 복제본 프런트 엔드 서버에 해당 계정 또는 전화 회의 디렉터리에 대한 데이터를 쿼리하여 풀의 복제를 확인합니다. 그런 다음 주 프런트 엔드 서버 및 복제본 서버에서 검색된 정보를 비교하여 데이터가 일치하면 풀 내부 복제가 정상적으로 작동하는 것으로 가정합니다.

이 cmdlet은 Lync Server 2013에 있는 사용자 또는 전화 회의 디렉터리를 사용해서만 호출할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsIntraPoolReplication"}

**Lync Server 제어판:** Debug-CsIntraPoolReplication cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>ConferenceDirectory</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>전화 회의 디렉터리의 복제를 확인할 수 있습니다. 전화 회의 디렉터리는 디렉터리 ID를 사용하여 지정해야 합니다. 다음 명령을 사용하여 전화 회의 디렉터리 ID를 검색할 수 있습니다.</p>
<p>Get-CsConferenceDirectory | Select-Object Identity, ServiceId</p>
<p>같은 명령에서 ConferenceDirectory 매개 변수와 UserUri 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserUri</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>풀 내부 복제 테스트에 사용되는 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-UserUri &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>같은 명령에서 ConferenceDirectory 매개 변수와 UserUri 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. Debug-CsIntraPoolReplication은 Lync Server를 사용하도록 설정된 사용자 계정의 Active Directory 표시 이름 또는 SIP 주소를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 이 cmdlet은 Lync Server를 사용하도록 설정된 사용자에 대한 Active Directory 사용자 개체의 파이프라인된 인스턴스도 허용합니다.

## 반환 형식

Debug-CsIntraPoolReplication은 Microsoft.Rtc.Management.UserPinservice.Data.syncReplicationDetails 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)  
[Test-CsReplica](test-csreplica.md)

