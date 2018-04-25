---
title: Get-CsDatabaseMirrorState
TOCTitle: Get-CsDatabaseMirrorState
ms:assetid: 458f5367-ee04-4281-971f-08f79a625509
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204845(v=OCS.15)
ms:contentKeyID: 49303490
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDatabaseMirrorState

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 풀에서 지정한 데이터베이스에 대해 데이터베이스 미러링이 구현되었는지 여부에 대한 정보를 반환합니다. 데이터베이스 미러링을 사용하면 서로 다른 서버에 있는 두 데이터베이스 복사본을 동시에 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsDatabaseMirrorState -PoolFqdn <Fqdn> [-DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt>] [-LocalStore <SwitchParameter>] [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀의 모니터링 데이터베이스에 할당된 데이터베이스 미러의 상태를 반환합니다.

    Get-CsDatabaseMirrorState -PoolFqdn "atl-cs-001.litwareinc.com" -DatabaseType Monitoring

## 자세한 정보

**Get-CsDatabaseMirrorState** cmdlet은 풀에 대해 구성된 미러 데이터베이스에 대한 정보를 반환합니다. 여기에는 프런트 엔드 서버 데이터베이스, 위치 정보 서비스 데이터베이스, 통화 정보 기록 및 체감 품질 데이터베이스 등에 대해 구성되었거나 구성되지 않았을 수 있는 미러 데이터베이스에 대한 정보가 포함됩니다. 각 데이터베이스에 대해 이 cmdlet은 기본 데이터베이스와 미러 데이터베이스 둘 다에 대한 동기화 상태를 보고합니다. 속성 값 DatabaseInaccessibleOrMirroringNotEnabled를 포함하여 다음과 같은 출력이 표시되는 경우도 있습니다.

DatabaseName : lcscdr

StateOnPrimary : DatabaseInaccessibleOrMirroringNotEnabled

StateOnMirror : DatabaseInaccessibleOrMirroringNotEnabled

MirroringStatusOnPrimary :

MirroringStatusOnSecondary :

이 출력은 대개 기본 데이터베이스(여기서는 통화 정보 데이터 유지 관리에 사용되는 lcscdr 데이터베이스)에 미러 데이터베이스가 할당되지 않았음을 의미합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDatabaseMirrorState"}

**Lync Server 제어판:** **Get-CsDatabaseMirrorState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>해당 데이터베이스 미러링 상태를 확인할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>DatabaseType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>해당 미러 상태를 확인할 데이터베이스의 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Edge</p>
<p>Lyss</p>
<p>Monitoring</p>
<p>PersistentChat</p>
<p>PersistentChatCompliance</p>
<p>Provision</p>
<p>Registrar</p>
<p>User</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 백업 미러 상태를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\DatabaseMirrorState.html&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDatabaseMirrorState** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDatabaseMirrorState** cmdlet은 Microsoft.Rtc.Management.Deployment.DatabaseMirrorState 클래스의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Install-CsMirrorDatabase](install-csmirrordatabase.md)  
[Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

