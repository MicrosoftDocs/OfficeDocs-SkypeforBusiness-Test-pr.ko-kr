---
title: Get-CsUserDatabaseState
TOCTitle: Get-CsUserDatabaseState
ms:assetid: c90150cd-fdb0-4c79-af58-c9ad884cb043
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398831(v=OCS.15)
ms:contentKeyID: 49305012
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserDatabaseState

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 Lync Server 사용자 데이터베이스에 대한 온라인 상태(True 또는 False) 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUserDatabaseState [-RegistrarPool <Fqdn>] <COMMON PARAMETERS>

    Get-CsUserDatabaseState [-Identity <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 각 사용자 데이터베이스의 온라인 상태를 반환합니다.

    Get-CsUserDatabaseState

## 예제 2

예제 2에 표시된 명령은 단일 사용자 데이터베이스, 즉 ID가 UserDatabase:atl-sql-001.litwareinc.com인 데이터베이스의 온라인 상태를 반환합니다.

    Get-CsUserDatabaseState -Identity "UserDatabase:atl-sql-001.litwareinc.com"

## 예제 3

예제 3에서는 등록자 풀 atl-cs-001.litwareinc.com 내에 있는 모든 사용자 데이터베이스에 대한 상태 정보를 반환합니다.

    Get-CsUserDatabaseState -RegistrarPool "atl-cs-001.litwareinc.com"\

## 예제 4

예제 4에서는 현재 온라인 상태인 모든 사용자 데이터베이스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUserDatabaseState** cmdlet을 호출합니다. 조직에서 사용 중인 모든 사용자 데이터베이스 컬렉션이 반환됩니다. 이 컬렉션은 Online 속성이 True와 같은 데이터베이스만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUserDatabaseState | Where-Object {$_.Online -eq $True}

## 자세한 정보

Lync Server은 사용자 데이터베이스(사용자 저장소라고도 함)를 사용하여 Lync Server 사용자의 현재 상태 및 경로 지정 정보를 유지 관리합니다. **Get-CsUserDatabaseState** cmdlet을 사용하면 조직에서 현재 사용 중인 모든 사용자 데이터베이스의 현재 상태(온라인 또는 오프라인)를 확인할 수 있습니다.

기본적으로 Lync Server Standard Edition을 설치하면 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 즉, Windows PowerShell의 원격 인스턴스에서 **Get-CsUserDatabaseState** cmdlet을 실행할 수 없습니다. 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 cmdlet을 로컬에서(즉, Standard Edition 서버 자체에서) 실행할 수는 있습니다. 하지만 **Get-CsUserDatabaseState** cmdlet을 원격에서 실행하려면 SQL Server Express에 대한 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsUserDatabaseState** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserDatabaseState"}

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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>온라인 상태를 반환할 사용자 데이터베이스의 고유 식별자입니다(예: -Identity &quot;UserDatabase:atl-sql-001.litwareinc.com&quot;).</p>
<p>Identity 및 RegistrarPool을 같은 명령에 함께 사용할 수 없으며 이러한 매개 변수에 와일드카드를 사용할 수도 없습니다. 두 매개 변수가 모두 없으면 <strong>Get-CsUserDatabaseState</strong> cmdlet에서 현재 사용 중인 모든 사용자 데이터베이스에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>온라인 상태를 반환할 사용자 데이터베이스를 호스트하는 등록자 풀의 정규화된 도메인 이름입니다 (예: -RegistrarPool &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>Identity 및 RegistrarPool을 같은 명령에 함께 사용할 수 없으며 이러한 매개 변수에 와일드카드를 사용할 수도 없습니다. 두 매개 변수가 모두 없으면 <strong>Get-CsUserDatabaseState</strong> cmdlet에서 현재 사용 중인 모든 사용자 데이터베이스에 대한 정보를 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUserDatabaseState** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUserDatabaseState** cmdlet은 Microsoft.Rtc.Management.Xds.UserStoreState 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsUserDatabaseState](set-csuserdatabasestate.md)  
[Update-CsUserDatabase](update-csuserdatabase.md)

