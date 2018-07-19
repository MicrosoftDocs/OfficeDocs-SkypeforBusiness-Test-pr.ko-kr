---
title: 재해 복구 중에 그룹 호출 받기 관리
TOCTitle: 재해 복구 중에 그룹 호출 받기 관리
ms:assetid: 2d32f19f-c649-4a72-a4fb-edd338e3a7cc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945618(v=OCS.15)
ms:contentKeyID: 52056811
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 재해 복구 중에 그룹 호출 받기 관리

 

_**마지막으로 수정된 항목:** 2015-03-09_

계획되지 않은 사고로 인해 프런트 엔드 풀을 사용할 수 없게 되면 서비스가 백업 풀로 장애 조치(failover)됩니다. 백업 풀로 장애 조치(failover)하는 중에는 사용자가 백업 풀로 리디렉션되고 복구 모드에 있게 됩니다. 복구 모드에서는 사용자가 다른 사용자의 전화를 받거나 다른 사용자가 자신에게 온 전화를 받도록 할 수 없습니다. 장애 조치(failover)가 완료되면 사용자가 그룹 호출 받기를 다시 정상적으로 사용할 수 있습니다.

기본 풀로의 장애 복구(failback) 중에 사용자는 기본 풀로 리디렉션되며 다시 복구 모드에 있게 됩니다. 사용자의 복구 모드가 해제될 때까지는 그룹 호출 받기 기능을 사용할 수 없습니다.

이 섹션에서는 재해 복구 중의 그룹 호출 받기에 대한 몇 가지 고려 사항과 사용자 환경에 대해 설명합니다.

## 재해 복구 중의 그룹 호출 받기에 대한 고려 사항

재해 복구 중에는 장애 조치(failover) 프로세스의 일환으로 백업 풀로 리디렉션되었던 사용자가 호출 받기 그룹 번호에 대해 백업 풀에서 실행되는 통화 대기 응용 프로그램을 사용합니다. 따라서 재해 복구 중에 그룹 호출 받기를 지원하려면 기본 풀과 백업 풀에서 모두 통화 대기 응용 프로그램을 배포하고 사용하도록 설정해야 합니다.

백업 풀로의 장애 조치(failover) 프로세스가 완료되고 나면 통화 대기 번호 테이블의 그룹 호출 받기 번호 범위를 백업 풀로 리디렉션해야 합니다. 기본 풀로의 장애 복구(failback) 프로세스가 완료된 후에는 번호 범위를 기본 풀로 다시 리디렉션해야 합니다. 그룹 호출 받기 범위를 리디렉션하려면 **Set-CsCallParkOrbit** cmdlet을 사용합니다.

FQDN(정규화된 도메인 이름)이 다른 새 풀을 배포하여 기본 풀을 대체할 경우 기본 풀과 연결된 모든 그룹 호출 받기 번호 범위를 새 풀의 FQDN에 다시 할당해야 합니다. 번호 범위를 새 풀에 다시 할당하려면 **Set-CsCallParkOrbit** cmdlet을 사용할 수 있습니다. **Set-CsCallParkOrbit** cmdlet에 대한 자세한 내용은 [Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit)을 참조하십시오.

## 풀 오류 발생 시 그룹 호출 받기 환경

다음 표에서는 재해 복구 단계 중의 그룹 호출 받기 환경에 대해 간략하게 설명합니다.

### 재해 복구 시 사용자 환경

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 상태</th>
<th>백업 풀로의 장애 조치(failover)</th>
<th>기본 풀로의 장애 복구(failback)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>새 통화</p></td>
<td><p><strong>장애 조치(failover) 프로세스 중:</strong></p>
<ul>
<li><p>복구 모드의 사용자에 대해 그룹 호출 받기를 사용할 수 없음</p></li>
</ul>
<p><strong>장애 조치(failover) 완료 후:</strong></p>
<ul>
<li><p>사용자의 복구 모드가 해제되고 그룹 호출 받기 번호 범위가 백업 풀로 리디렉션되면 그룹 호출 받기를 사용할 수 있음</p></li>
</ul></td>
<td><p><strong>장애 복구(failback) 프로세스 중:</strong></p>
<ul>
<li><p>복구 모드의 사용자에 대해 그룹 호출 받기를 사용할 수 없음</p></li>
</ul>
<p><strong>장애 복구(failback) 완료 후:</strong></p>
<ul>
<li><p>사용자의 복구 모드가 해제되고 그룹 호출 받기 번호 범위가 기본 풀로 다시 리디렉션되면 그룹 호출 받기를 사용할 수 있음</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>그룹 호출 받기 대기열의 통화</p></td>
<td><p><strong>장애 조치(failover) 프로세스 중:</strong></p>
<ul>
<li><p>그룹 호출 받기를 통해 대기열의 통화를 받을 수 없음</p></li>
</ul>
<p><strong>장애 조치(failover) 완료 후:</strong></p>
<ul>
<li><p>이 상태의 통화가 없음</p></li>
</ul></td>
<td><p><strong>장애 복구(failback) 프로세스 중:</strong></p>
<ul>
<li><p>그룹 호출 받기를 통해 대기열의 통화를 받을 수 없음</p></li>
</ul>
<p><strong>장애 복구(failback) 완료 후:</strong></p>
<ul>
<li><p>그룹 호출 받기를 통해 대기열의 통화를 받을 수 없음</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>연결된 통화</p></td>
<td><p><strong>장애 조치(failover) 프로세스 중:</strong></p>
<ul>
<li><p>통화가 연결된 상태로 유지됨</p></li>
</ul>
<p><strong>장애 조치(failover) 완료 후:</strong></p>
<ul>
<li><p>통화가 연결된 상태로 유지됨</p></li>
</ul></td>
<td><p><strong>장애 복구(failback) 프로세스 중:</strong></p>
<ul>
<li><p>통화가 연결된 상태로 유지됨</p></li>
</ul>
<p><strong>장애 복구(failback) 완료 후:</strong></p>
<ul>
<li><p>통화가 연결된 상태로 유지됨</p></li>
</ul></td>
</tr>
</tbody>
</table>

