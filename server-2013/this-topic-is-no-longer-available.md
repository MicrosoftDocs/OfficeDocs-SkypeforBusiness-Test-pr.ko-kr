---
title: DNS 요약 - 공용 인스턴트 메시징 연결
TOCTitle: DNS 요약 - 공용 인스턴트 메시징 연결
ms:assetid: ddf42a25-5ac4-4643-a10a-9fbd433fc2d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618375(v=OCS.15)
ms:contentKeyID: 49305255
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# DNS 요약 - 공용 인스턴트 메시징 연결

 

_**마지막으로 수정된 항목:** 2015-03-09_

공용 인스턴트 메시징 연결에 대한 DNS(Domain Name System)를 구성할 때는 외부 사용자를 지원하는 구성에서 공용 IM 연결을 지원함을 확인할 수 있습니다. 에지 서버 또는 에지 풀을 이미 구성한 경우 공용 IM 연결을 지원하는 데 필요한 DNS 레코드가 있어야 합니다.

## DNS 요약 – 공용 인스턴트 메시징 연결


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치/형식/포트</th>
<th>FQDN/DNS 레코드</th>
<th>IP 주소/FQDN</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 서비스 인터페이스</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스(Contoso). Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)

