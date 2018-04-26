---
title: 가상 트랜잭션을 실행하도록 감시자 노드 구성
TOCTitle: 가상 트랜잭션을 실행하도록 감시자 노드 구성
ms:assetid: cedda508-8881-4079-88d5-49798f342ddf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205314(v=OCS.15)
ms:contentKeyID: 49305078
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 가상 트랜잭션을 실행하도록 감시자 노드 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

System Center 에이전트 파일이 설치된 후 감시자 노드 자체를 구성해야 합니다. 감시자 노드를 구성하는 단계는 감시자 노드 컴퓨터가 조직의 경계 네트워크 내에 있는지, 아니면 외부에 있는지에 따라 달라집니다.

감시자 노드를 구성할 때 해당 노드에 채택할 인증 방식 유형도 선택해야 합니다. Lync Server 2013에서는 트러스트된 서버 또는 자격 증명 인증의 두 가지 인증 방식을 선택할 수 있습니다. 이 두 방식의 차이점은 다음 표에 정리되어 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>구성</th>
<th>설명</th>
<th>지원되는 위치</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>트러스트된 서버</p></td>
<td><p>인증서를 사용하여 내부 서버를 가장하고 인증 질문을 무시합니다.</p>
<p>이는 각 감시자 노드마다 다른 사용자 암호를 사용하지 않고 단일 인증서를 관리하려는 관리자에게 유용합니다.</p></td>
<td><p>기업 내부</p>
<p>이 방식을 사용하면 감시자 노드는 모니터링되는 풀과 동일한 도메인에 있어야 합니다. 감시자 노드 및 모니터링되는 풀이 서로 다른 도메인인 경우 자격 증명 인증을 대신 사용하세요.</p></td>
</tr>
<tr class="even">
<td><p>자격 증명 인증</p></td>
<td><p>각 감시자 노드의 Windows Credential Manager에 사용자 이름과 암호를 안전하게 저장합니다.</p>
<p>이 모드를 사용하면 암호 관리에 더 많은 작업이 필요하지만 기업 외부에 위치한 감시자 노드를 위한 유일한 옵션입니다. 이러한 감시자 노드는 인증을 신뢰할 수 있는 끝점으로 처리될 수 없습니다.</p></td>
<td><p>기업 외부</p>
<p>기업 내부</p></td>
</tr>
</tbody>
</table>


또한 방화벽에 MonitoringHost.exe 및 PowerShell.exe 모두에 대한 인바운드 규칙이 있는지 확인해야 합니다. 이러한 프로세스가 방화벽에 의해 차단될 경우 가상 트랜잭션이 실패하고 504(서버 시간 초과) 오류가 발생합니다.

