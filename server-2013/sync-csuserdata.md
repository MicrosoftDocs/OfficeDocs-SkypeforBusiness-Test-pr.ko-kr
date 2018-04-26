---
title: Sync-CsUserData
TOCTitle: Sync-CsUserData
ms:assetid: c385041f-f3f7-4db0-9ca7-b5f20a5d81d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205242(v=OCS.15)
ms:contentKeyID: 49304945
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Sync-CsUserData

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 풀 쌍 간에 사용자 데이터를 동기화합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Sync-CsUserData -PoolFqdn <Fqdn> [-LocalStore <SwitchParameter>] [-RoutingGroup <String>] [-Target <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀과 지정된 백업 풀을 동기화합니다.

    Sync-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

**Sync-CsUserData** cmdlet은 등록자 풀과 할당된 백업 풀 간에 사용자 데이터를 동기화합니다. 해당 풀을 백업 서비스가 활성화하지 않은 경우에는 이 cmdlet 호출이 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Sync-CsUserData"}

**Lync Server 제어판:** **Sync-CsUserData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>기본 Lync Server 2013 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 사용자 데이터를 검색합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RoutingGroup</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정된 라우팅 그룹에 대해서만 데이터를 동기화할 수 있습니다. 라우팅 그룹은 사용자가 등록되어 있는 프런트 엔드 서버를 지정하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>미리 할당된 백업 풀과 데이터를 동기화합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Sync-CsUserData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Convert-CsUserData](convert-csuserdata.md)  
[Export-CsUserData](export-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Update-CsUserData](update-csuserdata.md)

