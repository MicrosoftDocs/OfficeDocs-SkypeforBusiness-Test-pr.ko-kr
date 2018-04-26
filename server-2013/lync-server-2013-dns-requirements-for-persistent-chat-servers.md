---
title: 영구 채팅 서버에 대한 DNS 요구 사항
TOCTitle: 영구 채팅 서버에 대한 DNS 요구 사항
ms:assetid: f7531374-d7ed-4b63-ae81-02294cb4496a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205391(v=OCS.15)
ms:contentKeyID: 49305559
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 영구 채팅 서버에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 영구 채팅 서버을 배포하는 데 필요한 DNS(Domain Name System) 레코드에 대해 설명합니다.

## 영구 채팅 서버에 대한 DNS 레코드

다음 표는 영구 채팅 서버 배포에 대한 DNS 요구 사항을 지정합니다.

### 영구 채팅 서버에 대한 DNS 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>배포 시나리오</th>
<th>DNS 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>영구 채팅 서버 한 개</p></td>
<td><p>서버의 FQDN(정규화된 도메인 이름)을 IP 주소로 확인하는 내부 A 레코드</p></td>
</tr>
<tr class="even">
<td><p>영구 채팅 풀</p></td>
<td><p>서버의 FQDN(정규화된 도메인 이름)을 IP 주소로 확인하는 내부 A 레코드</p>
<p><strong>예</strong></p>
<p>PersistentChatServer01.contoso.com     10.10.10.1</p>
<p>PersistentChatServer02.contoso.com     10.10.10.2</p>
<p>서버의 FQDN(정규화된 도메인 이름)을 IP 주소로 확인하는 내부 A 레코드</p>
<p><strong>예</strong></p>
<p>PersistentChatPool.contoso.com    10.10.10.1</p>
<p>PersistentChatPool.contoso.com    10.10.10.2</p></td>
</tr>
</tbody>
</table>

